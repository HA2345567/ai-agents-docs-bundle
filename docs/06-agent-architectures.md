# 06 · Agent Architectures

> 🟡 **Stub chapter.** Links and papers are curated and accurate; full 14-point treatment (diagrams, code per pattern) pending. PRs welcome.

## Overview

All agent architectures are specific "shapes" of the generic agent loop from [Ch. 03](03-agent-fundamentals.md). The difference is *when* reasoning and action are interleaved vs. separated.

| Pattern | Shape | Best for |
|---|---|---|
| **ReAct** | Interleave reasoning + acting, one step at a time | General-purpose, dynamic tasks where the next step depends on the last result |
| **Chain-of-Thought (CoT)** | Reason step-by-step before answering, no tool calls | Pure reasoning tasks, math, classification |
| **Plan-and-Execute / ReWOO** | Plan all steps up front, then execute | Predictable multi-step tasks; cheaper (fewer LLM calls) and more auditable |
| **Tree of Thoughts (ToT)** | Explore multiple reasoning branches, backtrack | Search/puzzle-like problems with multiple candidate solutions |
| **Planner-Executor / DAG agents** | Decompose into a dependency graph of sub-tasks | Complex workflows with parallelizable sub-steps |

## Anthropic's Core Agentic Workflows
Anthropic's seminal guide, *Building Effective Agents*, categorizes agent architectures into 5 key design patterns (workflows). You should learn these to choose the right complexity for your task:

*   **Workflows** (Prescribed, step-by-step paths):
    *   **Prompt Chaining:** Decomposing a complex task into a sequential chain of steps, where each step's output is processed by the next.
    *   **Routing:** Classifying an input and sending it to a specialized downstream LLM/prompt template (e.g., separating support queries into refund requests vs. technical issues).
    *   **Parallelization:** Running multiple LLMs in parallel (either doing the same task for voting/self-consistency, or different sub-tasks) and aggregating their output.
*   **Agents** (Dynamic, self-directed paths):
    *   **Orchestrator-Workers:** A central coordinator agent analyzes a problem, dynamically delegates tasks to worker agents, and aggregates their results.
    *   **Evaluator-Optimizer:** A generator agent creates draft content, and an evaluator agent checks it against a rubric, returning feedback to the generator in a loop.

## Official documentation
- [Anthropic — Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents) — covers orchestrator-workers and evaluator-optimizer patterns
- [Visual Guide to Agentic Workflows — LangChain Blog](https://blog.langchain.dev/) — Interactive/visual representations of these 5 patterns.

## Seminal papers
| Paper | Pattern |
|---|---|
| [ReAct (Yao et al., 2023)](https://arxiv.org/abs/2210.03629) | ReAct |
| [Chain-of-Thought Prompting (Wei et al., 2022)](https://arxiv.org/abs/2201.11903) | CoT |
| [Tree of Thoughts (Yao et al., 2023)](https://arxiv.org/abs/2305.10601) | ToT |
| [ReWOO: Decoupling Reasoning from Observations (Xu et al., 2023)](https://arxiv.org/abs/2305.18323) | Plan-and-Execute |
| [Reflexion: Language Agents with Verbal Reinforcement Learning (Shinn et al., 2023)](https://arxiv.org/abs/2303.11366) | Self-correction loop |

## High-quality secondary resources
- [ReAct Prompting — promptingguide.ai](https://www.promptingguide.ai/techniques/react)
- [Every AI Agent Architecture in One Place — Towards AI (Medium)](https://pub.towardsai.net/every-ai-agent-architecture-in-one-place-595ba68d49cd) — best single comparison of ToT/GoT/ReWOO/LLMCompiler
- [Navigating Modern LLM Agent Architectures — Wollen Labs](https://www.wollenlabs.com/blog-posts/navigating-modern-llm-agent-architectures-multi-agents-plan-and-execute-rewoo-tree-of-thoughts-and-react)
- [Agentic AI Architecture: 5 Patterns Explained — Redis Blog](https://redis.io/blog/agentic-ai-architecture-examples/)

**Related:** ← [05 · Agent Memory](05-agent-memory.md) · [07 · Model Context Protocol](07-model-context-protocol.md) →
