<div align="center">

<img src="docs/logo.png" alt="Pick Your Professor: set how densely it explains. It holds for the whole session." width="720"/>

<p>
<a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License"/></a>
<img src="https://img.shields.io/badge/version-v1.1.0-blue?style=flat-square" alt="Version"/>
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

The replies below come from test runs of this version: a fresh session with the
skill installed, one run each. The wording is unedited; only the equation markup
was adapted so that GitHub renders it.

> *Why does the current in a scanning tunneling microscope change about tenfold
> when the tip moves just one ångström?*

| | What carries the argument | Length |
|---|---|---|
| **Feynman** | A stack of tinted glass: each sheet cuts the light by the same factor | ~860 words |
| **Griffiths** | Two flat metal slabs with a rectangular barrier between them | ~900 words |
| **Landau** | I ∝ V e<sup>−2κd</sup>, Tersoff–Hamann, WKB | ~290 words |
| **Feynman + algebra** | The same glass, then the Schrödinger equation with every symbol named | ~1,340 words |

All four land on about 8–10× per ångström for a 4–5 eV work function. All four
keep the same caveats: a small bias, a gap of several ångströms (the current
levels off near contact), and a measured factor often below 10 on real, less
clean surfaces.

<details>
<summary><b>Feynman</b></summary>

This is a rule about multiplying. Each extra ångström of gap cuts the current by the same *factor*, not by the same *amount*. Two things set the size of that factor: the electron's mass, and how much energy the electron is missing. The numbers below come from a simplified model that gets the size of the effect right.

**A stack of tinted glass.** Hold one sheet of dark glass up to a lamp, and say it lets through a third of the light. Put a second sheet behind it. That sheet passes a third of what reaches it, so a ninth gets out. A third sheet leaves a twenty-seventh. Each sheet you add cuts the light by the same factor of 3, however many are already there. So a little extra glass makes a large difference. Now slice the glass thinner. A half-thickness sheet cuts the light by about 1.7, the square root of 3, because two halves have to make one whole. So the real rule is that every millimetre of glass multiplies the light by the same fraction. Last, change the dye: darker glass gives a bigger factor per millimetre.

**Back to the microscope.** The empty gap between the tip and the surface plays the part of the glass. An electron inside the metal doesn't have enough energy to be out in the gap at all. Pulling even the most energetic electron out of a typical metal costs about 4 to 5 electron-volts (an electron-volt is the energy one electron gains by moving through one volt). By everyday rules, no electron would ever cross.

Quantum mechanics is the set of rules for things as small as electrons. It describes an electron as a wave. When a wave meets a region it doesn't have the energy to enter, it doesn't stop dead at the edge. It fades inside, dropping by the same factor for each ångström, just like the light in the glass. If the gap is thin enough that the wave hasn't faded to nothing, part of it reaches the tip, and the electron has a small chance of turning up there. That crossing is the "tunneling" in the microscope's name.

**The numbers.** For an electron missing about 4.5 electron-volts, the wave's height drops by about a factor of 3 per ångström. The chance of finding the electron at a spot goes as the square of the wave's height there. That is a basic rule of quantum mechanics, and we won't prove it here. So the chance of crossing, and with it the current, drops by about 3 × 3 ≈ 9 to 10 per ångström. That is the tenfold.

The "darker dye" stands for a bigger energy shortfall, which makes the wave fade faster:
- a metal that needs 4 electron-volts gives about 8× per ångström;
- one that needs 5 gives about 10×.

**Why an ångström.** Three things fix the distance over which the wave fades: the electron's mass, the energy shortfall, and Planck's constant (the number that sets how large quantum effects are). The same three things set the size of atoms. So the fading distance comes out atom-sized, around an ångström.

**Where the glass stops working.** Tinted glass soaks up the light it blocks and turns it into heat. The gap soaks up nothing. Electrons that fail to cross just bounce back into the metal, and the ones that do cross arrive with all their energy. The fading measures how likely a crossing is, not energy lost on the way.

