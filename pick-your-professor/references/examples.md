# Examples

Use these as behavioral targets, not scripts to copy verbatim. Preserve the rule
while adapting vocabulary and language to the user's field.

## Example 1 — A hard question does not set a register (negative)

**User**
> What's the difference between the Kubo formula and the Boltzmann transport
> approach for computing conductivity in disordered metals?

**Good response**

Answer at normal density. Do not set a register, do not offer one, do not add a
closing line about "explaining it more simply".

**Why this is good**

- Nothing in the prompt asks for a register or complains about density.
- A hard topic is not a trigger. Offering a register here tells a specialist
  they look lost, which is the over-firing failure the skill exists to avoid.

## Example 2 — Being new is not a register request (negative)

**User**
> I'm new to phylogenetics. What is a molecular clock?

**Good response**

Answer the question, at whatever density the default would produce. Do not set
a register, do not list prerequisites, do not announce a walkthrough.

**Why this is good**

- "New to X" describes the user; it does not ask for a register. Only an
  explicit request or complaint sets one.
- If they later say "that was too technical", Example 4 applies.
- If they want to be walked into the field, that is a different skill.

## Example 3 — An explicit request, then persistence

**User**
> Feynman style from now on. Why do batteries lose capacity in the cold?

**Good response**

> Picture the battery as two sponges with charged atoms, *lithium ions*, soaking
> between them. Discharging means the ions have to squeeze out of one sponge,
> swim through a liquid, and soak into the other. Cold makes that liquid
> thicker, the way honey stiffens in a fridge, so the ions move slower. ...

Every term is glossed in its own sentence; the answer opens with a picture; the
analogy's limit is stated later ("the sponge picture breaks down for ...").
The magnitude survives: at −20 °C a lithium-ion cell can deliver roughly half
its room-temperature capacity, much of it recovered on warming.

**User** (next turn)
> What's the boiling point of ethanol?

**Good response**

> About 78 °C at normal air pressure, meaning at sea level; higher up, where
> the air presses less, it boils a little cooler.

**Why this is good**

- The register held on a short factual question.
- No re-announcement of the register, no reminder of what Feynman means.

## Example 4 — Stepping down on a complaint

**User** (after a default-density answer about p-values)
> That was too technical.

**Good response**

Re-answer the same p-value question in Griffiths: define *null hypothesis*,
*test statistic* and *p-value* once each, then derive in visible steps and work
one case. End with one line:

> Want me to keep answers at this level for the rest of the session?

**Why this is good**

- It is a re-answer, not the old answer padded out.
- One register lighter (off → Griffiths), not a jump to a teaching sequence.
- It does not ask "what's your background?". The complaint already answered
  that.

## Example 5 — A Chinese complaint

**User** (after a dense answer about the Kramers–Kronig relations)
> 讲人话，太专业了。

**Good response**

Step down one register and reply entirely in Chinese. Keep the content: that
absorption and refraction are linked, the causality assumption behind it, and
the practical caveat that you need absorption data over a wide frequency range.

**Why this is good**

- It steps down without asking which register the user wants.
- The language follows the user.
- The causality assumption and the data-range caveat survive the step down.

## Example 6 — A brevity request is not a register (negative)

**User**
> One line: is O(n log n) faster than O(n²) for large n?

**Good response**

> Yes: for large n, n log n grows far more slowly than n².

**Why this is good**

- "One line" is a length request, not a register. The answer is one line.
- No explanation of registers and no offer of a choice.
