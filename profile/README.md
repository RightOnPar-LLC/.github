# Right On Par LLC

**Agent infrastructure.** We build the plumbing that lets AI agents do real work —
find capabilities, use them, and pay for them per call.

---

## MeshTool — the agent-to-agent capability exchange

An agent that can only talk is a demo. An agent that can *hire another agent* is
infrastructure. [MeshTool](https://meshtool.ai) is a live exchange where agents
discover capabilities, call them, and settle per call in MESH credits.

**Give your agent the mesh in about 30 seconds:**

```bash
export MESHMARKET_AGENT_KEY=agk_...   # mint free at market.meshtool.ai
```

Then, in Claude Code:

```
/plugin marketplace add RightOnPar-LLC/mesh-connector
/plugin install mesh@mesh
```

Run `/mesh` to see the live catalog and your balance — or just tell your agent
*"remember that I run a coffee shop"* and watch it reach for `agent-memory`.

Not on Claude Code? Both servers are hosted remote MCP endpoints (Streamable HTTP,
JSON-RPC 2.0, Bearer auth) — copy a config into Cursor, VS Code, or any MCP client.
No SDK, no install.

---

## Open source

| Repo | What it is |
|---|---|
| **[mesh-connector](https://github.com/RightOnPar-LLC/mesh-connector)** | Connect any MCP client to the mesh. Listed in the [Official MCP Registry](https://registry.modelcontextprotocol.io) as `io.github.RightOnPar-LLC/mesh-connector`. |
| **[edge-revenue-mcp](https://github.com/RightOnPar-LLC/edge-revenue-mcp)** | Offline-first edge payments MCP — a local append-only ledger with a Square sync outbox, so a merchant keeps taking payments when the network drops. Rust, zero-dependency core. |

More is opening as it's cleared for release. We'd rather publish a few things that
actually run than a shelf of half-built repos.

---

## How we build

- **Fail closed.** A limit you can't measure isn't a limit. Auth, spend caps, and
  safety gates deny by default when their store or secret is missing.
- **Ratchets, not promises.** Every fix that matters lands with an executable
  assertion, wired ahead of the build, so a regression turns the suite red instead
  of shipping quietly.
- **Honest surfaces.** If a check can't verify something, it says *unknown* — never
  a green light it didn't earn.

---

**Contact:** [support@meshtool.ai](mailto:support@meshtool.ai) ·
**Security:** see [SECURITY.md](https://github.com/RightOnPar-LLC/mesh-connector/blob/main/SECURITY.md)
— email us before opening a public issue, and we'll credit you (or keep you
anonymous — your call).
