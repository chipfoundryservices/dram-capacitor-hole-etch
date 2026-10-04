# Chapter 13: Charging, Mask Integrity, Striation & Hole Distortion

## Overview

The previous chapters treated the bow, the twist, and the bottom one at a time. Several mechanisms act on all of them at once. Charge on the hole walls bends ions into the bow, steers twisting holes, and slows the bottom. The carbon mask thins, facets, and roughens through the etch, and every change in its shape changes the ions that enter the hole. The edge of the mask carries roughness from lithography, which the etch either smooths or turns into vertical grooves down the wall. And the hole that should be round can become oval, square-cornered, or irregular, losing area and wall at the same time.

This chapter brings these shared mechanisms together: charging in more detail, the mask through the etch, striation and hole-edge roughness, circularity and distortion, and the effect of the support layers on the wall.

**Learning Objectives:**
- Describe the charge distribution along a high-aspect-ratio hole and its consequences
- Explain how sidewall conductivity relieves charging
- Track the mask's thickness, facet, and opening through the etch
- Explain how mask-edge roughness becomes striation and how to suppress it
- Quantify circularity and its cost in area and wall thickness
- Describe roughness and steps at the support layers

---

## 13.1 Charging Along the Hole

### 13.1.1 The Charge Profile

```
Charge along a 57:1 hole during the bias-on phase (schematic):

  depth     wall charge            cause
  ────────────────────────────────────────────────────────
  top       negative (−)           electrons arrive at wide angles
  upper     weakly negative        fewer electrons; some grazing ions
  middle    near neutral / mixed   transition
  lower     positive (+)           ions reach; electrons do not
  bottom    positive (++)          tens to hundreds of volts
```

The negative upper wall attracts low-energy positive ions and bends them into it, adding to the bow (Chapter 10). The positive lower wall and bottom repel arriving ions slightly and focus them away from the bottom corners, which tapers the bottom. The transition between the two sits roughly where the bow ends and the taper begins.

### 13.1.2 Sidewall Conduction

Charge leaks along the wall through the polymer film and the oxide surface. A conductive wall flattens the potential profile and reduces both the bottom potential and the lateral asymmetries that cause twisting.

```
Illustrative sidewall sheet resistance:
  Clean thermal oxide:             > 10¹⁶ Ω/□
  Fluorocarbon-polymer-coated,
    during ion bombardment:        10¹²–10¹⁴ Ω/□
  Doped (BPSG) wall, bombarded:    10¹¹–10¹³ Ω/□

RC time of a wall segment (length 200 nm, circumference 90 nm,
capacitance ≈ 1.8×10⁻¹⁷ F per 50 nm from Chapter 6 → ≈ 7×10⁻¹⁷ F):
  R ≈ R_□ × (200/90) ≈ 2×10¹³ Ω for R_□ = 10¹³ Ω/□
  τ = RC ≈ 2×10¹³ × 7×10⁻¹⁷ = 1.4×10⁻³ s
```

A relaxation time of about a millisecond is comparable to the pulse periods of Chapter 6 (0.2–1 ms). Wall conduction therefore matters on the same time scale as pulsing. The doped lower oxide has a more conductive wall, one reason twisting is often weaker in BPSG than in undoped oxide at the same aspect ratio.

### 13.1.3 Charging Damage to the Cell

Once the hole opens onto the W pad, the pad is connected through the storage-node contact to the cell's n⁺ junction. The positive charge delivered by the ions flows into the junction. The cell transistor is off, so the current flows through the junction to the substrate. At ion currents of 1.2 mA/cm² over a 452 nm² bottom, the current per cell is tiny (about 5×10⁻¹⁵ A), and junction damage from the BO step is not usually a concern. It becomes one if a hole stays open to the pad for a long overetch at full bias, or if the hole bottom arcs. The BO step's reduced bias helps.

---

## 13.2 The Mask Through the Etch

### 13.2.1 Thickness and Facet

```
Mask evolution (reference, illustrative):

  Time (s)   ACL top (nm)   facet angle   top CD of the hole (nm)
  ──────────────────────────────────────────────────────────────
     0       1350           ≈ 0°          31.0 (mask open)
   110       1135           ≈ 8°          31.5
   215       940            ≈ 14°         31.8
   305       734            ≈ 20°         32.0 (at the mold top)

Facet: the top corners of the mask opening round and slope inward-down.
```

The facet grows as the mask thins. Chapter 10's reflection model sent facet-reflected ions into the top of the hole. Late in the etch, the facet is close enough to the mold top that some reflected ions land in the top support and the upper oxide, widening the top CD by up to 1 nm.

### 13.2.2 Mask Clogging and Opening Narrowing

Polymer deposits on the mask sidewall, inside the mask opening. If the mask opening narrows faster than the facet widens it, the hole becomes shadowed. A narrowed mask opening cuts the ion flux into the hole and acts like an extra neck. It shows up as a smaller top CD, a lower rate at depth, and a smaller bottom CD.

### 13.2.3 Mask Materials

```
Mask options (illustrative):
  Material                   Oxide:mask    Ease of open   Ease of strip   Other
                             selectivity
  ──────────────────────────────────────────────────────────────────────────────
  PECVD ACL (reference)      ≈ 5.5         good           O₂ ash          baseline
  High-density ACL           ≈ 7           harder         O₂ ash          higher stress
  B-doped carbon             ≈ 9           harder         needs F-assisted B residues
                                                           strip
  W-doped carbon             ≈ 12          much harder    wet + dry       metal
                                                                          contamination
  Polysilicon over ACL       ≈ 15 (Si)     separate etch  separate strip  stack complexity
```

Harder masks allow taller molds (Chapter 14) at the cost of a harder mask open, a harder strip, and new contamination risks.

---

## 13.3 Striation

