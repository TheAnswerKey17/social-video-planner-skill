# `outline.md` 格式规范

`outline.md` 是 HyperFrames handoff 的草案层：它把口播 beat 组织成
scene，并说明每个 beat 的信息任务。它不是视觉设计稿，也不是代码计划。

## 核心原则

- `script.md` 决定口播顺序和 beat 边界。
- `article.md` 或素材源决定事实、案例、数字和画面信息密度。
- `outline.md` 只规划内容、节奏、信息关系和素材需求。
- 美学、设计系统、composition、HTML/CSS/GSAP、转场和渲染全部交给
  HyperFrames。

## 文件结构

```markdown
# Video Outline

> **主题**：<一句话说明视频讲什么>
> **平台**：<B站 / YouTube / 视频号 / 内部汇报 / 未指定>
> **目标受众**：<谁会看>
> **目标时长**：约 <T> 秒 / 分钟
> **规模**：<N> scenes / <M> beats

---

## Scene Map

| scene_id | beats | 估时 | 叙事功能 | 交接状态 |
|---|---:|---:|---|---|
| hook | 1-3 | ~35s | 建立反差和核心承诺 | ready |

---

## Scene 1 - <scene_id>：<中文标题>

**Beats**：1-3  
**估时**：~35s  
**叙事功能**：<这一幕在整条视频里负责什么>  
**信息关系**：<反差 / 递进 / 因果 / 证据 / 时间线 / 网络扩散 / 增长曲线等>

### Beat 1

- 口播引用：`<script.md 中对应 beat 的一句或全文>`
- 屏幕表达重点：<观众这一拍需要看懂什么>
- 来源 / 依据：<article §X / 用户素材 / opinion / needs-source>
- 素材需求：<真实截图 / 人物照片 / 无 / placeholder allowed>
- 风险状态：<source-backed / needs-source / opinion / risky>

### Beat 2

...

---

## 素材与来源清单

| item_id | 类型 | 用途 | 状态 | 备注 |
|---|---|---|---|---|
| dan-koe-photo | 人物照片 | 介绍人物身份 | needs-user | 不可用假头像替代 |

---

## 自检

- [ ] 每个 script beat 都在 outline 中出现一次，且顺序一致
- [ ] 每个 scene 都有清晰叙事功能
- [ ] 每个 beat 都有屏幕表达重点、来源/依据、素材需求、风险状态
- [ ] 没有写配色、字体、HTML、CSS、GSAP、React/Vite 或具体转场方案
- [ ] 没有要求下游伪造截图、数据、logo 或人物身份
```

## Scene Map 规则

`scene_id` 使用小写英文和连字符，例如：

- `hook`
- `beginner-hell`
- `validated-content`
- `non-needy-networking`
- `action-close`

每个 scene 通常覆盖 2-5 个 beats。信息密集型段落可以更短；故事铺垫或
案例可以更长。估时按口播字数粗估即可，不要写动画时长。

`叙事功能` 要写这一幕在视频里的作用，而不是视觉形式：

- 建立反常识钩子
- 解释问题为什么发生
- 给出第一个可执行杠杆
- 用案例证明方法有效
- 收束为行动清单

## Beat Sheet 规则

每个 beat 必须有五项：

| 字段 | 要求 |
|---|---|
| 口播引用 | 从 `script.md` 引用，允许节选但不能改意思 |
| 屏幕表达重点 | 只写观众这一拍应该看懂的核心内容 |
| 来源 / 依据 | 指向 `article.md`、用户素材，或标记为 opinion / needs-source |
| 素材需求 | 写真实素材需求；缺失时说明是否允许占位 |
| 风险状态 | `source-backed` / `needs-source` / `opinion` / `risky` |

## Visual Intent 边界

可以写信息关系：

- 反差对照：错误认知 vs 真实机制
- 因果链：失败经历 → 技能积累 → 起号优势
- 时间线：两周 / 四周 / 三个月的复利过程
- 网络扩散：朋友分享让内容进入别人的观众
- 证据墙：案例、数字、引用同时支持一个结论

不要写实现方式：

- 不写“黑底蓝字”“高级感 serif”“赛博朋克风”
- 不写“用 GSAP 0.5s 入场”“做 blur wipe”“用 shader 转场”
- 不写“做 React 组件”“建 Vite 项目”“用 CSS grid 实现”
- 不写“套某个模板”

如果用户明确给了品牌、风格或禁区，只记录到 handoff 的
`Design Inputs`，由 HyperFrames 的 DESIGN gate 消化。

## 自检要求

完成 `outline.md` 后必须逐项检查：

- [ ] `script.md` 中每个 `---` 分隔出的 beat 都被覆盖
- [ ] beat 顺序没有被重排，除非用户明确要求改叙事结构
- [ ] 每个 scene 的叙事功能不重复、不空泛
- [ ] 每个 beat 的屏幕表达重点不是简单复读口播
- [ ] 每个具体事实都能追到来源，或被标记为 `needs-source`
- [ ] 素材缺口没有被假素材掩盖
- [ ] 全文没有出现代码、框架、主题模板、动画参数或渲染命令
