---
title: "2017年Envoy动态"
linkTitle: "Envoy"
weight: 140300
date: 2021-09-27
description: >
  Matt Klein在Lyft进行Envoy的开发
---

{{% pageinfo color="primary" %}}
2017年，Envoy在平稳中逐渐走向成熟，xDS API逐渐成型
{{% /pageinfo %}}

## 年度动态

### 2017-03-08 Envoy1.2.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.2.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.2.0): 

- [Cluster discovery service (CDS) API](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/cluster_manager/cds#config-cluster-manager-cds).
- [Outlier detection](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/outlier#arch-overview-outlier-detection) (passive health checking).
- Envoy configuration is now checked against a JSON schema.
- [Ring hash](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/load_balancing#arch-overview-load-balancing-types) consistent load balancer, as well as HTTP consistent hash routing based on a policy.
- Vastly [enhanced global rate limit configuration](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/global_rate_limiting#arch-overview-rate-limit) via the HTTP rate limiting filter.
- HTTP routing to a cluster retrieved from a header.
- Weighted cluster HTTP routing.
- Auto host rewrite during HTTP routing.
- Regex header matching during HTTP routing.
- HTTP access log runtime filter.
- LightStep tracer [parent/child span association](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/tracing#arch-overview-tracing).
- [Route discovery service (RDS) API](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/http_conn_man/rds#config-http-conn-man-rds).
- HTTP router [x-envoy-upstream-rq-timeout-alt-response header](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/http_filters/router_filter#config-http-filters-router-x-envoy-upstream-rq-timeout-alt-response) support.
- *use_original_dst* and *bind_to_port* [listener options](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/listeners/listeners#config-listeners) (useful for iptables based transparent proxy support).
- TCP proxy filter [route table support](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/network_filters/tcp_proxy_filter#config-network-filters-tcp-proxy).
- Configurable stats flush interval.
- Various [third party library upgrades](https://www.envoyproxy.io/docs/envoy/v1.5.0/install/building#install-requirements), including using BoringSSL as the default SSL provider.
- No longer maintain closed HTTP/2 streams for priority calculations. Leads to substantial memory savings for large meshes.
- Numerous small changes and fixes not listed here.

个人小结：

- 关键更新：**CDS**（Cluster discovery service）API 、**RDS**(Route discovery service) API、离群检测 (Outlier detection，被动健康检查).
- 重要更新：环形哈希一致性的负载均衡，以及基于策略的HTTP一致性哈希路由，HTTP 路由增强，TCP 路由增强，使用BoringSSL作为默认的SSL提供商

### 2017-05-18 Envoy1.3.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.3.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.3.0): 

- 各种细节更新，没有特别大的新feature

### 2017-08-25 Envoy1.4.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.4.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.4.0): 

- 关键更新：**增加 LDS API**
- 重要更新：直接支持yaml作为配置文件、新增 Original destination [cluster](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/service_discovery#arch-overview-service-discovery-types-original-destination) and [load balancer](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/load_balancing#arch-overview-load-balancing-types-original-destination) 、新增 websocket 支持

### 2017-12-05 Envoy1.5.0版本发布

https://github.com/envoyproxy/envoy/releases/tag/v1.5.0

[版本更新列表](https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.5.0): 

- 关键更新：xds v2 API接近Production Ready，新增Lua filter
- 重要更新：直接支持yaml作为配置文件、新增 Original destination [cluster](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/service_discovery#arch-overview-service-discovery-types-original-destination) and [load balancer](https://www.envoyproxy.io/docs/envoy/v1.5.0/intro/arch_overview/load_balancing#arch-overview-load-balancing-types-original-destination) 、新增 websocket 支持，支持 subset load balancer，路由功能的各种优化和增强











## 年度总结

- xDS 的支持逐渐完善，xDS v2 API逐渐稳定
- 各种功能逐渐丰满

