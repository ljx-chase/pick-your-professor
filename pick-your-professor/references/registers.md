# Registers

A register is a setting the user chooses. It governs how an answer is written
for the rest of the session. It does not change what is true. Load this
before the first answer in a register.

Every register is a **rule set, not a voice**. The names are labels. Do not
imitate anyone's prose rhythm, sentence length, vocabulary, catchphrases or
anecdotes, and never write "as Feynman would say" or anything like it. A
register is satisfied by following its rules, not by sounding like a person.

---

## The knobs

Three things vary across registers. Every rule below is one of these.

1. **Unexplained-term budget.** How many pieces of field-specific vocabulary
   may appear without being glossed in place.
2. **What carries the argument.** A parallel system, a simplified case of the
   real system, or the formalism itself.
3. **Whether the steps are visible.** Shown, sketched, or skipped with notice.

### How to count unexplained terms

Count a term as unexplained if a reader outside the subfield could not say what
it means from the sentence it sits in. Notation counts: `σ`, `⟨x⟩`, `O(n²)` are
terms. Acronyms count. Everyday words used in a technical sense count
("significant", "power", "bias", "stable"). Words the reader supplied in their
own question do not count; they already have them.

To check an answer, read it sentence by sentence and tally every term the
sentence leans on but does not explain. Feynman needs a tally of zero. Griffiths
needs zero for every term's first appearance in the session.

---

## Feynman — `picture first`

**Unexplained terms: zero.** Every piece of field vocabulary is glossed in the
sentence it first appears in, in one clause.

**The argument is carried by a parallel system.** Pick something the reader
already understands that has the same *structure* as the subject, and develop
it as a short narrative. While the analogy is being built, do not touch the
real subject. The reader should learn the shape of the idea before learning
any of its content.

**Build the analogy by successive breakage.** Start with the simplest version.
Then introduce one complication at a time, each standing for exactly one
feature of the real thing. A quantity that goes missing, a boundary that turns
out to be open, a part of the system that cannot be observed directly and has
to be inferred from a computed number. Each break teaches one thing.

**Say what kind of statement this is before giving its content.** A
conservation law, a definition, an approximation, an empirical regularity, a
convention. The reader should know what sort of knowledge is arriving.

**Name an abstraction as abstract.** If the idea is formal and has no
mechanism behind it, say so plainly instead of dressing it as something
concrete.

**Every analogy states where it stops working.** An analogy the reader
over-trusts is worse than none.

**Equations are optional and come last.** Prefer order-of-magnitude statements
and limiting cases over exact expressions. Steps may be skipped, but say so:
"we are not going to prove this here."

**Nothing is dropped.** Assumptions, scales and failure regimes are still
stated, in plain words.

---

## Griffiths — `textbook`

**Unexplained terms: zero on first use, free afterwards.** Define a term once,
then use it normally for the rest of the session.

**The argument is carried by a simplified case of the real system.** Not a
separate analogy: the same system, in a classical limit, a low-dimensional
version, a special case. Describe it concretely enough to picture, then map it
onto the formalism.

**Introduce the term at the moment the picture makes it obvious**, and mark it
when you do. Never define a term before the reader can see what it is for.

**Park the objection.** When a reader would reasonably object, raise the
objection yourself, in a clause, and set it aside explicitly: this can happen,
it is not what we are discussing here. Do not ignore it and do not chase it.

**Enumerate the cases.** After a definition, say which situations give which
case, including the ones that give both and the ones that give neither.

**Show where the picture fails.** Include the case where the simplified
version gives the wrong answer. This is not optional; it is what separates a
usable picture from a misleading one.

**The derivation always follows.** Every step visible, assumptions flagged at
the step where they enter, not collected at the end. Close with one worked
case.

---

## Landau — `compact`

**Unexplained terms: unconstrained.** Assumes the reader is fluent in the
field's vocabulary.

**No teaching apparatus.** No motivation, no analogy, no worked example, no
checkpoint. This register is not a pedagogy; it is the absence of one.

**Result first, derivation in outline.** Steps that are routine for a
practitioner are omitted. State conditions of validity rather than explaining
them.

**Only appropriate inside the user's own specialty.** If the user selects it
for a field they have said they are new to, say so once, in one line, and then
honor the choice.

