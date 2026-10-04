# Chapter 10: Bowing, Necking & Hole Profile Control

## Overview

An ideal capacitor hole would be a cylinder with a slight, uniform taper. A real hole has a shape. Near the top it narrows into a **neck**, where polymer from the sticky fragments builds up. A few hundred nanometres below, it widens into a **bow**, where ions reflected from the neck and the mask, and ions bent by charge, strike the wall. Below the bow it tapers toward the bottom. The bow is the most dangerous part of this shape. It is where the oxide wall between two holes is thinnest, and where two holes that bow toward each other merge.

This chapter explains how the neck and bow form, builds a simple geometric model of the bow depth, sets the bow budget against the hole-to-hole wall, and lays out the knobs that control the profile and their costs.

**Learning Objectives:**
- Describe the reference hole profile: top, neck, bow, taper, and bottom
- Explain the three sources of ions that strike the sidewall below the neck
- Estimate the depth of the bow from the neck taper and the hole width
- Compute the wall between neighbours at the bow and the bridging probability
- Choose bow-control knobs and predict their effect on the neck, the bottom, and the mask

---

## 10.1 The Reference Profile

```
Reference hole profile (illustrative, CD in nm, depth from the top of the
mold):

  Depth (nm)     Feature                   CD
  ─────────────────────────────────────────────────
     0           top (top-support top)     32.0
    80           neck (in top SiN)         30.0
   350           bow maximum               33.5
   770           upper oxide / middle SiN  30.5
   820           below middle support      30.0
  1200           lower oxide               27.0
  1580           above bottom stop         24.5
  1600           bottom (on the pad)       24.0

Schematic:
        │← 32 →│
         \    /      neck 30
         /    \
        /      \     bow 33.5 at 350 nm
        \      /
         |    |      30 at the middle support
         |    |
          \  /       taper to 24 at the bottom
           ||
```

The average CD over the depth is about 28 nm, which is the value used for capacitance and ARDE in Chapters 1 and 3. The bow is 1.5 nm wider than the top, or 0.75 nm per side, and 3.5 nm wider than the neck.

---

## 10.2 How the Neck Forms

The neck forms where the sticky fluorocarbon fragments (CF, C₂, C₃F₃ from C₄F₆) land most. Chapter 3 showed that a radical with a high sticking coefficient deposits within a few hole diameters of the entrance. Ions at the top of the hole are mostly vertical and do not strike the wall, so the deposit is not cleared. The film grows until the hole narrows enough that ions begin to graze it.

```
Neck growth (illustrative):
  Sidewall film near the top: ≈ 2–3 nm per side at steady state
  The top-support SiN etches in a leaner step (SN1) and starts the neck;
  ME1 (C₄F₆-rich) builds it
```

The neck is useful. It shadows the wall below from ions arriving at the widest angles, and it narrows the top of the effective hole, which reduces the bow. But a neck that is too narrow cuts the ion and neutral flux into the hole, raises ARDE, shrinks the bottom, and leaves a re-entrant profile that the electrode deposition cannot fill without a void. And the neck is removed in the strip and clean, so the top CD of the finished capacitor is wider than the neck seen during the etch.

---

## 10.3 How the Bow Forms

Three populations of ions strike the sidewall below the neck:

1. **Ions reflected from the neck and the mask facet.** Ions that strike the tapered neck sidewall or the faceted mask corner at grazing angles reflect specularly, with their angle to the vertical increased by twice the local wall tilt. They cross the hole and hit the opposite wall a few hundred nanometres down.

2. **Ions arriving at wide angles.** The low-energy, wide-angle tail of the IED (Chapter 3) passes the neck and lands on the upper walls.

3. **Ions deflected by wall charge.** Low-energy ions are bent sideways by the negatively charged upper walls (electron shading, Chapter 3) and strike the wall where the charge is greatest.

### 10.3.1 A Geometric Model of the Bow Depth

