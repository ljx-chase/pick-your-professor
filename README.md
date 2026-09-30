<div align="center">

<img src="docs/logo.png" alt="Pick Your Professor: set how densely it explains. It holds for the whole session." width="720"/>

<p>
<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License"/></a>
<img src="https://img.shields.io/badge/version-v1.2.0-blue?style=flat-square" alt="Version"/>
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

## The three registers

<p align="center">
<img src="docs/registers.png" alt="Three registers: Feynman (picture first), Griffiths (textbook, default) and Landau (compact)" width="820"/>
</p>

Each register sets three knobs.

| | Feynman · `picture first` | Griffiths · `textbook` | Landau · `compact` |
|---|---|---|---|
| **Unexplained terms** | Zero. Every term glossed in the sentence it appears in. | Zero on first use, then free. | No limit. |
| **What carries the argument** | A different system you already understand from ordinary life, with the same structure, built up one complication at a time. It says what the analogy borrows, rules out the wrong conclusion it invites, and where it stops working. If nothing familiar fits, it says so instead of forcing one. | A simplified case of the real system: a limit, a special case, a lower dimension. It shows where the simplification gives the wrong answer. | The formalism itself. |
| **Steps** | Equations optional and last, every symbol named. Skipped steps are announced. | Every step visible, assumptions flagged where they enter, one worked case. | Result first, derivation sketched, conditions of validity stated. |

This is density, not depth. Every register keeps the assumptions, magnitudes and
caveats; only the vocabulary load, the carrier and the order change. Plain names
work too: `picture first`, `textbook`, `compact`.

**Mixing.** An explicit instruction overrides the one knob it names, for that
answer only. "Feynman, but show the algebra" keeps zero unexplained terms and the
analogy, and makes the derivation visible. It does not switch to Griffiths.

