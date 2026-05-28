---
title: "NVIDIA：遥操作将退场，机器人正在冲向“终局”"
source: "https://mp.weixin.qq.com/s/82LVtUTpPramzkgpiks4Fg"
author:
  - "[[Jim Fan]]"
published:
created: 2026-05-18
description: "2040 年：机器人的“终局终点”"
tags:
  - "clippings"
---
Jim Fan *2026年5月14日 00:00*

## 那是在 2016 年的一个夏日。实际上，就在我们现在所在的这间办公室里，有一个穿着闪亮皮夹克、胳膊肌肉很壮的人，正扛着一块巨大的金属托盘。在这块大金属板上，他写下了：“致 Elon 和 OpenAI 团队，致计算与人类的未来，我向你们呈现世界上第一台 DGX-1。”

本文来源于 Jim Fan，翻译整理而来，仅供参考。如需查看英文原版及更多资料，可在文末获取。

![图1：2016 年 Jensen Huang 向 Elon Musk 与 OpenAI 团队赠送首台 DGX-1](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图1：2016 年 Jensen Huang 向 Elon Musk 与 OpenAI 团队赠送首台 DGX-1

那是我第一次见到 Jensen。作为一名合格的实习生，我当然赶紧冲过去排队，在上面签下了自己的名字。Andre Karpathy 的名字也在旁边。现在想来，我们似乎真的要一起进入计算机历史博物馆了。我感觉自己像个恐龙。

你知道，那时候我完全不知道自己究竟参与到了什么事情里。而接下来发生的一切，没有人能比 Ilya 本人描述得更好：“如果你相信深度学习，深度学习也会相信你。”而天哪，深度学习后来真的是狠狠地“相信”了我们所有人。

三次阶跃式跃迁，六年时间。这就是把我们带到今天所需要的一切。第一个跃迁，GPT-3：预训练。“预测下一个 token”，本质上是在学习语法规则、语言的形状。它是在模拟思想、代码，以及更一般意义上的字符串，应当如何展开。2022 年，InstructGPT：监督微调，把这种模拟能力对齐到“能真正完成有用工作”的方向上。第三阶段，推理：使用强化学习超越模仿学习；再往后，是自动化研究，让整个循环加速到超出人类能力边界的程度。

![图2：Jim Fan 总结的大模型三次阶跃式跃迁](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图2：Jim Fan 总结的大模型三次阶跃式跃迁

所以，正如 Andre 所说，所有实验室都已经打到了最终 Boss 战。对于大语言模型来说，它们已经深陷“终局阶段”。说实话，我非常嫉妒。看看 Andre 当时笑得多开心，脸上挂着大大的笑容。搞 LLM 的人，正处在人生最盛大的派对里。他们正在依靠一种名字就很神秘、真的叫“methos”的神兽，速通 AGI。

那为什么机器人不能也来分一杯羹？所以，作为一名自尊自爱的科学家，我选择抄作业，然后给它起个新名字。我把它叫作：伟大的平行线（The Great Parallel）。

与其模拟字符串，我们能不能去模拟“下一个物理世界状态”？然后，再通过动作微调，把这种模拟能力对齐到现实机器人真正需要的那一小片区域上。最后，让强化学习完成“最后一公里”。就是这样。伟大的平行线：复制 LLM 的成功经验。打不过它们，就加入它们。

所以，请和我一起进入新的篇章：机器人，终局阶段。

那么，我们要如何打这场终局之战？归根到底，是两件事：模型战略与数据战略。

## 一、模型战略：从 VLA 走向世界动作模型

先来看模型。过去三年，领域主流是 VLA，也就是视觉—语言—动作模型（Vision-Language-Action Models）。像 Pi 和 GR00T 这样的模型，都属于这一类。它们的基本假设是：预训练由 VLA 完成，然后我们只需要在上面接一个动作头就可以了。

![图3：VLA 模型的典型路线](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图3：VLA 模型的典型路线

但认真想一想，这些模型其实更像是 LVA。因为参数量最多的部分，实际上都给了语言。所以，它们的优先级是：语言是一等公民，接下来才是视觉，最后才是动作。从设计上看，VLA非常擅长编码“知识”和“名词”，但并不那么擅长编码“物理”和“动词”。可以说，它们的“头部”长得有点偏，资源放错了地方。

这是我最喜欢的一个例子，来自最初那篇 VLA 论文：“把可乐罐移动到 Taylor Swift 的图片旁边。”没错，模型之前并没有见过 Taylor Swift。没错，它能够完成泛化。但这并不是我们真正想要的那种“预训练能力”。

![图4：VLA 模型将可乐罐移动到 Taylor Swift 图片旁边](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图4：VLA 模型将可乐罐移动到 Taylor Swift 图片旁边

那么，第二种预训练范式是什么？我过去一直以为，它会是某种极其宏大的东西。很遗憾，结果它居然是我们所谓的——AI 视频垃圾（AI video slop）。你知道，我可以整天看这些“监控摄像头里猫在弹班卓琴”的视频。这就是互联网巅峰内容。但说真的，看看这些东西，谁会认真对待它们？

![图5：Jim Fan 用 AI 视频垃圾引出第二类预训练范式](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图5：Jim Fan 用 AI 视频垃圾引出第二类预训练范式

直到我们意识到：这些视频模型，实际上正在内部学习如何模拟“下一个世界状态”。这里展示的是一些 VEO-3 的 rollout。你可以看到，模型学会了重力、浮力、光照、反射、折射。这一切都不是人手工写进去的。当模型在大规模数据上预测“下一团像素”时，物理规律会自然浮现出来。

![图6：VEO-3 在视频生成中展现物理规律学习能力](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图6：VEO-3 在视频生成中展现物理规律学习能力

甚至，视觉规划能力也会浮现。看看 VEO 是怎么解迷宫的。它是通过在像素空间中向前运行模拟来解决的。请特别注意右下角这个例子。这是我最喜欢的一个。我们来看一下，眨眼就会错过 VEO-3 是怎么解决这个问题的。它太聪明了。VEO-3 发现：只要你没看见，几何结构就是可选项。我把这种现象叫作“物理垃圾”（Physics Slop）。

![图7：视频世界模型尝试在像素空间中进行视觉规划](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图7：视频世界模型尝试在像素空间中进行视觉规划

那么，我们怎样才能让这些世界模型变得真正有用？答案是：动作微调（Action Fine-Tuning）。我们把“所有可能未来状态的叠加”，对齐并坍缩到现实机器人真正需要的那一小段状态空间上。

于是，我们提出了 Dream Zero。这是一种新型策略模型。它会先“梦见”未来几秒钟可能发生什么，然后据此采取动作。而运动动作本质上，是高维、连续的信号，看起来其实和像素非常相似。所以，我们可以在渲染视频的同时，同步渲染动作。也就是说，Dream Zero 会联合解码下一个世界状态与下一个动作。

![图8：Dream Zero 执行未见过的解鞋带任务](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图8：Dream Zero 执行未见过的解鞋带任务

结果是，它能够以零样本方式解决训练中从未见过的任务和动作。而当机器人实际执行动作时，我们还可以可视化它“正在梦见什么”。二者之间的相关性非常强：如果视频预测对了，动作就对；如果视频出现幻觉，动作就失败。

![图9：Dream Zero 的世界模型视图与机器人动作同步展示](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图9：Dream Zero 的世界模型视图与机器人动作同步展示

所以，再一次，视觉和动作现在成为了一等公民。我们也用 Dream Zero 做了很多有趣的实验。比如，我们就在实验室里随便推着机器人走来走去，然后往提示框里随机输入一些任务。当然，Dream Zero 不可能对所有任务都做到 100% 稳健。但它有点像 GPT-2，已经开始试图在每一种情况下，抓住“运动形状”的核心。

![图10：Dream Zero 在多类开放任务上的尝试](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图10：Dream Zero 在多类开放任务上的尝试

因此，Dream Zero 是我们通往机器人开放式、开放词表提示的第一步。我们把这种新模型称为：世界动作模型（World Action Models，WAM）。所以，让我们为亲爱的 VLA 默哀片刻。它们已经很好地服务了我们。安息吧。世界动作模型万岁。

![图11：Jim Fan 以幽默方式宣告 VLA 退场、WAM 登场](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图11：Jim Fan 以幽默方式宣告 VLA 退场、WAM 登场

## 二、数据战略：从遥操作到“传感化人类数据”

接下来，是数据战略。这是 NVIDIA 首席科学家 Bill Dally，正在我们实验室里做遥操作。考虑到他的薪资水平，我认为这大概是我们数据集中“最昂贵的一条遥操作轨迹”。

过去三年，是遥操作主导的时代。这是它的黄金年代。VR 头显、为流媒体传输极致优化的低延迟系统，还有这些看上去像中世纪刑具一样复杂的装置。行业投入巨大，研究者也吃了很多苦。但即便如此，遥操作天然受限于一个物理上限：每台机器人，每天最多只有 24 小时数据。实际上，我骗谁呢？更接近真实情况的数字，大概是每台机器人每天 3 小时，而且还得是在机器人之神愿意眷顾你的前提下，因为这些机器人一天到晚都在闹脾气。

![图12：过去三年机器人数据采集高度依赖遥操作](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图12：过去三年机器人数据采集高度依赖遥操作

那么，能不能做得更好？不如这样：你直接把机器人的手，穿戴到自己的手上。这就是所谓的 UMI，也就是通用操控接口（Universal Manipulation Interface）。它的想法看似简单，实际上极其巧妙：你把机器人的执行器穿戴在手上，然后直接以人类自然操作的方式采集数据，同时把机器人身体的其余部分排除在数据采集环节之外。

![图13：UMI 通用操控接口](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图13：UMI 通用操控接口

我甚至会说，UMI 可能是机器人数据领域有史以来最伟大的论文之一。它还催生出了两家独角兽初创公司。左边是 Genesis，它改进了这一设计，让你可以把夹爪戴在这里。右边是 Sunday，它做出了这些三指数据手套。

![图14：UMI 思路催生夹爪穿戴设备与数据手套](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图14：UMI 思路催生夹爪穿戴设备与数据手套

去年，我们又往前迈了一步。我们设计了一种外骨骼，可以与五指灵巧机器人手实现一一映射。我们把它称为 Dex UMI。来看看它的实际表现。左边，人类直接采集数据，永远是最快的。右边，你可以看到遥操作有多么困难。人类操作者，这里甚至是我们最熟练的博士之一，也必须极其小心地对齐位置。速度非常慢，成功率也很低。而中间，你只需要戴上外骨骼，就可以直接采集数据。

![图15：Human Direct、DexUMI 与 Teleop 的数据采集效率对比](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图15：Human Direct、DexUMI 与 Teleop 的数据采集效率对比

然后，我们用这些数据训练一个机器人策略。你现在看到的是一个完全自主运行的机器人，而这个策略模型的训练中，使用了零遥操作数据。这意味着，我们打破了“每台机器人每天最多 24 小时”的魔咒。你看这些机器人有多开心，因为它们再也不需要被绑在数据采集流程里了。

![图16：基于 Dex UMI 数据训练出的完全自主策略执行](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图16：基于 Dex UMI 数据训练出的完全自主策略执行

那么，这就是答案吗？我们已经解决机器人数据扩展问题了吗？当你开车的时候，你实际上正在为世界上最大的“物理数据飞轮”贡献数据。而这件事最美妙的地方在于：你甚至感觉不到它的存在。在 FSD 过程中，数据上传只是一个自然而然、在背景中发生的过程。

![图17：自动驾驶中的数据飞轮](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图17：自动驾驶中的数据飞轮

但是，穿戴这些 UMI 或数据可穿戴设备，依然很麻烦。它是侵入式的。它没有“每天开车上班”那么无感和顺畅。所以，我们需要一个 FSD 等价物。数据采集必须从人的注意力中消失，退到背景里。这样，我们才能捕捉到人类灵巧性的全部光辉：覆盖所有生活方式，覆盖所有具有经济价值的劳动形式。

因此，我们全面押注人类第一视角视频（Human Egocentric Videos）。这些视频还要附带详细标注，比如手部位置追踪、高密度语言标注。于是，我们提出了 Ego-Scale。

![图18：人类第一视角视频数据](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图18：人类第一视角视频数据

![图19：第一视角视频中的手部追踪与高密度语言标注](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图19：第一视角视频中的手部追踪与高密度语言标注

这个系统 99.9% 的训练，都来自人类第一视角视频。最终得到的是一个端到端策略模型：它可以直接从摄像头像素，映射到 22 自由度高灵巧机器人手。你现在看到的，是完全自主执行。

![图20：Ego-Scale 驱动高灵巧机器人手自主执行](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图20：Ego-Scale 驱动高灵巧机器人手自主执行

我们使用 2.1 万小时野外真实第一视角人类数据，对 Ego-Scale 进行预训练。其中，完全没有使用任何机器人数据。在预训练阶段，我们预测手部关节和手腕位姿。随后进入动作微调阶段：我们只采集了 50 小时高精度动作捕捉数据手套数据，以及 4 小时遥操作数据。只有 4 小时遥操作，在整个训练混合数据中的占比不到 0.1%。

![图21：Ego-Scale 预训练数据规模](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图21：Ego-Scale 预训练数据规模

![图22：Ego-Scale 在动作微调阶段使用机器人数据](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图22：Ego-Scale 在动作微调阶段使用机器人数据

凭借这些，Ego-Scale 已经能够泛化到极具灵巧性的任务上，比如整理卡片，或者操作注射器。对，甚至包括液体转移。你知道，也许未来某一天，我们家里会有机器人护士。那不妨提前试试看。对于这类任务，模型在测试时只需要一次演示，就可以学会不同的叠衣策略。

![图23：Ego-Scale 完成注射器液体转移任务](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图23：Ego-Scale 完成注射器液体转移任务

![图24：Ego-Scale 通过一次演示学习不同叠衣策略](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图24：Ego-Scale 通过一次演示学习不同叠衣策略

而这篇论文最迷人的发现，也许是：我们发现了一个关于灵巧性的神经缩放定律。预训练投入的小时数，与最优验证损失之间，存在非常清晰的关系。事实上，它可以用一个非常干净的对数线性数学方程来描述。这发生在语言模型原始神经缩放定律提出六年之后。

![图25：灵巧性神经缩放定律](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图25：灵巧性神经缩放定律

如果把这些数据战略全部放到一张图上：横轴是与机器人硬件的对齐程度，纵轴是可扩展性。那么会看到，遥操作的可扩展性最差；数据可穿戴设备，可以扩展到数十万小时；第一视角视频，如果我们能转动这个 FSD 式飞轮，明年左右轻松达到 1000 万小时。

![图26：遥操作、数据穿戴设备与第一视角视频的扩展性对比](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图26：遥操作、数据穿戴设备与第一视角视频的扩展性对比

如果我们在图中画一条线，这条线左侧的一切，都代表一种新范式：传感化人类数据（Sensorized Human Data）。所以，让我做几个预测。未来一到两年里，遥操作占比会持续下降，最终降到几乎可以忽略不计。随后，会出现一整套针对不同硬件和不同应用场景，专门设计的数据可穿戴设备。最后，机器人的主要“食粮”，将变成人类第一视角视频。

所以，让我们为亲爱的遥操作默哀片刻。它已经很好地服务了我们。安息吧。传感化人类数据万岁。

## 三、环境战略：把现实世界搬进可扩展训练系统

我们的数据战略讲完了吗？你注意到我在“数据战略”外面画了两个圆环吗？外圈是什么？

所有处在前沿的大模型实验室，如今都投入了大量预算，去获取数以百万计的编程环境，用于强化学习。机器人也是一样。我们迫切需要把环境规模扩起来。

当然，你永远可以直接在真实机器人上做强化学习。在我们的实验室里，我们就用 RL 把某些任务推到了接近 100% 的成功率。这样，它们就能连续执行数小时。你知道，看着这些机器人自己组装 GPU，其实有种莫名的疗愈感。或者，用某位智者的话说：“好孩子，这个任务已经被我老板批准了。”

![图27：真实机器人强化学习任务连续执行](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图27：真实机器人强化学习任务连续执行

![图28：真实机器人连续执行任务超过 3 小时](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图28：真实机器人连续执行任务超过 3 小时

但是，如果沿用这种方式，我们不可能得到 100 万个环境。因为那就意味着你需要 100 万台机器人。所以，我们需要更好的办法。

例如，你拿一张 iPhone 照片，把它输入一个 3D 世界扫描流程中，系统就能提取出场景中的全部物体，然后自动在一个经典物理模拟器里重新合成它们。扫描完成后，这些物体其实都可以互动。随后，你还可以在模拟环境中无限增强它们，生成各种变化版本。我们把这些变化称为“数字表亲”（Digital Cousins）。

![图29：真实桌面场景作为世界扫描输入](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图29：真实桌面场景作为世界扫描输入

![图30：真实场景被重建为可交互模拟环境](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图30：真实场景被重建为可交互模拟环境

![图31：数字孪生与数字表亲](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图31：数字孪生与数字表亲

于是，iPhone 在这个过程中，基本就变成了一个口袋里的世界扫描仪。我们把这一过程称为 Real-to-Sim-to-Real。通过这种方式，我们拥有了一种可扩展的方法，把物理世界迁移到数字世界。

![图32：Real-to-Sim-to-Real 流程](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图32：Real-to-Sim-to-Real 流程

但即便如此，这种方法仍然依赖传统图形引擎。我们能不能做得更好？于是，我们提出 Dream Dojo。这是我们对视频世界模型的一种延展，把它们进一步变成真正意义上的神经模拟器。

![图33：Dream Dojo 学习不同机器人形态的动作与动力学](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图33：Dream Dojo 学习不同机器人形态的动作与动力学

![图34：Dream Dojo 中的双臂操作场景](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图34：Dream Dojo 中的双臂操作场景

Dream Dojo 的输入，是连续动作信号；输出，则是下一帧 RGB 图像，以及传感器状态，而且是实时输出。你现在看到的画面里，没有一个像素是真实拍摄的。Dream Dojo 可以完全通过数据驱动的方式，捕捉并学习不同机器人的力学机制。整个过程中，没有物理方程，没有图形引擎。

因此，机器人新的后训练范式，会是一个大规模并行强化学习系统：少量真实机器人工作站，一批运行世界扫描的图形计算核心，以及大规模推理算力，用来运行世界模型。或者可以用一个公式来表达：算力 = 环境 = 数据。又或者，借用某位智者的话：“你买得越多，省得越多。”而这条信息，已经得到了我老板的批准。

![图35：真实世界、世界扫描与世界模型共同构成并行强化学习系统](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图35：真实世界、世界扫描与世界模型共同构成并行强化学习系统

## 四、伟大的平行线：机器人将如何进入终局

所以，就是这样。把所有东西合在一起，就得到机器人将要遵循的那条“伟大的平行线”。而这一切，正在我们说话的此刻发生。我们正站在终局阶段的开端。

我喜欢把自己的研究理解为：在文明科技树上解锁一个又一个成就。

![图36：机器人技术树仍有关键成就待解锁](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图36：机器人技术树仍有关键成就待解锁

对于机器人来说，还有三个成就需要解锁。完成之后，我们就结束了。我就可以退休了。我已经迫不及待了。

## 五、机器人还需解锁的三个终极成就

### 1\. 通过“物理图灵测试”

第一项成就，是通过物理图灵测试。在广泛的活动中，你无法判断一个任务究竟是人完成的，还是机器人完成的。当然，也许醉酒状态的人类不算。物理图灵测试的核心，是实现“单位能量输入，单位劳动输出”。只看这台机器人摆出的性感姿势，我觉得我们还有很多工作要做。所以，这件事也许还要两到三年。

![图37：物理图灵测试](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图37：物理图灵测试

### 2\. 实现“物理 API”

第二项成就，是物理 API。你拥有一整支机器人舰队，它们可以像任何软件一样，通过 API 和命令行进行配置。终有一天，它们也许会由 Opus 9.0 来统一编排。如果我们拥有这种物理 API，就能够实现“黑灯工厂”。它们本质上会成为“原子的打印机”：输入是 Markdown 文件里的设计方案，输出则是完整装配好的产品，全过程完全自主完成。

![图38：物理 API](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图38：物理 API

或者，它们也可以变成湿实验室，在化学、生物学和医学领域，自动化推进科学发现。

![图39：机器人驱动自动化科学实验](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图39：机器人驱动自动化科学实验

### 3\. 进入“物理自动研究”

最后一站，是物理自动研究。当机器人开始自主设计、改进并制造自己的下一代版本，其速度和能力将远远超出人类极限。

## 六、2040 年：机器人的“终局终点”

你可能会问，这是不是太科幻了？我们有生之年真的能看到吗？那么，回头看看 AI 社区。从 2012 年 AlexNet 的第一次前向传播，那个几乎只会勉强分辨猫和狗的模型，到今天，2026 年的 AI Ascent，我们已经开始讨论“智能体自动研究”。这中间只花了 14 年。

![图40：从 2012 年 AlexNet 到 2026 年 AI Ascent](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图40：从 2012 年 AlexNet 到 2026 年 AI Ascent

那我们再加 14 年，怎么样？2026 年，正好位于 2012 和 2040 的正中间。而技术并不是线性进步，它是指数级进步。所以，我可以以 95% 的确信程度说：到 2040 年，我们将走到终局的终点，走到整棵科技树的尽头。而那时候，我们依然还年轻。

![图41：Jim Fan 展望 2040 年机器人终局](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图41：Jim Fan 展望 2040 年机器人终局

如果你相信机器人，机器人也会相信你。

对于在座的所有人来说，我想，我们这一代人生得太晚，没能去探索地球；又生得太早，还无法去探索群星；但我们恰好生在了这样一个时代：正好来解决机器人。

---

声明：本文基于 https://www.youtube.com/watch?v=3Y8aq\_ofEVs 仅供学习交流参考，不构成任何投资建议。致敬原作者，原文版权归原作者及原平台所有，如涉及版权问题，请联系后台处理。本文未经授权，禁止转载。

---

👇 ****扫码加入「AI工业/机器人」知识星球，获取更多资料****

****![](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)****

继续滑动看下一个

AI工业

向上滑动看下一个