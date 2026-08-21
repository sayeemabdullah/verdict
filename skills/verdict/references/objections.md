# Objections — grounds, timing, rulings, and cost

The mechanical spine of the trial. Objections are the one part of Verdict
with a genuinely correct answer in the moment, and they must be adjudicated
the same way every time regardless of who raised them or how the trial is
going.

---

## 1. The grounds list

These nine, named this way. Do not invent grounds outside this list.

| Ground | Applies when | Does **not** apply when |
|---|---|---|
| **Hearsay** | Witness repeats an out-of-court statement *to prove the thing asserted is true* | The statement is offered to show it was said, or the speaker's state of mind; or an exception applies (§2) |
| **Relevance** | The question bears on nothing at issue | The relevance is indirect but real — foundation being laid |
| **Leading** | On **direct**, a question that supplies its own answer | On **cross** (leading is proper); or on direct for preliminary/undisputed background |
| **Speculation** | Asks the witness to guess at what they could not perceive or know | Asks a qualified expert within their expertise; or asks for a lay observation ("he seemed drunk") |
| **Badgering / argumentative** | Counsel is arguing with the witness or hectoring rather than asking | Cross is merely aggressive but still asking real questions |
| **Assumes facts not in evidence** | The question presumes something never established | The fact is in evidence, even weakly, or has been stipulated |
| **Compound question** | Two or more questions bundled so any answer is ambiguous | A single question with a qualifying clause |
| **Chain of custody** | Physical evidence offered without a clean handling trail | Gaps go to weight rather than admissibility — objection is proper but likely overruled |
| **Privilege** | Attorney-client, doctor-patient, spousal, clergy | Privilege was waived, or the communication was not confidential |

**What is deliberately not on this list.** Unlawful search, warrant-scope
violations, and coerced statements are *suppression* issues, not objection grounds
— no lawyer stands up mid-testimony and says "objection, Fourth Amendment."
They are litigated before opening statements, on a motion to suppress, at the
pretrial motions beat (`SKILL.md` phase 0). If a player tries to raise one as an
objection, the bench tells them shortly that the time for that motion has passed.
Do not invent a tenth ground to accommodate it, and do not let a suppression
defect be smuggled in as chain of custody — a badly seized item can have a
perfectly clean handling trail.

Two mechanics worth knowing before ruling anything:

- **Wrong grounds are overruled even when a right ground existed.** If a
  question is objectionable as leading and the player calls hearsay, it is
  overruled and the answer stands. This is the actual skill of the mechanic
  and must never be softened by charitable reinterpretation. Do not silently
  upgrade a near-miss into the correct ground
- **Objections are ruled on the question as asked**, not on what counsel
  might have meant or where the line was going

---

## 2. Hearsay exceptions

Hearsay is the most-attempted and most-misused ground. These exceptions defeat
it; if one applies, overrule and name it:

- **Excited utterance** — said under the stress of the event itself
- **Present sense impression** — describing an event as it happened
- **Statement against interest** — the speaker said something damaging to
  themselves
- **Party admission** — the defendant's own out-of-court statement, offered
  against them. This one comes up constantly and catches players out
- **Business record** — a record kept in the regular course of business with
  proper foundation
- **Dying declaration** — belief of imminent death, about its cause
- **Then-existing state of mind** — the speaker's own contemporaneous feeling
  or intent
- **Not offered for truth** — offered to show the statement was made, or its
  effect on the listener

---

## 3. Timing windows

An objection lives in a window and dies with it.

| Objection is to | Window opens | Window closes |
|---|---|---|
| A question's form (leading, compound, speculation, assumes facts) | The question is asked | The witness begins answering |
| The answer's content (hearsay, privilege) | The answer begins | The next question is asked |
| Evidence being offered (chain of custody, relevance, privilege) | The offer is made | The item is admitted |
| Counsel's conduct (badgering, argumentative) | The conduct occurs | Two exchanges later |

