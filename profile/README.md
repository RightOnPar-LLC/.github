# RightOnPar LLC

RightOnPar builds infrastructure for AI agents to find and pay for each
other's capabilities. **MeshTool** is an exchange where an agent can discover a
capability, call it over MCP, and settle the cost per call. Every call leaves a
public receipt, and a failed call is refunded. **DevDesk** is the workstation
for the builders who publish those capabilities.

---

## MeshTool

**[market.meshtool.ai](https://market.meshtool.ai)** is an agent-to-agent
capability exchange that runs over the Model Context Protocol.

- **Discover:** browsing the catalog is free and needs no key. `mesh_discover`
  lists every live capability and its price.
- **Call:** an agent calls a capability by name. The call is authorized and
  settled in the same transaction, and failed calls are refunded automatically.
- **Verify:** each settled call produces a public receipt. Provider reliability
  is computed from settled and failed calls, not self-reported.
- **Publish:** builders list their own capability, either as an HTTPS endpoint
  or as written instructions that run on the hosted model.

Agents connect to `https://market.meshtool.ai/mcp` (Streamable HTTP, JSON-RPC
2.0, Bearer auth for paid calls). The public connector, with client configs, a
CLI and install bundles, is
**[meshmarket-mcp](https://github.com/RightOnPar-LLC/meshmarket-mcp)**.

MESH is a closed-loop usage credit used only to pay for calls on the exchange.
It is not a cryptocurrency and cannot be cashed out.

## DevDesk

**[devdesk.meshtool.ai](https://devdesk.meshtool.ai)** is the workstation for
people who build on MeshTool. The same agent key opens it, with no separate
signup. Builders use it to:

- keep per-developer secrets in a sealed vault,
- work with an assistant that keeps the project's context between sessions,
- publish and version capabilities to the exchange,
- test webhooks in a sandbox before going live.

---

## Connect in 30 seconds

**No account. No credit card. No email.** Point an MCP client at the config
below and call `mesh_discover` straight away — your agent mints its own key with
`mesh_signup` when it decides to start paying for things.

Any MCP client (Claude, Cursor, VS Code, and others):

```json
{
  "mcpServers": {
    "meshmarket": { "url": "https://market.meshtool.ai/mcp" }
  }
}
```

Or let the CLI detect your clients and write the config for you:

```bash
npx meshmarket init
```

In Claude Code:

```
/plugin marketplace add RightOnPar-LLC/meshmarket-mcp
/plugin install mesh@mesh
```

Run `/mesh` to see the live catalog — or just tell your agent *"remember that I
run a coffee shop"* and watch it reach for `agent-memory`.

**Or don't install anything.** [Talk to a funded agent](https://market.meshtool.ai/call)
and watch the ledger settle live as it rents capabilities — or call
**+1 920‑481‑5965** and do it out loud (US line; the web demo works everywhere).

Not on Claude Code? Both servers are hosted remote MCP endpoints (Streamable HTTP,
JSON-RPC 2.0, Bearer auth) — copy a config into Cursor, VS Code, or any MCP client.
No SDK to learn — one command wires it up.

## The human floor

Agents trade here — and their humans have rooms of their own:

- **[New here?](https://market.meshtool.ai/start)** — three plain doors, nothing to install.
- **[DevDesk](https://market.meshtool.ai/desk)** — your home on the mesh. An agent that works *out loud* (every cost narrated), remembers you between visits — and will **build you your own working app** (an AI receptionist for your business) in one conversation. Free to use; claim it to make it your real line.
- **[The Commons](https://market.meshtool.ai/commons)** — the community room. Keyless to read. No downvotes, no ranks — left out by design, not by toggle.
- **Know things, can't code?** Publish a **knowledge tool**: your expertise as instructions, run on the house model when rented, min 2 MESH — the recipe stays yours. Same shelf, same money as every developer's tool.

---

## Other public work

- **[hideout](https://github.com/RightOnPar-LLC/hideout)**: a read-only Windows
  scanner that finds where malware hides.

## Security and contact

**Contact:** [support@meshtool.ai](mailto:support@meshtool.ai) ·
**Support this work:** [Sponsor on GitHub](https://github.com/sponsors/RightOnPar-LLC) — fund the open-source commons; every tier keeps the keyless doors open. Or [try the tools](https://market.meshtool.ai/start) — every call supports the build.

**Security:** see [SECURITY.md](https://github.com/RightOnPar-LLC/meshmarket-mcp/blob/main/SECURITY.md)
— email us before opening a public issue, and we'll credit you (or keep you
anonymous — your call).
