---
title: "2019年Linkerd2动态"
linkTitle: "Linkerd2"
weight: 120600
date: 2021-09-24
description: >
  Linkerd2挑起对抗Istio的重任
---

### 2019-02-13 Linkerd2 2.2.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.2.0

这个稳定版引入了自动请求重试和超时，并将自动注入功能作为一个完全支持的（非实验性）功能而毕业。它增加了几个新的CLI命令，包括 logs 和 endpoints ，为Linkerd的控制平面提供诊断可见性。最后，它引入了两个令人兴奋的实验性功能：一个是加密安全的客户身份头，一个是CNI插件，在部署时避免了对 NET_ADMIN 内核功能的需要。



