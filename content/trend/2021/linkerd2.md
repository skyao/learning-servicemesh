---
title: "2021年Linkerd2动态"
linkTitle: "Linkerd2"
weight: 100100
date: 2021-09-22
description: >
  2021年Linkerd2业界动态跟踪
---

### 2021-06-15 演讲：为什么云计算的未来将会构建在Rust之上？

https://buoyant.io/media/why-the-future-of-the-cloud-will-be-built-on-rust/



### 2021-07-08 CNCF毕业

#### William Morgan的博客

[Announcing Linkerd's Graduation](https://linkerd.io/2021/07/28/announcing-cncf-graduation/)

> For a project that started out as a small wrapper over some open source Twitter libraries and went on to face intense competition from some of the biggest companies in the world, graduation is a significant victory. But not just for Linkerd.
>
> 对于一个一开始只是在一些开源Twitter库上做了一个小包装，后来又面临世界上一些大公司的激烈竞争的项目来说，毕业是一个重大的胜利。但不仅仅是对Linkerd而言。
>
> This is a victory for everyone who has championed the virtues of simplicity and minimalism and rejected the narrative that service meshes must be complex and slow.
>
> 这对每一个拥护简单和极简主义的优点、拒绝服务网必须复杂和缓慢的说法的人来说都是一个胜利。
>
> This is a victory for everyone who has chosen a service mesh based on performance benchmarks, or coherent design principles, or solving concrete problems, rather than relying on vendor marketing or giving into hype cycles.
>
> 对于每一个根据性能基准、或连贯的设计原则、或解决具体问题，而不是依赖供应商的营销或屈从于炒作周期来选择服务网格的人来说，这是一个胜利。



> Linkerd is the first service mesh to rise to the level of graduation. But Linkerd has a long history of firsts: Linkerd was the first service mesh project and the one to coin the term itself. It was the first project to enter the CNCF’s inception (now sandbox) phase. It was the first CNCF project to adopt Rust—a language we believe is the future of the cloud.
>
> Linkerd是第一个上升到毕业水平的服务网格。但是Linkerd有很长的第一历史: Linkerd是第一个服务网状结构项目，也是创造这个术语本身的人。它是第一个进入CNCF初始阶段（现在是沙盒阶段）的项目。它是第一个采用Rust语言的CNCF项目--我们相信这个语言是云计算的未来。
>
> Linkerd adoption has only grown, year after year—not by marketing campaigns but by word of mouth.
>
> Linkerd的采用年复一年地增长--不是靠营销活动，而是靠口碑。

个人评论：

简单说，William 对 Istio（背后的google）以大欺小，长期营销和炒作非常的不满和鄙视，而 linkerd2 的毕业则可以说是出了一口恶气。

#### CNCF的官宣文章

[Cloud Native Computing Foundation Announces Linkerd Graduation](https://www.cncf.io/announcements/2021/07/28/cloud-native-computing-foundation-announces-linkerd-graduation/?hss_channel=tw-3286770860)

中文翻译版本: [CNCF宣布Linkerd正式毕业！](http://dockone.io/article/2434448)

个人评论：

> Inaugural service mesh project used in production by industry leaders like Expedia, JPMC, Microsoft, Nordstrom, and more

从官宣的Linkerd用户看，缺乏重量级用户和使用案例是linkerd2落地的大问题（虽然列出来了Microsoft但我很质疑微软实际使用的范围和数量），社区支持度相比istio实在是太可怜。

> It was the first service mesh project and the first CNCF project to adopt the Rust programming language to improve security and performance. 

Linkerd2率先使用rust，并将rust在网络编程方面的生态提升到新的层次，可谓功不可没，非常令人配置。Linkerd2的开发团队的工程能力非常令人敬佩。

> We didn’t choose a service mesh based on hype. My teams weren’t worried about which mesh had the most marketing behind it. 

这是在讽刺 Istio？ CNCF官方文章，这么明显的奚落Istio，非常有趣。

> Linkerd is working on an extensive roadmap, including server and client-side policies, “mesh expansion” to allow the Linkerd data plane to operate outside of Kubernetes, and much more. 

终于要开始支持 k8s 之外的部署了。



