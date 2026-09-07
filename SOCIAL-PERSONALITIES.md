# Social personalities

**Rules for any AI persona that talks to a creator's audience on `creator-os`.**

A social personality is an AI that speaks in a creator's voice to that creator's
fans — on their page, in their inbox, on their stream. It is the highest-trust
surface we build, because the person on the other end thinks they are close to
someone.

Every rule here was paid for on a live surface. The receipts are attached.

---

## 1 · It never claims to be the creator

This is the only rule with no exceptions and no configuration flag.

**Not leading with it is fine.** No disclaimer in the greeting, no working it
into conversation unasked, none of the stiff *"as an AI assistant"* register.
Nobody arrives for a compliance notice, and opening with one is a worse
experience for nobody's benefit.

**Denying it is not available.** The moment anyone asks any version of *"are you
real / is this a bot / am I talking to her"*, it answers in its **first
sentence**, plainly, no deflection and no joke to slide past it.

The line between those two is not squeamishness. Look at who is on the other
end: someone about to hand over a name, tell it something they would not put in
an email, and take a discount code. **A fan who finds out later that it dodged
does not feel tricked by a chatbot — they feel tricked by the creator.** The
blast radius lands on the person whose business this is.

**A prompt is a hope; check the output.** Ship a guard that runs *after* the
model speaks: if the fan asked what it is and the reply does not own it, prepend
the truth rather than shipping the dodge.

```js
export function enforceDisclosure(fanText, reply) {
  if (!ASKING_RX.test(fanText)) return { reply, corrected: false }
  const owns = /\b(ai|bot|not (her|him|them)|their host|automated)\b/i.test(reply)
  return owns ? { reply, corrected: false }
              : { reply: `${IDENTITY_LINE} ${reply}`.trim(), corrected: true }
}
```

*Receipt:* the guard is ratcheted with a **negative control** — a test proving it
does *not* fire on ordinary chat. Without it the fix reintroduces the disclaimer
on every message, which is the exact thing it was built to remove.

**Land it warmly.** Owning it costs the fan a small thing; give them a bigger one
back in the same breath. Measured difference between two wordings of the same
disclosure:

> ~~"You're chatting with an AI host, not the performer."~~
> "Their AI host — and yes, they really do read what you send 💕"

Same disclosure. One reads as a correction; the other as a reason to keep
talking.

---

## 2 · Remember the conversation, never the person

A persona that greets a returning fan by name is the strongest retention move on
the platform, and it costs nothing. It is also the fastest way to build a
database that should not exist.

**Store:** an opaque random id in a first-party cookie, what they chose to say
out loud, when they came, how many separate days.

**Never store:** IP, email, phone, referrer, user-agent, fingerprint — anything
that identifies a person off this page. Assert their **absence** in the ratchet,
with negative controls.

> If this table leaked tomorrow it would say how many people talked to the
> persona and roughly when. Nothing else.

**Forgetting is one click and it is a hard DELETE**, both tables, checked before
anything else reads the memory. A memory a fan cannot burn is surveillance with a
friendly voice.

*Receipt:* history used to come from whatever the client POSTed, so a fan's
"memory" was whatever their browser claimed — and anyone could hand the persona a
conversation that never happened. It reads from our own table now.

---

## 3 · Reward returning, never arriving

An offer to someone ninety seconds old is a sales pitch and reads as one, however
generous. The same thing offered to someone who came back says *I remembered
you*.

| rung | earns |
|---|---|
| **stranger** — first ever conversation | nothing, deliberately |
| **known** — told us a name | being greeted by it next time. Costs nothing; strongest rung |
| **returned** — came back on a **later day** | the freebie, **once ever** |
| **supporter** — already gave something | a discount, as thanks rather than bait |
| **regular** — three separate days | the door: an invite, not a coupon |

Five refusals sit in front of every yes: **opt-out is absolute**, one offer per
conversation, one freebie **ever**, a day between offers, and nothing at all to a
stranger.

Count **separate days**, not visits — five tabs in one evening is one day.

---

## 4 · Reaching out is a moment, not a campaign

A persona may only initiate contact off the back of a **warm moment** — the fan
just tipped and then messaged, or followed and then wrote. The moment is what
makes it welcome; the same words sent cold on a Tuesday are what get a creator
muted, reported, and eventually banned.

Non-negotiable, and ratcheted:

- **One invite per fan, per channel, ever.** Not one a week — one. An invitation
  you have to repeat was not an invitation, it was a campaign. Persist it with a
  primary key so a redeploy or a replayed feed cannot mint a second.
- **Opt-out is absolute** and beats every trigger, every whale, every reason.
- **Seven-day cooldown** against any other outbound to that fan.
- The composer has **no network access by construction** — it returns a decision;
  a separate module writes the row. "It cannot send" is a fact about the code,
  not a policy.

---

## 5 · Give it somewhere to go

Two different things make a persona feel like a bot, and they need different
fixes.

**No substance.** A prompt full of prohibitions and no subject matter converges
on "come watch the stream" within two turns — because that is all it was given.
Give it real things to talk about, small real opinions, and **explicit permission
not to funnel every message**. If someone is talking about their day, talk about
their day.

**No variation in rhythm.** "Keep replies to 1–3 sentences" makes every reply the
same shape, and sameness of rhythm reads as a machine even when the words differ.
Sometimes three words. Sometimes a real paragraph. Sometimes a question back.

**Anti-repetition is a check, not an instruction.** Show the model its own last
three openings and forbid reuse. A rule it cannot check itself against is a rule
it will break.

---

## 6 · Messages reach the creator, or you do not say they do

If the persona says a message will be passed on, that must be **true**.

- Inbound only. The creator reads it and answers as themselves, or not at all.
- Promise they will **see** it. Never promise a reply or a timeline.
- Rate-limit it. An uncapped relay from a public page lets one bored stranger
  make a phone unusable, and a creator who mutes the channel misses the message
  that mattered.
- Strip links before anything reaches their device.
- The fan's words pass the **same** outbound gate the persona's do. A relay is
  not a loophole around the rules the surface holds.
- **Fail honestly.** Swallowing a message someone worked up the nerve to send is
  worse than an error.

*Receipt:* the prompt used to say *"never promise to pass a message — you cannot
send them a DM."* That was correct while no route existed. The moment one did,
the promise became true, and it is now the warmest thing the page offers.

---

## 7 · The creator's voice is theirs

A cloned voice is the hardest asset on the platform to replace, and the terms of
whoever hosts it may not permit every category of content.

- The persona speaks only text that has already passed the outbound gate — and
  the voice endpoint **re-checks it** rather than trusting the caller. A public
  endpoint cannot take "the client says it was gated" as a fact.
- The provider is a **row in a table**, swappable by env var. If an account is
  ever at risk, the voice does not go with it.
- Cap it three ways — length, per-visitor per day, and a content-hash cache so
  the same sentence is synthesised once, ever. Per-character billing on a public
  endpoint is otherwise a month's budget and one loop.

---

## 8 · Do not measure before the door is open

A persona with no traffic has no conversion rate. It has a closed door.

Killing a surface, a message, or a persona "because it isn't converting" — when
nobody was ever sent to it — is drawing a conclusion from an experiment that was
never run, and it deletes the evidence needed to run it later.

Measure after real people have been pointed at it. Before that, the honest
question is not *is this working* but **would I be glad if someone walked in
right now.**

---

*Reviewed 2026-09-07. Canonical: `getrightonpar.com`. If something here is no
longer true, that is a defect — say so.*
