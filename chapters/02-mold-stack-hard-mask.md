# Chapter 2: The Mold Stack, Support Layers & Hard Mask

## Overview

The capacitor hole etch inherits everything it cuts through. The mold sets the depth and the materials the plasma meets on the way down. The nitride supports set where the etch must change chemistry, and where steps and notches tend to form. The carbon hard mask sets how long the etch can run and the shape of the opening the ions see. The patterning sets the top CD of every hole and how it varies from hole to hole. Each of these adds variation that the etch either absorbs or amplifies.

This chapter describes the incoming stack layer by layer, the reasons for each layer, and the variation each brings. It ends with the mask budget and the incoming specification the hole etch needs.

**Learning Objectives:**
- Describe the five-layer mold and the purpose of each layer
- Explain why the lower oxide is often doped and how its etch rate helps the bottom of the hole
- Describe the support layers and the support-opening scheme that follows the etch
- Compute the amorphous-carbon mask budget for the reference etch
- Explain how honeycomb patterning by double SADP or EUV creates CD families
- Estimate wafer bow from film stress and its effect on chucking and placement
- State the incoming specification for the hole etch

---

## 2.1 The Mold

### 2.1.1 The Reference Stack

```
Reference mold (top to bottom), H = 1600 nm:

  ┌───────────────────────────┐  SiON cap            40 nm  ┐ hard mask
  │  amorphous carbon (ACL)   │                    1400 nm  ┘
  ├───────────────────────────┤ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ z = 0
  │  top SiN support          │  LPCVD/PECVD SiN    120 nm
  ├───────────────────────────┤                               z = 120
  │  upper oxide (PE-TEOS)    │  undoped SiO₂       650 nm
  ├───────────────────────────┤                               z = 770
  │  middle SiN support       │                      50 nm
  ├───────────────────────────┤                               z = 820
  │  lower oxide (BPSG)       │  B/P-doped SiO₂     760 nm
  ├───────────────────────────┤                               z = 1580
  │  bottom SiN etch stop     │                      20 nm
  ├───────────────────────────┤                               z = 1600
  │  W landing pads in SiN    │
  └───────────────────────────┘

Oxide fraction of the mold: (650 + 760)/1600 = 0.88
Nitride fraction:           (120 + 50 + 20)/1600 = 0.12
```

### 2.1.2 Why Two Oxides

The lower oxide is often a **doped** oxide such as BPSG or a carbon- or boron-doped oxide. There are two reasons.

1. **It etches faster in the plasma.** Boron and phosphorus weaken the Si–O network, and doped oxides etch about 10–25% faster than TEOS under the same ion flux. At the bottom of the hole, where ARDE has cut the rate by half, this partly offsets the loss (Chapter 3).
2. **It etches faster in the wet removal.** After electrode deposition, the mold is removed in an HF-based solution through openings in the supports. The lower oxide is farthest from the openings, so a faster wet rate helps it clear at about the same time as the upper oxide.

```
Illustrative plasma etch rates (open area, reference main-etch chemistry):
  PE-TEOS:   600 nm/min
  BPSG:      700 nm/min  (ratio 1.17)
  SiN:       420 nm/min  (ratio 0.70 to TEOS in the oxide step)

Wet etch in dilute HF (illustrative, relative):
  TEOS 1.0, BPSG 3–5, SiN 0.02–0.05
```

The doped oxide has costs. It is more sensitive to moisture, it can outgas during the etch, and its dopants appear on the hole wall as a different polymer and charging environment. The interface between the middle support and the lower oxide is a common place for the bow to begin (Chapter 10).

### 2.1.3 The Supports

A TiN pillar 28 nm wide and 1.6 µm tall has an aspect ratio near 57. After the oxide is removed, pillars this slender lean, bend under the surface tension of the drying liquid, and touch their neighbours. The nitride supports hold them.

```
Pillar stability (illustrative):
  Without supports: capillary force during drying exceeds the restoring
  force of a 28 nm × 1600 nm TiN pillar by orders of magnitude → collapse
  With a top support: the pillar is a beam fixed at both ends; the free
  span is 1600 − 120 = 1480 nm
  With top + middle supports: two spans of ≈ 650 and 760 nm;
  bending stiffness ∝ 1/L³ → each span ≈ 10 times stiffer than 1480 nm
```

