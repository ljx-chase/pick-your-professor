# AGENTS.md

## Purpose

This repository contains **Pick your professor**, a skill that lets the user set
how densely an answer is written and keeps it that way for the rest of the
session. The behavioral specification lives in `pick-your-professor/SKILL.md`.

This file covers two things: how to install the skill, and how to behave once it
is loaded.

## Installation

If a user has asked you to install this skill, do the following. The skill root
is the inner directory `pick-your-professor/`, which contains `SKILL.md` at its
top level plus a `references/` directory. Keep that structure intact; `SKILL.md`
resolves its references relative to its own location.

Pick the case that matches your environment.

**Claude Code.** Copy the inner `pick-your-professor/` into `~/.claude/skills/`
for all projects, or into `.claude/skills/` in the current repository for this
project only. Equivalent one-liner if `npx` is available:

```bash
npx skills add ljx-chase/pick-your-professor -g
```

**Claude web, Desktop, or Cowork.** These do not read `~/.claude/skills/`. Tell
the user to download `pick-your-professor.zip` from the repository's releases
and upload it under Customize, then Skills. The zip must contain a single folder
with `SKILL.md` inside it, not a bare `SKILL.md` and not the whole repository.

**ChatGPT Skills.** Upload the same `pick-your-professor.zip`, or package the
inner `pick-your-professor/` folder yourself with `SKILL.md` at its root, through
the Skills tab.

**Codex or another repository-aware agent.** Clone this repository into the
workspace and keep this `AGENTS.md` at the workspace root. No further
installation is needed; load `SKILL.md` when the entrypoint below applies.

**Cursor, OpenCode, Kimi, Gemini CLI, or any other agent with a skills
directory.** Copy the inner `pick-your-professor/` into whatever directory that
agent reads skills from, preserving the folder structure.

**Anything else.** Use `pick-your-professor/SKILL.md` directly as the
instruction file.

**Verify.** In a fresh session, say "use Feynman style", then ask a technical
question. A correct answer opens with a concrete situation and glosses every
piece of field vocabulary in the sentence where it appears. Then ask a short
factual question: it should hold the same budget. If the first answer opens with
a definition or uses an unglossed term, the skill did not load.

## Agent entrypoint

When the user names a register or professor, asks for the picture first or the
derivation first, or says an answer was too dense:

1. Read `pick-your-professor/SKILL.md` first, and
   `pick-your-professor/references/registers.md` before the first answer in a
   register.
2. **Only explicit triggers set a register.** An explicit request or an explicit
   complaint. Never because a topic looks hard, because your answer came out
   dense, or because the user is new to something. Do not offer one unprompted.
3. **Persist.** A register holds for every answer until the user changes it,
   across topic changes and on short factual questions. A short factual
   question still gets a short answer.
4. **Override one knob on a mixed request.** "Feynman, but show the algebra"
   keeps Feynman's term budget and analogy and makes the derivation visible,
   for that answer only. Never average two registers.
5. **Never remove content.** Assumptions, magnitudes, caveats and failure
   regimes survive in every register. If the budget would force dropping one,
   spend more words.
6. **Never start a teaching sequence.** No prerequisites, no knowledge checks,
   no multi-turn plan. Answer the question that was asked.
7. **Step down on a complaint.** Re-answer the same question one register
   lighter, offer in one line to hold it, and do not ask about background.
8. Preserve the user's language.

## Repository conventions

- Keep `pick-your-professor/SKILL.md` a control plane, under 1,800 words. Detail
  goes in `references/` with a pointer.
- Keep every rule an imperative. Conditionally phrased rules get skipped.
- Preserve YAML frontmatter in `SKILL.md` with only `name` and `description`.
  Keep the `description` under 1024 characters, with both the positive triggers
  and the "Do not" clause.
- Any change that widens what the skill fires on must add a matching negative
  case to `references/examples.md`.

## Validation

After modifying the skill, run the cases in
`pick-your-professor/references/evals.md` in fresh sessions and paste the result
table into the pull request.

A valid distributable archive contains one folder, `pick-your-professor/`, with
`SKILL.md` at its root.
