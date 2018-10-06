---
date: 2018-10-04T20:00:00+08:00
title: Service Mesh市场竞争
weight: 120
menu:
  main:
    parent: "introduction"
keywords:
- Service Mesh市场竞争
description : "详细介绍Service Mesh市场竞争"
---

在过去的几年中，微服务技术得以迅猛普及，和容器技术一起成为这两年中最吸引眼球的技术热点。而以Spring Cloud为代表的传统侵入式开发框架，占据着微服务市场的主流地位，甚至一度成为微服务的代名词。

直到2017年年底，当非侵入式的Service Mesh技术终于从萌芽到走向了成熟，当Istio横空出世，人们才惊觉：微服务并非只有侵入式一种玩法，微服务更不是Spring Cloud的独角戏！

这一次的新生力量，完全不按照常理出牌，出场就霸道地掀翻桌子，直接摆出新的玩法：Service Mesh，下一代微服务！让我们一起来回顾这一场起于2017年的Service Mesh大战，一起领略各家产品的风采。

## Service Mesh的萌芽期

在我们正式开始之前，我们将时间回到2016年：有些故事背景需要预交交代一下。

虽然直到2017年底，Service Mesh才开始较大规模被世人了解，这场微服务市场之争也才显现，但是其实Service Mesh这股微服务的新势力，早在 2016年初就开始萌芽：

- 2016年1月15日，离开twitter的基础设施工程师William Morgan和Oliver Gould，在github上发布了linkerd 0.0.7版本，他们同时组建了一个创业小公司Buoyant，业界第一个Service Mesh项目诞生。

- 2016年，Matt Klein在Lyft默默的进行Envoy的开发。Envoy诞生的时间其实要比Linkerd更早一些，只是在Lyft内部不为人所知。

在2016年初，Service Mesh还只是Buoyant公司的内部词汇，而之后，随着Linkerd的开发和推广，Service Mesh这个名词开始逐步走向社区并被广泛接受，喜爱和推崇：

- 2016年9月29日在SF Microservices上，“Service Mesh”这个词汇第一次在公开场合被使用。这标志着“Service Mesh”这个词，从Buoyant公司走向社区。
- 2016年10月，Alex Leong开始在buoyant公司的官方Blog中开始”A Service Mesh for Kubernetes”系列博客的连载。随着”The services must mesh”口号的喊出，buoyant和Linkerd开始service mesh概念的布道。

在这一年中，第一代的Service Mesh产品在稳步推进：

- 2016年9月13日，Matt Klein宣布Envoy在github开源，直接发布1.0.0版本
- 2016年下半年，Linkerd陆续发布了0.8和0.9版本，开始支持HTTP/2 和gRPC，1.0发布在即；同时，借助Service Mesh在社区的认可度，Linkerd在年底开始申请加入CNCF。

而在这个世界的另外一个角落，Google和IBM两位巨人，握手开始合作，他们联合Lyft，启动了Istio项目。这样，在第一代Service Mesh还未走向市场主流时，以Istio为代表的第二代Service Mesh就迫不及待地上路。

现在我们可以进入主题，开始2017和2018年Service Mesh市场竞争的回顾。

## 急转而下的Linkerd

2017年，Linkerd迎来了一个梦幻般的开局，喜讯连连：

- 2017年1月23日，Linkerd加入CNCF
- 2017年3月7日，Linkerd宣布完成千亿次产品请求
- 2017年4月25日，Linkerd 1.0版本发布

可谓各条战线都进展顺利：产品完成1.0 release，达成最重要的里程碑；被客户接受并在生产线上成功大规模应用，这代表着市场的认可；进入CNCF更是意义重大，是对Linkerd的极大认可，也使得Linkerd声名大噪。一时风光无量，可谓”春风得意马蹄疾，一日看尽长安花”。

需要特别指出的是，Linkerd加入CNCF，对于Service Mesh技术是一个非常重要的历史事件：这代表着社区对Service Mesh理念的认同和赞赏，Service Mesh也因此得到社区更大范围的关注。

趁热打铁，就在Linkerd 1.0版本发布的同一天，创作者继续Service Mesh的布道：

- 2017年4月25日，William Morgan发布博文”What’s a service mesh? And why do I need one?“。正式给Service Mesh做了一个权威定义。

然而现实总是那么残酷，这个美好的开局，未能延续多久就被击碎：

- 2017年5月24日，Istio 0.1 release版本发布，google和IBM高调宣讲，社区反响热烈，很多公司在这时就纷纷站队表示支持Istio。

Linkerd的风光瞬间被盖过，从意气风发的少年一夜之间变成过气网红。当然，从产品成熟度上来说，linkerd作为业界仅有的两个生产级Service Mesh实现之一，暂时还可以在Istio成熟前继续保持市场。但是，随着Istio的稳步推进和日益成熟，外加第二代Service Mesh的天然优势，Istio取代第一代的Linkerd只是个时间问题。

