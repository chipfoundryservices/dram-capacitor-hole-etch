# Chapter 12: Not-Open Holes, the Bottom Etch Stop & Landing-Pad Interface

## Overview

The capacitor hole is useful only if it reaches the landing pad. A hole that stops in the lower oxide, in the bottom nitride, or on a film of polymer above the pad leaves its pillar floating. The cell cannot be written or read. Such **not-open** holes are rare, a few per billion in a good process, but there are seventeen billion holes on a die. The last 300 nm of the hole, where the rate is slowest, the bottom narrowest, and the charge highest, decides the not-open rate. Once the hole is open, the bottom must touch tungsten without driving into it, and without punching down beside the pad.

This chapter covers how holes stop, how the bottom CD narrows, how the bottom stop is opened and the pad landed, the side-punch risk beside the pad, the not-open budget and its contributors, and how not-open holes are found.

**Learning Objectives:**
- Explain the mechanisms that stop a hole before it reaches the pad
- Relate the taper angle to the bottom CD and compute its sensitivity to polymer
- Model the nitride remaining in each hole after the main etch and the gouge after the bottom-open step
- Estimate side-punch depth into the pad-isolation nitride for offset holes
- Build a not-open budget from its contributors and compare with the specification
- Describe voltage-contrast inspection for not-open and bridged holes

---

## 12.1 How Holes Stop

### 12.1.1 Polymer Etch Stop

At the bottom of a deep hole, the ion flux has fallen more slowly than the flux of polymer-forming neutrals in some regimes and faster in others. Where the ion-to-polymer ratio drops below what is needed to keep the fluorocarbon film thin, the film thickens. A thicker film absorbs more of the ion energy (Chapter 4: ER ∝ exp(−t_fc/λ_E)), the rate falls, and the film thickens further. The hole stops.

```
Bottom film and rate (illustrative, λ_E = 1.5 nm):
  t_fc (nm)    rate / rate(t_fc = 0.8)
  ───────────────────────────────────
  0.8          1.00
  1.5          0.63
  2.5          0.32
  4.0          0.12   → effectively stopped on a 30 s scale
```

The transition from etching to stopped is sharp, because the feedback is positive. A hole that is slightly narrower, slightly more charged, or slightly richer in polymer than its neighbours can cross it while they do not.

### 12.1.2 Taper Closure

A hole that tapers continuously narrows to zero at some depth:

```
Bottom CD after a tapered segment of length L at angle α (from vertical):
  CD_bot = CD_start − 2 L tan α

Reference lower segment: CD 30 nm at 820 nm depth → 24 nm at 1600 nm
  α = arctan(3 / 780) = 0.22°

If polymer raises α by 20% (to 0.264°):
  CD_bot = 30 − 2 × 780 × tan(0.264°) = 30 − 7.2 = 22.8 nm

Taper that would close the hole at 1600 nm: tan α = 30 / (2 × 780) →
  α = 1.10°
```

Taper closure across the whole wafer would need a gross recipe error. For single holes, it combines with the polymer stop: a hole whose bottom narrows below about 15 nm passes fewer ions, collects polymer faster, and is at risk.

### 12.1.3 Charging Retardation

The positive bottom charge (Chapter 3) slows the low-energy ions and reflects some of them. It does not stop the keV ions. But it deflects them toward the walls, which narrows the effective etch area at the bottom and favours polymer. Charging and polymer stop together.

### 12.1.4 Blocked Holes

A hole that never started (missing in the mask, scummed in the mask open) or that was covered by a particle (Chapter 9) is not-open from the beginning. These are **extrinsic** not-opens: they do not depend on the etch at the bottom at all.

---

## 12.2 The Bottom CD

### 12.2.1 Requirement

```
Bottom CD ≥ 20 nm on every hole (Chapter 1): contact area and resistance
Reference mean 24 nm; hole-to-hole σ ≈ 1.0 nm
Margin to 20 nm: 4σ
```

The 4σ margin seems small for 1.7×10¹⁰ holes. As with the placement budget, the 20 nm limit is soft: a hole with an 18 nm bottom has 81% of the reference contact area and works. A bottom below about 12 nm becomes a reliability concern, and a hole whose bottom closes is open-circuit.

### 12.2.2 Knobs

