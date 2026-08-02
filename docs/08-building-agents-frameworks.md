# 08 · Building Agents: Frameworks & SDKs

> 🟡 **Stub chapter.** Comparison table is curated and accurate; full 14-point treatment pending. PRs welcome.

## Framework comparison

| Framework | Best for | Maturity | License | Docs |
|---|---|---|---|---|
| **Claude Agent SDK** (Anthropic) | Native Claude integration, coding agents | Stable | Proprietary API, open SDK | [platform.claude.com/docs/en/agent-sdk/overview](https://platform.claude.com/docs/en/agent-sdk/overview) |
| **OpenAI Agents SDK** | Native OpenAI integration | Stable | Proprietary API, open SDK | [developers.openai.com/api/docs/guides/agents](https://developers.openai.com/api/docs/guides/agents) |
| **Google ADK** | Native Gemini integration, Google Cloud | Stable | Apache 2.0 | [google.github.io/adk-docs](https://google.github.io/adk-docs/) |
| **LangGraph** | Stateful, graph/cyclical control flow, most control | Mature | MIT | [docs.langchain.com](https://docs.langchain.com/oss/python/concepts/products) |
| **Pydantic AI** | Type-safe, structured Python-first agent design | Stable | Apache 2.0 | [ai.pydantic.dev](https://ai.pydantic.dev) |
| **Mastra** | TypeScript-first environments, workflows, and Next.js integration | Stable | MIT | [mastra.ai/docs](https://mastra.ai/docs) |
| **Agno** (formerly Phidata) | Building multi-agent systems with structured output and memory | Mature | MIT | [docs.agno.com](https://docs.agno.com) |
| **LangChain** | General LLM app framework | Mature | MIT | [docs.langchain.com](https://docs.langchain.com) |
| **CrewAI** | Role-based multi-agent "crews" | Mature | MIT | [docs.crewai.com](https://docs.crewai.com) |
| **LlamaIndex Agents** | RAG-first, grounded in your own data | Mature | MIT | [docs.llamaindex.ai](https://docs.llamaindex.ai) |
| **Microsoft AutoGen / Agent Framework** | Conversational multi-agent, Azure | Mature | MIT | [microsoft.github.io/autogen](https://microsoft.github.io/autogen/) |
| **Hugging Face smolagents** | Lightweight "code agents" | Growing | Apache 2.0 | [huggingface.co/docs/smolagents](https://huggingface.co/docs/smolagents/index) |
| **Rig** | High-performance, lightweight Rust-native AI agents | Growing | MIT | [github.com/0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) |
| **Haystack** | Search/RAG-first pipelines | Mature | Apache 2.0 | [haystack.deepset.ai](https://haystack.deepset.ai/overview/quick-start) |

## Choosing a framework
- Committed to one model provider, want first-party support → vendor SDK (Claude Agent SDK / OpenAI Agents SDK / ADK)
- Python-centric, strict Pydantic schema validation → Pydantic AI
- TypeScript-centric, Next.js / Node web stacks → Mastra
- Structured function calling, quick agent deployment → Agno
- Rust-centric, ultra-low latency & high performance → Rig
- Need portability across models, complex branching logic → LangGraph
- Role-based multi-agent teams, fastest prototyping → CrewAI
- RAG-heavy, document-grounded agents → LlamaIndex

## LLM Gateways & Routers
As you scale your agentic workflows across different models and frameworks, managing key rotation, retries, caching, and fallback logic manually becomes complex. **LLM Gateways** act as a single proxy layer for all model queries.

| Gateway / Proxy | Core Features | Docs |
|---|---|---|
| **LiteLLM** | Translate inputs/outputs to 100+ LLM APIs using OpenAI format, load balance, track spend | [docs.litellm.ai](https://docs.litellm.ai/) |
| **Portkey** | Production gateway with prompt management, semantic caching, routing, and guardrails integration | [docs.portkey.ai](https://docs.portkey.ai/) |

## High-quality secondary resources
- [A Detailed Comparison of Top 6 AI Agent Frameworks in 2026 — Turing](https://www.turing.com/resources/ai-agent-frameworks)
- [Comparative Study: LangGraph vs LlamaIndex vs CrewAI with IBM Watsonx.ai — Medium](https://medium.com/@ashgadag/comparative-study-langgraph-vs-llamaindex-vs-crewai-agents-with-ibm-watsonx-ai-c01ceb14ea45)

**Related:** ← [07 · MCP](07-model-context-protocol.md) · [09 · Evaluation & Testing](09-evaluation-testing.md) →
