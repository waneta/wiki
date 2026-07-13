---
title: "国外软件都靠英伟达抢跑物理AI，国产靠什么？"
source: "https://mp.weixin.qq.com/s/Z4YVIb9xnHeUiKVLBomQwg"
author:
  - "[[坤少]]"
published:
created: 2026-06-18
description:
tags:
  - "clippings"
---
坤少 坤少说 *2026年6月12日 13:04*

近半年来，黄仁勋的一连贯发布动作，不断颠覆工业软件行业。无论是 Omniverse数字孪生平台， 还是 物理 AI基础模型Cosmos， 亦或是支撑 自主 AI工程师的NemoClaw …… 英伟达 正在 将 GPU算力、世界模型、物理AI和AI Agent整合成 为 新的工业软件基础设施。

在这个庞大的基础设施上，工业软件巨头也迎来前所未有的技术革命！ 就在最近， Cadence、达索系统、西门子、新思科技等软件巨头 都 宣布基于 NVIDIA NemoClaw构建自主AI工程师，将原本需要数周完成的仿真验证流程压缩至数小时。

显然， 以 GPU算力为底座， 用工程 仿真生成物理数据， 再以 AI Agent重构工程流程， 是工业软件企业抢跑 物理 AI时代的 最新布局。但是， 对于国产工业软件而言，没有英伟达这样的生态支点， 还有追赶仿真巨头的机会吗？

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/TCYk0DsjjcwIqHsyQO9v0jqicc1VXdaBibgEpY1NgGzEjnAfPJ4pF37IurTcqZcodBy69gUKq0LicOskeCJhcia6xA7iaRUPCvrTlKPbGiaricxTD8/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

**国外巨头** **紧抱** **英伟达** **的** **目标** **一致**

虽然，国外商软巨头的业务范畴有所差异， 但 是目的都是在重构仿真。如 Cadence利用OpenShell打造自主芯片工程师 、 达索将 NemoClaw嵌入3DE平台 、 西门子把 Fuse EDA AI Agent用于多工具协同 、 新思科技 /Ansys 则要实现芯片设计全流程。

无论芯片验证、结构优化还是制造工艺， 它们的 底层都离不开物理规律求解与仿真数据生成。 正如 黄仁勋 所说 ： “Simulation is at the heart of almost everything NVIDIA does（仿真是英伟达几乎所有业务的核心）。”

我发现，至今还有很多同行认为 仿真 只是用于 研发验证 的工具 ， 其实在物理 AI时代， 它 更重要的身份是 训练 AI的必要 基础设施。 基于这层理解，你会发现 英伟达提供的是底座，而工业软件厂商 是基于它不断 重塑自己的能力边界。

![图片](https://mmbiz.qpic.cn/mmbiz_png/TCYk0Dsjjcxnsibib35lHRdAibDbQ8qGFFoPiaqaEs1X1bUy4tftT3WLTTluzhxVZGMAa0Ilrc0FC083ibgw6rM9UeXjwqy57A3yx9Fe1F3Ko9hE/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

**没有英伟达** **的** **国产 CAE** **怎么办？**

其实这个问题在我脑海里盘旋很久了，直到最近在 云道智能用户生态大会上，看到 的 一条截然不同却又 类似的 路径 ， 我才发现国产厂商并没有坐等差距被拉大 。

相比 国外 商软 ， 云道智能 以国产仿真引擎为核心，联合国产算力、本体厂商和行业用户共同搭建物理 AI生态。 例如，在 大会上发布的 Sim-PI平台， 其 背后 就 串联起 了 摩尔线程、沐曦、中科曙光、天数智芯等国产算力企业，以及云迹科技、埃夫特、极智嘉、魔法原子等机器人企业 。

与此同时，他们还 联合 了 中兴通讯、国家人工智能应用中试基地等行业用户，形成从算力、训练到部署的完整链条。 这个逻辑与 英伟达 Omniverse生态 很 相似 ， 都是通过生态协同打通物理 AI落地路径。 但 不同的是，国外是 “英伟达+工业软件”，而国内是“国产工业软件+国产算力+行业场景”的联合突围。

据透露， 云道智能原生 GPU架构的伏图（Simdroid）平台已实现数十倍仿真加速，部分原本需要数天完成的任务缩短至数小时甚至数分钟；叠加AI代理模型后，部分场景的预测效率提升近千倍。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/lFxjiaicSrgVWdHQzLP6WVuBZJ5XHoGB0nC2VL5ztQf4LvK6pUs1WaTVhicwdfD2a3I06vG2XU6M0jwIMvs4jr4nl5sTgibluFHngqyT2ufzznY/640?wx_fmt=jpeg&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1#imgIndex=1)

**仿真** **是物理 AI的核心**

除了 Sim-PI平台外，我对这场大会最深印象就是云道智能创始人屈凯峰的演讲,他重点提到：“世界是可模拟的，因为世界是有模型的。”他还指出，“物理AI的核心是仿真，物理AI将仿真推向了世界模型的C位。”

这正如我们前文所说的， 以前 的 仿真主要 用来工程 验证 ， 而 现在还要负责训练。 例如， 机器人怎么抓取、怎么插接、怎么避障，自动驾驶如何应对极端工况，这些不可能全部依赖真实世界反复试错， 而需要在 虚拟环境里生成大 量训练数据，不断提升模型的能力。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/lFxjiaicSrgVWoYmkVOzicicWTjs1icibQZ6icsaicNw9X7ZwSpQR0zicZHg12CgUPk231AUeib47MkXibQ55ZEKoK5TjxUH3l8ibaWlDI9R4r4pgWNuOpQ/640?wx_fmt=jpeg&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1#imgIndex=2)

这 些， 或许 是 国外工业软件拥抱英伟达、 国产 厂商联合算力和机器人企业 的 原因。 虽然 大家 的路径不一样 ，但都 在努力 让机器更快、更低成本地理解真实世界。 在这个过程中，我觉得 谁能率先把算力、求解器、数据和场景串起来，谁 更有 可能在下一轮竞争中抢占先机

国产替代 · 目录

作者提示: 个人观点，仅供参考

继续滑动看下一个

坤少说

向上滑动看下一个