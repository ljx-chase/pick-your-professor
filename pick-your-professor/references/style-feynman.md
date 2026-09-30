# Explanation style: Feynman Lectures, Vol. III (Quantum Mechanics)

Source: R. P. Feynman, R. B. Leighton, M. Sands, *The Feynman Lectures on
Physics*, Vol. III, New Millennium Edition (Basic Books, 2010). Section numbers
below are the book's own (e.g. §1-7 = Chapter 1, section 7).

This file describes **how the book explains**, not what it explains. It is the
move catalogue behind the **Feynman** register. Load it after `registers.md`,
before the first answer in Feynman. The register's rules in `SKILL.md` and
`registers.md` win wherever this file seems to disagree: in particular, the
zero unexplained-term budget holds, and nothing here licenses imitating the
book's voice.

## Stance

- **Label the status of every claim.** Observed, derived, assumed, or "put in
  by hand" are kept distinct, and the reader is told which is which even when
  the labelling is only "this is rough for now" (Preface; §3-1). Tell the
  reader when a statement is deliberately imprecise and that they will only be
  able to tell in retrospect.
- **State mystery; do not dissolve it.** The double-slit is chosen because it
  cannot be explained classically and "contains the only mystery" (§1-1). The
  book says how the rules work and refuses to say why. Confusion is the correct
  response to strange facts, shared by experts, not a defect in the reader.
- **Aim at the strongest reader, keep a backbone for everyone.** Fireworks are
  allowed, but a reader who ignores them must still get a complete core
  (Preface). The author also admits where the approach failed (Preface,
  Epilogue). The tone is experimental and self-critical, never authoritative.
- **Ideas arrive with a detailed worked example attached.** Never an abstract
  principle first (Foreword by Sands).

## Explanatory moves

Use these as named tools. Each line: the move, when to use it, where the book
does it.

1. **Concrete apparatus before formalism.** Bullets, armour plate, sand box
   (§1-2); magnets and beam blockers (§5-1). Use at the start of an answer: the
   reader must picture the measurement before a symbol appears.
2. **Classical case first, then contrast.** Bullets (no interference), water
   waves (interference), then electrons (both) (§1-2 to §1-5). Each case ends
   with a one-line verdict so the contrast is crisp. Use whenever the new field
   overturns an intuition the reader owns.
3. **State the paradox plainly, refuse premature resolution.** "Does the
   electron go through hole 1 or hole 2?" is answered only with the rule for
   what one may *say* (§1-6). Use when a reader wants a mechanism the field
   does not have.
4. **Smallest system, carried all the way.** Two-state systems (ammonia,
   spin-1/2, K-mesons) carry Chapters 8 through 11; position dependence is
   deferred on purpose, in the reverse order to most books (§16-1). One
   complete small case beats a general framework.
5. **Notation only when the phenomenon needs it.** Bracket amplitudes appear
   after the amplitude idea has been used repeatedly (§3-1); kets appear only
   when the sum-over-base-states needs abstraction (§8-1). Never introduce a
   symbol ahead of its first use.
6. **Generalize by copying the pattern.** Spin one is done in full as a
   prototype; the reader is told to redo it with more beams by copying
   everything down (§5-1). After the worked case, say explicitly how the
   general case follows.
7. **Idealize openly and say why.** Indestructible bullets (§1-2); a fictional
   modified Stern-Gerlach apparatus, justified because thought experiments cost
   nothing (§5-1). Name every idealization at the moment you make it.
8. **Flag roughness.** "That is part of the roughness involved" (§3-1). When a
   statement is approximate, say so in the same sentence, and say it can be
   made precise later.
9. **Analogy to something the reader owns, then isolate the one break.**
   Bra-ket versus dot product with unit vectors, developed side by side, then
   the single difference (order matters) is isolated (§8-1 to §8-2). Never
   leave an analogy without its breaking point.
10. **Preview the destination.** Frequent "we would like to look ahead a
    little" (§8-3). Tell the reader where the argument is going before a long
    stretch.
11. **Ask the reader's question for them.** "You may ask, first of all, what
    base states? Well..." (§8-3); "You may wonder why we stop..." (§8-6).
    Voice the likely objection and answer it at once.
12. **Remove fear of notation.** "Don't get frightened, it's just a notation"
    (§8-1); a digression on incomplete bra-ket forms exists so the reader is
    not paralyzed by other books (§8-3). Treat notation as bookkeeping, and
    say so.
13. **Ground abstractions in a number or device.** The ammonia splitting is tied
    at once to a frequency and a wavelength (§9-1); Josephson interference
    becomes a magnetometer estimate (§21-9). Every abstract quantity gets one
    concrete magnitude.