After the TiN fill, openings are etched through the top support (and, by a deeper etch, the middle support) so the wet etch can reach the oxide. Each opening exposes parts of several pillars. In the reference design the openings expose about 30% of each pillar's perimeter at the support level, and the rest of the support stays bonded to the pillars (Chapter 1, Section 1.3.3).

For the hole etch, the supports matter in three ways:

1. They are **nitride**, so the plasma must etch them in a different regime from the oxide. A chemistry tuned for oxide etches nitride more slowly and with a different polymer balance.
2. Their **interfaces** with the oxide create discontinuities in the sidewall polymer and in the charge stored on the wall. Notches and bow peaks often sit just below a support.
3. The **top support** is the first thing the hole meets. Its profile becomes the neck of the hole and sets the opening every later ion must pass.

### 2.1.4 The Bottom Stop

The 20 nm bottom nitride protects the landing pads and the pad-isolation nitride from the long oxide etch. The oxide main etch runs with high selectivity to nitride, so it slows down on the bottom stop across the wafer. A final step opens the stop with a nitride-capable chemistry and lands on tungsten (Chapter 12).

```
Bottom stop budget (illustrative):
  Main etch oxide:nitride selectivity at the hole bottom: ≈ 8
  Overetch in the main step: ≈ 25 s at the bottom-of-hole rate
  Lower-oxide equivalent removed at the bottom in that time ≈ 140 nm (at the
  bottom-of-hole rate, Chapter 3) → nitride loss ≈ 140/8 = 17.5 nm
  → most of the 20 nm stop is consumed; the stop-open step clears the rest
```

A thicker stop is safer for the main etch but harder to open at the bottom of a 50:1 hole. A thinner stop risks punching through in the deepest holes before the shallowest are out of the oxide.

### 2.1.5 Mold Film Variation

```
Mold thickness variation (illustrative, 3σ within wafer):
  Upper oxide  ±1.5%  (±10 nm)
  Lower oxide  ±1.5%  (±11 nm)
  Supports     ±3%    (±4, ±1.5 nm)
  Total H      ±15 nm (RSS, ≈ ±0.9%)
```

A ±15 nm range in H is small compared with the overetch, but it maps directly into the radial profile of capacitance (0.61 fF per 100 nm) and into the time at which each wafer zone reaches the bottom stop.

---

## 2.2 The Amorphous-Carbon Hard Mask

### 2.2.1 Why Carbon

Photoresist cannot survive a 1.6 µm oxide etch at kilovolt ion energies. The mask is amorphous carbon (ACL), deposited by PECVD from hydrocarbons at 400–600 °C. It is dense, hard, rich in sp³ bonds, and strongly resistant to fluorocarbon plasmas. It is also easy to remove in an oxygen ash after the etch.

```
Reference ACL (illustrative):
  Thickness 1400 nm; density ≈ 1.8 g/cm³; H content ≈ 15–20 at.%
  Stress −300 MPa (compressive)
  Extinction coefficient at 633 nm ≈ 0.4 (needs a transparent-window
  alignment strategy or a lower-k variant)
  SiON cap 40 nm: masks the ACL open; doubles as an antireflective layer
```

Higher-density and boron- or tungsten-doped carbon masks give better selectivity, but they are harder to open and strip and can bring metal contamination. Chapter 13 compares them.

### 2.2.2 The Mask Open

The ACL is opened in an O₂- or SO₂-based plasma through the SiON (Book: *Carbon Hard Mask Etch*). Its result is the hole the capacitor etch begins from:

```
After mask open (reference, illustrative):
  ACL opening CD at bottom of the ACL: 31 nm
  ACL sidewall angle: 89.3°
  ACL thickness: 1350 nm (top loss 50 nm in the open, SiON partly gone)
  Mask aspect ratio: 1350/31 = 44
```

