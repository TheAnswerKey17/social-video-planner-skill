# `hyperframes-handoff.md` 交接规范

`hyperframes-handoff.md` 是交给 HyperFrames agent 的唯一主文档。它应该让
下游不用再反复翻原始材料，也不会误以为前期 agent 已经做了设计决策。

## 文件结构

```markdown
# HyperFrames Handoff

## Project Summary

- Topic:
- Platform:
- Target audience:
- Target duration:
- Language:
- Tone:
- Source content angle:
- Delivery status: ready / blocked / usable-for-draft-only

## Strategy Brief

- Recommended direction:
- Viewer promise:
- Hook direction:
- Mid-video rhythm:
- Closing action:
- Assumptions inherited from `content-brief.md`:

## Content Boundaries

- Confirmed facts:
- Needs source:
- Risky / sensitive:
- Material gaps:
- Do not fabricate:

## Narration Beats

### Beat 1
<口播全文>

### Beat 2
<口播全文>

## Scene Map

| scene_id | beats | estimate | narrative job |
|---|---:|---:|---|
| hook | 1-3 | ~35s | Establish the counterintuitive promise |

## Beat Sheet

| beat | scene_id | narration | screen focus | source/material | risk |
|---:|---|---|---|---|---|
| 1 | hook | <short quote> | <what viewer must understand> | article §1 | opinion |

## Visual Intent

- <只写视觉任务和信息关系，不写设计实现>

## Design Inputs

- User-provided style:
- Brand constraints:
- Mood words:
- References:
- Explicit no-go:
- If empty: HyperFrames must run its visual identity gate.

## HyperFrames Notes

- Start from this handoff, then follow HyperFrames visual identity gate.
- Create or read `DESIGN.md` / `visual-style.md` before writing composition HTML.
- Use HyperFrames composition timing rules; `data-duration` is the duration source.
- Keep audio/video tracks under HyperFrames rules.
- Run `npx hyperframes lint` and `npx hyperframes inspect` before preview/render.

## Acceptance Checklist

- [ ] Every beat from `script.md` appears exactly once
- [ ] Strategy Brief matches `content-brief.md`
- [ ] Every beat has screen focus, source/material, and risk status
- [ ] No fake screenshot, fake metric, fake logo, or fake identity is requested
- [ ] No color, font, CSS, HTML, GSAP, shader, React, Vite, or transition implementation is prescribed
- [ ] Blockers from `content-review.md` are either resolved or clearly carried forward
```

## Content Boundaries

This section prevents downstream fabrication.

Write concrete constraints:

- “Dan Koe identity needs user/source confirmation before final render.”
- “Craig Perry view counts come from article text only; verify before using as on-screen fact.”
- “If screenshots are unavailable, use abstract labeled placeholders or redesign the evidence scene.”

Do not write vague warnings like “be careful with facts.” Say exactly which fact or asset is risky.

## Narration Beats

Copy the final `script.md` beats here, numbered. Do not include headings or stage directions.

If the script is long, each beat can include full narration plus a short label, but the narration
must remain available to HyperFrames for timing and scene planning.

## Scene Map

Scene IDs should be stable and implementation-friendly:

- lowercase
- hyphen-separated
- content-based

Good examples:

- `hook`
- `beginner-hell`
- `validated-content`
- `networking-lever`
- `action-close`

## Beat Sheet

Each beat must include:

- `scene_id`
- short narration quote or full text
- `screen focus`
- `source/material`
- `risk`

`screen focus` describes the information the viewer should understand. It should not duplicate
the full narration and should not prescribe design.

Good:

- “Show the false belief that growth is lottery-like, then identify platform mechanics as the real object.”
- “Make the two levers feel like the only things the viewer should track.”

Bad:

- “Use a black background with neon blue levers.”
- “Animate two icons with a 0.5s bounce.”

## Visual Intent

Allowed:

- information relationships
- narrative emphasis
- evidence hierarchy
- continuity needs between beats
- places where real素材 or screenshots are required

Forbidden:

- color palettes
- font choices
- CSS/HTML/JS/GSAP instructions
- React/Vite architecture
- concrete transition names
- template names

## Acceptance

If `content-review.md` verdict is `blocked`, handoff may still be created, but its
`Delivery status` must also be `blocked`. Do not hide unresolved blockers in footnotes.

If no design inputs exist, say so directly. HyperFrames is expected to ask or create a design
identity according to its own rules.
