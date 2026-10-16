---
title: "Isaac Sim Skills深度解读"
source: "https://mp.weixin.qq.com/s/QGcGSR1ZciNbkZ_iNEE77g"
author:
  - "[[游方]]"
published:
created: 2026-10-10
description: "NVIDIA 把机器人仿真经验写成 38 个 Agent Skills，让 AI 学习工程师的工作方法。本文带你深度了解这些skills"
tags:
  - "clippings"
---
游方 具身Agent *2026年10月9日 17:10*

NVIDIA 已经将一套面向 Isaac Sim 的 Agent Skills 集成进正式发行版。官方文档列出了 **38 项技能** ，让 Codex、Claude Code 等开发智能体能够按照既定工程流程完成机器人资产导入、物理配置、ROS 2 集成、仿真调试和结果验证。

**这不是给机器人增加新的运动控制算法，而是让 AI Agent 学习机器人仿真工程师的工作方法。**

过去，Agent 也能编写 Isaac Sim Python 代码，但机器人导入后为什么倒下、相机为什么黑屏、ROS 2 为什么收不到消息、怎样判断任务真正完成，仍然是大量工程问题。

NVIDIA 现在试图把这些经验写进 Skills。更有意思的是，Agent 还可以在验证和调试之后，把有价值的经验提炼出来，留给下一次任务使用。

**这套 Skills 最值得研究的，不是它能帮 Agent 写多少代码，而是它开始告诉 Agent：一项机器人开发工作，究竟怎样才算做完。**

## 01Isaac Sim Skills 究竟是什么？

先明确一个容易混淆的概念。

**Agent Skill 不是机器人的运动技能，而是 AI Agent 的工程技能。**

例如， **navigation-primitives** 并不是一个训练好的导航策略，而是教 Agent 如何使用占据栅格、A\*、机器人足迹和运动学组件构建导航功能。 **physics-simulation** 也不是一个新的物理引擎，而是教 Agent 如何正确配置 PhysX、Newton、碰撞体、关节和接触参数。

每个 Skill 的核心是一个 SKILL.md 文件，还可以配套可执行脚本和参考资料。其基本结构为：

skills/

physics-simulation/

SKILL.md

scripts/ references/

navigation-primitives/

SKILL.md

scripts/ references/

isaac-sim-ros2-bridge/

SKILL.md

scripts/ references/

其中，SKILL.md 告诉 Agent 什么时候应该使用这个技能、需要满足什么条件、按什么步骤操作、如何发现错误以及如何判断结果是否可靠。scripts/ 提供可复用的执行程序，references/ 则保存较长的 API 说明与技术细节。这样的设计避免了让大模型每次都从零搜索文档、猜测接口、重新生成整套程序。

### 官方的两层结构：Repo-native 与 Robotics-sim

NVIDIA 实际上将 Skills 分成了两个层次：一类面向 Isaac Sim 自身的构建、调试与性能分析（Repo-native），另一类面向使用 Isaac Sim 开发机器人应用的工程师（Robotics-sim）。前者帮助 Agent 维护和调试仿真开发环境，部分能力依赖源码仓库内部工具；后者帮助 Agent 创建场景、配置物理、集成机器人、生成数据并验证结果。

**两者都提供了可复用的工程知识，但并非所有辅助工具在源码、Pip 和二进制安装环境中都具有相同的可执行条件。**

### 一个重要变化：Skills 已经随 Isaac Sim 发布

这些 Skills 不需要额外拼装。NVIDIA 官方文档明确指出，它们已经随 Isaac Sim 的源码构建、Pip 包和二进制安装包一起提供，并且支持 Codex CLI、Claude Code、Cursor 等能够发现和使用 Skills 的开发智能体。未来一个熟悉 Skills 的 Agent 进入 Isaac Sim 开发环境，就可以直接利用 NVIDIA 提供的工程流程。

与传统软件开发相比，变化不在于少写几行代码，而在于 **工程知识有了可以被 Agent 发现、执行和复用的载体** 。

