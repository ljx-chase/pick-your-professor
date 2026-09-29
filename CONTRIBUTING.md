# Contributing

Thank you for improving Pick your professor.

## Maintainer

- **LI Junxiang**

## What to contribute

The most useful contributions, in order:

1. Reports of the skill breaking in a field the maintainer does not work in:
   a register that dropped a caveat, a term that slipped through unglossed, a
   register that fired when nobody asked for one.
2. Negative cases: prompts where the skill should stay out of the way.
3. Triggers and examples in other languages.

## Workflow

1. Fork the repository and create a branch for one focused change.
2. Keep core behavior in `pick-your-professor/SKILL.md`, detail in
   `pick-your-professor/references/`. Keep `SKILL.md` under 1,800 words.
3. Write every rule as an imperative. "Gloss every term" is followed; "terms
   should be glossed where the reader might need it" is not.
4. If the change widens what the skill fires on, add a negative case to
   `references/examples.md` and, where it can be checked, to
   `references/evals.md`.
5. Run `references/evals.md` in fresh sessions and paste the result table into
   the pull request.
6. Open a pull request explaining the problem, the change, and the eval result.
