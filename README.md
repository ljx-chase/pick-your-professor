<div align="center">

# Pick your professor

<p>
<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License"/></a>
<img src="https://img.shields.io/badge/version-v1.0.0-blue?style=flat-square" alt="Version"/>
<a href="https://github.com/ljx-chase/pick-your-professor/stargazers"><img src="https://img.shields.io/github/stars/ljx-chase/pick-your-professor?style=flat-square&color=yellow" alt="Stars"/></a>
</p>

<strong>Language</strong>: <a href="README.md">English</a> | <a href="README.zh-CN.md">中文</a>

</div>

> **Ask an assistant about your own research and the answer comes back correct
> and unreadable.** This skill lets you set how densely answers are written,
> Feynman, Griffiths or Landau, and holds that setting for the rest of the
> session.

## Quick start

Paste this into your agent, whichever one you use:

```text
Install the pick-your-professor skill from
https://github.com/ljx-chase/pick-your-professor, following the installation
section of the repo's AGENTS.md.
```

Or install it yourself:

- **Claude Code:** `npx skills add ljx-chase/pick-your-professor -g`, or copy the
  inner `pick-your-professor/` folder into `~/.claude/skills/`.
- **Claude web, Desktop, Cowork, ChatGPT:** download `pick-your-professor.zip`
  from [Releases](https://github.com/ljx-chase/pick-your-professor/releases) and
  upload it as a skill.
- **Codex and other agents:** see [AGENTS.md](AGENTS.md).

Then say "Feynman style" and ask something.

## Why this exists

Ask a question at the edge of your own field and the answer arrives at
specialist density: a paragraph with a dozen unglossed terms. There is no way to
say "the same answer, written so I can follow it" without also asking to be
taught the field from scratch.

**Before**, at default density:

> Your parameters are likely non-identifiable: the Jacobian is near
> rank-deficient, so the Fisher information is ill-conditioned and the
> covariance blows up along the degenerate direction. Reparametrize or add data
> that breaks the degeneracy.

**After**, in Feynman:

> Your model has two knobs, and your data can only see a combination of them.
> Say the curve depends only on the product a·b: doubling a and halving b draws
> the exact same curve, so the fit can slide along a whole line of values
> without matching the data any worse. The fitting routine reports that slide
> as a huge uncertainty on each knob separately, even though the product itself
> may be pinned down to a few percent. Fix it by fitting the product as one
> parameter, or by collecting data in a range where the two knobs change the
> curve in different ways. This assumes the error bars come from how sharply
> the fit's error rises around the best values, which is what most fitting
> routines report.

Same content. Same fix. Same caveat. Different number of terms you are expected
to already know.

The controlling knob is an **unexplained-term budget**: how many pieces of field
vocabulary may appear without a gloss where they appear. "Write more simply" is a
wish; a term budget is a rule that can be followed and checked.

## The three registers

- **Feynman** — zero unexplained terms. Picture first, analogies with their
  limits stated, equations after.
- **Griffiths** — each term defined on first use, then used freely. Textbook
  order: motivate, define, derive, work a case.
- **Landau** — compact. Assumes fluency. Result first, derivation sketched.

This is density, not depth. Every register keeps the assumptions, magnitudes and
caveats; only the vocabulary load and the order change. Plain names work too:
`picture first`, `textbook`, `compact`.

This is not an onboarding tool. It changes how an answer is written, not what gets taught in what order. If you want to be walked into a field you do not know yet, see [research-field-onboarding](https://github.com/ljx-chase/research-field-onboarding), which has its own explanation styles governing the teaching sequence.

## When it fires, and when it does not

It fires only on an explicit request ("Feynman style", "picture first", "讲人话")
or an explicit complaint ("too technical", "I didn't follow that", "看不懂").

It does **not** fire because a topic is hard, because an answer came out dense,
or because you said you are new to something. It never offers itself unprompted.
A style skill that decides you look lost is worse than no skill.

## Rules

- Only an explicit request or complaint sets a register.
- A register persists across topics and on short questions until you change it.
- A register never removes content; if the budget would drop a caveat, it spends
  more words instead.
- A complaint gets the same question re-answered one register lighter, not the
  same answer at greater length.
- It never asks about your background and never starts a teaching sequence.
- Switching is one clause of confirmation, no re-explanation.
- Code, logs and error messages are quoted as they are.

## Changelog

### v1.0.0

- First release. Three registers defined by an unexplained-term budget, set only
  by explicit request or complaint, persistent for the session.
- The rule set carries over lessons from
  [research-field-onboarding](https://github.com/ljx-chase/research-field-onboarding):
  rules are written as imperatives because conditionally phrased rules were
  skipped in testing there, and "clarity is not shallowness" is stated
  explicitly because a readable answer that drops a caveat was the failure most
  often seen.
- Ships with an eval set (`references/evals.md`) of three negative, five
  positive and one multilingual case.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Negative cases, where the skill fires
when it should not, are especially welcome.

## Feedback

This skill is new and has mostly been tested by its author, in physics and
adjacent fields. Reports of it breaking in other fields are the most useful
contribution: a term that slipped through unglossed, a caveat that disappeared
in Feynman, a register set when nobody asked.
[Open an issue](https://github.com/ljx-chase/pick-your-professor/issues).

## Citation

```bibtex
@misc{pick_your_professor_2026,
  title        = {Pick your professor: a cross-agent skill for setting the
                  density of research answers},
  author       = {Li, Junxiang and Zhou, Ziyan},
  year         = {2026},
  howpublished = {\url{https://github.com/ljx-chase/pick-your-professor}},
  note         = {GitHub repository}
}
```

## License

MIT License. Copyright (c) 2026 LI Junxiang and Ziyan Zhou (Anna).
