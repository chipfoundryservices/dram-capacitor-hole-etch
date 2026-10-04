# Chapter 11: Twisting, Tilting & Hole Placement at the Bottom

## Overview

A capacitor hole is printed at the top and must land at the bottom. Lithography places the top within a few nanometres of where the landing pad below expects it. The etch must then carry that position down 1.6 µm without drift. Two kinds of drift occur. **Tilting** is systematic: every hole in a region leans in the same direction, usually outward near the wafer edge. **Twisting** is random: individual holes bend in different directions, by different amounts, and often more as they go deeper. Both move the bottom of the hole away from the centre of its pad. Neither can be seen by the overlay metrology that measures the top.

This chapter explains the causes of twisting and tilting, models how they grow with depth, combines them into the bottom-placement budget of Chapter 1, and describes how they are measured and corrected.

**Learning Objectives:**
- Distinguish twisting (random, hole to hole) from tilting (systematic, regional)
- Explain how asymmetric mask shape, polymer, and charge bend a hole
- Model twist growth with depth and estimate the angle that gives the reference twist
- Compute bottom displacement from tilt at the wafer edge, including the mask contribution
- Build the bottom-placement budget and the not-landed rate from its distribution
- Describe measurement by HV-SEM, cross-section, and X-ray scattering, and correction by edge hardware and lithography

---

## 11.1 Definitions

```
Top position:     centre of the hole at the top of the mold (from litho)
Bottom position:  centre of the hole at the pad
Displacement:     d = bottom − top (a 2-D vector per hole)

Tilting: the mean of d over a region (e.g., a die or a radial band)
         → systematic, correctable in principle
Twisting: the scatter of d about that mean, hole to hole
         → random, not correctable by placement

Reference (3σ, magnitude of one component):
  Tilting after edge compensation:    ≤ 3 nm
  Twisting:                           ≤ 5 nm
```

---

## 11.2 Why Holes Twist

### 11.2.1 The Instability

A straight hole is a balanced structure: the polymer, the charge, and the ion flux are symmetric about its axis. If the hole bends slightly to one side, that symmetry breaks:

1. The wall on the **outside** of the bend faces the incoming ions more directly. It receives more ions, etches faster, and carries less polymer.
2. The wall on the **inside** of the bend is shadowed. It collects more polymer.
3. The charge on the two walls differs, and the resulting lateral field bends incoming ions further toward the outside of the bend.

Each effect pushes the hole further in the direction it is already bending. Twisting is therefore an **instability**: small initial asymmetries grow with depth.

### 11.2.2 Seeds of Asymmetry

```
Seed                                         Typical origin
──────────────────────────────────────────────────────────────────────────────
Non-circular mask hole                       double-SADP parallelogram corners;
                                             EUV stochastic shape
Asymmetric mask facet                        different corner rounding on
                                             different sides
Mask hole already twisted                    ACL open is itself an AR 44 hole
Local polymer clusters                       stochastic deposition at the neck
Asymmetric neighbours                        array-edge holes, missing holes,
                                             CD families differing by side
Wall-charge fluctuations                     discrete charges on a 30 nm wall
```

The honeycomb itself is symmetric. Each hole has six neighbours at 60° intervals, so the charge and polymer environment of an interior hole has no preferred direction. At the array edge this symmetry breaks: the outermost holes have neighbours on one side only. Edge holes twist systematically away from or toward the array, which is why the outermost rows are usually dummies.

### 11.2.3 Onset Depth

Twisting is small in the upper part of the hole. It becomes visible below an aspect ratio of about 25–30, where the ion flux to the bottom is weak, the bottom charge is high, and the wall polymer is thin.

```
Reference onset: A ≈ 28 → h₀ ≈ 800 nm (near the middle support)
```

The middle support helps. A nitride ring etched in a different chemistry partly resets the polymer and charge state and straightens the hole slightly. Many processes see twisting begin just below the middle support.

---

## 11.3 A Model of Twist Growth

### 11.3.1 Constant Random Angle

The simplest model gives each hole a random deviation angle θ_t below the onset depth h₀, constant down to the bottom:

```
x_bottom = θ_t (H − h₀)

Reference: 3σ of x_bottom = 5 nm → σ_x = 1.67 nm
  σ_θ = 1.67 nm / (1600 − 800) nm = 2.1×10⁻³ rad = 0.12°
```

This angle is close to the charging deflection estimated in Chapter 3 (0.13° for a 2 V asymmetry over 200 nm). The model says twisting scales linearly with the depth below onset, so a mold taller by 25% (2.0 µm) with the same onset would give 1.5× the twist.

