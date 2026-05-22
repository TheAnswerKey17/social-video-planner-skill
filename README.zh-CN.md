# Social Video Planner Skill

**把文章、口播稿或选题素材整理成 HyperFrames 视频制作前期策划包的 Agent Skill。**

[English](./README.md)

---

## 这是什么？

`social-video-planner` 是社交媒体视频的前置策划层。它不再生成网页演示，
也不负责录屏或渲染视频。

它负责把原始内容处理成：

- 能说出口的 `script.md`
- 写稿前确认方向的 `content-brief.md`
- 经过事实和素材审核的 `content-review.md`
- 清晰的 beat / scene 规划 `outline.md`
- HyperFrames agent 能直接接手的 `hyperframes-handoff.md`

HyperFrames 接手后，再负责视觉身份、HTML composition、GSAP 动画、预览、
检查和最终视频导出。

## 核心理念

- **内容先于设计**：先把观点、事实、口播节奏和素材边界讲清楚。
- **先策划再写稿**：先用 `content-brief.md` 理解素材、提炼角度、确认方向。
- **口播 beat 驱动结构**：方向确认后，`script.md` 用 `---` 切分，每个 beat 是一个完整想法。
- **审核是硬闸门**：具体事实、人物身份、数据、截图和引用都要标来源或风险。
- **交接文档是主产物**：`hyperframes-handoff.md` 是下游唯一入口。
- **不越界做美学决策**：配色、字体、动效、转场和代码结构全部交给 HyperFrames。

## 工作流

```text
Phase 1  识别输入与内容边界
Phase 2  生成 content-brief.md，讨论并确认内容方向
Phase 3  生成 / 清洗 script.md
Phase 4  内容审核与 claim/source 检查
Phase 5  生成 video outline
Phase 6  导出 hyperframes-handoff.md
Checkpoint  稿件 / 事实 / 素材 / 交接完整性确认
```

## 使用时生成的产出

```text
my-video-plan/
├── article.md
├── content-brief.md
├── script.md
├── content-review.md
├── outline.md
└── hyperframes-handoff.md
```

这些文件是在用户的视频策划项目里生成的产物，不是本 skill 仓库自带的示例文件。

## Reference Map

- [SCRIPT-STYLE.md](./references/SCRIPT-STYLE.md)：文章转口播稿与去 AI 味规则
- [CONTENT-BRIEF.md](./references/CONTENT-BRIEF.md)：写稿前的内容理解、角度和结构确认
- [CONTENT-REVIEW.md](./references/CONTENT-REVIEW.md)：内容保真、claim、素材和阻断项审核
- [OUTLINE-FORMAT.md](./references/OUTLINE-FORMAT.md)：beat / scene 规划格式
- [HYPERFRAMES-HANDOFF.md](./references/HYPERFRAMES-HANDOFF.md)：交给 HyperFrames 的主文档协议

## 与 HyperFrames 的关系

本 skill 输出前期策划包。HyperFrames 读取 `hyperframes-handoff.md` 后，继续：

1. 进入 visual identity gate，建立 `DESIGN.md` 或读取 `visual-style.md`。
2. 创建 HyperFrames composition。
3. 写 HTML / CSS / GSAP。
4. 运行 lint / inspect。
5. preview 并 render 视频。

本 skill 不生成 React/Vite 项目，不维护主题模板，不合成音频，不录屏。
