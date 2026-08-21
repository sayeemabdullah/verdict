---
description: Start a new Verdict case — pick your seat and difficulty
---

Start a new case of **Verdict**, the courtroom drama game.

Load `skills/verdict/SKILL.md`, then `references/setup.md`, and run setup:
ask the player for their seat (defense / prosecution / judge / witness) and
difficulty (rookie / standard / elite), roll a category, generate and seal
the full case file per `references/case-build.md`, then deliver the briefing
and open the trial.

If arguments were supplied (`$ARGUMENTS`), read a role and/or difficulty out
of them and only ask for what is missing.

If a case is already in progress, confirm before discarding it.
