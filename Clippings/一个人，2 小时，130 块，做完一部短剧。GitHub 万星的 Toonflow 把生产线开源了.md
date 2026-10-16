---
title: "一个人，2 小时，130 块，做完一部短剧。GitHub 万星的 Toonflow 把生产线开源了"
source: "https://mp.weixin.qq.com/s/x3yNOqxDoMckJ9tV4br7Nw"
author:
  - "[[竹苏]]"
published:
created: 2026-10-10
description: "最近刷短视频，总能刷到 AI 漫剧。画面精致，节奏飞快，评论区一水儿的「这居然是 AI 做的」。"
tags:
  - "clippings"
---
竹苏 CODE有戏 *2026年9月24日 19:05*

最近刷短视频，总能刷到 AI 漫剧。

画面精致，节奏飞快，评论区一水儿的「这居然是 AI 做的」。

但你自己动手做一部试试就知道了。剧本、分镜、出图、配音、剪辑，五个环节五套工具，中间全靠人肉搬运。

最要命的是角色一致性。上一个镜头主角还是长发，下一个镜头换了张脸，观众直接出戏。

前段时间我在 GitHub 上闲逛，看到一个叫 Toonflow 的项目。Star 已经破万，MIT 协议，完全免费。

它想干的事就一件， **把「小说到成片」这整条流水线，塞进一个软件里** 。

我把它的 README 和文档翻了一遍，挺有意思。今天跟你聊聊它是什么，能干什么，怎么装，以及什么人适合上手。