14. **Announce what is left unfinished.** Chapter 16 says openly the business
    is left open-ended (§16-1). Say what you are not covering instead of
    smoothing over it.
15. **Mark asserted versus derived.** The Chapter 21 seminar says up front that
    steps will be skipped and the reader should believe the results more or
    less (§21-1). When you skip algebra, say so and state what comes out.

## How equations are introduced

Order is strict: **phenomenon → rule in words → symbol.** The three rules of
quantum mechanics are first observed (Chapter 1), then written as a numbered
summary in words with equations attached (§1-7), then given a notation
(Chapter 3) with a reading guide: what is right of the bar is the starting
condition, what is left is the final condition, and the expression is read
right to left (§3-1).

- Every new symbol is named, motivated, and sometimes apologized for (footnote
  on reusing μ and E, §9-1).
- Pauli matrices are introduced with "there is no new physics here" and then
  solved for component by component (§11-1), with the honest note that
  professionals memorize them.
- Short derivations are shown (normalization of a state, §9-1); long ones are
  skipped with notice (Chapter 21).
- Conventions are treated as choices: kets versus bras is an arbitrary
  choice (§8-3); a dipole sign is fixed to match other authors (§9-1);
  normalization is discovered as a problem and then repaired rather than
  imposed (§9-1).

## Voice: not imitated

The book's voice (its pronoun habits, "Now," and "Suppose" as openers,
rhetorical questions answered with "Well, ...", the closing exclamation) is
deliberately left out of this file. The register is a rule set, not a voice;
see `SKILL.md`. What carries over from the voice is only what is also a rule:
short declarative sentences, honest hedges ("roughly", "it turns out") in place
of evasive ones, and the reader's likely question asked aloud and answered at
once (move 11).

## Handling the unknown

- "The rule works" and "why it works" are separated every time: no machinery
  behind the amplitude rules (§1-7); hidden-variable proposals are argued
  against, then "no one has figured a way out" (§1-7).
- Unknowns are stated as facts about the field and dated: strangeness
  conservation, "nobody knows, nature just works that way" (§11-5); ammonia
  parameters that must be measured because nobody has computed them (§9-1).
- Overreach is policed in both directions: the positivist claim that
  unmeasurable ideas have no place is refused (§2-6), and philosophy is kept
  out of the physics as much as possible.

## Anti-patterns the book refuses

- Historical-order curricula that start with classical mechanics and the
  Schrödinger equation (§3-1 preamble): the "advanced" parts are called the
  simplest.
- Apologizing to classical intuition: Chapter 5 makes no attempt to connect to
  classical mechanics and avoids the words "angular momentum" until later.
- Pure abstraction and pure hand-waving, both named as failure modes (§3-1).
- Unexplained notation.
- Pretending to derive what is postulated.
- Fake completeness.

## Costs of the style

- **No problem sets.** The Preface admits there are no lectures on solving
  problems and that exam results were a failure. If the user needs to compute
  something, that is a request for visible steps: keep Feynman and override
  that one knob (see Mixed requests in `registers.md`), or they can switch to
  Griffiths ([style-griffiths.md](style-griffiths.md)).
- **Hard to skim.** Rules live inside narrative; a definition may sit at the end
  of a three-page analogy. In an answer, state the one-sentence result where
  the reader can find it, outside the narrative.
- **Idiosyncratic order and notation.** Two-state-first, nonstandard symbols;
  the author notes his order is the reverse of most books (§16-1). Always
  state the convention and name the standard alternative.
- **Deliberate early imprecision** can mislead a reader who never reaches the
  later correction. Say when the precise version will come.
- **Assumes a strong, patient reader.** The Epilogue admits some readers were
  lost.

## Rule card

Begin with a concrete apparatus or situation the reader can picture, and say
what would be measured before naming any symbol. Say what classical intuition
predicts, then show where it fails, and state the failure plainly. Choose the
smallest system that shows the effect, work it completely, then say how to
generalize by copying the pattern. Introduce each symbol only when the argument
needs it, give it a name and a reading order, and say when a convention is
arbitrary. Gloss every field term in the sentence where it first appears. Label every statement as observed, derived, assumed, or put in by
hand; when you skip algebra, say so and say what comes out. Ask the reader's
likely question aloud and answer it at once. Anchor every abstraction in a
number, a frequency, or a device. When the reason is unknown, say nobody knows
and date it; never invent machinery. Admit roughness, name what you are
leaving out, and treat the reader's confusion as the correct response to
strange facts. Follow the moves, not the voice.
