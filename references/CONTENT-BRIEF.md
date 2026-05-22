# `content-brief.md` 内容策划规范

`content-brief.md` 是写 `script.md` 之前的方向确认文档。它的目标不是写稿，
而是先理解素材，提出可选内容打法，并让用户确认“这条视频到底怎么讲”。

它是整个流程的第一个创作闸门：

```text
article.md / raw material
   ↓
content-brief.md     # 先理解、提炼、给方向
   ↓
用户确认 / 迭代
   ↓
script.md
```

## 什么时候必须产出

只要用户给的是文章、视频链接、字幕、访谈、长文、资料包或多个素材片段，
都必须先产出 `content-brief.md`，再写 `script.md`。

如果用户直接给了一份已经定稿的口播稿，可以简化：只做 brief 摘要和风险
确认，然后进入脚本清洗。

## 文件结构

```markdown
# Content Brief

## Source Understanding

- 素材类型：
- 一句话总结：
- 核心问题：
- 核心结论：
- 目标观众可能关心：
- 不适合展开的内容：

## Signal Mining

### Strong Points
- <最值得保留的观点 / 判断>

### Good Lines
- "<可改造成金句或 hook 的原句 / 意思>"

### Evidence / Examples
- <数据 / 案例 / 故事 / 对比>

### Tension
- <冲突、反差、误区、争议、悬念>

## Platform Angles

| angle_id | 角度 | 适合平台 | 观众承诺 | hook 方向 | 风险 |
|---|---|---|---|---|---|
| a1 | <角度名> | <平台> | <看完得到什么> | <开头抓手> | <风险> |

## Recommended Direction

- 推荐角度：
- 为什么推荐：
- 视频主张：
- 观众承诺：
- 开头钩子：
- 中段节奏：
- 结尾动作：

## Draft Content Architecture

| section | purpose | key beats | retention job |
|---|---|---|---|
| Hook | <作用> | <要讲什么> | <为什么观众会继续看> |

## Discussion Checkpoint

- 必须确认：
  - [ ] 平台
  - [ ] 目标观众
  - [ ] 推荐角度或替代角度
  - [ ] 目标时长
  - [ ] 口吻边界
  - [ ] 哪些观点不能改
  - [ ] 哪些事实需要查证
- 可选确认：
  - [ ] 标题方向
  - [ ] 是否需要强人设
  - [ ] 是否需要保留原作者名字
  - [ ] 是否要做系列化

## Script Instructions

- 采用角度：
- 默认平台：
- 默认时长：
- 口吻：
- 必须保留：
- 必须避免：
- 待查证但可先占位：
```

## Source Understanding

这一节要先证明 agent 真的读懂了素材。不要一上来写脚本。

必须回答：

- 素材到底在解决什么问题？
- 原作者最重要的判断是什么？
- 哪些内容只是背景，哪些内容值得放到视频主线？
- 这条内容对目标观众的收益是什么？
- 哪些内容可能不适合目标平台，应该压缩或换说法？

## Signal Mining

从素材中挖四类信号：

| 类型 | 用途 |
|---|---|
| Strong Points | 视频主论点和章节骨架 |
| Good Lines | hook、标题、金句、结尾 |
| Evidence / Examples | 支撑可信度，避免空讲 |
| Tension | 制造观看动机和中段推进 |

好的 brief 不只是总结，还要判断“这条内容为什么值得被做成视频”。

## Platform Angles

至少给 2-3 个可选角度。每个角度都要说明：

- 适合什么平台。
- 给观众什么承诺。
- 开头用什么钩子方向。
- 中段靠什么维持注意力。
- 有什么事实、素材或立场风险。

常见角度类型：

- 反常识拆解：把大家以为对的东西推翻。
- 方法论提炼：把长内容压成可执行框架。
- 案例复盘：围绕一个人物、产品、事件讲清底层逻辑。
- 避坑提醒：告诉观众哪里最容易做错。
- 趋势判断：把一个现象放到更大的变化里。
- 实操教程：把内容拆成步骤、清单、动作。

## Recommended Direction

必须选一个推荐方向，不能只丢选项给用户。

推荐方向要包含：

- 视频主张：这条视频最想让观众相信什么。
- 观众承诺：看完能获得什么。
- 开头钩子：前 5-15 秒怎么让人留下。
- 中段节奏：如何从一个点推进到下一个点。
- 结尾动作：观众看完应该记住或做什么。

## Draft Content Architecture

这是写稿前的“内容架构”，不是最终 `outline.md`。

它只需要到 section 级别：

- Hook
- Setup / Context
- Point 1
- Point 2
- Case / Evidence
- Action / Close

每个 section 说明叙事作用和 retention job。不要写逐 beat 口播，也不要写
HyperFrames 视觉实现。

## Discussion Checkpoint

写完 `content-brief.md` 后必须停下来，除非用户明确说“你自己定方向直接
继续”。停下时不要问泛泛的“你觉得怎么样”，而是请用户确认关键决策：

- 平台：B 站 / YouTube / 视频号 / 小红书 / 内部汇报
- 目标观众：新手 / 进阶 / 专业人士 / 客户 / 投资人
- 角度：用推荐方向还是替代方向
- 时长：短视频 / 3-5 分钟 / 8-10 分钟 / 长视频
- 口吻：锐利 / 温和 / 教程感 / 观点感 / 故事感
- 红线：哪些观点、人物、品牌、事实不能改

如果用户没有回复，但要求继续，按 `Recommended Direction` 和
`Script Instructions` 里的默认值写稿，并在后续 `content-review.md`
中记录这是默认假设。

## 自检清单

- [ ] 先解释了素材内容，而不是直接写稿
- [ ] 挖出了 strong points、good lines、evidence、tension
- [ ] 至少给出 2 个可选角度，并明确推荐 1 个
- [ ] 推荐方向包含主张、观众承诺、hook、中段节奏、结尾动作
- [ ] Draft Content Architecture 只到 section 级别，没有写逐 beat 口播
- [ ] 没有写配色、字体、HTML、CSS、GSAP、转场或 HyperFrames 实现
- [ ] Discussion Checkpoint 的问题都是会影响脚本方向的关键决策
