# Chapter 14: Advanced Schemes — Cryogenic Etch, Taller Molds, Multi-Tier Holes, 4F² & 3D DRAM

## Overview

The reference process of this book etches a 1.6 µm hole at about 57:1 with fluorocarbon chemistry at room temperature. Each new DRAM generation asks for the same capacitance from a smaller cell, which means a taller or wider hole, a thinner dielectric, or a different cell. Wider holes are limited by the wall. Thinner dielectrics are limited by leakage. So the hole grows taller, and the etch runs into the limits of its own physics: ARDE that grows with the square of depth, a mask that erodes at constant rate, twisting that grows faster than linearly, and a bias voltage that cannot rise much further.

This chapter surveys how the industry is moving past those limits: cryogenic and HF-based etch, taller molds with harder masks, two-tier holes, the shift from cylinder to pillar and beyond, the denser capacitor arrays of 4F² vertical-channel DRAM, and the very different capacitor of 3D DRAM.

**Learning Objectives:**
- Compute etch time, bottom rate, and CD sensitivity for cryogenic HF-based chemistry
- Quantify the cost of a taller mold in time, mask, twist, and depth sensitivity
- Describe two-tier hole integration and its alignment budget
- Compare cylinder and pillar capacitors and explain the pillar's dominance at small CD
- Estimate the capacitor hole geometry for a 4F² cell
- Describe how the capacitor etch changes in 3D DRAM

---

## 14.1 Cryogenic and HF-Based Etch

### 14.1.1 The Chemistry

Chapter 4 introduced HF-based chemistry at low temperature: adsorbed HF and water on the oxide surface form a reactive layer that the ions convert into volatile products far more efficiently than a fluorocarbon film. Feed gases include HF itself, or H₂ with a fluorine source (C₄F₈, NF₃, SF₆), with the wafer at −40 to −70 °C.

### 14.1.2 Time to Depth

```
Illustrative cryogenic HF-based main etch:
  ER₀ = 1100 nm/min (TEOS-equivalent), k = 0.012, w = 28 nm
  k/(2w) = 2.14×10⁻⁴ nm⁻¹

  G(1600) = 1600 + 2.14×10⁻⁴ × 1600² = 1600 + 549 = 2149 nm
  t = 2149 / 1100 = 1.95 min    (vs. 4.19 min, reference)

  Bottom rate at 1600 nm: 1 / (1 + 0.012 × 57.1) = 0.59 of ER₀
  ∂h/∂w at 1600 nm:
    (0.012 × 1600² / (2 × 28²)) / (1 + 0.012 × 1600/28)
    = 19.6 / 1.69 = 11.6 nm per nm   (vs. 15.2)
```

Halving the etch time halves the mask erosion at the same erosion rate, and the lower ARDE coefficient cuts the CD-to-depth sensitivity by a quarter.

### 14.1.3 What Protects the Sidewall?

Cryogenic HF etch has little fluorocarbon polymer. The sidewall is protected mainly by its low temperature, which slows the chemical lateral etch, and by thin condensed or adsorbed layers. The protection is sensitive to temperature: a few degrees warmer at the wafer edge can give a different bow. The temperature uniformity requirements of Chapter 8 tighten accordingly.

### 14.1.4 Costs

```
Cryogenic HF etch: costs and risks (illustrative)
  Hardware: chuck at ≈ −90 °C surface; chillers; insulated chuck; warm walls
  Throughput: wafer cooldown/warmup adds 20–40 s per wafer
  Residues: (NH₄)₂SiF₆ on nitride supports; condensed products in holes
  Nitride steps: HF chemistry etches SiN differently; support steps may still
                 use fluorocarbon chemistry at a different temperature
  Mask: carbon mask selectivity similar or higher; mask facet behaviour differs
  Safety: HF handling and abatement
```

---

## 14.2 Taller Molds

### 14.2.1 The Capacitance Argument

```
Reference H_eff = 1461 nm → C_s = 8.9 fF
A 2.0 µm mold with the same support and stop thicknesses:
  H_eff = 2000 − 20 − 0.70 × 170 = 1861 nm → C_s = 8.9 × 1861/1461 = 11.3 fF
  or the same 8.9 fF at a 21% smaller average CD (28 × 1461/1861 = 22.0 nm)
```

### 14.2.2 The Etch Cost

