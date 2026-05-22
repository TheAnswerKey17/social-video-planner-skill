---
name: social-video-planner
description: 把文章、视频链接、字幕、口播稿或选题素材整理成社交媒体视频策划包，并导出 HyperFrames 可接手的 handoff。流程：识别输入与内容边界 → 生成 content-brief.md 并与用户确认内容方向 → 生成/清洗 script.md → 做内容审核与 claim/source 检查 → 拆成 video outline → 导出 hyperframes-handoff.md。这个 skill 不生成 React/Vite 页面，不写 HTML/CSS/GSAP，不做美学决策，不负责录屏或视频渲染；HyperFrames 负责 DESIGN gate、composition、动画、preview、lint、inspect、render。
---

# Social Video Planner

这是一个 **社交媒体视频前期策划 agent skill**。它负责把原始内容变成
可讨论、可审核、可交给 HyperFrames 制作的结构化策划包。

它的产出不是网页项目，而是内容决策、审核结论和 handoff 文档。

## 职责边界

### 本 skill 负责

- 识别用户给的是文章、已有口播稿、素材摘要，还是只有选题想法。
- 先理解素材，提炼观点、亮点、金句、可选角度和推荐内容方向。
- 和用户确认平台、受众、角度、目标时长、口吻边界和待查证事实。
- 把文章改写成能说出口的 `script.md`，并用 `---` 切成口播 beat。
- 审核内容保真度、事实 claim、素材缺口、待确认风险。
- 把口播 beat 组织成适合视频制作的 scene map。
- 导出 `hyperframes-handoff.md`，作为交给 HyperFrames 的唯一主文档。

### 本 skill 不负责

- 不创建 React / Vite / TypeScript 项目。
- 不维护主题 token、网页模板、章节组件或录屏流程。
- 不写 HTML、CSS、GSAP、shader、transition、composition 代码。
- 不替 HyperFrames 决定配色、字体、版式系统、动画实现。
- 不合成口播音频，不渲染视频。

> 任何美学、设计系统、代码架构、动画和导出视频的决策，都交给
> HyperFrames skill 处理。

## 标准产出包

每个项目最终至少包含：

```text
my-video-plan/
├── article.md               # 原文 / 素材源；用户给了就保留，不删
├── content-brief.md         # 写稿前的内容理解、角度和结构确认
├── script.md                # 纯口播稿；用 --- 切 beat
├── content-review.md        # 内容保真、claim、素材和阻断项审核
├── outline.md               # beat / scene 规划草案
└── hyperframes-handoff.md   # 交给 HyperFrames 的唯一主文档
```

`script.md` 只写能被念出来的正文，不写标题、Step 编号、舞台说明、括号
旁白、非口播注释。

`hyperframes-handoff.md` 是下游入口。HyperFrames agent 可以从它开始，
再按自己的规则进入 DESIGN gate、composition authoring、lint、inspect
和 render 流程。

## 工作流

```text
Phase 1  识别输入与内容边界
   ↓
Phase 2  内容理解与方向策划，生成 content-brief.md
   ↓
Checkpoint Brief  确认平台 / 受众 / 角度 / 时长 / 口吻 / 待查证事实
   ↓
Phase 3  生成 / 清洗 script.md
   ↓
Phase 4  内容审核与 claim/source 检查
   ↓
Phase 5  生成 video outline
   ↓
Phase 6  导出 hyperframes-handoff.md
   ↓
Checkpoint  稿件 / 事实 / 素材 / 交接完整性确认
```

## Phase 1 - 识别输入与内容边界

先判断用户给了什么：

| 用户输入 | 处理方式 |
|---|---|
| 原始文章、博客、访谈稿、长文 | 保存为 `article.md`，进入文章改写流程 |
| 视频链接 / 字幕 | 保存 transcript 或摘要为 `article.md`，先做内容理解 |
| 已有口播稿 | 保存为 `script.md`，仍生成简化 `content-brief.md` 确认方向和风险 |
| 素材摘要、bullet、选题说明 | 先整理成 `article.md` 风格素材，再做 brief |
| 只有一句选题 | 先向用户要素材、观点或参考来源；不要凭空编一整期视频 |

