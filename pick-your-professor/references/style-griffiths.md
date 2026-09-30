# Explanation style: Griffiths & Schroeter, Introduction to Quantum Mechanics (3e)

Source: D. J. Griffiths and D. F. Schroeter, *Introduction to Quantum
Mechanics*, 3rd ed. (Cambridge University Press, 2018). Section numbers below
are the book's own (e.g. §2.3.1 = Chapter 2, section 3, subsection 1).

This file describes **how the book explains**, not what it explains. It is the
move catalogue behind the **Griffiths** register. Load it after `registers.md`,
before the first answer in Griffiths. The register's rules in `SKILL.md` and
`registers.md` win wherever this file seems to disagree: in particular, every
term is defined on first use, and nothing here licenses imitating the book's
voice.

## Stance

- **Do first, interpret later, but never pretend interpretation does not
  exist.** The Preface says the book teaches you how to *do* quantum mechanics
  and defers what it means to the Afterword, because you cannot discuss meaning
  before you know what the theory does. Yet §1.2 lays out the realist,
  orthodox, and agnostic positions and Bell's theorem in outline, and invites
  the impatient reader to skip ahead. The debt is paid in full in Chapter 12.
- **Tools over tool-lessons.** Mathematics is a tool; the stated instinct is to
  hand over shovels and start digging rather than lecture on the shovel first
  (Preface). A reader who gets stuck is told where to look it up.
- **Problems are the curriculum.** Worked examples are deliberately fewer than
  usual; important material lives in the problems, because there is no
  substitute for exercise (Preface). Problems are star-rated for essential,
  harder, and long, placed at section ends and chapter ends respectively.
- **Reader as collaborator.** "I" is kept even with two authors because it is
  more intimate; "we" means author and reader calculating together (Preface).
- **Rigor is instrumental.** Completeness of eigenfunctions is assumed with a
  wry admission that physicists hope for the best (§2.2). The technically
  correct definition of Hilbert space is quarantined in a footnote (§3.1). But
  where rigor matters physically (why separable solutions suffice, §2.1; why
  the energy-time relation is a different beast, §3.5.3) the text slows down
  and insists.

## Explanatory moves

1. **Classical program first, then the quantum replacement.** Chapter 1 opens
   with Newton's second law and what it lets you compute, then presents the
   Schrödinger equation as its logical analogue (§1.1). Same pattern for the
   oscillator (Hooke's law, §2.3), spin (orbital versus daily rotation of the
   Earth, §4.4), scattering (marble off a bowling ball, §10.1), symmetry
   (rotating a square of paper, §6.1). Use to open the core of an answer.
   In the Griffiths register, the opener is the classical or everyday version
   of the *same* system, not a different one. Where the book reaches for a
   different system (the Earth's rotation for spin, §4.4), it says at once
   where the comparison fails; do the same, or leave it out.
2. **State the equation, then unpack the symbols one by one.** The equation is
   written first; then i, ħ, and the role of initial conditions are explained
   (§1.1). Never leave a symbol undefined past the sentence it appears in.
3. **Motivate a toy model and defend it.** The infinite square well is admitted
   to be artificial and the reader is urged to treat it with respect as the
   test case for later machinery (§2.2). When you use a toy, say why it earns
   its place.
4. **Solve the simplest case completely, then extract general properties as a
   numbered list.** After the square well: parity, node count, orthogonality,
   completeness, each tagged as universal or special to this potential (§2.2).
   Stationary states get three numbered reasons they matter (§2.1).
5. **Two routes to one result, easier first.** The oscillator's algebraic
   (ladder) method comes first because it is quicker and more fun; the
   power-series method is promised and delivered later (§2.3). Use when the
   field has a slick method and a brute-force one.
6. **Anticipated objection as a hinge.** "But wait, what if I apply the
   lowering operator repeatedly?" (§2.3.1); "you have every right to ask what
   is so great about separable solutions" (§2.1). Voice the objection in the
   reader's words, then answer it.
7. **Name a step as a trick and reuse the name.** Fourier's trick (§2.2)
   recurs in §3.1 and Chapter 11; the wiggle factor (§2.1) recurs in Chapter
   11. Give recurring manoeuvres a short name so they can be called later.
8. **Claim, proof, QED for the load-bearing step.** The raising-operator
   theorem is set off as a displayed claim followed by a proof (§2.3.1). The
   orthogonality proof is followed by asking where it fails for equal indices
   (§2.2). Isolate the one step everything rests on.
9. **Explicit Warning about the standard technical error.** Operators are
   slippery, always use a test function (§2.3.1); the mean of a square versus
   the square of a mean (§1.3.1); a letter doing double duty (§4.1 footnote).
   One Warning per answer, at most, aimed at the mistake practitioners
   actually make.
10. **Deferred justification with an IOU.** Boundary conditions: trust me for
    now, with a pointer to §2.5. Bell's argument deferred from §1.2 to the
    Afterword. When you defer, say where the debt is paid.
11. **Recap from a different angle after a dense stretch.** After the
    stationary-state derivation the text pauses to recapitulate and restates
    the whole procedure as an algorithm (§2.1). Use after a long derivation.
12. **Example boxes as short, fully executed calculations.** An Example applies
    the operator just derived and gets the next state (§2.3.1); another raises
    the well floor and remarks that first order is exact, of course (§7.1).
    Examples end with a sanity check (hermitian, trace one, §12.5). The
    exception is Example 1.1, which is qualitative and uses real experimental
    data.
13. **Footnotes quarantine subtleties, history, terminology gripes, and
    alternatives.** Bohm and many-worlds acknowledged and deferred (§1.2);
    axiomatic status of the commutator (§2.3.1); why spin-first is rejected
    (§4.4). In a chat reply, the equivalent is a short indented aside after
    the main argument, never inside it.
14. **Flag convention versus physics.** A prefactor is there only to make
    results look nicer (§2.3.1); a phase carries no physical significance
    (§2.2); numbering oscillator states from zero is a custom (§2.3.1).
15. **Point outward at the end.** Almost every hard idea ends with a pointer to
    one readable article (American Journal of Physics, Physics Today). One
    pointer, not a bibliography. Never name an article you have not verified in
    this session without marking it as unverified.

## How equations are introduced

Postulate-first at the top level, derive-first everywhere below it. The
Schrödinger equation (§1.1), Born's rule (§1.2), and the spin commutation
relations (§4.4) are laid down; a footnote labels the spin relations as
postulates while noting the orbital ones were derived and both follow from
rotational invariance in Chapter 6. Below the postulates everything is derived
in full, including algebra most texts skip.

- Symbols are introduced with a defining "≡" and a parenthetical meaning
  (k ≡ √(2mE)/ħ, §2.2; a "tidy up the notation" step for hydrogen, §4.2).
- Constants are named with a forward reference: the separation constant is
  called E "for reasons that will appear in a moment", and the reason arrives
  two pages later (§2.1).
- Normalization is done immediately after a solution is found, and the choice
  of the real positive root is stated as a convention (§2.3.1).
- Definitions are announced ("We define...", "We call this...") and results are
  announced ("Conclusion:", "This is the famous..."). Important relations are
  boxed.
- Sloppy but standard language is called out and then tolerated: lowercase
  versus uppercase psi (§2.1), ket versus spinor (§4.4), loose notation for
  uncertainties (§3.5.2), "terrible language" for differential cross-section
  (§10.1).

## Voice: not imitated

The book's voice (the authorial "I", dry one-clause humor, "check it!"
parentheticals) is deliberately left out of this file. The register is a rule
set, not a voice; see `SKILL.md`. What carries over is only what is also a rule:
short-to-medium paragraphs, opinion labelled as opinion, definitions and
results announced as such, and asides kept out of the main argument (move 13).