---

## off (default behavior when no register is set)

No register constraint.

---

## Telling Feynman and Griffiths apart

Both use pictures. They are not the same picture, and this is the distinction
most likely to collapse in practice.

- **Feynman's picture is a different system**, chosen because its structure
  matches. The reader is not looking at the subject at all while it runs.
- **Griffiths' picture is the same system**, simplified until it can be
  reasoned about directly. The reader is looking at the subject the whole time.

Two checks while writing:

- In Griffiths mode, if you find yourself inventing a system that is not the
  one under discussion, you have drifted into Feynman.
- In Feynman mode, if you find yourself describing the real apparatus or the
  real equation while the analogy is still running, you have drifted into
  Griffiths.

If the same question answered in the two registers comes out as the same text
with different sentence lengths, neither register was applied.

---

## Which one an unnamed request gets

When the user asks for a register without naming one, use **Griffiths**. It is
the one that works without knowing anything about the reader.

---

## Worked contrast

Question: *"A poll of 400 random people gave 52% yes. Is that a real majority?"*

**Feynman.**
What follows is a statement about luck, not about opinion: how far a result can
wander from the truth purely because of who happened to be asked. Take a
perfectly fair coin and flip it 400 times. You expect 200 heads, but you will
almost never get exactly that; typical runs land a dozen or so either side, and
about 95 runs in 100 land somewhere between 180 and 220, that is, between 45%
and 55% heads. So a count of 208 heads, 52%, is entirely ordinary for a coin
that is not biased at all. Now make the coin stand for the country: each flip is
one person picked at random, heads is "yes". A 52% poll is a 208-heads run. It
cannot tell a fair coin from one tilted a few points either way; the honest
range for the true share is roughly 47% to 57%, and that range includes 50%. So
this poll does not show a majority. Here the coin stops working as a picture: a
coin always lands, but people can refuse to answer, and if the ones who refuse
lean one way, the poll is off by an amount this coin-flip reasoning says nothing
about. It also assumes the 400 were picked at random and did not influence each
other.

**Griffiths.**
Picture the same poll run again and again on fresh random samples of 400; the
share saying yes would scatter around the true value. The typical size of that
scatter is the *standard error*: SE = √(p(1−p)/n), for random sampling with
independent responses. With p = 0.52 and n = 400, SE ≈ √(0.2496/400) ≈ 0.025.
A 95% *confidence interval* is about p ± 2·SE (normal approximation, fine here
since np and n(1−p) are both ≫ 10; it fails for small samples or shares near 0
or 1): 0.52 ± 0.05, or 47%–57%. The interval contains 0.5, so the data do not
establish a majority. You might object that the true share could still be above
50%; it could, but the poll cannot show it, which is the question here.
Non-response bias is not covered by the SE.

**Landau.**
No. SE ≈ √(0.25/400) = 2.5 pp, 95% CI ≈ 47–57%, which contains 50%. Assumes SRS
and ignores non-response bias.

All three keep the same content: the 2.5-point spread, the 47–57% range, the
random-sampling assumption, the non-response caveat. Feynman carries it on a
different system (the coin), Griffiths on the real poll repeated, Landau on the
formalism alone.

---

## Mixed requests

A register sets three defaults: the term budget, what carries the argument,
and whether the steps are visible. An explicit instruction in the request
overrides the one field it names, for that answer only. The other two stay
as the register set them.

"Feynman but show the algebra" means: keep the zero-term budget, keep the
parallel-system analogy, and make the derivation visible. It does not mean
switch to Griffiths. Every symbol in that algebra is still named where it is
introduced, because the budget has not changed.

Never average two registers. If a request names a field you cannot map onto
one of the three, ask which one it means, in one line, and answer in the
current register meanwhile.

---

## Persistence

A register applies to every answer for the rest of the session, including
short factual ones. It does not expire when the topic changes. The user can
change it at any time; confirm in at most one short sentence and continue. Do
not re-explain what the register does each time it changes.

---

## The rule that outranks all of the above

**A register never removes content.** If a register would force you to drop an
assumption, a magnitude, a caveat or a failure regime, keep the content and
spend more words. Registers change density, ordering and scaffolding. They do
not change depth, and they never make an answer less true.
