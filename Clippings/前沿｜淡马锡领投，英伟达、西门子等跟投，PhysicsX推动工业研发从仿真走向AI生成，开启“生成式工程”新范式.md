---
title: "前沿｜淡马锡领投，英伟达、西门子等跟投，PhysicsX推动工业研发从仿真走向AI生成，开启“生成式工程”新范式"
source: "https://mp.weixin.qq.com/s/e8iV-uQXc7Hk_MAVypw6aQ"
author:
  - "[[TP]]"
published:
created: 2026-06-18
description: "PhysicsX所代表的“物理AI”方向，通过深度建模物理定律，从源头释放被传统仿真所束缚的工业创新潜力。"
tags:
  - "clippings"
---
TP The Prospect *2026年6月12日 18:00*

![图片](https://mmbiz.qpic.cn/mmbiz_png/zzrD6kgYTibHTT2A9qvtZCiare2btWXucWn7LkBZibEpzYZkBGhibuzg8HGJlwTrCErdYaibeOQ7aiaQTy7UfMYFexcxNpYA4bLCicGtbqtB9iaibF1w/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

核心观点：2026年6月，伦敦AI初创公司PhysicsX完成3亿美元C轮融资，估值约24亿美元。本轮由淡马锡领投，英伟达、Applied Materials、西门子等产业资本持续跟投。这家AI驱动的工程仿真平台，正试图改写硬件创新的底层规则。如果说过去三年，大模型主要重塑了数字世界的知识生产效率，那么PhysicsX所代表的“物理AI”方向，则通过深度建模物理定律，从源头释放被传统仿真所束缚的工业创新潜力。

![PhysicsX raises $300M Series C at $2.4B valuation to scale AI for  engineering and](https://mmbiz.qpic.cn/mmbiz_png/zzrD6kgYTibHBcQFRYpPlqHZPQ0uZak5R0S4psCq08jVcsKQCMexaia3nWFF94u5fJn9jmY2gBUk9uWAkE0mdXcPxpEFs9ic4ic3YPFugBnvV08/640?wx_fmt=png&from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

PhysicsX raises $300M Series C at $2.4B valuation to scale AI for engineering and

### 一、仿真瓶颈：硬件创新为何被“锁死”

在航空航天、半导体、能源系统等尖端工业领域，硬件创新长期受制于物理仿真瓶颈。工程师每调整一个设计参数，都需要借助CFD或FEA进行验证。这类数值模拟精度极高，但代价同样巨大：一次完整仿真往往耗时数小时甚至数天，而复杂系统的设计空间组合更是天文数字。研发过程因此趋于保守，工程师只能在极有限的选项中做局部修正，难以进行系统性探索。

PhysicsX的突破恰恰在于打破这一瓶颈。它并非试图让传统仿真“更快一点”，而是通过AI学习物理系统的本质规律，直接跳过繁琐的迭代过程，在秒级时间内给出最优设计方案。这正是从“验证设计”（Validation）到“生成设计”（Generation）的根本性范式转移。

二、PhysicsX：AI原生工程平台

PhysicsX的核心是一套AI原生工程平台，其设计目标是用AI推理完全取代传统的数值仿真。传统仿真工具依赖不断求解复杂的偏微分方程，精度虽高但计算成本极为昂贵，一次完整的仿真往往耗费数小时甚至数天。PhysicsX通过学习海量仿真数据与真实实验数据的结构，将预测时间从数小时压缩至秒级。

区别于传统CAE软件在旧架构上叠加AI功能的“修补式”路径，PhysicsX从底层重新设计了工程计算范式，涵盖以下三个核心维度：

**1\. 大型物理模型（Large Physics Models）**

PhysicsX构建的LPM在概念上类似于大语言模型理解文本，但训练对象是物理方程而非语料，内化了流体、热力学、结构力学、电磁场等多物理场定律，能够进行预测性推理而非执行固定方程求解。

公司于2024年发布了全球首个飞行领域大型物理模型Ai.rplane，可在不到一秒的时间内推断出设计的气动性能、飞行稳定性和结构应力，而传统数值模拟需要数小时。该模型已用于将飞机设计周期从数月缩短至数天。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/zzrD6kgYTibHtQWibXSiakQU8ZicMibA0ic9pibWLj8ib5TMvqoOIH2IYncsiaYSXUoBtVVugwvBDZ9jup6ABVXkMpKiccib7hnzwQN06ficicBQoBYeqibGs/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=15)

**2\. 大型几何模型（Large Geometry Models）**

PhysicsX于2024年底推出业界首个大型几何模型LGM-Aero，专为航空航天工程设计。训练数据涵盖超过2500万个网格、超过100亿个顶点，以及数万次CFD和FEA仿真结果。该模型参数量约1亿，与GPT-1相当，实现了对任何三维形状之间关系的理解。

工程师可以设定目标（如“提升散热效率且降低重量”），LGM-Aero在极短时间内生成、评估并筛选成千上万种设计变体。该模型是零样本学习器，在生成几何结构的同时零样本评估物理性能，完全绕开传统数值仿真，使设计概念研究时间从数月压缩至数小时。

![PhysicsX Launches LGM-Aero for Aerospace Engineering - Engineering.com](https://mmbiz.qpic.cn/sz_mmbiz_png/zzrD6kgYTibE8ZQVsJWiamy4HbfnIF2lbOsV2MQb9wmh6icEjaicB5gp42Rs80GBQBmVrIFkBUPGxjt76w644lJMY3nFxxXrMA8uQGN63RK3b0c/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=16)

PhysicsX Launches LGM-Aero for Aerospace Engineering - Engineering.com

**3\. 全生命周期闭环**

PhysicsX的平台不仅在研发端进行生成式设计，更打通了制造与运营全链路。在制造阶段预测工艺缺陷并优化生产参数；在运营阶段作为“虚拟传感器”实时评估设备性能，形成从设计到制造的闭环数字孪生能力。

微软和PhysicsX已达成战略合作，将PhysicsX的AI仿真平台集成至Microsoft Discovery平台，使智能体能够连续、大规模地设计、模拟、评估和迭代，从而压缩传统研发周期，在汽车、航空航天、半导体、能源等行业实现前所未有的自动化与优化水平。将物理知识与AI架构深度耦合，正是PhysicsX在工业软件领域最核心的差异化壁垒。

![PhysicsX - PhysicsX Forges Strategic Collaboration with Microsoft to  Accelerate Engineering Innovation with Microsoft Discovery](https://mmbiz.qpic.cn/sz_mmbiz_jpg/zzrD6kgYTibF5jGjsgJal7uqQ3icH6x5BSeXia54SH8R21FC67CTUxg6icBoARN3k9beKzVQk2bwH5ev639bFbhMxvnLvQ9DnGQHCNUk96Mon0A/640?wx_fmt=jpeg&from=appmsg&watermark=1#imgIndex=30)

PhysicsX - PhysicsX Forges Strategic Collaboration with Microsoft to Accelerate Engineering Innovation with Microsoft Discovery

### 三、团队基因：从F1到工业AI的工程积淀

PhysicsX由Robin Tuluie与Jacomo Corbo联合创立。Tuluie曾任雷诺（Alpine）F1与梅赛德斯F1研发主管，以及宾利汽车技术总监。Corbo曾任麦肯锡旗下AI公司QuantumBlack的首席科学家与联合创始人，同时担任雷诺（Alpine）F1首席比赛策略师。

![图片](https://mmbiz.qpic.cn/mmbiz_png/zzrD6kgYTibGXekeBEicEDZERNTkCJY3ib0Urvz6jeNXJJwGBw3nY3TtPjf03stZaDGIH7av2gdyQQ1bqCnoCvqGmo1zuKkV6iaBjImb10wVAD8/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=44)

两人从F1赛道的工程实践起步，后逐步将物理学与AI的交叉能力拓展至航空航天、能源、半导体等更广泛的工业领域。目前，公司团队已扩展至约350人，涵盖仿真工程师、机器学习专家、数据科学家与软件工程师，具有深厚的数值物理、企业级AI与先进工程背景。

2026年6月，PhysicsX完成3亿美元C轮融资，估值约24亿美元，由淡马锡领投，英伟达、Applied Materials、西门子等产业资本持续跟投。本轮融资将用于加速大型物理模型与大型几何模型的研发，以及全球市场拓展。资本的持续加注，不仅印证了物理AI在工业场景中的商业化前景，更将PhysicsX的团队能力与行业地位推向了新的高度。

## 四、护城河：数据、工程与客户绑定

PhysicsX的护城河并非依赖单一技术优势，而是由三层相互支撑的壁垒共同构成。

**1\. 物理数据资产**

**高质量工业仿真数据是物理AI最稀缺的资源。PhysicsX的训练数据覆盖超过2500万个零部件几何形状、数万亿网格单元，并涵盖了流体、热力学、结构力学、电磁场等多物理场耦合。随着客户在生产中使用，他们产生的新数据将持续回流到模型中，形成“数据飞轮效应”。使用越久，模型越精准，客户的切换成本也就越高。**

**2\. 工程知识与AI原生架构的融合**

工业AI的核心壁垒不在于模型架构本身，而在于背后所封装的、对物理定律和复杂工程流程的深刻理解。PhysicsX团队由约350名仿真工程师、物理学家和机器学习专家组成，兼具数值物理功底与AI工程化能力。

![图片](https://mmbiz.qpic.cn/mmbiz_png/zzrD6kgYTibEsvZI5obAkBSJQrnY6muegSMLTlEvTQnzsfvc9cPpZ8R2NumWiam8QRdDgYz7mLEYn3IOraGcySXje2Lok77aebdtt5r0BloDw/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=45)

更重要的是，公司采用AI原生架构，这区别于传统CAE软件“旧壳加AI”的修补式路径，而是从底层重新设计了工业计算范式，在计算速度、求解精度和发展迭代上具备代际优势。

**3\. 产业资本与客户深度绑定**

**PhysicsX的客户已涵盖Applied Materials、西门子、Stellantis等工业巨头，订单积压已达六个月。本轮融资中，英伟达、Applied Materials等产业资本持续加注，将PhysicsX视为自身AI战略的关键拼图。竞争对手或许可以复制算法，但难以复制公司在多年合作中积累的工业信任与协同网络。**

结语

如果说通用AI解决了智能的普惠化问题，那么以PhysicsX为代表的物理AI，正在直面工业创新的效率瓶颈。不久之后，AI生成的最优物理构型将无处不在：更高效的航空叶片、更低能耗的数据中心冷却系统、极限性能的电机结构。这些进步的背后，不再是枯燥的方程反复迭代，而是AI对物理定律的精准重写。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/zzrD6kgYTibFBfbibN4dZeMxCUMDBmLIpxQefdbYBz3q3GOemOIqZ0scicTNicUmArrCib0ia9W4tVxJEX6oa8xNZD9dsd4VdD4pdtlxty1CeXVls/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=46)

[前沿｜a16z领投，Town完成5500万美元融资，“记忆层”正成为个人AI助理的新护城河](https://mp.weixin.qq.com/s?__biz=MzA4NDcyMjg4Ng==&mid=2247484861&idx=1&sn=357b43df6fe1bc4846ab1ee6d106331b&scene=21#wechat_redirect)

[对话｜iPod之父Tony Fadell：AI降低了开发门槛，但伟大的产品靠的是品味、细节和讲故事](https://mp.weixin.qq.com/s?__biz=MzA4NDcyMjg4Ng==&mid=2247484848&idx=1&sn=863a406b7de64d0b5b2ab7fcbae74e5c&scene=21#wechat_redirect)

继续滑动看下一个

The Prospect

向上滑动看下一个