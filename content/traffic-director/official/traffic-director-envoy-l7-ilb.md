---
date: 2018-10-07T11:00:00+08:00
title: Presentation：Traffic Director & Envoy-Based L7 ILB
weight: 1016
menu:
  main:
    parent: "traffic-director-official"
description : "Traffic Director & Envoy-Based L7 ILB for Production-Grade Service Mesh & Istio (Cloud Next '19)"
---



### 背景

2019年4月，google 在 Cloud Next '19 会议上的演讲，介绍 google traffic director：

https://www.youtube.com/watch?v=FUITCYMCEhU

> We are excited to announce Traffic Director and Envoy-based L7 ILB, our new GCP services for Service Mesh and Istio. Traffic Director is toil-free, GCP-managed control plane with SLA for Service Meshes. In Istio environments, Traffic Director provides a GCP-managed Pilot for your service mesh. Traffic Director delivers traffic management and multi-region global load balancing for service meshes built using open proxies like Envoy and through the open xDSv2 APIs. It provides policy driven traffic routing, enabling you to control the flow of traffic between services. All of this makes load balancing, scaling, A/B testing, canary roll outs, and blue-green deployments toil-free to set up.Traffic Director also provides centralized high fidelity health checking, and traffic driven autoscaling. Envoy-based Layer 7 Internal Load Balancing (L7 ILB), another flavor of Traffic Director, brings modern traffic management capabilities to traditional environments. With L7 ILB, Traffic Director controls a pool of GCP-managed Envoy proxies under the hood but presents this service as a traditional Layer 7 ILB middle proxy to front your legacy apps. Traffic Director supports VM-based, Kubernetes and GKE apps and more enabling you to modernize at your pace from your starting point. Join us to get a deep dive into Service Mesh Networking, Traffic Director and L7 ILB through a series of demos and real world customer use cases and best practices.
>
> 我们很高兴地宣布 Traffic Director 和 Envoy L7 ILB，这是我们为Service Mesh和Istio提供新的GCP服务。 Traffic Director是无痛，GCP托管的控制平面，具有用于Service Mesh的SLA。在Istio环境中，Traffic Director为服务网格提供GCP托管的Pilot。 Traffic Director为使用Envoy等开放代理和开放式xDS v2 API构建的服务网格提供流量管理和多区域全局负载均衡。它提供策略驱动的流量路由，使您能够控制服务之间的流量。所有这些都使得负载均衡，伸缩，A/B测试，金丝雀推出和蓝绿部署变得容易.Traffic Director还提供集中式高保真健康检查和流量驱动自动伸缩。基于Envoy的第7层内部负载平衡（L7 ILB）是另一种Traffic Director，它为传统环境带来了现代化的流量管理功能。借助L7 ILB，Traffic Director可以控制GCP管理的Envoy代理池，但是将此服务作为传统的第7层ILB中间代理提供给您的旧版应用程序。 Traffic Director支持基于VM，Kubernetes和GKE的应用程序以及更多功能，使您能够从起点开始进行现代化。加入我们，通过一系列演示和现实世界的客户使用案例和最佳实践，深入了解Service Mesh Networking，Traffic Director和L7 ILB。

### 内容摘要





### 资料

- [Session @ cloud next 19](https://cloud.withgoogle.com/next/sf/sessions#April10)

- [slides下载地址](https://storage.googleapis.com/gweb-cloudnext19.appspot.com/event-assets/sf/materials/NET207_%20Traffic%20Director%20and%20Envoy-based%20L7%20ILB%20for%20Production-Grade%20Service%20Mesh%20and%20Istio.pdf)



