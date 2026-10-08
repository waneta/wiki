---
title: "NVIDIA Newton 1.5 开源物理引擎更新，强化大规模机器人训练仿真"
source: "https://mp.weixin.qq.com/s/6ZAyjFaPMee3XUlYpym6Gw"
author:
  - "[[AI纪元志]]"
published:
created: 2026-08-17
description: "Newton 1.5 并行机器人仿真、选择性重置与接触物理\x0d\x0aNVIDIA Robotics 今日发布 Ne"
tags:
  - "clippings"
---
AI纪元志 AI纪元志 *2026年8月15日 13:42*

![Newton 1.5 并行机器人仿真、选择性重置与接触物理](https://mmbiz.qpic.cn/mmbiz_jpg/9OdJEsMRQmTkeCHXgUFpcfH3db8aIqsKibZEYWyY0aFsyXwediaAN9UAsH6AI76ynCkrX4iaPjlQPBtC9uEXfDuFpbJToGwYRiclrwyez7DfrI8/640?from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

Newton 1.5 并行机器人仿真、选择性重置与接触物理

NVIDIA Robotics 今日发布 Newton 1.5，这是这一开源 GPU 物理引擎自 2024 年 12 月由 NVIDIA、Google DeepMind 与 Disney Research 联合推出以来的又一次重要迭代。新版本围绕大规模机器人训练的核心痛点展开：更高的并行仿真效率、更低的内存占用、选择性重置机制、一致的接触物理，以及实验性的批处理 GPU 控制。对于正在 Isaac Lab 或 MuJoCo Playground 上跑大规模强化学习的团队来说，这些改动直接关系到训练吞吐和策略迁移的可靠性。

![Newton 1.5发布，带来更高并行仿真、更低内存、选择性重置、一致接触物理与实验性批处理GPU控制，显著提升机器人训练可靠性与规模](https://mmbiz.qpic.cn/mmbiz_png/9OdJEsMRQmRezewp7evNYYPY5TN5KxEgfOicZvMVWDep98UAZT63hiaDjf9ZECBbkSU39Bjv894usMdibq4Ijqic8NanBD258zucdd5Ga2UvlLE/640?from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

Newton 1.5发布，带来更高并行仿真、更低内存、选择性重置、一致接触物理与实验性批处理GPU控制，显著提升机器人训练可靠性与规模

Newton 1.5发布，带来更高并行仿真、更低内存、选择性重置、一致接触物理与实验性批处理GPU控制，显著提升机器人训练可靠性与规模

，时长00:10

<video src="https://mpvideo.qpic.cn/0bc3qqayuaabjiahgtt6vrvfdbgdrkcadcqa.f10002.mp4?dis_k=0a940dcb8b2b221273b1840a72974550&amp;dis_t=1786955688&amp;play_scene=10120&amp;auth_info=dfHSnfYEanFD7KDtu3ZbQT9CODdkH2YyTS5AUXdyFwFTJnB/Y0sVCzIHdmh8Tldi&amp;auth_key=145c403f068c1011bd283f46f0af9df9&amp;vid=wxv_4650302816408305665&amp;format_id=10002&amp;support_redirect=0&amp;mmversion=false" controls="">您的浏览器不支持 video 标签</video>

## 从 Isaac Sim 到 Newton：一次架构上的重新定位

要理解 Newton 1.5 的意义，需要先看清它在 NVIDIA 机器人技术栈中的位置。Newton 并非 Isaac Sim 的替代品，而是建立在 NVIDIA Warp 与 OpenUSD 之上的独立物理引擎，由 Linux Foundation 管理，采用 Apache-2.0 许可证。它兼容 MuJoCo Playground、Isaac Lab 和 Isaac Sim，核心设计目标是 GPU 加速、可插拔求解器、可微分物理，以及从刚体到软体、接触、摩擦、执行器和传感器的统一建模。

开发者 Henri 在回应 Newton 1.5 发布时表示，自己一直在深入使用 Isaac Sim，期待跳入 Newton 的生态。这种从 Isaac Sim 向 Newton 转移的兴趣并非个例——Newton 的定位恰恰是补足 Isaac Sim 在大规模并行仿真上的短板，让研究者可以在 GPU 上同时跑数千个环境，而不是受限于 CPU 单线程的仿真瓶颈。

![开发者反馈正从Isaac Sim转向Newton，期待新版本在实际机器人仿真中的表现](https://mmbiz.qpic.cn/sz_mmbiz_png/9OdJEsMRQmSn1LPO1hXmKribJcPqQzlF3u1duBGqjh2tAF8G79NujNicmfeuJA7OicH6uKJ37OdO652Y6BEaAbb2Xn348cZCd7Y8WbXiaMbtFnk/640?from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=2)

开发者反馈正从Isaac Sim转向Newton，期待新版本在实际机器人仿真中的表现

开发者反馈正从Isaac Sim转向Newton，期待新版本在实际机器人仿真中的表现

，时长00:25

<video src="https://mpvideo.qpic.cn/0bc3cmasgaab4ianult6nzvfce6demjqciya.f10002.mp4?dis_k=89af00603c0918677a0fdf6272f05224&amp;dis_t=1786955688&amp;play_scene=10120&amp;auth_info=frmj0foKbXRDvvK65yRdEj9CZzBlGGE2RXYYA3cmQlNYJ3IkYEESDjJVJD8gHFEx&amp;auth_key=9632355bde07ae0872f4c4d5fc95b694&amp;vid=wxv_4650303409181376514&amp;format_id=10002&amp;support_redirect=0&amp;mmversion=false" controls="">您的浏览器不支持 video 标签</video>

## 选择性重置与内存优化：大规模训练的两个关键瓶颈

Newton 1.5 最值得关注的改动是选择性重置（selective resets）。在强化学习训练中，当某个仿真环境中的智能体任务失败时，传统做法是重置整个环境，这会导致大量计算资源的浪费。选择性重置允许只重置失败的环境，而保留仍在正常推进的环境，从而显著提升训练效率。

内存优化同样关键。大规模并行仿真面临的核心约束之一就是 GPU 显存——每个仿真环境都需要存储状态、接触信息、传感器数据等，环境数量上去之后，显存很快成为瓶颈。Newton 1.5 在内存占用上的优化，直接意味着同一块 GPU 上可以跑更多的并行环境，或者为更复杂的场景留出余量。

这两个改动叠加在一起，指向的是同一个目标：让机器人训练在规模上更接近大语言模型训练的方式——不是靠单个环境的精确模拟，而是靠海量环境的并行探索。

## 一致接触物理：仿真到现实的鸿沟

接触物理的一致性，是仿真引擎最容易被忽视却又最致命的环节。机器人抓取、操作、行走，本质上都是接触问题——手指与物体接触、脚底与地面接触、工具与工件接触。如果仿真中的接触模型与真实物理不一致，策略在仿真中学到的行为迁移到真实机器人上就会失效，这就是所谓的 sim-to-real gap。

Newton 1.5 强调的一致接触物理（consistent contact physics），意味着在不同求解器、不同时间步长、不同硬件条件下，接触行为的表现保持一致。这对策略的稳定迁移至关重要——训练时的仿真行为越接近真实物理，部署时的意外就越少。

## 实验性批处理 GPU 控制与更干净的导入流程

批处理 GPU 控制（batched GPU control）是 Newton 1.5 中的实验性功能。在传统仿真中，控制策略通常在 CPU 上计算，然后传给 GPU 上的仿真环境。批处理 GPU 控制将策略推理也放到 GPU 上，减少了 CPU-GPU 之间的数据传输开销，进一步提升了训练吞吐。这一功能目前标记为实验性，意味着 API 可能在未来版本中调整，但方向已经明确：整个训练管线都在向 GPU 端迁移。

此外，Newton 1.5 改进了 USD/MJCF 导入流程。MJCF 是 MuJoCo 的场景描述格式，USD 则是 NVIDIA 力推的通用场景描述标准。更干净的导入意味着从 MuJoCo Playground 迁移到 Newton 的摩擦更小，开发者不需要花大量时间处理格式转换和资产兼容问题。

## 前代基线：1.4 的性能数据与 1.5 的增量判断

要评估 Newton 1.5 的实际增益，需要参考 1.4 版本的公开基线。根据 Newton v1.4.0 官方发布说明，该版本已引入实验性的求解器组合（coupled solver composition）、可移植的确定性执行、变形体 USD 工作流和 VBD 软体接触改进。官方给出的代表性性能数据包括：大型 GPU 批量 MuJoCo 工作负载约快 15%–26%，部分 Allegro 工作负载约快 11%，布料和接触密集场景约快 10%–13%。

这些数据是 1.5 之前的基线，不能直接等同于 1.5 的增益。但可以看出，Newton 在批量 MuJoCo 工作负载上的性能优势已经相当明显，而 1.5 在此基础上进一步优化了并行仿真和内存占用。对于已经在使用 MuJoCo 的团队来说，Newton 提供了一个 GPU 加速的替代路径，而不需要放弃现有的 MJCF 资产。

## 软体物理的持续短板

开发者 Numan 在 Newton 1.5 发布后评论道："still havent solved the deformables i see"——可变形体的问题仍然没有解决。这一评论指向仿真引擎在软体物理上的持续短板。

![指出可变形体（deformables）问题仍未解决，提醒仿真引擎在软体物理上的持续短板](https://mmbiz.qpic.cn/sz_mmbiz_png/9OdJEsMRQmSeExPiacRCNsLiaApqICyj3sWz4WwNtpJ07Wwo08EsfeMg9FsKA4HSgtKnkMddbF892fS0EFjAZmXq3Y3XDlXOOrTg9XRHtGQhM/640?from=appmsg&watermark=1#imgIndex=3)

指出可变形体（deformables）问题仍未解决，提醒仿真引擎在软体物理上的持续短板

这并非无的放矢。虽然 Newton 1.4 已加入 VBD 软体接触改进和变形体 USD 工作流，但可变形体的精确模拟——比如布料折叠、海绵压缩、绳索缠绕——仍然是物理仿真中最困难的问题之一。软体物理需要极高的空间和时间分辨率才能获得准确结果，这与大规模并行仿真的效率诉求存在天然张力。Numan 的评论提醒我们，Newton 在刚体仿真上的优势并不自动延伸到软体领域，对于需要精细软体操作的机器人任务（如衣物折叠、线缆操作），仿真引擎的选择仍需谨慎。

## 开源治理与部署边界

Newton 由 Linux Foundation 管理，采用 Apache-2.0 许可证，这意味着它可以被自由使用、修改和商用，而不需要担心授权问题。但开源不等于任意硬件可用——根据官方 GitHub 仓库，Newton 要求 Python 3.10 以上，Linux 和 Windows 平台需要 NVIDIA Maxwell 或更新的 GPU 与较新驱动，macOS 仅支持 CPU 运行。

这一部署边界对研究团队有实际影响：如果训练集群使用的是较老的 GPU，或者开发环境是 macOS，Newton 的 GPU 加速优势就无法充分发挥。对于生产环境，这意味着需要评估现有硬件是否满足要求，而不是默认"开源=随处可跑"。

## 判断：Newton 的定位与边界

Newton 1.5 的发布，标志着 NVIDIA 在机器人仿真领域的一次明确发力。它不是要取代 MuJoCo 或 Isaac Sim，而是提供了一个 GPU 原生的、可扩展的、面向大规模并行训练的物理引擎选项。选择性重置、内存优化和批处理 GPU 控制，都是针对强化学习训练的实际瓶颈做的针对性改进。

，时长00:11

<video src="https://mpvideo.qpic.cn/0bc3fqcv4aafxmakovt26fvfklgdlywakxqa.f10002.mp4?dis_k=30c6e57c53494f066d504c2b37631515&amp;dis_t=1786955688&amp;play_scene=10120&amp;auth_info=eN7ntotVa3VCu/fstyFZQjtHNzNhH2I3Tn8aUyIjQwBed3YkZR8UDzNQIWlwGVVh&amp;auth_key=e04a88114f40ae87fbfa3df57fb6a062&amp;vid=wxv_4650301887723012097&amp;format_id=10002&amp;support_redirect=0&amp;mmversion=false" controls="">您的浏览器不支持 video 标签</video>

但 Newton 的边界同样清晰：软体物理仍是短板，实验性功能需要时间成熟，硬件要求限制了部署范围。对于刚体操作、抓取、移动等任务的大规模训练，Newton 1.5 提供了值得认真评估的路径；对于依赖精细软体模拟的任务，现有方案可能仍然更合适。

开发者从 Isaac Sim 转向 Newton 的兴趣，反映了社区对 GPU 原生仿真引擎的期待。这种期待能否转化为实际的生产力提升，取决于 Newton 在真实训练工作负载中的表现，以及 NVIDIA 能否在后续版本中补齐软体物理的缺口。就目前而言，Newton 1.5 是一个方向明确的进步，但远未到"解决所有仿真问题"的程度。

**参考资料**

- NVIDIA Robotics 官方推文：Newton 1.5 发布：https://x.com/NVIDIARobotics/status/2088371040582017142
- NVIDIA Developer：Newton Physics Engine 官方文档：https://developer.nvidia.com/newton-physics
- Newton Physics / Linux Foundation：GitHub 仓库：https://github.com/newton-physics/newton
- Newton Physics：v1.4.0 Release Notes：https://github.com/newton-physics/newton/releases/tag/v1.4.0
- 开发者 Henri 对 Newton 1.5 的回应：https://x.com/HardAtWorkHenri/status/2088438847281475622

机器人 · 目录