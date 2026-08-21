# Verdict — How to Play

A courtroom drama where you take one seat in the room, and Claude runs
everyone else — opposing counsel, the judge, all twelve jurors, every
witness — each of them reasoning from their own private knowledge, not from
what you know or what Claude the narrator knows. The case is real and fixed
before you say a word. Nobody bends it to let you win.

---

## 1. Starting a case

Type **`/case`** (or just say "let's play" / "start a case").

You'll be asked two things:

**What seat do you want?**

| Role | You're playing | You win by |
|---|---|---|
| **Defense lawyer** | The person fighting for acquittal | Getting your client off — whether or not they're actually innocent |
| **Prosecutor** | The person building the case against the defendant | Getting a conviction, beyond reasonable doubt |
| **Judge** | The referee — no stake in the outcome | Running a fair trial: correct rulings, no reversible error |
| **Witness** | Someone who was there | Getting through cross-examination without your story falling apart |

**How hard?**

| Difficulty | What changes |
|---|---|
| **Rookie** | Opposing counsel makes real mistakes; jurors are easy to read |
| **Standard** | Opposing counsel plays it straight and competent; some jurors are genuinely hard to read |
| **Elite** | Opposing counsel plays to win — exploits every opening; some jurors send visible signals that don't match what's actually convincing them |

Once you answer both, a full case gets built — a crime, a defendant, real
evidence, real people — and locked. It does not change after this point, no
matter how the trial goes. You're about to walk into something that already
happened; your job is to work with it, not guess what Claude wants to hear.

---

## 2. What winning actually means, per role

This is the part people miss: **the goal is not the same for everyone**, and
it's not "find out who really did it."

- **Defense**: your client's actual guilt is irrelevant to victory. A guilty
  client and a clean acquittal is a *good* outcome for this role, not a
  cheat. You're managing what the jury gets to hear cleanly, not uncovering
  truth.
- **Prosecution**: you carry the burden. "Probably guilty" isn't enough —
  you need beyond reasonable doubt, built from admissible evidence and
  testimony that holds up under the defense's cross.
- **Judge**: you don't care who wins. You're graded afterward on whether
  your rulings were correct and consistent — a fair trial you presided over
  badly is a loss even if the "right" side won.
- **Witness**: you have one true account. Your only job is surviving
  hostile questioning without contradicting yourself or revealing more than
  you meant to. You don't control the room at all — this is the tensest
  seat.

---

## 3. Commands

| Command | What it does |
|---|---|
| `/ask <person> about <topic>` | Question a witness or suspect |
| `/press <person>` | Push harder on something they said — costs a little goodwill |
| `/examine <thing>` | Closely inspect a piece of evidence |
| `/object <grounds>` | Raise an objection during testimony (see grounds table below) |
| `/theory` | Say your current read on the case out loud and get an honest response on where it's strong or thin — free, doesn't cost a turn |
| `/notebook` | Pull up everything you've legitimately learned so far: evidence, timeline, witness notes |
| `/accuse <person>` | (non-trial modes only) End the case on an accusation |
| `/hint` | Get a nudge if you're stuck — has a small cost |
| `/save` | Save your progress to resume later |
| `/load` | Resume a saved case |

Plain English works fine too — "let me talk to the witness again" gets read
as `/ask`. You don't need to memorize syntax to play.

---

## 4. How a trial actually unfolds

1. **Opening statements** — each side lays out their theory of the case.
   Say something in your opening and contradict it later, and sharp jurors
   will notice.
2. **Case-in-chief** — the side with the burden (prosecution in criminal
   cases) presents its witnesses and evidence first, through friendly
   questioning.
3. **Cross-examination** — the other side gets the same witness. This is
   where contradictions get found and doubt gets built. If you're the
   Witness, this is the part where things get uncomfortable.
4. **Objections** — live throughout both of the above. See below.
5. **Closing arguments** — your last chance to reframe everything the jury
   heard.
6. **Deliberation** — you don't get to watch. You'll get a few overheard
   fragments, not a transcript, not a headcount.
