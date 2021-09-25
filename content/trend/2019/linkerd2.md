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

### 2019-02-12 博客：Linkerd2 2.2.0 发布

https://linkerd.io/2019/02/12/announcing-linkerd-2-2/

**Retries and timeouts**

> Linkerd 2.2 can now automatically retry failed requests, improving the overall success rate of your application in the presence of partial failures. Building on top of the service profiles model introduced in 2.1, Linkerd allows you to configure this behavior on a per-route basis. Here’s a quick screencast of using retries and timeouts to handle a failing endpoint:

Linkerd 2.2现在可以自动重试失败的请求，在部分失败的情况下提高您的应用程序的整体成功率。在2.1中引入的服务配置文件模型的基础上，Linkerd允许你在每个路由的基础上配置这种行为。

> Of course, controlling when retries can be implemented is a critical component of making retries safe to use. Linkerd 2.2 allows you to mark which routes are idempotent (isRetryable), limit the maximum time spent retrying an individual request (timeout), and configure the percentage of overall requests that can be retries (retryBudget). This parameterization allows you to ensure that retries happen safely and don’t escalate issues in an already-failing system.

当然，控制何时可以实施重试是使重试安全使用的一个重要组成部分。Linkerd 2.2允许你标记哪些路由是幂等的（isRetryable），限制重试单个请求的最大时间（timeout），并配置可以重试的总体请求的百分比（retryBudget）。这种参数化允许你确保重试安全发生，并且不会在一个已经失败的系统中升级问题。

**Auto-inject (and uninject, and improvements to inject)**

> Linkerd 2.2 graduates auto-inject to be a fully-supported (non-experimental) feature. Auto-inject is a feature that allows a Kubernetes cluster to automatically add (“inject”) Linkerd’s data plane proxies to application pods as they’re deployed.

Linkerd 2.2毕业后，自动注入成为一项完全支持的（非实验性）功能。自动注入是一项功能，允许Kubernetes集群在部署应用pod时自动添加（"注入"）Linkerd的数据平面代理。

> Moving proxy injection out of the client and onto the cluster can help ensure that all pods are running the proxy uniformly, regardless of how they’re deployed. Linkerd 2.2 also switches auto-inject’s behavior to be opt-in rather than opt-out. This means that, once enabled, only namespaces or pods that have the `linkerd.io/inject: enabled` annotation will have auto-inject behavior.

将代理注入从客户端转移到集群上，可以帮助确保所有pod统一运行代理，无论它们是如何部署的。Linkerd 2.2还将自动注入的行为改为选择进入而不是选择退出。这意味着，一旦启用，只有拥有 `linkerd.io/inject: enabled` 注解的命名空间或pod才有自动注入行为。

> Finally, for client side (non-auto) injection, Linkerd 2.2 improves the `linkerd inject` command to upgrade the proxy versions if they’re already specified in the manifest (previous behavior was to skip them entirely), and introduces a linkerd uninject command for removing Linked’s proxy from given Kubernetes manifest.

最后，对于客户端（非自动）注入，Linkerd 2.2改进了 `linkerd inject` 命令，如果清单中已经指定了代理版本，则升级代理版本（之前的行为是完全跳过它们），并引入了 `linkerd uninject` 命令，从给定的Kubernetes清单中删除Linked的代理。

**Better NET_ADMIN handling with a CNI plugin**

> Linkerd 2.2 introduces a new, experimental CNI plugin that does network configuration outside of the security context of the user deploying their application. This makes Linkerd better suited for multi-tenant clusters, where administrators may not want to grant kernel capabilities (specifically, NET_ADMIN) to users.

Linkerd 2.2 引入了一个新的、试验性的 CNI 插件，在用户部署其应用程序的安全环境之外进行网络配置。这使得Linkerd更适合于多租户集群，管理员可能不想授予用户内核能力（特别是NET_ADMIN）。

> Background: injecting Linkerd’s data plane proxy into a pod requires setting iptables rules so that all TCP traffic to and from a pod automatically goes through its proxy, without any application configuration needed. Typically, this is done via a Kubernetes Init Container that runs as the deployer’s service account. In single-tenant clusters this is usually fine, but in multi-tenant clusters this can pose a problem: modifying iptables rules requires the kernel’s NET_ADMIN capability, but granting this capability allows tenants to control the network configuration across the host as a whole.