如果内容涉及现实人物、公司、数据、新闻、医疗、法律、金融等高风险事实，
必须在 `content-review.md` 中标注需要来源确认。需要实时事实时，按当前
环境能力检索可靠来源；不能确认就标 `needs-source`，不要伪造。

## Phase 2 - 内容理解与方向策划

必须阅读 [`references/CONTENT-BRIEF.md`](references/CONTENT-BRIEF.md)。

产出 `content-brief.md`，在写口播稿前先完成：

- Source Understanding：总结素材讲什么、核心问题、核心结论和观众收益。
- Signal Mining：提炼 strong points、good lines、evidence/examples、tension。
- Platform Angles：至少给 2-3 个可选自媒体转化角度。
- Recommended Direction：明确推荐一个方向，并说明为什么。
- Draft Content Architecture：只到 section 级别，说明 hook、context、
  points、evidence、close 的叙事作用。
- Script Instructions：确认后用于生成 `script.md` 的写稿指令。

### Checkpoint Brief - 必须讨论的关键点

写完 `content-brief.md` 后必须停下来，除非用户明确说“你自己定方向继续”。
要让用户确认：

- 平台：B 站 / YouTube / 视频号 / 小红书 / 内部汇报等。
- 目标观众：新手、进阶、专业人士、客户、投资人等。
- 内容角度：采用推荐方向，还是替代方向。
- 目标时长：短视频、3-5 分钟、8-10 分钟、长视频。
- 口吻边界：锐利、温和、教程感、观点感、故事感。
- 内容红线：哪些观点、人物、品牌、事实不能改。
- 查证项：哪些事实需要来源，哪些素材必须由用户提供。

如果用户授权继续但没有逐项确认，按 `content-brief.md` 的
Recommended Direction 执行，并在 `content-review.md` 记录默认假设。

## Phase 3 - 生成 / 清洗 script.md

必须阅读 [`references/SCRIPT-STYLE.md`](references/SCRIPT-STYLE.md)。

执行规则：

- 必须按 `content-brief.md` 的 `Script Instructions` 写稿。
- 从文章改写时，默认信息保留度不低于 60%。
- 关键数字、案例、人物、时间线、因果链不能丢。
- 用 `---` 切 beat；一个 beat 只承载一个可口播的完整想法。
- 口播稿里不写视觉说明、不写标题层级、不写 Step 编号。
- 写完后按 `SCRIPT-STYLE.md` 的三层自检修稿，再进入审核。

如果用户给的是已有口播稿，只做清洗和切 beat，不擅自重写立场。

## Phase 4 - 内容审核与 Claim 检查

必须阅读 [`references/CONTENT-REVIEW.md`](references/CONTENT-REVIEW.md)。

产出 `content-review.md`，至少包含：

- 信息保真结论：原文到脚本是否保留关键事实、案例和论证链。
- Claim Register：逐条列出具体事实，并标记 `source-backed`、
  `needs-source`、`opinion` 或 `risky`。
- Material Register：列出人物照、截图、品牌图、数据图、引用来源等素材。
- Blockers：哪些问题会阻止交接完成。
- Open Questions：哪些问题可以交给用户补充，但不阻止下游开始设计。

交接阻断项包括：

- 核心事实没有来源，且视频主论点依赖它。
- 素材缺口会导致画面只能伪造截图、数据或人物身份。
- `script.md` 明显有 AI 味、不可口播，或与原文观点相反。
- beat 数、scene map、handoff 引用互相对不上。

## Phase 5 - 生成 Video Outline

必须阅读 [`references/OUTLINE-FORMAT.md`](references/OUTLINE-FORMAT.md)。