### 13.3.1 What Striation Is

Striation is vertical grooving of the hole wall. Seen from above, the hole edge is wavy instead of round. Seen in cross-section, the waves run down the wall as ridges and grooves.

```
Striation metrics:
  Hole-edge roughness (radius variation around the perimeter, 3σ)
  Spatial period around the perimeter: often 5–15 nm
  Spec (Chapter 1): ≤ 2.0 nm (3σ) at the top
```

### 13.3.2 How It Forms

1. **Mask-edge roughness.** The resist or spacer edge has line-edge roughness of 2–3 nm (3σ). The mask open transfers it into the ACL.
2. **Amplification by polymer.** Polymer deposits more thickly in the concave parts of a rough edge (more solid angle of wall) and less on the convex parts. Ions then etch the convex parts more. Depending on the balance, roughness grows or shrinks.
3. **Mask softening.** A mask that is heated and softened by ion bombardment can buckle at its edges, creating wiggles in the opening.

### 13.3.3 Suppression

```
Striation sensitivities (illustrative):
  Smoothing step in the mask open (lateral trim):   −0.5 nm
  Lower Π in ME1 (thinner, more uniform polymer):    −0.3 nm per −0.03 Π
  Lower wafer T (mask hardening):                    −0.2 nm per −5 °C
  Higher-density ACL:                                −0.3 nm
```

Striation costs capacitance only slightly (a rough wall has slightly more area), but it thins the wall locally and roughens the electrode surface, which concentrates the electric field in the dielectric and raises leakage.

---

## 13.4 Circularity and Distortion

### 13.4.1 Circularity

```
Circularity = min diameter / max diameter (top-down, at a given depth)
Spec ≥ 0.90 at the top

An ellipse with axes a ≥ b and the same area as a 32 nm circle:
  a b = 16²; b/a = 0.90 → a = 16 / √0.90 = 16.87 nm, b = 15.18 nm
  max diameter 33.7 nm, min 30.4 nm
  wall toward the neighbour along the long axis: 45 − 33.7 = 11.3 nm
  (vs 13.0 nm for a circle)
```

An oval hole of the same area as the reference hole spends 1.7 nm of wall in its long direction. If the long axes of neighbouring holes line up, the wall between them thins further.

### 13.4.2 Sources of Distortion

- **Patterning**: double-SADP crossings produce parallelograms; rounding steps make them nearly circular, but some anisotropy remains.
- **Neighbour arrangement**: the six neighbours of a honeycomb hole are evenly spaced, but if the lattice is stretched to match the cell grid (Chapter 1), the neighbour distances differ slightly and the polymer and charge environment is anisotropic.
- **Deep distortion**: below about 1 µm, holes can become irregular and lose their round shape, especially when the mask is thin and polymer deposition is patchy.

---

## 13.5 The Support Layers

### 13.5.1 Steps and Notches

The support nitrides etch in their own steps. Their profile in the hole often differs from the oxide above and below: slightly narrower if the nitride step is more polymerizing, or with a notch at the interface if the transition is abrupt (Chapter 7).

```
Illustrative profile at the middle support:
  oxide just above:    30.5 nm
  SiN support:         29.5 nm (−1 nm step)
  oxide just below:    30.0 nm
  notch at the lower interface (abrupt transition): +1.5 nm local widening
```

A narrower support ring is harmless for the hole but leaves a ledge that the TiN fill must cover. A notch below the support thins the wall locally at the depth where the support must later hold the pillars.

### 13.5.2 Support Integrity After Mold Removal

The support layers hold the pillars after the oxide is gone. Their strength depends on the remaining nitride between holes:

```
Remaining support web between holes at the top support (CD 32 nm, p 45):
  thinnest web width = 13 nm (on the line of centres)
  web cross-section per hole edge = 13 nm × 120 nm
After support-opening patterning, about 30% of the web is removed
  (Chapter 1) → the rest must carry the capillary load during drying
```

A top CD 1 nm larger thins the web by 1 nm, about 8% of its width, and the web's bending stiffness by more. Top CD control is therefore also a mechanical requirement.

---

## Summary and Key Takeaways

1. **The hole has a charge profile.** Negative at the top, positive at the bottom. The upper charge feeds the bow; the lower charge tapers and slows the bottom.

2. **Wall conduction matters on millisecond time scales.** Polymer-coated and doped walls relax charge in about a millisecond, matching pulse periods.

3. **The mask changes through the etch.** It loses about 600 nm, and its facet grows from 0° to about 20°, widening the top CD late in the etch.

4. **Striation grows from mask-edge roughness.** Polymer can amplify or smooth it. A smoothing step in the mask open is the most effective fix.

5. **Oval holes spend wall.** At circularity 0.90, the wall along the long axis loses 1.7 nm.

6. **The supports are mechanical.** The web between holes at the top support is 13 nm. Top CD is a strength requirement as well as a capacitance one.

---

## Study Questions

1. Estimate the RC time of a 200 nm wall segment for R_□ = 10¹² Ω/□ and 10¹⁴ Ω/□. Which would benefit more from 2 kHz bias pulsing?

2. Estimate the ion current reaching the pad of one cell during the BO step, at 0.8 mA/cm² over a 24 nm bottom. Over 30 s, how much charge passes through the junction?

3. A mask with selectivity 7 replaces the reference ACL (5.5). Assuming the same step times, how much ACL remains at the end of the etch?

4. For circularity 0.85 at the same area as a 32 nm circle, compute the max diameter and the wall along the long axis.

5. The striation at the top is 2.6 nm (3σ). Which two changes from Section 13.3.3 bring it within specification with the least effect on the bottom CD?

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Cryogenic Etch, Taller Molds, Multi-Tier Holes, 4F² & 3D DRAM](./14-advanced-capacitor-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