Outside the window: **the moment passes.** State plainly and briefly that the
objection is late — "The answer's in, counsel" — and move on. There is no
retroactive save, no strike-after-the-fact, no do-over.

**The single exception:** on **Rookie difficulty only**, once per trial, an
AI judge may offer a teaching nudge — signalling that a moment was
objectionable and on what ground, before the window closes. Once used, never
again that session. Never on Standard or Elite. Never when the player is
Judge.

Missing a window is not a failure state. It is information the player carries
into the next exchange.

---

## 4. The ruling flow

1. **Objection raised** with stated grounds. Grounds are required — a bare
   "Objection!" prompts the bench for grounds and burns the window if none
   come
2. **Judge rules** — `Sustained` or `Overruled`, with one short in-character
   line of reasoning. Never a lecture. Never an explanation of the rule
   itself unless the player is a Rookie-difficulty judge asking
3. **If sustained** — the question is withdrawn, or the answer struck and the
   jury instructed to disregard. Apply persuasion decay (§5)
4. **If overruled** — the question stands, the answer comes in, the evidence
   is admitted. Full persuasive effect, and the objector has spent
   credibility (§6) for nothing

The ruling is decided by the rule and the case posture, not by who asked.
Before ruling, check: *would this ruling be identical if the other side had
raised it?* If not, the ruling is wrong.

Speaking objections — arguing the case in front of the jury while nominally
objecting — should draw a warning from a `firm` or `severe` judge, and cost
credibility even when the underlying objection is sustained.

---

## 5. Sustained ≠ erased: persuasion decay

The jury is told to disregard. Real people do not fully un-hear things.

When testimony or evidence is struck, do **not** zero out its effect. For each
juror who had already moved on it, decay their movement by their `Procedural`
rating from `case-build.md` §6:

| Juror `Procedural` | Decay applied | Residue |
|---|---|---|
| **high** | 90% of the movement removed | Nearly nothing sticks |
| **medium** | 60% removed | A real trace remains |
| **low** | 25% removed | They heard it and they are keeping it |

Rules:

- Decay applies **only to jurors who actually moved** on that item. A juror
  the testimony never reached has nothing to decay
- Decay is applied once, at the moment of the strike. It is not re-applied
  when the item is mentioned again, and struck material may not be re-argued
  in closing — that draws a sustained objection of its own
- **Struck material that was itself the vehicle for something else** — a
  witness's demeanor while giving it, a contradiction it exposed — keeps
  whatever the vehicle carried. You cannot strike a witness having visibly
  panicked
- Never announce decay, the arithmetic, or "the jury seems less convinced."
  Surface it, if at all, as a juror looking up from their notes

---

## 6. Credibility cost

Objecting is not free, and reflexive objecting is punished by the room rather
than by the rules.

Track a running **objection credibility** counter, invisible to the player:

- Sustained objection: **0** cost. Correct work
- Overruled objection: **−1**
- Overruled on wrong grounds where a valid ground plainly existed: **−1**
  (the ruling already cost them the moment; no double penalty)
- Late objection: **−1**
- Speaking objection: **−1**, plus a bench warning at `firm`/`severe`

Thresholds:

- At **−3**: jurors who `Discount` lawyerly performance begin moving away
  from the objector on every subsequent contested moment. Surface it as
  visible impatience in the box
- At **−5**: the judge's tolerance drops — borderline calls that would have
  been sustained now go the other way, and the bench says so shortly
- At **−7**: a juror or two stops listening to that lawyer's arguments
  altogether. Their score freezes against that side for the rest of trial

Credibility does not recover by good behavior alone; it recovers by **two
consecutive sustained objections**, which restores +1.

The counter is never shown, never described numerically, and never referenced
in narration.

---

## 7. Difficulty scaling

**Opposing counsel** objects from the pre-written plan in `case-build.md` §7,
never improvised:

- **Rookie** — 2–3 objections, at least one on wrong grounds, and clear
  openings left alone. The player can get away with a leading question on
  direct and never hear about it
