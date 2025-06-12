---
title: Jenkins-note
description: Jenkins学习笔记记录 | 具有时效性，更新日期3/25/2025
publishDate: 2025-04-28
tags:
  - study
ogImage: /social-card.avif
---

### Jenkins 介绍
一款开源CI&CD 软件，用于自动化各种任务，包括构建、测试和部署软件。
支持系统包、Docker或者通过一个独立的Java程序。
与开发并行，而无需等待项目完成上线
![work-process.png](https://picx-6wq.pages.dev/rest/ITh6TrK.png)
由图示可知，Jenkins安装需要Java、git、maven、tomcat环境，所以在服务器中部署需要安装前置环境，但是支持docker部署，所以有docker环境会省不少事情
按照官网直接docker run命令,
```markdown
Blue Ocean 是 Jenkins 的一个插件，它重新设计了 Jenkins 的 UI，使其更加现代化、直观，特别适合可视化流水线（Pipeline）的构建过程。
jenkinsci/blueocean 镜像是一个 预装了 Blue Ocean 插件的 Jenkins 镜像，它包含了：
- Jenkins 核心
- Blue Ocean 插件
- 其他常用插件（如 Git、Docker 等）
- 更适合现代 CI/CD 工作流
```
```docker
docker run \
  -u root \
  --rm \  
  -d \ 
  -p 8080:8080 \ 
  -p 50000:50000 \ 
  -v jenkins-data:/var/jenkins_home \ 
  -v /var/run/docker.sock:/var/run/docker.sock \ 
  jenkinsci/blueocean 
```
---
但是搜索了下网上的教程，和官网不一致，是不包含任何插件的Jenkins，镜像会更小

<details>

<summary>可参考</summary>

1. docker拉取镜像
`docker pull jenkins/jenkins:版本号-lts` 指定版本，否则拉取的镜像是比较老的版本 | lts：long-term support 长期支持

2. 创建挂载目录
```docker
// 创建目录
mkdir -p /var/jenkins_data
// 授权权限
chmod 777 /var/jenkins_data
```

3. 启动Jenkins容器
```docker
docker run \
  -u root \ 
  -d \ 
  -p 8080:8080 \ 
  -p 50000:50000 \ 
  -v /var/jenkins_data:/var/jenkins_home \  
  -v /var/run/docker.sock:/var/run/docker.sock \ 
  --name myjenkins \
  jenkins/jenkins:版本号-lts
```
`-d`：后台运行容器
`-p 8080:8080\` ：端口映射，第一个数字代表主机上的端口，而最后一个代表容器端口，8080是Jenkins Web 界面的工作端口,50000是JNLP（Java Network Launch Protocol）工作端口
若主机端口被占用，换为闲置端口即可
`-v /var/jenkins_data:/var/jenkins_home`：目录挂载，持久化数据到主机的 /var/jenkins_data 目录，可以按需修改
`v /var/run/docker.sock:/var/run/docker.sock`：允许 Jenkins 调用宿主机 Docker

1. 查看Jenkins是否启动成功
`docker ps -l` 
</details>


---

:::note[扩展一下] 
<img src="https://www.runoob.com/wp-content/uploads/2014/06/d0c50-linux2bfile2bsystem2bhierarchy.jpg"/>
q1：挂载目录有什么讲究吗？  
a： 
- /var：通常用于存放经常变动的数据，例如系统运行时的数据（如日志、数据库、缓存等）；
- /user：存放用户安装的软件与程序；
- /opt：存放第三方软件；
- /home：存放所有用户的用户数据，一般用`~`代替，eg.~/user,普通用户只能访问自己的用户目录而不能访问他人的。

q2：chmod 777 目录 代表什么？
a：Linux/Unix文件调用权限分为三级：文件所有者（owner）、用户组（group）、其他用户（other users） 。只有owner和超级用户可以修改文件或目录的权限
权限由**3位数字**组成，分别对应所有者（Owner）、组（Group）、其他用户（Others） 的权限。
| 数字 | 权限 | 二进制 | 含义|
|--|--|--|--|
|7|rwx|111|读、写、执行|
|6|rw-|110|读、写|
|5|r-x|101|读、执行|
|4|r--|100|读|
|0|---|000|无权限|

q3：为什么使用777？
a：Jenkins需要写入权限：Jenkins作为CI/CD工具，需要在该目录下创建、修改文件；

q4：先拉取镜像再执行docker run命令和直接在run命令中直接拉取(隐式拉取：若在本地找不到镜像会自动拉取)有什么区别呢？
a：执行流程对比
- 方式一：显式拉取（推荐）
1. 先拉取（明确版本，独立检查）

  `docker pull jenkins/jenkins:lts`

1. 再运行（确保使用刚拉取的镜像）
  `docker run -d --name jenkins -p 8080:8080 jenkins/jenkins:lts`
- 方式二：隐式拉取
 直接运行（若本地无镜像会自动拉取，但可能存在问题）
 `docker run -d --name jenkins -p 8080:8080 jenkins/jenkins:lts`


:::

参考引用：
> https://www.jenkins.io/zh/doc/
>
> https://www.cnblogs.com/fuzongle/p/12834080.html |（2020发布，部分内容已过时，仅供参考）