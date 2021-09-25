---
title: "2020年Linkerd2动态"
linkTitle: "Linkerd2"
weight: 110600
date: 2021-09-25
description: >
  Linkerd2在2020年主要改进了加密，支持k8s多集群
---

### 2020-02-07 Linkerd2 2.7.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.7.0

这个版本增加了对Linkerd的PKI与外部证书颁发者（如cert-manager）集成的支持，并在总体上简化了证书轮换过程。

这个版本还包括对仪表盘的性能改进，减少代理的内存使用，对Helm图表的各种改进，以及更多更多。

个人小结：改善加密功能

### 2020-06-10 Linkerd2 2.8.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.8.0

这个版本为Linkerd引入了新的多集群扩展，允许它在 Kubernetes 集群间建立安全的连接。

这对应用程序来说是透明的，并能与任何网络拓扑结构一起工作。

个人小结：新增对k8s多集群扩展的支持

### 2020-11-07 Linkerd2 2.9.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.9.0

这个版本将Linkerd的零配置双向TLS（mTLS）支持扩展到所有的TCP连接，允许Linkerd在安装时透明地加密和验证集群中的所有TCP 连接。它还增加了对ARM的支持。引入了一个新的多核代理运行时，以获得更高的吞吐量，增加了对Kubernetes服务拓扑结构的支持。

个人小结：改进mTLS，改善性能