```
Reference chemistry, H = 2000 nm:
  G(2000) = 2000 + 3.57×10⁻⁴ × 2000² = 2000 + 1429 = 3429 nm
  t = 3429 / 600 = 5.71 min   (+36% for +25% depth)
  Bottom rate: 1 / (1 + 0.020 × 71.4) = 0.41 of ER₀
  ∂h/∂w at 2000 nm: (0.020 × 2000² / 1568) / (1 + 1.43) = 51.0/2.43
                  = 21.0 nm per nm
  Mask loss scales with time: ≈ 616 × 5.71/4.19 ≈ 840 nm
  → 1350 − 840 = 510 nm remaining; at the 500 nm limit

Twisting with onset still at 800 nm:
  constant-angle model:  × (1200/800) = × 1.5
  growth model (L_g = 400 nm): (e³ − 1)/(e² − 1) = 19.1/6.39 = × 3.0
```

A 25% taller mold costs 36% more etch time, a 38% larger depth sensitivity to CD, all of the mask margin, and 1.5 to 3 times the twist. Taller molds therefore come with thicker or harder masks (Chapter 13), cryogenic or waveform-tailored etch, and an extra support layer to straighten the hole and stiffen the pillars.

---

## 14.3 Two-Tier Holes

### 14.3.1 The Scheme

Instead of etching one tall hole, the mold is built and etched in two tiers:

```
Two-tier capacitor flow (simplified):
  1. Lower mold (≈ 1.0 µm) → lower-tier hole etch → land on pad
  2. Fill the lower holes with a sacrificial material (e.g., carbon or poly)
  3. Upper mold (≈ 1.0 µm) with its own supports and hard mask
  4. Upper-tier hole etch, aligned to the lower holes, landing on the
     sacrificial fill
  5. Remove the sacrificial fill through the upper holes
  6. Electrode fill of the joined hole
```

### 14.3.2 Etch Time

```
Each tier, reference chemistry, h = 1000 nm:
  G(1000) = 1000 + 3.57×10⁻⁴ × 10⁶ = 1357 nm → 2.26 min per tier
Two tiers: 4.52 min for 2.0 µm (vs. 5.71 min single-tier)
Bottom rate at the end of each tier: 1 / (1 + 0.020 × 35.7) = 0.58 of ER₀
∂h/∂w at 1000 nm: (0.020 × 10⁶ / 1568) / (1.71) = 7.5 nm per nm
```

Each tier is a much easier etch: shallower, with a smaller depth sensitivity, less twist, and no mask crisis. The cost moves to integration: two molds, two masks, two lithography steps, a sacrificial fill and removal, and an alignment between the tiers.

### 14.3.3 The Tier Joint

```
Tier-to-tier alignment budget (illustrative, 3σ):
  Upper-to-lower lithographic overlay        3.0 nm
  Lower-tier bottom twist (at its 1 µm top)  not applicable (top is printed)
  Upper-tier twist/tilt at its bottom        3.0 nm
  RSS                                         4.2 nm

Joint: the upper hole (bottom CD ≈ 24 nm) lands on the lower hole
(top CD ≈ 32 nm); offset 4.2 nm leaves an overlap ≥ 24 nm on the narrower
side
```

The joint creates a step in the hole profile: the narrow bottom of the upper hole sits on the wide top of the lower hole. The electrode must fill around the step without voids, and the support layers must sit away from the joint.

---

## 14.4 Cylinder, Pillar, and Beyond

```
Capacitor forms by generation (illustrative):

  Form                     Area used                 Viable when
  ──────────────────────────────────────────────────────────────────────────
  Double-sided cylinder    inside + outside of a     inner diameter ≥ 2×
                           thin TiN shell            (dielectric + plate),
                                                     roughly CD ≥ 35–40 nm
  Single-sided cylinder    inside only               mold kept; simpler,
                                                     less area
  Pillar (reference)       outside of a solid TiN    CD ≤ 30 nm; needs
                           pillar                    supports; mold removed
  Pillar + extra supports  as pillar                 taller molds
```

```
Area comparison at CD 32 nm (top), H = 1.6 µm, TiN 5 nm:
  Double-sided cylinder: outside π × 32 + inside π × (32 − 10) = π × 54
  Pillar:                outside π × 32
  → cylinder ≈ 1.7× the area at this CD, if the inside can be filled
  Inside diameter 22 nm must hold 2 × (dielectric 5 nm + plate ≥ 5 nm) = 20 nm
  → marginal at 32 nm; impossible at 28 nm and below
```

The pillar has dominated since the hole CD fell below about 30 nm. Its single-sided area is paid for by height, which is why the hole has grown so tall.

---

