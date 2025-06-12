---
title: Azure 虚拟机
description: 这是一篇有意思的文章
publishDate: 2025-03-06
tags:
  - vps
ogImage: /social-card.avif
---
Azure学生认证可免费创建Linux虚拟机，创建免费虚拟机的方式似乎改了，可以直接在以下url中直接创建

> [Microsoft Azure](http://portal.azure.com/#view/Microsoft_Azure_Marketplace/GalleryItemDetailsBladeNopdl/id/microsoft.freeaccountvirtualmachine-linux/resourceGroupId//resourceGroupLocation//dontDiscardJourney~/false/_provisioningContext~/%7B%22initialValues%22%3A%7B%22subscriptionIds%22%3A%5B%2244abf6d9-3a16-4bae-8546-14cc71feb722%22%5D%2C%22resourceGroupNames%22%3A%5B%5D%2C%22locationNames%22%3A%5B%22eastasia%22%5D%7D%2C%22telemetryId%22%3A%225e2a4b3b-b904-4aba-8ee3-dfcd05f5900f%22%2C%22marketplaceItem%22%3A%7B%22categoryIds%22%3A%5B%5D%2C%22id%22%3A%22Microsoft.Portal%22%2C%22itemDisplayName%22%3A%22NoMarketplace%22%2C%22products%22%3A%5B%5D%2C%22version%22%3A%22%22%2C%22productsWithNoPricing%22%3A%5B%5D%2C%22publisherDisplayName%22%3A%22Microsoft.Portal%22%2C%22deploymentName%22%3A%22NoMarketplace%22%2C%22launchingContext%22%3A%7B%22telemetryId%22%3A%225e2a4b3b-b904-4aba-8ee3-dfcd05f5900f%22%2C%22source%22%3A%5B%5D%2C%22galleryItemId%22%3A%22%22%7D%2C%22deploymentTemplateFileUris%22%3A%7B%7D%2C%22uiMetadata%22%3Anull%7D%7D)

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

1. b1s
- 区域：East Asia
- 映像：Ubuntu Server 20.04
- 大小：
Standard B1s (1 vcpu，1 GiB 内存[**实际可用约900MB**])

2. b2ats
- 区域：Japan East
- 映像：Debian
- 大小（2 vcpu , 1 GiB 内存）

创建完毕后，即可使用FinalShell远程连接工具连接Linux虚拟机

1. 在Finalshell中新建SSH连接
2. 输入名称（随意）、主机（在创建好的虚拟机面板概述中复制 `公共IP地址`）、端口号默认22、以及认证方式（密码登录/SSH登录）
3. 确认连接（若密码不正确会一直弹窗提醒输入密码）

---

~~由于不支持动态ip~~，把b1s的机子删掉了（幸好还没部署什么服务），在b2ats上安装了1panel面板，个人还不太熟悉docker，所以先从可视面板入手吧
[1panel 官方文档](https://1panel.cn/docs/)
按照文档来操作还是很简单的
1. 连接az虚拟机后输入命令行 : `curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && bash quick_start.sh` (Debian)
2. 除了用户名和密码自设置外其余均可设为默认
3. 由于是远程虚拟机，需要在az中放行端口
很简单,但是搭完突然不知道要干什么了，又想起之前看到的[朋友圈项目](https://github.com/kingwrcy/moments)了,支持docker部署，所以顺便一起部署一下吧
<details>
<summary>my own comments </summary>
<img src="https://picx-6wq.pages.dev/rest/F4snURK.png"/>
后续可能会绑域名+Nginx代理+SSL证书上传

</details>

---
还是可以暂时改为动态ip的（到9月底可能会下掉），可以用命令行（虽然我试了没效果），我直接在azure面板改的，先取消关联，再修改为动态ip，再恢复关联即可

