---
title: "(2021)服务网格除了 Istio，其实你还可以有其它 8 种选择"
linkTitle: "服务网格的9种选择"
weight: 1480
date: 2021-10-29
description: >
  介绍 9 种较受欢迎的用以支撑微服务开发的服务网格框架，每种方案都给出了其适用场景。
---

## 前言

9 open-source service meshes compared

[Bill Doerrfeld](https://techbeacon.com/contributors/bill-doerrfeld), Consultant, Doerrfeld.io

https://techbeacon.com/app-dev-testing/9-open-source-service-meshes-compared

服务网格除了 Istio，其实你还可以有其它 8 种选择

https://z.itpub.net/article/detail/91AA8B3895CE8F037D73675116731CED

---------

哪种服务网格最适合你的企业？近年来，Kubernetes 服务网格框架数量增加迅速，使得这成为一个棘手的问题。

下面将介绍 9 种较受欢迎的用以支撑微服务开发的服务网格框架，每种方案都给出了其适用场景。

## 什么是服务网格

服务网格近年来有很高的话题度，背后的原因是什么？

微服务已经成为一种灵活快速的开发方式。然而，随着微服务数量成倍数地增长，开发团队开始遇到了部署和扩展性上的问题。

容器和 Kubernetes 这样的容器编排系统 ，将运行时和服务一起打包进镜像，调度容器到合适的节点，运行容器。这个方案可以解决开发团队遇到的不少问题[1]。然而，在这个操作流程中仍存在短板：如何管理服务间的通信。

在采用服务网格的场景下，以一种和应用代码解耦的方式，增强了应用间统一的网络通信能力。服务网格扩展了集群的管理能力，增强可观测性、服务发现、负载均衡、IT 运维监控及应用故障恢复等功能。

## 服务网格概览

服务网格一直有很高的热度。正如 Linkerd 的作者 William Morgan 所提到[2]的：“服务网格本质上无非就是和应用捆绑在一起的用户空间代理。” 此说法相当简洁，他还补充道，“如果你能透过噪音看清本质，服务网格能给你带来实实在在的重要价值。”

Envoy 是许多服务网格框架的核心组件，是一个通用的开源代理，常被用于 Pod 内的 sidecar 以拦截流量。也有服务网格使用另外的代理方案。

若论具体服务网格方案的普及程度，Istio 和 Linkerd 获得了更多的认可。也有其它可选项，包括 Consul Connect，Kuma，AWS App Mesh和OpenShift。下文会阐述9种服务网格提供的关键特性。

### Istio

Istio 是基于 Envoy 构建的一个可扩展的开源服务网格。开发团队可以通过它连接、加密、管控和观察应用服务。Istio 于 2017 年开源，目前 IBM、Google、Lyft 仍在对其进行持续维护升级。Lyft 在 2017 年把 Envoy 捐赠给了 CNCF。

Istio 花了不少时间去完善增强它的功能特性。Istio 的关键特性包括负载均衡、流量路由、策略创建、可度量性及服务间认证。

Istio 有两个部分组成：数据平面和控制平面。数据平面负责处理流量管理，通过 Envoy 的 sidecar 代理来实现流量路由和服务间调用。控制平面是主要由开发者用来配置路由规则和观测指标。

Istio 观测指标是细粒度的属性，其中包含和服务行为相关的特定数据值。下面是个样例：

```yaml
request.path: xyz/abc 
request.size: 234 
request.time: 12:34:56.789 04/17/2017 
source.ip: [192 168 0 1] 
destination.service.name: example
```

与其他服务网格相比，Istio 胜在其平台成熟度以及通过其 Dashbaord

着重突出的服务行为观测和业务管理功能，然而也因为这些高级特性和复杂的配置流程，Istio 可能并不如其它一些替代方案那样容易上手。

### Linkerd

按照官网的说法，Linkerd 是一个轻量级、安全优先的 Kubernetes 服务网格。它的创建流程快到让人难以置信（据称在 Kubernetes 安装只需要 60 秒），这是大多数开发者喜闻乐见的。Linkerd 并没有采用基于 Envoy 的构建方案。而是使用了一个基于 Rust 的高性能代理 linkerd2-proxy，这个代理是专门为 Linkerd 服务网格编写的。

Linkerd 由社区驱动，是 100% 的 Apache 许可开源项目。它还是 CNCF 孵化项目。Linkerd 始于 2016 年，维护者也花了不少时间去解决其中的缺陷。

使用 Linkerd 服务网格，应用服务可以增强其可靠性、可观测性及其在 Kubernetes 上部署的安全性。举个例子，可观测性的增强可以帮助用户解决服务间的延迟问题。使用 Linkerd 不要求用户做很多代码调整或是花费大量时间写 YAML 配置文件。可靠的产品特性和正向的开发者使用回馈，使得 Linkerd 成为服务网格中一个强有力的竞争者。

### Consul Connect

Consul Connect 是来自 HashiCorp 的服务网格，专注于路由和分段，通过应用级的 sidecar 代理来提供服务间的网络特性。Consult Connect 侧重于应用安全，提供应用间的双向 TLS 连接以实现授权和加密。

Consult Connect 独特的一点是提供了两种代理模式。一种是它内建的代理，同时它还支持 Envoy 方案。Connect 强调可观测性，集成了例如 Prometheus 这样的工具来监控来自 sidecar 代理的数据。Consul Connect 可以灵活地满足开发者使用需求。比如，它提供了多种方式注册服务：可以从编排系统注册，可以通过配置文件，通过 API 调用，或是命令行工具。

### Kuma

Kuma 来源于 Kong，自称是一个非常好用的服务网格替代方案。Kuma 是一个基于 Envoy 的平台无关的控制平面。Kuma 提供了安全、观测、路由等网络特性，同时增强了服务间的连通性。Kuma 同时支持 Kubernetes 和虚拟机。

Kuma 让人感兴趣的一点是，它的企业版可以通过一个统一控制面板来运维管理多个互相隔离独立的服务网格。这项能力可以满足安全要求高的使用场景。既符合隔离的要求，又实现集中控制。

Kuma 也是相对容易安装的一个方案。因为它预先内置了不少策略。这些策略覆盖了常见需求，例如路由，双向 TLS，故障注入，流量控制，加密等场景。

Kuma 原生兼容 Kong，对于那些已经采用 Kong API 管理的企业组织，Kuma 是个非常自然而然的候选方案。

### Maesh

Maesh 是来自 Containous 的容器原生的服务网格，标榜自己是比市场其它服务网格更轻量级更易用的方案。和很多基于 Envoy 构建的服务网格不同，Maesh 采用了 Traefik， 一个开源的反向代理和负载均衡器。

Maesh 并没有采用 sidecar 的方式进行代理，而是在每个节点部署一个代理终端。这样做的好处是不需要去编辑 Kubernetes 对象，同时可以让用户有选择性地修改流量，Maesh 相比其他服务网格侵入性更低。Maesh 支持的配置方式：在用户服务对象上添加注解或是在服务网格对象上添加注解来实现配置。

实际上，SMI 是一种新的服务网格规范格式，对 SMI 的支持 Maesh 独有的一大亮点。随着 SMI 在业界逐渐被采用，可以提高可扩展性和减缓供应商绑定的担忧。

Maesh 要求 Kubernetes 1.11 以上的版本，同时集群里安装了 CoreDNS/KubeDNS。这篇安装指南[3]演示了如何通过 Helm v3 快速安装 Maesh。

```bash
$ helm repo add maesh https://containous.github.io/maesh/charts 
$ helm repo update 
$ helm install maesh maesh/maesh
```

### ServiceComb-mesher

Apache 软件基金会形容旗下的 ServiceComb-mesher “是一款用 Go 语言实现的高性能服务网格”。Mesher 基于一个非常受欢迎的 Go 语言微服务开发框架 Go Chassis[4] 来设计实现。因此，它沿袭了 Go Chassis 的一些特性如服务发现、负载均衡、错误容忍、路由管理和分布式追踪等特性。

Mesher 采用了 sidecar 方式；每个服务有一个 Mesher sidecar 代理。开发人员通过 Admin API 和 Mesher 交互，查看运行时信息。Mesher 同时支持 HTTP 和 gRPC，可快速移植到不同的基础设施环境，包括 Docker、Kubernetes、虚拟机和裸金属机环境。

### Network Service Mesh（NSM）

Network Service Mesh（NSM）是一款专门为 telcos 和 ISPs 设计的服务网格。它提供了一层级用以增强服务在 Kubernetes 的低层级网络能力。NSM 目前是 CNCF 的沙箱项目。

根据 NSM 的文档说明，“经常接触 L2/L3 层的网络运维人员抱怨说，适合他们的下一代架构的容器网络解决方案几乎没有”。

因此，NSM 在设计时就考虑到一些不同使用场景，尤其是网络协议不同和网络配置混杂的场景。这使得 NSM 对某些特殊场景具备相当吸引力，例如边缘计算、5G 网络和 IOT 设备等场景。NSM 使用简单直接的 API 接口去实现容器和外部端点的之间的通信。

和其他服务网格相比，NSM 工作在另一个不同的网络层。VMware 形容 NSM“专注于连接”。GitHub 的文档[5]演示了 NSM 是如何与 Envoy协同工作的。

### AWS App Mesh

AWS APP Mesh 为开发者提供了“适用于不同服务的应用层的网络”。它接管了服务的所有网络流量，使用开源的 Envoy 代理去控制容器的流量出入。AWS App Mesh 支持 HTTP/2 gRPC。

AWS App Mesh 对于那些已经将容器平台深度绑定 AWS 的公司而言，会是相当不错的服务网格方案。AWS 平台包括 AWS Fargate，Amazon Elastic Container Service，Amazon Elastic Kubernetes Service（EKS），Amazon Elastic Compute Cloud（EC2），Kubernetes on EC2，包括 AWS App Mesh 不需要付额外费用。

AWS App Mesh 和 AWS 生态内的监控工具无缝兼容。这些工具包括 CloudWatch 和 AWS X-Ray，以及一些来自第三方供应商的工具。因为 AWS 计算服务支持 AWS Outposts，AWS App Mesh 可以和混合云和已经部署的应用良好兼容。

AWS App Mesh 的缺点可能是使得开发者深度绑定了单一供应商方案，相对闭源，可扩展性缺失。

### OpenShift Service Mesh by Red Hat

OpenShift 是来自红帽的一款帮助用户“连接、管理、观测微服务应用”的容器管理平台。OpenShift 预装了不少提升企业能力的组件，也被形容为企业级的混合云 Kubernetes 平台。

OpenShift Service Mesh 基于开源的 Istio 构建，具备 Isito 的控制平面和数据平面等特性。OpenShift 利用两款开源工具来增强 Isito 的追踪能力和可观测性。OpenShift 使用 Jaeger 实现分布式追踪，更好地跟踪请求是如何在服务间调用处理的。

另一方面，OpenShift 使用了 Kiali 来增强微服务配置、流量监控、跟踪分析等方面的可观测性。

## 如何选择

正如文中所提到的，可供选择的服务网格方案[6]有很多，同时还有新的方案在涌现。当然，每一种方案在技术实现上都略有不同。选择一款合适的服务网格，主要考虑的因素包括，你能接受它带来多大的侵入性，它的安全性如何，以及平台成熟度等。

以下几点可以帮助 DevOps 团队选择一款适合他们场景的服务网格：

- 是否依赖Envoy。Envoy 有一个活跃的社区生态。开源，同时是许多服务网格的底座。Envoy 具备的丰富特性使得其成为一个很难绕过的因素。
- 具体使用场景。服务网格为微服务而生。如果你的应用是一个单体的庞然大物，那你在服务网格上的投入可能达不到预期的收益。如果不是所有应用都部署在 Kubernetes，则应该优先考虑平台无关的方案。
- 现有容器管理平台。有些企业已经使用了特定供应商的生态来解决容器编排问题，例如 AWS 的 EKS，红帽的 OpenShift，Consul。沿袭原有的生态，可以继承并拓展原有的特性。而这些可能是开源方案所不能提供的。
- 所在行业。许多服务网格不是为特定行业专门设计的。Kuma 统一管理多个隔离服务网格的能力可能更适用于收到高度管制的金融行业。底层网络 telcos 和 ISPs 则更应该考虑 Network Service Mesh。
- 对可视化的要求。可观测性是服务网格的核心能力之一。考虑进一步定制和更深度能力的团队应该优先考虑 Istio 或 Consul。
- 是否遵循开发标准。遵循开发标准使得你的平台更具备前瞻性和可扩展性。这使得企业会倾向于采用支持 SMI 的方案，Maesh 或其他基金会孵化的项目如 Linkerd。
- 是否重视用户体验。考虑运维人员的易用性是评判新工具的关键指标。这方 Linkerd 似乎在开发者中间口碑不错。
- 团队准备。评估你的团队所具备的资源和技术储备，在技术选型时决定你们适合用基于 Envoy 的 Istio，或是供应商抽象封装的方案，例如 OpenShift。

这些考虑因素没有覆盖到全部场景。此处仅是抛砖引玉，引起读者的思考。希望读完上面所列的服务网格清单，和相关的决策因素之后，你们的团队能找到新的方法去改善微服务应用的网络特性。

相关链接：

1. https://techbeacon.com/app-dev-testing/3-reasons-why-you-should-always-run-microservices-apps-containers
2. https://buoyant.io/service-mesh-manifesto/
3. https://docs.mae.sh/quickstart/
4. https://github.com/go-chassis/go-chassis
5. https://github.com/networkservicemesh/examples/tree/master/examples/envoy_interceptor
6. https://techbeacon.com/app-dev-testing/make-your-app-architecture-cloud-native-service-mesh

