# 16 · Best Books

> ✅ Every title, author, and publisher below was verified via search in this session (August 2026). Organized by what you actually need each book for, not just publication date.

## Read this order

**If you don't know how LLMs work internally** → start with *Build a Large Language Model (From Scratch)* or *Hands-On Large Language Models*, then move to the agent-specific books. Skipping this step is the most common reason people bounce off agent frameworks — you can't debug what you don't understand.

## Foundations — how LLMs actually work

| Book | Author(s) | Publisher | Why |
|---|---|---|---|
| **Build a Large Language Model (From Scratch)** | Sebastian Raschka | Manning, 2024 | Codes a GPT-style model from raw PyTorch — no libraries. The best way to stop treating LLMs as a black box before you build agents on top of them. Runs on a laptop. |
| **Hands-On Large Language Models** | Jay Alammar & Maarten Grootendorst | O'Reilly, 2024 | Alammar's famous visual-explainer style applied to embeddings, semantic search, classification, generation — directly informs how you'd design agent memory/retrieval components. |
| **Artificial Intelligence: A Modern Approach** (4th ed.) | Stuart Russell & Peter Norvig | Pearson | The original textbook definition of a "rational agent" — perceives environment, acts to maximize goal achievement. Every modern "agent loop" diagram is a descendant of this book's framing. Dense and academic, but it's the source, not a summary of the source. |

## Agent-specific — the core reading

| Book | Author(s) | Publisher | Why |
|---|---|---|---|
| **AI Engineering** | Chip Huyen | O'Reilly, 2025 | The most-recommended 2026 pick across every list I checked. Full production stack: evaluation, prompt design, RAG, agent architectures, deployment tradeoffs. Engineering-first, not research-first. Her free blog post "[Agents](https://huyenchip.com/2025/01/07/agents.html)" (§13/15 addendum) is adapted directly from this book's agent chapter. |
| **Building Agentic AI Systems** | Anjanava Biswas & Wrick Talukdar | Packt, 2025 | The most complete single-volume treatment of agent architecture specifically — coordinator/worker/delegator patterns, reflection, tool use, planning, and a full chapter on trust/safety/ethics in agent design. |
| **LLM Engineer's Handbook** | Paul Iusztin & Maxime Labonne | Packt, 2024 | Full LLMOps pipeline — fine-tuning, RAG architecture, deployment, reliability under real load. Reads like it was written by people who've hit the same production walls you will. |

## Systems thinking — for when your agent needs to survive contact with production

| Book | Author(s) | Publisher | Why |
|---|---|---|---|
| **Designing Machine Learning Systems** | Chip Huyen | O'Reilly, 2022 | Not agent-specific, but the precursor to *AI Engineering* — data drift, retraining, monitoring, reliability under real-world constraints. Read this if you're the engineer who has to keep the agent running, not just ship the demo. |

---

### A word on book-list churn
Several "Top 10/15 AI agent books" roundups from mid-2026 also list titles like *Mastering Agentic AI*, *Designing Multi-Agent Systems*, and *AI Engineering Bible* — these weren't independently verified against a publisher/author record in this session the way the ones above were, so they're left out rather than risk pointing you at something that doesn't check out. If you want those chased down and confirmed too, say so and I'll verify them the same way.

**Related:** ← [15 · Essential Resources Addendum](#) · [13 · Free YouTube Channels](13-youtube-channels.md) · [Back to README](../README.md)
