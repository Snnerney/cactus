---
title: 如何快速找到需要的资源or解决方案
description: 如何快速找到答案
publishDate: 2025-03-30
ogImage: /social-card.avif
---
### 1.其一是我觉得是要学会如何提问，准确的提问可以避免时间的浪费

> [How-To-Ask-Questions-The-Smart-Way](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/main/README-zh_CN.md)

> [你会问问题吗？- CoolShell](https://coolshell.cn/articles/3713.html)

刚进入L站时经常会碰到不懂的名词，如alist、ollama、硅基、apikey、new-api、DeepL、多模态、prompt…

但直接提问这些是什么肯定不是一个明智的选择

1. 根据左耳朵耗子老师在文中提到的：在正确的地方做正确的事情，L站虽然不是linux开发社区（雾），但是人工智能领域很突出，起初论坛也是靠pandora项目起家的，所以在L站搜索ai相关内容再合适不过，如果是编程相关问题，去stackoverflow寻找答案或许更好。如果不确定是什么问题，直接google会比较好（不要用baidu,可以选择bing）
2. 先根据现有的关键词去搜索信息，比如我想知道如何使用api-key，就根据关键字搜索，可能会出现回复提到一些工具譬如cherry或者openweb-ui等等..，我再根据这些关键字搜索，去了解这些工具的用途和使用方法。如果经过这些步骤搜不到的话再去提问。
3. 如果在操作过程中出现了问题，可以爬楼或者翻译错误信息尝试先自己解决
4. 如果还是没有找到解决办法时，可以将自己的尝试步骤和错误信息一一列出，发帖礼貌询问，这样既缩窄提问范围，节省了回复一些疑问的时间，也能让答主更加了解你的需求，从而更好更快得解决问题。
5. 根据自己的踩坑经验，去帮助这方面的小白。感觉有点费曼学习法的意思，不仅帮助了他人，也许还会让自己收获更多意想不到的内容

本人在AI使用方面，从开始只会网页傻瓜式操作，作为一个从未用过api的小白，在经过几个月的学习后，已经慢慢摸到了一些门槛；
同时在逛论坛的时候找到了不少好用的工具（listary快速启动工具或网站、quicker、cherry多模型api服务、ndm/idm多线程下载等）来提升自己的上网舒适度。

### 2.搜索引擎进阶使用：更精准地获取所需信息

掌握一些高级搜索技巧，可以帮助我们从海量信息中更快、更准确地找到所需内容，大幅提升搜索效率。
个人觉得常用的关键词如下，让ai整理了一下直接贴图吧
![](/assets/images/quicker_20250330_185442.png)

### 3.AI方面，除了直接在网页提问，还有什么方式呢

调用API，除了各大官方的api（ds、gpt、claude…）还有很多三方的api，譬如字节的火山引擎、Azure（学生认证可获得100刀免费额度，可用于部署ai）、阿里魔搭、硅基流动等等 + prompt 

网页端直接发送prompt和调用api设置sys prompt有什么区别呢？

直接在网页端（例如 Gemini）输入提示词，而不是在设置中设置持久化的提示词 (Prompt Engineering) ，效果通常会更差一些。 原因如下：

![](/assets/images/quicker_20250330_190115.png)