## Handling the unknown and contested

- Machinery and foundations are separated by structure (the Afterword) and by
  labelling. Opinions are marked with "I think", "I believe", "I prefer".
- The orthodox platform is adopted for pedagogy, with alternatives named in a
  footnote (§1.2); the Afterword calls it the conceptually simplest and
  majority view and then says the author cannot believe it is the end of the
  story (§12.6).
- Open problems are stated bluntly: no characterization of measurement is
  entirely satisfactory; decoherence is not fully understood (§12.5).
- Kinds of ignorance are distinguished: quantum indeterminacy versus classical
  ignorance in mixed states; subsystem versus ignorance density matrices
  (§12.5).

## Anti-patterns the book refuses

- Interpreting before calculating, and equally, pretending interpretation does
  not exist.
- Mystical language about wave-particle duality; a "profound"-sounding
  statement is insisted to be precise (§4.4).
- Elaborate mathematics lectures before use; proving completeness.
- Changing notation mid-stream even when a letter is overloaded (§4.1).
- Starting with spin, because abstraction costs conceptual footing (§4.4).
- Hiding when a result is a convention, when a statement is too strong, or
  when the author's own interest has run out (§8.3).

## Costs of the style

- **Thin motivation for top-level postulates.** A reader who wants to know why
  the Schrödinger equation has that form gets an analogy and a footnote. Pair
  with one sentence on why the postulate has the form it does, or say plainly
  that it is laid down, not derived.
- **Toy models can feel disconnected from experiment.** Add one real
  measurement or number per answer.
- **The text alone is incomplete.** Skipping the problems skips degeneracy,
  Bell's classical counterexample, and more. In a chat reply, fold the
  essential problem content into the answer as its one worked case. Do not add
  exercises or comprehension checks; a register never starts a teaching
  sequence.
- **Tolerated sloppy language** can propagate confusion. If you tolerate it,
  say so each time.

## Rule card

Open with the classical or everyday version of the problem and say exactly
what it lets you compute. State the governing equation or postulate outright,
then define every symbol in one sentence each, marking what is a definition,
what is a convention chosen for tidiness, and what is a result. Pick the
simplest nontrivial case and solve it completely, normalizing as you go; then
list the general properties it reveals, tagging each as special or universal.
Show the easier of two methods first and promise the other. Anticipate the
reader's objection in their own words and answer it. Set the crucial step as
claim then proof. Put every subtlety, alternative convention, or historical
remark in a short aside after the argument. Warn explicitly about the standard
mistake. Label opinion as opinion. Say plainly when something is unproved,
unknown, or merely assumed, and point to one good article, verified or marked
as unverified. End with the one-sentence lesson. Follow the moves, not the
voice.
