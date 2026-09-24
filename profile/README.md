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

No key is needed to browse. When an agent needs to make a paid call, it can get
its own key with `mesh_signup`.

---

## Other public work

- **[hideout](https://github.com/RightOnPar-LLC/hideout)**: a read-only Windows
  scanner that finds where malware hides.

## Security and contact

- General and support: [support@meshtool.ai](mailto:support@meshtool.ai)
- Security: please report vulnerabilities privately to
  [support@meshtool.ai](mailto:support@meshtool.ai) before opening a public
  issue. See the
  [security policy](https://github.com/RightOnPar-LLC/meshmarket-mcp/blob/main/SECURITY.md).
  We acknowledge reports and credit reporters who want it.
