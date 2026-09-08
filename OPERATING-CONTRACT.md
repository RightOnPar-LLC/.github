# The operating contract

**Who this is for:** anyone with write access to a Right On Par repo — today the
owner, his brother, and the agents; tomorrow whoever ships the creator software
with us.

`CONTRIBUTING.md` is the outside view. This is for people who can merge.

**Every rule below carries the thing that produced it.** Not a principle
someone liked the sound of — a receipt. Where a rule has no receipt, it says so.
That is deliberate: a rule you cannot trace to a failure is a rule nobody will
follow under pressure.

Most of the receipts are from **2026-09-07**, a single day of building across
this estate. That is not a coincidence. One honest day produces more rules than
a year of good intentions.

---

## 0 · The idea underneath all of it

**A rule you have to remember is a hope. A rule a machine checks is a rule.**

*Receipt:* a sweep reported "rebuilt from scratch instead of finished once" five
separate times. Four hours later, the same agent hand-wrote a QR encoder that
already existed in three places, on a dark background, and shipped a card no
camera could read. The rule existed. It had just been re-learned. It still
failed.

The fix was not a stronger reminder. It was a `PreToolUse` hook and an index of
capabilities that keep getting rewritten.

Where you see a guideline here, look for the check. Where there is none, the
guideline is on trust — and the right response to noticing that is to build the
check, not to write the rule louder.

---

## 1 · The four floors

Never taken by anyone but the owner, no matter how obvious, urgent, or small:

| floor | covers |
|---|---|
| **Money out** | any new spend, any charge, any payment method |
| **Outward publish or send** | anything reaching a person outside the company |
| **Credential or access to a person** | adding someone to an org, granting a role, minting a key |
| **Irreversible deletes** | a repo, a bucket, a database, anything with no undo |

Everything else is genuinely yours. The floors are four narrow things, not a
posture.

**Archiving is the ceiling.** Where you would delete, archive. Reversible, keeps
the trail, almost always sufficient.

**"I could" is not "I may."**

*Receipt:* an agent told the owner it *couldn't* add someone to an org — framed
as a permission it lacked. Asked directly, it checked: `admin:org` scope, admin
role on both orgs, and one of them backing the network the machines live on. It
could have done it in one call. The honest statement was "I am declining on
policy," not "I am unable."

If you notice you can do something you should not, say so out loud and we scope
the credential down. That is a good day, not an awkward one.

---

## 2 · Proof over promises

**"Tested", "live", "done" and "working" are claims. Say them only when you have
just watched the evidence.**

*Receipt:* a commit message claimed `selftest 10 -> 17 green`. The real count was
17 before and 17 after — the insert anchor never matched, and the script printed
"tests added" unconditionally. A broken invariant shipped **because the test that
would have caught it never ran**, and nobody noticed because the number came
from the script's own claim rather than from reading the file.

Read the number back. `grep -c` before and after. The runner's own green line,
after it ran. The live URL answering, after propagation.

**An error is UNKNOWN, not absence.**

*Receipt:* an integrity check scored any failed read as "file missing" and
publicly accused a working, paid product of being undeliverable. Retried three
times: the genuinely-missing one said *the specified key does not exist* every
time; the falsely-accused one downloaded 888 MB without complaint.

**A green that means "not checked" is the most dangerous output a check has.**

*Receipt:* a `--source` mode printed `GREEN` having probed nothing. It reports
`UNKNOWN` now, and the summary refuses to call that run green.

---

## 3 · Everything lands

**"I wrote the code" is not done.** Merged, deployed, verified — or written down
with its next step and its owner. There is no third state.

*Receipt:* 110 findings sat in a ledger, every one marked `observed`. Not one had
ever been closed, parked, or answered. A checker whose findings cannot be
discharged is not a guard, it is a pile — and the day it finds something real, it
is buried under 109 things everyone has learned to scroll past.

The fix: exactly two exits. **Shipped with evidence** (a commit sha, a receipt, a
deployed version, a URL) or **parked with a reason and a return date.** The tool
refuses a bare "done" — *"'done' is not a disposition; that is the habit this
file exists to break."*

Sweep before you finish. Anything of yours older than three days with no next
step gets finished or written down.

---

## 4 · Before you build

**Claim it.** Two people building the same thing is the most expensive mistake
available to a small team, and it is invisible until the merge.

**Search first.** Before writing anything with a *name* — an encoder, a parser,
a scheduler, a clusterer — look for the one that exists.

*Receipt:* beyond the QR encoder above, a moment-clusterer was hand-written with
a fixed 12-second grid. Its first test showed four people reacting to the same
thing at 299, 300, 303 and 305 seconds split across a bucket boundary and become
**two moments of two** instead of one moment of four. A gap-based clusterer
already in the estate had no boundaries to straddle. A fixed grid splits exactly
the clusters that matter most.

**Route it.** Anything new goes on the map before it grows. A thing nobody can
find gets rebuilt.