产出 `outline.md`，这里的 outline 特指 **video outline**：根据最终
`script.md` 拆 scene / beat，服务于 HyperFrames handoff。它不是写稿前
的内容架构，也不是视觉设计稿。

允许写：

- scene 切分、beat 范围、估时、叙事功能。
- 每个 beat 的屏幕表达重点。
- 信息关系：反差、递进、因果、证据、时间线、网络扩散、增长曲线等。
- 素材需求、来源标注、风险状态。

禁止写：

- 配色、字体、CSS、HTML、GSAP、transition、shader、React/Vite 架构。
- “用某套模板”“做某个具体动效”“某元素 0.5s 入场”这类实现方案。
- 假截图、假数据、假 logo、无来源背书的权威说法。

## Phase 6 - 导出 HyperFrames Handoff

必须阅读 [`references/HYPERFRAMES-HANDOFF.md`](references/HYPERFRAMES-HANDOFF.md)。

`hyperframes-handoff.md` 固定包含：

- Project Summary：主题、平台、目标时长、受众、语气。
- Content Boundaries：哪些事实已确认，哪些需要来源或素材。
- Narration Beats：按编号引用 `script.md` 的每个 beat。
- Scene Map：`scene_id`、对应 beats、估时、叙事功能。
- Beat Sheet：口播、屏幕表达重点、信息来源、素材需求、风险状态。
- Visual Intent：只写视觉任务和信息关系，不写美学实现。
- Design Inputs：用户明确给过的品牌、情绪、禁区、参考；没有就交给
  HyperFrames DESIGN gate。
- HyperFrames Notes：提醒下游遵守 visual identity gate、
  composition timing、lint / inspect / render 流程。
- Acceptance Checklist：下游接手前必须满足的完整性检查。

## Checkpoint - 交接前确认

完成 `hyperframes-handoff.md` 后停下，向用户汇报：

```text
前期策划包完成：
  - article.md
  - content-brief.md
  - script.md
  - content-review.md
  - outline.md
  - hyperframes-handoff.md

需要确认：
  1. 稿件口吻和观点是否准确
  2. content-brief.md 的方向是否仍然成立
  3. content-review.md 里 needs-source / risky 的项是否要补来源
  4. 素材缺口是否由用户提供，还是允许 HyperFrames 使用占位说明
  5. handoff 是否可以交给 HyperFrames 进入设计和渲染阶段
```

如果存在阻断项，不能说“可以直接交给 HyperFrames”。必须清楚标记：
“当前 handoff 可用于创意预研，但还不能进入最终制作”。

## 自检协议

所有核心产出都必须自检后再汇报：

| 产出 | 自检来源 |
|---|---|
| `content-brief.md` | [`CONTENT-BRIEF.md`](references/CONTENT-BRIEF.md) |
| `script.md` | [`SCRIPT-STYLE.md`](references/SCRIPT-STYLE.md) |
| `content-review.md` | [`CONTENT-REVIEW.md`](references/CONTENT-REVIEW.md) |
| `outline.md` | [`OUTLINE-FORMAT.md`](references/OUTLINE-FORMAT.md) |
| `hyperframes-handoff.md` | [`HYPERFRAMES-HANDOFF.md`](references/HYPERFRAMES-HANDOFF.md) |

检查失败要先修文档，再向用户汇报。不要把未修复的检查结论直接丢给用户。

## HyperFrames 交接提醒

下游 HyperFrames agent 接手时，应从 `hyperframes-handoff.md` 开始，然后：

1. 进入 HyperFrames 的 visual identity gate；没有 `DESIGN.md`、
   `visual-style.md` 或用户明确风格时，由 HyperFrames 提问或生成设计方向。
2. 按 handoff 的 scene/beat 信息创建 composition 结构。
3. 用 HyperFrames 自己的规则处理 HTML、CSS、GSAP、media tracks 和 timing。
4. 运行 `npx hyperframes lint` 与 `npx hyperframes inspect`。
5. 预览和渲染由 HyperFrames CLI 负责。

本 skill 不越界替它做这些事。
