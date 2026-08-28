# Jury — ledgers, persuasion, deliberation, verdict

Twelve sealed people. The player never sees a score, a ledger, or a tally.
They see bodies in a box and, at the end, fragments through a door.

---

## 1. The ledger

Format and content requirements are in `case-build.md` §6. What matters here
is how a ledger is *used*.

A juror ledger is the **only** authority for that juror's movement. A juror
may be moved by:

- Evidence or testimony that hits their `Persuaded by` axis
- A moment that engages their `Private bias`, specifically
- Credibility damage to a lawyer they were inclined toward
- Something they saw with their own eyes in the courtroom — a witness
  faltering, a defendant's reaction, a lawyer losing the bench

A juror may **never** be moved by:

- An argument being "strong" or "well-made" in the abstract
- Anything that matches no line in their own ledger
- Ground truth, or anything only Claude and the sealed file know
- What a *different* juror found persuasive
- The narrative need for the trial to be close, or for the player to be
  rewarded for effort

If an argument lands on nothing in a juror's ledger, that juror does not move.
Twelve people who all move together are one person with twelve faces.

---

## 2. Scoring

Each juror holds an integer from **−5 (firm acquit)** to **+5 (firm
convict)**, starting at 0.

Per-moment movement:

| Magnitude | When |
|---|---|
| **±1** | The moment touches their `Persuaded by` axis in the ordinary course |
| **±2** | The moment hits their `Private bias` directly, or lands a genuine contradiction on a witness they had been believing |
| **±3** | Rare. A witness breaks on the stand; a central evidence item is destroyed or established outright. At most two or three times in a whole trial |

Constraints:

- **Movement per juror per phase is capped at ±3 net.** Net, not per direction:
  a juror moved +2 and then −1 in the same phase has spent 3 of their budget,
  not 1. No single dramatic closing swings the box
- **Cross-examination is phase 3, not phase 2**, even though it happens inside the
  other side's case. A juror can therefore move +3 while a witness is put up and
  −3 while that same witness is taken apart. This is what makes a case
  recoverable — do not collapse direct and cross into one phase budget, or a
  side that has a bad case-in-chief can never climb back
- **A juror at ±5 is not immovable, but takes ±3-magnitude work to shift.**
  Late reversals should be possible and expensive
- Scores below −2 or above +2 create *inertia*: subsequent contrary moments
  move them at half magnitude, rounded toward zero. People dig in. Note what this
  implies and treat it as intended: a ±1 moment halves to 0, so a dug-in juror
  is untouched by ordinary persuasion and can only be moved by a ±2 or ±3
  moment aimed squarely at their own ledger
- Log every movement with the juror, the magnitude, the moment, and **the
  ledger line that justified it.** If you cannot name the ledger line, the
  movement is illegal — do not make it. This log is what the endgame reveal
  reads off

Struck testimony decays per `objections.md` §5, applied against the movement
it originally caused.

---

## 3. What the player is allowed to perceive

**Never** during trial:

- A score, a count, a tally, a range, or a direction
- "The jury seems convinced" / "you're losing them" / "that landed well"
- Any statement of how the verdict is trending
- A juror's ledger content stated as fact

**Allowed**, and the only channel available: physical reaction, described
plainly and without interpretation.

> Juror 4 stops taking notes.
> The woman in the second row glances at the defendant, then away.
> Juror 9 has been looking at the clock since the second exhibit.

Rules for reactions:

- Describe the behavior; never gloss it. "Juror 7 folds his arms" — not
  "Juror 7 folds his arms, unconvinced"
- Reactions fire only for jurors who **actually moved** on that moment, or —
  Elite only — for a `false-signal` juror doing the opposite of what they feel
- Rate-limit to **one or two per beat.** A courtroom where every juror
  reacts to everything is noise, and noise is unreadable, which is the same
  as showing nothing
- The same juror reacting the same way twice is meaningful. Keep each
  juror's physical vocabulary consistent all trial — it is the player's only
  handhold

**False-signal jurors (Elite only):** their visible reaction is generated
from the *opposite* of their real movement, consistently, all trial. Never
break the illusion, never hint, and never let the reveal make it feel like a
cheat — the reveal names them and shows their real log, which is the payoff.

---

## 4. Handing off

Deliberation, verdict resolution, and the hung-jury rules live in `endgame.md`,
which loads once the closing arguments are done. They are not needed while the
trial is running; scoring is.

When you hand off, pass: every juror's final score and full movement log, the
ledger line that decided each one, every evidence item's final state and which
jurors it did and did not reach, the holdouts and what would have moved them if
the jury hung, and — on Elite — which jurors were false-signal and where the
player misread them.
