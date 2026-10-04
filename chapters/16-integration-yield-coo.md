# Chapter 16: Post-Etch Integration, Yield & Cost of Ownership

## Overview

The hole etch ends on the landing pad, but the hole's story does not. The remaining mask must be stripped and the polymer cleaned without widening the hole or oxidizing the pad. The hole is filled with TiN, the fill is planarized, the supports are opened, and the mold is dissolved away, leaving seventeen billion pillars standing on their pads. Each of these steps is a customer of the etch: it inherits the hole's profile, its bottom, its residues, and its defects, and some of them amplify what the etch left. In the end, the capacitor module's yield is counted in failing bits, and its cost is counted in dollars per wafer against the value of the yield it protects.

This chapter follows the hole through strip, clean, electrode fill, support opening, and mold removal, catalogues the defect modes and their yield signatures, and builds a cost-of-ownership model for the capacitor hole etch.

**Learning Objectives:**
- Describe the strip and clean after the hole etch and their effect on CD and the pad
- Explain how the hole profile affects TiN fill, seams, and pillar shape
- Describe support opening and mold removal and the failure modes they reveal
- Map defect modes to yield signatures in the bit map
- Build a cost-of-ownership model for the capacitor hole etch and compare it with the value of yield

---

## 16.1 Strip and Clean

### 16.1.1 Ashing the Mask

```
Remaining ACL ≈ 730 nm (Chapter 2)
O₂ (or O₂/N₂/H₂) downstream or low-bias ash, ≈ 1.5 µm/min at 250 °C
  ash time ≈ 30 s + 50% overash ≈ 45 s
```

The ash also removes the sidewall polymer and the fluorocarbon film on the pad. It oxidizes the W pad surface slightly. Hydrogen-containing ash chemistries reduce W oxidation.

### 16.1.2 Wet Clean

```
Wet clean goals:
  Remove fluorinated residues, B/P-fluoride crystals, WOₓFᵧ on the pad
  Do not widen the hole: oxide loss ≤ 0.5 nm per side
  Do not attack W: W loss ≤ 1 nm

Typical: dilute fluoride-containing organic or semi-aqueous clean;
  very dilute HF only with tight time control
```

Every nanometre of oxide removed per side in the clean costs a nanometre of wall on each side of the wall: 2 nm of wall for 1 nm per side. The clean is therefore part of the bow budget.

### 16.1.3 Queue Time

```
Queue limits (illustrative):
  Etch → ash: ≤ 4 h (fluorinated residues absorb moisture; BPSG-derived
              B/P fluorides crystallize into defects)
  Clean → TiN deposition: ≤ 4 h (W pad oxide regrowth)
```

---

## 16.2 Electrode Fill

### 16.2.1 TiN Fill and the Profile

TiN is deposited by CVD or ALD from TiCl₄ and NH₃. It grows inward from the walls and closes in the middle, leaving a seam along the axis.

```
Fill sensitivity to profile:
  Re-entrant neck (neck narrower than the bow): the neck closes first and
    traps a void at the bow depth
  Reference neck 30.0 nm vs bow 33.5 nm: the neck is removed by the strip
    and clean to ≈ 32 nm; residual re-entrance ≈ 0.75 nm per side
  TiN conformality ≥ 95% → the bow is filled before the top closes if
    re-entrance ≤ ≈ 1 nm per side
```

A void in a pillar is not fatal by itself, because only the outside surface is used. But a void open to the top after planarization traps chemicals in later steps, and a void at the support level weakens the pillar.

### 16.2.2 Planarization

The TiN overburden on the top support is removed by etchback or CMP. The top of each pillar becomes the top of the capacitor. A top CD 1 nm larger than target gives a pillar top 1 nm larger; a hole with a striated top gives a pillar with a ridged top.

---

## 16.3 Support Opening and Mold Removal

### 16.3.1 Support Opening

Openings are patterned and etched through the top support, and, in a deeper etch, the middle support. Their placement relative to the pillars sets how much of each pillar's support web is removed (Chapter 1). Openings that are misplaced remove too much web from some pillars and leave them weakly held.

### 16.3.2 Mold Removal

```
Wet removal (illustrative):
  HF-based solution through the support openings
  TEOS and BPSG removed; SiN supports and stop remain; TiN unaffected
  Drying: IPA or supercritical/low-surface-tension methods to reduce
    capillary forces on the pillars
```

### 16.3.3 What Mold Removal Reveals

The hole etch's errors become visible when the mold is gone:

```
Etch error                    Revealed after mold removal as
──────────────────────────────────────────────────────────────────────────
Bridged holes (bow, twist)    two pillars joined by TiN where the wall
                              broke → bit pairs shorted
Thin walls (not broken)       pillars that touch after drying (leaning)
Twisted holes                 pillars leaning or bent; reduced spacing to
                              neighbours → plate cannot fill; local leakage
Notches below supports        pillar necked at the support → mechanical
                              weakness
Side punch beside the pad     TiN finger toward the bit line → BL–SN
                              leakage or short
```

---

## 16.4 Defect Modes and Yield Signatures

