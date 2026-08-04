# Contributing

Thanks for looking under the hood. These repos are small on purpose — we
publish what actually runs, so contributions are easy to reason about.

## Filing issues

- **Bugs**: say what you ran, what you expected, what happened. A copy-paste
  of the failing command beats a description of it.
- **Ideas**: open an issue before writing code — we'd rather say "yes, and
  here's the seam to build against" than review a PR that fights the design.
- **Security**: don't open a public issue. See `SECURITY.md` in the repo
  (mesh-connector carries the policy for the platform surface).

## Pull requests

- Keep a PR to one change. Small and reviewable merges fast.
- Repos with a `tests/` directory treat it as a ratchet: if you fix a bug,
  add the assertion that would have caught it. Run the repo's selftest before
  pushing (`node tests/selftest.mjs` where present; `cargo test` in Rust).
- Match the code around you — comment density, naming, error handling.
- Plain honest docs: never claim tested/live/done for anything that isn't.
  It's the house rule, and it's enforced retroactively.

## What's welcome right now

- Client-compatibility fixes for `mesh init` (new MCP clients appear weekly)
- Docs clarity — especially anything that confused you on first read
- Test coverage where a repo admits it's thin (check its `TASKS.md`)
