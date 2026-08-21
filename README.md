# Verdict

**A playable courtroom drama for [Claude Code](https://claude.com/claude-code).**

You take one seat in the room. Claude plays everyone else — opposing counsel,
the judge, all twelve jurors, every witness — and each of them reasons only
from their own sealed private knowledge, not from what you know and not from
what Claude the narrator knows.

The case is generated and locked before you say a word. What actually happened,
and whether the defendant actually did it, is decided up front and never
changes to fit how the trial is going. Nobody bends it to let you win.

```
/case
```

---

## What makes it a game

Most AI roleplay bends toward you. It notices you struggling and gets easier;
it notices you doing well and produces a satisfying reversal. Verdict is built
so that it can't.

**The truth is sealed before play.** Guilt, evidence, and every person's
private knowledge are rolled and written down at case generation, then never
revisited. Claude is instructed not to retcon the ground truth in either
direction — not to rescue you, not to check you.

**Nobody knows what they shouldn't.** Every AI participant gets a private
ledger: what they actually know, what moves them, what bias they carry, what
they will never say. A witness doesn't know what another witness saw. A juror
doesn't know what's on the evidence table. Opposing counsel doesn't know the
truth. Leakage between ledgers is the design's cardinal sin, and every
reference file is written around preventing it.

**Opposing counsel plays a written plan.** Their opening theory, their planned
objections, their strongest moment, and a specific reachable weakest moment
are all written down before the trial starts — so difficulty stays consistent
instead of drifting toward whatever you happen to need. You get to read that
plan at the end. If you win, you beat something real.

**You never see the machinery.** No scores, no tallies, no "the jury seems
convinced." The jury is visible only as twelve people with body language, and
afterward as a few fragments overheard through a door.

---

## Install

Verdict is distributed as a Claude Code plugin. From inside Claude Code:

```
/plugin marketplace add sayeemabdullah/verdict
/plugin install verdict@verdict
```

Then start a case:

```
/case
```

To update later, `/plugin marketplace update verdict`. To remove it,
`/plugin uninstall verdict`.

<details>
<summary>Installing from a local clone instead</summary>

```bash
git clone https://github.com/sayeemabdullah/verdict.git
```

Then, in Claude Code:

```
/plugin marketplace add ./verdict
/plugin install verdict@verdict
```

</details>

---

## Choosing your seat

`/case` asks you two things. The first is which seat you want — and since the
win condition is different for every seat, that choice is the whole game.

| Role | You play | You win by |
|---|---|---|
| **Defense lawyer** | The person fighting for acquittal | Getting your client off — whether or not they are actually innocent |
| **Prosecutor** | The person building the case | A conviction, beyond reasonable doubt |
| **Judge** | The referee, with no stake in the outcome | A fair trial: correct rulings, no reversible error |
| **Witness** | Someone who was there | Getting through cross-examination without your story falling apart |

This is the part people misread: **the goal is not "find out who really did
it."** It is never that, for anyone.

- **Defense** — your client's actual guilt is irrelevant to victory. A guilty
  client and a clean acquittal is a *good* outcome for this seat, and the game
  says so without irony. You are managing what the jury gets to hear cleanly.
  You never have to prove anything, offer a theory, or put your client on the
  stand
- **Prosecution** — the hardest seat. You need all twelve jurors, built only
  from admissible evidence that survives cross. What you personally believe
  about the defendant is worth nothing. And if you build a strong case against
  an innocent person and win, you have won — and then you find out
- **Judge** — you don't care who wins. Afterward you get a bench review
  instead of a verdict: were your rulings correct, were they *consistent*
  between the two sides, did the trial stay fair. A trial that reached the
  "right" answer but was presided over badly is a loss
- **Witness** — the most exposed seat. You have one true account, including
  its real limits, since nobody sees everything — and it may contain things
  you sincerely believe that are simply wrong. You have no control over the
  room at all

New to it? **Defense on Standard** is the most forgiving first game.

## Choosing difficulty

| Difficulty | What changes |
|---|---|
| **Rookie** | Opposing counsel makes real mistakes; jurors are easy to read; the bench will nudge you once |
| **Standard** | Opposing counsel plays it straight and competent; some jurors are genuinely hard to read |
| **Elite** | Opposing counsel plays to win and exploits every opening; some jurors' visible reactions do not match what is actually convincing them |

Role and difficulty are independent — any combination works. Difficulty is not
"the AI is meaner." It sets opposing counsel's sharpness, how legible the jury
is, and how strict the bench is, and nothing else.

The **case category** is rolled for you: homicide, assault / self-defense, or
theft, fraud and embezzlement. So are the things that actually matter — whether
the defendant did it, how strong the case is, and whether the evidence carries
a technicality or a red herring.

---

## How a trial unfolds

0. **Pretrial motions** — before anyone speaks to the jury, if there is
   anything to argue: whether a piece of evidence comes in at all. Some cases
   turn here, before the trial has really started
1. **Opening statements** — each side lays out its theory. Promise something
   here and fail to deliver it later, and the jurors who noticed will hold it
   against you
2. **Case-in-chief** — the side with the burden presents its witnesses first,
   through friendly questioning
3. **Cross-examination** — the other side gets the same witness. Where
   contradictions get found and doubt gets built
4. **Objections** — live throughout both of the above
5. **Closing arguments** — your last reframe. Struck testimony is off limits
6. **Deliberation** — you don't get to watch. A few overheard fragments, no
   transcript, no headcount
7. **Verdict** — conviction, acquittal, or a hung jury, which is a real and
   distinct ending rather than "you didn't win"
8. **The reveal** — what actually happened, replayed from the other side,
   showing exactly where your read was right and where you got lucky

---

## Commands

| Command | What it does |
|---|---|
| `/case` | Start a new case |
| `/ask <person> about <topic>` | Question a witness or other person |
| `/press <person>` | Push harder on what they just said — costs a little goodwill |
| `/examine <thing>` | Closely inspect a piece of evidence |
| `/object <grounds>` | Raise an objection during testimony |
| `/theory` | Say your current read out loud and get an honest response on where it is strong or thin — free, costs no turn |
| `/notebook` | Everything you have legitimately learned: evidence, timeline, witness notes, your own opening promises |
| `/accuse <person>` | End on an accusation (non-trial modes only) |
| `/hint` | A nudge if you are stuck — has a small cost |
| `/save` | Save your progress |
| `/load` | Resume a saved case |

**Plain English works throughout.** "Let me talk to the witness again" is read
as `/ask`. You never need to memorize syntax to play.

`/save` and `/load` persist the entire sealed case — the jury's private
leanings, everyone's ledgers, the evidence, the phase you were in. Time away
resets nothing and re-rolls nothing.

---

## Objections

The one part of the game with a genuinely correct answer in the moment.

| Ground | When it applies |
|---|---|
| **Hearsay** | The witness repeats what someone else said, to prove that thing is true |
| **Relevance** | The question bears on nothing actually at issue |
| **Leading** | On direct examination, a question that feeds its own answer |
| **Speculation** | Asking someone to guess at what they could not know |
| **Badgering** | Counsel is arguing with the witness, not questioning them |
| **Assumes facts not in evidence** | The question presumes something never established |
| **Compound question** | Two questions bundled as one |
| **Chain of custody** | Physical evidence offered without a clean handling trail |
| **Privilege** | Attorney-client, doctor-patient, spousal, clergy |

Five things worth knowing before you play:

- **The window is short.** Miss it and the moment is gone — no going back
- **Wrong grounds get overruled**, even when a right ground existed. Naming it
  correctly is the actual skill
- **Objecting constantly backfires.** A lawyer who objects to everything loses
  credibility with the jury regardless of whether each call was right
- **Sustained does not mean forgotten.** The jury is told to disregard, but
  real people do not fully un-hear things. How much sticks depends on the
  individual juror
- **Some fights happen before the trial.** If evidence was seized badly — a
  bad warrant, a search that went past what it authorized — that gets argued
  in pretrial motions. There is no "objection, illegal search"

---

## The jury

Twelve people. You never see their leanings, their scores, or anything like a
running tally — no "the jury seems convinced," ever, during the trial.

What you can pick up on is body language: leaning in, arms crossed, note-taking
that stops, a glance at the defendant. Each juror keeps a consistent physical
vocabulary all trial, and it is your only handhold.

On **Elite**, be careful: a juror's visible reaction and what is actually
moving them can be two different things. Reading the room is part of the
challenge, not a solved problem.

Criminal cases need all twelve to convict, and all twelve to acquit. Anything
else is a hung jury — a real ending with its own consequences, not a soft loss.

---

## Losing

You can lose, and losing is meant to feel earned rather than arbitrary.

The reveal is built to make it legible. It opens the sealed case file and shows
you the ground truth, the evidence table with the red herring finally marked,
the jurors who decided it with the specific moment that moved each one, and
opposing counsel's game plan exactly as it was written before the trial began —
including the weakest moment they had, and whether you ever found it.

"You lost because the jury wasn't convinced" is explicitly a failure of that
section. "Juror 3 needed a timeline she could follow and never got one — the
bank records would have given it to her, and they were admissible the whole
trial" is what it is for.

---

## Repo layout

```
.claude-plugin/
  plugin.json              plugin manifest
  marketplace.json         lets this repo be installed directly
commands/                  11 slash commands, thin entry points
skills/verdict/
  SKILL.md                 routing table, core loop, standing rules
  README.md                the in-plugin player guide
  references/
    setup.md               role and difficulty select
    case-build.md          building and sealing the case file
    objections.md          grounds, timing, rulings, credibility
    jury.md                ledgers, scoring, deliberation, verdict
    trial-defense.md       \
    trial-prosecution.md    | one per playable seat
    trial-judge.md          |
    trial-witness.md       /
    endgame.md             verdict, bench review, reveal
verdict-build-plan.md      the design spec this was built from
verdict-how-to-play.md     the player-facing spec
```

Reference files load only when their phase or role is active, so a trial never
carries all of them at once.

---

## Status

Version 0.1.0. The three criminal categories are built and playable. The four
pre-launch test cases have been run end to end; see
[PR #1](https://github.com/sayeemabdullah/verdict/pull/1) for what they found.

Designed for but not built: civil cases with a preponderance standard and
damages, custody disputes decided by a single judge instead of a jury, and an
appeal mode that tries the fairness of a prior trial — the Judge seat's natural
home.

## License

MIT. See [LICENSE](LICENSE).
