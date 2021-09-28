---
title: "xDS协议概述"
linkTitle: "xDS概述"
weight: 10001
date: 2021-09-27
description: >
  xDS协议概述
---



2017-12-04 Envoy 1.5.0 版本，

https://www.envoyproxy.io/docs/envoy/latest/version_history/v1.5.0

- config: the [v2 API](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/overview/v2_overview#config-overview-v2) is now considered production ready.

https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/overview/v2_overview#config-overview-v2

The Envoy v2 APIs are defined as [proto3](https://developers.google.com/protocol-buffers/docs/proto3) [Protocol Buffers](https://developers.google.com/protocol-buffers/) in the [data plane API repository](https://github.com/envoyproxy/data-plane-api/tree/master/api). They evolve the existing [v1 APIs and concepts](https://www.envoyproxy.io/docs/envoy/v1.5.0/configuration/overview/v1_overview#config-overview-v1) to support:

- Streaming delivery of [xDS](https://github.com/envoyproxy/data-plane-api/blob/master/XDS_PROTOCOL.md) API updates via gRPC. This reduces resource requirements and can lower the update latency.
- A new REST-JSON API in which the JSON/YAML formats are derived mechanically via the [proto3 canonical JSON mapping](https://developers.google.com/protocol-buffers/docs/proto3#json).
- Delivery of updates via the filesystem, REST-JSON or gRPC endpoints.
- Advanced load balancing through an extended endpoint assignment API and load and resource utilization reporting to management servers.
- [Stronger consistency and ordering properties](https://github.com/envoyproxy/data-plane-api/blob/master/XDS_PROTOCOL.md#eventual-consistency-considerations) when needed. The v2 APIs still maintain a baseline eventual consistency model.

See the [xDS protocol description](https://github.com/envoyproxy/data-plane-api/blob/master/XDS_PROTOCOL.md) for further details on aspects of v2 message exchange between Envoy and the management server.





https://www.envoyproxy.io/docs/envoy/latest/api/api_supported_versions#api-supported-versions

Supported API versions

Envoy’s APIs follow a [versioning scheme](https://github.com/envoyproxy/envoy/blob/d48543b/api/API_VERSIONING.md) in which Envoy supports multiple major API versions at any point in time. The following versions are currently supported:

- [v3 xDS API](https://www.envoyproxy.io/docs/envoy/latest/api-v3/api#envoy-v3-api-reference) (*active*). Envoy developers and operators are encouraged to be actively adopting and working with v3 xDS.

The following API versions are no longer supported by Envoy:

- v1 xDS API. This was the legacy REST-JSON API that preceded the current Protobuf and dual REST/gRPC xDS APIs.
- v2 xDS API. Support for this was removed in Q1 2021.



1.14.0 (April 8, 2020

- api: froze v2 xDS API. New feature development in the API should occur in v3 xDS. While the v2 xDS API has been deprecated since 1.13.0, it will continue to be supported by Envoy until EOY 2020. See [Supported API versions](https://www.envoyproxy.io/docs/envoy/latest/api/api_supported_versions#api-supported-versions).

    
