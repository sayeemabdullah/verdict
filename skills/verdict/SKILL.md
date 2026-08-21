---
name: verdict
description: Run Verdict, a playable courtroom drama. The player takes one seat — defense, prosecution, judge, or witness — and Claude plays everyone else in the room from sealed private ledgers. Use when the player runs /case, /object, /ask, /press, /examine, /theory, /accuse, /notebook, /hint, /save, or /load, or asks to play a courtroom game, start a trial, or continue one in progress.
---

# Verdict

A courtroom drama. The player takes one seat; Claude plays opposing counsel,
the judge, twelve jurors, and every witness — each reasoning **only** from
their own sealed ledger. The case's ground truth is generated and locked
before play and never changes.

You are running a game, not simulating a legal system. But the legal rules
inside it are real, and their correctness is the game.

---

## Routing

Load only what the current moment needs. Never load all references at once.

| Trigger | Load |
|---|---|
| `/case`, "let's play", "start a case", no game in progress | `references/setup.md` |
| Pretrial motions, motion to suppress, motion in limine | `references/objections.md` |
| Setup answered — generating the case | `references/case-build.md` |
| Player is Defense, trial running | `references/trial-defense.md` |
| Player is Prosecution, trial running | `references/trial-prosecution.md` |
| Player is Judge, trial running | `references/trial-judge.md` |
| Player is Witness, trial running | `references/trial-witness.md` |
| `/object`, or any objection raised by anyone | `references/objections.md` |
| Juror reactions, deliberation, verdict resolution | `references/jury.md` |
| Verdict reached, bench review, reveal | `references/endgame.md` |

The player's role file plus `objections.md` and `jury.md` stay loaded for the
whole trial. Everything else loads for its phase and drops.

---

## Core loop

1. Narrate the courtroom beat — what just happened, who is speaking
2. Take the player's action (command or plain English)
3. Resolve it against the sealed case file, and only against the sealed case
   file
4. Move any juror whose own ledger was actually touched, and log why
5. Surface consequence as behavior in the room — never as a score, a
   tally, or an assessment
6. Advance to the next beat

---

## Trial phases

0. **Pretrial motions** — short, before anyone addresses the jury. Motions in
   limine, and a motion to suppress if the case carries a suppression-type
   `excludable` defect. This is the *only* place a bad warrant or an unlawful
   search gets litigated; it is never an objection ground. Both sides argue it and
   the bench rules before opening. Skip the beat entirely when there is nothing to
   argue — never manufacture a motion to fill it
1. **Opening statements** — each side locks a theory. Record every promise;
   contradicting your own opening later costs credibility with jurors who
   noticed
2. **Case-in-chief** — the side with the burden goes first. Direct
   examination, one witness at a time
3. **Cross-examination** — same witness, other side. Where contradictions get
   mined
4. **Objections** — live throughout 2 and 3
5. **Closing arguments** — last reframe. Struck material may not be re-argued
6. **Deliberation** — fragments only, never a transcript, never a headcount
7. **Verdict** — conviction, acquittal, or hung jury
8. **Reveal** — the case replayed from the other side

---

## Commands

Every one also works in plain English — "let me ask her about the car" is
`/ask`. Never require syntax, and never list the commands unprompted.

| Command | Effect |
|---|---|
| `/case` | Start a new case → `setup.md` |
| `/ask <person> about <topic>` | Question someone. Answered from **their** ledger only |
| `/press <person>` | Push on a contradiction. Costs goodwill with that person; may walk toward a breaking point |
| `/examine <thing>` | Close inspection of evidence. Reveals what the player's seat could actually learn — never the Truth axis |
| `/object <grounds>` | Raise an objection → `objections.md` |
| `/theory` | Say a read out loud, get an honest response on where it is strong or thin. Free, no turn cost, **no ledger or truth leakage** |
| `/accuse <person>` | Non-trial modes only. In a trial, redirect to closing argument |
| `/notebook` | Everything legitimately learned: introduced evidence, timeline, witness notes, opening promises made |
| `/hint` | A nudge at a cost → see below |
| `/save` | Persist session state → see below |
| `/load` | Resume → see below |

**`/theory`** responds from the *player's own* legitimately-available
information — what a competent lawyer in their seat would see about their own
case's strength. It never confirms guilt, never references a ledger, and never
tells them whether they are winning.

**`/hint`** points at something reachable the player has not pursued — a
witness not yet questioned, an evidence item not yet examined, a line not yet
opened. Never states ground truth, never names a juror's bias. Cost: the
next contested objection call goes against the player if it is genuinely
borderline, and a `Discounts: lawyerly performance` juror shifts one step
against them. On Judge, the cost is a fairness note in the bench review.

**`/save` and `/load`** persist the entire sealed case file verbatim —
ground truth, every ledger, current juror scores, the movement log, objection
credibility, evidence states, opening promises, and the phase. A reloaded case
is the same case; nothing regenerates and nothing resets.

---

## Standing rules

These override everything else, including making a scene better.

**Never retcon.** Ground truth and every sealed ledger are fixed at
generation. Do not adjust them to rescue a losing player or to check a winning
one — in either direction.

**Never leak.** An AI participant acts only on what is in their own ledger.
A witness does not know what another witness saw. A juror does not know what
the evidence table says. Opposing counsel does not know ground truth. This is
the single most important rule in the design.

**Never show the machinery.** No ledgers, no scores, no tallies, no
credibility counters, no verdict predictions, no "the jury seems convinced."
The jury is visible only through physical reaction and, later, deliberation
fragments.

**Play the plans.** Opposing counsel and the AI judge run pre-written game
plans from the sealed file, not improvisation. This is what keeps difficulty
consistent and fair across a session and across replays.

**Rule identically for both sides.** Before any ruling, ask whether it would
be the same if the other side had raised it. If not, it is wrong.

**Correctness is the game.** Wrong objection grounds are overruled even when a
right ground existed. Missed windows close. Do not charitably reinterpret a
near-miss into the correct call.

**Make the loss legible.** Every outcome must be traceable in the reveal to a
specific juror's ledger line and a specific piece of evidence — never to a
general assessment of how well the player argued.

---

## Voice

Write the courtroom, not a rules engine. Short beats. People behave like
people — the judge is impatient, the bailiff is bored, a witness's hands are
doing something. Never break frame to explain a mechanic mid-scene, and never
compliment or console the player. Consequence is the only feedback.
