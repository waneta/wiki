---
title: "GPT-6.1发布：自此Codex 不必再死死绑在你开着的那台电脑上"
source: "https://mp.weixin.qq.com/s/jBnCU8uqZedV1vOa7i2RnQ"
author:
  - "[[麥柯Michael]]"
published:
created: 2026-10-09
description: "Codex 云端工作流更新：合上电脑，任务继续..."
tags:
  - "clippings"
---
麥柯Michael 麥柯Michael *2026年9月30日 10:40*

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/IxSNsOria2NRiambQS0nYfStkOXnOOiactjMcicR0hYUiaBw4iarJl5Q9sWqRictKYJyBPkbo5HuaGiagdCTsXUYUnmTzYQTaDyxcMU1yHguJGvEsa4/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

## Codex 云端工作流更新：合上电脑，任务还能继续

对用 Codex 做界面、修 Bug、开发小产品的人来说，这轮更新最实用的变化，是可以把开发任务交给云端运行，再从手机、网页或桌面端查看结果、继续修改。

例如，你让 Codex 为一个页面补上空状态，它可以在云端读取项目、修改代码并运行检查。你合上笔记本后，任务仍能继续；稍后打开手机，就能查看它改了哪些文件，再提出下一轮要求。

理解这次更新，需要分清三个环节： **准备开发环境、执行任务、审查结果。**

**开发环境可以提前准备，后续任务重复使用**

开发任务开始前，往往需要安装依赖、配置工具、确认版本和访问权限。项目越复杂，这些准备工作越容易耗时。

Codex Cloud 可以先为项目准备好一套环境。连接 GitHub 仓库后，Codex 会检查代码、安装依赖和工具、测试开发流程，并向你询问缺少的信息或权限。你检查设置和测试结果后，再发布这个环境。

这里的“发布”，指的是让准备好的开发环境可供后续任务使用，并不是把网站上线，也不是把代码公开。

之后，同一项目的新任务可以复用这套配置，同时拥有各自独立的工作区。这样既能减少重复准备，也能让不同任务的修改分别保留，方便检查和继续处理。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/IxSNsOria2NSnRVGy2F0Hl6moG5rTD3qjTictzZPFdbHtnalbUsls7RPZvx41iaF1lElJVMxD8KtMmqnAlECo9Ty3zL3OCiak4XSe80oPn9lbeQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

**选择云端运行，才可以摆脱本机持续开机的要求**

“用手机控制 Codex”和“让 Codex 在云里运行”是两件事。

如果任务仍在你的电脑上执行，远程访问只是换了一个操作入口；要让任务在电脑休眠后继续，应在创建任务时选择云端环境。Codex Cloud 的代码执行发生在云端，网页、手机和桌面端则用于查看进度、提出要求和检查结果。

对个人开发者和小团队来说，这能改变工作安排。你可以先交代一个范围明确的任务，离开电脑去处理其他事情，回来后集中看结果，而不必一直守着终端。

不过，任务仍需要清楚的目标和验收标准。例如，“优化这个页面”很难判断是否完成；“为订单列表增加空状态，保留现有布局，并检查移动端显示”就更容易执行和验收。

**Code Review 帮你理解改动，再决定如何处理**

代码生成之后，还需要回答几个问题：改动是否符合需求？有没有影响原有行为？有没有遗漏异常情况？

Code Review 用于检查这些变化。你可以查看文件差异，也就是 diff，让 Codex解释某段修改，或针对具体风险进行评审。例如：

“这次改动会不会导致未登录用户也能看到订单？”

相比只读一份“任务已完成”的摘要，结合代码差异和具体问题检查，更容易判断结果能不能接受。Codex 的评审会给出问题和依据；是否应用修复、提交代码或推送改动，仍由你决定。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/IxSNsOria2NQEX1mtWwqjtPHMnQUGvibrdOmGKhHFsWxLfs2v0st2JrDrEJIE5aNA91QUkiad5zCSgx3u413HSTjzG6XpgqavMcx6PqbgibBqas/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=2)

**Security Cloud 用于进一步检查仓库中的安全问题**

普通代码评审主要围绕当前改动。Codex Security Cloud 则可以对连接的 GitHub 仓库进行安全扫描，提供问题说明、相关代码、影响分析和验证依据。

使用前，需要先配置 Codex Cloud，并为目标仓库准备环境。创建扫描时，再选择仓库、分支、环境和扫描历史范围。初次扫描可能需要数小时，大型仓库或较长的历史范围会花费更多时间。

发现问题后，你可以查看证据，并从问题详情中发起修复 PR，把补丁交给正常的审核流程。

GPT-6.1 Sol 提供了一个成本更低的模型选择

同一轮更新中的 GPT-6.1 Sol，定位是以更低成本处理复杂编程、电脑操作和专业工作。OpenAI 将其描述为接近 Astra 的表现，同时建议用户用自己的任务比较两者。

它的标准 API 价格为每百万 token 输入 2 美元、缓存输入 0.10 美元、输出 10 美元。对需要反复修改、测试和评审的开发任务来说，成本降低具有实际意义。但模型表现如何，仍应看它在具体项目中的交付结果。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/IxSNsOria2NTxrElTVlxZYaU7QZGkuhzicnRFSzEhAa7O2zdgMVO6uwzdEWegwPYLicSaRrDHzjR4JmvKTibLIN02EPnFZpNdlzUpWiaPSCagodk/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=3)

**第一次尝试，可以从一个容易验收的小任务开始**

在 ChatGPT 网页或桌面端创建新任务，选择 **Work in → Cloud** ，然后创建或选择环境。

连接 GitHub 仓库，让 Codex 完成准备工作；检查设置和测试结果，再点击 **Publish** 。环境发布后，交给它一个小任务，例如补充空状态、修复一个明确的 Bug，或调整一处移动端布局。

接着合上电脑，稍后从手机查看进度和改动。检查它有没有完成要求、测试是否通过，再决定继续修改，还是提交代码。

对做界面和小产品的人来说，这套工作方式最直接的价值，是可以更灵活地分配时间：让 Codex 在云端执行明确的开发任务，自己把注意力放在需求、体验和结果验收上。

---

*欢迎加入讨论学习小组，加好友进群*

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/IxSNsOria2NSB5AHgUtH3uGYJs9iaVmNkd393ocbZ6S9EClq1KQlIrAUQfj2szeqBUkmxW2YzgOGTtvibmdXhmZDR2NdKpsWuLuqRe3kovl1EA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=4)

大家好，我是麦柯 Michael

设计师 / 开发者 / 摄影师

长期在设计、AI与工程的交汇处工作

**持续探索 Context Engineering 与 AI 辅助设计工作流**

和我一起用Vibe Code构建属于自己的产品！

Vibe Coding · 目录