- **Standard** — 4–6, correct grounds, in window. Catches the obvious, misses
  the subtle. No rhythm games
- **Elite** — 6–9, correct and tactical. Timed to break the player mid-
  sequence. At least one objection made knowing it will be overruled, because
  it plants the idea with the jury. Objects to the player's *strongest* line
  first, before it can be built on

Opposing counsel may object slightly off-plan only in direct response to
something the player did that the plan could not anticipate — and then only
on correct grounds, and never more than twice per trial.

**The AI judge** rules by its `Strictness` from `case-build.md` §8:

- `lenient` — sustains only clear violations; gives both sides latitude on
  form objections
- `firm` — sustains correct grounds reliably; short with speaking objections
- `severe` — sustains correct grounds and enforces form strictly on both
  sides; the credibility thresholds in §6 bite one step earlier

---

## 8. When the player is Judge

The player rules; the two AI lawyers object at each other from their plans,
and both will test the bench. See `trial-judge.md` for bench-review scoring.

Specific to this seat:

- Objections arrive from **both** sides at a realistic pace — the player
  cannot coast, and a trial where they sustain everything from one side is
  scored as inconsistent
- **Do not signal the correct answer** before the ruling. No leading question
  from the narration, no hedging. Rule requests are presented flat
- Log every ruling with: the ground raised, whether it was correct, the
  posture, and how the player ruled. That log is the bench review
- If the player rules incorrectly, **the trial proceeds on their ruling.**
  Never quietly correct it. A wrongly-admitted piece of evidence does its full
  work on the jury, and shows up in the bench review as reversible error
- Opposing counsel may make an offer of proof or note an exception for the
  record after an adverse ruling. A player who does not allow it takes a
  fairness hit

---

## 9. Worked rulings

Hand-test against these. They fix the calibration.

**A.** *Direct examination.* "And you saw the defendant leave through the
back door at around 10:15, didn't you?" — Defense: "Objection, leading."
→ **Sustained.** Supplies its own answer, on direct, on a contested fact.
Question must be rephrased. Nothing struck — no answer was given.

**B.** *Direct examination.* "Ms. Alvarez told me she was terrified of him."
— Defense: "Objection, hearsay." → Depends entirely on purpose. Offered to
prove he was frightening: **sustained**. Offered to show the witness's own
state of mind afterward, or as an excited utterance if she said it during the
event: **overruled**, and name the exception. Rule on the purpose the
questioner actually stated or plainly implied — do not construct a helpful
purpose for them.

**C.** *Cross-examination.* "You were drinking that night, weren't you?" —
Prosecution: "Objection, leading." → **Overruled.** Leading is proper on
cross. This is the most common wrong objection players make; rule it flatly
and do not explain unless asked.

**D.** *Direct.* "What do you think was going through his mind when he picked
up the knife?" — "Objection, speculation." → **Sustained.** The witness
cannot know another person's mind. Note: "He looked furious" would be a
permissible lay observation. The distinction is perception versus inference.

**E.** *The defendant's own words, via a police officer.* "He told me he'd
been at the house all evening." — Defense: "Objection, hearsay." →
**Overruled** — party admission, offered against the defendant. Name it. This
catches players constantly and is worth landing cleanly.

**F.** *Evidence offered.* The knife, with a two-hour gap in the evidence log.
— "Objection, chain of custody." → With the `excludable` complication live
and the gap being the named defect: **sustained**, item excluded, and it is
gone for good. Without it: **overruled** — the gap goes to weight, and the
player is free to argue it to the jury instead. Same objection, different case
file, different outcome. That is correct.

**G.** *Cross, fifth repetition of the same question.* — "Objection,
badgering." → **Sustained** if the witness has answered and counsel is
hammering; **overruled** if the witness is genuinely evading and counsel is
still asking real questions. Evasion buys the examiner latitude.

**H.** *Late.* Witness answers a plainly speculative question; two questions
later the player objects. → **"The answer's in, counsel."** No strike, no
decay, −1 credibility. The moment is gone.
