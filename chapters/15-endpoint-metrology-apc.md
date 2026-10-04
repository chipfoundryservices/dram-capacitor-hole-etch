# Chapter 15: Endpoint, Metrology & Advanced Process Control

## Overview

The capacitor hole etch is controlled mostly by time. The holes reach each interface at different moments, spread by their CD, by the wafer's radial profile, and by the falling rate at depth, so optical emission sees transitions only as slow, smeared changes. Most of what matters about the hole (its bow, its bottom, its placement, whether it is open) cannot be seen from the plasma at all. It must be measured after the etch, on a sample of holes, by methods that look through 1.6 µm of oxide. Production control therefore combines a time-based recipe, an endpoint signal used mainly as a check, a metrology plan that samples the profile and the tail, and APC that adjusts each wafer from what came in and what the previous wafers showed.

This chapter covers endpoint signals for the capacitor hole, the metrology of profile, placement, and opens, electrical monitors, and the feed-forward and feedback loops that hold the hole on target across a fleet.

**Learning Objectives:**
- Identify the OES signals available during each step and what they can and cannot detect
- Choose metrology for top CD, bow, bottom CD, placement, and not-open rate
- Explain what electrical monitors reveal about the capacitor hole
- Design a feed-forward correction from incoming mask CD and mold thickness
- Design feedback and consumable-age corrections for a chamber fleet

---

## 15.1 Endpoint

### 15.1.1 Signals

```
OES lines used during the capacitor hole etch (illustrative):
  CN       387 nm   nitride being etched (supports, stop)
  N₂       337 nm   nitride (weaker)
  CO       483 nm   oxide being etched (O from the oxide + carbon)
  SiF      440 nm   silicon-containing film being etched
  F        704 nm   fluorine (actinometry vs Ar 750 nm)
  H        656 nm   hydrogen-containing steps
  B, P     various  BPSG etch products (weak)
```

### 15.1.2 Support Transitions

When the etch front enters the top support, CN rises; when it leaves, CN falls and CO rises. At the top support the holes are shallow and enter together, so the transition is sharp enough to call SN1's end. At the middle support, the holes are at an aspect ratio near 28 and arrive over several seconds. The CN signal rises and falls over 5–10 s. The SN2 step time is set by the ARDE model (Chapter 7) and the CN trace is used to confirm that the support has been reached and cleared.

### 15.1.3 Arrival at the Stop

As the holes reach the bottom stop, the oxide removal rate across the wafer falls and the CO signal falls with it. The fall is spread over 20–30 s by the spread of arrival times. A **knee** in the CO signal marks the median arrival:

```
CO/Ar trace in ME2 (schematic):
  ───────────────╮
                 ╰──╮           knee: median arrival (≈ 20 s before ME2 end)
                    ╰────────   floor: most holes on the stop
```

The knee is used as a **monitor**: a knee earlier or later than expected flags a change in rate, mold thickness, or mask CD. Some fabs set the overetch as a fixed time after the knee, which absorbs wafer-to-wafer rate changes but not hole-to-hole variation.

### 15.1.4 Bottom Open

The BO step's CN signal falls as the stop clears. Because the remaining nitride varies from 2.5 to 20 nm across holes (Chapter 12), the fall is gradual. The BO time is fixed; the CN decay confirms clearing.

---

## 15.2 Profile Metrology

### 15.2.1 Methods

```
Method                 Measures                         Sample           Notes
───────────────────────────────────────────────────────────────────────────────────────
CD-SEM (top-down)      top CD, circularity, striation   many sites,      top only
                                                         per wafer
HV-SEM (10–30 kV)      top and bottom CD, bottom        many sites       bottom CD and
                       placement (twist, tilt)                           placement through
                                                                          the mold
OCD (spectroscopic     average profile: top, bow,       many sites       model-dependent;
  ellipsometry,        mid, bottom CDs, depth           per wafer        weak at the bottom
  reflectometry)                                                         of 57:1 holes
CD-SAXS (transmission  average profile and tilt with    few sites        slow; very good for
  X-ray scattering)    sub-nm precision                                  bow and tilt
FIB-SEM / TEM          full profile, interfaces,        few holes,       destructive; the
  cross-section        notches, gouge, side punch       few wafers       reference for all
                                                                          others
```

### 15.2.2 Measuring the Bow

The bow sits 350 nm below the top, behind the neck. Top-down SEM cannot see it. OCD can, through a model of the profile, but the model must be calibrated against cross-sections, and its accuracy degrades when the shape departs from the model's assumptions. CD-SAXS fits the profile with fewer assumptions and is often the reference for OCD calibration.

```
Bow metrology plan (illustrative):
  OCD: 13 sites per wafer, 1 wafer per lot per chamber
  CD-SAXS: 5 sites, 1 wafer per chamber per day (OCD calibration)
  Cross-section: 1 wafer per chamber per week + after every PM
```

### 15.2.3 Measuring the Bottom and Placement

HV-SEM is the workhorse. Its backscattered-electron image shows the hole bottom against the W pad with good contrast. It measures the bottom CD and the offset of each bottom from its top for thousands of holes per site, giving the twist σ, the regional tilt, and a direct count of severe outliers.

---

## 15.3 Opens, Bridges, and Electrical Monitors

### 15.3.1 Voltage-Contrast Inspection

Chapter 12 described VC inspection. It runs after BO and clean (open/not-open) and after electrode fill (open, bridged). Its sample size limits it to rates above about 10⁻⁹ per hole with useful statistics on a weekly basis.

### 15.3.2 Electrical Test Structures

