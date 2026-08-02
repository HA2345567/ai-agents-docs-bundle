# 🧠 Awesome AI Agents — The Complete Learning Roadmap & Docs Bundle

A single-file, GitHub-ready reference for learning **AI Agents** end-to-end — mirrors the structure of the [roadmap.sh AI Agents roadmap](https://roadmap.sh/ai-agents), but every bullet is backed with the best real resource I could find across **official docs, Medium, Reddit, GeeksforGeeks, IBM/AWS/Google explainers, arXiv papers, and dev blogs** — not just GitHub repos.

[![Status](https://img.shields.io/badge/status-active-brightgreen)]() [![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange)]()

> 🍴 Fork this, star it, and use it as your personal or team study path. Sections go beginner → advanced, following the exact order of the roadmap.

---

## Table of Contents
0. [Prerequisites](#0-prerequisites)
1. [LLM Fundamentals](#1-llm-fundamentals)
2. [Prompt Engineering](#2-prompt-engineering)
3. [AI Agents 101](#3-ai-agents-101)
4. [Tools / Actions](#4-tools--actions)
5. [Agent Memory](#5-agent-memory)
6. [Agent Architectures](#6-agent-architectures)
7. [Model Context Protocol (MCP)](#7-model-context-protocol-mcp)
8. [Building Agents](#8-building-agents)
9. [Evaluation & Testing](#9-evaluation--testing)
10. [Debugging, Monitoring & Observability](#10-debugging-monitoring--observability)
11. [Security & Ethics](#11-security--ethics)
12. [Free Structured Courses](#12-free-structured-courses)
13. [Communities (Reddit, Discord, Forums)](#13-communities-reddit-discord-forums)
14. [Suggested Study Path](#14-suggested-study-path)

---

## 0. Prerequisites

| Topic | Best Resource |
|---|---|
| Git & GitHub | [roadmap.sh Git & GitHub Roadmap](https://roadmap.sh/git-github) |
| REST APIs | [roadmap.sh API Design Roadmap](https://roadmap.sh/api-design) |
| Backend basics | [roadmap.sh Backend Beginner Roadmap](https://roadmap.sh/backend) |

---

## 1. LLM Fundamentals

### Transformers, tokenization, context windows
| Resource | Source type | Link |
|---|---|---|
| Tokens & Context Windows in LLMs | GeeksforGeeks (clean technical explainer) | [geeksforgeeks.org](https://www.geeksforgeeks.org/artificial-intelligence/tokens-and-context-windows-in-llms/) |
| Tokens and Context Windows, Explained | MLQ Guides (concise + worked example) | [blog.mlq.ai](https://blog.mlq.ai/tokens-context-window-llms/) |
| Understanding LLM Context Windows: Tokens, Attention, Challenges | **Medium** — good on the "lost in the middle" problem | [medium.com/@tahirbalarabe2](https://medium.com/@tahirbalarabe2/understanding-llm-context-windows-tokens-attention-and-challenges-c98e140f174d) |
| LLM context windows: what they are & how they work | Redis Engineering Blog (practical, benchmarked) | [redis.io/blog](https://redis.io/blog/llm-context-windows/) |
| Tokens, Context Windows, and Why They Matter | **DEV Community** — beginner-friendly, real debugging story | [dev.to/satinathnit](https://dev.to/satinathnit/tokens-context-windows-and-why-they-matter-the-complete-guide-2ko7) |

### Generation controls (temperature, top-p, penalties, max length)
Generation parameters dictate model determinism and output structure. You should adjust:
*   **Temperature / Top-p:** Controls randomness. Use low values (~0.0 to 0.2) for structured outputs and code generation; use higher values (~0.7 to 1.0) for creative writing.
*   **Frequency / Presence Penalties:** Discourage repetition of recently generated tokens/topics.
*   **Stopping Criteria & Max Length:** Safety parameters to enforce strict token boundaries and avoid infinite loops.

| API Reference | Link |
|---|---|
| **Anthropic Messages Parameter Reference** | [docs.anthropic.com/en/api/messages](https://docs.anthropic.com/en/api/messages) |
| **OpenAI Chat Completion Parameters** | [platform.openai.com/docs/api-reference/chat/create](https://platform.openai.com/docs/api-reference/chat/create) |

### Open vs. closed weight models, model families
- Hugging Face Model Hub (browse open-weight families): [huggingface.co/models](https://huggingface.co/models)
- "Open weight vs open source AI models" — IBM explainer: [ibm.com/think/topics/open-source-ai](https://www.ibm.com/think/topics/open-source-ai)

### Embeddings, Vector Search & RAG basics
| Resource | Source type | Link |
|---|---|---|
| What is RAG (Retrieval-Augmented Generation)? | IBM Think — best conceptual breakdown of chunking/embedding/retrieval | [ibm.com/think/topics/retrieval-augmented-generation](https://www.ibm.com/think/topics/retrieval-augmented-generation) |
| What is RAG? | AWS — practitioner-oriented, good diagrams | [aws.amazon.com/what-is/retrieval-augmented-generation](https://aws.amazon.com/what-is/retrieval-augmented-generation/) |
| Introduction to RAG and Vector Databases | **Medium** — step-by-step retrieve/augment/generate breakdown | [medium.com/@sachinsoni600517](https://medium.com/@sachinsoni600517/introduction-to-rag-retrieval-augmented-generation-and-vector-database-b593e8eb6a94) |
| Vector Databases for RAG | IBM Think | [ibm.com/think/topics/rag-vector-database](https://www.ibm.com/think/topics/rag-vector-database) |
| RAG Series Part 2 — Vector Databases | **Medium** (100 Days of AI series — good for sequential learning) | [medium.com/@akankshasinha247](https://medium.com/@akankshasinha247/rag-series-part-2-storing-intelligence-understanding-vector-databases-in-rag-systems-21729ca0ac02) |

### Streamed vs. Unstreamed Responses
Streaming returns tokens incrementally as they are generated, improving user experience by reducing Time to First Token (TTFT). Unstreamed responses block execution until the entire generation completes.
*   [Anthropic — Streaming Messages API Guide](https://docs.anthropic.com/en/api/messages-streaming)
*   [Server-Sent Events (SSE) and Streaming — Vellum Guide](https://www.vellum.ai/)

### Reasoning vs. Standard Models
Reasoning models use internal reinforcement learning and Chain-of-Thought reasoning *before* outputting any visible tokens. They perform significantly better on complex math, logic, and coding tasks but consume more time and input/output tokens.
*   **Anthropic Extended Thinking:** [docs.anthropic.com/en/docs/build-with-claude/extended-thinking](https://docs.anthropic.com/en/docs/build-with-claude/extended-thinking) (How Claude 3.7 Sonnet uses adaptive reasoning budgets).
*   **OpenAI Reasoning Guide:** [platform.openai.com/docs/guides/reasoning](https://platform.openai.com/docs/guides/reasoning) (Covers o1 and o3-mini models).

### Fine-Tuning vs. Prompt Engineering
*   **Prompt Engineering:** Quick iteration, context-based, best for defining behaviors and structure.
*   **Fine-Tuning:** Customizing weights, best for style transfer, domain specificity, and lowering latency/cost by baking instructions directly into the model weights.
*   [When to Prompt vs. Fine-Tune — OpenAI Guide](https://platform.openai.com/docs/guides/fine-tuning)

### Pricing & Token-Based Pricing
Understanding cost estimation is critical for deploying agents. Pricing differs for prompt tokens, completion tokens, prompt caching (writing vs. reading cache), and extended reasoning tokens.
*   [Hugging Face / Ray — LLM Cost Calculation and Performance numbers](https://github.com/ray-project/llm-numbers)

---

## 2. Prompt Engineering

| Resource | Why it's the pick |
|---|---|
| [Prompt Engineering Guide (promptingguide.ai)](https://www.promptingguide.ai/) — by DAIR.AI | The gold standard. 3M+ learners, covers zero-shot → ReAct → agents, actively maintained. Also on [GitHub](https://github.com/dair-ai/Prompt-Engineering-Guide). |
| [Learn Prompting](https://learnprompting.org/docs/introduction) | Free, beginner-friendly, cited by Google/Microsoft/Wikipedia. Good if promptingguide.ai feels too dense at first. |
| [Google Cloud — Prompt Engineering for AI Guide](https://cloud.google.com/discover/what-is-prompt-engineering) | Vendor-neutral fundamentals + a free downloadable PDF whitepaper. |
| [IBM — The 2026 Guide to Prompt Engineering](https://www.ibm.com/think/prompt-engineering) | Good "why" explanations, links to a hands-on GitHub tutorial repo. |

**Core techniques to learn in order:** zero-shot → few-shot → chain-of-thought (CoT) → self-consistency → ReAct → Tree of Thoughts. All are documented with examples on [promptingguide.ai/techniques](https://www.promptingguide.ai/techniques).

### Writing Good Prompts (Structured & XML tags)
Claude-specific guidelines represent the gold standard for structuring prompts using custom delimiters like XML tags to feed context, instructions, and examples cleanly.
*   **Anthropic Prompt Engineering Overview:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
*   **Using XML Tags:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/use-xml-tags) — Essential delimiter strategy for Claude.
*   **System Prompts:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts) — Setting global boundaries, roles, and safety instructions.
*   **Anthropic Prompt Generator:** [docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-generator](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-generator) — Interactive tool to auto-generate structured system instructions.

---

## 3. AI Agents 101

| Concept | Resource |
|---|---|
| What is an AI agent? (workflows vs. agents) | [Anthropic — Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents) — the definitive primer, cited by nearly every other guide on this list |
| The Agent Loop (Perceive → Reason → Act → Observe) | [Hugging Face Agents Course, Unit 1](https://huggingface.co/learn/agents-course/unit1/introduction) |
| **Loop Engineering (Inner vs. Outer Loop)** | [Addy Osmani — Loop Engineering](https://addyosmani.com/) (Designing the self-correcting inner-loop harness) & [Own the Outer Loop](https://addyosmani.com/) (The human role in evaluating agent outputs) |
| Real-world agent use cases (assistants, coding, data analysis, scraping, game NPCs) | [Every AI Agent Architecture in One Place — Towards AI (Medium)](https://pub.towardsai.net/every-ai-agent-architecture-in-one-place-595ba68d49cd) |

### The Agent Loop
The core cycle of any agentic system revolves around four phases:
1.  **Perceive (User Input / Environment):** The agent receives input prompts, system state, or environment variables.
2.  **Reason and Plan:** The model analyzes the inputs, sets sub-goals, and decides on the execution path.
3.  **Acting (Tool Invocation):** The agent formats and executes external actions (calling APIs, queries, code runtimes).
4.  **Observation & Reflection:** The agent inspects the tool output/environment feedback and evaluates if the goal has been achieved or requires redirection.

### Example Agent Use Cases
*   **Personal Assistants:** Conversational agents acting on calendar, emails, and notes.
*   **Code Generation:** Self-correcting coding agents (e.g. SWE-bench style agents) that write, run, and patch code.
*   **Data Analysis:** Agents executing queries and plotting visualizations dynamically.
*   **Web Scraping / Crawling:** Browser automation agents executing multi-step web research.
*   **NPC / Game AI:** Generative agents simulating human-like behavior in virtual worlds.

---

## 4. Tools / Actions

Concept: how an agent defines a tool (name, description, input/output schema, error handling) and invokes it.

| Resource | Covers |
|---|---|
| [OpenAI — Function Calling Guide](https://platform.openai.com/docs/guides/function-calling) | Canonical `tools` JSON-schema format |
| [Anthropic — Tool Use Docs](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview) | `input_schema` format, server-side tools (web search, code execution) |
| [Google — Gemini Function Calling Docs](https://ai.google.dev/gemini-api/docs/function-calling) | Protocol-buffer style `FunctionDeclaration` |
| [LLM Function Calling and Tool Use Guide 2026 — RockB](https://baeseokjae.github.io/posts/llm-function-calling-tool-use-guide-2026/) | Best **single side-by-side comparison** of OpenAI vs Anthropic vs Gemini schemas, with working code for each |
| [🔬 Native Function Calling: How OpenAI, Claude & Gemini Really Work — Medium](https://medium.com/@vikassanmacs0609/native-function-calling-how-openai-claude-gemini-really-work-b3bad4dee182) | Practical code comparison including local models via Ollama |

### Anthropic Claude Computer Use
Anthropic provides a state-of-the-art API allowing Claude to interact directly with OS-level user interfaces: navigating desktop screens, moving cursors, clicking, and typing.
*   **Computer Use Guide:** [docs.anthropic.com/en/docs/build-with-claude/computer-use](https://docs.anthropic.com/en/docs/build-with-claude/computer-use)

### Web Browsing & Automation Tools
| Tool / Resource | Description | Link |
|---|---|---|
| **Browser Use** | The leading open-source web agent framework to control browsers | [docs.browser-use.com](https://docs.browser-use.com/) |
| **Playwright** | The standard web testing/automation framework used as the backbone for web agents | [playwright.dev](https://playwright.dev/) |
| **WebArena** | A web agent evaluation environment (benchmarking agents on real-world web tasks) | [webarena.dev](https://webarena.dev/) |

### Examples of Tools
Agents interface with the world through structured tools:
*   **Web Search:** Searching Google, DuckDuckGo, or Bing APIs (e.g., Tavily, Exa, Serper).
*   **Code Execution / REPL:** Executing Python/JavaScript dynamically in safe microVMs.
*   **Database Queries:** Reading and updating databases (SQL, MongoDB).
*   **API Requests:** Querying REST/GraphQL endpoints for third-party platforms.
*   **Email / Slack / SMS:** Sending messages or notifications to users.
*   **File System Access:** Creating, reading, editing, and deleting local or cloud-stored files.

---

## 5. Agent Memory

| Topic | Resource |
|---|---|
| Short-term vs. long-term memory, architecture patterns | [IBM — What Is AI Agent Memory?](https://www.ibm.com/think/topics/ai-agent-memory) |
| Building agents with short & long-term memory (production patterns) | [Redis Engineering Blog](https://redis.io/blog/build-smarter-ai-agents-manage-short-term-and-long-term-memory-with-redis/) |
| Episodic, semantic, procedural memory (cognitive-science framing) | [Beyond Short-term Memory: 3 Types of Long-term Memory AI Agents Need — MachineLearningMastery.com](https://machinelearningmastery.com/beyond-short-term-memory-the-3-types-of-long-term-memory-ai-agents-need/) |
| How real frameworks implement memory (CrewAI, LangMem, Mem0, Zep, Letta compared) | [AI Agent Memory Architectures — Zylos Research](https://zylos.ai/research/2026-04-05-ai-agent-memory-architectures-persistent-knowledge/) |
| Memory vs. plain vector DB — when you need more than similarity search | [Agentic AI Memory vs Vector Database — Atlan](https://atlan.com/know/agentic-ai-memory-vs-vector-database/) |

### Episodic vs. Semantic Memory
*   **Episodic Memory:** Storing sequential histories of conversation sessions or specific user interactions (remembering "what happened and when").
*   **Semantic Memory:** Extracting and storing factual facts, rules, and world knowledge (remembering "user preferences, user profile details, or domain facts").

### Maintaining Memory & Vector Databases
Memory state overflows context windows quickly. Managing it requires:
*   **RAG and Vector Databases:** Similarity search retrieves relevant facts based on similarity queries.
*   **Summarization / Compression:** Periodically summarizing older conversation chunks to compress dialogue histories.
*   **Forgetting & Aging Strategies:** Deleting stale, unused, or superseded information based on priority/time decay.
*   **User Profile Storage:** Storing structural, profile-based configurations of a user's habits and interests.

### Official Memory Framework Documentation
| Framework | Purpose | Docs |
|---|---|---|
| **Letta** (MemGPT) | Stateful agent orchestration, long-term memory management, and agent-as-a-service | [letta.readme.io](https://letta.readme.io/) |
| **Mem0** | Personalized, self-improving memory layer for AI applications | [docs.mem0.ai](https://docs.mem0.ai/) |
| **Zep** | Fast, production-grade memory store for LLM apps (session, semantic, user memory) | [docs.getzep.com](https://docs.getzep.com/) |

---

## 6. Agent Architectures

### Anthropic's Core Agentic Workflows
Anthropic's seminal guide, *Building Effective Agents*, categorizes agent architectures into 5 key design patterns (workflows). You should learn these to choose the right complexity for your task:

*   **Workflows** (Prescribed, step-by-step paths):
    *   **Prompt Chaining:** Decomposing a complex task into a sequential chain of steps, where each step's output is processed by the next.
    *   **Routing:** Classifying an input and sending it to a specialized downstream LLM/prompt template (e.g., separating support queries into refund requests vs. technical issues).
    *   **Parallelization:** Running multiple LLMs in parallel (either doing the same task for voting/self-consistency, or different sub-tasks) and aggregating their output.
*   **Agents** (Dynamic, self-directed paths):
    *   **Orchestrator-Workers:** A central coordinator agent analyzes a problem, dynamically delegates tasks to worker agents, and aggregates their results.
    *   **Evaluator-Optimizer:** A generator agent creates draft content, and an evaluator agent checks it against a rubric, returning feedback to the generator in a loop.

*Resources:*
- [Anthropic — Building Effective Agents (Workflows & Patterns)](https://www.anthropic.com/engineering/building-effective-agents) — The definitive reference guide.
- [Visual Guide to Agentic Workflows — LangChain Blog](https://blog.langchain.dev/) — Interactive/visual representations of these 5 patterns.

### ReAct (Reason + Act)
- **Original paper (primary source):** [react-lm.github.io](https://react-lm.github.io/) — Yao et al., 2023
- **Best explainer:** [ReAct Prompting — promptingguide.ai](https://www.promptingguide.ai/techniques/react)
- **Deep dive w/ code:** [ReAct Prompting Guide 2026 — explainx.ai](https://explainx.ai/blog/react-prompting-reasoning-acting-agents-guide-2026)
- **Video/Q&A breakdown:** [Keys To Understanding ReAct — Arize AI blog](https://arize.com/blog/keys-to-understanding-react/)

### Chain of Thought (CoT)
- [Chain-of-Thought — promptingguide.ai](https://www.promptingguide.ai/techniques/cot) (based on Wei et al. 2022)

### Tree of Thoughts (ToT) & Graph of Thoughts
- [Every AI Agent Architecture in One Place — Towards AI (Medium)](https://pub.towardsai.net/every-ai-agent-architecture-in-one-place-595ba68d49cd) — best single overview of ToT, GoT, ReWOO, LLMCompiler side-by-side
- [Navigating Modern LLM Agent Architectures — Wollen Labs](https://www.wollenlabs.com/blog-posts/navigating-modern-llm-agent-architectures-multi-agents-plan-and-execute-rewoo-tree-of-thoughts-and-react) — how ToT, LATS, ReAct, and plan-and-execute relate

### Planner–Executor & DAG agents
- [AI Agent Planning: ReAct, Tree of Thoughts, and Plan-and-Execute — OpenLegion](https://www.openlegion.ai/en/learn/ai-agent-planning)
- [Separating AI Agents into Planner and Executor — Medium (paper walkthrough: LLMCompiler, ADaPT)](https://medium.com/@jaouadi.mahdi1/separating-ai-agents-into-planner-and-executor-7705b58d79fd)
- [What are Plan and Execute Agents? — PromptLayer Glossary](https://www.promptlayer.com/glossary/plan-and-execute-agents/)
- [Agentic AI Architecture: 5 Patterns Explained — Redis Blog](https://redis.io/blog/agentic-ai-architecture-examples/) (covers DAG plan-and-execute clearly)

### RAG Agents (agents grounded in retrieval)
- Combine [§1 RAG basics](#1-llm-fundamentals) with tool-calling (§4) — an agent that treats "search my knowledge base" as one of its callable tools rather than a fixed pipeline step.
- [LlamaIndex Agents docs](https://docs.llamaindex.ai) — the framework built specifically around this pattern.

### Graph Engineering (From Loops to Graphs)
As agent systems scale, a single agent loop often fails. Graph Engineering organizes multiple loops, tools, and human-in-the-loop check gates into a structured network (graph) of nodes and edges.

- **Foundational Guide:** [LangChain — The Art of Loop & Graph Engineering](https://blog.langchain.dev/) (Detailed look at representing agent behavior as graphs to bring reliability to non-deterministic LLMs)
- **Deep Dive:** [Eigent AI — Graph Engineering for AI Agents: Beyond Single Feedback Loops](https://www.eigent.ai/)
- **Comparative Study:** [Analytics Vidhya — Graph Engineering for AI Agents: Beyond the Single-Agent Loop](https://www.analyticsvidhya.com/)

---

## 7. Model Context Protocol (MCP)

Model Context Protocol is an open standard that enables developers to build secure, bidirectional connections between AI models and their data sources/tools.

### Core MCP Components
*   **MCP Hosts:** Orchestrator clients (e.g., Claude Desktop, Cursor) that initiate connection and direct models.
*   **MCP Client:** Software library components within hosts that initiate and handle communication protocols.
*   **MCP Servers:** Lightweight services exposing resources, prompts, or tools via the MCP protocol.

### Deployment & Creation
*   **Local Desktop:** Running MCP servers directly on local machine ports or stdio connections.
*   **Remote / Cloud:** Deploying secure MCP servers behind auth protocols for centralized enterprise tools.

| Resource | Link |
|---|---|
| Official MCP docs | [modelcontextprotocol.io/docs](https://modelcontextprotocol.io/docs/getting-started/intro) |
| Official specification | [modelcontextprotocol.io/specification](https://modelcontextprotocol.io/specification/2025-06-18) |
| MCP servers registry (reference + community servers) | [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) |
| Python SDK docs | [py.sdk.modelcontextprotocol.io](https://py.sdk.modelcontextprotocol.io/) |
| TypeScript SDK | [github.com/modelcontextprotocol/typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) |
| MCP Hosts / Clients / Servers, explained plainly | [Anthropic — Building Effective Agents (MCP section)](https://www.anthropic.com/engineering/building-effective-agents) |

---

## 8. Building Agents

### A. Manual (from scratch) — direct API calls
- Implementing the raw agent loop yourself teaches you the most. Start from [OpenAI Function Calling docs](https://platform.openai.com/docs/guides/function-calling) or [Anthropic Tool Use docs](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview) and hand-write the loop: call model → parse tool call → execute → feed result back → repeat.
- [LLM Function Calling and Tool Use Guide 2026 — RockB](https://baeseokjae.github.io/posts/llm-function-calling-tool-use-guide-2026/) walks through the loop for all three major providers with working code.

### LLM Native Function Calling
Most major model providers offer native endpoints built specifically for structure definitions and execution parsing.

| Provider / SDK | Documentation |
|---|---|
| **Anthropic Tool Use (Claude)** | [docs.anthropic.com/en/docs/build-with-claude/tool-use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use) |
| **OpenAI Function Calling** | [platform.openai.com/docs/guides/function-calling](https://platform.openai.com/docs/guides/function-calling) |
| **OpenAI Assistants API** | [platform.openai.com/docs/assistants/overview](https://platform.openai.com/docs/assistants/overview) |
| **Gemini Function Calling** | [ai.google.dev/gemini-api/docs/function-calling](https://ai.google.dev/gemini-api/docs/function-calling) |

### B. Vendor-native SDKs
| SDK | Docs |
|---|---|
| **Claude Agent SDK** (Anthropic) | [platform.claude.com/docs/en/agent-sdk/overview](https://platform.claude.com/docs/en/agent-sdk/overview) |
| **OpenAI Agents SDK** | [developers.openai.com/api/docs/guides/agents](https://developers.openai.com/api/docs/guides/agents) |
| **Google Agent Development Kit (ADK)** | [google.github.io/adk-docs](https://google.github.io/adk-docs/) |

### C. Cross-provider frameworks
| Framework | Best for | Docs |
|---|---|---|
| **LangGraph** | Stateful, graph/cyclical control flow, most control | [docs.langchain.com](https://docs.langchain.com/oss/python/concepts/products) |
| **LangChain** | General LLM app framework, simpler abstraction | [docs.langchain.com](https://docs.langchain.com) |
| **CrewAI** | Role-based multi-agent "crews" | [docs.crewai.com](https://docs.crewai.com) |
| **LlamaIndex Agents** | RAG-first, grounded in your own data | [docs.llamaindex.ai](https://docs.llamaindex.ai) |
| **Microsoft AutoGen / Agent Framework** | Conversational multi-agent, Azure integration | [microsoft.github.io/autogen](https://microsoft.github.io/autogen/) |
| **Hugging Face smolagents** | Lightweight "code agents" (LLM writes/executes code) | [huggingface.co/docs/smolagents](https://huggingface.co/docs/smolagents/index) |
| **Haystack** | Search/RAG-first pipelines with agent support | [haystack.deepset.ai/overview](https://haystack.deepset.ai/overview/quick-start) |

**Comparative reading** (Medium/blog, useful for picking a framework):
- [A Detailed Comparison of Top 6 AI Agent Frameworks in 2026 — Turing](https://www.turing.com/resources/ai-agent-frameworks)
- [AI Agent Frameworks Compared: LangChain vs CrewAI vs LlamaIndex — getaibook.com](https://getaibook.com/blog/ai-agent-frameworks-compared/)
- [Comparative Study: LangGraph vs LlamaIndex vs CrewAI with IBM Watsonx.ai — Medium](https://medium.com/@ashgadag/comparative-study-langgraph-vs-llamaindex-vs-crewai-agents-with-ibm-watsonx-ai-c01ceb14ea45)

---

## 9. Evaluation & Testing

Unlike standard software, agent evaluation requires testing non-deterministic outputs and tool execution correctness across several layers:

### Testing Layers
*   **Unit Testing for Individual Tools:** Ensuring helper functions, parser formats, and individual API calls return exact schemas.
*   **Integration Testing for Flows:** Verifying the full multi-turn execution chain (Agent -> Tool -> Model -> Refinement -> Final Output).
*   **Human-in-the-Loop (HITL) Evaluation:** Gatekeeping critical agent actions (like sending emails or triggering payments) using human approval loops and grading agent logs.

### Metrics to Track
*   **Hallucination Rate:** Ensuring generated statements match retrieved context.
*   **Semantic Similarity / Accuracy:** Scoring final agent outputs against ground truth responses.
*   **Success Rate / Goal Completion:** Measuring how frequently the agent completes user tasks.
*   **Cost & Latency:** Monitoring token consumption and time to complete execution loops.

| Tool / Framework | Best for | Docs |
|---|---|---|
| **LangSmith** | Tracing + evals + experiment tracking, best if using LangChain/LangGraph | [docs.langchain.com/langsmith](https://docs.langchain.com) |
| **Ragas** | RAG-specific metrics (faithfulness, relevancy, retrieval precision) | [docs.ragas.io](https://docs.ragas.io) |
| **DeepEval** | pytest-style unit testing for LLM apps, CI/CD friendly | [docs.confident-ai.com](https://docs.confident-ai.com) |
| **Promptfoo** | Red-teaming / adversarial testing, OWASP LLM Top 10 test suites | [promptfoo.dev/docs](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/) |

**Comparative reading:**
- [DeepEval vs. RAGAS vs. LangSmith — Descope](https://www.descope.com/blog/post/deepeval-vs-ragas-vs-langsmith) — clearest breakdown of when to use which
- [DeepEval vs RAGAS (2026) — genai.qa](https://genai.qa/blog/deepeval-vs-ragas/)

---

## 10. Debugging, Monitoring & Observability

Observability tracks non-deterministic execution graphs, helping you identify failing tool invocations, infinite execution loops, or token bottlenecks.

### Core Concepts
*   **Structured Logging & Tracing:** Recording prompt templates, raw inputs/outputs, model parameters, and sub-call latencies at every node.
*   **Inner vs. Outer Loop Tracing:** Tracking the low-level tool invocation logs (inner loop) separately from the high-level user session flow (outer loop).

| Tool | Best for | Docs |
|---|---|---|
| **LangFuse** | Open-source, self-hostable, tracing + prompt mgmt + evals in one | [langfuse.com/docs](https://langfuse.com/docs) |
| **Helicone** | Drop-in proxy — add observability with a one-line base-URL change | [docs.helicone.ai](https://docs.helicone.ai) |
| **Arize Phoenix** | ML-grade evaluation rigor, strong for RAG debugging | [docs.arize.com/phoenix](https://docs.arize.com/phoenix) |
| **OpenLLMetry / OpenTelemetry GenAI conventions** | Vendor-neutral standard tracing spec for LLM calls | [opentelemetry.io GenAI semantic conventions](https://opentelemetry.io/docs/specs/semconv/gen-ai/) |

**Comparative reading:**
- [8 LLM Observability Tools to Monitor & Eval AI Agents — LangChain resource hub](https://www.langchain.com/resources/llm-observability-tools)
- [Agent Observability: LangSmith, Langfuse, Arize 2026 — Digital Applied](https://www.digitalapplied.com/blog/agent-observability-platforms-langsmith-langfuse-arize-2026)

---

## 11. Security & Ethics

| Topic | Resource |
|---|---|
| **The canonical reference** | [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) — prompt injection is risk #1, updated yearly by the OWASP GenAI project |
| Practitioner's implementation guide to the OWASP list | [OWASP Top 10 for LLMs: A Practitioner's Guide — Improving](https://www.improving.com/thoughts/owasp-top-10-llm-security-guide/) |
| What changed in the 2025 OWASP list & why (RAG poisoning, excessive agency) | [OWASP Top 10 for LLM Applications (2025) — Aembit](https://aembit.io/blog/owasp-top-10-llm-risks-explained/) |
| Prompt injection & red-teaming test automation | [Promptfoo — OWASP LLM Top 10 red-team docs](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/) |
| Tool sandboxing / least-privilege for planner-executor agents | [Architecting Resilient LLM Agents: Secure Plan-Execute — arXiv](https://arxiv.org/pdf/2509.08646) |
| OWASP Top 10 **for Agentic Applications** (goal hijacking, tool misuse, memory poisoning — the agent-specific follow-up to the LLM list) | Referenced in [Cisco Integrated AI Security Framework Report](https://arxiv.org/pdf/2512.12921) |

### Secure Code Execution Sandboxes
When an agent is allowed to execute arbitrary code (e.g., Python scripts it generates to solve math/data problems), it **must** run in a secure, isolated sandbox to prevent host system compromise.

| Sandbox Provider | Description | Docs |
|---|---|---|
| **E2B Sandbox** | Secure sandboxes (microVMs) for running AI-generated code and agent tools | [e2b.dev/docs](https://e2b.dev/docs) |
| **Docker** | Running local Docker containers with CPU/memory limits for safe local execution | [docs.docker.com](https://docs.docker.com/) |
| **Fly.io Machines** | MicroVMs for serverless agent executions on demand | [fly.io/docs/machines](https://fly.io/docs/machines/) |

### Data Privacy & PII Redaction
Agents often ingest private user logs or emails. Redacting Personally Identifiable Information (PII) before forwarding inputs to LLM APIs is crucial.
*   **Microsoft Presidio:** [microsoft.github.io/presidio](https://microsoft.github.io/presidio/) — The standard open-source library for scanning and redacting sensitive text.

### Bias, Toxicity & Safety Guardrails
Enforcing boundary layers on agent inputs and outputs prevents toxic generation or prompt injection bypasses.
*   **NVIDIA NeMo Guardrails:** [docs.nvidia.com/nemo/guardrails](https://docs.nvidia.com/nemo/guardrails/) — Programmable guardrails for LLM conversational safety.
*   **Llama Guard:** [huggingface.co/meta-llama/Llama-Guard-3](https://huggingface.co/meta-llama/Llama-Guard-3) — Fine-tuned models for input-output moderation.

---

## 12. Free Structured Courses

| Course | Level | Link |
|---|---|---|
| **Hugging Face Agents Course** | Beginner → Advanced, free certificate | [hf.co/learn/agents-course](https://huggingface.co/learn/agents-course) ([GitHub](https://github.com/huggingface/agents-course)) |
| DeepLearning.AI — Building Code Agents with smolagents | Intermediate | [deeplearning.ai/courses/building-code-agents-with-hugging-face-smolagents](https://www.deeplearning.ai/courses/building-code-agents-with-hugging-face-smolagents) |
| DeepLearning.AI — AI Agents in LangGraph | Intermediate | [deeplearning.ai/short-courses/ai-agents-in-langgraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/) |
| Anthropic Academy | Beginner → Advanced | [anthropic.com/learn](https://www.anthropic.com/learn) |
| dair-ai Prompt Engineering Guide course track | Beginner | [promptingguide.ai](https://www.promptingguide.ai/) |

---

## 13. Communities (Reddit, Discord, Forums)

Not just docs — these are where people actually debug real agent problems in public.

| Community | Best for |
|---|---|
| [r/AI_Agents](https://reddit.com/r/AI_Agents) | The dedicated agent-building subreddit — build logs, architecture questions, post-mortems |
| [r/LangChain](https://reddit.com/r/LangChain) | LangChain/LangGraph-specific dev discussion |
| [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA) | Local/open-weight model agents, hardware, quantization — most rigorous benchmarking culture on Reddit |
| [r/ClaudeAI](https://reddit.com/r/ClaudeAI) | Claude Code / Claude Agent SDK workflows, CLAUDE.md patterns, subagents |
| [r/AutoGenAI](https://reddit.com/r/AutoGenAI) | Multi-agent orchestration, AutoGen-specific |
| [r/MachineLearning](https://reddit.com/r/MachineLearning) | Research-level discussion, paper drops (ReAct, ToT, etc. get discussed here first) |
| [r/PromptEngineering](https://reddit.com/r/PromptEngineering) | Prompting technique discussion |
| Hugging Face Discord | Official support channel for the Agents Course |
| MCP Contributors Discord | For MCP server/client dev questions (linked from the [python-sdk repo](https://github.com/modelcontextprotocol/python-sdk)) |

---

## 14. Suggested Study Path

1. **Prerequisites** (§0) — skip if you already code.
2. **LLM Fundamentals** (§1) — tokens, context windows, embeddings/RAG basics. Don't skip this even if you've used ChatGPT a lot; it explains *why* agents fail (context overflow, lost-in-the-middle, retrieval quality).
3. **Prompt Engineering** (§2) — go through promptingguide.ai's zero-shot → CoT → ReAct sequence.
4. **AI Agents 101 + Tools** (§3–4) — read Anthropic's "Building Effective Agents" fully, then read one provider's function-calling docs end to end.
5. **Memory + Architectures** (§5–6) — understand ReAct deeply (it's the base pattern almost everything else builds on), then skim planner-executor/ToT so you recognize them.
6. **MCP** (§7) — understand it conceptually even before you build anything with it; it's becoming the standard tool-connection layer.
7. **Pick ONE framework** (§8) and build a real agent — don't survey all of them, that's a trap. Vendor SDK if you're committed to one model provider, LangGraph/CrewAI if you want portability.
8. **Eval + Observability** (§9–10) — add this as soon as your agent does anything beyond a demo. Most tutorials skip this; most production failures happen here.
9. **Security** (§11) — read the OWASP LLM Top 10 once, seriously, before you give any agent real tool access (email, file system, payments, etc.).
10. **Join a community** (§13) and start reading real build threads — this is where you learn what actually breaks in production that no doc mentions.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) to learn how to propose updates, fix links, or add new curated resource recommendations.

---
*Compiled August 2026 from official docs, Medium, Reddit, GeeksforGeeks, IBM/AWS/Google/Redis engineering blogs, dair-ai, arXiv, and OWASP. Frameworks and doc URLs in this space change often — most projects publish an `llms.txt` machine-readable index (e.g. `modelcontextprotocol.io/llms.txt`) if a link here goes stale.*

**License:** MIT License. Feel free to fork, edit, and redistribute this file — it's meant to be shared.