```
Ion reflected specularly from a wall tilted by φ from vertical:
  outgoing angle to the vertical ≈ 2φ (for a vertical incoming ion)

The reflected ion crosses the hole width w and strikes the far wall at a
depth below the reflection point of:
  Δz ≈ w / tan(2φ)

Reference neck: taper φ ≈ 2.5° in the lower part of the neck, w ≈ 30 nm
  Δz ≈ 30 / tan(5°) = 30 / 0.0875 = 343 nm
Reflection point ≈ 40 nm below the top (in the neck) → strike at
  ≈ 380 nm

Mask facet: φ ≈ 10–20° at the faceted corner → 2φ = 20–40°
  Δz ≈ 30 / tan(20°) = 82 nm to 30 / tan(40°) = 36 nm below the mask
  bottom → strikes the very top of the hole (widens the top)
```

The model puts the bow maximum a few hundred nanometres below the neck, consistent with the reference profile at 350 nm. It also predicts two trends that are seen in practice:

- A **steeper neck** (smaller φ) sends reflected ions deeper and spreads them over a longer wall, so the bow moves down and becomes shallower but longer.
- A **faceted mask** (large φ) sends ions into the top of the hole, widening the top CD rather than the bow. As the mask thins late in the etch and its facet grows, the top CD grows.

### 10.3.2 Lateral Etch Rate at the Bow

```
Lateral etch at the bow (reference): from neck 30.0 to bow 33.5 nm
  → 1.75 nm per side
Hole reaches 350 nm depth at t ≈ 0.6 min into the oxide; ME1 + ME2 run
  ≈ 4 min after that
  → average lateral rate ≈ 0.45 nm/min per side, ≈ 0.08% of the vertical
     open-area rate
```

A lateral rate of less than a tenth of a percent of the vertical rate is enough to make the bow. Bow control is the art of suppressing a very small rate on a very long time scale.

---

## 10.4 The Bow Budget

### 10.4.1 Wall at the Bow

```
Wall between neighbouring holes at the bow depth:
  t_wall = p − (b₁ + b₂)/2 − |Δ|
  p = 45 nm, b = bow CD of each hole, Δ = relative displacement of the two
  hole axes at that depth (from top placement + twisting so far)

Reference mean: t_wall = 45 − 33.5 = 11.5 nm
```

### 10.4.2 Variation

```
Hole-to-hole σ of bow CD: σ_b ≈ 0.6 nm
Relative displacement at 350 nm depth: σ_Δ ≈ 0.5 nm (litho + early twist)
σ_t = √(σ_b²/2 + σ_Δ²) = √(0.18 + 0.25) = 0.66 nm

Merge threshold: walls below ≈ 3 nm are broken by the strip, clean,
or electrode deposition (illustrative)

Margin: (11.5 − 3) / 0.66 = 12.9 σ
```

On Gaussian statistics alone, bridging would never happen. In practice it does, at rates of 10⁻⁹ to 10⁻⁷ per pair, because the tails are not Gaussian. Bridges come from local causes: a mask hole that was printed large, a mask edge with a defect that facets early, a particle or residue that changes the polymer locally, or a twisted hole that leans into its neighbour. The bow budget therefore holds a large Gaussian margin to leave room for these.

How should the 34 nm bow specification of Chapter 1 be read? If it applied to every hole (mean + 3σ), the mean would have to stay below 34 − 3 × 0.6 = 32.2 nm. The reference mean of 33.5 nm plus 3σ (1.8 nm) gives 35.3 nm, above the 34 nm specification. The specification is written on the **wafer-level mean bow CD by site**, measured by OCD or cross-section, not on every hole. A hole-level requirement is expressed separately as the bridging rate. The book uses this convention: bow CD ≤ 34 nm is a site-mean limit, and bridging ≤ 10⁻⁹ per pair is the hole-level limit.

### 10.4.3 The Bow–Capacitance Trade

A larger bow raises the average CD and the capacitance (0.32 fF per nm of average CD). It is tempting to accept more bow for capacitance. The budget does not allow it: a wider bow uses the margin set aside for the non-Gaussian bridging tail, and bow mainly widens the upper third of the hole, which also hosts the top support where the pillars are held.

---

## 10.5 Controlling the Bow

### 10.5.1 Knobs and Their Costs

