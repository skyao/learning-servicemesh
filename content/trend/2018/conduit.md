---
title: "2018年Conduit动态"
linkTitle: "Conduit"
weight: 140500
date: 2021-09-23
description: >
  Condoit发布0.5.0版本之后，改名为Linkerd2
---

### 2018-02-01 Conduit 0.2.0 发布

https://github.com/linkerd/linkerd2/releases/tag/v0.2.0

- 新增对 HTTP/1.x 和 TCP 的支持

### 2018-02-22 Conduit 0.3.0 发布

https://github.com/linkerd/linkerd2/releases/tag/v0.3.0

- 主要是改进telemetry
- conduit从*experimental*改为*alpha*

### 2018-04-17 Conduit 0.4.0 发布

https://github.com/linkerd/linkerd2/releases/tag/v0.4.0

- 继续改进telemetry（重点是Prometheus）和服务发现

### 2018-07-05 Conduit 0.5.0 发布

- 新增对 TLS 的支持

### 2018-07-06 博客：Conduit 0.5.0 and the future of Conduit

https://linkerd.io/2018/07/06/conduit-0-5-and-the-future/

> We’re also happy to announce that 0.5.0 will be the last major release of Conduit. Conduit is graduating into the Linkerd project to become the basis of Linkerd 2.0. 
>
> 我们也很高兴地宣布，0.5.0将是Conduit的最后一个主要版本。Conduit将毕业于 Linkerd 项目，成为 Linkerd 2.0的基础。
>
> Why merge Conduit into Linkerd? When we launched Conduit in December 2017, our hypothesis was that we could build a dramatically simpler solution to the problems that we’ve spent the last several years helping Linkerd users tackle: monitoring, reliability, and security of their cloud native applications. Furthermore, we were pretty sure that we could do this using only a small fraction of the system resources that Linkerd requires. But this was a risky move, and it didn’t feel right to our many Linkerd production users to call it “Linkerd” until we were sure it would be successful.
>
> 为什么将Conduit并入Linkerd？当我们在2017年12月推出Conduit时，我们的假设是，我们可以建立一个非常简单的解决方案来解决我们在过去几年中帮助Linkerd用户解决的问题：他们的云原生应用程序的监控、可靠性和安全性。此外，我们非常确定，我们只需使用Linkerd所需系统资源的一小部分就可以做到这一点。但这是一个冒险的举动，对于我们的许多Linkerd生产用户来说，在我们确定它将获得成功之前，将其称为 "Linkerd" 是不合适的。
>
> Happily, after seven months of iterating on Conduit, it’s clear to us that Conduit is worthy of bearing the Linkerd name. Conduit’s lightning-fast Rust proxies are ~10mb per instance, have sub-millisecond p99 latencies, and support HTTP/1.x, HTTP/2, and gRPC. Conduit can be installed in seconds on almost any Kubernetes cluster and applied incrementally to just the services you’re interested in. Conduit’s telemetry support is best in class and, like TLS, comes “for free” without requiring any application changes. Most importantly, the community around Conduit has dramatically ramped up over the past few months, with contributors, production users, and, of course, lots of GitHub stars!
>
> 令人高兴的是，在对Conduit进行了7个月的迭代之后，我们清楚地看到，Conduit值得以Linkerd的名义出现。Conduit的闪电式Rust代理每个实例约10MB，具有亚毫秒级的p99延迟，并支持HTTP/1.x、HTTP/2和gRPC。Conduit可以在几秒钟内安装到几乎所有的Kubernetes集群上，并逐步应用于你感兴趣的服务。Conduit的遥测支持是同类中最好的，而且像TLS一样，"免费"提供，不需要改变任何应用程序。最重要的是，在过去的几个月里，围绕Conduit的社区急剧增加，有贡献者，有生产用户，当然还有很多GitHub star!

具体的合并方式是：

1. `github.com/runconduit/conduit` 仓库被改为 `github.com/linkerd/linkerd2`
2. 数据平面（rust proxy）被拆分到 `github.com/linkerd/linkerd2-proxy` 仓库
3. 合并后，Linkerd 1.x 和 2.x 两条线将继续并行开发。（事实上 Linkerd 1.x 进入维护模式或者废弃）

#### 个人评论

1. 及时止损：linkerd 1.x 版本已经被证实完全不是istio、envoy的对手，继续在 linkerd 1.x 上投入没有意义，Buoyant是一家初创型的小公司，资源有限的情况下必须集中力量主打 Conduit / Linkerd 2.0
2. Conduit 可以理解为是一个原型验证，用了7个月的时间证明了自己，无论是技术选项（rust重写）还是产品形态（servicemesh only & k8s only & security first），可以委以重任，对抗istio和envoy
3. 弃用 Conduit 的名称，继续延用 Linkerd ，可以直接集成 Linkerd 现有的品牌和社区影响力，还有在 CNCF 的位置。毕竟 Linkerd 早就是 CNCF 一员，以 Linkerd2 的名字直接继承会简单的多。这也使得后面 Linkerd2 在2021年7月快速成为 CNCF 的毕业项目，距离此时只有两年半的时间。 

#### 其他评论

[Conduit 0.5发布—以及R.I.P. Conduit](https://www.servicemesher.com/blog/rip-conduit/) (来自崔秀龙):  

> 回想一下，2017 年 12 月 5 日发布到现在的两百多天里，一共发布了 13 个版本、9 篇文档以及 12 篇博客。大致完成了 Conduit 问世之初的承诺：轻量、快速以及 Service Mesh 该有的种种功能；然而很可惜，第一篇 Conduit 博客中还提到了一点：“Conduit is not Linkerd 2.0. ”。这一次“战略性转移”，也印证了之前大家的担心——如果自身投入不足，又不能有效持续制造焦点、获取社区的持续关注和支持，先驱就变成先烈了。
>
> Service Mesh 的鏖战尚未开始，已经有人出局了，R.I.P. Conduit。