**What this assumes, and where it fails.**
- **Flat wall.** It treats the gap as a flat wall exactly as high as the energy needed to pull an electron out. Near a metal the real wall is lower and rounded. That's because an electron close to a metal shifts the metal's own charges around, and those shifted charges pull it back. So measured factors are often below 10, anywhere from about 3 to 10 per ångström, depending on the tip, the surface and how clean they are.
- **Small voltage.** It assumes the voltage between tip and surface, usually a few thousandths of a volt up to a volt or two, is small next to the 4 to 5 electron-volt shortfall. At several volts the wall gets tilted and thinned, and the current follows a different rule.
- **Normal working gap.** It holds at gaps of roughly 4 to 10 ångströms. If the tip is pushed so close that its end atom almost touches the surface atoms, the atoms start pulling on each other and the wall collapses. Then the current stops rising tenfold per ångström and levels off.

**In symbols, if you want them:** current ∝ e<sup>−2κd</sup>.
- "∝" means "goes in proportion to."
- e ≈ 2.718, and e raised to a power that grows with d is the formula way of saying "multiply by the same fraction for every bit of d."
- d is the width of the gap.
- The 2 is the squaring.
- κ = √(2mφ)/ħ, where m is the electron's mass, φ is the energy shortfall, and ħ is Planck's constant divided by 2π.

With φ = 4.5 electron-volts, κ ≈ 1.1 per ångström, and e<sup>2 × 1.1</sup> ≈ 9.

</details>

<details>
<summary><b>Griffiths</b></summary>

Griffiths it is.

**The simplified system.** Treat the tip and the sample as two flat slabs of the same metal facing each other across a vacuum gap of width d. Inside each metal, electrons fill the available energy levels up to a top filled level, the *Fermi level*. An electron at the Fermi level needs extra energy φ to get out into the vacuum. That energy is the *work function*, about 4–5 electron-volts (eV) for common metals. From that electron's point of view, the gap is a wall: a region d wide where its potential energy would be φ above its total energy. Classically it bounces off every time and the current is zero. Getting through anyway is *tunneling*.

**Step 1: the electron inside the wall.** Describe the electron by its *wavefunction* ψ(x). The squared magnitude |ψ|² is the probability of finding it at position x. Inside the gap, the Schrödinger equation (the equation that fixes ψ for a given energy) reads

  −(ħ²/2m) ψ″ + U ψ = E ψ,  with U − E = φ,

where m is the electron mass, ħ is Planck's constant divided by 2π, U is the potential energy in the gap and E is the electron's energy. Rearranged, this is ψ″ = κ²ψ, with

  κ = √(2mφ) / ħ.

The solutions are e<sup>−κx</sup> and e<sup>+κx</sup>. Neither oscillates; one decays and one grows. κ is the *decay constant*: every distance 1/κ, ψ shrinks by a factor of e.

**Step 2: drop the growing piece.** *Assumption: the barrier is thick, κd ≫ 1.* Matching ψ at the far wall then makes the coefficient of e<sup>+κx</sup> negligible, so across the gap ψ(x) ≈ ψ(0) e<sup>−κx</sup>.

**Step 3: square it.** The chance that an electron hitting the wall comes out the other side is the *transmission probability* T. It goes as |ψ(d)|² / |ψ(0)|²:

  T ≈ (prefactor) × e<sup>−2κd</sup>.

For a rectangular barrier the prefactor is at most 4. It depends on the electron's energies but, in the thick limit, not on d. The factor 2 in the exponent appears because probability is the *square* of ψ.

**Step 4: from T to current.** *Assumption: the bias V, the voltage applied between tip and sample, is small, so eV ≪ φ (e is the electron charge).* Only electrons within eV of the Fermi level have empty levels on the other side to move into. All of them see essentially the same wall. How many arrive per second is set by V and the metals, not by d. So

  I ∝ V e<sup>−2κd</sup>,  which gives  I(d) / I(d + 1 Å) = e<sup>2κ · 1 Å</sup>.

Nothing else in I depends on d, so the whole distance sensitivity sits in that exponent.

**Objection, parked.** You might object that a real tip is a rounded point ending in a few atoms, and that tip and sample are usually different metals. The shape changes the prefactor, and for a sharp tip it leaves the exponent close to 2κd. Different metals make the wall slightly sloped; to this accuracy, use the average of the two work functions for φ. Neither changes the answer to your question.

