---
title: "Envoy的WASM支持概述"
linkTitle: "WASM概述"
weight: 2801
date: 2021-10-31
description: >
  Envoy的WASM支持概述
---



### 使用基于 Web Assembly 的 Get Envoy 工具包扩展 Envoy

https://cloudnative.to/blog/introducing-getenvoy-extension-toolkit-for-webassembly-based-envoy-extensions/

### Envoy WASM 源码抽丝剥茧

本文旨在从源码角度解析 Envoy 和 WASM 沙箱是如何桥接的。希望读者通过阅读本文，能够对 Envoy WASM 的接入有一定的了解。在实践的过程之中，能够帮助读者在繁杂的类型关系和调用链路中理清思路。本文默认读者具备一定的 Envoy 知识基础并且对 Envoy Filter 机制具备一定的了解。如果仅仅是希望使用 WASM 而不需要深入了解或者二次开发 Envoy WASM，那么可以阅读 SDK 文档即可。

https://cloudnative.to/blog/envoy-wasm-source-deep-dive/

### Istio 进阶学习系列 基于 Web Assembly 实现 Envoy 与 Istio 的功能扩展

本文对 WebAssembly 和 Envoy 技术进行了介绍，通过 WASM Filter 的构建、发布和部署过程，方便读者了解 Envoy WASM Filter 的扩展方式及其实现原理。

https://cloudnative.to/blog/envoy-wasm/