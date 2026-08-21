# Verdict — Build Plan for Claude Code

A playable courtroom drama **plugin**. One human plays a chosen role; every
other person in the room — opposing counsel, judge, jury, witnesses — is run
by Claude, each reasoning only from sealed knowledge the human never sees
directly.

This ships as a **plugin**, not a bare skill, because the game leans on real
slash commands (`/case`, `/object`, `/ask`, `/accuse`, etc.). A plugin bundles
commands (actual slash-command entry points) together with the skill
(instructions Claude reads once a command or the game context triggers it).
A bare skill can't register real slash commands on its own.

Give this whole file to Claude Code as the spec. It describes what to build,
not the finished prose of each file — write the actual plugin and skill
content fresh, using this as the source of truth for structure and rules.

---

## 1. Core Premise

The trial's ground truth (what actually happened, and whether the defendant
is actually guilty) is generated and locked before play starts and never
changes to fit how the game is going. The human picks a seat in the room and
plays toward that seat's own definition of winning — which is not always
"reveal the truth."

---

## 2. Playable Roles

| Role | Win condition | What makes it distinct |
|---|---|---|
| **Defense lawyer** | Acquittal | Truth is irrelevant to victory — reasonable doubt is the currency, even against a guilty client |
| **Prosecutor** | Conviction | Carries the burden of proof; builds a case from evidence rather than privileged knowledge |
| **Judge** | A fair, error-free trial (scored by bench review, not verdict) | No stake in outcome — a rules-enforcement role |
| **Witness** | Get through cross without your account fracturing or over-revealing | No control over the room — pure pressure, most novel role |

Role and difficulty are chosen independently at setup.

---

## 3. Difficulty Levels

Two dials move together: how sharp opposing counsel plays, and how legible
the jury is.

| Level | Opposing counsel | Jury |
|---|---|---|
| **Rookie** | Makes real mistakes — misses objections, leaves openings, overplays weak evidence | Simple ledgers, biases easy to read from questions asked |
| **Standard** | Competent, catches obvious errors, plays it straight | Full ledger complexity, some jurors genuinely hard to read |
| **Elite** | Plays to win — exploits inconsistencies, objects aggressively and tactically, reframes closings before the player gets there | Includes false-signal jurors: visible reactions don't match what's actually swaying them |

- **Judge strictness** scales as its own dial (harder to play *as* judge and
  harder to get away with borderline moves *against* a strict one).
- **Cross-examiner sharpness** scales separately for the Witness role.

---

## 4. Case Categories

Not a fixed list of stories — a set of shapes, each combined with
independently randomized guilt/innocence and evidence quality, so no category
plays the same way twice.

**Launch set (build these 3):**
1. **Homicide** — richest evidence table, classic whodunit stakes
2. **Assault / self-defense** — guilt of the act isn't in question, justification is
3. **Theft / fraud / embezzlement** — paper-trail heavy: financial records, digital footprints, chain-of-custody on documents

