# `content-review.md` 内容审核规范

`content-review.md` 用来保护视频前期策划不把未经确认的事实、缺失素材、
AI 味口播或错误归因交给 HyperFrames。它是 handoff 前的质量闸门。

## 文件结构

```markdown
# Content Review

## Verdict

- 交接状态：ready / blocked / usable-for-draft-only
- 主要结论：<一句话说明>
- 阻断项数量：<N>

## Fidelity Check

- 原文到脚本信息保留度：<比例或定性结论>
- 保留的关键事实：<列表>
- 被压缩 / 删除的内容：<列表>
- 是否改变原文立场：yes / no

## Claim Register

| id | claim | status | source | action |
|---|---|---|---|---|
| c1 | <具体事实> | source-backed | article §X | none |

## Material Register

| id | material | needed for | status | fallback |
|---|---|---|---|---|
| m1 | <人物照片> | <scene/beat> | needs-user | placeholder label only |

## AI Voice Check

- 假共情：pass / fail
- 假深刻：pass / fail
- 自我标榜：pass / fail
- 万能模板：pass / fail
- 排比堆砌：pass / fail
- 需要修改的句子：<列表>

## Blockers

- <没有则写 None>

## Open Questions

- <没有则写 None>
```

## Claim 状态

| 状态 | 含义 |
|---|---|
| `source-backed` | 有 article、用户素材、可靠来源或用户明确声明支持 |
| `needs-source` | 具体事实存在，但当前没有足够来源 |
| `opinion` | 主观判断、评论、创作者观点，不需要事实来源但不能伪装成事实 |
| `risky` | 可能涉及名誉、医疗、法律、金融、时效新闻或高风险指控 |

具体事实包括：

- 人名、公司名、产品名、身份介绍
- 数字、播放量、收入、增长率、时间线
- “某人说过 / 某报告指出 / 某平台机制是”这类归因
- 案例结果、对比结论、排名

## Material 状态

| 状态 | 含义 |
|---|---|
| `available` | 素材已在项目里或用户已提供 |
| `needs-user` | 必须由用户提供，不能替代 |
| `needs-source` | 需要外部来源或授权确认 |
| `placeholder-ok` | 可以用文字占位说明，不影响理解 |
| `avoid` | 不建议使用，容易误导或侵权 |

素材缺失时不要写“找一张差不多的图”。要写清楚：

- 是否可以用文字占位。
- 是否必须等用户提供。
- 是否允许 HyperFrames 改用抽象信息表达。

## 阻断项

以下情况必须标为 `blocked`：

- 视频核心论点依赖一个 `needs-source` 或 `risky` claim。
- 需要展示真实人物、真实后台、真实数据，但素材不存在。
- 口播稿明显保留了 AI 味，念出来不像真人。
- 脚本与原文观点相反，或删除了关键反方/限制条件。
- outline / handoff 中 beat 编号不一致。

以下情况可以标为 `usable-for-draft-only`：

- 少数非核心数字需要来源。
- 某些视觉素材缺失，但可以使用明确标注的占位。
- 用户还没有确定平台或目标时长，但内容结构完整。

## 自检清单

- [ ] 每个具体 claim 都在 Claim Register 中出现
- [ ] 每个 claim 都有 `status`
- [ ] `needs-source` / `risky` 的 action 明确
- [ ] 每个素材缺口都有 fallback 或阻断说明
- [ ] AI Voice Check 失败项已经回写修正到 `script.md`
- [ ] Verdict 与 Blockers 一致；有 blocker 时不得写 `ready`
