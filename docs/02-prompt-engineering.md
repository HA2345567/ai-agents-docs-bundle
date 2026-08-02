# 02 · Prompt Engineering

> 🟡 **Stub chapter.** Links are curated and accurate; full 14-point treatment (diagrams, papers, exercises) pending. PRs welcome.

## Plain-language explanation (brief)
Prompt engineering is the practice of structuring instructions, context, and examples so an LLM reliably produces the output you want. For agents specifically, this extends to how you write system prompts, tool descriptions ([Ch. 04](04-tools-function-calling.md)), and reasoning scaffolds (CoT, ReAct — [Ch. 06](06-agent-architectures.md)).

## Official documentation
- **Anthropic Prompt Engineering Guide:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) — The industry gold standard guide.
- **Using XML Tags with Claude:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags) — Essential structuring technique using delimiters.
- **System Prompts Best Practices:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts) — Global persona and safety boundaries.
- **Anthropic Interactive Prompt Generator:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-generator](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-generator) — Helper tool to auto-generate system instructions.
- **OpenAI Prompt Engineering Guide:** [platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)

## High-quality secondary resources
- [Prompt Engineering Guide (promptingguide.ai)](https://www.promptingguide.ai/) — the gold standard, actively maintained by DAIR.AI
- [Learn Prompting](https://learnprompting.org/docs/introduction) — beginner-friendly alternative
- [Google Cloud — Prompt Engineering for AI Guide](https://cloud.google.com/discover/what-is-prompt-engineering)
- [IBM — The 2026 Guide to Prompt Engineering](https://www.ibm.com/think/prompt-engineering)

## Seminal papers
| Paper | Contribution |
|---|---|
| [Chain-of-Thought Prompting Elicits Reasoning (Wei et al., 2022)](https://arxiv.org/abs/2201.11903) | Foundational technique underlying almost all agent reasoning |
| [Self-Consistency Improves Chain of Thought Reasoning (Wang et al., 2022)](https://arxiv.org/abs/2203.11171) | Sampling multiple reasoning paths and voting |

## Core techniques (learn in this order)
zero-shot → few-shot → chain-of-thought → self-consistency → ReAct → Tree of Thoughts (all covered with examples at [promptingguide.ai/techniques](https://www.promptingguide.ai/techniques))

**Related:** ← [01 · LLM Fundamentals](01-llm-fundamentals.md) · [03 · Agent Fundamentals](03-agent-fundamentals.md) →
