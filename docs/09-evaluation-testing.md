# 09 · Evaluation & Testing

> 🟡 **Stub chapter.** Comparison table is curated and accurate; full 14-point treatment pending. PRs welcome.

## Testing Layers
*   **Unit Testing for Individual Tools:** Ensuring helper functions, parser formats, and individual API calls return exact schemas.
*   **Integration Testing for Flows:** Verifying the full multi-turn execution chain (Agent -> Tool -> Model -> Refinement -> Final Output).
*   **Human-in-the-Loop (HITL) Evaluation:** Gatekeeping critical agent actions (like sending emails or triggering payments) using human approval loops and grading agent logs.

## Metrics to Track
*   **Hallucination Rate:** Ensuring generated statements match retrieved context.
*   **Semantic Similarity / Accuracy:** Scoring final agent outputs against ground truth responses.
*   **Success Rate / Goal Completion:** Measuring how frequently the agent completes user tasks.
*   **Cost & Latency:** Monitoring token consumption and time to complete execution loops.

## Tool comparison

| Tool | Best for | Licensing | Docs |
|---|---|---|---|
| **LangSmith** | Tracing + evals, best with LangChain/LangGraph | Commercial (free tier) | [docs.langchain.com](https://docs.langchain.com) |
| **Ragas** | RAG-specific metrics (faithfulness, relevancy, retrieval precision) | Open source (Apache 2.0) | [docs.ragas.io](https://docs.ragas.io) |
| **DeepEval** | pytest-style unit testing, CI/CD friendly | Open source | [docs.confident-ai.com](https://docs.confident-ai.com) |
| **Promptfoo** | Red-teaming / adversarial testing, OWASP LLM Top 10 suites | Open source (MIT) | [promptfoo.dev/docs](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/) |

## LLM-as-a-Judge (G-Eval)
Using a capable model (like Claude 3.5 Sonnet or GPT-4o) as an evaluator ("judge") to grade agent outputs based on custom rubrics. This replaces slow and costly human grading with structured, automated criteria.
*   **Model-Based Evaluation Guides:** [langfuse.com/docs/scores/model-based-evals](https://langfuse.com/docs/scores/model-based-evals) (Langfuse conceptual walkthrough).
*   **G-Eval: NLG Evaluation with Chain-of-Thought:** Explains scoring outputs with reasoning steps using OpenAI/Claude. Covered in [docs.confident-ai.com/docs/evaluation-metrics-g-eval](https://docs.confident-ai.com/docs/evaluation-metrics-g-eval) (DeepEval G-Eval implementation).

## High-quality secondary resources
- [DeepEval vs. RAGAS vs. LangSmith — Descope](https://www.descope.com/blog/post/deepeval-vs-ragas-vs-langsmith) — clearest breakdown of when to use which
- [DeepEval vs RAGAS (2026) — genai.qa](https://genai.qa/blog/deepeval-vs-ragas/)

**Related:** ← [08 · Building Agents](08-building-agents-frameworks.md) · [10 · Observability](10-observability.md) →