This is not an onboarding tool. It changes how an answer is written, not what gets taught in what order. If you want to be walked into a field you do not know yet, see [research-field-onboarding](https://github.com/ljx-chase/research-field-onboarding), which has its own explanation styles governing the teaching sequence.

## One question, three registers

The replies below come from test runs of this version: a fresh agent session
with only the skill's files loaded, one run each, with the register named in
the message. The wording is unedited; only the equation markup was adapted so
that GitHub renders it.

> *Why does the current in a scanning tunneling microscope change about tenfold
> when the tip moves just one ångström?*

| | What carries the argument | Length |
|---|---|---|
| **Feynman** | A stack of tinted glass: each sheet cuts the light by the same factor | ~1,190 words |
| **Griffiths** | The same setup simplified: a one-dimensional rectangular barrier between two metals | ~1,210 words |
| **Landau** | I ∝ e<sup>−2κd</sup>, Tersoff–Hamann, WKB | ~350 words |
| **Feynman + algebra** | Tracing paper thinned into fog, then the Schrödinger equation with every symbol named | ~1,670 words |

All four land on about 8–10× per ångström for a 4–5 eV work function. All four
keep the same caveats: a small bias, a gap of several ångströms (the current
levels off near contact), and a measured factor often below 10 on real, less
clean surfaces. The two Feynman replies also say what the analogy borrows, name
the wrong conclusion it invites (that the gap absorbs electrons), and label each
claim as derived, measured or assumed.

<details>
<summary><b>Feynman</b></summary>

**The short answer.** Every extra ångström of gap cuts the current by the *same fraction*, however wide the gap already is. The gap multiplies the current down; it does not subtract from it. How big that fraction is depends on how tightly the metal holds on to its electrons. For ordinary metals that works out to roughly a factor of ten per ångström.

What follows is a **derived** result: it comes out of the rules that govern electrons at this scale (quantum mechanics), plus one **measured** number. The tenfold figure itself is **observed** in the lab.

---

### A stack of tinted glass

Leave the microscope aside for a moment and think about sheets of tinted glass.

Say one sheet lets through a third of the light that hits it. Put a second sheet behind it. The second sheet also passes a third of what *reaches* it, so a ninth gets through. Three sheets pass a twenty-seventh, and four pass an eighty-first. Adding one sheet never takes away a fixed *amount* of light. It divides what is left by three. That holds whether the stack is two sheets thick or twenty.

**First complication: make the sheets thinner.** Slice each sheet in half, so each half-sheet passes a bit more than half the light (about 58%, because 58% of 58% is a third). A given *thickness* of glass still divides the light by three. The count of sheets stops mattering. What matters is the fraction lost per millimetre, and the loss compounds smoothly with thickness.

**Second complication: use darker glass.** Darker glass loses a bigger fraction per millimetre, and because the losses compound, a small difference in darkness turns into a big difference after a few millimetres. At one third per sheet, two sheets pass a ninth. At one fifth per sheet, two sheets pass a twenty-fifth.

That is the whole shape of the answer. Here is how it maps onto the microscope.

---

### Back to the microscope

The tip and the surface are two pieces of metal separated by a few ångströms of empty space. By everyday rules an electron cannot cross that space at all. Inside a metal the electrons are held in. Pulling one out takes a definite amount of energy, called the metal's **work function**: about 4 to 5 electron-volts for common metals (one electron-volt is the energy an electron picks up when it is pushed across one volt). This number is **measured**, for example by shining light on the metal and finding the weakest light that knocks electrons out. The small voltage across the microscope gap is far too little to supply that energy.

Quantum mechanics says the electron still gets across sometimes. It describes the electron by a spread-out quantity, usually called its "wave", and the square of the wave's size at a place gives the chance of finding the electron there. In a region where the electron lacks the energy to be, the wave does not stop dead at the edge. It dies away, losing the **same fraction of its size for each equal step** into the region. That is the tinted glass: the empty gap acts as the stack, and each ångström acts as one more sheet. The larger the energy shortfall (the work function), the darker the glass. The current is simply how many electrons make it across per second, so it follows the chance of crossing.

**Why the electron is described by such a wave, nobody knows.** It is the rule that works, and it has been tested to great precision. There is no deeper mechanism behind it that I can give you.

---

### What the glass picture borrows, and the wrong conclusion it invites

The picture borrows exactly two things: **the same fraction lost per equal step of distance**, and **a stronger barrier makes each step cost more**.

The tempting wrong conclusion is that the gap *soaks up* electrons the way tinted glass soaks up light, so that the electrons arriving at the surface are dimmed or weakened. That is wrong. Empty space absorbs nothing. Each electron either crosses with its full energy or bounces back into the tip. What shrinks with each ångström is the *chance* of crossing, and nothing is lost along the way.

**Where the picture stops working:** light absorbed by glass is gone and turns into heat. An electron that fails to cross is reflected and is still there. Also, the "darkness" of the gap is not a fixed property like the tint of glass. It depends on the electron's own energy, so it shifts somewhat with the applied voltage.

---

### The number

With an energy shortfall of 4 to 5 electron-volts, the quantum rule gives this: across each ångström, the size of the wave shrinks by a factor of about 2.8 to 3.1. The chance of crossing goes as the *square* of the size, so the current falls by about **8 to 10 times per ångström**. That is the tenfold you asked about (**derived**, and it agrees with the **observed** value in clean conditions).

For readers who want it as a formula (optional):

current ∝ exp(−2 · d · √(2 · m · φ) / ħ)

Here *d* is the gap width, *m* is the electron's mass, *φ* is the energy shortfall (roughly the work function), *ħ* is Planck's constant divided by 2π (the constant that sets the size of quantum effects), and "exp" means the number e ≈ 2.718 raised to that power. In convenient units, √(2mφ)/ħ ≈ 0.51 × √(φ in electron-volts) per ångström. Plugging in:

| energy shortfall φ | current drops per ångström |
| --- | --- |
| 5 eV | ≈ 10× |
| 4 eV | ≈ 8× |
| 2 eV | ≈ 4× |
| 1 eV | ≈ 3× |

### What this assumes, and when it fails

- **The gap is treated as a flat, uniform wall**, with the same shortfall all the way across (**assumed**, a simplification). In reality the pull each electron feels toward the nearby metal rounds off and lowers the wall. So the shortfall that experiments infer from the current, called the "apparent barrier height", often comes out below the work function.
- **Clean conditions.** With dirt, adsorbed water or other films on the tip or surface, the measured factor per ångström is often well under ten, and a few times per ångström is common. The tenfold figure belongs to clean metal in vacuum.
- **Small voltage**, much less than the work function. At voltages of several volts the electrons get a real push and the simple picture changes.
- **A gap of several ångströms.** When the tip comes within a couple of ångströms of contact, the atoms start to touch and the current stops following this rule; it levels off instead of rising another tenfold.

A consequence worth knowing: because each ångström costs a factor of ten, nearly all the current flows through the single atom at the very front of the tip. An atom set back by just one ångström contributes only about a tenth as much. That is why the microscope can see individual atoms, even with a tip that looks blunt by everyday standards.

</details>

<details>
<summary><b>Griffiths</b></summary>

**Short answer:** the current depends *exponentially* on the gap, not as a power of it. Each extra ångström multiplies it by a fixed factor, e<sup>−2κ·1 Å</sup>. For a typical metal that factor comes out close to 1/10.

## The classical version of the same setup

Start with the setup itself. There is a metal tip, a metal sample, and a vacuum gap of width *d* between them, a few ångströms (1 Å = 10⁻¹⁰ m). A small voltage *V*, called the **bias** (definition), is applied across the gap.

An electron inside a metal is bound. Pulling it out into the vacuum costs a minimum energy called the **work function** φ (definition). For common metals φ is about 4–5.5 eV. So from the electron's point of view the vacuum gap is a wall of potential energy about φ higher than its own energy. A region like this is called a **potential barrier** (definition).

Classically, an electron that doesn't have enough energy to get over the wall bounces back, every time. The classical prediction is therefore a current of **exactly zero** at any gap width: a 5 Å gap and a 50 Å gap block it equally. Quantum mechanics gives a different answer, and the rest of this is about how it differs.

## The simplified case: a rectangular barrier in one dimension

Here are the assumptions. Each one gets revisited below.

1. **One dimension.** The electron moves straight across the gap, along *x*.
2. **Rectangular barrier.** The potential energy is flat at height *U₀* inside the gap, 0 < *x* < *d*, and zero in the metals on either side.
3. **Low bias.** *eV* ≪ φ, so the voltage barely tilts the top of the barrier. The electrons that carry the current sit at the **Fermi level** (definition: the energy of the highest filled electron states in the metal). For them, *U₀* − *E* ≈ φ.

Inside the barrier the time-independent Schrödinger equation reads

  −(ħ²/2m) ψ″(x) + U₀ ψ(x) = E ψ(x).

Here ψ is the electron's **wavefunction**, and |ψ|² gives the probability of finding the electron at *x*. *m* is the electron mass, ħ is Planck's constant divided by 2π, and *E* is the electron's energy. Rearranging gives

  ψ″ = κ² ψ,  with κ ≡ √(2m(U₀ − E)) / ħ.

Call κ the **decay constant** (definition). It has units of inverse length.

This equation doesn't have the oscillating solutions you get outside the barrier. Its solutions are e<sup>−κx</sup> and e<sup>+κx</sup>. So the wavefunction doesn't stop at the wall. It leaks in and falls off exponentially. If the gap is thin enough, a small amplitude survives to the far side, and the electron can appear in the other metal. Crossing a region that is classically forbidden this way is called **tunneling** (definition).

**The load-bearing step.** Across the gap the amplitude drops by a factor of about e<sup>−κd</sup>. A probability is an amplitude squared, so the probability of getting through, the **transmission probability** *T* (definition), drops by the square of that:

  T ≈ 16 (E/U₀)(1 − E/U₀) · e<sup>−2κd</sup>  (result, valid when κd ≫ 1).

The prefactor in front changes slowly with *d*. The exponential is what matters. (A fourth assumption comes in here: κd ≫ 1, the thick-barrier limit. At STM gaps κd is about 5–10, so this holds.)

At low bias the current is (number of electrons arriving at the barrier in the energy window *eV*) × (chance each one gets through). The first factor doesn't depend on *d*, so

  I ∝ V · e<sup>−2κd</sup>  (result).

Move the tip back by Δ*d* and the *d*-independent parts cancel:

  **I(d + Δd) / I(d) = e<sup>−2κ Δd</sup>.**

This is the whole answer. The ratio doesn't depend on where you start, only on how far you move. Every ångström costs the same factor.

**Warning:** don't drop the 2. The *amplitude* decays as e<sup>−κd</sup>, but the current follows the *probability*, which decays as e<sup>−2κd</sup>. Leaving out the 2 gives you about a factor of 3 per ångström instead of about 10.

## Worked case

Take φ = 5 eV, a representative metal value. A convenient numerical form is κ [Å⁻¹] ≈ 0.512 √(φ [eV]) (result: this is just the definition of κ with the constants plugged in). Then:

- κ ≈ 0.512 × √5 ≈ 1.15 Å⁻¹
- 2κ × (1 Å) ≈ 2.29
- e<sup>2.29</sup> ≈ **9.9**

That is about tenfold per ångström. With φ = 4 eV the same steps give about 7.8. So "about tenfold" is the right rule of thumb for clean metals.

The same numbers show why an STM can measure heights so finely. A change of just 0.1 Å changes the current by a factor of e<sup>0.229</sup> ≈ 1.26, about 26%, which is easy to detect. The instrument's **feedback loop** (definition: circuitry that moves the tip up or down to keep the current constant) turns that sensitivity into height resolution of a few picometres.

## Where the simplified picture gives the wrong answer

The rectangular model says the current keeps rising tenfold per ångström right up to the point where tip and sample touch. **That is wrong.** Two things happen as the gap closes:

- **The barrier isn't rectangular, and it gets lower as the gap shrinks.** An electron in the gap is attracted by the charge it induces in both metals (the *image-charge* effect: the metal's electrons rearrange as if a mirror-image charge of opposite sign sat inside it). This rounds off the corners of the barrier and lowers its top. So the barrier height you measure from how the current changes with distance, usually called the **apparent barrier height** (definition, and a convention: the φ you'd infer from d ln I / d d = −2√(2mφ)/ħ), often comes out below the tabulated work function. It also depends on the state of the tip.
- **At contact the exponential stops.** Once the barrier has collapsed and a single atom bridges the gap, the current levels off. The conductance settles near the **conductance quantum** G₀ = 2e²/h ≈ 77.5 µS (definition), the value for one fully open conduction channel. It stops growing tenfold per ångström.

The other assumptions fail in their own regimes:

- **High bias** (*eV* comparable to φ): the voltage tilts the barrier so much that κ depends on *V*, and the simple *I* ∝ *V* e<sup>−2κd</sup> no longer holds.
- **Three dimensions:** an electron with some sideways momentum has less energy left for crossing the gap, so it sees a larger effective κ. The current is therefore carried mostly by electrons heading straight across. This is also why most of the current flows through the one atom at the very front of the tip. That atom sits about 1 Å closer than its neighbours, so it carries about ten times more current, and this is what lets an STM resolve individual atoms.

**Lesson:** a wavefunction decays exponentially through a region where the electron doesn't have enough energy to be. The current goes as the square of that decaying amplitude. With a barrier of about 5 eV, the square falls by about e<sup>−2.3</sup> ≈ 1/10 per ångström.

> *Aside.* The exponential distance dependence and its use for imaging surfaces were the basis of the original STM work by Binnig, Rohrer and co-workers at IBM Zürich in the early 1980s. The first paper is usually cited as G. Binnig, H. Rohrer, Ch. Gerber, E. Weibel, *Phys. Rev. Lett.* **49**, 57 (1982). I'm giving that citation from memory and haven't verified it. For the 3D treatment of the tip, look up the Tersoff–Hamann model (also from memory, unverified).

</details>

<details>
<summary><b>Landau</b></summary>

$`I \propto e^{-2\kappa d}`$, with $`\kappa = \sqrt{2m\phi}/\hbar`$. In practical units $`\kappa\,[\text{Å}^{-1}] = 0.512\sqrt{\phi\,[\text{eV}]}`$. For $`\phi \approx 4\text{–}5`$ eV (typical metal work functions), $`\kappa \approx 1.0\text{–}1.15\ \text{Å}^{-1}`$, so $`e^{2\kappa \cdot 1\,\text{Å}} \approx 8\text{–}10`$. A factor of exactly 10 per Å corresponds to $`2\kappa = \ln 10 = 2.30\ \text{Å}^{-1}`$, i.e. $`\phi \approx 5.0`$ eV.

**Sketch.** Treat the gap as a 1D rectangular barrier of height $`\phi \approx (\phi_t + \phi_s)/2`$ measured from $`E_F`$. At low bias, Bardeen's transfer-Hamiltonian result in the Tersoff–Hamann limit (s-wave tip) gives $`I \propto V\,\rho_t(E_F)\,\rho_s(\mathbf r_0, E_F)`$. Here $`\rho_s(\mathbf r_0)`$ is the sample LDOS at the tip centre. Outside the surface, $`\psi_s \sim e^{-\kappa z}`$, so $`\rho_s(\mathbf r_0) \propto e^{-2\kappa(d+R)}`$. The $`d`$-dependence of the prefactors is algebraic and negligible next to the exponential. WKB gives the same exponent: $`T \approx e^{-2\int \kappa(z)\,dz}`$.

Inverting gives the apparent barrier height: $`\phi_A = \frac{\hbar^2}{8m}\left(\frac{d\ln I}{ds}\right)^2 = 0.952\ \text{eV·Å}^2 \times \left(\frac{d\ln I}{ds}\right)^2`$.

**Validity and corrections.**
- $`eV \ll \phi`$. At finite bias the effective barrier is $`\approx \phi - e|V|/2`$, which lowers $`\kappa`$. For $`eV \gtrsim \phi`$ you are in the Fowler–Nordheim regime.
- States with $`k_\parallel \neq 0`$ decay faster: $`\kappa^2 = 2m\phi/\hbar^2 + k_\parallel^2`$. Tunnelling therefore samples near-$`\bar\Gamma`$ states, and the corrugation of high-$`k_\parallel`$ Fourier components decays much faster than $`I`$ does.
- The image potential rounds and lowers the barrier. Measured $`\phi_A`$ is typically 1–4 eV rather than the full work function, so the decade-per-Å figure is an upper-end estimate. Under ambient or contaminated conditions, $`\phi_A`$ can be well below 1 eV.
- At $`d \lesssim 3\text{–}5`$ Å the barrier collapses toward point contact, $`G \to G_0 = 2e^2/h`$, and the exponential law fails. Tip–sample forces also deform the junction, so the true gap differs from the piezo displacement $`s`$.
- The exponent assumes elastic, single-barrier tunnelling. Inelastic channels and resonant (adsorbate-mediated) channels modify the prefactor. They do not change the leading $`e^{-2\kappa d}`$ scaling unless they introduce states inside the barrier.

This steepness is also why lateral resolution comes from roughly the single front-most tip atom: an atom recessed by 1 Å contributes about 10% as much current.

</details>

<details>
<summary><b>Feynman, but show the algebra</b></summary>

**Short answer:** the chance that an electron gets across the gap drops by the same fraction for every extra ångström of gap, and for the metals normally used that fraction works out to about 1 in 8 to 1 in 10 per ångström. The algebra is below.

## What kind of statement this is

It combines two things. One is a **derived** rule: an electron's chance of crossing a gap it does not have enough energy for falls off *exponentially* with the width of the gap (each extra slice of gap multiplies the chance by the same factor). The other is a **measured** number: how much energy it takes to pull an electron out of the metal. Put the two together and the factor of ten comes out. No new idea is needed beyond those two.

## A parallel: light through a stack of tracing paper

Shine a torch through one sheet of tracing paper, and say one third of the light gets through. Add a second sheet. It sees only the light the first sheet let through, and passes a third of *that*, so 1/9 gets through. A third sheet gives 1/27. The rule is simple: **every sheet you add cuts what you get by the same factor, no matter how many sheets are already there.**

First complication: make the sheets thinner and thinner until you have something smooth, like fog. Now every millimetre of fog passes the same fraction of the light that reaches it. That is what "exponential" means: equal steps in thickness give equal *factors*, not equal *amounts*.

Second complication: make the fog denser. Each millimetre now passes a smaller fraction, so the light dies off faster with distance. How dense the fog is sets the factor per millimetre.

Third complication: suppose you can only read a light meter on the far side, and you want to know what happens if the fog gets 1 mm thicker. You do not need to know how bright the torch is. The meter reading drops by the per-millimetre factor whether the torch is bright or dim.

What the fog borrows, and all it borrows: **equal slices of gap multiply the result by the same fraction, and a single number (the "density") sets that fraction.**

The tempting wrong conclusion: fog soaks up light, so you might think the gap in a microscope soaks up electrons, stopping them partway or draining their energy. It does not. The gap is empty; nothing there absorbs anything. An electron that does not get across simply bounces back into the metal it came from, and one that does get across arrives with its energy intact. Nobody ever finds an electron "halfway, slowed down". The fog has the right arithmetic for the wrong reason.

Where the parallel stops: in fog the fraction is set by stuff in the way. In the microscope there is no stuff. What sets the fraction is how far short the electron is of the energy it would need to be in the gap at all. Why an electron can be found in a region it does not have the energy for is something no everyday system does. The rule that says it happens is observed and has been checked very precisely; nobody has a machinery underneath it, and I will not invent one. What follows describes what the rule predicts.

## Now the real thing

A scanning tunneling microscope holds a sharp metal tip a few ångströms above a metal surface, with a small voltage between them (the *bias voltage*, typically a few thousandths of a volt to about a volt). Classically no current should flow: an electron inside a metal is held in by an energy step at the surface, and the empty gap is on the wrong side of that step. The size of the step is the *work function*, written φ, which is the energy needed to pull one electron out of the metal into empty space. It is **measured**, and for common tip and surface metals it is about 4 to 5 *electronvolts* (eV; one eV is the energy an electron gains when it moves through one volt, 1 eV = 1.602 × 10⁻¹⁹ J).

Yet a small current does flow. Electrons crossing a gap they classically cannot cross is called *tunneling*. Here is the algebra for how fast the crossing chance falls with gap width.

### Step 1: the rule for the electron inside the gap

In quantum mechanics an electron is described by a *wavefunction* ψ(x): a number attached to each position x, whose square |ψ(x)|² gives the chance of finding the electron at x. Let x be the distance measured across the gap, from the tip (x = 0) towards the surface.

The rule that governs ψ is the *Schrödinger equation*. For one direction and a region where the potential energy is a constant U, it reads

$`\displaystyle -\frac{\hbar^2}{2m}\,\frac{d^2\psi}{dx^2} + U\,\psi = E\,\psi`$

where:
- m is the electron's mass, 9.109 × 10⁻³¹ kg,
- ħ ("h-bar") is Planck's constant divided by 2π, 1.055 × 10⁻³⁴ J·s, the constant that sets the size of all quantum effects,
- E is the electron's energy,
- U is the potential energy it would have in the gap,
- d²ψ/dx² is the *curvature* of ψ: how fast its slope changes as you step along x.

This equation is **postulated** (put in by hand, then tested against experiment), not derived from anything deeper.

### Step 2: rearrange

Move terms across:

$`\displaystyle \frac{d^2\psi}{dx^2} = \frac{2m\,(U - E)}{\hbar^2}\,\psi`$

In the gap the electron is short of energy: U − E is positive, and for an electron near the top of the filled levels in the metal it is just the work function, U − E ≈ φ. So the right-hand side is a **positive** number times ψ. Give that number a name:

$`\displaystyle \kappa^2 = \frac{2m\,\varphi}{\hbar^2}, \qquad \kappa = \frac{\sqrt{2m\varphi}}{\hbar}`$

κ ("kappa") is the *decay constant*: it plays the role of the fog's density. The equation is now

$`\displaystyle \frac{d^2\psi}{dx^2} = \kappa^2\,\psi .`$

### Step 3: solve it

Try ψ(x) = A e<sup>−κx</sup>, where A is whatever value ψ has at the tip end of the gap. Take the slope twice:

$`\displaystyle \frac{d\psi}{dx} = -\kappa A e^{-\kappa x}, \qquad \frac{d^2\psi}{dx^2} = \kappa^2 A e^{-\kappa x} = \kappa^2\,\psi. \;\checkmark`$

So this works. (e<sup>+κx</sup> also solves the equation, but it grows across the gap; for a gap of several ångströms it contributes a negligible correction to the crossing chance, and I am dropping it. This is the **assumption** κd ≫ 1, checked below.)

This is the fog: every extra distance Δx multiplies ψ by the same factor e<sup>−κΔx</sup>.

### Step 4: from ψ to current

The chance of finding the electron at the far side of a gap of width d is |ψ(d)|², which is proportional to

$`\displaystyle e^{-2\kappa d}.`$

(The 2 appears because the chance is ψ *squared*.)

The current I is the number of electrons per second that try to cross, times the chance each one makes it. At small bias voltage the number trying does not depend on d, so

$`\displaystyle I \propto e^{-2\kappa d}.`$

### Step 5: move the tip by Δd

Divide the current at gap d by the current at gap d + Δd:

$`\displaystyle \frac{I(d)}{I(d+\Delta d)} = \frac{e^{-2\kappa d}}{e^{-2\kappa (d+\Delta d)}} = e^{2\kappa\,\Delta d}.`$

The starting gap d has cancelled out, exactly like the torch brightness in the fog. The factor per step depends only on κ and the step.

### Step 6: put in numbers

Take φ = 4.5 eV = 4.5 × 1.602 × 10⁻¹⁹ J = 7.21 × 10⁻¹⁹ J.

$`\displaystyle 2m\varphi = 2 \times 9.109\times10^{-31} \times 7.21\times10^{-19} = 1.314\times10^{-48}\ \text{kg·J}`$

$`\displaystyle \sqrt{2m\varphi} = 1.146\times10^{-24}, \qquad \kappa = \frac{1.146\times10^{-24}}{1.055\times10^{-34}} = 1.09\times10^{10}\ \text{m}^{-1} = 1.09\ \text{Å}^{-1}.`$

A handy form of the same result: κ ≈ 0.51 × √(φ in eV), in inverse ångströms.

For Δd = 1 Å:

$`\displaystyle 2\kappa\,\Delta d = 2.17, \qquad e^{2.17} \approx 8.8 .`$

Over the range of work functions for common metals:

| work function φ | κ (per Å) | current factor per Å, e<sup>2κ·1 Å</sup> |
| --- | --- | --- |
| 4.0 eV | 1.02 | ≈ 7.8 |
| 4.5 eV | 1.09 | ≈ 8.8 |
| 5.0 eV | 1.14 | ≈ 9.9 |

That is the "about tenfold". Check of the assumption from Step 3: at a working gap of about 5 Å, κd ≈ 5, and e<sup>−5</sup> is under 1%, so dropping the growing piece was safe.

## What was assumed, and where it breaks

- **Flat energy step (assumed).** The gap was treated as a region of constant height φ. Really the height sags near each metal surface (an electron near a metal is pulled toward it by the charge it induces there) and tilts with the bias voltage. That lowers the effective step, so the *measured* factor per ångström is often somewhat below the table's numbers; experiments commonly report an "apparent barrier height" smaller than the work function.
- **Small bias (assumed).** If the bias voltage is not small compared with φ/e (roughly, not well under a few volts), electrons at higher energies see a lower step and φ in the formula has to be replaced by a smaller average.
- **Only the exponential kept (approximation).** The number of electrons trying to cross, and the exact prefactor in front of the exponential, also depend weakly on d. Next to the exponential that is a small correction.
- **One direction only (simplification).** Electrons also move sideways; the ones heading straight across see the smallest effective step and dominate the current, which is why the one-dimensional calculation lands close.
- **Very close gaps (breaks down).** Below roughly 3 to 4 Å the tip starts to touch the surface electronically: the energy step collapses, atoms can be pulled by the tip, and the current stops rising exponentially and levels off.

That tenfold change per ångström is also why the microscope can see single atoms: if one atom on the tip sits even one ångström closer to the surface than its neighbours, it carries almost all of the current.

</details>

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

The main knob is the **unexplained-term budget**: how many pieces of field
vocabulary may appear without a gloss where they appear. "Write more simply" is a
wish; a term budget is a rule that can be followed and checked.

## When it fires, and when it does not

It fires only on an explicit request ("Feynman style", "picture first", "讲人话")
or an explicit complaint ("too technical", "I didn't follow that", "看不懂").

It does **not** fire because a topic is hard, because an answer came out dense,
or because you said you are new to something. It never offers itself unprompted.
A style skill that decides you look lost is worse than no skill.

## Rules

- Only an explicit request or complaint sets a register.
- A register persists across topics and on short questions until you change it.
  A short factual question still gets a short answer.
- An explicit instruction ("Feynman, but show the algebra") overrides only the
  knob it names, for that answer. Two registers are never averaged.
- A Feynman analogy must be apt (same structure), familiar (needs no gloss of its
  own) and hard to misread; if none fits, it says so rather than forcing one.
- A register never removes content; if the budget would drop a caveat, it spends
  more words instead.
- A complaint gets the same question re-answered one register lighter, not the
  same answer at greater length.
- It never asks about your background and never starts a teaching sequence.
- Switching is one clause of confirmation, no re-explanation.
- Code, logs and error messages are quoted as they are.

## Changelog

### v1.2.0

- Feynman now chooses its analogy by three tests: the same structure as the
  subject, familiar enough to need no gloss, and hard to misread. Each answer
  says what the analogy borrows and rules out the wrong conclusion it most
  invites; if nothing familiar has the structure, it says so and describes the
  behavior directly. Grounded in *The Feynman Lectures on Physics* (Vol. I §4-1,
  Vol. II §12-1 and §12-7, Vol. III §1-1). Prompted by maintainer feedback that
  an analogy which is apt but easy to misread fails the register.
- New evals F1 (analogy quality) and F2 (no forced analogy); new Example 7.
- Added `references/style-feynman.md` and `references/style-griffiths.md`:
  catalogues of how *The Feynman Lectures on Physics*, Vol. III, and Griffiths &
  Schroeter's *Introduction to Quantum Mechanics* (3e) explain, with section
  references, loaded before the first answer in the matching register. The
  explanatory moves are kept; the books' voices are left out, because a register
  is a rule set, not an impersonation. Two rules moved into `SKILL.md` from
  them: Feynman labels each claim as observed, derived, assumed or convention,
  and never invents a mechanism; Griffiths marks definitions, conventions and
  results, and warns once about the standard mistake. New evals S1 and S2.
- README samples re-run on this version, in English and Chinese, so they show the
  new analogy and claim-labelling rules in practice.
- Full eval set run on this version: 15/15 pass (table in
  [PR #7](https://github.com/ljx-chase/pick-your-professor/pull/7)).
- README equations use GitHub's `` $`…`$ `` inline form, and `` $`\displaystyle …`$ ``
  for display equations, after the re-run samples came through with forms GitHub
  does not render inside `<details>`.

### v1.1.0

- Registers are now defined by three knobs: the unexplained-term budget, what
  carries the argument, and whether the steps are visible.
- Feynman carries the argument on a different system the reader already knows;
  Griffiths on a simplified case of the real system. `registers.md` explains how
  to tell them apart.
- Mixed requests ("Feynman, but show the algebra") override one knob for one
  answer. Two registers are never averaged.
- A short factual question gets a short answer in every register.
- New evals: D1 (Feynman and Griffiths stay distinct) and X1 (a mixed request
  overrides one knob).
- README: logo, register figure, and sample answers from test runs.

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
  author       = {Li, Junxiang},
  year         = {2026},
  howpublished = {\url{https://github.com/ljx-chase/pick-your-professor}},
  note         = {GitHub repository}
}
```

## License

MIT License. Copyright (c) 2026 LI Junxiang.
