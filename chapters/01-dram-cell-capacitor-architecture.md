# Chapter 1: The DRAM Cell & the Role of the Capacitor Hole

## Overview

A DRAM stores each bit as charge on a capacitor, reached through a single access transistor. Books #26 and #27 followed the transistor: the active area, the buried word line, and the gate edge beside the storage-node junction. This book follows the charge. Above the transistor, above the bit line, above the storage-node contact and its landing pad, stands a capacitor about 1.6 µm tall and 28 nm wide. Its shape is set by a hole etched through a mold of oxide and nitride. When the mold is removed, the electrode that filled the hole remains as a pillar, and the dielectric and plate are wrapped around it.

This chapter explains why the capacitor must be so tall, how the holes are arranged, how much capacitance each nanometre of depth and diameter buys, and what the bottom of the hole must land on. It ends with the specification sheet that the rest of the book works to.

**Learning Objectives:**
- Compute the sense signal and retention budget from the cell capacitance
- Describe the honeycomb storage-node layout and compute pitch, CD, and wall thickness
- Compute cell capacitance from hole depth, profile, and dielectric EOT
- Compute the capacitance sensitivity to depth, average CD, and EOT
- Build the placement budget at the hole bottom from the landing-pad geometry
- Place the hole etch in the DRAM flow and read its specification sheet

---

## 1.1 The Cell and Its Charge

### 1.1.1 Reading a Bit

```
One DRAM cell:

        Bit line (BL)
            │
            │ bit-line contact (DC)
          ┌─┴─┐
   WL ────┤ T ├──── access transistor (buried word line, Book #27)
          └─┬─┘
            │ storage-node contact (BC) → landing pad (LP)
          ══╪══ storage capacitor C_s, plate at V_PL = V_DD/2
            │       (the subject of this book)
           ───

Read:  BL precharged to V_DD/2; WL raised; charge sharing moves the BL by
       ΔV_BL = (V_DD/2) · C_s / (C_s + C_BL)
```

The bit line is long and heavily loaded. Its capacitance C_BL is several times C_s, so only a fraction of the stored charge appears as signal. The sense amplifier must resolve that signal against its own offset, coupling noise from neighbouring bit lines, and the charge the cell has lost since its last refresh.

```
Reference values (illustrative):
  V_DD (array) = 1.1 V, plate at 0.55 V, C_BL = 40 fF

  C_s (fF)    ΔV_BL (mV)
     6           72
     8           92
     8.9        100   ← reference (Section 1.3.3)
    10          110
    12          127

  Sense-amplifier requirement (offset + noise + retention loss margin):
  ΔV_BL ≥ 90 mV at time zero  →  C_s ≥ 7.8 fF
```

The capacitance target has hardly moved for twenty years. Bit lines have become shorter and sense amplifiers better, but each generation also lowers V_DD, which takes signal away. The usual target has stayed at about 8–10 fF per cell while the cell footprint has shrunk by roughly a factor of ten.

### 1.1.2 Retention

```
Q = C_s · V_DD/2 = 8.9 fF × 0.55 V = 4.9 fC  ≈ 30,600 electrons
Allowed loss (40%) over 64 ms:
  I_max = 0.4 × 4.9×10⁻¹⁵ C / 0.064 s = 3.1×10⁻¹⁴ A = 31 fA
```