**V2 candidates (design for, don't build yet):**
4. Wrongful death / malpractice (civil — preponderance standard, damages not jail)
5. Contract / business dispute (civil — no crime, no moral center)
6. Defamation (argument-heavy, light on physical evidence)
7. Custody / family dispute (single judge instead of 12-person jury)
8. Wrongful conviction / appeal (trying the fairness of a prior trial — Judge's natural home)

**Per-case randomization, independent of category:**
- Actually guilty vs. actually innocent — decide first, never let anything downstream change it
- Strength of the case for whichever side the player isn't playing: strong / moderate / weak
- Evidence complication: clean / one excludable technicality / one seeded red herring (pick one, not several — stacking makes it incoherent rather than hard)

---

## 5. Core Systems

### Anti-leakage (the most important rule in the whole design)
Every AI participant — opposing counsel, each of 12 jurors, each witness —
gets a private, sealed ledger at case-generation time: what they actually
know, what argument style moves them, what bias they carry. During play, an
AI may only act on what's in its own ledger. Claude must never let one AI
participant behave as if it knows what only another AI participant (or the
hidden ground truth) knows.

### Evidence table
Every piece of evidence is tagged along three independent axes:
- **True or red herring** (seeded at generation, not improvised mid-game)
- **Admissible or excludable**, with a specific named reason (hearsay, chain
  of custody, relevance, privilege)
- **Persuasive or not, per juror** (resolved via jury ledgers during play)

This keeps "I found evidence" from collapsing into "I found the truth."

### Witness ledgers
One per witness: their true account (with real limits — people don't see
everything), how they tell it under friendly vs. hostile questioning, and
optionally a specific breaking point — a line of questioning that would make
them contradict themselves or lose composure. Not every witness needs one; a
witness with nothing to hide can simply be consistently truthful.

### Jury system (12 sealed jurors)
Each juror: a one-line sketch, what persuades them, what they discount, a
private bias (specific and generative, not vague), and — Elite only — a
false-signal juror or two whose visible reactions don't track their real
internal score.

Track a rough persuasion score per juror, moved only when something at trial
is traceable to that juror's own ledger — never because an argument was
"good in general" or because Claude knows something the juror doesn't. Never
show scores or ledgers to the player directly. Surface the jury only through
visible reactions during trial and fragmentary fingerprints during
deliberation — never a running tally, never a stated verdict prediction.

Verdict resolution: criminal cases require unanimity for conviction;
anything else is a hung jury, which should be written as a real, distinctly-
weighted ending, not a consolation prize.

### Objections (the mechanical spine — build this first and test it hardest)
Real grounds, named correctly: hearsay, relevance, leading, speculation,
badgering/argumentative, assumes facts not in evidence, compound question,
chain of custody, privilege. Don't invent grounds outside this list without
good reason.

Flow: objection raised with stated grounds → judge rules sustained/overruled
with a short in-character reason → if sustained, evidence/testimony is
struck, but model jury impact as **partial persuasion decay** sized to how
procedural vs. impressionistic each individual juror's ledger is (not a full
wipe) → if overruled, it stands in full.

Wrong grounds or a missed window means the moment passes with no retroactive
save (except a single, one-time teaching nudge from a Rookie-difficulty judge
only). Reflexive over-objecting should visibly cost credibility with the
jury over time.

Opposing counsel's objection behavior should be pre-written per case (see
below), not improvised, and should scale with difficulty exactly as
described in section 3.

### Pre-planned opposing counsel
Whichever side the player isn't playing needs a written game plan at
case-generation time, not improvisation: opening theory, planned objections
tied to difficulty, their strongest moment, and a specific, reachable weakest
moment. This is the trial's equivalent of a mystery's "tell budget" — it
keeps difficulty consistent and fair rather than randomly generous or
unbeatable, and gives opposing counsel a real throughline instead of pure
reaction to the player.

### AI Judge disposition (when Judge is not the player)
Strictness tied to chosen difficulty, plus two or three specific behavioral
tendencies (e.g. quick to sustain relevance objections, lenient on leading
questions during cross) so rulings feel like a consistent person on the
bench, not a random rules engine. Must rule identically-strictly on both
sides — inconsistency between sides is a bug, not difficulty.

---

## 6. Trial Phase Structure

1. **Opening statements** — locks each side's theory; contradicting your own
   opening later costs credibility with jurors who noticed
2. **Case-in-chief** — direct examination, one witness at a time
3. **Cross-examination** — same witness, opposing side; where contradictions
   get mined
4. **Objections** — live throughout phases 2 and 3
5. **Closing arguments** — last reframe
6. **Deliberation** — fragments only, never a full transcript
7. **Verdict**
8. **Endgame reveal** — replay the case from the other side's POV, showing
   the player where their read was right and where they got lucky

---

## 7. Plugin & File Structure to Build

```
verdict/                          ← plugin root
├── plugin.json                   ← plugin manifest: name, description,
│                                    version, entry points
├── commands/                     ← real slash commands (each a short .md
│                                    file: what it does, what it hands off
│                                    to the skill, minimal args)
│   ├── case.md                   — /case — start a new case (setup entry point)
│   ├── ask.md                    — /ask <person> about <topic> — question someone
│   ├── press.md                  — /press <person> — push on a contradiction
│   ├── examine.md                — /examine <thing> — close inspection
│   ├── object.md                 — /object <grounds> — raise an objection
│   ├── theory.md                 — /theory — float a theory, get an honest read
│   ├── accuse.md                 — /accuse <person> — end via accusation (non-trial modes)
│   ├── notebook.md               — /notebook — show case file: evidence, timeline
│   ├── save.md                   — /save — persist current session state
│   ├── load.md                   — /load — resume a saved case
│   └── hint.md                   — /hint — nudge, at a cost
└── skills/
    └── verdict/                  ← the skill itself
        ├── SKILL.md              — routing table, core loop, standing rules
        ├── README.md             — human-facing: how to start and how to play
        └── references/
            ├── setup.md          — role select, difficulty select, case
            │                        generation entry point
            ├── case-build.md     — how to build the locked case file: ground
            │                        truth, defendant, evidence table, witness
            │                        ledgers, juror ledgers, opposing counsel's
            │                        game plan, plus pre-play sanity checks
            ├── trial-defense.md  — defense objectives and tactics
            ├── trial-prosecution.md — prosecution objectives, burden of proof
            ├── trial-judge.md    — ruling logic, bench-review scoring
            ├── trial-witness.md  — staying consistent under cross, breaking points
            ├── objections.md     — grounds list, timing windows, sustain/
            │                        overrule logic, jury-decay interaction,
            │                        difficulty scaling
            ├── jury.md           — ledger format, persuasion scoring,
            │                        deliberation, verdict resolution
            └── endgame.md        — verdict, bench review, reveal scene
```

