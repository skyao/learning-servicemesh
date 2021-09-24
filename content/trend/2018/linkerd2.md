---
title: "2018年Linkerd2动态"
linkTitle: "Linkerd2"
weight: 140600
date: 2021-09-24
description: >
  Linkerd2挑起对抗Istio的重任
---

### 2018-07-18 Linkerd2 18.7.1 发布

https://github.com/linkerd/linkerd2/releases/tag/v18.7.1

Linkerd2的第一个版本。

### 2018-08-01 Linkerd2 18.7.3 发布

https://github.com/linkerd/linkerd2/releases/tag/v18.7.3

- 完成从Conduit到Linkerd2的品牌转变
- 性能改进，优化cpu使用率约20%

### 2018-09-18 Linkerd2 edge-18.9.2 发布

https://github.com/linkerd/linkerd2/releases/tag/edge-18.9.2

- 从这个版本开始，按照 edge 和 stable 划分发布通道

### 2018-09-19 Linkerd2 stable-2.0.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.0.0

这是Linkerd 2.0的第一次GA发布! 

### 2018-09-19 博客: Linkerd2.0发布

https://blog.linkerd.io/2018/09/18/announcing-linkerd-2-0/

> The 2.0 release of Linkerd brings some very significant changes. First, we’ve completely rewritten Linkerd to be orders of magnitude faster and smaller than Linkerd 1.x. Linkerd 2.0’s data plane is comprised of ultralight Rust proxies which consume around 10mb of RSS and have a p99 latency of <1ms. Linkerd’s minimalist control plane (written in Go) is similarly designed for speed and low resource footprint.
>
> Linkerd的2.0版本带来了一些非常重要的变化。首先，我们完全重写了Linkerd，使其比Linkerd 1.x更快更小。Linkerd 2.0的数据平面由超轻量级的Rust代理组成，消耗约10MB的RSS，p99延迟<1ms。Linkerd的极简控制平面（用Go语言编写）也是为速度和低资源占用率而设计的。
>
> Linkerd 2.0 has a ton of other great design goals: a focus on minimal configuration, a modular control plane design, and UNIX-style CLI tools, and we’ll be expanding on those in the future.
>
> Linkerd 2.0还有很多其他伟大的设计目标：专注于最小化配置，模块化控制平面设计，以及UNIX风格的CLI工具，我们将在未来对这些进行扩展。

### 2018-12-07 Linkerd2 stable-2.1.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.1.0

主要的改进包括: 每线路的指标、service profile和大为改进的仪表盘用户界面。它还增加了几个重要的实验性功能，包括代理自动注入、单一命名空间安装，以及控制平面的高可用性模式。

### 2018-12-06 博客: Linkerd2.1发布

https://linkerd.io/2018/12/06/announcing-linkerd-2-1/

> **Per-route metrics**
>
> In 2.1, Linkerd can now provide metrics not just at the service level but at the *route* level. This means that Linkerd can reveal failures, slowdowns, or changes in traffic levels to a particular API call in a service.
>
> 在2.1中，Linkerd现在不仅可以提供服务层面的指标，还可以提供路由层面的指标。这意味着Linkerd可以揭示服务中某一特定API调用的故障、减速或流量水平的变化。
>
> **Service Profiles**
>
> Linkerd 2.1 introduces the concept of the service profile, a lightweight way of providing information about a service to Linkerd. This information includes the service’s routes, i.e. the API calls that it is expected to respond to, and the way that Linkerd should treat these routes. (As a side note, service profiles are implemented as a Kubernetes CRD, bringing the grand total of Linkerd-created Kubernetes CRDs to 1.)
>
> Linkerd 2.1引入了服务配置文件的概念，这是一种向Linkerd提供服务信息的轻量级方式。这些信息包括服务的路由，即它应该响应的API调用，以及Linkerd应该如何处理这些路由。(作为附带说明，服务配置文件作为Kubernetes CRD实现，使Linkerd创建的Kubernetes CRD总数达到1)。
>
> Service profiles are a very exciting addition because they provide a fundamental building block for the project: the ability to configure Linkerd’s behavior on a per-service basis. In upcoming releases, we’ll be adding many features built on service profiles, including retries, circuit breaking, rate limiting, and timeouts.
>
> 服务配置文件是一个非常令人兴奋的补充，因为它们为项目提供了一个基本的构建块：在每个服务的基础上配置Linkerd行为的能力。在即将发布的版本中，我们将增加许多基于服务配置文件的功能，包括重试、断路、速率限制和超时。
>
> Service profiles are also a great demonstration of the design philosophy behind Linkerd 2.x. By attaching configuration at the service level, rather than globally, we ensure that Linkerd continues to be incrementally adoptable—one service at a time. And, of course, Linkerd continues to just work out of the box even if no service profiles are specified.
>
> 服务配置文件也是Linkerd 2.x背后的设计理念的一个很好的证明。通过在服务层面附加配置，而不是全局配置，我们确保Linkerd继续是可逐步采用的，一次一个服务。当然，即使没有指定服务配置文件，Linkerd也会继续开箱即用。

