# 05 · Agent Memory

> 🟡 **Stub chapter.** Links are curated and accurate; full 14-point treatment pending. PRs welcome.

## Plain-language explanation (brief)
Since the context window ([Ch. 01](01-llm-fundamentals.md)) resets every call, "memory" is an engineering pattern you build on top, not a native LLM capability. **Short-term memory** = the current conversation, kept in-context. **Long-term memory** = information persisted outside the context window (vector DB, SQL, key-value store) and selectively retrieved back in on later calls.

## Mental model
Short-term memory is your working desk; long-term memory is the filing cabinet. A good agent knows when to walk to the cabinet (retrieve) instead of trying to remember everything on the desk.

## Episodic vs. Semantic Memory
*   **Episodic Memory:** Storing sequential histories of conversation sessions or specific user interactions (remembering "what happened and when").
*   **Semantic Memory:** Extracting and storing factual facts, rules, and world knowledge (remembering "user preferences, user profile details, or domain facts").

## Maintaining Memory & Vector Databases
Memory state overflows context windows quickly. Managing it requires:
*   **RAG and Vector Databases:** Similarity search retrieves relevant facts based on similarity queries.
*   **Summarization / Compression:** Periodically summarizing older conversation chunks to compress dialogue histories.
*   **Forgetting & Aging Strategies:** Deleting stale, unused, or superseded information based on priority/time decay.
*   **User Profile Storage:** Storing structural, profile-based configurations of a user's habits and interests.

## Official documentation
- [Anthropic — Context Editing & Memory](https://docs.claude.com) — official patterns for managing context over long agent sessions
- [OpenAI — Agents SDK: Memory & Sessions](https://developers.openai.com/api/docs/guides/agents)

## Official Memory Framework Documentation
| Framework | Purpose | Docs |
|---|---|---|
| **Letta** (MemGPT) | Stateful agent orchestration, long-term memory management, and agent-as-a-service | [letta.readme.io](https://letta.readme.io/) |
| **Mem0** | Personalized, self-improving memory layer for AI applications | [docs.mem0.ai](https://docs.mem0.ai/) |
| **Zep** | Fast, production-grade memory store for LLM apps (session, semantic, user memory) | [docs.getzep.com](https://docs.getzep.com/) |

## High-quality secondary resources
- [IBM — What Is AI Agent Memory?](https://www.ibm.com/think/topics/ai-agent-memory)
- [Redis Engineering Blog — Build Smarter AI Agents: Short & Long-Term Memory](https://redis.io/blog/build-smarter-ai-agents-manage-short-term-and-long-term-memory-with-redis/)
- [Beyond Short-term Memory: 3 Types of Long-term Memory AI Agents Need — MachineLearningMastery.com](https://machinelearningmastery.com/beyond-short-term-memory-the-3-types-of-long-term-memory-ai-agents-need/) — episodic/semantic/procedural framing
- [Agentic AI Memory vs Vector Database — Atlan](https://atlan.com/know/agentic-ai-memory-vs-vector-database/) — why memory is more than similarity search

## Related concepts
- [01 · LLM Fundamentals](01-llm-fundamentals.md) (RAG/embeddings underpin long-term memory retrieval)
- [09 · Evaluation & Testing](09-evaluation-testing.md) (testing memory retrieval quality)

**Related:** ← [04 · Tools & Function Calling](04-tools-function-calling.md) · [06 · Agent Architectures](06-agent-architectures.md) →