![Isaac Sim Skills 全景](https://mmbiz.qpic.cn/mmbiz_jpg/zBXylMy1OfM0UVrgjaPJiam0n29PhgBLnl1U5KiaScSVNd52r0AlPkXCrCfT1YoYdSM0zL7npVkeKd8kJVEc8T2RFAuYKAib9QCbL008e7CLicI/640?from=appmsg&watermark=1#imgIndex=0)

Isaac Sim Skills 全景

▲ Isaac Sim Skills 全景：任务编排、资产导入、物理仿真、ROS 2 集成、验证与经验沉淀（图：具身Agent）

## 0238 个 Skills，覆盖机器人开发全流程

NVIDIA 官方将 **38 个 Skills 分为 11 类** 。为了方便理解，我们按照实际机器人开发过程，将它们归并为七组。这一节是能力地图，不是使用手册。

### 第一组：让 Agent 会安装、会调试、会验收

这是最容易被忽略、但实际价值很高的一组能力。

**isaac-sim-installation：** 环境检查、兼容性验证与多种安装路径，包含授权确认和预热检查等约束。

**isaac-sim-remote：** 连接正在运行的 Isaac Sim，执行 Python、检查 Prim、控制物理、读取日志、截取画面。

**profile-isaac-sim：** 性能分析，支持基准工具和 Tracy 诊断耗时。

**validation-diff-gifs：** 仿真截图与基准图的像素级对比，定位视觉回归。

**流程五件套：** isaac-sim-orchestrator 任务编排；meta-skills 技能设计与组合；isaac-sim-validator 交付检查；isaac-sim-troubleshooting 故障诊断；skill-distillation 经验沉淀。

这组技能实际上回答了一个问题： **Agent 不仅要能生成程序，还要知道程序为什么失败、什么时候算完成。**

### 第二组：让 Agent 真正理解机器人资产

很多机器人仿真任务，第一步就卡在模型导入上。机器人原本可能采用 URDF 或 MJCF 描述，而 Isaac Sim 使用 OpenUSD 表达场景与物理属性。 **urdf-mjcf-to-usd-conversion** 处理这条转换路径，覆盖关节、驱动器、碰撞模型以及适用于强化学习的资产配置； **usd-articulation** 负责多连杆、多关节结构的组织与验证；physics-simulation 建立刚体、碰撞、质量、材料和关节驱动。 **usd-pipeline** 、 **usd-composition-architecture** 和 **spatial-reasoning** 可以合并理解为一组 USD 工具链：资产发现与测量、分层组织物理与视觉资产、空间坐标与包围盒管理。

这里有一个工程细节值得展开。 **模型能够显示，不代表它已经是一个正确的物理机器人。** 场景使用厘米还是米、Articulation Root 是否正确、碰撞体是否合理、关节驱动是否稳定，都可能决定一个仿真能否运行。这些通常依赖工程师经验的检查项，正在被写进 Skills。

### 第三组：让机器人在场景中移动

移动机器人部分包含四个技能。navigation-primitives 提供占据地图、A\* 路径规划、差速与全向运动学以及机器人足迹计算； **occupancy-map** 将 USD 场景转换成 ROS 兼容地图，优先根据物理碰撞体生成，碰撞数据不可用时退回到几何投影方案——后者只是替代方法，不能保证与实际碰撞空间完全一致，当前生成的也主要是二维栅格； **isaac-sim-robot-navigation** 负责仿真运行期间的导航控制。

**mobility-gen** 的设计值得单独强调： **先采集运动轨迹，再回放渲染传感器数据。** 也就是说，机器人运动、轨迹记录和昂贵的图像渲染不必耦合在同一个实时循环里。对于大规模机器人数据生产，这种解耦有实际价值。

### 第四组：机械臂操作与运动规划

**manipulation-ik** 负责逆运动学、抓取坐标系、关节空间控制和接触验证；主分支索引中的 **motion-generation** 进一步覆盖基于运动生成控制器的避障轨迹，参考实现涉及 cuMotion、RMPflow。这里的重点不是 NVIDIA 发明了新的 IK 算法，而是让 Agent 知道什么时候应当选用 IK、什么时候需要规划器，以及抓取之后如何验证物体真的被移动了。

### 第五组：传感器与空间感知

**isaac-sim-sensor** 覆盖 RGB、深度、语义分割、LiDAR、IMU 和接触传感器； **isaac-camera** 负责相机参数、Render Product、标注器和镜头畸变。另有三个偏向数字孪生的技能： **place-camera-aim-at** 围绕目标物体寻找无遮挡视角； **place-camera-max-coverage** 用覆盖率驱动的贪心求解在指定区域布置摄像机； **calibrate-metropolis-camera** 提取已布置相机的内外参和视场区域。这类技能适合工业站场、仓库、生产线和智慧园区的视觉系统验证。贪心策略并不保证全局最优，但它把原本需要人工反复调整的相机选址，变成了 Agent 可以自动尝试、测量和修正的过程。

### 第六组：合成数据，以及更复杂的物理事件

这一组最能体现 NVIDIA 对 Physical AI 的整体布局。 **data-collection-sim** 面向静态场景的 Replicator 数据生成； **actor-sdg-sweep-config** 生成经过 Schema 验证的参数配置变体，支持可重复的批量实验； **action-and-event-data-generation** 将场景对象、移动实体、行为、物理事件、摄像机和标注组织到一起。

**behavior-tree-generation：** 用 LLM 驱动的规划器，把场景任务转成行为树结构，为模拟人的行为、机器人动作和事件响应提供组织形式。但生成行为树不等于已经获得稳定可靠的控制策略，示例动作仍需集成和验证。

**generate-incident-config 与 run-incident-events：** 配置并执行物体倾倒、火灾、液体泄漏等模拟事件，记录事件报告。在仓库里主动制造货物倾倒，再观察机器人能否感知障碍变化，比只在理想静态场景里测试导航更接近真实工程问题。

**vlm-scene-captioning：** 利用三维场景真值构造场景图，再借助 NVIDIA NIM 模型生成场景描述或问答数据。生成描述的依据不仅是图片，还包括对象、空间关系与语义标签，于是 **三维仿真中较为明确的结构化真值，被转化为 VLM 训练所需的文本监督信号** 。

**object-bin-packing：** 箱体和货物的密集装箱、装托盘等场景构造。

这一组能力连起来，就不只是生成漂亮图片，而是能够构造有行为、有事件、有语义标注的训练和测试场景。需要说明，行为树生成和场景描述等功能依赖相应模型服务及 API 凭据，并非所有数据生成任务都可以完全离线运行。

### 第七组：渲染、无头部署与 ROS 2

**isaac-sim-rendering** 处理光线追踪、路径追踪、光照与画面采集； **isaac-sim-headless-deployment** 指导无窗口运行和批处理； **actor-sdg-generate-lighting-variations** 用可复现的 USD 光照覆盖层生成不同光照条件，不直接修改原始场景。

**isaac-sim-ros-workspaces** 负责构建相关 ROS 工作空间，支持原生构建、Docker、Pixi 等方式，但它并不负责安装整个 ROS 2 发行版； **isaac-sim-ros2-bridge** 通过 OmniGraph 建立 ROS 2 通信，涉及话题、TF、Nav2 和多机器人命名空间。后者尤其重要：Agent 不必把所有控制逻辑写在 Isaac Sim 内部，仿真系统也更容易沿用实际机器人的软件接口。

**版本说明：** 上述 38 项来自 Isaac Sim 官方 Agent Skills 文档。截至本文核对时，IsaacSim GitHub 主分支的 skills/SKILLS.md 又列出了 isaac-sim-assets、isaac-sim-migration、isaac-sim-workflow 和 motion-generation 四项，因此主分支索引共有 42 项，分别补充了资产访问、版本迁移、演示任务定义和运动规划等能力。GitHub 主分支与实际发布安装包并不一定完全同步，使用时应以已安装版本包含的 Skills 及对应 API 为准。

## 03从写代码到做工程：Skills 的真正价值

逐个看 Skill 的功能，很容易将其理解为一套更方便的机器人 API 文档。但深入源码，会发现它的设计目标不止于此。真正体现 NVIDIA 思路的，是四个核心机制。

### Orchestrator：让 Agent 按照工程顺序做事

isaac-sim-orchestrator 不亲自完成每一项专业工作，而是负责识别任务所需能力、选择合适的 Skill，并规定集成顺序。源码把端到端流程组织成资产导入、物理配置、传感器挂载、验收交付等阶段，每个阶段都有明确的交付契约。例如，Orchestrator 在物理配置阶段定义了明确的交付条件：机器人必须在重力作用下保持姿态稳定，连续运行 **200 帧** ，才能进入下一阶段的传感器集成。 **这不是通用的物理正确性证明，而是一道具体、可执行的工程检查关口。**

它还要求先逐段验证每个阶段，再做增量集成，每加入一种能力都重新检查已有功能是否正常。背后的原则非常朴素： **一次只引入少量变化，让每次失败都更容易定位。** 如果允许 Agent 一次生成上千行仿真代码，随后启动就崩溃，大模型往往很难判断是资产、渲染、物理还是软件接口出了问题。将问题分解成可独立验证的能力，反而更有机会稳定完成复杂任务。

### Remote：不只是运行脚本，而是反复观察和修改

isaac-sim-remote 允许 Agent 连接正在运行的 Isaac Sim 并直接执行 Python。我们核对了它的源码：默认连接本机 127.0.0.1:8226，底层是 isaacsim.code\_editor.python\_server 提供的 TCP 接口，代码在 Kit 进程内执行，返回状态、输出和异常信息，并在同一会话内保留 Python 状态。

一个典型的调试过程因此变成：Agent 先检查某个机器人 Prim 是否存在，再读取关节结构；发现物理属性异常后修改配置，运行若干物理步，重新读取状态；随后截取画面，确认实际运动是否符合预期。它不必每次都重新生成完整程序、重启整个仿真器。源码还记录了非常具体的渲染排查经验：无头模式下出现黑屏时，需要检查场景光源、渲染模式和预热状态，并按实际场景调整 DomeLight 等光照参数。

但必须明确： **这种远程接口提供的是 Kit 进程内的 Python 执行能力，权限极高，不能视为安全沙盒。** 源码将其定位为本地开发者控制平面，信任边界等同于启动 Isaac Sim 的操作系统用户，并明确要求仅绑定回环地址，不得对外开放端口。

### Validator：把"验收"变成 Agent 必须执行的步骤

以前，Agent 写完代码，程序没有报错，可能就宣布任务完成。但在机器人仿真中，程序退出码为零并不意味着场景正确。isaac-sim-validator 将常见交付问题转为检查项：过时的 API、硬编码路径、缺少光源、错误的渲染模式、黑屏或过暗画面等。它甚至要求检查演示视频的开头、中间和结尾，避免交付一段机器人被遮挡或者摄像机丢失目标的视频。

不过，这些检查主要保证脚本和展示结果的基本质量，真正的物理正确性仍需额外测试：运行日志、关节状态、传感器数据有效性，以及任务级的目标到达率、碰撞次数、终点误差。机械臂是否成功抓取，要看物体最终位置、抓取状态和接触信息；移动机器人是否成功导航，要看目标到达、碰撞、轨迹和 ROS 反馈，而不是只看它有没有移动。

**Skill 指导 Agent 如何做事，Validator 检查交付是否合格，而具体的物理任务仍需自己的评价机制。画面质量、程序正确性与物理任务成功，是三个不同层次的验收。**

### Skill Distillation：把失败经验留下来

如果说前面的能力让 Agent 学会做事，那么 skill-distillation 开始回答另一个问题：同一个错误，下次能不能不再犯？NVIDIA 在 meta-skills 中定义了一个任务循环：ORIENT›PLAN›EXECUTE›VALIDATE›DISTILL›DELIVER，对应理解任务、制定计划、执行、验证、经验提炼和交付。

假设某次仿真中，机器人导入后一直穿过地面，经过几轮排查，Agent 发现是碰撞属性和初始高度配置不正确。如果只修复当前任务，这次经历很快就结束了。但 skill-distillation 希望把具体问题提炼为通用检查流程：导入机器人之后，应检查碰撞体、地面高度与初始姿态，并进行短时间物理稳定性测试。 **这才是值得留给后续任务的经验。**

NVIDIA 在源码里明确区分了临时事实与可复用程序，并规定持久化更新需要经过用户确认，而不是让 Agent 擅自修改自己的 Skills。 **这个限制非常重要：一次失败可能只是偶然现象，如果 Agent 把错误的归因沉淀成长期规则，反而会在未来任务里反复制造新问题。**

因此，Skill Distillation 更接近 **受监督的工程经验积累，而不是模型权重层面的自主进化** 。但它确实提供了一条从一次性编程走向持续积累专业能力的路径。

## 04一次机器人仿真任务，如何调用多个 Skills？

这些 Skill 如何协同工作？考虑一个具体任务：

在 Isaac Sim 6.1 中创建一个仓库场景，部署 Nova Carter 移动机器人，接入 ROS 2 和 Nav2，让机器人从起点导航到指定货架，并记录可复现的测试结果。

这不是 NVIDIA 官方已经保证可以一键完成的 Benchmark，而是一个能够用其 Skills 组织实施的典型案例。

**第一步：确定任务与验收标准。** 若安装版本已提供 isaac-sim-workflow，先明确交付物：可运行的 USD 场景、ROS 2 配置、启动脚本、测试日志和演示视频。先定义成功条件，再动手。

**第二步：准备机器人与物理环境。** 用 usd-pipeline、usd-articulation 和 physics-simulation 检查机器人尺寸、关节、碰撞体、重力和驱动，先证明机器人能在地面保持稳定，并对基本速度控制做出合理响应。

**第三步：建立地图与导航基础。** 用 occupancy-map 生成 ROS 兼容地图，再用 navigation-primitives 检查机器人实际足迹、障碍膨胀与规划路径。货架、墙体和机器人之间的碰撞关系需要单独验证。

**第四步：接入 ROS 2。** 用 isaac-sim-ros2-bridge 建立必要的话题和 TF 关系，例如 clock、odom、scan、cmd\_vel，再接入 Nav2，验证机器人能从导航目标获得速度指令并正确反馈自身状态。

**第五步：运行仿真并收集证据。** 通过 isaac-sim-remote 观察仿真状态、修改参数、记录问题。测试至少应包括：导航目标是否到达、有没有碰撞、轨迹是否符合规划、ROS 2 数据是否持续正常发布，以及不同初始状态下结果是否稳定。

**第六步：生成演示，再沉淀经验。** 用 isaac-sim-rendering 录制仿真，通过 isaac-sim-validator 检查交付质量，最后由 skill-distillation 总结共性问题，审核后更新相关技能。

**最终，Agent 交付的不应该只是一段机器人移动的视频，而是一套能够复现的仿真任务：机器人从指定起点出发，接收 Nav2 导航目标，完成路径规划与运动控制，并输出目标到达情况、碰撞记录、ROS 2 通信日志和可重复执行的场景文件。如果任务失败，Agent 应能根据日志和仿真状态定位原因，而不是只调整镜头、重新录制视频。**

一个任务就这样把资产、物理、导航、ROS 2、传感器、验证与经验积累连接起来。如果要扩展，可以加入 MobilityGen 采集轨迹数据，或者用事件生成工具构造货物倾倒等异常场景。但需要指出，这套流程仍然需要一个具备工具执行能力的 Agent，以及真实可用的 Isaac Sim、ROS 2 和导航软件环境；Skills 本身不会自动提供完整的自主导航系统。

## 05如何让 Codex、Claude Code 用起来？

对 Isaac Sim 6.1 的开发者来说，最直接的方式是利用安装包中自带的 Skills。先找到安装目录中的 skills/：

export ISAAC\_SIM\_DIR=/path/to/isaac-sim

export WORKSPACE\_DIR=/path/to/my-project/workspace

ls "$ISAAC\_SIM\_DIR/skills"

二进制安装方式下，Skills 通常位于安装根目录；Pip 方式可以通过 pip show isaacsim 查找安装位置。接下来要让开发智能体发现这些 Skills：Codex 等支持 AGENTS.md 的工具，通过工作区中的 AGENTS.md 获取技能目录；Claude Code 使用 CLAUDE.md 和.claude/skills/；Cursor 通过相应规则文件获得指引。 **一个很实际的细节：仅仅设置 ISAAC\_SIM\_DIR，不代表 Agent 就能自动发现全部 Skills，还必须把技能目录或对应指引文件暴露给 Agent。**

环境准备好之后，可以直接给 Agent 一段这样的任务指令：

请读取当前 Isaac Sim 安装目录中的 Skills 索引与相关 SKILL.md。

目标：在 Isaac Sim 6.1 中创建一个基础移动机器人仿真。

要求先验证机器人资产与物理稳定性，再接入传感器和 ROS 2。

每个阶段输出检查结果；出现错误时先定位原因，不要直接跳过。

最后提供可复现的脚本、日志和运行截图。

这比再增加几条安装命令更有价值，因为读者可以直接尝试。需要注意的是，Skills 随发行包提供，不代表所有能力在任何安装方式下都能完整运行：profile-isaac-sim、validation-diff-gifs 等 Repo-native 技能依赖源码仓库内部工具，在 Pip 或二进制环境中可执行条件不同，官方对此有明确限制。

初次使用时，不建议一上来就做复杂的多机器人项目。可以先让 Agent 完成一个小的、可检验的任务，例如导入一台机器人，配置正确的物理属性，运行数秒并输出截图和日志。等这条链路稳定之后，再逐步增加 ROS 2、导航、传感器和合成数据。

## 06Skills 能做到什么，还缺少什么？

在具身 Agent 系统中，Skills 常与 MCP、Harness 同时出现，但三者并不是一回事。NVIDIA 也有专门的 Isaac Sim MCP Server，主要通过语义检索向 Agent 提供 Isaac Sim 的扩展、示例、设置和开发知识。

**MCP** 提供一种工具或知识访问接口；

**Skill** 说明面对具体任务应该如何组合和使用这些能力，包括执行顺序、注意事项和错误排查；

**Harness** 范围更大，负责 Agent 的运行环境、工具执行、会话状态、权限与反馈机制。

**MCP 让 Agent 能够访问能力，Skill 让 Agent 知道如何使用能力，Harness 让能力在受约束的运行环境中持续工作。** 但把 Skill 加入 Agent，并不意味着机器人已经实现自主运行。真正进入物理世界时，还需要本体状态管理、控制接口、实时执行、安全约束、故障恢复与结果验证——这恰恰是具身 Agent 与一般编程 Agent 的重要区别。

与此同时，这套 Skills 的边界也必须看清。

**Skill 的质量仍取决于底层程序与仿真模型。** 资产碰撞配置不准确，A\* 再正确也可能规划出实际无法通行的路线；物理参数不合理，抓取动画再漂亮也不能说明策略具有真实可迁移性。

**通用 Validator 不能代替任务级评价器。** 黑屏检查、运行日志、API 合规性是必要的工程质量控制，但导航成功率、碰撞次数、抓取成功率以及仿真到真实机器人的性能差异，还需要具体任务自己的指标体系。

**版本一致性需要显式管理。** Isaac Sim 不同版本之间存在 API、扩展和资产路径变化，GitHub 主分支里的 Skill 也可能引用比当前安装包更新的接口。工程实践应尽量固定 Isaac Sim 版本、资产版本和 Skills 版本，并保留可复现的运行配置。

**安全边界必须显式管理。** isaac-sim-remote 使用的 Python Server 可以在 Isaac Sim 进程内执行代码，官方要求将服务限制在可信环境；isaac-sim-validator 的第三级检查也可能执行目标 Python 脚本，且没有提供操作系统级沙盒。对真实机器人系统来说，Agent 是否有能力生成代码，与它是否有权执行物理动作，必须严格分开。

## 结语：从积累工程技能，到积累物理经验

Isaac Sim Skills 让我们看到了一种新的机器人开发方式：Agent 不再每次从零开始查文档、写脚本、修错误，而是能够调用已有的工程知识，并逐步积累可复用的开发经验。

NVIDIA 这套 Skills 积累的主要是三种工程能力：任务执行程序、故障诊断经验和结果验收规则。而具身智能体要真正成长，还需要积累另一类东西：与物理世界交互得到的经验——机器人什么时候发生滑移、什么抓取姿态更稳定、为什么当前路径会发生碰撞、遇到扰动后应如何调整控制策略。前者让 Agent 更会开发机器人；后者才有可能让机器人更会完成物理任务。两者不是对立关系，而是两个不同层次的学习过程。

所以，学会开发机器人，与机器人学会在物理世界中行动，还不是一回事。下一步真正值得期待的，是让工程经验与物理交互经验连接起来：Agent 不仅知道怎样构建、运行和验证一套机器人系统，也能从机器人的成功、失败和环境反馈中持续改进。

**从积累工程技能，到积累物理经验，或许才是具身 Agent 持续成长的一条重要路径。**

**参考资料**  
NVIDIA Isaac Sim Agent Skills 官方文档: https://docs.isaacsim.omniverse.nvidia.com/latest/development\_tools/agent\_skills.html  
Isaac Sim Skills 源码及组合索引: https://github.com/isaac-sim/IsaacSim/blob/main/skills/SKILLS.md  
Isaac Sim Python Server: https://docs.isaacsim.omniverse.nvidia.com/latest/development\_tools/python\_server.html  
Isaac Sim MCP Server: https://docs.isaacsim.omniverse.nvidia.com/latest/development\_tools/isaac\_sim\_mcp.html  
NVIDIA Agent Skills 生态仓库: https://github.com/NVIDIA/skills

**讨论话题**  
机器人开发的工程经验，应该由工程师写成 Skill 交给 Agent，还是让 Agent 自己从失败中蒸馏？如果两者都要，人和 Agent 的分工边界应该画在哪里？欢迎在评论区聊聊你的看法。

具身Agent — 深度解构物理AI的前沿与边界  
专注具身智能前沿，深度拆解模型、技能、协议与进化  
及时分享，陪你看见物理AI的未来

具身Skill · 目录