---
title: Deno反代llm-api
description: llm
publishDate: 2025-03-19
tags:
  - llm
ogImage: /social-card.avif
---
在国内无法直接调用.../oai/Gemini/Claude-API，所以可以采用代理.../oai/Gemini/ClaudeGemini的方式来调用 **OR** 自部署中转站点如：`new-api`等

1. 注册/登录 Deno
2. 创建新项目
3. 填入仓库中的源码
   
    [api-proxy.js](https://gist.github.com/ZX-11/edc4e6b4654c4ef19fd89199455e3292)
    
4. 运行部署，若显示 `Service is running` 就代表部署成功
5. 在 `Domains` 中添加自己的域名，按照提示去托管的cf中添加DNS记录，或者去域名服务商添加
6. eg：在Cherry Studio中选择提供商provider为 `Gemini` ，或者新建-类型选择Gemini-填入api地址（就是你的自定义域名 + `/gemini`）和key（去ai studio中获取）
7. 管理模型，添加模型，测试检查 done

---
<details>

<summary>some-questions</summary>

- 自定义域名是出于稳定性和速度的考虑，也方便记忆

</details>

文章参考引用：

> https://linux.do/t/topic/359495