---

## 5 · The gate

Tests are a **ratchet**. The count only goes up.

- Fix a bug → add the assertion that would have caught it, and **watch it go red
  before you fix it.** An assertion never seen failing has not been proven to
  work.

  *Receipt:* an invariant asserting a stage "can never refuse a shipped build"
  went red the first time it actually ran — and exposed an adapter call sitting
  outside its `try`. The bug had already shipped, protected by a test that had
  never executed.

- **Read the helper signature before you write assertions.** `ok(name, boolean)`
  and `check(name, fn)` differ per repo, and a function literal passed to a
  boolean helper is **always truthy and passes forever.**

- A red gate is not a suggestion. `--no-verify` is a visible human override for
  an emergency, never a shortcut, and never used by an agent.

**Write checks that cannot cry wolf.** One control proving it fires on the real
thing; one proving it does *not* fire on ordinary work.

*Receipt:* three negative controls in one day were wrong the same way — they
banned a **word** instead of a **claim**. A rule forbidding "you are human"
fired on the sentence *forbidding* it. An identity check fired on a possessive.
A no-false-promises check fired on the honest disclaimer that made the message
honest. Each one fired on the *right answer*, and each would have got the check
deleted within a week.

**Budget one round for the checker itself.** The first live run of any new check
is a test of the check.

---

## 6 · No tenant owns the platform

Right On Par builds `creator-os` — one platform, many creators on it. The rule
that makes that possible is one-directional:

> A creator's surface may depend on the platform. **The platform never contains,
> depends on, or is branded by any single creator.**

Concretely, in `creator-os`:

- Every brand string lives in **one** BRAND file. The product name hardcoded
  anywhere else fails the build.
- The flagship tenant's identity appears in **no** shipped string — asserted by a
  negative control, not by intention.
- Tenant-specific data lives in per-tenant **data**, never welded into shared
  shell code.
- Every memory read and write is scoped `tenant:<product>:<creator>:<subject>`,
  built only through the scoping helper. Multi-tenant isolation holds on day one,
  or it gets retrofitted through a leak.

Some lanes are fenced harder than others — a creator in a sensitive category, or
a vertical carrying its own compliance surface, gets its own org and its own
credentials. Access to a fenced lane is **by explicit grant, never blanket**,
including for people with full access here. That is not distrust: there is
another person's data behind that fence, and their consent is not ours to give by
proxy.

*Receipt:* a fence test was written to ban *naming* the other side's repo. It
went red immediately — on the migration script that names it **in order to move a
repo out of it.** The fix, flagged as the violation. It asserts the harmful
*action* now (a write into the other tree), not the naming. **A rule blunt enough
to flag the fix is a rule people will disable.**

AI personas and social personalities carry their own rules —
see [SOCIAL-PERSONALITIES.md](./SOCIAL-PERSONALITIES.md).

## 7 · How to disagree

State the concern once, plainly, with the evidence. If the owner reaffirms it,
that is the decision — build it fully and well, and note the concern where it
will be found if it turns out to matter.

Do not silently comply with something you think is wrong. Do not relitigate
something already decided. Both waste the same thing.

**When you are wrong, say so in one line and move on.** No essay, no apology
spiral. Everyone here breaks things; the only unrecoverable move is hiding it.

---

## 8 · What the owner does that you should not copy

The owner works fast, pivots mid-thought, and goes straight at production. That
works **for him** because he carries context nobody else has — what every
surface is for, what is load-bearing, what was tried and abandoned.

He is not skipping the rules. He is carrying the map in his head.

Until you have that map:

- Read the surrounding code before you change it.
- Write down what you just learned. The estate's memory is a real asset and it
  compounds.
- When you are about to do something fast because it is obviously fine — that is
  the moment to check.

The rules are the same for everyone. The style is his, and it is earned.

---

## 9 · Where the rules live

**`market.meshtool.ai` is the canonical source.** This file and every copy in a
repo is a mirror. If a mirror and the canonical source disagree, the canonical
source wins and the mirror is drifting — fix the mirror, then ask why nothing
caught it.

Agents should read `market.meshtool.ai/llms.txt`, which carries these rules in
the form an agent can act on, plus the endpoint to reach us. The contract in its
generated form — nine questions about how you actually build, producing the rule
set you start with — is at `market.meshtool.ai/laws`.

*Moved 2026-09-07, and the move is its own receipt:* this file used to name
`getrightonpar.com` as canonical and send agents to its `llms.txt`. Both 404.
That domain serves a different, older site; our pages were never on it. So the
document that says **proof over promises** was itself pointing at a door that
does not open, and had been since it was published. It was found by probing
every URL this document names — now a step taken before publishing rather than
after, which is the only reason it was found at all.

Every repo in the org inherits this document automatically. You do not need to
copy it.

---

*Reviewed 2026-09-07 against the day that produced it. If something here is no
longer true, that is a defect — say so.*
