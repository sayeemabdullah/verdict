# Setup — role, difficulty, case generation

Runs on `/case`, or on any plain-English start ("let's play", "start a
case", "I want to be a defense lawyer"). Keep it short — two questions and a
case. Do not explain the rules up front; the game teaches itself in play.

---

## 1. Open

Two or three sentences of frame, no more. Something like: you take one seat
in a courtroom, everyone else is played by Claude from their own private
knowledge, and the case is built and locked before you say a word.

Then ask both questions. If the player already named a role or difficulty in
their message, take it and only ask what is missing.

---

## 2. Question one — the seat

Present all four with their win conditions, because the win condition is the
choice:

| Role | You play | You win by |
|---|---|---|
| **Defense lawyer** | The person fighting for acquittal | Getting your client off — whether or not they are actually innocent |
| **Prosecutor** | The person building the case | A conviction, beyond reasonable doubt |
| **Judge** | The referee — no stake in the outcome | A fair trial: correct rulings, no reversible error |
| **Witness** | Someone who was there | Getting through cross without your story falling apart |

Worth adding, briefly, since players consistently misread it: the goal is not
the same for every seat, and none of them is "find out who really did it."

If the player asks which to pick: Defense is the most forgiving first game,
Prosecution the hardest, Witness the most unusual.

---

## 3. Question two — difficulty

| Difficulty | What changes |
|---|---|
| **Rookie** | Opposing counsel makes real mistakes; jurors are easy to read; one teaching nudge from the bench |
| **Standard** | Opposing counsel plays it straight and competent; some jurors are genuinely hard to read |
| **Elite** | Opposing counsel plays to win and exploits every opening; some jurors' visible reactions do not match what is actually moving them |

Role and difficulty are independent — any combination is valid.

Difficulty sets three dials at once: opposing counsel's sharpness, jury
legibility, and judge strictness (or, for Witness, the cross-examiner's
sharpness). Set all of them from the one answer.

---

## 4. Category

Do not ask. Roll it — `homicide`, `assault-self-defense`, or `theft-fraud` —
unless the player names one unprompted, in which case use it.

---

## 5. Generate

Run `case-build.md` end to end, silently. Roll every dial, write ground
truth, cast, build the evidence table, write every witness and juror ledger,
write opposing counsel's plan and the judge's disposition, and run all seven
sanity checks before sealing.

Do not narrate generation. Do not stream partial case details. One brief line
that the case is being built, then the briefing.

---

## 6. The briefing

What the player sees, and nothing beyond it:

- **The charge** and the defendant's name
- **One paragraph** of what they are accused of — the version their own side
  would tell
- **The witness list**, names and one line each on who they are
- **Their own materials**, which differ by seat:
  - *Defense* — their client's account, told from the defendant's own ledger,
    including any lies that ledger contains
  - *Prosecution* — the case file as investigated: evidence in hand, with its
    gaps
  - *Judge* — the charge, both sides' counsel, and any pretrial motions filed
  - *Witness* — their full personal ledger, in their own voice, per
    `trial-witness.md` §1
- **Who is on the other side** — opposing counsel's name and courtroom manner.
  Their aggressiveness is not stated; the player discovers it in play

Never show: the evidence table's Truth axis, any juror ledger, any witness
ledger other than the player's own, opposing counsel's game plan, or anything
from ground truth.

---

## 7. Begin

Open the trial. Load the player's role file — `trial-defense.md`,
`trial-prosecution.md`, `trial-judge.md`, or `trial-witness.md` — plus
`objections.md` and `jury.md`, and run the trial from `SKILL.md` — starting at
phase 0 if the case carries a suppression-type `excludable` defect or either side
has a motion in limine, otherwise at phase 1.

Do not list the commands. `/notebook` and `/hint` exist if the player wants
them; plain English works throughout.
