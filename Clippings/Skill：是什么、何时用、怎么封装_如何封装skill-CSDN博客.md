---
title: "Skill：是什么、何时用、怎么封装_如何封装skill-CSDN博客"
source: "https://blog.csdn.net/YSbnhoffer/article/details/163779785"
author:
  - "[[全马必破三]]"
published: 2026-08-15
created: 2026-10-15
description: "文章浏览阅读260次，点赞7次，收藏7次。本文详解Skill的核心定位——解决能力无法沉淀、复用与按需加载的问题。重点阐述Skill适用场景（高频流程、多步骤判断、知识固化、跨团队复用、上下文受限），对比Tool的适用边界；深入解析封装技巧：统一入口+frontmatter元数据、渐进式披露机制、资源随包携带、单一职责与组合性、版本化分发；并揭示其三层加载逻辑与token账本优化价值。"
tags:
  - "clippings"
---
## 一文讲透 Skill：是什么、何时用、怎么封装

> 这篇文章用 **一个完整的 Skill 示例代码** ，带你搞懂 Skill 解决了什么问题、什么时候该用、以及 frontmatter + 渐进式披露（Progressive Disclosure）的核心实现逻辑。

---

### 一、Skill 解决了什么问题

核心是解决 **“能力无法沉淀、复用和按需加载”** 的问题，具体对应四个痛点：

| 痛点 | Skill 的解法 |
| --- | --- |
| Prompt 每次重写、无法复用 | 把指令 + 流程打包成 **可复用的资产** |
| 全量塞进 system prompt，浪费上下文 | **渐进式披露** ：元数据常驻、正文按需加载 |
| 工具只有"原子操作"，缺流程编排 | Skill 提供 **多步流程 + 工具组合的编排** |
| 专家知识散落在人脑 / 文档里，难传递 | 把领域知识 + 最佳实践 **固化成包** |

一句话总结： **工具解决"能不能做"，Skill 解决"怎么做得专业、且能反复做"。**

---

### 二、什么情况下需要用到 Skill

判断标准：重点看是否有 **“复用”** 和 **“知识沉淀”** 价值。

#### 该用 Skill 的场景

- 某类任务 **高频反复执行** ，每次都要走一套固定流程
- 需要 **多步骤、有顺序、有判断** ，不是一次函数调用能搞定
- 需要 **领域知识 + 多个工具组合** ，纯 prompt 写太长或每次重写浪费
- 需要 **跨项目 / 跨团队复用** ，把专家经验固化下来
- 上下文窗口有限，希望能力 **按需加载而非常驻**

#### 不该用 Skill（用 Tool 就够）

- 单次、一次性的原子操作（查个天气、发个请求）
- 没有知识沉淀价值的简单调用
- 逻辑简单到一句 prompt 就能说清

一句话判据： **“这个能力会不会被反复使用？要不要把经验传下去？” 两个都是 Yes 才上 Skill。**

---

### 三、Skill 封装的技巧（实操层）

结合主流 Agent Skills （如 Claude Skills）的真实机制，关键技巧如下：

1. **统一入口 + 元数据（SKILL.md + frontmatter）**  
	每个 Skill 一个目录，入口文件用 YAML 头写 `name` 和 `description` 。name / description 是"广告位"，正文是"说明书"。
2. **渐进式披露（最核心的技巧）**
	- 元数据（name + description） **始终常驻** 上下文 —— 便宜
		- 完整指令正文 **只在被触发时加载** —— 贵，用到才给
		- 这样 Agent 能"知道有什么能力"，又不浪费 token
3. **description 写"何时用"，不写"是什么"**  
	description 里写清 **触发条件** （“当用户想生成 PPT 时”），而不是能力清单。目的是让 Agent **自动判断** 什么时候该加载它。
4. **资源随包携带**  
	Skill 目录里带脚本（ `scripts/` ）、参考文档（ `reference/` ）、模板（ `assets/` ）。正文只引用，不内联大段内容。
5. **单一职责 + 可组合**  
	一个 Skill 只干一类活；Skill 内部可以调用工具（包括 MCP 工具）甚至其他 Skill，形成分层。
6. **可版本化、可分发**  
	Skill 本质是文件 / 目录，能进 git、能分享、能做版本管理，让"能力"像代码一样被工程化管理。

---

### 四、完整示例：目录结构 + SKILL.md（含 frontmatter）

#### 4.1 目录结构

