---
title: Docker-note
description: Docker学习笔记
publishDate: 2025-06-15
tags:
  - docker
ogImage: /social-card.avif
---



> just for recording the note of docker-study ， to be added

---



<img src="https://pub-2922618b298540fba9bd5a8f8500b762.r2.dev/63996080b1fccdcd36efbb66.jpg.jpeg" alt="img" style="zoom:50%;" />

### Docker框架

Docker是一个CS架构的程序，由两部分组成

- 服务端（server）：Docker守护进程，负责处理Docker指令，管理镜像、容器等
  - 镜像（**Images**）：镜像是创建Docker容器的**只读**模板。包含了运行应用程序所需的一切：应用程序及其所需的依赖、环境、函数库、配置文件
  - 容器（**Container**）：镜像中的应用程序形成后的进程就是`容器`，Docker会给容器做隔离，对外不可见。
- 客户端（client）：通过命令或RestAPI向Docker服务端发送指令，可以在本地或远程向服务端发送指令
- Docker仓库（**Registry**）：集中存储和分发Docker镜像的地方，常见的[Docker Hub](https://hub.docker.com/)，或者国内的阿里云镜像服务

