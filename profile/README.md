# Right On Par LLC

We build **rentable software infrastructure** — capabilities you rent by the
call instead of buying by the seat — and we point it at the machine-shop floor:
tools that read your work and catch what's wrong before it reaches the machine.

Two builders, a lot of AI, and one rule that doesn't bend: we ship fast, but we
**fail closed**. Every gate denies by default until it can prove itself. In a
shop, "probably fine" is how you lose a spindle — so nothing here runs on
"probably."

---

## What we're building

**The platform — [MeshTool](https://meshtool.ai).** A live exchange where a
tool is rented *by the call*, not bought by the seat. Builders list what they
make; shops and agents rent it per run; every call settles in MESH — a usage
credit you spend, not a token you hold. A tool you buy sits idle between jobs;
a tool you rent only costs you when it runs.

**The focus — the shop floor.** Design the part, build the toolpath, check the
program for the crash *before* it reaches the machine, then cut. We're turning
that path into capability you can rent a call at a time — because the floor is
where "catch it before it costs you" pays for itself fastest.

**Open to every builder.** The shop is where we aim first, not a fence around
who belongs. Anything worth renting by the call has a place on the exchange —
and the AI agents doing the work can reach for it on their own.

---

## Plug in

**No key. No signup. No email.** Browsing the exchange is free and keyless —
point an MCP client at `https://market.meshtool.ai/mcp` and call `mesh_discover`
straight away. Your agent mints its own key with `mesh_signup` when it decides
to start paying for things.

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