面对google和IBM加持的Istio，linkerd实在难有胜算：

- Istio作为第二代Service Mesh，通过控制平面带来了前所未有的控制力，远超Linkerd。
- Istio通过收编和Linkerd同为第一代Service Mesh的envoy，直接拥有了一个功能和稳定性与linkerd在一个水准的数据平面（也就是作为 sidecar 模式部署的 proxy）。
- 基于c++的envoy在性能和资源消耗上本来就强过基于Scala/Jvm的Linkerd
- Google和IBM组合在人力，资源和社区影响力方面远非Buoyant公司这样的小公司可以比拟

Linkerd的发展态势顿时急转而下，未来陷入一片黑暗。出路在哪里？

在一个多月后，Linkerd给出一个答案：和Istio集成，成为Istio的数据面板。

- 2017年7月11日，Linkerd发布版本1.1.1，宣布和Istio项目集成。Buoyant发表博文”Linkerd and Istio: like peanut butter and jelly”。

这个方案在意料之中，毕竟面对Google和IBM的联手威胁，选择低头和妥协是可以理解的。只是存在两个疑问：

1. 和Envoy相比，Linkerd并没有特别优势。考虑编程语言的天生劣势，Linkerd想替代Envoy难度非常之大。
2. 即使替代成功，在Istio的架构下，只是作为一个数据平面存在的Linkerd，可以发挥的空间有限。这种境地的Linkerd，是远远无法承载起Buoyant的未来的。

Linkerd的这个谜团，直到2017年即将结束的12月，在Conduit发布之后才被解开。

## 波澜不惊的Envoy

自从在2016年决定委身于Istio之后，Envoy就开始了一条波澜不惊的平稳发展之路，和Linkerd的跌宕起伏完全不同。

在功能方面，由于定位在数据平面，因此Envoy无需考虑太多，很多工作在Istio的控制平面完成就好，Envoy从此专心于将数据平面做好，完善各种细节。在市场方面，Envoy和Linkerd性质不同，不存在生存和发展的战略选择，也没有正面对抗生死大敌的巨大压力。Envoy在2017年有条不紊地陆续发布了1.2、1.3、1.4和1.5版本，在2018年发布了1.6，1.7，1.8版本，稳步地完善自身，表现非常稳健。

稳打稳扎的Envoy一方面继续收获独立客户，一方面伴随Istio一起成长。作为业界仅有的两个生产级Service Mesh实现之一，Envoy在2017年中收获了属于它的殊荣：

- 2017年9月14日，Envoy加入CNCF，成为CNCF的第二个Service Mesh项目

可谓名至实归，水到渠成。作为一个无需承载一家公司未来的开源项目，Envoy在2017和2018年的表现，无可挑剔。

## 背负使命的Istio

从Google和IBM联手决定推出Istio开始，Istio就注定永远处于风头浪尖，无论成败。

Istio背负了太多的使命：

- 建立Google和IBM在微服务市场的统治地位
- 为Google和IBM的公有云打造杀手锏级特性
- 在k8s的基础上，延续Google的战略布局

Google在企业市场的战略布局，是从底层开始，一步一步向上，一步一步靠近应用。刚刚大获全胜的K8s为Istio准备了一个非常好的基石，而Istio的历史使命，就是继k8s拿下容器之后，更进一步，**拿下微服务**！

2017年，Istio稳步向前，先后发布0.1 / 0.2 / 0.3 / 0.4 四个版本，在2018年初，Istio的发布周期修改为每月一次。

在社区方面，Istio借助Google和IBM的大旗，外加自身过硬的实力、先进的理念，很快获得了社区的积极响应和广泛支持。包括Oracle和Red Hat在内的业界大佬都明确表示对支持Istio，而Isito背后，还有日渐强大的Kubernetes和CNCF社区。

在平台支持方面，Istio的初期版本只支持k8s平台，从0.3版本开始提供对非k8s平台的支持。从策略上说，Istio借助了k8s，但是没有强行绑定在k8s上。

Istio面世之后，赞誉不断，尤其是Service Mesh技术的爱好者，可以说是为之一振：以新一代Service Mesh之名横空出世的Istio，对比Linkerd，优势明显。同时产品路线图上有一大堆令人眼花缭乱的功能。假以时日，如果Istio能顺利地完成开发，稳定可靠，那么这会是一个非常美好、值得憧憬的大事件，它的意义重大：

- 重新定义微服务开发方式，让Service Mesh成为主流技术
- 大幅降低微服务开发的入门门槛，让更多的企业和开发人员可以落地微服务
- 统一微服务的开发流程，标准化开发/运维方式