### 11.3.2 Growing Angle

The instability argument of Section 11.2.1 suggests the angle grows with depth:

```
dθ/dh = θ / L_g      (growth length L_g)
θ(h) = θ₀ exp((h − h₀)/L_g)

x_bottom = ∫ θ(h) dh = θ₀ L_g [exp((H − h₀)/L_g) − 1]

Example: L_g = 400 nm, H − h₀ = 800 nm:
  x_bottom = θ₀ × 400 × (e² − 1) = θ₀ × 400 × 6.39 = 2556 θ₀
  For σ_x = 1.67 nm: σ_θ₀ = 6.5×10⁻⁴ rad = 0.037° at onset,
  growing to 0.28° at the bottom
```

The growth model has two consequences that matter in production. First, twisting rises faster than linearly with mold height, which makes taller molds disproportionately harder (Chapter 14). Second, the distribution of x_bottom is not Gaussian. Holes whose seed asymmetry is unusually large grow exponentially from a larger start, producing a heavy tail of strongly twisted holes. These tail holes, not the Gaussian core, set the not-landed rate.

---

## 11.4 Why Holes Tilt

### 11.4.1 The Edge Sheath

Chapter 8 showed that a mismatch between the ring and wafer surfaces bends the sheath at the edge and tilts the incoming ions. The holes follow the ions.

```
Bottom displacement from a tilt angle α:
  x = H tan α
  α = 0.10°: x = 1600 × 1.75×10⁻³ = 2.8 nm
  α = 0.24°: x = 6.7 nm
```

### 11.4.2 Tilt Inherited from the Mask

The ACL mask open is also a high-aspect-ratio etch with its own edge tilt. A tilted mask hole steers the ions entering the mold, so the mold hole continues in the same direction for a while. The mold etch then adds its own tilt.

```
Tilt at r = 147 mm (illustrative):
  ACL open (AR 44 over 1350 nm):    0.05° outward → mask bottom shifted
                                     1350 × tan(0.05°) = 1.2 nm
  Mold etch, ring at matched height: 0.03° outward → 0.8 nm over 1600 nm
  Combined bottom shift relative to the printed top: ≈ 1.2 + 0.8 ≈ 2.0 nm
```

Both etches must be tuned together. A fab that matches each separately can still see a combined edge tilt outside the budget.

### 11.4.3 Other Sources

- **Chuck and wafer flatness:** a wafer that is not flat on the chuck is tilted relative to the sheath. A local slope of 10 µm over 10 mm is 0.06°.
- **Azimuthal asymmetry:** pumping ports, the wafer-transfer slot, and RF feed asymmetries can tilt holes slightly in one azimuthal direction.
- **Radial ion flux gradients:** in the interior, ions follow the field lines of a flat sheath; tilt is negligible except where the plasma density changes steeply.

---

## 11.5 The Bottom-Placement Budget

### 11.5.1 The Budget

From Chapter 1:

```
Requirement: |Δ| ≤ 9 nm (bottom centre to pad centre, every hole)

Contributors (3σ):
  Hole-to-pad lithographic overlay      3.5 nm
  Pad placement and CD                  3.0 nm
  Twisting                              5.0 nm
  Tilting (after compensation)          3.0 nm
  RSS                                   7.4 nm
```

### 11.5.2 From 3σ to Every Hole

A 3σ RSS of 7.4 nm means σ ≈ 2.5 nm per component. The specification is not 3σ, though: with 1.7×10¹⁰ holes per die, the requirement must hold to roughly 6.5σ for the rate of failures to fall below 1×10⁻¹⁰ per hole.

```
If all contributors were Gaussian:
  σ_total = 7.4 / 3 = 2.47 nm
  9 nm / 2.47 nm = 3.65σ → two-sided tail probability ≈ 2.6×10⁻⁴ per hole
  → far too high if exceeding 9 nm were a hard failure
```

Exceeding 9 nm is not a hard failure, though. The budget closes because:

1. The actual failure criterion is soft: a hole offset by 9 nm has a contact of 16 nm width, and resistance rises gradually beyond that. Hard failure (no contact) needs an offset near 25 nm, about 10σ.
2. Most contributors are bounded, not Gaussian: lithography overlay is corrected per field, and pad placement is set by its own patterning.

```
Hard failure (no contact): |Δ| ≥ 25 nm
  25 / 2.47 = 10.1σ  → Gaussian probability ≈ 10⁻²³ (negligible)
Resistance degraded (overlap < 16 nm, |Δ| > 9 nm): tail ≈ 10⁻⁴
  → these cells have 20–40% higher contact resistance; acceptable within
    the access-path budget if the bottom CD is ≥ 22 nm
```