**plugin.json** should declare the plugin name (`verdict`), a short
description Claude Code can use for discovery, a version, and register each
file under `commands/` as an entry point. Commands stay thin — each one's job
is to state the action clearly and route into the skill; the actual game
logic and rules live in the skill's `references/`, not duplicated in the
command files.

Same progressive-disclosure principle as other Claude skills applies inside
`skills/verdict/`: SKILL.md holds only the routing table and role-agnostic
rules that apply no matter what's happening. Each reference file loads only
when that phase or role is active — never load all of them into context at
once.

**README.md is a required deliverable, not optional polish.** SKILL.md is
written for Claude; the README is written for the person playing, and should
work standalone without needing SKILL.md open. It must cover:
- What the game is, in two or three sentences
- How to start a case (the exact command: `/case`)
- How role and difficulty get chosen (what the player will be asked, what
  the options mean)
- The full command list (from `commands/`) with one-line descriptions
- How a session ends and how `/save` / `/load` work
- A short "what winning looks like" note per role, since it's not the same
  goal for everyone

---

## 8. Build Order

1. **case-build.md** — the locked case file format; everything else reads off it
2. **objections.md** — the crunchiest, most failure-prone mechanic; draft the
   grounds list and sustain/overrule logic, hand-test 2–3 transcripts before
   wiring anything else around it
3. **jury.md** — ledger format and persuasion scoring
4. Role files (trial-defense, trial-prosecution, trial-judge, trial-witness)
   — each fairly thin once the systems above exist
5. **endgame.md** — verdict + reveal scene
6. **SKILL.md** — routing table and core loop, written once the parts it
   routes to are stable
7. **commands/** — thin entry-point files, one per slash command, once the
   skill logic they route into is settled
8. **plugin.json** — manifest tying commands to the skill, written once both
   exist so it accurately registers what actually shipped
9. **README.md** — written last of all, once commands and flow are locked,
   so it accurately reflects what shipped rather than what was planned

---

## 9. Test Cases (Pre-Launch)

| Test | Purpose |
|---|---|
| Defense, Standard, actually-innocent client | Baseline — should be winnable through solid work |
| Prosecution, Elite, actually-guilty defendant with one excludable technicality | Tests whether the technicality mechanic lands and doesn't feel arbitrary |
| Witness, Elite cross-examiner | Tests whether staying consistent is genuinely hard, not just tense |
| Judge, Standard | Tests whether bench-review scoring feels like real evaluation, not a participation trophy |

---

## 10. Standing Design Rules (apply across every file)

- **Never retcon the ground truth or any sealed ledger** to fit how play is
  going, in either direction.
- **Never let one AI-run participant leak knowledge** that belongs to
  another AI-run participant or to the hidden ground truth.
- **Never show ledgers, scores, or a running verdict prediction** to the
  player — only in-world behavior and fragments.
- **Opposing counsel and the AI judge play pre-written plans**, not
  improvisation, so difficulty stays consistent and fair across a whole
  session and across replays.
- **A loss should be legible.** The endgame reveal should let the player see
  specifically where their argument had real gaps, traceable to a juror's
  ledger or a missed piece of evidence — not just a bare win/loss.

---

## 11. Open Questions for Later

- Civil case burden-of-proof (preponderance) and damages-based endgame — v2
- Custody/family mode with a single judge instead of a 12-person jury — v2
- Appeal mode (trying the fairness of a prior trial) — natural fit for the
  Judge role — v2
- Whether opposing counsel's aggressiveness should be visibly telegraphed at
  setup ("you're facing a sharp DA") or left for the player to discover
  during play
