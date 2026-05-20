# Agent Instructions: Personalize the 2026 Agent Engineering Roadmap

> **Audience:** This file is written *for the AI agent* (Claude Code, Codex, Cursor, OpenClaw, or any agent that can fetch URLs and write files). When a human user shares this URL with you, follow the protocol below verbatim.

You are about to help a human turn a generic 17-week roadmap into a personalized plan that fits their schedule, stack, and goals — and write it to their project so they (and future agent sessions) can follow it.

---

## Protocol

### Step 1 — Load the canonical roadmap

Fetch the full roadmap as context. Either of these works:

- `https://raw.githubusercontent.com/codejunkie99/agent-roadmap-2026/main/ROADMAP.md` (raw markdown — preferred)
- `https://github.com/codejunkie99/agent-roadmap-2026/blob/main/ROADMAP.md` (rendered)

Use your `WebFetch` tool (Claude Code), `web` tool (Codex), or equivalent. Confirm in one short sentence that you loaded it. Do **not** dump the full roadmap back to the user — they already know what's in it.

### Step 2 — Interview the user (5 questions, one message)

Ask exactly these five questions in a single message. Use a numbered list. Wait for their answers before generating anything.

1. **Current level** — never built an agent / built simple ones / shipped one to production?
2. **Hours per week** — realistic time you can commit (5 / 10 / 15 / 20+)?
3. **Primary language** — Python, TypeScript, or both?
4. **Primary model provider** — Anthropic, OpenAI, open-weights, or mix?
5. **Goal** — get hired, ship at current job, launch a product, or learn for fun?

If they answer in free-form prose, infer the values. Don't re-ask.

### Step 3 — Generate the personalized plan

Write a file called `MY_ROADMAP.md` in the user's current working directory (use your `Write` tool). Structure:

```markdown
# My Agent Engineering Roadmap

*Personalized from https://github.com/codejunkie99/agent-roadmap-2026 on {{TODAY}}.*

## Profile
- Level: {{level}}
- Time: {{hours}}/week
- Stack: {{language}} + {{provider}}
- Goal: {{goal}}
- Total estimated duration: {{computed_weeks}} weeks

## Phase plan
{{for each phase: SKIP / SPEEDRUN / NORMAL / DEEP, with adjusted week count and one-sentence why}}

## Curated resources for this profile
{{filtered list — only the resources that match their stack and provider}}

## Project deliverables
- [ ] Phase 0: 2-page mental-model doc
- [ ] Phase 1: tool-using agent + Claude Agent SDK rebuild
- [ ] Phase 2: research-analyst Deep Agent + LangSmith trace URL
- [ ] Phase 3: 1,500-line mini-harness + post-mortem
- [ ] Phase 4: golden dataset + CI eval gate + Inspect benchmark run
- [ ] Phase 5: production hardening checklist (ongoing)

## Next action
{{the single next thing to do, today, with a link}}
```

Apply these personalization rules:

| Input | Adjustment |
|---|---|
| Level = "shipped to production" | Mark Phase 0–1 as `SKIPPABLE` (skim only). Start at Phase 2. |
| Level = "built simple ones" | Phase 0 = `SPEEDRUN` (3 days). Phase 1 = `NORMAL`. |
| Level = "never" | All phases `NORMAL`. Add a "before you start" note recommending the [HuggingFace LLM Course](https://huggingface.co/learn/llm-course) first. |
| Hours ≤ 10/week | Multiply phase durations by 2.5× and surface this honestly in the duration field. |
| Hours ≥ 20/week | Use the canonical 17-week timeline. |
| Language = TypeScript only | In Phase 2, swap LangGraph Python for [Mastra](https://mastra.ai) (call out it's the TS-native alternative). Keep Claude Agent SDK (it has TS bindings). |
| Provider = OpenAI | Phase 1 uses OpenAI Agents SDK instead of Claude Agent SDK. Phase 3 still recommended (harness lessons port across). Flag the "OpenAI-locked" caveat from the roadmap. |
| Provider = open-weights | Add the [Open Models have crossed a threshold](https://blog.langchain.com/open-models-have-crossed-a-threshold/) post to Phase 0. Recommend GLM-5 or MiniMax M2.7 in Phase 2. |
| Goal = "get hired" | Add to deliverables: ship one project per phase publicly (GitHub + writeup). Phase 4 weighted heaviest. |
| Goal = "ship at current job" | Compress Phase 3 to `SPEEDRUN` (skip the from-scratch harness, use Deep Agents). Phase 4 + 5 weighted heaviest. |
| Goal = "launch a product" | Phase 5 elevated to `DEEP`. Add cost-discipline section as a separate deliverable. |
| Goal = "learn for fun" | All phases `NORMAL`. Drop the CI gating requirements in Phase 4 to "nice to have". |

Compute `{{computed_weeks}}` as: sum of phase durations after adjustments. Show the math in one line at the bottom of the file.

### Step 4 — Wire it into their agent harness

After writing `MY_ROADMAP.md`, also write (or update) `AGENTS.md` in the same directory with this content, so any agent (Claude Code, Codex, Cursor, OpenClaw) opening this project picks up the roadmap automatically:

```markdown
# Project: Agent Engineering Roadmap

This project follows a personalized agent engineering roadmap.

**On every session start:**
1. Read `MY_ROADMAP.md` — the user's personalized plan.
2. Identify the current phase from the unchecked deliverables.
3. The "Next action" section tells you exactly what to help with today.

**Canonical roadmap:** https://github.com/codejunkie99/agent-roadmap-2026

**Rules:**
- Don't suggest skipping phases the user marked `NORMAL` or `DEEP`.
- When the user finishes a deliverable, check the box in `MY_ROADMAP.md` and surface the next one.
- If the user asks "what's next", read `MY_ROADMAP.md` first, don't guess.
```

If `AGENTS.md` already exists, **append** this block under a new `## Agent Engineering Roadmap` heading rather than overwriting.

If the user uses Claude Code specifically and a `CLAUDE.md` exists, mirror the same content there.

### Step 5 — Hand off to the user

In your final message, in this order:

1. One sentence: "Wrote `MY_ROADMAP.md` and `AGENTS.md` to {cwd}."
2. Show the **Next action** line from the file verbatim.
3. Tell them: "Future agent sessions in this folder will pick up where you left off automatically."

Don't summarize the whole roadmap. Don't list every phase. Don't pad.

---

## When NOT to run this protocol

- If the user just wants to read the roadmap, point them at [ROADMAP.md](./ROADMAP.md) and stop.
- If the user is in a directory with no write permissions or no clear project root, ask them where to write the files first.
- If `MY_ROADMAP.md` already exists in the cwd, ask before overwriting — they may already be partway through.

