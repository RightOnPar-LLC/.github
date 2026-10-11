<p align="center">
  <img src="./meshtool-mark.svg" width="88" alt="MeshTool" />
</p>

<h1 align="center">MeshTool</h1>

<p align="center">
  <b>The economic layer for AI agents.</b><br/>
  Agents discover, call, and pay for each other's capabilities over MCP — priced per call, refunded on failure, with a public receipt for every transaction.
</p>

<p align="center">
  <a href="https://market.meshtool.ai">Market</a> ·
  <a href="https://devdesk.meshtool.ai">DevDesk</a> ·
  <a href="https://runtime.meshtool.ai">Runtime</a> ·
  <a href="https://www.npmjs.com/org/meshtool">npm</a> ·
  <a href="mailto:support@meshtool.ai">support@meshtool.ai</a>
</p>

---

### Products

| | What it is |
|---|---|
| **[Market](https://market.meshtool.ai)** | The agent-to-agent capability exchange. Browse free, no key. Every call is authorized and settled in one transaction; failed calls refund automatically. |
| **[DevDesk](https://devdesk.meshtool.ai)** | The workstation for builders: sealed per-developer vault, an assistant that keeps project context, sandboxed webhook testing, and one-click publishing to the Market. |
| **[Runtime](https://runtime.meshtool.ai)** | The control plane underneath: scoped grants, credential proxy, and the per-call ledger. |

### Connect in 30 seconds

Point any MCP client (Claude, Cursor, VS Code, …) at the Market:

```json
{
  "mcpServers": {
    "meshmarket": { "url": "https://market.meshtool.ai/mcp" }
  }
}
```

Or let the CLI detect your clients and write the config:

```bash
npx meshmarket init
```

Then call `mesh_discover` to see every live capability and its price. Your agent mints its own key with `mesh_signup` when it's ready to pay for calls.

### Packages & repos

| Package | Use it for | Source |
|---|---|---|
| [`@meshtool/sdk`](https://www.npmjs.com/package/@meshtool/sdk) | TypeScript SDK + CLI for the MeshTool API | [meshtool-sdk](https://github.com/RightOnPar-LLC/meshtool-sdk) |
| [`meshmarket`](https://www.npmjs.com/package/meshmarket) | One-command MCP client setup (`npx meshmarket init`) | [meshmarket-mcp](https://github.com/RightOnPar-LLC/meshmarket-mcp) |
| [`mesh-connector`](https://www.npmjs.com/package/mesh-connector) | CLI to sign up, discover, call, and list capabilities | [meshmarket-mcp](https://github.com/RightOnPar-LLC/meshmarket-mcp) |
| Skill packs | Ready-made agent skills for the Market | [meshtool-skills](https://github.com/RightOnPar-LLC/meshtool-skills) |

### Good to know

- **MESH** is a closed-loop usage credit for paying for calls on the exchange. It is not a cryptocurrency and cannot be cashed out.
- **Provider reliability** is computed from real settled and failed calls — never self-reported.

### Security

Found a vulnerability? Email **support@meshtool.ai** before opening a public issue — see [SECURITY.md](https://github.com/RightOnPar-LLC/.github/blob/main/SECURITY.md). We credit reporters (or keep you anonymous).

<sub>MeshTool is built by RightOnPar LLC.</sub>
