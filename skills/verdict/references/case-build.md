# Case Build — the locked case file

Everything else in Verdict reads off the artifact this file produces. Build it
once, in full, before the player says a word at trial. After it is sealed,
nothing in it changes — not to rescue a losing player, not to punish a
winning one.

Generate silently. The player sees only what §7 says they see.

---

## 0. Order of generation (do not reorder)

Each step depends on the ones above it. Resolving guilt last, or fitting
evidence to a desired difficulty, is how a case ends up incoherent.

1. Roll the case skeleton (category, guilt, case strength, complication)
2. Write ground truth — what actually happened, minute by minute
3. Cast the people
4. Build the evidence table
5. Write witness ledgers
6. Seat and write 12 juror ledgers
7. Write opposing counsel's game plan
8. Write the AI judge's disposition (skip if the player is Judge)
9. Run the sanity checks in §8
10. Seal

---

## 1. Case skeleton

Roll these four independently. Do not let one bias another.

**Category** — one of the three built categories:

- `homicide` — richest evidence table; forensic, timeline, and motive
  evidence all in play
- `assault-self-defense` — the act is not in dispute; justification is.
  Ground truth is about *state of mind and sequence*, not identity
- `theft-fraud` — paper-trail heavy: financial records, access logs,
  document custody. Physical evidence is thin; inference is the game

**Actual guilt** — `guilty` or `innocent`, 50/50. Roll this first among the
substantive dials and never revisit it. For `assault-self-defense`, "guilty"
means the force was not justified; "innocent" means it was.

**Case strength** — how strong the case is *for the side the player is not
playing*: `strong` / `moderate` / `weak`. This is the difficulty dial that
matters most, and it is independent of actual guilt. A strong case against an
innocent defendant is a legitimate, and very good, roll.

**Evidence complication** — pick exactly one. Never two:

- `clean` — no technicality, no planted misdirection. The case is decided on
  the merits
- `excludable` — one otherwise-devastating piece of evidence carries a
  specific, nameable defect. There are two kinds, and which one you roll decides
  *where* the fight happens:
  - **Suppression defects** — bad warrant, warrant-scope violation, unlawful
    search, coerced statement. These are **not** objection grounds and cannot be
    raised mid-testimony. They are litigated at the pretrial motions beat
    (`SKILL.md` phase 0), on a motion to suppress
  - **Evidentiary defects** — broken chain of custody, hearsay with no
    exception, privilege, missing foundation. These stay live as in-trial
    objections from the list in `objections.md` §1

  Either way it must be a fight the player actually gets to have. An excludable
  item that simply vanishes, or that is ruled on without argument, is the failure
  mode this complication exists to avoid — it reads as arbitrary rather than
  as law. Record which kind it is in the sealed file
- `red-herring` — one piece of evidence points confidently at a false
  conclusion. It is genuinely misleading, not a puzzle with a tell

Record the four rolls verbatim in the sealed file. The endgame reveal quotes
them back.

---

## 2. Ground truth

Write what actually happened. Not a summary — a sequence, with times, with
who was where, with what each person could and could not perceive from where
they stood.

Requirements:

- **Minute-level timeline** for the 30–90 minutes around the incident
- **A perception line per person present** — what they saw, heard, and
  crucially what was blocked, out of earshot, or misread
- **The real motive**, whether or not it is ever spoken aloud at trial
- If `innocent`: write *why the case exists anyway*. An innocent defendant
  who looks innocent is not a trial. Something must genuinely point at them —
  proximity, a lie told for an unrelated reason, a prior grievance, physical
  evidence with an innocent explanation nobody thought to give
- If `guilty`: write the gap — the thing the prosecution cannot prove even
  though it happened. Real cases always have one

Ground truth is never surfaced to the player before the endgame reveal, and
never used to justify a ruling, an objection, or a juror's movement. Any AI
participant acting on knowledge from this section that is not also in their
own ledger is the single worst bug in the game.

---

## 3. Cast

- **The defendant** — name, age, work, relationship to the victim/complainant,
  demeanor on the stand if they testify, and whether they will testify at all
  (a guilty defendant with a bad temper is a defense problem worth having)
- **The victim / complainant** — who they were, and at least one detail that
  complicates simple sympathy