![图片](https://mmbiz.qpic.cn/mmbiz_png/iapI7WE6qru5Nqj8NNibprnjIBVm3cYG6UEDhialH4xLpMFHcL3KVG6iaRgDiblx4jP55VEx9p4mU4wwCss6ibq00DVWquGW43M0Jbib95T7Pz1mtc/640?wx_fmt=png&from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

Toonflow 项目首页与灵感创作（图源 GitHub 官方仓库）

01

它到底是什么

Toonflow 是一个开源的 AI 短剧、漫剧创作平台，背后的开发团队是北京爱阿科技。

一句话说清它的定位。粘一段小说进去，它帮你生成剧本、拆分镜、批量出图、合成视频，抖音竖屏和 B 站横屏都能直接导出。

看两组数据。

一组是热度。GitHub Star 破万，官方社群用户 6000+，冲上过 GitHub 趋势榜。对一个新项目来说，这个速度不算常见。

另一组是工程量。README 里写着，从第一行代码到现在 130 天，20 个版本，800 多次 commit，21 万行代码，中途推翻重写了三次，最后把协议从 Apache-2.0 换成了更宽松的 MIT。

没有任何商业附加条款，你可以拿它做任何事。

技术栈是 TypeScript 加 Vue 3，运行时用 Bun，桌面端覆盖 Windows 和 macOS。项目数据全部留在本地，不经任何第三方服务器，这点对创作者来说挺重要。

**它替代的，是一条原本要五六个人、五六套工具才能串起来的流水线。**

02

核心能力，一个 AI 剧组

Toonflow 最有意思的设计是多 Agent。

它没有让一个大脑包打天下，而是模拟了一个真实剧组。导演、编剧、分镜、一致性、质检、配音，六个 Agent 各干各的活。

导演 Agent 统筹叙事节奏，编剧 Agent 把小说转成标准剧本，分镜 Agent 输出景别、构图、光线、运镜的完整描述。质检 Agent 负责挑毛病，查情节逻辑漏洞、角色矛盾、场景跳跃。

**角色一致性是 AI 短剧最难啃的骨头，Toonflow 专门设了一个一致性 Agent，给角色建外貌数据库，跨镜头盯住主角配角不变脸。**

![图片](https://mmbiz.qpic.cn/mmbiz_png/iapI7WE6qru4hyicDfHqjxa5p0Ac2wnbdV9E1EHibFsicub6p5PicDHwUxLDOJIBaeyvNTNoWjgMAJQSqBTSwkvUQWo2uicyvMhIcwNcvkicuW2WEk/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=1)

角色三视图与图片生成，用来锁住角色的外貌（图源 GitHub 官方仓库）

模型选择上也很自由。图像侧支持 Nano Banana、即梦这类主流模型，视频侧可灵、海螺、Seedance 都能接，把 API Key 填进设置就行。

你甚至可以把本地的 ComfyUI 和本地大模型接进来。官方还做了个开源的模型中转平台 TF-Router，给开不了白、用不上某些模型的用户兜底。

再加两个细节。一个无限画布，剧本、角色、场景、视频片段全摆在同一张画布上组织。一个插件市场，扩展节点和工具随装随用，还支持 MCP 连接外部服务。

![图片](https://mmbiz.qpic.cn/mmbiz_png/iapI7WE6qru5fAT7ptT0XbiaznpaxiabFDuTQjcOk2plNVM8YQpdl8o7zIDzqrOO9wicsicWJfwNPTebzXTcCiauDia5yUia7ZJHkOBNdQk7ibzrBhiaQ/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=2)

创作画布 · 深色主题（图源 GitHub 官方仓库）

官方 README 里记了一个真实案例，我原样搬给你。

用 Seedance 2.0 出视频，GPT Image 2 出图，Claude Opus 4.6 写剧本，约 2 小时做出一部约 2 分钟的成片，模型总成本约 130 元。

语言模型  
¥10视频生成  
¥120图片生成  
<¥1总成本  
¥130

官方案例的成本构成，数据来自项目 README

视频生成是绝对大头，图片便宜到可以忽略。这个成本结构，对后面怎么规划生成次数很有参考价值。

03

怎么装，怎么用

安装有三条路，按省事程度排。

最省事的是桌面版。去 GitHub 的 Releases 页面下载安装包，Windows 双击安装会自动配好 WebView2，macOS 把图标拖进「应用程序」就行。第一次打开如果被系统拦，去「隐私与安全性」里点「仍要打开」。

想自己部署的，Docker 三条命令。

git clone https://github.com/HBAI-Ltd/Toonflow-app.git  
cd Toonflow-app  
docker compose up -d --build

跑起来之后，浏览器打开 127.0.0.1:3000 就能用了。

Linux 服务器裸装也可以。项目指定 Bun 1.3.14 做运行时，装依赖、构建、启动三步，README 写得很细。

| 安装方式 | 适合谁 | 上手要点 |
| --- | --- | --- |
| 桌面安装包 | 普通用户，想立刻上手 | Releases 页下载，双击装 |
| Docker | 有 NAS 或服务器的玩家 | 三条命令，数据存卷里 |
| Linux 服务器 | 团队部署，多人共用 | Bun 运行时，注意端口防护 |

三种安装方式对比

一个安全提醒值得单独说。3000 端口的页面和 API 默认没有登录鉴权，放公网前一定要加防火墙或反向代理。个人远程用，官方推荐走 SSH 隧道。

![图片](https://mmbiz.qpic.cn/mmbiz_png/iapI7WE6qru7GFBibR3gRk1aMOeNWVOqX4XR8bLicMquVayYYYrgSXo8mUpN1Ym7exgug6cTJIaiaPml0fbgrdyu3f9viajE5IS0BtP0Tpfkd0jg/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=3)

3D 导演台与镜头预演（图源 GitHub 官方仓库）

装好之后的第一次使用，路径大概是五步。配 API Key，建项目，粘小说，跑流程，导出。

把小说文本或者一句话创意贴进去，剩下的交给那六个 Agent。你在旁边像制片人一样拍板就行，每一步的产出都可以改。

04

谁适合用，怎么上手

说几个我认为特别匹配的场景。

短剧漫剧创作者，最直接。整部小说批量转换、自动规划节奏密度，官方说一个人能跑一条完整生产线，有案例数据撑着。

小说作者。把写完的章节丢进去，几小时后看到自己笔下的角色动起来，这种反馈和纯文字完全不一样。

想入门 AI 视频的普通人。社区里有用户说，之前用 ComfyUI 又要找工作流又要付费踩坑，现在上手难度和成本都降了一大截。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/iapI7WE6qru7KWvoOMvcaicLRseiaMd0mze9aPchgMfRObwYG9ZyG0b9MbNnB7k1V4KTv51R8wC5YUCibXW5xLlIFSZf3GibDvwibNdGBKp81BMhc/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=4)

多参考素材视频生成（图源 GitHub 官方仓库）

上手给三条建议。

**先用桌面版。** 别一上来就折腾 Docker 和服务器，工具的意义是先跑通流程。

**从短文本开始。** 几百字的小故事先全流程走一遍，确认每一步的产出质量，再上长篇。有专业团队拿它处理 400 章节的小说，但那是跑通之后的事。

**模型先贱后贵。** 视频生成占了成本九成以上，试错阶段用便宜模型，定稿了再换 Seedance 这一档，130 块的案例成本就是这么控制出来的。

再进个社群。6000 多人的微信社群加官方 Discord，README 里有入口，踩过的坑基本都有人答过。

工具层面聊完了，说点感受。

Toonflow 做的事不神秘，就是把散落各处的环节串起来，再用 Agent 把重复劳动吃掉。但它背后那个方向值得认真看一眼。短剧的制作权，原来握在有预算的团队手里，现在正在滑向任何一个有想法的人。

一个人，一台电脑，一条生产线。

工具越来越像剧组，人的角色就越来越像导演。 **往后比拼的，可能不是谁会操作软件，而是谁手里有个好故事。**

仓库地址放这儿，自己去翻。

github.com/HBAI-Ltd/Toonflow-app  
toonflow.net

教程、插件市场、开发者文档，README 里都能找到。

作者提示: 个人观点，仅供参考