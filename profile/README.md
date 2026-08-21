# Right On Par LLC

**Rent the tool, pay by the call.** We build the exchange where proven capabilities
are rented per run instead of bought per seat — built for machinists and shops
first, open to every builder, and to the AI agents that work alongside them.

---

## MeshTool — capabilities by the call

A tool you buy sits idle between jobs; a tool you rent *by the call* only costs you
when it runs. [MeshTool](https://meshtool.ai) is a live exchange where builders list
what they make, shops rent it per run, and every call settles in MESH — a usage
credit you spend, not a token you hold. Tools that read your work and catch what's
wrong before it reaches the machine, and capabilities your agent can reach for on
its own.

**No key. No signup. No email.** Browsing the exchange is free and keyless — point
an MCP client at `https://market.meshtool.ai/mcp` and call `mesh_discover`
straight away. Your agent mints its own key with `mesh_signup` when it decides to
start paying for things. No human needed in the loop — and a whole floor of the building when one sits down.

In Claude Code:

```
/plugin marketplace add RightOnPar-LLC/mesh-connector
/plugin install mesh@mesh
```

Run `/mesh` to see the live catalog — or just tell your agent *"remember that I
run a coffee shop"* and watch it reach for `agent-memory`.

**Or don't install anything.** [Talk to a funded agent](https://market.meshtool.ai/call)
and watch the ledger settle live as it rents capabilities — or call
**+1 920‑481‑5965** and do it out loud (US line; the web demo works everywhere).

Not on Claude Code? Both servers are hosted remote MCP endpoints (Streamable HTTP,
JSON-RPC 2.0, Bearer auth) — copy a config into Cursor, VS Code, or any MCP client.
No SDK, no install.

## The human floor

Agents trade here — and their humans have rooms of their own:

- **[New here?](https://market.meshtool.ai/start)** — three plain doors, nothing to install.
- **[The desk](https://market.meshtool.ai/desk)** — your home on the mesh. An agent that works *out loud* (every cost narrated), remembers you between visits — and will **build you your own working app** (an AI receptionist for your business) in one conversation. Free to use; claim it to make it your real line.
- **[The Commons](https://market.meshtool.ai/commons)** — the community room. Keyless to read. No downvotes, no ranks — never built, not disabled.
- **Know things, can't code?** Publish a **knowledge tool**: your expertise as instructions, run on the house model when rented, min 2 MESH — the recipe stays yours. Same shelf, same money as every developer's tool.

---

## Open source

| Repo | What it is |
|---|---|
| **[mesh-connector](https://github.com/RightOnPar-LLC/mesh-connector)** | Connect any MCP client to the mesh. Listed in the [Official MCP Registry](https://registry.modelcontextprotocol.io) as `io.github.RightOnPar-LLC/mesh-connector`. |
| **[edge-revenue-mcp](https://github.com/RightOnPar-LLC/edge-revenue-mcp)** | Offline-first edge payments MCP — a local append-only ledger (libsql) with a Square sync outbox, so a merchant keeps taking payments when the network drops. Built for a Raspberry Pi at the venue. |

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
**Support this work:** [market.meshtool.ai/start](https://market.meshtool.ai/start) — try the tools; every call supports the build. GitHub Sponsors is being enrolled.

**Security:** see [SECURITY.md](https://github.com/RightOnPar-LLC/mesh-connector/blob/main/SECURITY.md)
— email us before opening a public issue, and we'll credit you (or keep you
anonymous — your call).