```
skills/
└── video-downloader/              # 一个 Skill = 一个目录
    ├── SKILL.md                   # 入口：frontmatter 元数据 + 正文指令
    ├── scripts/
    │   └── fetch_video_info.py    # 可执行脚本（资源）
    ├── reference/
    │   └── yt-dlp-cheatsheet.md   # 参考文档（资源）
    └── assets/
        └── config.example.json    # 模板 / 配置（资源）
text123456789
```

#### 4.2 SKILL.md 完整示例

```markdown
---
name: video-downloader
description: 当用户需要下载视频、提取音频或查询视频信息时使用。
  触发场景：用户提到"下载""视频""音频""yt-dlp""B站""YouTube"等关键词。
  不要在没有明确下载意图时使用。
---

# 视频下载技能

你负责把用户给的视频链接下载到本地，或提取音频。

## 使用前必读
先读取 \`assets/config.example.json\`，了解默认输出目录、格式等参数。

## 标准流程
1. 先运行 \`scripts/fetch_video_info.py <url>\` 拿到视频标题、可用格式、时长。
2. 把可选清晰度 / 格式列给用户确认（不要擅自选最高清）。
3. 确认后执行下载命令。
4. 校验文件是否生成、大小是否合理。

## 平台差异
不同平台的参数、限速、是否需要 Cookie，见 \`reference/yt-dlp-cheatsheet.md\`。
遇到报错先去该文档查对应平台的处理方式。

## 注意事项
- 不要下载版权受限内容，先提醒用户确认授权。
- 大文件要提示磁盘空间。
markdown123456789101112131415161718192021222324252627
```

**关键点：frontmatter 里的 `description` 写的是"何时用 / 何时不用"（触发条件），不是能力清单。** 这样 Agent 才能自动判断该不该加载它。

---

### 五、渐进式披露的实现逻辑

核心： **三层加载，越靠后越重，用到才加载。**

```js
// 1) 解析 frontmatter：只提取 name + description
function parseFrontmatter(md) {
  const m = md.match(/^---\n([\s\S]*?)\n---/);
  const meta = {};
  for (const line of m[1].split("\n")) {
    const [k, v] = line.split(":").map(s => s.trim());
    if (k) meta[k] = v.replace(/^["']|["']$/g, "");
  }
  return meta;
}

// 2) 启动时：遍历所有 Skill，只收集「元数据」（便宜，常驻）
function collectSkillMetadata(skillsDir) {
  const skills = [];
  for (const dir of listDirs(skillsDir)) {
    const md = readFile(\`${dir}/SKILL.md\`);
    const meta = parseFrontmatter(md);
    skills.push({
      name: meta.name,
      description: meta.description,   // 只留这一段进 system prompt
      path: \`${dir}/SKILL.md\`,         // 全文路径，用到才读
    });
  }
  return skills;
}

// 3) 构建 system prompt：只注入元数据列表，不注入正文
function buildSystemPrompt(skills) {
  const skillList = skills
    .map(s => \`- ${s.name}: ${s.description}\`)
    .join("\n");
  return [
    "你是一个 Agent，拥有以下技能（按需加载）：",
    skillList,
    "",
    "规则：当用户任务匹配某个技能的 description 时，",
    "调用 loadSkill(name) 加载该技能的完整指令再执行。",
  ].join("\n");
}

// 4) 运行时：命中后按需加载完整正文（贵，用到才读）
function loadSkill(name) {
  const skill = skills.find(s => s.name === name);
  return readFile(skill.path); // 返回完整 SKILL.md，包含脚本/文档引用
}
js123456789101112131415161718192021222324252627282930313233343536373839404142434445
```

#### token 账本（面试最加分的一句）

| 层 | 内容 | 是否常驻 | 开销 |
| --- | --- | --- | --- |
| 元数据 | name + description | 常驻 | 每个约 50–100 token |
| 正文 | SKILL.md 指令 | 按需加载 | 每个可能上千 token |
| 资源 | scripts / reference / assets | 正文引用后才读 | 可能几万 token |

10 个 Skill 全部元数据常驻也不到 1k token；若全量塞进 system prompt 则可能几万 token。 **渐进式披露让 Agent"知道有哪些能力"，但不为没用的能力付费。**

---

### 总结

- `frontmatter` 负责"让 Agent 知道 **何时** 用它"
- `SKILL.md 正文 + 资源目录` 负责"教它 **怎么做** "
- 加载器负责" **三层按需取用** "

这就是 Skill 封装的完整闭环。记住一句话： **Skill 是把"人做某类事的专业经验（指令 + 流程 + 工具 + 知识）"打包成一个可发现、可复用、按需加载、可版本化的能力单元。**