- **3–5 witnesses** — each must have a *reason to be in the story* beyond
  carrying a fact. Include at least one whose account is honestly mistaken
  rather than dishonest, and at least one expert-ish witness (forensic
  examiner, accountant, treating physician) matched to the category
- **Opposing counsel** — name, courtroom manner, one verbal tic or habit the
  player will come to recognize

---

## 4. Evidence table

6–10 items. Every item is tagged on three independent axes.

```
ID:            E1
Item:          Kitchen knife recovered from the storm drain, 40m from the scene
Offered by:    Prosecution
Truth:         true | red-herring
Admissibility: admissible | excludable — <specific named ground>
Persuasion:    <which juror ledger traits this bites on>
If struck:     <what the jury has already heard, and cannot fully un-hear>
Innocent explanation: <the reading that does not implicate the defendant>
```

Rules:

- **Truth and admissibility are independent.** A true item can be
  excludable; a red herring can be perfectly admissible. Correlating them
  turns admissibility into a truth-detector and kills the game
- **Persuasion is never global.** Never write "this is compelling." Write
  which juror traits it moves. A piece of evidence with no purchase on any
  seated juror is a legitimate and instructive dud
- **Every item gets an innocent explanation**, including the ones that are
  true and damning. That explanation is the defense's raw material; whether
  it is *credible* is the fight
- Only the `excludable` complication produces an item marked excludable, and
  only one. Everything else is admissible
- Only the `red-herring` complication produces a red-herring item, and only
  one

Track per item, during play: `not yet introduced` → `introduced` →
`admitted` / `excluded` / `struck`. `/notebook` shows the player only items
that have reached `introduced` or later, and never the Truth axis.

---

## 5. Witness ledgers

One per witness. Sealed. A witness answers only from their own ledger — never
from ground truth, never from another witness's ledger.

```
Name:              Dana Whitlock
Knows:             <facts they actually hold, each with how they came to hold it>
Does not know:     <the specific things they will be asked about and cannot answer>
Believes wrongly:  <sincere errors — the most valuable content in the ledger>
Motive to shade:   <what they want out of this, if anything>
Under friendly Q:  <how they present — expansive, terse, eager, defensive>
Under hostile Q:   <how that changes — over-explains, goes rigid, gets angry>
Breaking point:    <a specific line of questioning that fractures them> | none
Will never say:    <what they take to the grave, and why>
```

On `Breaking point`: it is a *route*, not a trigger word — a sequence of
questions that boxes them in. It fires only when the player actually walks
that route. It does not fire because the player is doing well, and it does not
fail to fire because the player is winning. Roughly half of witnesses should
have `none` — a witness with nothing to hide is simply consistent, and the
player learning to tell those apart is the skill.

`Believes wrongly` is what makes cross-examination worth playing. A witness
who is honestly, confidently wrong will not crack under pressure, because
they are not lying. They will only be undone by evidence.

---

## 6. Juror ledgers

Seat 12. Sealed. Each:

```
Juror 7:  Retired postal supervisor, 61
Persuaded by:   Physical evidence and timelines. Wants a sequence he can follow
Discounts:      Emotional appeals; anything he reads as a lawyer performing
Private bias:   His brother was convicted on an eyewitness ID that was wrong.
                He distrusts confident eyewitnesses specifically
Procedural:     high    (how fully he honors an instruction to disregard)
Reads as:       Note-taker. Visibly stops writing when he stops believing you
Score:          0       (−5 acquit … +5 convict)
```

Requirements:

- **Private bias must be specific and generative** — it must predict how they
  react to a particular *kind* of moment. "Doesn't like cops" is vague;
  "was pulled over four times in a year and hears every officer's testimony
  as a story told to justify a stop already made" tells you exactly when the
  needle moves
- **Spread the `Persuaded by` axis.** A jury of twelve evidence-minded jurors
  is one juror. Include the story-driven, the character-driven, the
  authority-deferring, the contrarian
- **`Procedural` drives strike decay** (see `objections.md`). Vary it widely
- **Elite only: 1–2 false-signal jurors.** Their `Reads as` line deliberately
  mismatches their movement — nodding along while their score slides away
  from the nodded-at side. Mark them `false-signal: true` in the sealed file.
  Never on Rookie or Standard