## 14.5 4F² Vertical-Channel DRAM

In a 4F² cell, the access transistor is vertical: its channel runs up a silicon pillar, with the word line wrapped around it and the bit line buried below. The capacitor sits directly above each transistor pillar.

```
4F² cell, F = 15 nm (illustrative):
  Cell area 4F² = 900 nm²
  Hexagonal-equivalent pitch: p² = 900 / 0.866 = 1039 nm² → p = 32.2 nm
  (on a square grid: p = 2F = 30 nm)

Capacitor hole (illustrative): top CD 22 nm, bottom 16 nm, average 19 nm;
  wall at top on a 30 nm square grid: 8 nm; diagonal 42.4 − 22 = 20.4 nm

Capacitance at H = 1.6 µm, EOT 0.5 nm, with the reference support loss:
  C_s ≈ 8.9 × 19/28 = 6.0 fF
```

Vertical-channel arrays have shorter bit lines with lower C_BL, so a smaller C_s can give the same signal. Even so, the capacitor hole of a 4F² cell is narrower and its wall thinner than the reference, and the aspect ratio for the same height rises to about 84:1 on the average CD. The etch requirements of Chapters 10–12 tighten together. Square-grid layouts also lose the six-fold symmetry of the honeycomb, so each hole has four close neighbours and four farther ones, which makes its polymer and charging environment anisotropic.

---

## 14.6 3D DRAM

3D DRAM stacks cells in layers, as 3D NAND stacks memory cells. In the most widely discussed forms, each layer is a horizontal silicon channel in an epitaxial Si/SiGe stack, with a horizontal capacitor beside it. The vertical capacitor hole of this book disappears. In its place:

1. **Deep stack etches** cut slits or holes through the Si/SiGe stack (Book #24 and #25 territory), at aspect ratios similar to or above the capacitor hole.
2. **Lateral recesses** selectively remove SiGe or Si from the sidewalls of those openings to form horizontal cavities.
3. **Lateral capacitors** are built inside the cavities by conformal deposition.

```
Etch challenges carried over from the capacitor hole:
  High-aspect-ratio vertical etch with tight profile and no bow
  Twisting/tilting of the openings that define every layer's cell
  Selectivity between alternating materials (Si vs. SiGe instead of
    oxide vs. nitride)
New challenges:
  Lateral etch uniformity layer to layer
  Epitaxial stack stress and wafer bow
```

The physics of this book (ARDE, charging, twisting, the mask budget) applies directly to the vertical part of 3D DRAM. The capacitor itself moves from the vertical etch to the lateral one.

---

## Summary and Key Takeaways

1. **Cryogenic HF chemistry halves the etch.** About 1.95 min instead of 4.19 min for 1.6 µm, with a lower ARDE coefficient and a smaller CD-to-depth sensitivity.

2. **Taller molds cost more than their height.** +25% depth costs +36% time, the whole mask margin, +38% CD sensitivity, and 1.5–3× the twist.

3. **Two tiers trade etch difficulty for integration.** Each tier is a 1 µm etch at 7.5 nm/nm sensitivity, but the tiers must be aligned within about 4 nm.

4. **The pillar won because the cylinder ran out of room.** Below about 30 nm CD, the inside of a cylinder cannot hold a dielectric and a plate.

5. **4F² cells shrink the hole further.** On a 30 nm grid, the hole is about 22 nm and its aspect ratio over 80:1.

6. **3D DRAM moves the capacitor sideways.** The vertical etch remains, cutting through Si/SiGe stacks, but the capacitor is built by lateral recess.

---

## Study Questions

1. Compute the cryogenic etch time and bottom rate for a 2.0 µm mold with ER₀ = 1100 nm/min and k = 0.012. Compare with the reference chemistry at 2.0 µm.

2. A harder mask with selectivity 9 (versus 5.5) is used for the 2.0 µm mold. With erosion proportional to time and inversely to selectivity, how much mask remains from 1350 nm?

3. A two-tier process uses tiers of 900 nm (lower) and 1100 nm (upper). Compute the etch time of each tier and the total.

4. For a double-sided cylinder at CD 36 nm with 5 nm TiN, compute the area ratio to a pillar at the same CD. What inner clearance is left for the dielectric and plate?

5. A 4F² array on a 30 nm square grid uses holes with average CD 20 nm. What height gives C_s = 6.5 fF with the reference EOT and support loss?

---

**Next Chapter:** [Chapter 15: Endpoint, Metrology & Advanced Process Control](./15-endpoint-metrology-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