```
Defect mode                        Bit-map signature              Etch cause (Chapter)
──────────────────────────────────────────────────────────────────────────────────────
Not-open hole                      single bit, fails "0" and "1"  bottom stop, mask
                                   in all patterns                defect, particle (12, 9)
Unlanded hole (severe twist)       single bit, as not-open, or    twisting (11)
                                   weak (high resistance)
Bridged pillars                    bit pairs along the six        bow, twist, oval (10,
                                   neighbour directions           11, 13)
Low capacitance                    retention-weak bits, regional  depth, CD, mold (1, 3)
                                   (radial, chamber)
Side punch / BL–SN leakage         bit-line failures, column      BO overetch, offset (12)
                                   patterns
Particle clusters                  clusters of failing bits       chamber parts (9)
                                   (dozens)
Edge tilt                          edge-die weak/unlanded bits    ring, mask open (8, 11)
```

### 16.4.1 Repair Budget

```
Illustrative 16 Gb die repair budget: ≈ 4000 repairable failing bits
(rows/columns plus ECC margin, product-dependent)
  Not-open allocation (≈ 1×10⁻⁸): ≈ 170 bits
  Bridging allocation (≈ 1×10⁻⁹ per pair × 3 pairs per hole): ≈ 50 pairs →
    ≈ 100 bits
  Other capacitor-module mechanisms: ≈ 300 bits
  Retention, transistor, and other modules: the remainder
```

A chamber whose not-open rate rises tenfold, to 1×10⁻⁷, consumes 1700 repairs per die on that mechanism alone, and dies with clustered failures exhaust their local redundancy first. Yield loss from the capacitor hole is therefore often sudden: a small increase in a tail rate pushes a fraction of dies past their repair limit.

---

## 16.5 Cost of Ownership

### 16.5.1 Cost per Wafer

```
Reference fleet (Chapter 5): 20 chambers for 100,000 wafers/month
  = 1.2 million wafer passes per year

Capital (illustrative):
  ≈ $3.0M per chamber-equivalent (high-power dielectric etch on a 4-chamber
  platform, including share of platform and facilities)
  20 × $3.0M = $60M, depreciated over 5 years → $12M/year
  Per wafer: $12M / 1.2M = $10.0

Consumables (per wafer; RF time per wafer 305 s = 0.085 h):
  Upper electrode: $15,000 per 500 RF h → $30/RF h → $2.5
  Focus ring set:  $6,000 per 300 RF h  → $20/RF h → $1.7
  Confinement rings, edge parts: ≈ $1.0
  Chuck: $150,000 per 3000 RF h → $50/RF h → $4.2
  Subtotal: ≈ $9.4

Gases (C₄F₆ is costly), power, cooling, abatement: ≈ $2.5
Maintenance labour, qualification wafers, metrology share: ≈ $3.5

Total: ≈ $25 per wafer
```

### 16.5.2 What Moves the Cost

```
Sensitivities (illustrative):
  +10% etch time (30 s; cycle 410 → 440 s):  +$0.7 depreciation,
                                              +$0.9 consumables
  Skip WAC (60 s → 0): −15% cycle time → −$1.5 depreciation, but drift
                       (Chapter 9)
  Cryogenic etch (Chapter 14): −50% etch time, but higher capital and chiller
                       cost; roughly neutral to −15% in this model
  Electrode life +20%: −$0.4
```

### 16.5.3 The Value of Yield

```
Illustrative DRAM wafer output value: ≈ $5,000 per wafer (product- and
market-dependent)
  0.1% yield = $5 per wafer
  1% yield   = $50 per wafer, twice the entire etch cost
```

The cost of the capacitor hole etch is about half a percent of the wafer's value. Its yield impact can be several percent. Recipe choices that cost etch time, consumables, or throughput but cut the not-open or bridging tail by a factor of two almost always pay. The economic logic of the capacitor hole, like its physics, is dominated by the tail.

---

## Summary and Key Takeaways

1. **Strip and clean are part of the profile.** Each nanometre per side of oxide lost in the clean costs 2 nm of wall.

2. **The neck can trap a void.** Re-entrance above about 1 nm per side risks a void at the bow depth during TiN fill.

3. **Mold removal reveals the etch.** Bridged, leaning, notched, and side-punched pillars all trace back to the hole.

4. **The bit map separates the mechanisms.** Single bits, pairs along neighbour directions, clusters, columns, and edge dies each point to a different cause.

5. **The etch costs about $25 per wafer.** Capital is about $10, consumables about $9, the rest gases, power, and labour.

6. **Yield dwarfs cost.** 1% of yield is worth about twice the whole etch cost. Tail rates, not mean profiles, decide the economics.

---

## Study Questions

1. The wet clean removes 0.8 nm of oxide per side. What is the new wall at the bow (reference bow 33.5 nm)? How much must the bow shrink to restore it?

2. A process change removes the neck re-entrance entirely but raises the bow by 0.5 nm. Is this a good trade for the TiN fill? For bridging?

3. Recompute the cost per wafer if the etch time rises to 360 s (taller mold) and electrode life falls to 400 RF h.

4. A chamber's not-open rate rises to 5×10⁻⁸ for one week. If 20% of the fab's wafers pass through it and dies with more than 4000 failing bits are lost, estimate the yield impact, assuming the other mechanisms consume 3200 repairs per die on average with σ = 300.

5. A cryogenic etch upgrade costs $1M per chamber more and halves etch time. Using Section 16.5, how many chambers can the fab retire, and what is the net change in cost per wafer?

---

**Return to:** [INDEX](../INDEX.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
