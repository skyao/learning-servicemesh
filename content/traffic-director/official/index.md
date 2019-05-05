---
date: 2018-10-07T10:00:00+08:00
title: Traffic Director官方资料
weight: 1010
description: "介绍Google Traffic Director"
---

来自Traffic Director官方网站的介绍资料，Traffic Director的口号是：

> Enterprise-ready traffic management for open service mesh.
> 
> 企业就绪的流量管理，用于开放 service mesh

- 用于服务网格的流量管理

	服务网格是一种强大的抽象，在提供微服务和现代应用程序方面越来越受欢迎。在服务网格中，具有服务代理（如Envoy）的服务网格数据平面移动流量，服务网格控制平面为这些服务代理提供策略，配置和智能。Traffic Director是GCP完全托管的服务网格流量控制平面。借助Traffic Director，可以跨多个区域中的群集和VM实例轻松部署全局负载均衡，下放健康检查到服务代理，以及配置复杂的流量控制策略。Traffic Director使用开放的 xDSv2 API与数据平面中的服务代理进行通信，从而确保您不会被锁定在专有接口中。
	
	- 完全管理，有SLA保证

	作为Google托管的服务，Traffic Director提供了99.99％的生产级SLA：如果出现问题，我们的运维会处理，而不是您的运维。您无需担心部署和管理控制平面，这意味着您的员工可以专注于您的业务。

	- 先进的流量管理让事情变得简单

	使用Traffic Director轻松部署所有内容，从简单负载均衡到高级功能，如请求路由和基于百分比的流量拆分。

- 建立弹性服务

	通过将服务以VM或容器的方式部署在多个区域，并使用Traffic Director通过自动跨区域访问和故障转移提供全局负载均衡，从而使您的服务保持正常运行。
	
- 	与部署无缝扩展

	Traffic Director旨在无缝地处理部署的增长。随着服务数量的增长，Traffic Director可以无缝扩展以管理所有服务，即使是大型安装也是如此。

- 按照您的步调进行现代化

	Traffic Director适用于基于VM（Compute Engine）和容器化应用程序（Google Kubernetes Engine或自我管理的Kubernetes），可以逐步引入到您的服务。
	
	Traffic Director的特性如下：
	
- 	开放服务代理的流量管理

	Traffic Director为兼容 xDSv2 标准的开放服务代理（如Envoy）提供GCP托管的流量管理控制平面。

- 适用于VM和容器

	使用托管实例分组部署Traffic Director管理的VM服务实例，并使用网络端点分组部署的容器实例

- 全局负载均衡

	使用Traffic Director，您可以在多个区域中部署服务实例，以实现弹性和可访问，同时只需要一个服务IP。这意味着，例如，您的GKE服务可以位于多个集群中，而每个集群可以位于不同的区域中。如果最靠近用户的实例发生故障或过载，则流量将无缝地定向到另一个可用实例。

- 大规模的健康检查

	Traffic Director提供由GCP交付的大规模健康检查。这将从Envoy/服务代理卸载健康状况检查到Google弹性系统，允许您扩展健康检查到所有大小的部署。此外，您的实例本身不会因网格大小的运行状况检查而不堪重负。

- 具有请求路由和丰富流量策略的流量控制（alpha）

	Traffic Director支持高级请求路由功能，如流量拆分，启用基于各种header值（包括cookie）的canarying，url重写/重定向，故障注入，流量镜像和高级路由功能等用例。Traffic Director还支持许多高级流量策略，包括许多负载均衡方案，熔断器和后端异常检测。

- 为服务提供智能，快速的自动扩展功能

	Traffic Director为您提供按需驱动的自动缩放功能，允许您仅为您使用的内容付费，同时快速智能地扩展，而无需访问您的云提供商且无需任何预热要求。
	
	来自 Envoy 创始人 Matt Klein 的评价：
	
> 	Traffic Director可以更轻松地将Envoy和服务网格的优势带入生产环境。随着Envoy提供通用数据平面，Traffic Director提供了完全托管的流量控制平面，其开放式接口可以避免锁定。Traffic Director的SLA，全局负载均衡和丰富的流量控制有助于减少企业和云原生终端用户的流量管理的工作。

### 参考资料

Traffic Director官方网站首页：

https://cloud.google.com/traffic-director/