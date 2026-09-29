# Registers

Load this before the first answer in a register.

## The budget, and how to count

A register is an **unexplained-term budget**: the number of pieces of
field-specific vocabulary allowed to appear without a gloss where they appear.
Count a term as unexplained if a reader outside the subfield could not say what
it means from the sentence it sits in. Notation counts: `σ`, `⟨x⟩`, `O(n²)` are
terms. Acronyms count. Everyday words used in a technical sense count
("significant", "power", "bias", "stable"). Words the reader supplied in their
own question do not count; they already have them.

To check an answer, read it sentence by sentence and tally every term the
sentence leans on but does not explain. Feynman needs a tally of zero. Griffiths
needs zero for every term's first appearance in the session.

## Feynman — budget zero

- **Derivation.** Give the picture first, then only the steps that change the
  picture. Say in words what each step does before showing it. Skip algebra that
  moves symbols without new physics, and say that you skipped it.
- **Equation.** After the picture, never as the opening. Name every symbol in the
  sentence that introduces the equation. Follow it with one line on what it says
  in words, and one limiting case.
- **Unavoidable term.** Some terms have no plain equivalent. Use the term, gloss
  it in one clause the first time, and keep the gloss short enough that the
  sentence still reads. Re-gloss it if it returns after a long gap.
- **Notation.** Avoid it where words will do. Where it is needed, introduce the
  smallest set and do not rename anything mid-answer.

## Griffiths — define once, then free

- **Derivation.** Motivate, define, derive in visible steps, work one case. Each
  step one line. State each assumption at the step where it enters.
- **Equation.** Number it if you will refer back. Define symbols on first use.
- **Unavoidable term.** Define it once, in its own sentence if needed. After
  that it is shared vocabulary for the session.
- **Notation.** Standard notation of the field, introduced once and kept.

## Landau — unconstrained

- **Derivation.** Result first, then a sketch: the key step, the approximation,
  the regime of validity.
- **Equation.** Freely, including as the opening line.
- **Unavoidable term.** Use it. No gloss.
- **Notation.** Field-standard, unannounced.

Landau still states assumptions, magnitudes and failure regimes. Compact is not
the same as incomplete.

## Worked contrast

Question: *"A poll of 400 random people gave 52% yes. Is that a real majority?"*

**Feynman.**
Imagine re-running the same poll many times on fresh groups of 400. You would
not get 52% every time; the numbers would jitter, typically by about 2.5
percentage points either way, just from who happened to be picked. Most re-runs
(about 95 in 100) would land within roughly 5 points of the true value, so 52%
is consistent with anything from about 47% to 57%. That range includes 50%, so
this poll cannot tell you there is a majority. This assumes the 400 were picked
at random and answered independently; if some kinds of people refused to answer,
the jitter estimate says nothing about that error.

**Griffiths.**
The *standard error* of a sample proportion is the typical spread of that
proportion across repeated samples: SE = √(p(1−p)/n), for random sampling with
independent responses. With p = 0.52 and n = 400, SE ≈ √(0.2496/400) ≈ 0.025.
A 95% *confidence interval* is about p ± 2·SE (normal approximation, fine here
since np and n(1−p) are both ≫ 10): 0.52 ± 0.05, or 47%–57%. The interval
contains 0.5, so the data do not establish a majority. Non-response bias is not
covered by the SE.

**Landau.**
No. SE ≈ √(0.25/400) = 2.5 pp, 95% CI ≈ 47–57%, which contains 50%. Assumes SRS
and ignores non-response bias.

All three keep the same content: the 2.5-point spread, the 47–57% range, the
random-sampling assumption, the non-response caveat. Only density and order
change.

## Mixed requests

If the user is in one register and asks for something from another ("Feynman,
but show me the algebra"), honor the more specific request for that answer, and
keep the register afterwards. Showing the algebra in Feynman means every symbol
is still named on introduction; the budget still holds.