2018年上半年的Istio，在万众瞩目充满期待之时，突然陷入困境长达数月：开发进度放缓，代码质量下降，经常犯低级错误。表现令人惊讶和迷惑，好在这个状态在年中开始好转，进入下半年之后Istio开始稳打稳扎：

- 2018年6月1日，发布0.8.0 LTS版本，这是Istio第一个长期支持版本
- 2018年7月31日，发布令整个社区期待已久的1.0.0版本
- 2018年10月，预计发布1.1.0版本


从目前局势看，Istio慢慢的完善产品，表现相对2018年要成熟很多，但是依然存在诸多问题，依然缺乏大规模的落地实践。但相信随着时间的推移，Google和Istio社区应该能够继续向前推进。

## 背水一战的Buoyant

2017年底的KubeConf，在Service Mesh成为大会热点、Istio备受瞩目时，Buoyant公司出人意料地给了踌躇满志又稍显拖沓的Istio重重一击：

- 2017年12月5日，Conduit 0.1.0版本发布，Istio的强力竞争对手亮相KubeConf。

Conduit的整体架构和Istio一致，借鉴了Istio数据平面+控制平面的设计，同时别出心裁地选择了Rust编程语言来实现数据平面，以达成Conduit 宣称的更轻、更快和超低资源占用。

继Isito之后，业界第二款第二代Service Mesh产品就此诞生。话说得有些拗口，但是一场大战就此浮出水面。Buoyant在Linkerd不敌Istio的恶劣情况下，绝地反击，祭出全新设计的Conduit作为对抗Istio的武器。

需要额外指出的是，作为一家初创型企业，在第一款主力产品Linkerd被Istio强力阻击之后，Buoyant已经身陷绝境，到了生死存亡之秋，作为背负公司期望，担负和Istio正面抗衡职责的Conduit，可谓压力巨大。

从目前得到的信息分析，Conduit明显是有备而来，针对Istio当前状况，针锋相对的：

- **编程语言**：为了达成更轻、更快和更低资源消耗的目标，考虑到Istio的数据面板用的是基于C++语言的Envoy，Conduit跳过了Golang，直接选择了Rust，颇有些剑走偏锋的意味。不过，单纯以编程语言而言，在能够完全掌握的前提下，Rust的确是做proxy的最佳选择。考虑到Envoy在性能方面的良好表现，Conduit要想更进一步，选择Rust也是可以理解。
- **架构设计**：在借鉴Istio整体架构的同时，Conduit做了一些改进。首先Conduit控制平面的各个组件是以服务的方式提供功能的，极富弹性。另外，控制平面特意为定制化需求进行了可扩展设计，可以通过编写gPRC插件来扩展Conduit的功能而无需直接修改Conduit，这对于有定制化需求的客户是非常便利的。

然而，要抗衡Istio和其身后的Google与IBM，谈何容易。尤其控制平面选择Rust，成为一把双刃剑，固然Rust的上佳表现让Conduit在性能和资源消耗方面有不小的亮点，但是Rust毕竟是小众语言，普及程度远远不能和Java/C++/Golang相比，导致Conduit很难从社区借力。Conduit几乎是凭Buoyant以一家之力在独立支撑对抗Istio，终于难以为继：

- 2018年7月，Conduit 0.5发布，同时宣布这是 Conduit 最后一个版本，Conduit未来将作为Linkerd2.0的基础继续存在。随后Conduit的github仓库被从`runconduit/conduit更名`为`linkerd/linkerd2`


在2017年5月Istio发布0.1版本之后，在巨大的生存压力下，Buoyant就一直在苦苦寻找出路，尝试过多种思路：

1. 用Linkerd做数据平面，和Istio集成，替代Envoy。但Linkerd终究是Scala编写，做数据平面和Envoy比毫无优势，Istio官方也没有任何正面回应，不了了之
2. 2017年底启动Conduit项目，剑走偏锋选择Rust做数据平面，但控制平面和Istio相比相去甚远，最终在2018年5月停止发展，转为Linkerd2.0。
3. 2018年5月尝试在GraalVM上运行Linkerd，试图通过将Linkerd提前编译为本地可执行文件，以换取更快的启动时间和更少的内存占用。但后续未见有进一步的信息。
4. 2018年5月启动Linkerd2.0，在Conduit的基础上（也许应该称为改名？）继续发展，定位为k8s平台上的轻量级Service Mesh。

作为Service Mesh先驱，Buoyant这两年中的发展道路，充满挑战，面对Istio和背后的Google，艰难险阻可想而知，期待他们在后面能有更好的表现。

## 其他参与者

Service Mesh市场，除了业界先驱Linkerd/Envoy，和后起之秀Istio/Conduit，还有一些其它的竞争者陆陆续续在2017和2018年进入这个市场。

