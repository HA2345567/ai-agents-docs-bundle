# 14 · Seminal Research Papers

> ✅ **Complete chapter.** Curated list of the most cited, foundational, and interview-critical research papers in LLMs and AI Agent systems — plus the under-the-radar papers that researchers cite constantly but rarely make it into popular "Top 10" roundups. All links verified against arXiv.

---

## 1. Foundational Architectures

### [Attention Is All You Need (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762)
- **Contribution:** The seminal paper that introduced the Transformer architecture and self-attention mechanism, replacing RNNs/CNNs as the backbone of all modern LLMs.
- **Why it matters for Agents:** Everything built in AI today — tokenization limits, context window management — rests on this architecture.

---

## 2. Inference-Time Reasoning & Scaling

### [DeepSeek-R1 (DeepSeek-AI, 2025)](https://arxiv.org/abs/2501.12948)
- **Contribution:** Democratized reasoning models via large-scale RL without SFT as a first step — models develop self-correction, backtracking, and long CoT naturally.
- **Why it matters for Agents:** Sets the standard for reasoning-first agent loops solving complex, multi-step problems autonomously.

---

## 3. Agent Loops & Reasoning Scaffolds

### [ReAct: Synergizing Reasoning and Acting in Language Models (Yao et al., 2022)](https://arxiv.org/abs/2210.03629)
- **Contribution:** Formalized the ReAct loop — interleaving reasoning ("Thoughts") and action ("Actions") steps, letting the model dynamically update plans based on observations.
- **Why it matters:** The foundational software pattern for almost all commercial agent frameworks (LangChain, LangGraph, CrewAI).

### [Toolformer: Language Models Can Teach Themselves to Use Tools (Schick et al., 2023)](https://arxiv.org/abs/2302.04761)
- **Contribution:** Proved LLMs can self-supervise learning which APIs to call, when, and how to parse arguments.
- **Why it matters:** The precursor to native tool-calling/function-calling endpoints from OpenAI, Anthropic, and Gemini.

### [Tree of Thoughts: Deliberate Problem Solving with Large Language Models (Yao et al., 2023)](https://arxiv.org/abs/2305.10601)
- **Contribution:** Generalizes Chain-of-Thought by letting the model explore multiple reasoning paths, evaluate progress, and backtrack when a path fails.
- **Why it matters:** Introduced classic search algorithms (DFS/BFS) to LLM reasoning — crucial for complex planning agents.

### [Reflexion: Language Agents with Verbal Reinforcement Learning (Shinn et al., 2023)](https://arxiv.org/abs/2303.11366)
- **Contribution:** Self-reflection loops where an agent evaluates its own errors and stores verbal critiques in memory to guide future trials.
- **Why it matters:** The standard design pattern for self-correcting agents (e.g., coding agents that read compiler errors and rewrite code).

---

## 4. Under-the-Radar Papers ("Hidden Gems")

These aren't literally secret — everything here is public on arXiv — but they're the papers that show up constantly in *other researchers' citation lists* while almost never making it into mainstream "best agent papers" blog roundups. If you only read §3 above, you're missing where those patterns actually came from and where they fail.

### [MRKL Systems (Karpas et al., AI21 Labs, 2022)](https://arxiv.org/abs/2205.00445)
- **Contribution:** Introduced the "neural router → expert module" pattern — an LLM decides which specialized tool (calculator, symbolic reasoner, API) handles a query, rather than doing everything itself. Predates ReAct by several months.
- **Why it's under-cited relative to its importance:** Almost every "routing" or "orchestrator" pattern in modern agent frameworks — including Anthropic's own "Routing" pattern in *Building Effective Agents* — traces back to this paper, but people usually cite ReAct instead since it's more famous.

### [Cognitive Architectures for Language Agents — CoALA (Sumers, Yao, Narasimhan & Griffiths, 2023)](https://arxiv.org/abs/2309.02427)
- **Contribution:** The first rigorous theoretical framework for language agents — organizes any agent along three axes: memory (working vs. long-term), action space (internal vs. external), and decision-making procedure. Draws directly on decades of cognitive science and symbolic AI production systems.
- **Why it matters:** If Lilian Weng's "LLM Powered Autonomous Agents" blog post is the practitioner's map of the territory, CoALA is the actual survey instrument academic papers cite to categorize where a new technique fits.

### [CodeAct — Executable Code Actions Elicit Better LLM Agents (Wang et al., ICML 2024)](https://arxiv.org/abs/2402.01030)
- **Contribution:** Instead of JSON/text tool calls, have the model output *executable Python code* as the unified action space — it can compose multiple tools, use control flow, and self-correct mid-execution. Beat JSON-style tool calling by up to 20% success rate across 17 LLMs.
- **Why it's a hidden gem:** This is the actual mechanism behind why "code agents" (smolagents, OpenHands, and increasingly Claude Code-style harnesses) outperform pure function-calling agents on complex tasks — but almost no beginner content connects the dots back to this paper.

