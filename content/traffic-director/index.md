---
date: 2018-10-07T10:00:00+08:00
title: Google Traffic Director
weight: 1000
description: "介绍Google Traffic Director"
---

Google Traffic Director 是与 AWS App Mesh 对标的 Service Mesh 产品。Traffic Director通过xDS协议与数据平面的Envoy进行通讯，可分别与Google Cloud的 [MIG](https://cloud.google.com/compute/docs/instance-groups/) 和 [NEG](https://cloud.google.com/load-balancing/docs/negs/) 两款产品结合去提供Service Mesh的能力。

Traffic Director的功能与开源Istio项目中的Pilot-discovery相似，也复用了Istio的不少技术实现（比如，通过iptables完成流量透明拦截）。Traffic Director支持全球负载均衡、集中式的集群健康检查、流量驱动的自动扩缩容等功能，帮助客户在全球部署与管理高弹性的无状态应用。

- https://cloud.google.com/traffic-director/
- https://cloud.google.com/traffic-director/docs/


### 参考资料：

- [Introducing Traffic Director: Google's Service Mesh Control Plane](https://www.infoq.com/news/2019/04/google-traffic-director)