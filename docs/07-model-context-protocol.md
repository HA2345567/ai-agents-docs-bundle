# 07 · Model Context Protocol (MCP)

> 🟡 **Stub chapter.** Links are curated and accurate; full 14-point treatment pending. PRs welcome.

## Plain-language explanation (brief)
MCP is an open standard (originally from Anthropic, now broadly adopted) for connecting agents to tools and data sources in a consistent, reusable way — instead of writing custom tool-integration code per framework, you write one MCP server and any MCP-compatible host (Claude, IDEs, other agent frameworks) can use it.

## Core MCP Components
*   **MCP Hosts:** Orchestrator clients (e.g., Claude Desktop, Cursor) that initiate connection and direct models.
*   **MCP Client:** Software library components within hosts that initiate and handle communication protocols.
*   **MCP Servers:** Lightweight services exposing resources, prompts, or tools via the MCP protocol.

## Deployment & Creation
*   **Local Desktop:** Running MCP servers directly on local machine ports or stdio connections.
*   **Remote / Cloud:** Deploying secure MCP servers behind auth protocols for centralized enterprise tools.

## Official documentation
- [MCP Docs](https://modelcontextprotocol.io/docs/getting-started/intro)
- [MCP Specification](https://modelcontextprotocol.io/specification/2025-06-18)
- [MCP Servers Registry](https://github.com/modelcontextprotocol/servers)
- [Python SDK](https://py.sdk.modelcontextprotocol.io/)
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [MCP Hosts / Clients / Servers, explained plainly](https://www.anthropic.com/engineering/building-effective-agents) — Anthropic Building Effective Agents MCP section

## Related concepts
- [04 · Tools & Function Calling](04-tools-function-calling.md) — MCP standardizes tool exposure, doesn't replace the underlying function-calling mechanism
- [11 · Security](11-security.md) — MCP servers are a new trust boundary; treat third-party servers with the same scrutiny as any tool integration

**Related:** ← [06 · Agent Architectures](06-agent-architectures.md) · [08 · Building Agents](08-building-agents-frameworks.md) →
