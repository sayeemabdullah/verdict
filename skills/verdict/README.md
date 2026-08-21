# Verdict

A courtroom drama where you take one seat in the room and Claude plays
everyone else — opposing counsel, the judge, all twelve jurors, every witness
— each of them reasoning from their own private knowledge rather than from
what you know. The case is built and locked before you say a word, and
nothing about it bends to let you win.

Type **`/case`** to start.

---

## Starting

`/case` asks you two things.

**What seat do you want?**

| Role | You play | You win by |
|---|---|---|
| **Defense lawyer** | The person fighting for acquittal | Getting your client off — whether or not they are actually innocent |
| **Prosecutor** | The person building the case against the defendant | A conviction, beyond reasonable doubt |
| **Judge** | The referee, with no stake in the outcome | Running a fair trial: correct rulings, no reversible error |
| **Witness** | Someone who was there | Getting through cross-examination without your story falling apart |

**How hard?**

| Difficulty | What changes |
|---|---|
| **Rookie** | Opposing counsel makes real mistakes; jurors are easy to read; the bench will nudge you once |
| **Standard** | Opposing counsel plays it straight and competent; some jurors are genuinely hard to read |
| **Elite** | Opposing counsel plays to win and exploits every opening; some jurors' visible reactions do not match what is actually convincing them |

Role and difficulty are independent — any combination works. Then a full case
gets generated: a crime, a defendant, real evidence, real people, all of it
sealed. It does not change after that point.

New to it? Defense on Standard is the most forgiving first game.

---

## What winning means, per seat

This is the part people miss. **The goal is not the same for everyone**, and
it is never "find out who really did it."

- **Defense** — your client's actual guilt is irrelevant to victory. A guilty
  client and a clean acquittal is a *good* outcome for this seat, not a cheat.
  You are managing what the jury gets to hear cleanly, not uncovering truth.
  You never have to prove anything or offer a theory of your own
- **Prosecution** — you carry the burden, and it is the hardest seat.
  "Probably guilty" is not enough. You need all twelve, built from admissible
  evidence and testimony that survives cross. What you personally believe
  about the defendant is worth nothing
- **Judge** — you do not care who wins. Afterward you get a bench review
  instead of a verdict: were your rulings correct, were they *consistent*
  between the two sides, did the trial stay fair. A trial that reached the
  "right" answer but was presided over badly is a loss
- **Witness** — you have one true account, including its real limits, since
  nobody sees everything. Your job is surviving hostile questioning without
  contradicting yourself or saying more than you meant to. You have no control
  over the room at all. This is the tensest seat

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

Plain English works fine throughout. "Let me talk to the witness again" is
read as `/ask`. You never need to memorize syntax.

---

## How a trial unfolds

0. **Pretrial motions** — before anyone speaks to the jury, if there is
   anything to argue: whether a piece of evidence comes in at all. Some cases turn
   here, before the trial has really started
1. **Opening statements** — each side lays out its theory. Promise something
   here and fail to deliver it later, and the jurors who noticed will hold it
   against you
2. **Case-in-chief** — the side with the burden presents its witnesses first,
   through friendly questioning
3. **Cross-examination** — the other side gets the same witness. Where
   contradictions get found and doubt gets built
4. **Objections** — live throughout both of the above
5. **Closing arguments** — your last chance to reframe everything the jury
   heard. Struck testimony is off limits
6. **Deliberation** — you do not get to watch. A few overheard fragments, no
   transcript, no headcount
7. **Verdict** — conviction, acquittal, or a hung jury, which is a real and
   distinct ending rather than "you didn't win"
8. **The reveal** — what actually happened, replayed from the other side,
   showing exactly where your read was right and where you got lucky

---

## Objections

The one part of the game with a genuinely correct answer in the moment.

| Say this | When it applies |
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

Four things worth knowing before you play:

- **The window is short.** Miss it and the moment is gone — no going back
- **Wrong grounds get overruled**, even when a right ground existed. Naming it
  correctly is the actual skill
- **Objecting constantly backfires.** A lawyer who objects to everything loses
  credibility with the jury regardless of whether each call was right
- **Sustained does not mean forgotten.** The jury is told to disregard, but
  real people do not fully un-hear things. How much sticks depends on the
  individual juror
- **Some fights happen before the trial.** If evidence was seized badly — a bad
  warrant, a search that went past what it authorised — that gets argued in
  pretrial motions, not by objecting mid-testimony. There is no "objection,
  illegal search"

---

## The jury

Twelve people. You never see their leanings, their scores, or anything like a
running tally — no "the jury seems convinced," ever, during the trial.

What you can pick up on is body language: leaning in, arms crossed, note-taking
that stops, a glance at the defendant. And afterward, a few deliberation
fragments — not a preview of the verdict.

On **Elite**, be careful: a juror's visible reaction and what is actually
moving them can be two different things. Reading the room is part of the
challenge, not a solved problem.

Criminal cases need all twelve to convict. Anything else is a hung jury.

---

## Saving

`/save` at any point to pause; `/load` to pick back up. The case resumes
exactly where you left it — the jury's private leanings, everyone's ledgers,
the evidence, all of it persists. Time away resets nothing and re-rolls
nothing.

---

## A few honest notes

- **You can lose, and losing is meant to feel earned.** The reveal shows you
  exactly where the gap was — a juror never reached, evidence left unexamined,
  a contradiction the other side found first
- **A hung jury is a real outcome**, with its own ending, not a soft loss
- **Nothing is improvised against you.** Opposing counsel's whole game plan —
  their opening, their objections, their best and weakest moments — was
  written down before the trial started, and you get to see it at the end. If
  you win, you beat something real

Type `/case` when you are ready.