背景：将Linkerd的数据平面代理注入到一个pod中，需要设置iptables规则，使所有进出pod的TCP流量自动通过其代理，而不需要任何应用程序配置。通常情况下，这是通过Kubernetes初始容器完成的，该容器作为部署者的服务账户运行。在单租户集群中，这通常是好的，但在多租户集群中，这可能构成一个问题：修改iptables规则需要内核的NET_ADMIN能力，但授予这种能力允许租户控制整个主机的网络配置。

> With Linkerd’s new CNI plugin, this network configuration is done in at the CNI level, effectively removes the requirement that users have the NET_ADMIN kernel capability. This makes running Linkerd in multi-tenant, security-conscious environments far more practical.

有了Linkerd的新CNI插件，这种网络配置在CNI层面完成，有效地消除了对用户拥有NET_ADMIN内核能力的要求。这使得在多租户、有安全意识的环境中运行Linkerd更加实用。

> This plugin was contributed by our friends at Nordstrom Engineering and was inspired by Istio’s CNI plugin. A special thank you to Cody Vandermyn for this feature.

这个插件是由我们在Nordstrom Engineering的朋友贡献的，灵感来自Istio的CNI插件。在此特别感谢Cody Vandermyn提供的这个功能。

**Client Identity**

>  Linkerd 2.2 introduces a new, secure mechanism for providing client identity on incoming requests. When --tls=optional is enabled, Linkerd now adds l5d-client-id header to each request. This header can be used by application code to implement authorization, e.g. requiring all requests to be authenticated or restricting access to specific services.

Linkerd 2.2 引入了一种新的、安全的机制，在传入的请求中提供客户身份。当 `-tls=optional` 被启用时，Linkerd现在为每个请求添加 `l5d-client-id` 头。这个头可以被应用程序代码用来实现授权，例如，要求所有的请求都要经过认证或限制对特定服务的访问。

> This header is currently marked as experimental, but is a critical first step towards providing comprehensive authentication and authorization mechanisms for Linkerd. In coming weeks, we’ll be publishing Linked’s roadmap for securely providing both identity and confidentiality of communication within a Kubernetes cluster.

这个头目前被标记为实验性的，但这是为Linkerd提供全面的认证和授权机制的关键第一步。在未来几周，我们将公布Linked的路线图，以安全地提供Kubernetes集群内通信的身份和保密性。

### 2019-04-17 Linkerd2 2.3.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.3.0

这个版本将mTLS从实验性的功能发展为完全支持的功能，并引入了几个重要的安全基元。最重要的是，Linkerd 2.3默认开启了网格服务间的认证、加密通信。

### 2019-04-17 博客：Linkerd2 2.3.0 发布

Announcing Linkerd 2.3: Towards Zero-Touch Zero-Trust Networking for Kubernetes

https://linkerd.io/2019/04/16/announcing-linkerd-2.3/

> This release graduates mTLS out of experimental to a fully supported feature, and introduces several important security primitives. Most importantly, Linkerd 2.3 turns authenticated, confidential communication between meshed services *on by default*.

这个版本将mTLS从实验性的功能发展为完全支持的功能，并引入了几个重要的安全基元。最重要的是，Linkerd 2.3默认开启了网格服务间的认证、加密通信。

> This is the first step towards answering a challenge we posed ourselves over a year ago: **Can we make secure communication *easier* than insecure communication for Kubernetes?**

我们一年多前提出了一个挑战，这是回答这个挑战的第一步：**我们能否让Kubernetes的安全通信比不安全通信更容易**？

> This isn’t just a theoretical question. In a world where the majority of web browsers and web sites use strong encryption and authentication with zero effort on the part of the user, it’s increasingly strange for Kubernetes services to communicate without authentication and over plain text. Why should surfing for cat pictures on Reddit have more security guarantees than the internals of our own applications?

这不仅仅是一个理论上的问题。在这个世界上，大多数网络浏览器和网站都使用强大的加密和认证，而用户不需要做任何努力，Kubernetes服务在没有认证的情况下通过纯文本进行通信，这一点越来越奇怪。为什么在Reddit上冲浪的猫咪图片要比我们自己的应用程序的内部有更多的安全保障？

