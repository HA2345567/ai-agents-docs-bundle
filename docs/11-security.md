# 11 · Security & Ethics

> 🟡 **Stub chapter.** The canonical reference below is authoritative and current; full 14-point treatment pending. PRs welcome.

## The canonical reference
[OWASP Top 10 for LLM Applications](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — prompt injection is risk #1, updated yearly by the OWASP GenAI Security Project. Read this before giving any agent real tool access.

## Key risks specific to agents (beyond plain LLM apps)
- **Excessive agency** — granting a tool more privilege than the task requires
- **Tool output re-entering context** — a tool that fetches a webpage/email can carry an injected instruction back into the agent's context, indistinguishable in principle from a user instruction
- **Memory poisoning** — long-term memory ([Ch. 05](05-agent-memory.md)) stores can be corrupted with adversarial content that influences future sessions
- **Goal hijacking in multi-agent systems** — one compromised agent influencing others it delegates to

## Secure Code Execution Sandboxes
When an agent is allowed to execute arbitrary code (e.g., Python scripts it generates to solve math/data problems), it **must** run in a secure, isolated sandbox to prevent host system compromise.

| Sandbox Provider | Description | Docs |
|---|---|---|
| **E2B Sandbox** | Secure sandboxes (microVMs) for running AI-generated code and agent tools | [e2b.dev/docs](https://e2b.dev/docs) |
| **Docker** | Running local Docker containers with CPU/memory limits for safe local execution | [docs.docker.com](https://docs.docker.com/) |
| **Fly.io Machines** | MicroVMs for serverless agent executions on demand | [fly.io/docs/machines](https://fly.io/docs/machines/) |

## Data Privacy & PII Redaction
Agents often ingest private user logs or emails. Redacting Personally Identifiable Information (PII) before forwarding inputs to LLM APIs is crucial.
*   **Microsoft Presidio:** [microsoft.github.io/presidio](https://microsoft.github.io/presidio/) — The standard open-source library for scanning and redacting sensitive text.

## Bias, Toxicity & Safety Guardrails
Enforcing boundary layers on agent inputs and outputs prevents toxic generation, PII leaks, or prompt injection bypasses.
*   **Google Cloud Model Armor:** [cloud.google.com/model-armor](https://cloud.google.com/model-armor) — An enterprise AI security layer ("AI firewall") designed to filter prompt injections, safety risks, toxicity, and sensitive data leakage (PII) for any cloud model.
*   **Guardrails with LangChain:** [python.langchain.com/docs/concepts/#guardrails](https://python.langchain.com/docs/concepts/#guardrails) — Standard middleware systems and Human-in-the-Loop (HITL) checkpoints in LangGraph/LangChain to validate outputs or restrict tool access dynamically.
*   **NVIDIA NeMo Guardrails:** [docs.nvidia.com/nemo/guardrails](https://docs.nvidia.com/nemo/guardrails/) — Programmable guardrails for LLM conversational safety.
*   **Llama Guard:** [huggingface.co/meta-llama/Llama-Guard-3](https://huggingface.co/meta-llama/Llama-Guard-3) — Fine-tuned models for input-output moderation.

## High-quality secondary resources
- [OWASP Top 10 for LLMs: A Practitioner's Guide — Improving](https://www.improving.com/thoughts/owasp-top-10-llm-security-guide/)
- [OWASP Top 10 for LLM Applications (2025) explained — Aembit](https://aembit.io/blog/owasp-top-10-llm-risks-explained/) — covers what changed (RAG poisoning, excessive agency)
- [Promptfoo — OWASP LLM Top 10 red-team test docs](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/)

## Seminal / applied research
- [Architecting Resilient LLM Agents: Secure Plan-Execute (arXiv, 2025)](https://arxiv.org/pdf/2509.08646) — tool sandboxing and least-privilege for planner-executor agents

**Related:** ← [10 · Observability](10-observability.md) · [12 · Courses & Communities](12-courses-communities.md) →