```
Bottom-CD sensitivities (illustrative, ME2):
  O₂ +5 sccm                   +0.8 nm
  NF₃ +3 sccm (late)           +0.5 nm
  Pressure −3 mTorr            +0.3 nm
  Bias pulsing (last 60 s)     +0.4 nm
  Wafer T +3 °C                +0.2 nm
  Overetch +10 s               +0.3 nm (the bottom widens on the stop)
```

The bottom widens during overetch because the etch front, held on the nitride stop, continues to etch the lower sidewall slowly. Overetch is the cheapest bottom-CD knob, but it costs mask, nitride, and pad.

---

## 12.3 The Bottom Stop and the Pad

### 12.3.1 Nitride Remaining After the Main Etch

The holes do not reach the stop at the same time. The first to arrive (wide holes, fast zones) sit on the nitride for the longest part of the overetch. The last (narrow holes, the CD tail) arrive near the end.

```
Main-etch overetch: 29 s; nitride rate at the hole bottom in ME2 ≈ 36 nm/min
(oxide bottom rate 290 nm/min near the stop / selectivity 8)

  Hole           arrives before end   nitride consumed   nitride remaining
  ──────────────────────────────────────────────────────────────────────
  First (wide)   29 s                 17.5 nm             2.5 nm
  Median         ≈ 20 s               12 nm               8 nm
  Last (3σ narrow, slow zone) ≈ 0 s   0 nm                20 nm
```

### 12.3.2 Opening the Stop and Landing

```
BO step (Chapter 7): 30 s; SiN 60 nm/min, W 15 nm/min at the hole bottom

  Hole      nitride left   time to clear   time on W   W gouge
  ─────────────────────────────────────────────────────────────
  First     2.5 nm         2.5 s           27.5 s      6.9 nm
  Median    8 nm           8 s             22 s        5.5 nm
  Last      20 nm          20 s            10 s        2.5 nm

Spec: gouge ≤ 10 nm ✓; every hole cleared with ≥ 10 s margin ✓
```

The BO step must be long enough to clear the thickest remaining nitride with margin, and short enough that the earliest holes do not gouge the pad too deeply. The 4:1 nitride:W selectivity sets how much margin is available. A more W-protective chemistry would allow a longer BO step, at the risk of polymer on the W surface.

### 12.3.3 Side Punch Beside the Pad

A hole offset from its pad (Chapter 11) puts part of its bottom over the SiN that isolates the pads from each other. The BO step etches that SiN at 60 nm/min, while the W beside it etches at only 15 nm/min. The hole then punches down beside the pad.

```
Side-punch depth into pad-isolation SiN for the first-arriving holes:
  27.5 s × 60 nm/min = 27.5 nm below the pad top

Below the pad-isolation SiN: the bit-line cap and spacer, ≈ 40 nm below
the pad top (illustrative)
Margin: 40 − 27.5 = 12.5 nm
```

Side punch matters because the electrode will fill it. A TiN finger reaching down beside the pad toward the bit line reduces the bit-line-to-storage-node spacing and raises coupling and leakage. In the worst case it shorts the cell to the bit line. Side punch is the reason the BO chemistry is chosen with nitride:W selectivity of only about 4, not higher: a much more aggressive nitride etch would clear the stop faster but punch deeper beside offset holes.

### 12.3.4 The Pad Surface

```
After BO, the W pad surface carries (illustrative):
  WOₓFᵧ, 1–2 nm, from fluorine and oxygen in the BO plasma
  Fluorocarbon film, ≈ 1 nm
  Air exposure before the wet clean grows the oxide further
```

These layers raise contact resistance. The post-etch ash removes carbon. A dilute wet clean removes the oxyfluoride, and a queue-time limit between etch and electrode deposition keeps the oxide from regrowing (Chapter 16).

---

## 12.4 The Not-Open Budget

### 12.4.1 Contributors

```
Not-open budget (illustrative, per hole; spec ≤ 1×10⁻⁸):

  Contributor                                   Rate          Notes
  ──────────────────────────────────────────────────────────────────────────
  Incoming mask defects (missing, scummed,      3×10⁻⁹        litho, mask open
  bridged mask holes)
  Particles on the mask before or during etch   0.5×10⁻⁹      Chapter 9
  Local polymer/charging stop in the last       2×10⁻⁹        stochastic; rises
  300 nm                                                     with Π and electrode age
  CD-tail under-etch (narrowest holes in slow   1×10⁻⁹        overetch margin
  zones)
  Incomplete BO (residue, thick local nitride)  1×10⁻⁹
  Severely twisted holes (no contact)           0.5×10⁻⁹      Chapter 11
  ──────────────────────────────────────────────────────────────────────────
  Total                                         8×10⁻⁹       ≈ 140 per die
```