The mask is itself a high-aspect-ratio hole. Its taper, its bow, and any twist it carries are passed to the mold etch below.

### 2.2.3 The Mask Budget

The ACL erodes at a rate set by the open-surface ion flux and chemistry. That rate does **not** slow down as the hole deepens. The oxide at the hole bottom does. The effective selectivity of the whole etch is therefore much lower than the blanket selectivity.

```
Reference etch steps and ACL erosion (illustrative):

  Step                    Time    ACL erosion rate   ACL loss
  ─────────────────────────────────────────────────────────────
  Top SiN (SN1)           20 s    150 nm/min           50 nm
  Upper oxide (ME1)       90 s    110 nm/min          165 nm
  Middle SiN (SN2)        15 s    150 nm/min           38 nm
  Lower oxide (ME2)      150 s    105 nm/min          263 nm
     (121 s to the stop + 29 s overetch)
  Bottom SiN open (BO)    30 s    120 nm/min           60 nm
  ─────────────────────────────────────────────────────────────
  Total                  305 s  (5.1 min)             576 nm
  Faceting allowance at the top corners                ≈ 40 nm
  Remaining ACL: 1350 − 576 − 40 ≈ 730 nm   (spec ≥ 500 nm) ✓

Blanket oxide:ACL selectivity ≈ 600/110 = 5.5
Effective selectivity (mold removed / ACL lost) = 1600/616 ≈ 2.6
```

The difference between 5.5 and 2.6 is ARDE. Every minute spent at the bottom of a deep hole erodes the mask at the full rate while the hole gains little depth. Taller molds therefore cost mask faster than linearly (Chapter 14).

The remaining mask is not just a margin. It is part of the hole. A tall mask lengthens the total hole the ions must traverse and raises the aspect ratio at the start. A thin mask facets, and the facet sends ions into the sidewall below it. Chapter 13 shows that the bow often grows as the mask thins late in the etch.

---

## 2.3 Honeycomb Patterning

### 2.3.1 Two Routes

The hexagonal hole array at 45 nm pitch is below the single-exposure limit of 193 nm immersion lithography (about 76–80 nm pitch). Two routes are common.

**Double SADP at 60°.** Two line-space patterns are made by self-aligned double patterning, one rotated 60° (or 120°) from the other. Their crossings define parallelogram islands or holes, which are rounded by the subsequent etches. The hexagonal lattice appears as the intersection of two line sets.

**EUV.** A single EUV exposure (or EUV with a spacer step) prints the holes directly. Stochastic variation in the exposure gives each hole a slightly different CD and edge.

### 2.3.2 CD Families

In double SADP, the holes come in **families**: some are bounded by core-side lines, others by gap-side lines, and the spacer and core widths differ slightly. A typical honeycomb has two to four CD families whose means differ by 0.5–1.5 nm.

```
CD families (illustrative, double SADP):
  Family A (core-core):   top CD 32.4 nm
  Family B (core-gap):    top CD 32.0 nm
  Family C (gap-gap):     top CD 31.4 nm
  Within each family, σ ≈ 0.5 nm

Depth sensitivity at fixed time (Chapter 3): ∂h/∂CD ≈ 15 nm/nm
  Family C reaches the bottom stop ≈ (32.4 − 31.4) × 15 = 15 nm behind A
```

EUV has no families, but its stochastic hole-to-hole CD variation is larger, about σ = 0.8–1.2 nm at this pitch. The smallest holes of the distribution, three or four sigma below the mean, set the overetch.

### 2.3.3 Placement

Each hole's top position is set by the lithography and SADP. The hole etch must not add to it. The bottom position depends on the top position plus the twist and tilt the etch adds (Chapter 11).

---

## 2.4 Stress and Wafer Bow

A 1.4 µm compressive carbon film, a 1.6 µm mold, and the structures below them bend the wafer.

