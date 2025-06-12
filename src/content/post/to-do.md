---
title: TO-DO
description: todo-list
publishDate: 2025-03-30
tags:
  - todo
ogImage: /social-card.avif
---
### 1. 每天学一点 - AI篇

### 2. wsl配置

<img src="https://pub-2922618b298540fba9bd5a8f8500b762.r2.dev/image-20250612171156255.png" alt="wsl-ubuntu-config" style="zoom:67%;" />

> 有部分重复内容，后续结合自己的操作步骤再整理筛选一下

* Ubuntu 20.04 升级 -> 22.04 
* 发行版本后续可能换成`Debian`

[WSL2配置完全指北——手把手教你配置WSL2](https://linux.do/t/topic/132043)

\-- 参考文件位置： `C:\Users\<username>\.wslconfig`

```bash
[wsl2]
networkingMode=bridged
vmSwitch=WSLBridge
ipv6=false
memory=16GB
swap=4GB
processors=8
localhostForwarding=true
```

[windows WSL2避坑指南](https://www.cnblogs.com/yjmyzz/p/wsl2-tutorial-1.html)

[解决Windows中使用WSL2占用磁盘空间问题 - 鸿辰个人分享站](https://www.sunyonghong.com/post/20240722117.html)

[Vmmem进程(WSL)占用CPU或内存资源过高的解决办法-CSDN博客](https://blog.csdn.net/Power_Blogger/article/details/128158694)

### 3. Docker配置

[从前端角度学习docker](https://linux.do/t/topic/469643)

~~[Windows下Docker Desktop占用过大空间解决方法 | 张益铭的博客](https://zhangyiming748.github.io/post/docker_desktop_on_windows_compact/)~~ -> 不打算使用docker-desktop了

### 4. Azure 虚拟机（https://portal.azure.com/#home）

- [x] [(新手体验总结帖)Azure Linux1c1g学生机+宝塔面板+CloudflareTunnels部署容器，以oneapi为例（1g1c的还是首推命令行直接输命令）](https://linux.do/t/topic/101813)

- [x] [宝塔面板如何设置反向代理？_网硕互联](https://www.wsisp.com/helpcontent/146.html)

### 5. VPS配置
> ps:可重复参考

- [x] [服务器安全设置](https://blog.laoda.de/archives/how-to-secure-a-linux-server)  only setting on vps-do

