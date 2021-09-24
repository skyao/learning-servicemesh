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

### 2018-09-19 博客: Linkerd2.0宣布

https://blog.linkerd.io/2018/09/18/announcing-linkerd-2-0/

> The 2.0 release of Linkerd brings some very significant changes. First, we’ve completely rewritten Linkerd to be orders of magnitude faster and smaller than Linkerd 1.x. Linkerd 2.0’s data plane is comprised of ultralight Rust proxies which consume around 10mb of RSS and have a p99 latency of <1ms. Linkerd’s minimalist control plane (written in Go) is similarly designed for speed and low resource footprint.
>
> Linkerd的2.0版本带来了一些非常重要的变化。首先，我们完全重写了Linkerd，使其比Linkerd 1.x更快更小。Linkerd 2.0的数据平面由超轻量级的Rust代理组成，消耗约10MB的RSS，p99延迟<1ms。Linkerd的极简控制平面（用Go语言编写）也是为速度和低资源占用率而设计的。
>
> Linkerd 2.0 has a ton of other great design goals: a focus on minimal configuration, a modular control plane design, and UNIX-style CLI tools, and we’ll be expanding on those in the future.
>
> Linkerd 2.0还有很多其他伟大的设计目标：专注于最小化配置，模块化控制平面设计，以及UNIX风格的CLI工具，我们将在未来对这些进行扩展。