7. **Verdict** — conviction, acquittal, or (in criminal cases) a hung jury,
   which is a real and distinct outcome, not just "you didn't win."
8. **The reveal** — after the verdict, you get to see what actually
   happened, replayed from the other side's point of view. This is where
   you find out exactly where your read was right and where you got lucky.

---

## 5. Objections, if you're a lawyer

Objections are the one part of this game with a genuinely correct answer in
the moment. Naming the right grounds matters — both what you object to and
why.

| Say this | When it applies |
|---|---|
| **Hearsay** | Witness repeats what someone else said, to prove that thing is true |
| **Relevance** | The question doesn't bear on anything actually at issue |
| **Leading** | On direct examination, a question that feeds its own answer |
| **Speculation** | Asking someone to guess at something they couldn't know |
| **Badgering** | The lawyer is arguing with the witness, not questioning them |
| **Assumes facts not in evidence** | The question presumes something never established |
| **Compound question** | Two questions bundled as one |
| **Chain of custody** | Physical evidence introduced without a clean handling trail |
| **Privilege** | Attorney-client, doctor-patient, spousal, etc. |

A few things worth knowing before you play:

- **The window is short.** If you don't object in time, the moment passes —
  no going back for it later.
- **Wrong grounds get overruled**, even if a right ground existed. Naming it
  correctly is the actual skill here.
- **Objecting constantly backfires.** A lawyer who objects to everything
  starts losing credibility with the jury, whether or not each individual
  call was correct.
- **Sustained doesn't mean forgotten.** The jury's told to disregard it, but
  real people don't fully un-hear things — some jurors will still be a
  little swayed by testimony that got struck, depending on who they are.

---

## 6. The jury — what you can and can't know

Twelve people. You never see their private leanings, their scores, or
anything resembling a running tally — no "the jury seems convinced" from
Claude, ever, during the trial itself.

What you *can* pick up on:
- **Body language during testimony** — leaning in, arms crossed, note-taking,
  glances at the defendant
- **Deliberation fragments** afterward — a few overheard lines, a sense of
  the room's temperature, not a verdict preview

On Elite difficulty, be aware: a juror's visible reaction and what's
actually moving them internally can be two different things. Reading a room
correctly is part of the challenge, not a solved problem.

---

## 7. If you're playing Witness

This is the most exposed seat. You know the truth — your version of it,
anyway, including its real limits, since nobody sees everything. Your job
during direct examination (friendly questions from whoever called you) is
straightforward. Cross-examination is where it gets hard: the opposing
lawyer is trying to find the place where your story bends. Staying
consistent, saying only what you actually know, and not overexplaining under
pressure are your real tools. There's no "win the argument" here — there's
just holding your ground.

---

## 8. If you're playing Judge

You have no side. Your only job is ruling correctly and consistently on
objections from both lawyers — same standard applied evenly, regardless of
who's asking. At the end, instead of a verdict, you get a bench review:
were your rulings correct, were they consistent, did the trial stay fair. A
"win" here looks like a trial neither side could credibly appeal.

---

## 9. Saving and resuming

`/save` at any point to pause. `/load` to pick back up later — the case
state resumes exactly where you left it, and nothing about the locked case
changes in the meantime. If you're mid-trial, the jury's private leanings
and everyone's ledgers persist too; time away from the game doesn't reset
anything.

---

## 10. A few honest notes before you start

- **You can lose, and losing is meant to feel earned.** The reveal will show
  you exactly where the gap was — a juror never fully reached, a piece of
  evidence left unexamined, a contradiction the other side found first. It's
  built to teach you something, not just tell you "you lost."
- **A hung jury is a real outcome**, not a soft loss. Treat it as its own
  ending.
- **Difficulty doesn't just make the AI meaner** — Elite specifically means
  opposing counsel is playing tactically and the jury is harder to read
  honestly, not that the dice are loaded against you.
- **Nothing is improvised against you.** Opposing counsel's whole game plan
  — their opening, their objections, their best and weakest moments — was
  written down before the trial started. If you win, you beat something
  real, not something that got easier because you were struggling.

That's everything you need. Type `/case` when you're ready.