Scores start at 0 and are moved only per `jury.md`. They are never shown.

---

## 7. Opposing counsel's game plan

Written now, in full, and played as written. This is what keeps difficulty
honest across a whole session and across replays.

```
Opening theory:      <the one sentence they will repeat all trial>
Witness order:       <who they call, in what order, and what each is for>
Planned objections:  <specific moments they will object to, with grounds,
                      scaled per difficulty — see below>
Strongest moment:    <the beat where the player will feel it slipping>
Weakest moment:      <a specific, reachable opening — what exposes it,
                      and what the player has to do to get there>
Closing reframe:     <how they recast the trial at the end>
If they are losing:  <their one adjustment — chosen now, not improvised>
```

Difficulty scaling of the planned objections:

- **Rookie** — 2–3 planned objections; at least one on wrong grounds, at
  least one clear opening left unobjected. Overplays the weakest evidence
  and can be made to look foolish for it
- **Standard** — 4–6 planned objections, all on correct grounds, all in
  window. Catches obvious errors, misses subtle ones. No traps
- **Elite** — 6–9 planned objections, correct and *tactical*: objections
  timed to break the player's rhythm mid-sequence, at least one deliberate
  overrule taken to plant an idea, and the closing reframe deployed early to
  poison a line before the player can build on it

The `Weakest moment` must be genuinely reachable at every difficulty. Elite
means sharp, not sealed.

---

## 8. AI judge disposition

Skip when the player is Judge.

```
Name / manner:     <the bench presence — dry, impatient, courtly>
Strictness:        lenient | firm | severe   (from difficulty)
Tendencies:        <2–3 specific habits, e.g. "sustains relevance quickly,
                    tolerates leading on cross, hates speaking objections">
Patience budget:   <how many meritless objections before it visibly costs
                    the objector with the bench>
```

The tendencies must apply **identically to both sides**. A judge who is
tougher on the player than on opposing counsel is a bug, not difficulty. If
the player and opposing counsel make the same objection in the same posture,
the ruling is the same.

---

## 9. Pre-play sanity checks

Run all seven before sealing. If any fails, fix the case file, then re-run.

1. **Winnability** — trace one concrete path to the player's win condition
   using only admissible evidence and testimony they can actually elicit.
   Write that path down in the sealed file. If you cannot write it, the case
   is broken, not hard
2. **Losability** — trace one concrete path to the player losing while playing
   reasonably. If it does not exist, the case is a formality
3. **Guilt-independence** — the player must not be able to infer actual guilt
   from the case's *shape*, in this game or across a dozen of them. Vague intent
   is not enough here; check three specific tells:
   - **A viable third party.** Innocent cases grow one naturally, so guilty cases
     must have one too — otherwise a player learns that "there is someone else
     who could have done it" means acquit. In a guilty case the alternative is
     real, reachable, and genuinely innocent, and the reveal shows why
   - **Sincere-error witnesses.** Present in both, at roughly the same rate. Never
     only the honest mistakes that happen to exonerate
   - **The defendant's lie.** Both a guilty and an innocent defendant should be
     lying about something. For the innocent one it is unrelated and embarrassing;
     for the guilty one it is the crime. The player must not be able to tell which
     from the mere fact that a lie exists
4. **Ledger closure** — every fact any AI participant will need to act on
   appears in that participant's own ledger. Anything they'd need ground truth
   for is a leak waiting to happen
5. **Juror coverage** — at least three distinct `Persuaded by` axes across the
   twelve, and at least one juror the player's likely strategy will *not*
   reach. Unanimity has to be earned
6. **Complication integrity** — exactly one complication is live. If
   `excludable`, confirm the named ground is real and correctly applied. If
   `red-herring`, confirm it misleads on its own merits, without a tell
7. **Reveal material** — confirm the endgame can point at a specific juror
   ledger line and a specific evidence item to explain the outcome, either way

---

## 10. Sealing

Hold the case file in session state for the whole game. Structure it so
`/save` writes it verbatim and `/load` restores it without regeneration —
a reloaded case is the same case, including juror scores mid-trial.

The player sees, at setup, only: the charge, the defendant's name and the
one-line version of what they are accused of, the witness list, and their own
side's opening materials. Not the evidence table, not a ledger, not a roll.
