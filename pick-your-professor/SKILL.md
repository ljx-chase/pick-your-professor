---
name: pick-your-professor
description: Set how densely an answer is written and keep it that way for the rest of the session. Three registers, Feynman (zero unexplained terms, physical picture first), Griffiths (define each term on first use, textbook order), and Landau (compact, assumes fluency). Use when the user names a register or one of those professors, asks for the picture first or the derivation first, says an answer was too technical or had too much jargon or that they could not follow it, or asks to be told something in plain words. Also trigger in other languages, including Chinese such as 讲人话, 说简单点, 太专业了, 看不懂, 术语太多, 先讲物理图像, 直接推导. Do not set a register because a topic looks difficult, because an answer contains many terms, or because the user is new to a field. Only an explicit request or an explicit complaint sets one.
---

# Pick your professor

The failure this skill exists to prevent: a correct answer the reader cannot
use, because it arrived at the density of someone who already knows the field.

The user picks a register. It governs how densely you write, for the rest of the
session, in every answer including short ones.

## The mechanism

Each register is defined by an **unexplained-term budget**: how many pieces of
field-specific vocabulary may appear without being glossed where they appear.

Everything else follows from the budget. Ordering, whether analogies appear,
where equations sit, how much scaffolding a derivation gets. Set the budget and
the rest is determined.

Count a term as unexplained if a reader outside the subfield could not say what
it means from the sentence it appears in. Notation counts. An acronym counts.

## The three registers

**Feynman — budget: zero.**
Gloss every piece of field vocabulary in the same sentence it first appears, in
one clause. If a sentence would need three glosses, it is the wrong sentence;
rebuild it. Open with a concrete situation, a number, or something the reader
can picture, never with a definition. Use analogies, and state where each one
breaks. Put equations after the picture, and name every symbol on introduction.
Prefer a limiting case or an order of magnitude where either would serve.

**Griffiths — budget: zero on first use, unlimited after.**
Define each term once, then use it freely for the rest of the session. Motivate,
define, derive in visible steps, then work one case. State each assumption where
it enters the derivation, not collected at the end. Analogies optional.

**Landau — budget: unconstrained.**
Assume fluency in the field's vocabulary. Result first, derivation sketched,
scaffolding minimal. No motivating narrative, no analogies.

**off — default.** No constraint.

When the user asks for a register without naming one, use Griffiths.

The names are labels for rule sets, not voices. Do not imitate anyone's prose
style, personality or anecdotes. Accept plain names for the same three:
`picture first` for Feynman, `textbook` for Griffiths, `compact` for Landau.

## When to set one

Set a register when, and only when:

1. **The user asks.** By register name, by professor name, by plain name, or by
   description: "give me the picture first", "just the derivation", "讲人话".
2. **The user says an answer was too dense.** "Too technical", "too much
   jargon", "I didn't follow that", "看不懂", "术语太多".

Do not set a register because a question is hard, because your own answer came
out full of terms, or because the user said they are new to something. Do not
offer a register unprompted. Over-firing makes this skill worse than not having
it.

## Stepping down on a complaint

When the user says an answer was too dense, do not repeat it at greater length
and do not ask what their background is.

Re-answer the same question one register lighter. Then offer, in one line, to
hold that register for the rest of the session.

From off, step to Griffiths. From Griffiths, step to Feynman. At Feynman, the
budget is already zero, so the problem is structural: shorten the sentences,
cut the answer to one claim, and work a concrete number.

## Persistence

A register applies to every answer until the user changes it. It does not expire
when the topic changes, and it does not lapse on short factual questions.

The user may switch at any time, including mid-answer. Confirm in at most one
short clause and continue. Do not re-explain what the register does each time it
changes.

## What a register never does

**It never removes content.** Assumptions, magnitudes, caveats, failure regimes
and uncertainty all survive in every register, Feynman included. A register
changes term density, ordering and scaffolding. If holding the budget would mean
dropping an assumption or a number, keep the content and spend more words.

Clarity is not shallowness. An answer that reads easily because it quietly
dropped a caveat is a worse failure than the dense answer it replaced.

**It never starts a teaching sequence.** Do not name prerequisites, do not ask
the user to mark what they know, do not add comprehension checks, do not
announce a multi-turn plan. Answer the question that was asked, in the register
that is set.

If the user does want to be walked into an unfamiliar field from the beginning,
that is a different task and a different skill.

**It never applies to code or data.** Variable names, log output, file paths and
error messages are quoted as they are. The register governs your prose around
them.

## Landau outside the user's specialty

If the user selects Landau for something they have told you they are new to, say
so once, in one line, then honor the choice. Do not repeat the warning.

## References

Load a reference when the moment for it arrives, not up front.

| File | Load it when |
| --- | --- |
| `references/registers.md` | Before the first answer in a register |
| `references/examples.md` | An example would settle how a rule applies |
| `references/evals.md` | You are changing this skill, not using it |

## Anti-patterns

- Setting or offering a register because a topic looked hard. This is the
  failure that makes a style skill worse than no skill.
- Repeating a too-dense answer at greater length instead of re-answering it
  lighter.
- Producing a smooth, readable answer that has quietly dropped an assumption, a
  magnitude or a caveat.
- Holding the register for one answer and drifting back on the next.
- Imitating a physicist's voice instead of following the register's rules.
- Asking what the user's background is. The register is the answer to that
  question; that is the point of setting one.
