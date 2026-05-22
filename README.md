# Social Video Planner Skill

**An agent skill for turning articles, scripts, and topic material into a pre-production planning package for HyperFrames.**

[中文文档](./README.zh-CN.md)

---

## What Is This?

`social-video-planner` is a planning layer for social-media video production and
HyperFrames handoff. It no longer builds web presentations, records screens, or renders video.

It produces:

- `script.md` — narration copy split into speakable beats
- `content-brief.md` — pre-script understanding, angle selection, and direction confirmation
- `content-review.md` — fidelity, claim, source, material, and blocker review
- `outline.md` — beat / scene planning
- `hyperframes-handoff.md` — the single handoff document for a HyperFrames agent

HyperFrames remains responsible for visual identity, HTML composition, GSAP animation,
preview, lint, inspect, and final rendering.

## Core Ideas

- **Content before design** — settle facts, claims, narration rhythm, and material boundaries first.
- **Plan before scripting** — use `content-brief.md` to understand the source, mine angles, and confirm direction.
- **Narration beats drive structure** — after direction is confirmed, `script.md` uses `---` separators; each beat carries one complete idea.
- **Review is a hard gate** — factual claims, people, metrics, screenshots, and citations need a source or risk status.
- **The handoff is the product** — `hyperframes-handoff.md` is the downstream entrypoint.
- **No design overreach** — palettes, typography, motion, transitions, and code architecture belong to HyperFrames.

## Workflow

```text
Phase 1  Identify input and content boundaries
Phase 2  Create content-brief.md and confirm content direction
Phase 3  Generate / clean script.md
Phase 4  Review claims, sources, and material risks
Phase 5  Create video outline
Phase 6  Export hyperframes-handoff.md
Checkpoint  Confirm script, facts, assets, and handoff completeness
```

## Generated Output

```text
my-video-plan/
├── article.md
├── content-brief.md
├── script.md
├── content-review.md
├── outline.md
└── hyperframes-handoff.md
```

These files are generated inside a user's video planning project. They are not
sample files shipped in this skill repository.

## Reference Map

- [SCRIPT-STYLE.md](./references/SCRIPT-STYLE.md) — article-to-narration style and anti-AI-voice rules
- [CONTENT-BRIEF.md](./references/CONTENT-BRIEF.md) — pre-script understanding, angle selection, and structure confirmation
- [CONTENT-REVIEW.md](./references/CONTENT-REVIEW.md) — fidelity, claim, material, and blocker review
- [OUTLINE-FORMAT.md](./references/OUTLINE-FORMAT.md) — beat / scene planning format
- [HYPERFRAMES-HANDOFF.md](./references/HYPERFRAMES-HANDOFF.md) — downstream HyperFrames handoff contract

## Relationship To HyperFrames

This skill outputs the pre-production package. HyperFrames then reads
`hyperframes-handoff.md` and continues with:

1. Visual identity gate and `DESIGN.md` / `visual-style.md`.
2. HyperFrames composition planning.
3. HTML / CSS / GSAP authoring.
4. Lint and visual inspect.
5. Preview and render.

This skill does not create React/Vite projects, maintain theme templates, synthesize audio,
record screens, or render video.
