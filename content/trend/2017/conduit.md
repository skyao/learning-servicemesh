---
title: "2017年Conduit动态"
linkTitle: "Conduit"
weight: 140500
date: 2021-09-23
description: >
  2017年Conduit业界动态跟踪
---

### 2017-12-05 Conduit 0.1.0 发布

https://github.com/linkerd/linkerd2/releases/tag/v0.1.0

- 仅支持HTTP2(后续版本增加了对HTTP1.1的支持)
- 仅仅支持k8s部署（到2021年都只支持k8s）

### 2017-12-05 博客：Introducing Conduit

https://linkerd.io/2017/12/05/introducing-conduit/

> We’ve built Conduit from the ground up to be the fastest, lightest, simplest, and most secure service mesh in the world. It features an incredibly fast and safe data plane written in Rust, a simple yet powerful control plane written in Go, and a design that’s focused on performance, security, and usability. Most importantly, Conduit incorporates the many lessons we’ve learned from over 18 months of production service mesh experience with Linkerd.
>
> 我们从头开始打造Conduit，使其成为世界上最快、最轻、最简单、最安全的服务网格。它的特点是用Rust编写的令人难以置信的快速和安全的数据平面，用Go编写的简单而强大的控制平面，以及专注于性能、安全性和可用性的设计。最重要的是，Conduit融合了我们从Linkerd超过18个月的生产服务网格经验中获得的许多教训。
>
> One thing we’ve learned is that there are deployment models where Linkerd’s resource footprint is simply too high. While Linkerd’s building blocks—widely-adopted, production-tested components like Finagle, Netty, Scala, and the JVM—allow Linkerd scale *up* to incredibly high workloads when given lots of CPU and RAM, they aren’t designed to scale *down* to environments that have limited resources—in particular, to sidecar-based Kubernetes deployments. So, earlier this year, we asked ourselves: if we could build the ideal service mesh, focused on ultra-low-resource environments, but *with* the benefit of everything we’ve learned from 18 months of production service mesh experience—what would we build?
>
> 我们学到的一点是，在某些部署模式下，Linkerd的资源占用率太高。虽然Linkerd的构建模块--广泛采用的、经过生产测试的组件，如Finagle、Netty、Scala和JVM--允许Linkerd在有大量CPU和内存的情况下扩展到令人难以置信的高工作负载，但它们并不是为了扩展到资源有限的环境--尤其是基于sidecar的Kubernetes部署。因此，今年早些时候，我们问自己：如果我们能建立一个理想的服务网格，专注于超低资源环境，但受益于我们从18个月的生产服务网经验中学到的一切，我们会建立什么？
>
> The answer is Conduit. Conduit is a next generation service mesh that makes microservices safe and reliable. Just like Linkerd, it does this by transparently managing the runtime communication between services, automatically providing features for observability, reliability, security, and flexibility. And just like Linkerd, it’s deployed as a data plane of lightweight proxies that run alongside application code, and a control plane of highly available controller processes. Unlike Linkerd, however, Conduit is explicitly designed for low resource sidecar deployments in Kubernetes.
>
> 答案是Conduit。Conduit是下一代服务网格，使微服务安全可靠。就像Linkerd一样，它通过透明地管理服务之间的运行时通信，自动提供可观察性、可靠性、安全性和灵活性等功能来做到这一点。就像Linkerd一样，它被部署为一个轻量级代理的数据面，与应用程序代码一起运行，以及一个高可用的控制器进程的控制面。然而，与Linkerd不同的是，Conduit是明确为Kubernetes中的低资源sidecar部署而设计的。

Conduit的特点：

> **Blazingly fast and lightweight**
> A single Conduit proxy has a sub-millisecond p99 latency and runs with less than 10mb RSS.
> **惊人的速度和重量**
> 单一的Conduit代理的p99延迟为亚毫秒级，并以低于10MB的RSS运行。
>
> **Built for security**
> From Rust’s memory safety guarantees to TLS by default, we’re focused on making sure Conduit has security in mind from the very beginning.
> **为安全而构建**
> 从 Rust 的内存安全保证到默认的TLS，我们专注于确保 Conduit 从一开始就考虑到安全性。
>
> **Minimalist**
> Conduit’s feature set is designed to be as minimal and as composable as possible, while allowing customization through gRPC plugins.
> **极简主义**
> Conduit 的功能集被设计为尽可能的简约和可组合，同时允许通过 gRPC 插件进行定制。

