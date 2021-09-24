---
title: "2016年Linkerd动态"
linkTitle: "Linkerd"
weight: 150200
date: 2021-09-22
description: >
  Linkerd成为第一个Servicemesh产品
---

{{% pageinfo color="primary" %}}
2016年1月15日，离开twitter的基础设施工程师William Morgan和Oliver Gould，在github上发布了linkerd 0.0.7版本，他们同时组建了一个创业小公司Buoyant，业界第一个Service Mesh项目诞生。
{{% /pageinfo %}}

## 年度动态

### 2016-01-15 Linkerd 0.0.7 发布

https://github.com/linkerd/linkerd/releases/tag/release-0.0.7

> linkerd is a dynamic linker for distributed applications (aka "microservices"). In the same way that `ld` binds software components (libraries), linkerd binds services by mediating inter-service communication (RPC).
>
> linkerd是一个用于分布式应用（又称"微服务"）的动态链接器。与`ld`绑定软件组件（库）的方式相同，linkerd通过调解服务间通信（RPC）来绑定服务。

协议支持：

- http
- thrift(实验性)
- mux(实验性)

namer（服务发现）支持：

- 基于文件系统的服务发现（应该是用于开发阶段）
- kubernetes(实验性)

### 2016-01-18 博客：Linkerd和Twitter的关系

[Linkerd: Twitter-style Operability for Microservices](https://linkerd.io/2016/02/18/linkerd-twitter-style-operability-for-microservices/)

备注：这是linkerd的第一篇博客文章。

> Happily, a tremendous amount of that knowledge was already encoded in an open-source project called [Finagle](https://finagle.github.io/), the high-throughput RPC library that powers Twitter’s microservice architecture.
>
> 令人高兴的是，大量的知识已经编码在一个名为 [Finagle](https://finagle.github.io/) 的开源项目中，这是一个为Twitter的微服务架构提供动力的高吞吐量RPC图书馆。
>
> Finagle is Twitter’s core library for managing the communication between services. Practically every online service at Twitter is built on Finagle, and it powers millions upon millions of RPC calls every second. 
>
> Finagle 是 Twitter 管理服务间通讯的核心类库。Twitter 上几乎每一项在线服务都建立在 Finagle 上， 每秒钟为数百万个 RPC 调用提供支持。
>
> Today, we’re happy to announce a small step towards our vision of making Finagle usable by the masses. **[Linkerd](https://linkerd.io/)** has hit 0.1.0
>
> 今天，我们高兴地宣布，我们朝着让 Finagle 为大众所利用的愿景迈出了一小步。Linkerd 已经达到 0.1.0。
>
> **Linkerd** is our open-source *service mesh* for cloud-native applications. It’s built directly on Finagle...
>
> **Linkerd** 是我们的开源 *service mesh*，用于云原生应用程序。它直接建立在Finagle上......

### 2016-01-31 Linkerd 0.0.8发布

https://github.com/linkerd/linkerd/releases/tag/release-0.0.8

- 支持 Zookeeper
- 支持服务器端TLS

### 2016-02-10 Linkerd 0.0.10发布

- 支持端到端的TLS

### 2016-02-18 Linkerd 0.1.0发布

- 引入基于Marathon的服务发现，用于Mesos平台
- 更新到 Finagle 6.33

### 2016-03-31 Linkerd 0.3.0发布

- 增加 namerd 服务

### 2016-04-14 Linkerd 0.3.1发布

- 支持zipkin
- 完善namerd

### 2016-04-29 Linkerd 0.4.0发布

- 继续完善namerd和dtab
- 新的dashboard

### 2016-05-11 Linkerd 0.5.0发布

- 继续完善trace和dtab
- 支持retry
- 支持prometheus

### 2016-05-25 Linkerd 0.6.0发布

- 完善ZooKeeper的支持

### 2016-06-29 Linkerd 0.7.0发布

- 完善HTTP的支持
- 完善timeout/zookeeper/dashboard的支持

### 2016-07-29 Linkerd 0.7.2发布

- 支持consul

### 2016-07-29 Linkerd 0.8.0发布

- 完善consul、trace的支持

### 2016-10-18 Linkerd 0.8.2发布

- 引入http2、grpc的支持（实验性）

## 年度总结

2016年1月15日，linkerd 在github发布第一个版本0.0.7。2016年下半年，Linkerd陆续发布了0.8和0.9版本，开始支持HTTP/2 和gRPC，1.0发布在即；
并在2016年底开始申请加入CNCF。