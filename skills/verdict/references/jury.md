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

## 4. Deliberation

The player does not attend. They get fragments — overheard through a door,
across a hallway, secondhand from the bailiff.

Generate deliberation from the actual scores, then release **4–8 fragments**
over the course of it. Each fragment must:

- Come from a specific juror and sound like their ledger — their vocabulary,
  their concerns, their bias speaking without naming itself
- Reference something that actually happened at trial
- Reveal **partial** information. A juror arguing hard for one side tells you
  about that juror, not about the room

Never provide:

- A headcount, a split, or "they're leaning toward…"
- A complete argument chain start to finish
- A juror's private bias stated openly
- Foreshadowing of the verdict

Deliberation can **move scores** — jurors argue each other around, but only
along ledger lines. A juror persuaded by physical evidence can be pulled by
another juror's better reading of the physical evidence; they cannot be pulled
by an emotional appeal they would have discounted in the courtroom. Cap
deliberation movement at ±2 per juror.

**Resolve the fence-sitters.** Any juror sitting at exactly 0 when deliberation
opens gets argued at by the room, and moves to ±1 in the direction of the
room's weight — *provided* some juror in the majority makes an argument that
lands on the fence-sitter's own ledger. This step is not optional bookkeeping. With
twelve jurors each needing to clear ±1, a trial left alone will hang almost
every time on arithmetic rather than on conviction, and a game whose modal ending
is "no ending" is broken. Deliberation is the release valve.

**Then let genuine holdouts hold.** A juror whose ledger the winning side never
reached does not get argued around, however lopsided the room, and a fence-sitter
nobody can reach on their own terms stays at 0. One juror at −2 against eleven
at +3 is a hung jury and must be written as one.

Give the player a beat of silence between the last fragment and the verdict.

---

## 5. Verdict resolution

**Criminal cases (all three launch categories):**

- **Conviction** requires all twelve at **+1 or higher**
- **Acquittal** requires all twelve at **−1 or lower**
- Anything else — including any juror sitting at exactly 0 after
  deliberation — is a **hung jury**

Do not nudge a stray juror to make a clean ending. A hung jury on an 11–1
split is the correct outcome and a better story than a manufactured
unanimity.

**Writing the hung jury.** It is a distinct, fully-weighted ending, not a
consolation prize. It carries its own consequences and should be written to
land:

- The judge declares a mistrial after the jury reports deadlock
- The defendant walks out *today*, with the case unresolved — and the
  prosecution's decision whether to retry is a real, stated question
- For **Defense**: a partial win. The client is not convicted, but not free
  of it either
- For **Prosecution**: a partial loss with a road back — and the endgame
  should name which juror or jurors held, and what would have reached them
- The reveal treats it as its own thing, not as a near-miss of a real ending

---

## 6. Handing off to the endgame

Pass to `endgame.md`:

- Final score for each juror, with their full movement log
- The specific ledger line that decided each juror's final position
- Every evidence item's final state, and which jurors it did and did not
  reach
- For a hung jury: the holdouts, and the specific thing that would have moved
  them
- Elite: which jurors were false-signal, and where the player read them wrong