```
Stoney estimate of wafer curvature from one film (biaxial modulus E/(1−ν)):
  κ = 6 σ_f t_f (1 − ν) / (E t_s²)
  Sag across the full diameter: δ = κ D² / 8

  ACL: σ_f = −300 MPa, t_f = 1.4 µm
  Si:  E = 130 GPa, ν = 0.28, t_s = 775 µm, D = 300 mm

  κ = 6 × 3.0×10⁸ × 1.4×10⁻⁶ × 0.72 / (1.30×10¹¹ × 6.01×10⁻⁷)
    = 1814 / 78,100 = 0.0232 m⁻¹       (radius of curvature ≈ 43 m)
  δ = 0.0232 × 0.090 / 8 = 2.6×10⁻⁴ m = 260 µm
```

Compressive ACL alone would bow the wafer by about 260 µm. Tensile mold nitrides and backside films are used to balance it. The electrostatic chuck can flatten a wafer bowed by up to about 200–300 µm, but a wafer that is clamped flat while its films want to bow carries in-plane stress. That stress shifts the hole positions slightly between lithography (unclamped or vacuum-clamped) and etch (electrostatically clamped), and it changes the gap between wafer and chuck at the edge, which shifts the edge temperature (Chapter 8).

---

## 2.5 The Incoming Specification

```
Incoming specification for the capacitor hole etch (reference, illustrative)

Mold
  Total H                         1600 ± 15 nm (3σ, within wafer)
  Top support / middle support    120 ± 4 nm / 50 ± 1.5 nm
  Lower-oxide dopant level        within ±0.2 wt% (B, P)
  Moisture: queue after BPSG anneal ≤ 24 h

Mask
  ACL after open                  ≥ 1330 nm
  ACL bottom CD                   31.0 ± 1.0 nm (all families)
  Family offset                   ≤ 1.2 nm between means
  ACL sidewall angle              ≥ 89.0°; no bow > 1 nm; no twist visible
                                  in top-down HV-SEM
  Residue (SiON, polymer)         none in the hole bottom

Wafer
  Bow                             ≤ 120 µm before clamp
  Backside particles              ≤ 30 (≥ 0.2 µm) for clamping
```

---

## Summary and Key Takeaways

1. **The mold has five layers.** Two oxides make up 88% of it. Three nitrides support the pillars and stop the etch.

2. **The lower oxide is often doped.** It etches 10–25% faster, partly offsetting ARDE at the bottom, and it clears faster in the wet removal.

3. **The supports are part of the profile.** The top support forms the neck. Bow peaks and notches tend to sit just below support interfaces.

4. **The mask budget is set by time, not depth.** Blanket selectivity is about 5.5, but effective selectivity over the whole etch is about 2.6. The reference etch leaves about 730 nm of the 1350 nm ACL.

5. **Patterning creates CD families.** A 1 nm family offset becomes about 15 nm of depth at fixed time.

6. **Stress matters.** A 1.4 µm compressive carbon film alone would bow the wafer by about 260 µm. It must be balanced by tensile films, and clamping a bowed wafer flat shifts both placement and edge temperature.

---

## Study Questions

1. The lower oxide is changed from BPSG (700 nm/min) to TEOS (600 nm/min). Using the step times of Section 2.2.3, how much longer is the lower-oxide step if the same depth must be reached? How much more ACL is consumed?

2. A taller mold adds 200 nm to the lower oxide. Assuming the bottom-of-hole rate in the added depth is 40% of the open-area rate, compute the extra time and the extra ACL loss. Is the 500 nm remaining-mask specification still met?

3. A double-SADP pattern has family means of 32.6, 32.0, and 31.2 nm. With ∂h/∂CD = 15 nm/nm, how far behind is the smallest family when the largest reaches the bottom stop?

4. Compute the Stoney bow from a 1.6 µm mold with an average stress of +80 MPa (tensile) and compare it with the ACL bow. What is the net bow?

5. The stop is thinned to 15 nm. With the bottom-of-hole oxide:nitride selectivity of 8 and 140 nm of oxide-equivalent overetch, will the stop survive the main step? What change to the main etch would restore margin?

6. Explain why the effective mask selectivity would fall further if the hole ARDE coefficient rose from 0.020 to 0.030.

---

**Next Chapter:** [Chapter 3: High-Aspect-Ratio Hole Etch Physics](./03-har-hole-etch-physics.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
