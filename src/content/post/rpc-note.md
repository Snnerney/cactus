---
title: 微服务篇 rpc-note
description: rpc笔记
publishDate: 2025-07-25
tags:
  - study
ogImage: /social-card.avif
---

## 什么是rpc

> 像调用本地方法一样，调用远程服务

全程 `remote procedure call` ，远程过程调用，与之相对的是本地调用



### 本地调用

运行在同一个程序（进程）里，A调用B方法，不涉及网络传输

```python
function pay(){
 //业务代码
}
function order(){
 // 前置业务逻辑
 pay();
 // 后置业务逻辑
}

function main(){
order();
}

main();
```



### 远程调用

#### 常规HTTP调用

调用各个模块需要域名才能调用通



#### RPC

在order模块中注册一个payment的client，`client.pay()`建立一个请求rpc连接，实现远程调用。

在order的代码块中，看上去就像是在本地调用一样

<img src="https://pub-2922618b298540fba9bd5a8f8500b762.r2.dev/image-20250725230338775.png" alt="image-20250725230338775" style="zoom:67%;" />

类比http需要解决的问题？

- 函数映射
- 网络传输
  - http的框架库会使用成熟的网络库基于TCP/UDP传输



