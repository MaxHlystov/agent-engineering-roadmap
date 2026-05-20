# My Agent Engineering Roadmap

*Personalized from https://github.com/codejunkie99/agent-roadmap-2026 on 2026-05-20.*

## Profile
- Level: never built an agent
- Time: 4-5 hours/week
- Stack: Python + TypeScript primary, Java/Kotlin secondary + mix
- Goal: get hired
- Total estimated duration: 42.5 weeks

## Before you start
Because your level is "never built an agent," spend your first study block skimming the [HuggingFace LLM Course](https://huggingface.co/learn/llm-course), especially tokenization, transformers, inference, and basic fine-tuning concepts. Do not try to master all ML theory first; use it to make the roadmap less foggy.

Java/Kotlin are useful background, but this roadmap should be executed mainly in Python + TypeScript because the strongest agent tooling, examples, eval harnesses, and hiring signals are there. Use Java/Kotlin only when a portfolio project benefits from JVM integration.

## Phase plan
- **Phase 0: Foundations — NORMAL — 5 weeks.** You are starting from zero agents, so build the mental models slowly instead of sprinting into framework code.
- **Phase 1: Build your first simple agent — NORMAL — 7.5 weeks.** Build the same small tool-using agent from scratch and with an SDK so you can feel what a harness gives you.
- **Phase 2: Build a real agent with proper architecture — NORMAL — 10 weeks.** Use LangGraph + Deep Agents as the main production-shaped stack, while keeping provider choice flexible through mix/model-agnostic patterns.
- **Phase 3: Build the harness layer yourself — NORMAL — 10 weeks.** Write a small Python harness once so you understand the moving parts employers care about: loop, tools, context, persistence, hooks, traces.
- **Phase 4: Build the eval and regression harness — NORMAL / HEAVIEST FOR HIRING — 10 weeks.** This is the strongest hiring signal: golden datasets, trajectory evals, CI gates, Inspect benchmark run, and public writeups.
- **Phase 5: Production hardening — NORMAL, ongoing.** Keep cost, latency, sandboxing, monitoring, drift, and durability as permanent habits after the portfolio projects exist.

## Curated resources for this profile

### Foundations and mental models
- [HuggingFace LLM Course](https://huggingface.co/learn/llm-course) — quick foundations before Phase 0.
- [Building Effective Agents by Anthropic](https://anthropic.com/research/building-effective-agents) — workflow vs agent, augmented LLMs, core patterns.
- [Effective context engineering for AI agents](https://anthropic.com/engineering/effective-context-engineering-for-ai-agents) — context as the main engineering discipline.
- [Context Engineering for Agents by LangChain](https://blog.langchain.com/context-engineering-for-agents/) — Write, Select, Compress, Isolate.
- [How to think about agent frameworks](https://blog.langchain.com/how-to-think-about-agent-frameworks/) — pick frameworks by architecture, not hype.

### Python + TypeScript agent building
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) — runnable Python examples for workflows and agents.
- [OpenAI Cookbook](https://github.com/openai/openai-cookbook) — OpenAI-side tools, structured outputs, evals, and agents.
- [Claude Agent SDK docs](https://platform.claude.com/docs/en/agent-sdk) — reference harness with Python and TypeScript bindings.
- [LangGraph docs](https://langchain-ai.github.io/langgraph/) — primary Python runtime to learn deeply.
- [Deep Agents source](https://github.com/langchain-ai/deepagents) — read middleware and harness patterns while building Phase 2 and 3.
- [Mastra](https://mastra.ai) — TS-native alternative to watch and optionally compare, but not the main path because you are not TypeScript-only.

### Provider-mix resources
- [OpenAI Cookbook](https://cookbook.openai.com) — OpenAI-specific examples when you route to OpenAI models.
- [Claude Agent SDK, Skills reference](https://code.claude.com/docs/en/agent-sdk/skills) — progressive disclosure and skill loading.
- [Open Models have crossed a threshold](https://blog.langchain.com/open-models-have-crossed-a-threshold/) — use this when deciding whether open-weight models belong in a specific project.
- [Composio docs](https://composio.dev) — SaaS integrations and credential brokering.
- [Arcade docs](https://arcade.dev) — per-user identity and tool auth.

### Evals, traces, and hiring signal
- [Agent Evaluation Readiness Checklist](https://blog.langchain.com/agent-evaluation-readiness-checklist/) — use throughout Phase 4.
- [Demystifying evals for AI agents](https://anthropic.com/engineering/demystifying-evals-for-ai-agents) — single-turn, trajectory, judge, and end-state evals.
- [Inspect docs](https://inspect.aisi.org.uk) — benchmark-grade eval framework.
- [inspect_evals](https://github.com/UKGovernmentBEIS/inspect_evals) — GAIA, SWE-bench, Cybench, BFCL.
- [Braintrust docs](https://braintrust.dev) — framework-agnostic experiments and CI gates.
- [LangSmith docs](https://docs.smith.langchain.com) — best default if your portfolio centers on LangGraph.

### Production hardening
- [Code execution with MCP](https://anthropic.com/engineering/code-execution-with-mcp) — avoid stuffing every MCP tool into context.
- [Beyond permission prompts: making Claude Code more secure and autonomous](https://anthropic.com/engineering/claude-code-sandboxing) — sandboxing patterns.
- [Modal docs](https://modal.com/docs) — Python execution sandbox option.
- [E2B docs](https://e2b.dev) — agent-focused code execution sandbox.
- [Temporal Python SDK](https://docs.temporal.io) — durable execution option.
- [Inngest docs](https://inngest.com/docs) — durable steps and retries.

### Ongoing signal sources
- [Anthropic engineering blog](https://anthropic.com/engineering)
- [LangChain blog](https://blog.langchain.com)
- [Simon Willison's blog](https://simonwillison.net)
- [Hamel Husain's blog](https://hamel.dev)
- [Latent Space](https://latent.space)
- [AI Engineer](https://ai.engineer)

## Project deliverables
- [ ] Phase 0: 2-page mental-model doc
- [ ] Phase 0 public artifact: publish the mental-model doc + learning notes on GitHub
- [ ] Phase 1: tool-using agent + Claude Agent SDK rebuild
- [ ] Phase 1 public artifact: GitHub repo + writeup explaining what the harness gave you
- [ ] Phase 2: research-analyst Deep Agent + LangSmith trace URL
- [ ] Phase 2 public artifact: GitHub repo + architecture writeup with trace link
- [ ] Phase 3: 1,500-line mini-harness + post-mortem
- [ ] Phase 3 public artifact: GitHub repo + post-mortem comparing your harness to Claude Agent SDK and Deep Agents
- [ ] Phase 4: golden dataset + CI eval gate + Inspect benchmark run
- [ ] Phase 4 public artifact: eval report + failure-mode writeup + benchmark result
- [ ] Phase 5: production hardening checklist (ongoing)
- [ ] Hiring portfolio index: one README that links all phase projects, writeups, demos, and traces

## Next action
Today: create a GitHub repository named `agent-engineering-roadmap`, add this `MY_ROADMAP.md`, then start Phase 0 by reading [Building Effective Agents by Anthropic](https://anthropic.com/research/building-effective-agents) and writing 10 bullet notes on workflow vs agent.

## Duration math
Canonical focused timeline: 2 + 3 + 4 + 4 + 4 = 17 weeks. Your available time is 4-5 hours/week, so apply the ≤10 hours/week multiplier: 17 × 2.5 = 42.5 weeks. Phase 5 is ongoing and not included in the total.
