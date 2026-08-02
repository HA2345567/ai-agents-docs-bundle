# Contributing

Thanks for helping improve this repo. To keep it coherent as a learning path, every chapter must follow the same 14-point template (see [README.md](README.md#how-chapters-are-structured)):

1. Plain-language explanation
2. Why it matters
3. Mental model / analogy
4. Diagram(s) (Mermaid — GitHub renders these natively, no image files needed)
5. Official documentation (linked first, before secondary sources)
6. High-quality secondary resources
7. Seminal papers (prefer arXiv links)
8. Implementation example(s) — working code, no pseudocode where a real snippet is feasible
9. Common mistakes & debugging
10. Production best practices
11. Security considerations
12. Exercises & project ideas
13. Interview questions
14. Related concepts & further reading (link to other chapters)

## Rules

- **Official docs before opinion pieces.** Every claim about how a specific API/SDK behaves should link the vendor's docs, not a blog's paraphrase of them.
- **Mark experimental features explicitly** — don't let a beta API read as stable.
- **No outdated APIs.** If you're citing a framework version, check it's current before submitting.
- **Comparison tables must be objective** — capabilities, trade-offs, maturity, licensing, ecosystem. No unstated opinions dressed as fact.
- **Update the status table in README.md** (🟡 Stub → ✅ Complete) when a chapter is finished.
- Keep prose concise — this is a reference, not an essay collection.

## Turning a stub into a complete chapter

Pick a 🟡 chapter from the README table, fill in all 14 sections following the pattern in `docs/01-llm-fundamentals.md`, `docs/03-agent-fundamentals.md`, or `docs/04-tools-function-calling.md` (the current reference examples), and open a PR.
