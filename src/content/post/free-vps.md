---
title: 免费额度vps收录-一览余
description: vps白嫖渠道 | 具有时效性，更新日期4/30/2025
publishDate: 2025-04-30
tags:
  - vps
ogImage: /social-card.avif
---

#### 主要是用来学习而非部署一些长期服务的，所以收集了一些免费的vps来源（部分需要学生认证）
##### 另外也有一点仓鼠症:laughing:

### 1. github 学生包
github通过学生认证后可以更加方便得通过其他权益，比如Azure（同属微软）
不过本人是直接使用edu先开的Azure 100，后续才开通github学生包。

入口 -> [github-education](https://education.github.com/experiences/intro_to_web_dev)，找到`Digital Ocean`
<img src="https://picx-6wq.pages.dev/rest/GBq6vrK.png" width=20%>
点击`Get access by connecting your Github account on DigitalOcean`通过oauth授权即可获得一年有效期的200\$赠金，另外，其实也可以通过他人的邀请链接获得6个月的200$赠金，两者不可叠加。

需要绑卡验证，此处可以选择信用卡、支付宝、paypal（会提前扣5\$），个人选择的是支付宝认证，不会提前扣款，验证之后可以去zfb后台取消自动扣款。

进入控制台点击new project -> Create Droplets
<img src="https://picx-6wq.pages.dev/rest/NlRivrK.png" width=70%>
配置好地区、os、cpu、认证方式等就可以拥有一台小鸡了，具体计费可见上图，例如premium intel-1c2g-16\$ 每月，差不多可以用1年，也可以选择更高的配置。

### 2. Azure 100
可用于开通虚拟机服务（也可用于开通大模型eg.OpenAI、DS..），学生认证之后就可以看到下面的认证信息。如果有成本那一栏，说明每月流量有100+15g，没有的话每月15g。
<img src="https://picx-6wq.pages.dev/rest/fuHfvrK.png" width=50% >


从免费服务中进 - > [Free Services- vps](https://portal.azure.com/#view/Microsoft_Azure_Billing/FreeServicesBlade)，但是自动分配了静态ip（会从200\$配额中扣取一定额度），后续可以改为免费的动态ip（应该能撑到25年9月）

> ps: Azure风控加严，学生认证如果失败的话可以联系客服 -> [Azure
Dev Tools for Teaching](https://azureforeducation.microsoft.com/en-us/institutions/Contact)，选择学校所在地区，等待回复（约五个工作日左右）即可。

<details>
<summary>部署过程</summary>


<details>

<summary>Azure 免费帐户包括 </summary>

- 750 hours of *Standard B1, B2ATS, and B2PTS Linux Virtual Machine*

  750 小时的*标准 B1、B2ATS 和 ~~B2PTS Linux 虚拟机~~*
  
- 750 hours of *Standard B1, B2ATS Windows Virtual Machine*

    750 小时的*标准 B1、B2ATS Windows 虚拟机*

- 2 P6 (64GiB) managed disks
  
   2 个 P6（64GiB） 托管磁盘

In order to create a free virtual machine with managed disk, you have to choose the correct parameters such as image, vm size and disk size. This offer helps you select these parameters. Virtual machines created through this offer are free only for users with free account benefits. This offer supports Intel (B1) and AMD (B2ATS) deployments.

为了创建带有托管磁盘的免费虚拟机，您必须选择正确的参数，例如映像、虚拟机大小和磁盘大小。此优惠可帮助您选择这些参数。通过此优惠创建的虚拟机仅对拥有免费帐户优惠的用户免费。此优惠支持 Intel (B1) 和 AMD (B2ATS) 部署。

</details>

我的选择： 

b2ats
- 区域：Japan East
- 映像：Debian
- 大小（2 vcpu , 1 GiB 内存）

创建完毕后，即可使用FinalShell远程连接工具连接Linux虚拟机

1. 在Finalshell中新建SSH连接
2. 输入名称（随意）、主机（在创建好的虚拟机面板概述中复制 `公共IP地址`）、端口号默认22、以及认证方式（密码登录/SSH登录）
3. 确认连接（若密码不正确会一直弹窗提醒输入密码）

---

~~由于不支持动态ip~~，把b1s的机子删掉了（幸好还没部署什么服务），在b2ats上安装了1panel面板
[1panel 官方文档](https://1panel.cn/docs/)
按照文档来操作还是很简单的
1. 连接az虚拟机后输入命令行 : `curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && bash quick_start.sh` (Debian)
2. 除了用户名和密码自设置外其余均可设为默认
3. 由于是远程虚拟机，需要在az中放行端口
顺便一起部署了之前看到的[朋友圈项目](https://github.com/kingwrcy/moments)了,支持docker部署
<details>
<summary>my own comments </summary>
<img src="https://picx-6wq.pages.dev/rest/F4snURK.png"/>
后续可能会绑域名+Nginx代理+SSL证书上传

</details>

vps安全设置[参考](https://blog.noospic.me/posts/to-do/#5-vps%E9%85%8D%E7%BD%AE);否则就会看到日志中一堆异国或异地尝试登录自己的小鸡...


---
还是可以暂时改为动态ip的（到9月底可能会下掉），可以用命令行（虽然我试了没效果），我直接在azure面板改的，先取消关联，再修改为动态ip，再恢复关联即可

</details>


### ~~3. GCP300~~
- 前提条件：需要gmail邮箱和信用卡
  

已有，有效期三月，不打算一直续，弃


----

### expand
vps测速：
https://blog.laoda.de/archives/vps-speedtest