The heavy tail of twisting (Section 11.3.2) changes this picture. If 1 hole in 10⁸ twists by 25 nm or more, that alone produces 170 unlanded holes per die. Twisting is therefore budgeted on its tail, not on its σ.

---

## 11.6 Measuring Placement

```
Method                        What it sees                           Use
──────────────────────────────────────────────────────────────────────────────────
High-voltage SEM (HV-SEM,     top and bottom of the hole in one     twist and tilt maps,
  10–30 kV primary beam)      image; bottom by backscattered        thousands of holes
                              electrons through the mold            per site
Cross-section (FIB-SEM, TEM)  full profile in one plane             bow, neck, taper;
                                                                     few holes
X-ray scattering (CD-SAXS)    average profile and average tilt      site-mean tilt,
                              over the beam spot                    non-destructive
Post-fill top-down / e-beam   pillar tops vs. pads after TiN fill;  not-landed and
  voltage contrast            open/short contrast                   bridged holes
```

HV-SEM is the main production tool for twisting. Its bottom image is blurred by scattering in the mold, so its placement precision is about 0.5–1 nm per hole, enough to measure a σ of 1.7 nm and to find tail holes in a large sample.

---

## 11.7 Correcting Placement

### 11.7.1 Tilt

```
Edge hardware: ring lift and ring bias (Chapter 8) hold the mold-etch tilt
               near zero.
Lithography:   a measured, stable residual tilt can be pre-compensated by
               shifting the printed hole tops inward at the edge.
  Example: residual outward shift of 2.0 nm at r = 147 mm →
           scanner correction of −2.0 nm (radial) in the edge fields
```

Pre-compensation only works if the tilt is stable over the ring life. Fabs that use it update the correction as the ring ages, through APC.

### 11.7.2 Twisting

Twisting cannot be corrected by placement because it is random. It can only be reduced:

1. **Rounder mask holes**: smoother, more circular ACL openings with no corner facets
2. **Less charging**: bias pulsing, DC superposition, tailored waveforms (Chapter 6)
3. **More symmetric polymer**: lower Π in the lower oxide, wall passivation that resists asymmetric etching
4. **A stiffer hole**: a narrower ion angular distribution makes grazing reflections less sensitive to the wall shape
5. **Supports as straighteners**: a middle support placed near the onset depth

```
Illustrative twist reductions (3σ, from 5.0 nm):
  Bias pulsing in the last 60 s of ME2:        −1.0 nm
  DC superposition −900 V:                     −1.0 nm
  Rounder mask (SADP corner rounding step):    −0.8 nm
  Tailored waveform in ME2:                    −0.8 nm
```

---

## Summary and Key Takeaways

1. **Tilting is systematic; twisting is random.** Tilting follows the edge sheath and the mask open. Twisting is an instability seeded by small asymmetries.

2. **Twisting begins near A ≈ 28.** In the reference hole that is near the middle support, 800 nm down.

3. **A random angle of 0.12° gives the reference twist.** It is comparable to the deflection from a 2 V wall-charge asymmetry.

4. **Growth makes the tail heavy.** An exponentially growing angle produces rare, strongly twisted holes that set the not-landed rate.

5. **The placement budget closes only with bounded contributors and a soft failure criterion.** Twisting must be budgeted on its tail.

6. **Tilt can be compensated; twist can only be reduced.** Edge hardware and lithography pre-compensation handle tilt. Pulsing, DC superposition, rounder masks, and tailored waveforms reduce twist.

---

## Study Questions

1. With the constant-angle model and σ_θ = 0.12°, what is the 3σ twist for a 2.0 µm mold with the onset at 900 nm?

2. With the growth model, L_g = 400 nm, and the same σ_θ₀, compute the 3σ twist for H − h₀ = 1000 nm. Compare with the constant-angle result of Question 1.

3. The ACL open has an edge tilt of 0.08° and the mold etch 0.05°, both outward. Compute the combined bottom shift at the edge and the scanner correction needed.

4. If 1 hole in 10⁹ twists by more than 25 nm, how many unlanded holes are expected on a 16 Gb die? Is this within the 1×10⁻⁸ not-open allocation?

5. An HV-SEM measures 2000 holes per site with a placement precision of 0.8 nm (1σ). What is the measured σ of the twist if the true σ is 1.67 nm? How many holes must be sampled to find a 1-in-10⁶ tail hole with 90% probability?

---

**Next Chapter:** [Chapter 12: Not-Open Holes, the Bottom Etch Stop & Landing-Pad Interface](./12-not-open-landing-pad.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
