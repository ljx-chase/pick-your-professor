# Evals

A regression set for the skill itself. Run it after any change to `SKILL.md` or
to a reference file. It is not part of using the skill.

## How to run

Start a **fresh session** with the skill installed and no prior context about
the skill, one case per session. A case run in a session that already discussed
the skill proves nothing, because the model has been primed.

Read the response against the checks. Each check is pass or fail. If a check
needs interpretation, it is written badly: rewrite the check.

Record results as a table in your PR:

```
| id  | pass | note                                   |
|-----|------|----------------------------------------|
| N1  | ✓    |                                        |
| P3  | ✗    | repeated the answer with more words    |
```

A change to trigger scope or to a core rule needs every negative and at least
five positives.

---

### N1 — a hard question does not set a register

Ask a dense technical question in the user's own field, with no complaint and no
style request.

- Passes if the answer is normal and no register is set or offered.
- Fails if a register is volunteered because the topic looked hard.

### N2 — being new to a field does not set a register

Say "I'm new to X, what is it?"

- Passes if the question is answered. This skill does not fire.
- Fails if it sets a register, names prerequisites, or starts a walkthrough.

### N3 — a request for brevity is not a register request

Ask for a one-line answer.

- Passes if the answer is one line.
- Fails if the reply explains the register system or offers a choice.

### P1 — an explicit request is honored

"Use Feynman style." Then ask a technical question.

- Passes if every field term is glossed in the sentence it appears in, and the
  answer opens with a concrete situation rather than a definition.
- Fails if any term appears unglossed, or if the answer opens with a definition.

### P2 — the register persists

After P1, ask three unrelated questions, including one very short factual one.

- Passes if all three hold the budget.
- Fails if the register is dropped after the first answer, or if the short
  question is answered at default density.

### P3 — a complaint steps it down

Ask a question with no register set, then reply "that was too technical".

- Passes if the same question is re-answered one register lighter, with a
  one-line offer to hold it.
- Fails if the same answer is repeated at greater length, or if the reply asks
  about the user's background.

### P4 — a register does not strip content

Set Feynman, then ask something whose correct answer needs an assumption and an
order of magnitude.

- Passes if both survive, in plain words.
- Fails if the answer reads well but has dropped either.

### P5 — switching is cheap

Mid-session, say "switch to Landau".

- Passes if the switch is confirmed in at most one clause and the next answer is
  compact.
- Fails if the reply re-explains the register system.

### D1 — Feynman and Griffiths stay distinct

In two fresh sessions, ask the same question once in Feynman and once in
Griffiths.

- Passes if the Feynman answer runs on a different system from the subject and
  says where that analogy stops working, and the Griffiths answer runs on a
  simplified case of the real system and shows where that simplification fails.
- Fails if both answers use the same picture, or differ only in sentence length.

### X1 — a mixed request overrides one knob

Set Feynman, then ask "Feynman, but show the algebra" with a question that has a
short derivation.

- Passes if the derivation is visible, every symbol is named where it is
  introduced, and the argument is still carried by a parallel system.
- Fails if it switches to Griffiths (analogy dropped, terms left unglossed after
  first use), or if it refuses to show the algebra.

### M1 — Chinese trigger

"讲人话，太专业了。"

- Passes if the register steps down and the whole reply is in Chinese.
- Fails if it replies in English or asks which register the user wants.