The leakage paths are the junction and gate edge (Books #26 and #27) and the capacitor dielectric itself. A smaller capacitor stores less charge, so the same leakage drains it faster. Lost capacitance does not only reduce signal. It also moves the retention tail.

---

## 1.2 The Honeycomb Layout

### 1.2.1 One Hole per Cell

The capacitors sit above the bit lines (capacitor-over-bit-line, COB). Each cell's storage-node contact rises between two bit lines and ends in a **landing pad** (LP). The landing pads are arranged on a nearly hexagonal lattice, so the capacitors above them can be packed as tightly as possible.

```
Reference cell:  F = 17 nm, 6F² = 1734 nm²

Hexagonal lattice with one hole per cell:
  area per lattice site = (√3/2) p²
  (√3/2) p² = 1734 nm²  →  p = 44.7 nm  →  reference p = 45 nm
  (area per site 1754 nm²; the lattice is stretched slightly to match
   the 34 nm × 51 nm word-line/bit-line grid)

Plan view (schematic):
     ○   ○   ○   ○   ○
       ○   ○   ○   ○
     ○   ○   ○   ○   ○      nearest-neighbour distance p = 45 nm
       ○   ○   ○   ○        row spacing (√3/2)p = 39 nm
     ○   ○   ○   ○   ○      six neighbours per hole
```

### 1.2.2 Diameter and Wall

```
Wall between neighbours (along the line of centres):
  t_wall = p − CD

  Top of the mold, CD = 32 nm:     t_wall = 13 nm
  Average,         CD = 28 nm:     t_wall = 17 nm
  Bottom,          CD = 24 nm:     t_wall = 21 nm
  At a 34 nm bow (spec max):        t_wall = 11 nm

Open fraction of the array at the top of the mold:
  (π/4)(32²) / 1754 = 804 / 1754 = 0.46

The wall is thinnest on the line of centres. Between three holes the
oxide is thicker: the triple point lies p/√3 = 26.0 nm from each centre,
so the oxide there has an inscribed radius of 26.0 − 16.0 = 10.0 nm at the top.
```

Nearly half of the array is hole at the top of the mold. Across a die with 55% array, about a quarter of the wafer surface is open hole. This makes the capacitor hole etch a strongly loaded etch: the oxide it removes is a large fraction of the oxide the plasma sees (Chapter 3).

### 1.2.3 Why the Wall Matters

The wall carries three loads:

1. **Electrical isolation.** After electrode deposition, each wall separates two TiN pillars. If the wall breaks, the two electrodes merge into a two-bit short.
2. **Mechanical support during processing.** Until the mold is removed, the walls hold the pillars. After removal, only the nitride supports do. A thin wall at the support level weakens the lattice that holds 1.6 µm pillars upright.
3. **Dielectric coverage.** After mold removal, the space between pillars must take a conformal high-k film and a plate electrode. Where two pillars come close, the plate cannot fill the gap.

The bow budget (Chapter 10) and the placement budget (Section 1.4) are both, in the end, budgets on this wall.

---

## 1.3 Capacitance from the Hole

### 1.3.1 The Pillar Capacitor

In the reference process, the hole is filled with TiN to form a solid **pillar** bottom electrode. The mold oxide is then removed, leaving the pillars held by the nitride supports. The dielectric and the top plate are deposited around the pillars. Only the outside surface of the pillar is used. This is a single-sided capacitor.

```
Cross-section of one pillar capacitor after completion (schematic):

  ─────────┬──┬────────┬──┬──────── top support (SiN, 120 nm, with openings)
           │▓▓│        │▓▓│
     plate │▓▓│ plate  │▓▓│ plate     ▓ TiN pillar (shape of the hole)
     (TiN) │▓▓│        │▓▓│           │ high-k dielectric on the pillar
           │▓▓│        │▓▓│
  ─────────┼──┼────────┼──┼──────── middle support (SiN, 50 nm)
           │▓▓│        │▓▓│
           │▓▓│        │▓▓│
           │▓▓│        │▓▓│
  ═════════╧══╧════════╧══╧════════ bottom stop (SiN, 20 nm)
           [LP]        [LP]          W landing pads
```

Older generations used a **cylinder**: a thin TiN shell lining the hole, with both its inside and outside used. A cylinder gives nearly twice the area per hole, but its inside must have room for two dielectric layers and a plate. Below about 30 nm hole CD, there is no room, and the pillar takes over (Chapter 14).

### 1.3.2 Parallel-Plate Estimate

The dielectric is thin compared with the pillar radius (EOT 0.5 nm against a radius of 14 nm), so the cylindrical capacitor reduces to a parallel plate:

```
C_s = ε₀ · 3.9 · A / EOT
    ε₀ · 3.9 = 8.854×10⁻¹² × 3.9 = 3.453×10⁻¹¹ F/m

Pillar side area for a linear taper from CD_top to CD_bot:
  A = π · CD_avg · H,   CD_avg = (CD_top + CD_bot)/2

Reference (full sidewall):
  CD_avg = 28 nm, H = 1600 nm
  A = π × 28 × 1600 = 1.407×10⁵ nm² = 1.407×10⁻¹³ m²
  C_s = 3.453×10⁻¹¹ × 1.407×10⁻¹³ / 0.50×10⁻⁹ = 9.72×10⁻¹⁵ F = 9.7 fF
```

### 1.3.3 What the Supports and Stop Take Away

Not all of the pillar side faces the plate. The bottom stop covers the lowest 20 nm. The top and middle supports stay in place as perforated plates. Where a support touches a pillar, there is no dielectric and plate on that part of the pillar. The support openings expose about 30% of each pillar's perimeter at the support level (Chapter 2).

```
Effective height:
  H_eff = H − t_stop − 0.70 × (t_top + t_mid)
        = 1600 − 20 − 0.70 × (120 + 50) = 1461 nm

Effective capacitance:
  C_s = 9.72 fF × 1461/1600 = 8.88 fF  ≈ 8.9 fF   (reference)
```

### 1.3.4 Sensitivities

```
∂C/∂H      ≈ C_s / H_eff  = 8.9 / 1461 = 6.1×10⁻³ fF/nm   → 0.61 fF per 100 nm
∂C/∂CD_avg ≈ C_s / CD_avg = 8.9 / 28  = 0.32 fF/nm      → 3.6% per nm
∂C/∂EOT    ≈ −C_s / EOT   = −8.9 / 0.5 = −17.8 fF/nm    → −0.18 fF per 0.01 nm
```

These numbers drive the whole book. A hole that ends 50 nm short of the pad does not lose much capacitance (0.3 fF), but it is not connected and the cell is dead (Chapter 12). A hole whose average CD is 1 nm smaller loses 0.32 fF, about a third of the margin between the reference 8.9 fF and the 7.8 fF floor. A bow that raises the average CD gains capacitance but spends wall.

The fight for capacitance has three fronts: **taller molds** (etch), **wider holes** (etch and lithography, limited by the wall), and **thinner EOT** (dielectric). Dielectric progress has slowed as ZrO₂-based stacks approach their leakage limits. Much of the burden has therefore moved to the etch.

---

## 1.4 The Bottom of the Hole

### 1.4.1 The Landing Pad

The storage-node contact (BC) rises from the silicon between the bit lines. It is too narrow and in the wrong place to receive the capacitor directly, because the bit lines run on a rectangular grid and the capacitors on a hexagonal one. A **landing pad** of tungsten, patterned on top of the BC, shifts the contact point onto the hexagonal lattice.

```
Reference landing pad (illustrative):
  W, 26 nm wide at its top, ≈ 60 nm thick
  Pads on the same 45 nm hexagonal lattice as the holes
  Gap between neighbouring pads: 45 − 26 = 19 nm, filled with SiN
```

### 1.4.2 The Placement Budget

The hole bottom (24 nm) must overlap the pad (26 nm) enough for a low-resistance contact and must not come near the neighbouring pad.

```
Let Δ be the offset between the hole-bottom centre and the pad centre.

Contact overlap (1-D, along the worst direction):
  overlap = (w_hole + w_pad)/2 − |Δ|, capped at min(w_hole, w_pad)
          = 25 − |Δ|
  requirement: overlap ≥ 16 nm  →  |Δ| ≤ 9 nm

Clearance to the neighbouring pad (at 45 nm):
  neighbour pad edge at 45 − 13 = 32 nm; hole edge at Δ + 12 nm
  requirement: clearance ≥ 5 nm  →  Δ ≤ 15 nm   (less binding)

Bottom placement budget: |Δ| ≤ 9 nm (3σ)
```

```
Contributors (illustrative, 3σ):
  Hole-to-pad lithographic overlay                3.5 nm
  Pad placement and CD (from its own patterning)  3.0 nm
  Twisting (hole-to-hole random bending)          5.0 nm
  Tilting (systematic, after edge compensation)   3.0 nm
  RSS = √(3.5² + 3.0² + 5.0² + 3.0²) = √55.3 = 7.4 nm  ≤ 9 nm ✓
```

Two of the four contributors belong to the etch. Lithography sees the hole only at the top. It cannot correct a bottom that wanders after the top is printed. Chapter 11 develops the physics of twisting and tilting.

### 1.4.3 The Bottom CD

```
Bottom CD requirement: CD_bot ≥ 20 nm at the pad
  Contact area at 20 nm: (π/4)(20²) = 314 nm²
  TiN/W interface resistivity (illustrative) 1×10⁻⁸ Ω·cm² = 1×10⁶ Ω·nm²
  → interface resistance 1×10⁶ / 314 = 3.2 kΩ
  Access-path budget for the cell (transistor + contacts) ≈ 15–20 kΩ
```

A hole that narrows to 15 nm at the bottom raises the interface term to 5.7 kΩ. A hole that closes is open-circuit. The taper of the hole is not just a capacitance loss. It is a contact problem at the bottom (Chapter 12).

---

## 1.5 Where the Hole Etch Sits in the Flow

```
Capacitor module (simplified):

  ... bit line, storage-node contact, landing pad (W), pad isolation (SiN)
   1. Mold deposition: bottom SiN stop, lower oxide (BPSG), middle SiN,
      upper oxide (TEOS), top SiN
   2. Hard mask: amorphous carbon (ACL) 1.4 µm, SiON 40 nm
   3. Honeycomb patterning (EUV, or double SADP at 60°) → resist/spacer mask
   4. SiON open and ACL mask open (Carbon Hard Mask Etch)
 ► 5. CAPACITOR HOLE ETCH: top SiN → upper oxide → middle SiN → lower oxide
      → bottom SiN → land on W pad
   6. Ash (remaining ACL), wet clean
   7. Bottom electrode: TiN fill (CVD/ALD) → etchback/CMP to the top support
   8. Support opening: pattern and etch openings in the top (and middle)
      SiN supports
   9. Mold removal: HF-based wet etch through the openings (oxide gone,
      SiN supports remain)
  10. High-k dielectric (ZrO₂/Al₂O₃/ZrO₂, ALD), top electrode (TiN + SiGe/W)
```

The hole etch is the longest single etch in the DRAM flow and, together with the mask open, one of the most expensive.

---

## 1.6 The Specification Sheet

```
Capacitor hole etch specification (reference, illustrative)

Geometry
  Top CD (at top-support top)              32.0 ± 1.5 nm
  Maximum bow CD (anywhere)                ≤ 34 nm (wall ≥ 11 nm)
  Bottom CD (at pad)                       24 ± 2 nm; ≥ 20 nm every hole
  Depth                                    through bottom stop, on W
  Pad gouge                                ≤ 10 nm into W
  Circularity (min/max diameter, top)      ≥ 0.90
  Striation (LER of hole edge, 3σ)         ≤ 2.0 nm

Placement
  Bottom placement vs. top (3σ, twist+tilt) ≤ 6 nm within die; edge tilt ≤ 0.1°

Defects
  Not-open holes                           ≤ 1×10⁻⁸ per hole (≈ 170 per die)
  Bridged neighbours                       ≤ 1×10⁻⁹ per pair
  Particles adders (≥ 40 nm)               ≤ 10 per wafer

Mask
  Remaining ACL after etch                 ≥ 500 nm, no breakthrough

Uniformity
  Bottom CD range, center to 3 mm edge     ≤ 2.0 nm
  Bow CD range, center to 3 mm edge        ≤ 1.5 nm

Productivity
  Etch time                                ≈ 5.1 min; ≥ 7 wafers/h per chamber
```

The not-open specification follows from repair. A 16 Gb die carries enough redundant rows and columns to repair a few thousand failing bits. Not-open holes should take only a small part of that, because retention, dielectric leakage, and other mechanisms need the rest.

---

## Summary and Key Takeaways

1. **The capacitance target hardly changes.** About 8–10 fF per cell is needed for a 90–100 mV bit-line signal. The reference cell holds 8.9 fF.

2. **The holes fill half the array.** On a 45 nm hexagonal pitch with a 32 nm top CD, the wall between holes is 13 nm thick at the top.

3. **Depth and diameter are capacitance.** 100 nm of depth buys about 0.6 fF. 1 nm of average CD buys about 0.3 fF.

4. **The bottom has a placement budget.** The hole must land within 9 nm of the pad centre. Etch twisting and tilting take two of the four terms.

5. **The bottom CD is a contact.** Below about 20 nm, interface resistance climbs quickly. A closed hole is a dead cell.

---

## Study Questions

1. A product uses C_BL = 32 fF and V_DD = 1.05 V. What C_s gives a 95 mV signal? How much mold height does that save compared with the reference, at the same CD profile?

2. A future cell has F = 15 nm in a 6F² layout. Compute the hexagonal pitch, and the top wall thickness if the top CD scales with the pitch.

3. A hole has CD_top = 33 nm and CD_bot = 21 nm. Compute C_s with the reference H and EOT and the support correction of Section 1.3.3. Compare with the reference.

4. A process change thins the top support to 80 nm and adds the 40 nm to the upper oxide. Compute the change in H_eff and C_s.

5. If the pad is enlarged to 28 nm, recompute the bottom placement budget. Which constraint now binds?

6. Twisting grows from 5 to 7 nm (3σ). With the other contributors fixed, does the placement budget still close? How much must overlay improve to recover it?

---

**Next Chapter:** [Chapter 2: The Mold Stack, Support Layers & Hard Mask](./02-mold-stack-hard-mask.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