### 12.4.2 What the Etch Controls

Only part of the budget belongs to the bottom etch: the polymer and charging stop, the CD-tail under-etch, and the incomplete BO, about 4×10⁻⁹. The rest comes from incoming defects and particles. Etch changes aimed at not-opens should be judged against the part they can move.

```
Response of the etch-controlled part to common changes (illustrative):
  O₂ +5 sccm in ME2:            ÷3
  Bias pulsing in the last 60 s:  ÷2
  DC superposition:              ÷3–5
  Overetch +10 s:                ÷2 (cost: +2.5 nm W gouge, +10 nm side punch,
                                       +17 nm ACL)
  Electrode at 400 RF h vs. new: ×2.5 (Chapter 9)
```

---

## 12.5 Finding Not-Open Holes

### 12.5.1 Voltage-Contrast Inspection

An electron beam scanning the wafer charges each hole bottom. A hole that reaches the W pad is connected through the pad and the storage-node contact to the silicon, and drains its charge. A hole that stops on oxide or nitride stays charged. The two appear with different brightness in the secondary-electron image.

```
Voltage contrast (VC) inspection (illustrative):
  After BO and clean: holes open to W → bright (grounded, positive mode)
                      not-open → dark
  After TiN fill and CMP: open pillars → grounded; floating pillars → dark;
                      bridged pillars → pairs with linked contrast
  Throughput: a few dies per wafer at ≈ 10⁸ holes per hour
```

At 10⁸ holes per hour, inspecting a whole 16 Gb die takes about 170 hours. VC inspection therefore samples. To estimate a rate near 10⁻⁸ per hole with useful precision, it needs on the order of 10⁹ holes inspected, a few dies' worth of area, accumulated over many wafers.

### 12.5.2 Electrical Test

The final measure is the bit map from wafer test. Not-open cells appear as single-bit failures that fail both "0" and "1" in every pattern. Their density, map, and clustering separate the contributors: particles and mask defects cluster, the polymer stop follows the wafer's radial profile and the chamber's electrode age, and CD-tail under-etch follows the patterning families.

---

## Summary and Key Takeaways

1. **Holes stop by positive feedback.** A thicker bottom film lowers the rate, which thickens the film further. The transition is sharp.

2. **Taper is a slow way to close.** The reference lower taper is 0.22°. It would take about 1.1° to close the hole at full depth, but a narrow bottom raises the risk of a polymer stop.

3. **The holes reach the stop at different times.** After the main overetch, 2.5–20 nm of nitride remains. The BO step clears all of it and gouges the W by 2.5–7 nm.

4. **Offset holes punch down beside the pad.** About 27 nm into the pad isolation for the earliest holes, with about 12 nm of margin to the bit line.

5. **Half of the not-open budget is extrinsic.** Mask defects and particles take about half. The etch controls the rest through O₂, pulsing, DC superposition, overetch, and electrode age.

6. **Voltage contrast finds them.** Open holes drain to the pad; not-open holes stay charged. Inspecting enough holes to measure 10⁻⁸ takes many dies.

---

## Study Questions

1. Using ER ∝ exp(−t_fc/λ_E) with λ_E = 1.5 nm, how thick must the bottom film become for the rate to fall to 5% of its value at 0.8 nm?

2. The lower taper rises to 0.30°. Compute the bottom CD with the reference CD of 30 nm at 820 nm depth. How much O₂ (using Section 12.2.2) is needed to restore 24 nm?

3. The BO step is lengthened to 40 s. Recompute the W gouge for the first-arriving holes and the side-punch depth. Do both still meet their limits?

4. A new BO chemistry has SiN at 50 nm/min and W at 8 nm/min. Design a BO time that clears 20 nm of nitride with 10 s margin and compute the gouge and side punch for a hole with 2.5 nm of nitride remaining.

5. The polymer-stop contribution doubles as the upper electrode ages. What O₂ offset (using the response table) brings the etch-controlled part back to its new-electrode value?

6. How many holes must a VC tool inspect to observe, on average, 10 not-open holes at a rate of 8×10⁻⁹? At 10⁸ holes per hour, how long does this take?

---

**Next Chapter:** [Chapter 13: Charging, Mask Integrity, Striation & Hole Distortion](./13-charging-mask-striation.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