### Nginmesh

首先是nginmesh，来自大名鼎鼎的Nginx，定位为"Istio compatible service mesh using NGINX"：

- 2017年9月，在美国波特兰举行的nginx.conf大会上，nginx宣布了nginmesh。随即在github上发布了0.1.6版本。
- 2017年12月6日，nginmesh 0.2.12版本发布
- 2017年12月25日，nginmesh 0.3.0版本发布

之后沉寂过一段时间，后来又突然持续更新，接连发布了几个版本。但是，在2018年7月发布0.7.1版本之后，就停止提交代码。

### Aspen Mesh

来自大名鼎鼎的F5 Networks公司，基于Istio构建，定位企业服务网格，口号是"Service MeshMade Easy"。Aspen Mesh项目据说启动非常之早，在2017年5月Istio发布0.1版本不久之后就开始组件团队进行开发，但是一直以来都非常低调，外界了解到的信息不多。

在2018年9月，Aspen Mesh 1.0发布，基于Istio 1.0。注意这不是一个开源项目，但是可以在Aspen Mesh的官方网站上申请免费试用。

### Consol Connect

Consol是来自HashiCorp公司的产品，主要功能是服务注册和服务发现，基于Golang和Raft协议。

在2018年6月26日发布的Consul 1.2版本中，提供了新的Connect功能，能够将现有的Consul集群自动转变为service mesh 。Connect 通过自动TLS加密和基于鉴权的授权机制支持服务和服务之间的安全通信。

### Kong

Kong是被广泛使用的开源API Gateway，在2018年9月18号，kong宣布1.0版本准备发布（实际为9月26日在github上发布了1.0.0rc1版本，GA版本即将发布），而在1.0发布之后kong将转型为服务控制平台，支持Service Mesh。

比较有意思的是，Kong CTO [Marco Palladino](https://www.linkedin.com/in/marcopalladino/) 撰文提出"Service Mesh Pattern"的概念，即Service Mesh是一种新的模式，而不是一种新的技术。

### Maistra

2018年9月，Red Hat的OpenShift Service Mesh技术预览版上线，基于Istio。

Red Hat是Istio项目的早期采用者和贡献者，希望将Istio正式成为OpenShift平台的一部分。Red Hat为OpenShift上的Istio开始了一个技术预览计划，为现有的OpenShift Container Platform客户提供在其OpenShift集群上部署和使用Istio平台的能力。

Red Hat正在与上游Istio社区合作，以帮助推进Istio框架，按照Red Hat的惯例，围绕Istio的工作也是开源的。为此Red Hat创建了一个名为[Maistra](http://maistra.io/)的社区项目。

## Service Mesh国内发展

2017年，随着Servic Mesh的发展，国内技术社区也开始通过新闻报道/技术文章等开始接触Service Mesh，但是传播范围和影响力都非常有限。直到2017年底才剧烈升温，开始被国内技术社区关注：

- 2017年10月QCon上海站，来自敖小剑的名为”Service Mesh：下一代微服务”的演讲，成为Service Mesh技术在国内大型技术峰会上的第一次亮相。
- 2017年12月，在全球架构师峰会（ArchSummit）2017北京站上，华为田晓亮分享了”Service Mesh在华为云的实践”。
- 2017年12月，新浪微博周晶分享Service Mesh在微博的落地情况。
- 2018年6月，Service Mesh中国技术社区成立，网站servicemesher.com开通，并开始在杭州，北京，深圳组织多场线下Meetup，同时组织翻译Envoy，Istio官方文档和各种博客文章，大力推动了Service Mesh在国内的交流与发展。
- 2018年7月，Istio核心开发团队成员Lin Sun在ArchSummit2018深圳站进行了名为"Istio-构造、守护、监控微服务的守护神"的演讲，这是Istio官方在国内第一次亮相。 

之后，作为Servic Mesh国内最早的开发和实践者，以下公司相继宣布和开源了自己的Service Mesh产品：

- 2017年底，新浪微博Service Mesh的核心实现，跨语言通信和服务治理已经在Motan系列项目中提供
- 2018年6月，蚂蚁金服对外宣布Service Mesh类产品SOFAMesh，这是一个基于Istio的增强扩展版本，并使用基于Golang开发的SOFAMosn作为数据平面替代Envoy。
- 2018年8月，华为开源了基于Golang的Servic Mesh产品——Mesher。

## 总结

Service Mesh在过去的两年间，迅猛发展，涌现出多个产品，市场竞争激烈。而目前看，Istio借助k8s和云原生的大潮，依托Google在社区的巨大号召力，发展势头良好，有望成为这一轮大战的赢家。

在下一章，我们将详细介绍Istio的架构和功能。