```
Scribe-line and in-die structures (illustrative):
  Capacitor arrays (10⁴–10⁶ cells in parallel): total capacitance →
    average C_s; tracks average CD and depth
  Comb structures between adjacent capacitor rows: leakage → bridging
  Chains of capacitors through pads (after a special connection level):
    resistance → contact quality, not-open density
  Bit-line-to-storage-node leakage: side punch (Chapter 12)
```

### 15.3.3 Bit Maps

The final test is the bit map. Not-open, bridged, and low-capacitance cells have distinct signatures: hard single-bit fails, paired fails, and pattern-sensitive weak cells. Their maps by wafer, chamber, and electrode age close the loop to the etch.

---

## 15.4 Advanced Process Control

### 15.4.1 Feed-Forward from Incoming Data

```
Inputs measured before the etch, per wafer or lot:
  ACL bottom CD (mask-open metrology), family means if SADP
  Mold thickness (film metrology on monitor or product)
  ACL thickness after open

Outputs adjusted:
  ME2 overetch time; ME2 O₂ offset
```

```
Example: a lot arrives with mask CD 0.6 nm below target and a lower oxide
12 nm thicker than target.

Depth deficit at the reference time from CD: 15.2 × 0.6 = 9.1 nm
Extra depth from thickness:                   12 nm
Total extra depth at the bottom rate (≈ 330 nm/min in BPSG at depth):
  (9.1 + 12) / 330 × 60 = 3.8 s  → ME2 +4 s

Bottom CD from the smaller mask CD: −0.6 × (24/31) ≈ −0.46 nm
  O₂ correction at +0.16 nm per sccm (Chapter 4): +2.9 sccm → +3 sccm
```

### 15.4.2 Feedback from Post-Etch Metrology

```
Feedback (EWMA per chamber and product):
  e_k = (measured − target) for bottom CD and bow
  offset_{k+1} = offset_k − λ G⁻¹ e_k,  λ = 0.3

Sensitivity matrix G (bottom CD, bow) per (O₂ sccm, wafer T °C), from
Chapters 4 and 8:
  G = [ 0.16   0.07 ]
      [ 0.10   0.13 ]

Example: bottom CD −0.4 nm, bow +0.3 nm from target.
  det G = 0.16 × 0.13 − 0.07 × 0.10 = 0.0208 − 0.0070 = 0.0138
  G⁻¹ = (1/0.0138) [ 0.13  −0.07 ]
                   [ −0.10  0.16 ]
  G⁻¹ e = (1/0.0138) [ 0.13 × (−0.4) − 0.07 × 0.3 ]  = (1/0.0138) [ −0.073 ]
                     [ −0.10 × (−0.4) + 0.16 × 0.3 ]              [ 0.088 ]
        = [ −5.29 ] , [ 6.38 ]
  Full correction: −G⁻¹ e → O₂ +5.3 sccm, T −6.4 °C
  With λ = 0.3: O₂ +1.6 sccm, T −1.9 °C this lot
```

The matrix is well conditioned only because O₂ moves the bottom more than the bow, and temperature the bow more than the bottom. If the two columns become nearly parallel (for example at a different operating point), the inverse amplifies noise. APC systems check the condition number and limit step sizes.

### 15.4.3 Consumable-Age Corrections

```
Scheduled offsets (illustrative):
  O₂ in ME1/ME2: +1.5 sccm per 100 upper-electrode RF hours (Chapter 9)
  Ring lift: +25 µm per ≈ 8 RF hours of ring erosion (Chapter 8)
  Edge zone temperature: small offsets with ring age
Reset at each consumable change; first post-PM wafers measured before
release
```

### 15.4.4 Fleet Matching

Each chamber carries constants for rate, bottom CD, bow, and edge tilt, learned from its own metrology. New chambers or chambers after major PM start with fleet-median constants and converge within a few lots. A chamber whose constants drift outside a band is held for engineering review rather than corrected indefinitely.

---

## Summary and Key Takeaways

1. **Endpoint is a check, not a call.** Support transitions and arrival at the stop are smeared over seconds. Step times come from the ARDE model; OES confirms them.

2. **No single metrology sees the whole hole.** CD-SEM sees the top, HV-SEM the bottom and placement, OCD and CD-SAXS the average profile, cross-sections the truth.

3. **Opens and bridges need large samples.** VC inspection and electrical structures measure rates near 10⁻⁹ only over many dies.

4. **Feed-forward handles incoming variation.** A 0.6 nm smaller mask CD and a 12 nm thicker mold need about +4 s of ME2 and +3 sccm of O₂.

5. **Feedback uses a 2×2 matrix.** O₂ steers the bottom; temperature steers the bow. The matrix must stay well conditioned.

6. **Consumables are scheduled into the recipe.** Electrode age and ring wear carry their own offsets, reset at each change.

---

## Study Questions

1. A lot arrives with mask CD 0.4 nm above target and a mold 8 nm thinner. Compute the ME2 time and O₂ corrections.

2. Repeat the feedback example of Section 15.4.2 for bottom CD +0.3 nm and bow +0.5 nm. What is the full correction and the λ = 0.3 step?

3. If G changed to [[0.16, 0.12], [0.10, 0.13]], compute det G. Why would this operating point be harder to control?

4. A CO knee arrives 5 s later than usual on one wafer. List three causes and the metrology that would distinguish them.

5. Design a sampling plan for HV-SEM that detects a change in twist σ from 1.67 to 2.0 nm with 95% confidence within one day on one chamber.

---

**Next Chapter:** [Chapter 16: Post-Etch Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
