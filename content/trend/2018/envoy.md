---
title: "2018年Envoy动态"
linkTitle: "Envoy"
weight: 130300
date: 2021-09-28
description: >
  Matt Klein在Lyft进行Envoy的开发
---

{{% pageinfo color="primary" %}}
2017年，Envoy在平稳中逐渐走向成熟，xDS API逐渐成型
{{% /pageinfo %}}

## 年度动态

### 2018-03-21 Envoy1.6.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.6.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.6.0#): 

- 关键更新：gRPC 支持的各种改进（和google合作有关？），路由功能的持续完善和改进
- 重要更新：健康检查的完善和改进，支持Unix Domain socket

### 2018-05-22 Envoy1.7.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.7.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.7.0): 

- 关键更新：新增 http RBAC 支持
- 重要更新：健康检查的完善和改进,新增 weighted round robin 和 locality weighted 负载均衡策略

### 2018-10-05 Envoy1.8.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.8.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.8.0): 

- 关键更新：默认不再支持xDS v1, 支持xDS中的RLS(Rating Limit Service)和SDS(Secret Discovery Service) 
- 重要更新：直接支持yaml作为配置文件、新增 Original destination [cluster](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/service_discovery#arch-overview-service-discovery-types-original-destination) and [load balancer](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/load_balancing#arch-overview-load-balancing-types-original-destination) 、新增 websocket 支持

个人小结：

- xDS v2 API成熟，v1 API弃用

### 2018-11-28 CNCF宣布Envoy毕业



### 2018-12-21 Envoy1.9.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.9.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.9.0): 

- 关键更新：
- 重要更新：

备注：release note长达三页，都是比较琐碎的内容









## 年度总结

- xDS 的支持逐渐完善，xDS v2 API逐渐稳定
- 各种功能逐渐丰满

