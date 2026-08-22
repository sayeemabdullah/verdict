# Roadmap

What Verdict does not do yet, and the design questions still open. Extracted
from the original build spec so the intent survives the spec itself.

## Shipped

Three criminal case categories, each rolled with independent guilt, case
strength, and evidence complication:

- **Homicide** — the richest evidence table
- **Assault / self-defense** — the act is not in dispute, the justification is
- **Theft / fraud / embezzlement** — paper-trail heavy

All four seats (defense, prosecution, judge, witness) at three difficulties.

## Next: civil cases

The current engine assumes a criminal trial throughout — beyond reasonable
doubt, a unanimous twelve, conviction or acquittal. Civil work needs a
different spine, not just different stories:

- **Wrongful death / malpractice** — preponderance of the evidence rather than
  beyond reasonable doubt, and damages rather than jail. The endgame stops
  being binary, which `endgame.md` and `jury.md` both currently assume
- **Contract / business dispute** — no crime and no moral center. Tests whether
  the game holds up when there is nobody to sympathize with
- **Defamation** — argument-heavy and light on physical evidence, which leans
  hard on the parts of the jury system that are least about evidence

The blocking piece is the burden of proof. `jury.md`'s scoring is built around
unanimity for conviction; preponderance means a majority and a different
verdict-resolution rule.

## Next: structural variants

- **Custody / family dispute** — decided by a single judge instead of twelve
  jurors. Removes the jury system entirely and puts everything on one
  ledger, which is either a much tighter game or a much thinner one. Worth
  building to find out
- **Appeal mode** — trying the fairness of a prior trial rather than the facts
  of a case. The Judge seat's natural home, and the one variant that would
  give that seat something to do besides rule on objections. Would reuse the
  bench-review logic in `trial-judge.md` as the thing under examination rather
  than the thing produced at the end

## Open design questions

- **Should opposing counsel's aggressiveness be telegraphed at setup?** Telling
  the player "you are facing a sharp DA" makes difficulty legible before the
  first ruling. Leaving it to be discovered makes the first cross-examination
  mean more. Currently undisclosed — `setup.md` gives the player counsel's name
  and manner but not their sharpness
- **Is the hung jury weighted correctly?** It is written as a real ending with
  its own consequences, and the fence-sitter rule in `jury.md` keeps it from
  being the default outcome. Whether it still lands too often is a play
  question, not a design one, and needs real sessions to answer
- **Does the Witness seat need a second act?** It is the most novel seat and
  the shortest — the player is on the stand and then they are not. Redirect
  is currently the only repair mechanism

## Testing

The four pre-launch cases in the original spec have been run; see
[PR #1](https://github.com/sayeemabdullah/verdict/pull/1) for what they found.
They are worth keeping as regression fixtures when the civil categories land,
since they exercise every mechanic the criminal engine has.