> Securing the communication between Kubernetes services is an important step towards adopting zero-trust networking. In the zero-trust approach, we discard assumptions about a datacenter security perimeter, and instead push requirements around authentication, authorization, and confidentiality “down” to individual units. In Kubernetes terms, this means that services running on the cluster validate, authorize, and encrypt their own communication.

确保Kubernetes服务之间的通信安全是采用零信任网络的重要一步。在零信任方法中，我们放弃了关于数据中心安全边界的假设，而是将围绕认证、授权和保密性的要求 "下沉" 到各个单元。在Kubernetes术语中，这意味着在集群上运行的服务要验证、授权和加密自己的通信。

> But security that imposes a burden on the user—especially complex setup and configuration—is security that doesn’t get used. If zero trust is the foundation of the future of Kubernetes network security, then the cost of adopting zero trust must be as close to zero as possible. In Linkerd 2.3, we tackle this challenge head-on:

但是，给用户带来负担的安全--特别是复杂的设置和配置--是不被使用的安全。如果零信任是未来Kubernetes网络安全的基础，那么采用零信任的成本必须尽可能接近于零。在Linkerd 2.3中，我们正面应对这一挑战。

> - The control plane ships with a certificate authority (called simply “identity”).
> - The data plane proxies receive TLS certificates from this identity service, tied to the Kubernetes [Service Account](https://kubernetes.io/docs/reference/access-authn-authz/service-accounts-admin/) that the proxy belongs to, rotated every 24 hours.
> - The data plane proxies automatically upgrade all communication between meshed services to authenticated, encrypted TLS connections using these certificates.
> - Since the control plane also runs on the data plane, communication between control plane components is secured in the same way.

- 控制平面有一个证书授权机构（简称 "身份"）。
- 数据平面代理从这个身份服务中收到TLS证书，与代理所属的Kubernetes服务账户绑定，每24小时轮换一次。
- 数据平面代理会自动将网格化服务之间的所有通信升级为使用这些证书的认证、加密的TLS连接。
- 由于控制平面也在数据平面上运行，所以控制平面组件之间的通信也是以同样的方式来保障的。

> All of this is enabled by default and requires no configuration. This means that as of the 2.3 release, Linkerd now gives you encrypted, authenticated communication between all your meshed services with no effort on your part. That may not be all you need for zero trust networking in Kubernetes, but it’s a significant start.

所有这些都是默认启用的，不需要配置。这意味着，从2.3版本开始，Linkerd现在为你提供了所有网格服务之间的加密、认证的通信，而不需要做任何努力。这可能不是在Kubernetes中实现零信任网络的全部要求，但这是一个重要的开始。

> This release represents a major step forward in Linkerd’s security roadmap. In an upcoming blog post, Linkerd creator Oliver Gould will be detailing the design tradeoffs in this approach, as well as covering Linkerd’s upcoming roadmap around certificate chaining, TLS enforcement, identity beyond service accounts, and authorization. 

这个版本代表了Linkerd的安全路线图的一个重要步骤。在即将发表的一篇博文中，Linkerd的创建者Oliver Gould将详细介绍这种方法的设计权衡，以及涵盖Linkerd即将推出的围绕证书链、TLS执行、超越服务账户的身份和授权的路线图。

> Finally, we’d be remiss if we didn’t point out that this approach has been deeply inspired by our friends at Smallstep, Cloudflare, Let’s Encrypt, Mozilla, and other amazing organizations that strive to make the Internet secure by default.

最后，如果我们不指出这种方法受到Smallstep、Cloudflare、Let's Encrypt、Mozilla和其他努力使互联网默认安全的优秀组织的深刻启发，那就是我们的失职。

### 2019-07-11 Linkerd2 2.4.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.4.0

> This release adds traffic splitting functionality, support for the Kubernetes Service Mesh Interface (SMI), graduates high-availability support out of experimental status, and adds a tremendous list of other improvements, performance enhancements, and bug fixes.

这个版本增加了流量拆分功能，支持Kubernetes服务网格接口（Service Mesh Interface / SMI），将高可用性支持从实验状态中毕业。并增加了大量的其他改进、性能提升和错误修复。

> Linkerd's new traffic splitting feature allows users to dynamically control the percentage of traffic destined for a service. This powerful feature can be used to implement rollout strategies like canary releases and blue-green deploys.

Linkerd的新流量分割功能允许用户动态地控制用于服务的流量比例。这一强大的功能可用于实施推出策略，如金丝雀发布和蓝绿部署。

> Support for the [Service Mesh Interface](https://smi-spec.io/) (SMI) makes it easier for ecosystem tools to work across all service mesh implementations.

对 [服务网格接口](https://smi-spec.io/) (Service Mesh Interface / SMI) 的支持使生态系统工具更容易在所有服务网格实现中工作。

> Along with the introduction of optional install stages via the `linkerd install config` and `linkerd install control-plane` commands, the default behavior of the `linkerd inject` command only adds annotations and defers injection to the always-installed proxy injector component.

随着通过 `linkerd install config` 和 `linkerd install control-plane ` 命令引入的可选安装阶段，`linkerd inject` 命令的默认行为只添加注解，并将注入推迟到始终安装的代理注入器组件。

> Finally, there have been many performance and usability improvements to the proxy and UI, as well as production-ready features including:
> 
> - A new `linkerd edges` command that provides fine-grained observability into the TLS-based identity system
> - A `--enable-debug-sidecar` flag for the `linkerd inject` command that improves debugging efforts

最后，代理和用户界面有了许多性能和可用性的改进，还有一些可用于生产的功能，包括:

- 一个新的 `linkerd edges`命令，提供了对基于TLS的身份系统的细粒度观察。
- 为 `linkerd inject` 命令设置的 `enable-debug-sidecar` 标志，改善了调试工作。

个人小结：支持SMI，新增流量拆分功能

### 2019-08-21 Linkerd2 2.5.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.5.0

这个版本增加了对Helm的支持，通过RBAC进行tap认证和授权，流量分割统计，动态日志级别，新的集群监控仪表板，以及无数的性能提升和错误修复。

### 2019-08-21 博客：Linkerd2 2.5.0 发布

https://linkerd.io/2019/08/20/announcing-linkerd-2.5/

Announcing Linkerd 2.5: Helm support and RBAC-aware tap

> This release adds support for installation via Helm, hardens Linkerd’s tap command to obey Kubernetes RBAC rules, improves Linkerd’s CLI to report metrics during traffic splits, allows logging levels to be set dynamically, and much, much more.

这个版本增加了对通过Helm安装的支持，强化了Linkerd的tap命令以遵从Kubernetes的RBAC规则，改进了Linkerd的CLI以在流量分流时报告指标，允许动态设置日志级别，还有更多。

> Linkerd’s new Helm support offers an alternative to linkerd install for installation. If you’re a Helm 2 or Helm 3 user, you can use this install Linkerd with your existing deployment flow. Even if you’re not, this method may provide a better mechanism for environments that require lots of customization at install time, which would otherwise require a complicated set of arguments to linkerd install. (And getting a Linkerd 2.x Helm chart into the Helm stable repo itself is in progress.)

Linkerd的新Helm支持提供了一个替代linkerd install的安装方式。如果你是Helm 2或Helm 3的用户，你可以使用这个安装Linkerd与你现有的部署流程。即使你不是，这种方法也可能为需要在安装时进行大量定制的环境提供一个更好的机制，否则就需要向linkerd install提供一组复杂的参数。 (而将Linkerd 2.x Helm图表纳入Helm稳定版本本身正在进行中)。

> Linkerd’s tap command provides “tcpdump for microservices” functionality that allows users to view a sample of live request/response calls for meshed deployments. (Particularly useful since as of 2.3, Linkerd encrypts all meshed HTTP traffic by default, rendering tcpdump itself less than useful!) In Linkerd 2.5, tap now uses Kubernetes RBAC to provide granular access to results. This means that applications which process sensitive data can now control who has access that data in transit by using the RBAC rules of the underlying Kubernetes cluster.

Linkerd的tap命令提供了 "用于微服务的tcpdump" 的功能，允许用户查看网格化部署的实时请求/响应调用样本(特别有用的是，从2.3版本开始，Linkerd默认对所有网状的HTTP流量进行加密，使得 tcpdump 本身变得不那么有用！）。在Linkerd 2.5中，tap现在使用Kubernetes RBAC来提供对结果的细化访问。这意味着，处理敏感数据的应用程序现在可以通过使用底层Kubernetes集群的RBAC规则来控制谁可以在传输过程中访问这些数据。

个人小结：增加对Helm的支持

### 2019-10-11 Linkerd2 2.6.0 发布

https://github.com/linkerd/linkerd2/releases/tag/stable-2.5.0

这个版本引入了分布式跟踪支持，为linkerd tap增加了请求和响应头信息，极大地提高了仪表盘在大型集群上的性能，在仪表盘上增加了流量分割的可视化功能，增加了一个 公共Helm repo，还有更多改进!

### 2019-10-10 博客：Linkerd2 2.6.0 发布

https://linkerd.io/2019/08/20/announcing-linkerd-2.5/

Announcing Linkerd 2.6: Distributed tracing, live request headers, faster dashboard, and more!

> This release adds support for distributed tracing, brings request and response headers to Linkerd’s live tap output, adds traffic split visualizations to the dashboard, dramatically improves the performance of the dashboard on large clusters, adds a public Helm repo, and much, much more.

这个版本增加了对分布式跟踪的支持，为Linkerd的实时tap输出带来了请求和响应头，为仪表盘增加了流量分割的可视化，极大地提高了仪表盘在大型集群上的性能，增加了一个公共的Helm repo，还有很多很多。

> Linkerd’s new distributed tracing support means that Linkerd’s data plane proxy now emit trace spans, allowing proxy timing for individual requests to be captured with systems like Jaeger. Since distributed tracing is a complex topic that (unlike most of Linkerd’s features!) requires some investment to use, Linkerd maintainer Alex Leong has written a handy blog post describing how to assemble a functioning end-to-end distributed tracing system with Linkerd 2.6.

Linkerd新的分布式跟踪支持意味着Linkerd的数据平面代理现在可以发出跟踪span，允许用Jaeger等系统捕获单个请求的代理时间。由于分布式跟踪是一个复杂的话题，（与Linkerd的大多数功能不同！）需要一些投资才能使用，Linkerd维护者Alex Leong写了一篇方便的博文，描述了如何用Linkerd 2.6组装一个有效的端到端分布式跟踪系统。

> This release also adds live request and response headers to Linkerd’s tap output. Linkerd’s tap feature provides a live sample of actual requests flowing between any two pods, deployments, or namespaces. (Particularly useful since Linkerd encrypts all meshed HTTP traffic by default!) In Linkerd 2.5, we ensured that tap obeyed Kubernetes RBAC restrictions; the addition of 2.6 headers brings us one step closer to our vision of a complete “tcpdump for microservices”–if tcpdump obeyed fine-grained access control, that is.

这个版本还为Linkerd的tap输出增加了实时请求和响应头信息。Linkerd的tap功能提供了在任何两个pod、部署或命名空间之间流动的实际请求的实时样本。(特别有用的是，Linkerd默认对所有网格的HTTP流量进行加密！）。) 在Linkerd 2.5中，我们确保tap服从Kubernetes的RBAC限制；2.6头文件的增加使我们离我们的愿景更近了一步，即一个完整的 "微服务的tcpdump" -- 如果tcpdump服从细粒度的访问控制，那就是。

> Linkerd 2.6 brings several improvements to Linkerd’s dashboard. First, we’ve dramatically reduced the Prometheus load generated by the dashboard—the dashboard should now be usable on large clusters, and cause significantly less load even on small ones. Second, the dashboard now includes a visualization of the traffic split feature for canary deployments, which is already causing some excitement in the community:

Linkerd 2.6给Linkerd的仪表盘带来了一些改进。首先，我们极大地减少了仪表盘产生的Prometheus负载--现在仪表盘应该可以在大型集群上使用，即使在小型集群上也能显著减少负载。第二，仪表盘现在包括了一个可视化的金丝雀部署的流量分割功能，这已经在社区中引起了一些兴奋。

个人小结：增加了对分布式跟踪的支持
