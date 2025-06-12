---
title: docker项目-moments
description: 有趣的Docker项目
publishDate: 2025-04-21
tags:
  - docker
ogImage: /social-card.avif
---
之前docker部署了一个朋友圈项目-moments，但是还没绑自定义域名和上传ssl证书，vps不关机ip不变所有直接在cf上添加了一条A记录指向了vps ip
其实如果要关机的话的话也可以添加cname记录，这样ip变化部署的项目还可以根据域名正常访问

本来部署了Nginx Proxy Manager，想在上面反代一下moments，可是添加SSL一直显示internel error，google了一下这个问题还挺常见的，有部分说是npm版本问题、网络问题... 好像没有有效的解决方案，索性把npm镜像删掉，直接在1panel上反代，发现还是很简单的，看有关宝塔的都是建站点然后改Nginx配置文件什么的，1panel就显得很无脑了。

1. 1panel面板中，网站-> 网站 -> 如果是首次操作的话需要安装一下 `OpenResty`
2. 安装好后，创建 -> 反向代理 -> 主域名填入托管在cf上的域名（我用的二级子域名）| 代号随意，符合格式即可 | 代理地址 即为服务器ip:端口号
3. 访问域名配置好了之后就可以开启https访问了
   - 网站设置 -> HTTPS
   - 大部分可以按照默认，HTTP选项我选择的是禁止HTTP访问
   - 证书需要自行配置，这里我的A记录是开了cf代理的，所以直接使用cf中的15年证书
   - SSL选项中，手动导入crt与key即可，设置完成
   - 即可https访问moments

   > cf申请证书流程： 对应域名 -> SSL -> 源服务器 -> 创建证书
   > 将原证书crt与秘钥key保存好（密钥格式PEM）
   >

---

之前部署在claw cloud中的new-api也只能http访问，根据官网文档[doc-自定义域证书](https://docs.run.claw.cloud/clawcloud-run/guide/app-launchpad/custom-domain-certificates) 中可以手动上传ssl证书，crt和key同样也可以使用cf的

证书

另记一则：在使用vim时粘贴内容总是会出现缩进错乱的问题 -> 解决方案：`:set paste` 进入粘贴模式，不过好像还是会出现代码丢失的情况...