```
Bow-control knobs (illustrative sensitivities in ME1):

  Knob                           Δ bow CD     Δ neck CD   Δ bottom CD   Δ ACL loss
  ───────────────────────────────────────────────────────────────────────────────
  C₄F₆ +5 sccm                   −0.5 nm      −0.4 nm     −0.4 nm       −20 nm
  O₂ −5 sccm                     −0.5 nm      −0.3 nm     −0.8 nm       −40 nm
  Wafer T −5 °C                  −0.65 nm     −0.25 nm    −0.35 nm      −15 nm
  Tailored bias (vs. sine)       −1.2 nm      ≈ 0         +0.3 nm       +10 nm
  Pressure −5 mTorr              −0.4 nm      +0.2 nm     +0.4 nm       +20 nm
  Thicker / harder mask          −0.3 nm      ≈ 0         ≈ 0           (more
                                                                         budget)
```

Most chemistry knobs that shrink the bow also shrink the bottom. That is the **bow–bottom trade**: polymer that protects the upper wall also accumulates at the neck and the bottom. The knobs that break the trade change the ion population rather than the polymer: tailored waveforms and lower pressure reduce the wide-angle and low-energy ions that make the bow, without adding polymer.

### 10.5.2 Sidewall Passivation Additives

Adding a small flow of a silicon- or sulfur-containing gas, such as SiCl₄ or COS, forms a thin, robust passivation layer (SiOₓ-like or sulfur-containing) on the sidewall. It is harder for grazing ions to remove than fluorocarbon polymer, and it reduces the bow without closing the bottom as much as extra C₄F₆ would.

```
Illustrative: COS 5 sccm in ME1
  bow CD −0.8 nm; bottom CD −0.2 nm; residue on the mask top removed in the
  ash
```

### 10.5.3 Cyclic Deposition and Etch

The upper oxide step can be split into cycles: a short deposition segment with no or low bias, which coats the sidewall, followed by an etch segment at full bias. The deposition is conformal near the top and thin at the bottom, so it protects the bow region preferentially. The cost is time: each cycle adds a few seconds.

### 10.5.4 Bow Below the Middle Support

A second, weaker bow often appears just below the middle support, where the chemistry changes from SN2 back to oxide (Chapter 7, Section 7.4.2). It is controlled by the transition rather than by the main chemistry: a short, polymer-rich start to ME2.

---

## Summary and Key Takeaways

1. **The hole has a shape.** Neck 30 nm at 80 nm depth, bow 33.5 nm at 350 nm, taper to 24 nm at the bottom; average about 28 nm.

2. **The neck makes the bow.** Ions reflected from a neck tapered by 2.5° land about 340 nm lower. Faceted mask corners widen the top instead.

3. **The bow is a tiny lateral rate over a long time.** About 0.45 nm/min per side, less than a tenth of a percent of the vertical rate.

4. **The wall at the bow is about 11.5 nm.** Gaussian variation leaves a large margin; bridges come from non-Gaussian local defects.

5. **Most bow knobs cost bottom CD.** Tailored bias, lower pressure, and passivating additives break the bow–bottom trade.

---

## Study Questions

1. If the neck taper is reduced from 2.5° to 1.5°, where does the geometric model place the bow maximum? What happens to its magnitude?

2. A mask facet at 15° reflects ions into the hole. At what depth below the mask bottom do they strike the far wall, for w = 31 nm?

3. The bow mean rises to 34.5 nm after a chamber change. Recompute the wall at the bow and the Gaussian margin to 3 nm. Would you expect the bridging rate to change measurably? Why or why not?

4. Using the knob table, find a combination of C₄F₆ and wafer temperature that reduces the bow by 1.0 nm while costing no more than 0.5 nm of bottom CD.

5. Estimate the additional etch time from splitting ME1 into eight dep–etch cycles with 2 s of deposition each. How much additional mask does this consume if the mask erodes only during the etch segments?

---

**Next Chapter:** [Chapter 11: Twisting, Tilting & Hole Placement at the Bottom](./11-twisting-tilting-placement.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
