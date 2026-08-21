# Playing Judge

**Win condition: a fair, error-free trial.** Scored by bench review, not by
verdict. The player has no side and gains nothing from either outcome.

Load `objections.md` (especially §8) alongside this.

---

## 1. What is different about this seat

The player is not trying to win the case; both lawyers are AI, both running
pre-written game plans, and the trial proceeds substantially on its own. The
player's inputs are rulings, and the trial's shape is the consequence of them.

Two things follow:

- **The trial must have real pace.** Objections arrive from both sides at a
  realistic clip, motions come up, witnesses need controlling. A judge player
  who has nothing to do is not being tested
- **Rulings have teeth.** Wrongly admitted evidence does its full work on the
  jury; wrongly excluded evidence is gone. Never quietly correct a bad ruling,
  and never re-offer an item to give the player a second chance

Skip the AI judge disposition in `case-build.md` §8 entirely — the player is
the bench.

---

## 2. What the player rules on

- **Objections** from both sides, per the grounds list and the ruling flow in
  `objections.md`
- **Admissibility of evidence** when offered, including the `excludable` item
  if that complication is live. This is usually the trial's pivot for this seat
- **Motions**: at minimum a motion in limine before opening, a motion to suppress
  if the case carries a suppression-type `excludable` defect, and a motion for
  directed verdict / judgment of acquittal after the prosecution rests. The
  suppression motion is usually this seat's pivot — decided on the warrant's
  four corners before the jury has heard a word, and the ruling shapes everything
  after it
- **Courtroom control**: a lawyer badgering a witness, a witness refusing to
  answer, speaking objections, a lawyer arguing after a ruling
- **Jury instructions** at the close — which instructions to give, and whether
  to give a curative instruction after struck testimony

---

## 3. How the room behaves toward a judge player

- **Present rule requests flat.** No hinting, no leading, no "counsel makes a
  compelling point." State the objection and the grounds, and stop
- **Never confirm a ruling was right.** No "correct" and no wince. Lawyers
  react in character — a lawyer who lost a ruling they expected to win may
  look surprised, which is information, but never a verdict on the ruling
- **Both sides test the bench.** Each lawyer's plan should include at least
  one borderline offer designed to see what the player will tolerate. If the
  player lets one side get away with something, that side's plan escalates in
  the same direction — which is how inconsistency punishes itself
- **Offers of proof.** After an adverse ruling, counsel may ask to make a
  record. A player who refuses takes a fairness hit in the review
- **The one exception, Rookie only:** a single teaching nudge across the whole
  trial — a clerk's murmured note, or counsel citing the actual rule in
  argument — before the player rules. Once. Never on Standard or Elite

---

## 4. The ruling log

Log every ruling as it happens. This is the entire basis of the bench review,
so log it precisely:

```
#7  Prosecution offers Ex.4 (bank records). Defense: chain of custody.
    Correct call: overruled — gap goes to weight, foundation adequate.
    Player ruled: sustained. Item excluded.
    Consequence: prosecution loses its clearest paper link.
    Flag: incorrect — exclusion of admissible evidence, prejudicial to state.
```

Also track, per ruling: which side raised it, and whether the same posture
arose for the other side. **Consistency is measured pairwise** — find the
matched pairs and compare.

---

## 5. Bench review

Delivered at the end in place of a win/loss, after the verdict. Four
dimensions, each scored and each explained with specific ruling numbers.

**1. Correctness** — what fraction of rulings matched the correct call.
Report the count, then walk the incorrect ones: what the rule was, what the
player did, and what it cost.

**2. Consistency** — the heavier metric. For each matched pair of comparable
rulings, did the player rule the same way regardless of who asked? A judge
who is 70% correct but perfectly even-handed scores better here than one who
is 85% correct with a visible tilt. Name the tilt if there is one, and name
the pairs that show it.

**3. Trial fairness** — did both sides get to put on their case? Was the
record preserved? Were offers of proof allowed? Was the jury properly
instructed? Did courtroom control hold without the bench taking over the
examination?

**4. Reversible error** — the sharp one. List every ruling that would
plausibly be reversed on appeal, and name the appellant. A trial with a
conviction and two reversible errors is a **loss for this seat**, and should
be stated that way.

The overall result is one of the following. **Check them in order and take the
first that applies** — a trial can be both tilted and reversible, and when it is,
reversible is what it gets called:

- **Reversible** — one or more errors that would not survive appeal. Name each
  one and name the appellant. A loss regardless of anything else in the review
- **Tilted** — no reversible error, but the rulings were defensible one at a
  time while favoring one side in aggregate. Name the side and cite the matched
  pairs that show it
- **Sound but appealable** — even-handed and substantially correct, with one
  identifiable error an appellate court would probably let stand
- **Clean record** — no reversible error, consistency holds, both sides got
  their case in. The trial neither side could credibly appeal. This is the win

Rough correctness bands, offered as context rather than as the score: **above 85%**
is a bench that knows the rules; **70–85%** is workable, and normal for a first
trial; **below 70%** means the rulings were shaping the trial more than the evidence
was. Consistency and reversible error override the band in both directions — a
90%-correct bench that denied a party proper cross-examination is Reversible, and
the review says so plainly.

State the verdict the jury reached, then make clear it does not factor into
the score. A judge who presided badly over a trial that reached the "right"
answer has lost.

---

## 6. Then the reveal

Bench review comes first, then the standard endgame reveal from `endgame.md` —
including ground truth. For this seat the reveal has a specific sting worth
landing plainly: whether the player's rulings, correct or not, helped the
trial arrive at the truth or away from it. Those two things are independent,
and that is the point of the seat.
