---
title: ai-不完全白嫖指南
description: ai-不完全白嫖指南 | 具有时效性，更新日期3/25/2025
publishDate: 2025-03-25
tags:
  - llm
ogImage: /social-card.avif
---
## 1.DeepSeek V3 0324
- [DeepSeek: DeepSeek V3 0324 (free) -- OpenRouter](https://openrouter.ai/deepseek/deepseek-chat-v3-0324:free/api)
- [chute](https://chutes.ai/app/chute/154ad01c-a431-5744-83c8-651215124360)(3.25仅需输入用户名即可登录，且v3-0324暂不收费）

## 2.DeepSeek-R1
- 官网时不时繁忙，可在低峰期适量使用，或可选择API充值（[DeepSeek-API](https://platform.deepseek.com/top_up)）
- Azure（学生认证100\$免费额度/绑定信用卡200\$）
- 火山引擎（实名）
- 魔搭社区（需需绑定阿里云账号）
- [硅基流动](https://siliconflow.cn/zh-cn/)（需手机号，可邀请获赠金，但是被刷得太猛了，速度一般）
- [Nvidia](https://build.nvidia.com/deepseek-ai/deepseek-r1)

## 3.Gemini 

> 模型介绍：[gemini-api|docs](https://ai.google.dev/gemini-api/docs/models?hl=zh-cn)
<details>

<summary>模型版本名称模式 | 为方便查看，将文档部分内容粘贴至此：</summary>
Gemini 模型有*预览版*和*稳定版*两种版本。

- **最新**：指向指定生成和变体的尖端模型版本。底层模型会定期更新，并且可能是预览版。只有探索性测试应用和原型才应使用此别名。
            
  最新版本格式：`<model>-<generation>-<variation>-latest`。例如 `gemini-1.0-pro-latest`。
- **最新稳定版**：指向为指定的模型生成和变体发布的最新稳定版。
            
  最新的稳定版本：`<model>-<generation>-<variation>`。例如 `gemini-1.0-pro`。
  
- **稳定**：指向特定的稳定模型。稳定型模型通常不会发生变化。大多数正式版应用都应使用特定的稳定型模型。
            
  稳定版本模式：`<model>-<generation>-<variation>-<version>`。例如 `gemini-1.0-pro-001`。

- **实验性**：指向实验性模型（不适用于生产环境）。官方发布实验性模型是为了收集反馈、快速将最新动态交到开发者手中，并突出展示 Google 的创新步伐。

  实验版本格式：`<model>-<generation>-<variation>-<version>`。例如 `gemini-2.0-pro-exp-02-05`。

</details>
            
- 官网（除了deepsearch功能外，没有api和ai studio好用，时不时会抽风）
- [ai studio](https://aistudio.google.com/)

## 4.ChatGPT
- 官网/官方API（~~expensive~~）/官转or逆向API

## 5.Claude
- 官网（不支持大陆手机号|需接码，额度也少🥲，但代码能力强）
- 其他提供api的平台（OpenRouter）自费购买
- cursor等代码辅助工具（疑似降智）

大模型集成（以上模型均包含，有一定免费额度）：

1. [poe](https://poe.com/)
2. [OpenRouter](https://openrouter.ai/)

---

另外科普一下模型速率限制： — 参考 Gemini API文档

速率限制是根据以下三个维度衡量的：

- 每分钟请求数 (**RPM**)
- 每分钟令牌数 (**TPM**)
- 每日请求次数 (**RPD**)

eg：Gemini模型的费率限制如下：（中文版的文档 rpm翻译成了每千次展示收入了… 转为英文文档才懂）

![](https://raw.githubusercontent.com/Snnerney/image/refs/heads/main/image.png)