**Which situations give which behavior.**
- **Thick barrier, small bias** (κd ≫ 1, eV ≪ φ): the current changes by e<sup>2κ</sup> per ångström. This is normal STM operation, with gaps of roughly 5–10 Å.
- **Bias comparable to φ/e (several volts):** the voltage tilts the top of the wall. Electrons near the top of the energy window meet a lower, thinner wall, so κ is no longer one number and the factor per ångström shrinks. Once eV > φ, the wall becomes a triangle and electrons leave by *field emission* (tunneling through a wall whose thickness is set by the electric field rather than directly by d). The distance dependence is then different and weaker.
- **Gap within a few ångströms of contact:** the exponential picture breaks down (next section).

**Where the picture gives the wrong answer.** The simple model predicts the current keeps growing tenfold per ångström all the way in. It does not, because of the *image potential*: an electron in the gap is attracted by the opposite charge it induces in the nearby metal surface. This rounds the corners of the wall and lowers it. Near contact, the lowering from both surfaces overlaps until the wall collapses and κd is no longer large. The current then levels off near the *conductance quantum*, G₀ = 2e²/h ≈ 77 µS (about 12.9 kΩ, where h is Planck's constant), which is roughly the conductance of a single-atom contact.

Even at normal gaps, the barrier height fitted from measured I(d) curves, the *apparent barrier height*, often comes out below the textbook work function. On clean surfaces in vacuum it is usually within a couple of eV of φ. In air or on contaminated surfaces it can drop below 1 eV. So the measured factor per ångström ranges from about 10 down to about 3 or less.

**Worked case.** Take φ = 4.5 eV, typical of a tungsten tip. For an electron, ħ²/2m = 3.81 eV·Å², so

  κ = √(φ / (ħ²/2m)) = √(4.5 / 3.81) Å⁻¹ = √1.18 Å⁻¹ ≈ 1.09 Å⁻¹.

Over 1 Å, ψ falls by e<sup>1.09</sup> ≈ 3.0 and the current falls by e<sup>2.17</sup> ≈ 8.8. With φ = 5 eV, κ ≈ 1.15 Å⁻¹ and the factor is e<sup>2.29</sup> ≈ 9.9.

Checking Step 2's assumption: at a 6 Å gap, κd ≈ 6.5, which is well above 1.

So the tenfold figure is the square of a roughly threefold drop in ψ per ångström, and that drop is set by a 4–5 eV work function.

</details>

<details>
<summary><b>Landau</b></summary>

The tunnelling current falls off exponentially with the gap:

```math
I \propto V\,e^{-2\kappa d},\qquad \kappa=\frac{\sqrt{2m\phi}}{\hbar}\;\Rightarrow\; -\frac{d\ln I}{dd}=2\kappa\approx 1.025\sqrt{\phi\,[\mathrm{eV}]}\ \text{Å}^{-1}.
```

Here φ is the effective barrier, roughly (φ<sub>tip</sub> + φ<sub>sample</sub>)/2. For metals, φ ≈ 4–5 eV, so 2κ ≈ 2.0–2.3 Å⁻¹. That gives a factor of e<sup>2κ·1 Å</sup> ≈ 8–10 per ångström. An exact factor of 10 corresponds to φ ≈ 5 eV.

**Sketch.** Use Bardeen's transfer Hamiltonian with an s-wave tip (Tersoff–Hamann), at low bias: I ∝ V ρ<sub>t</sub>(E<sub>F</sub>) ρ<sub>s</sub>(r₀, E<sub>F</sub>). The sample states at E<sub>F</sub> decay into vacuum as ψ ∝ e<sup>−κz</sup>, so ρ<sub>s</sub>(r₀) ∝ e<sup>−2κ(d+R)</sup>. A 1D WKB treatment of a rectangular barrier gives the same exponent. Any d-dependence in the prefactor is algebraic and negligible next to the exponential. Components with k<sub>∥</sub> ≠ 0 decay with √(κ² + k<sub>∥</sub>²), so the current comes mainly from k<sub>∥</sub> ≈ 0, and κ is the smallest decay constant available.

**Validity.**
- **Low bias, eV ≪ φ.** At finite bias the barrier is trapezoidal and φ → φ − eV/2. For eV > φ you are in the Fowler–Nordheim regime, where the dependence on d is weaker.
- **Opaque barrier, κd ≫ 1, with d ≳ 4–5 Å.** The image potential rounds the barrier and lowers it, but d ln I/dd stays close to its work-function value down to a few Å. At smaller gaps the barrier collapses, the apparent barrier height drops, and the conductance saturates near G₀ = 2e²/h at contact.
- **Clean surfaces.** Measured apparent barrier heights are often only 1–4 eV, which means about 3–8× per Å instead of 10×. Causes include:
  - adsorbates or contamination, especially in air or liquid;
  - tip–sample forces, which make the real change in d smaller than the piezo's Δz;
  - tip states that are not s-like.

  The factor of 10 is the value for clean metal-on-metal surfaces in ultra-high vacuum.

</details>

<details>
<summary><b>Feynman, but show the algebra</b></summary>

This is an approximate scaling law, and it has two parts. The first is a counting rule about losing the same fraction at every step. The second is a short calculation that tells you how big that fraction is.

**The picture: light through tinted glass**

Take a sheet of tinted glass that lets through a third of the light that hits it. With two sheets in a row, a third of a third gets through, which is 1/9. With three sheets it is 1/27. Call the brightness going in B₀, the fraction one sheet lets through f, and the number of sheets N. The brightness coming out is

  B = B₀ · f<sup>N</sup>

Adding one more sheet always multiplies the output by f, whether you already had 2 sheets or 200. The ratio from one step to the next doesn't depend on where you are.

*First complication: the stack becomes one solid block.* Think of the block as many thin slices of thickness s, each letting through the fraction f. A block of thickness x holds x/s slices, so

  B(x) = B₀ · f<sup>x/s</sup>

Make the block thicker by an amount Δ and the output drops by the factor f<sup>Δ/s</sup>. Again, that factor is the same however thick the block already was. A quantity that falls by the same factor for every equal step is said to fall *exponentially*. It is usually written with the number e ≈ 2.718, as B(x) = B₀ · e<sup>−x/L</sup>. Here L is the extra thickness that cuts the brightness by a factor of 2.718.

*Second complication: a square.* What the glass shrinks is the height of the light wave, meaning how strongly it swings. What a light meter reads, the brightness, is that height squared. Suppose the height falls as e<sup>−κx</sup>, where κ (Greek "kappa") is the fade rate of the height per unit thickness. Then the brightness falls as (e<sup>−κx</sup>)² = e<sup>−2κx</sup>, so it falls twice as steeply.

*Third complication: darkness.* Darker glass has a bigger κ, so the same extra thickness costs a bigger factor. How dark the glass is sets the size of the whole effect.

*Where the glass picture stops working.* Glass absorbs: the missing light becomes heat. The gap in the microscope is empty, absorbs nothing, and the electrons that fail to cross just bounce back. The fading also has a different cause. Nothing in the gap blocks the electron; the electron doesn't have enough energy to be there. So take only the *shape* of the answer from the glass: a fixed factor per ångström, and a square. The *size* of the factor comes from the calculation below.

**The real thing, with the algebra**

The tip and the surface are two pieces of metal with a gap of empty space between them, of width d, usually several ångströms. A metal holds on to its electrons. Pulling one out into empty space costs a definite energy φ (Greek "phi"), called the *work function*. For common tip and sample metals φ is about 4 to 5.5 eV. One eV (electron-volt) is the energy an electron gains falling through one volt, 1.6×10⁻¹⁹ joule.

The electrons that cross are the most energetic ones in the metal, and even they are short of that energy by about φ. In pre-quantum physics none of them could enter the gap, and the current would be exactly zero. In quantum mechanics, the physics of very small things, an electron is also a wave spread through space. At the gap its wave fades instead of stopping dead. That leak through a region the electron doesn't have the energy to be in is what "tunneling" means. Here is how fast the wave fades.

1. Let ψ(x) (Greek "psi") be the height of the electron's wave at position x. The rule every electron wave obeys (the Schrödinger equation) reads, for a problem along one direction:

   d²ψ/dx² = (2m/ħ²) · (U − E) · ψ

   The symbols:
   - d²ψ/dx² is how sharply the graph of ψ bends at x.
   - m = 9.11×10⁻³¹ kg is the electron's mass.
   - ħ ("h-bar") = 1.055×10⁻³⁴ joule-seconds is Planck's constant divided by 2π. It is the constant that sets how wave-like matter is.
   - E is the electron's energy.
   - U is the energy it would need to be at x.

2. Inside the metal, E is bigger than U, so the right side has the opposite sign to ψ. Wherever the wave is above zero it bends back down, and wherever it is below zero it bends back up. The result is a wiggle, which is an ordinary moving electron.

3. In the gap, U − E = φ, which is positive. Now the wave bends *away* from zero wherever it is, so it grows or shrinks without wiggling. The shrinking piece is ψ(x) = ψ(0) · e<sup>−κx</sup>. Its bending is κ² · e<sup>−κx</sup>. Substituting into the rule gives

   κ² = 2mφ/ħ²  →  κ = √(2mφ) / ħ

   (A gap of finite width also allows a growing piece. When κd is well above 1, as it is here at about 5 to 10, including it changes only the constant in front and not the fade. I'm skipping that bookkeeping.)

4. Quantum mechanics has a rule that the chance of finding the electron at a spot is the square of the wave's height there. At the far side of the gap the height is down by e<sup>−κd</sup>, so the chance of arriving is down by e<sup>−2κd</sup>. This is the square from the glass. The current follows it:

   I ≈ C · V · e<sup>−2κd</sup>

   Here I is the current and V is the small voltage between tip and sample that makes electrons flow one way. C lumps together how many electrons are ready on one side and how many empty places are waiting on the other.

5. Pull the tip back by 1 Å:

   I(d) / I(d + 1 Å) = e<sup>2κ · 1 Å</sup>

   d has cancelled, so the factor is the same at every gap width. This is the extra-sheet rule.

6. Now the numbers, taking φ = 5 eV = 8.0×10⁻¹⁹ J:
   - 2mφ = 2 × (9.11×10⁻³¹ kg) × (8.0×10⁻¹⁹ J) = 1.46×10⁻⁴⁸ kg·J
   - √(2mφ) = 1.21×10⁻²⁴ kg·m/s
   - κ = 1.21×10⁻²⁴ / 1.055×10⁻³⁴ = 1.15×10¹⁰ per metre = 1.15 per ångström
   - 2κ × 1 Å = 2.29, and e<sup>2.29</sup> ≈ 9.9

   That is the tenfold. A handy form is κ ≈ 0.51 × √(φ in eV) per ångström, which gives:

   | Wall height φ | Current change per Å |
   |---|---|
   | 4 eV | ×7.8 |
   | 4.5 eV | ×8.8 |
   | 5 eV | ×9.9 |
   | 5.5 eV | ×11 |

   "Tenfold" is the round number for a wall about 5 eV tall. Because φ sits under a square root, the answer barely changes from one metal to another.

**What this rests on, and where it fails**

- **Flat wall.** The wall is treated as flat on top, with height φ. For two different metals, use roughly the average of their two work functions. This holds while the voltage V is small compared with the few volts that φ corresponds to; normal operation is about 0.01 to 1 V. At several volts the top of the wall tilts into a ramp, electrons cross a thinner slice of it, and a different law takes over.
- **A clean fade.** This needs κd well above 1, meaning gaps of several ångströms. Below about 3 Å, the pull each electron feels toward the nearby metal surfaces drags the top of the wall down until it stops being a wall. The tip and surface atoms start to touch, and the current stops growing tenfold per ångström and levels off.
- **Clean conditions.** The factor of about 10 is for clean metals in vacuum. In air, or with stray molecules stuck to the tip, the wall is effectively lower. The measured factor per ångström is then often noticeably smaller than 10.
- **C varies across the surface.** Different atoms have different numbers of electrons at the right energy. C changes slowly with d compared with the exponential, so it doesn't spoil the tenfold-per-ångström rule. It does mean a change in current is not purely a change in height.

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

### Unreleased

- Feynman now chooses its analogy by three tests: the same structure as the
  subject, familiar enough to need no gloss, and hard to misread. Each answer
  says what the analogy borrows and rules out the wrong conclusion it most
  invites; if nothing familiar has the structure, it says so and describes the
  behavior directly. Grounded in *The Feynman Lectures on Physics* (Vol. I §4-1,
  Vol. II §12-1 and §12-7, Vol. III §1-1). Prompted by maintainer feedback that
  an analogy which is apt but easy to misread fails the register.
- New evals F1 (analogy quality) and F2 (no forced analogy); new Example 7.

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
