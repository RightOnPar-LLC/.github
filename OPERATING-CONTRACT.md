# The operating contract

**Who this is for:** anyone with write access to a Right On Par repo — today the
owner, his brother, and the agents; tomorrow whoever ships the creator software
with us.

`CONTRIBUTING.md` is for people looking under the hood from outside. This is for
people who can merge. Different audience, different rules, higher stakes.

Read it once properly. It is short because every rule in it was paid for.

---

## 0 · The one thing to understand first

**A rule you have to remember is a hope. A rule a machine checks is a rule.**

That is the organising idea behind everything below. Where you see a guideline
here, look for the check that enforces it — a selftest, a hook, a required
status. Where there is no check yet, the guideline is on trust, and the right
response to noticing that is to build the check, not to write the rule louder.

You will find that written into the code in a dozen places. It is not a slogan;
it is why this estate works with as few people as it has.

---

## 1 · The four floors

Four actions are **never** taken by anyone except the owner, no matter how
obvious, urgent, or small they look:

| floor | what it covers |
|---|---|
| **Money out** | any new spend, any charge, any payment method |
| **Outward publish or send** | anything that reaches a person outside the company — a post, an email, an SMS, a listing |
| **Credential or access to a person** | adding someone to an org, granting a role, minting them a key |
| **Irreversible deletes** | deleting a repo, a bucket, a database, a record that has no undo |

Everything else is yours. Genuinely — you do not need permission to build,
refactor, deploy, fix, or ship. The floors are four narrow things, not a
posture.

**Two rules about the floors themselves:**

**Archiving is the ceiling.** Where you would delete, archive instead. It is
reversible, it keeps the audit trail, and it is almost always sufficient.

**"I could" is not "I may."** You will sometimes hold a credential that would
let you cross a floor. That is a fact about tokens, not a permission. If you
notice you can do something you should not — say so, out loud, and we scope the
credential down. That is a good day, not an awkward one.

---

## 2 · Proof over promises

**"Tested", "live", "done" and "working" are claims. Say them only when you have
just watched the evidence.**

- Not "the tests pass" — the runner's own green line, read after it ran.
- Not "it deployed" — the live URL answering, after propagation.
- Not "N tests added" — the count read back from the file, not from the script
  that claimed to add them.

This is enforced retroactively and without drama: a doc that says something is
tested when it is not gets corrected, and so does the claim that put it there.
Nobody is in trouble for a red test. The only thing that costs trust is a green
that was never measured.

**Corollary — an error is UNKNOWN, not absence.** A check that fails to run has
not proven anything. A timeout is not "it's down". A permission error is not
"the file is missing". Retry, distinguish the error text, and report what you
actually know.

---

## 3 · Everything lands

**"I wrote the code" is not done.** A unit of work is done when it is merged,
deployed, and verified — or when it is written down somewhere with its next step
and its owner.

There is no third option, and this is the rule that keeps the estate from
silting up. If you have to stop, stop *and log it*. An unfinished thing that is
recorded is a task; an unfinished thing that is not is a landmine for whoever
touches that file next.

Sweep before you finish for the day. Anything of yours older than three days
with no next step gets finished or written down.

---

## 4 · Before you build

**Claim it.** Say what you are building before you start, in whatever channel
we use for it. Two people building the same thing is the most expensive
mistake available to a small team, and it is invisible until the merge.

**Search first.** Before writing anything with a *name* — an encoder, a parser,
a scheduler, a cache, a QR generator — grep the estate for it. This is the rule
most often broken by the most experienced person in the room, because
experienced people can write it faster than they can find it. The estate has
been burned by exactly this: a hand-rolled QR encoder shipped when three already
existed, and the resulting card would not scan.

**Route it.** Anything new — a repo, a service, a folder — goes on the map
before it grows. A thing nobody can find gets rebuilt.

---

## 5 · The gate

Every repo with a `tests/` directory treats it as a **ratchet**: the count only
goes up.

- Fix a bug → add the assertion that would have caught it, and **watch it go
  red before you fix it.** An assertion never seen failing has not been proven
  to work.
- Run the repo's own gate before pushing. A red gate is not a suggestion and
  not a rate limit.
- `--no-verify` is a visible human override for an emergency. It is never a
  shortcut, and it is never used by an agent.

**Write checks that cannot cry wolf.** A guard that fires on innocent work gets
switched off within a week, and then it protects nothing. Every new check gets
two controls: one proving it fires on the real thing, one proving it does *not*
fire on ordinary work. Budget one round for fixing the checker itself — the
first live run of any new check is a test of the check.

---

## 6 · The ring-fence

The company runs two lanes. The boundary is **one-directional**:

> The adult vertical may depend on the platform. The platform never contains,
> depends on, or is branded by the adult vertical.

Nothing from that side lands in a Right On Par repo — no hostnames, no room
names, no identifiers, not in code, not in a comment, not in a commit message.
If you are unsure whether something crosses, it crosses; ask.

Access to that side is **by explicit grant, never blanket** — including for
people who have full access here. That is not distrust. There is a third
person's personal data on that side, and her consent is not the owner's to give
by proxy.

---

## 7 · How to disagree

State the concern once, plainly, with the evidence. If the owner reaffirms it,
that is the decision — build it fully and well, and note the concern where it
will be found later if it turns out to matter.

Do not silently comply with something you think is wrong, and do not relitigate
something already decided. Both waste the same thing.

**And when you are wrong, say so in one line and move on.** No essay, no
apology spiral. Correct it, note what changed, keep going. Everyone here breaks
things; the only unrecoverable move is hiding it.

---

## 8 · What the owner does that you should not copy

This is here because it is genuinely confusing otherwise.

The owner works fast, pivots mid-thought, and goes straight at production. That
works **for him** because he holds context nobody else has: what every surface
is for, what is load-bearing, what was already tried and abandoned. He is not
skipping the rules — he is carrying the map in his head.

You do not have that map yet, and neither did the agents when they started.
Until you do:

- Read the surrounding code before you change it.
- Write down the thing you just learned — the estate's memory is a real asset
  and it compounds.
- When you are about to do something fast because it is obviously fine, that is
  the moment to check.

The rules are the same for everyone. The *style* is his, and it is earned.

---

## 9 · Where the rules live

**`rightonpar.com` is the canonical source.** This file, and every copy of these
rules in a repo, is a mirror of it. If a mirror and the canonical source
disagree, the canonical source wins and the mirror is drifting — fix the mirror,
and if it drifted silently, ask why nothing caught it.

Every repo inherits this document automatically via the org's `.github`
defaults. You do not need to copy it.

---

*Last reviewed 2026-09-07. If you read something here that is no longer true,
that is a defect — say so.*