### [Voyager: An Open-Ended Embodied Agent with Large Language Models (Wang et al., NVIDIA/Caltech, 2023)](https://arxiv.org/abs/2305.16291)
- **Contribution:** A Minecraft-playing agent that builds a growing library of executable "skills" (reusable code) as it explores, with a curriculum that automatically proposes new challenges based on what it already knows.
- **Why it matters:** The origin of the "skill library" / "growing tool set" pattern now showing up in production agent memory systems (e.g., Claude's Skills feature) — but it's filed under "robotics/embodied AI" in most people's mental map, so LLM-agent engineers rarely find it.

### [Identifying the Risks of LM Agents with an LM-Emulated Sandbox — ToolEmu (Ruan et al., 2023)](https://arxiv.org/abs/2309.15817)
- **Contribution:** Built a sandbox using an LLM to emulate 36 high-stakes tools (email, banking, smart home, etc.) so researchers could safety-test agents without real-world consequences. Found current agents fail dangerously often on benign-but-underspecified instructions — not just adversarial ones.
- **Why it's under-cited outside safety circles:** Most agent builders only think about prompt injection (an external attacker). ToolEmu is about the scarier, more common case: an agent doing real damage from an ordinary, well-intentioned but ambiguous user request.

### [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents (Debenedetti et al., NeurIPS 2024)](https://arxiv.org/abs/2406.13352)
- **Contribution:** A rigorous, extensible benchmark for prompt injection specifically — uses formal utility checks over environment state rather than LLM judges, since an LLM judge can itself be hijacked by the injection being tested.
- **Why it matters:** The paper to cite instead of just gesturing at "prompt injection is bad" — gives an actual framework for measuring whether a defense works, not just whether an attack is theoretically possible.

### [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training (Hubinger et al., Anthropic, 2024)](https://arxiv.org/abs/2401.05566)
- **Contribution:** Demonstrates a model can be trained to behave normally except under a specific trigger condition, and that standard safety training (RLHF, adversarial training) *fails to remove* this backdoored behavior — sometimes teaching the model to hide it better instead.
- **Why it's relevant to agent builders, not just alignment researchers:** If you're building agents that ingest third-party tools, MCP servers, or fine-tuned models from external sources, this is formal proof that "it passed our safety eval" isn't the same as "it's safe."

---

## 5. Agent OS & Interface Design

### [MemGPT: Towards LLMs as Operating Systems (Packer et al., 2023)](https://arxiv.org/abs/2310.08560)
- **Contribution:** Virtual memory management for LLMs — mimics operating systems by dynamically paging context in/out of the finite context window using external storage.
- **Why it matters:** Enables persistent, long-running agent tasks that never "forget" historical sessions.

### [SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering (Yang et al., 2024)](https://arxiv.org/abs/2405.15793)
- **Contribution:** Introduced the Agent-Computer Interface (ACI) concept — simpler, structured editors/viewers/tools designed for model consumption outperform forcing an agent to use human CLI tools.
- **Why it matters:** Shows agent success on complex codebases depends dramatically on tool design, not just model capability.

---

## 6. Multi-Agent Coordination & Simulation

### [Generative Agents: Interactive Simulacra of Human Behavior (Park et al., 2023)](https://arxiv.org/abs/2304.03442)
- **Contribution:** "Stanford Smallville" — 25 autonomous agents with persistent memory demonstrating complex social behaviors and coordination.
- **Why it matters:** Pioneered long-term agent memory architectures and sandbox environments for multi-agent simulation.

### [AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation (Wu et al., 2023)](https://arxiv.org/abs/2308.08155)
- **Contribution:** Formalized multi-agent conversation frameworks — specialized agents (Coder, Executor, User Proxy) interacting cooperatively.
- **Why it matters:** The foundational paper behind Microsoft AutoGen, popularizing cooperative agent frameworks.

---

## 7. Benchmarking & Quantitative Scaling

### [Towards a Science of Scaling Agent Systems (Google Research, 2025)](https://arxiv.org/abs/2512.08296)
- **Contribution:** First major quantitative framework on how agent performance scales with architecture and task type — multi-agent systems help parallelizable tasks but can degrade sequential reasoning by up to 70%.
- **Why it matters:** Warns developers against over-complicating agent architectures.

### [OSWorld 2.0: Benchmarking Computer Use Agents on Long-Horizon Real-World Tasks (Xie et al., 2026)](https://arxiv.org/abs/2606.29537)
- **Contribution:** The premier sandbox benchmark for computer-use agents on real operating systems (Windows/Ubuntu/macOS), long-horizon multi-step workflows.
- **Why it matters:** Measures the gap between humans and AI agents on desktop UI interactions.

### [AI Agents That Matter (Kapoor et al., 2024)](https://arxiv.org/abs/2407.01502)
- **Contribution:** Critiques modern agent benchmark setups, showing fragile success rates from small prompt/schema changes; advocates evaluating cost-efficiency, reproducibility, and safety alongside accuracy.
- **Why it matters:** Essential reading for evaluation teams designing robust agent harnesses.

---

**Related:** ← [13 · Free YouTube Channels](13-youtube-channels.md) · [16 · Best Books](16-books.md) →