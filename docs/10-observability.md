# 10 · Observability & Debugging

> 🟡 **Stub chapter.** Comparison table is curated and accurate; full 14-point treatment pending. PRs welcome.

## Core Concepts
*   **Structured Logging & Tracing:** Recording prompt templates, raw inputs/outputs, model parameters, and sub-call latencies at every node.
*   **Inner vs. Outer Loop Tracing:** Tracking the low-level tool invocation logs (inner loop) separately from the high-level user session flow (outer loop).

## Tool comparison

| Tool | Best for | Licensing | Docs |
|---|---|---|---|
| **LangFuse** | Open-source, self-hostable, tracing + prompt mgmt + evals in one | Open source (MIT core) | [langfuse.com/docs](https://langfuse.com/docs) |
| **Helicone** | Drop-in proxy — one-line base-URL change | Open source + hosted | [docs.helicone.ai](https://docs.helicone.ai) |
| **Arize Phoenix** | ML-grade evaluation rigor, strong for RAG debugging | Open source | [docs.arize.com/phoenix](https://docs.arize.com/phoenix) |
| **OpenTelemetry GenAI semantic conventions** | Vendor-neutral standard tracing spec | Open standard | [opentelemetry.io](https://opentelemetry.io/docs/specs/semconv/gen-ai/) |

## High-quality secondary resources
- [8 LLM Observability Tools to Monitor & Eval AI Agents — LangChain resource hub](https://www.langchain.com/resources/llm-observability-tools)
- [Agent Observability: LangSmith, Langfuse, Arize 2026 — Digital Applied](https://www.digitalapplied.com/blog/agent-observability-platforms-langsmith-langfuse-arize-2026)

**Related:** ← [09 · Evaluation & Testing](09-evaluation-testing.md) · [11 · Security](11-security.md) →
