# Chapter 7: Gas Delivery, Polymer Control & Multi-Step Recipes

## Overview

A single chemistry cannot etch the whole capacitor hole well. The mold has five layers. The hole's aspect ratio rises from zero to 57. The oxygen released by the wafer falls as the bottom slows. The neutral supply that reaches the bottom thins out. A recipe that is right for the upper oxide closes the hole in the lower oxide, and a recipe that keeps the lower oxide open bows the upper one. The capacitor hole recipe is therefore a sequence of steps, each tuned to a layer and a depth, with gas flows that change inside steps as well as between them.

This chapter covers pressure, flow, and residence time at high power, the reference five-step recipe and how its times follow from the ARDE curve, ramped chemistry with depth, step transitions, and center/edge gas tuning.

**Learning Objectives:**
- Choose pressure and dilution for the capacitor hole and explain their effect on ion angle and polymer
- Derive step times from the ARDE curve and layer rate ratios
- Design gas ramps that compensate for the falling oxygen release and the rising aspect ratio
- Manage step transitions without notches, charging events, or particles
- Use center/edge gas splits and edge tuning gases for radial control

---

## 7.1 Pressure, Flow, and Dilution

### 7.1.1 Pressure

```
Effect of pressure in the main etch (illustrative, 15–30 mTorr):

  Pressure    s/λ (sheath)   Energetic ions    Polymer      k (ARDE)
  ─────────────────────────────────────────────────────────────────
  15 mTorr     0.6            ≈ 55%             lower        0.018
  20 mTorr     0.8            ≈ 45%             reference    0.020
  30 mTorr     1.2            ≈ 30%             higher       0.025
```

Lower pressure narrows the ion angular distribution (fewer charge-exchange collisions in the sheath, Chapter 3) and reduces ARDE. It also reduces the density and the supply of fluorocarbon radicals, so the rate per unit power falls, and the mask and sidewall get less protection. The capacitor hole runs at the low end of the CCP range, typically 15–25 mTorr, as a compromise.

### 7.1.2 Argon Dilution

Argon makes up about 80% of the reference main-etch flow. It sets the ion composition (mostly Ar⁺), lowers the partial pressure of the fluorocarbons for a given total pressure, and shortens the residence time. More argon means more physical sputtering and less polymer per ion: the bottom stays open, but the mask and the neck facet faster.

### 7.1.3 Residence Time Revisited

At fixed pressure, raising total flow shortens τ (Chapter 5) and preserves larger fragments. In practice the confinement-ring gap or the throttle valve sets the pressure, and the flow is chosen for τ and for the Ar fraction.

---

## 7.2 The Reference Recipe

### 7.2.1 Step Table

```
Reference capacitor hole recipe (illustrative; 40 MHz source / 400 kHz bias)

Step  Layer           Time   P      Src/Bias    Gases (sccm)                       T_wafer
                       (s)   (mT)   (kW)
────────────────────────────────────────────────────────────────────────────────────────────
SN1   top SiN          20    20     2.0 / 8     CH₂F₂ 30, C₄F₈ 15, O₂ 25, Ar 300    20 °C
ME1   upper oxide      90    20     2.5 / 12    C₄F₆ 40, C₄F₈ 20, O₂ 35, Ar 400     20 °C
SN2   middle SiN       15    20     2.5 / 12    CH₂F₂ 25, C₄F₈ 20, O₂ 30, Ar 350    20 °C
ME2   lower oxide     150    18     2.5 / 12    C₄F₆ 40, C₄F₈ 20, O₂ 35→42 (ramp),  20 °C
        (+ overetch)          (pulsed bias      NF₃ 0→6 (last 60 s), Ar 400
                              in last 60 s)
BO    bottom SiN       30    25     2.0 / 8     CHF₃ 40, O₂ 15, Ar 300              20 °C
────────────────────────────────────────────────────────────────────────────────────────────
Total                 305 s
```

### 7.2.2 Step Times from the ARDE Curve

Chapter 3 gave the time-to-depth relation for a single material:

```
t = [h + k h² / (2w)] / ER₀,   k/(2w) = 3.57×10⁻⁴ nm⁻¹

Define G(h) = h + 3.57×10⁻⁴ h²   (nm, "ARDE-corrected depth")

  h (nm)    G(h)
  ─────────────────
   120      125.1
   770      981.7
   820     1060.1
  1580     2471.5

Step times (using each layer's open-area rate in its own step):
  SN1:  G(120) − G(0)    = 125.1 nm / 420 nm/min = 0.30 min = 18 s  → 20 s
  ME1:  G(770) − G(120)  = 856.6 nm / 600 nm/min = 1.43 min = 86 s  → 90 s
  SN2:  G(820) − G(770)  = 78.4 nm  / 420 nm/min = 0.19 min = 11 s  → 15 s
  ME2:  G(1580) − G(820) = 1411.4 nm / 700 nm/min = 2.02 min = 121 s
        + overetch 29 s (24%)                                       → 150 s
```

Each nitride step is padded by a few seconds because the arrival of the etch front at the nitride is spread across holes and across the wafer, and the step must clear the nitride from all of them before the oxide chemistry returns. The 29 s overetch in ME2 covers the CD tail (8 s for a 3 nm narrow hole, Chapter 3), the radial spread in time to the stop (about 8 s), the mold-thickness spread (±15 nm at the bottom rate of 330 nm/min, about 3 s), and margin.

### 7.2.3 Why ME1 Runs Lean of ME2

ME1 etches the upper oxide, where the bow forms. Its Π is about 0.38 early, and its sidewall film must be thick enough to protect the upper wall. ME2 runs at depths where the bottom is starved. Its O₂ ramp and late NF₃ keep the bottom open as the oxygen from the wafer falls:

```
O₂ ramp in ME2 (illustrative):
  O from the wafer falls from ≈ 12 sccm (start of ME2) to ≈ 8 sccm (end)
  Feed O₂ ramps 35 → 42 sccm (+14 sccm O atoms)
  Π at start: (240 − 70 − 12) / 400 = 0.395
  Π at end:   (240 − 84 − 8)  / 400 = 0.37  (NF₃ adds 18 F → 148/418 = 0.35)
```

The ramp does more than hold Π constant. It makes the late etch slightly leaner, because the bottom needs more help as the aspect ratio rises.

---

## 7.3 Ramped Chemistry with Depth

### 7.3.1 Why Ramp

Three quantities change continuously during the oxide steps:

1. **Aspect ratio**: the bottom receives fewer neutrals and fewer ions.
2. **Oxygen release from the wafer**: falls as the bottom rate falls.
3. **Remaining mask**: thinner mask, more faceting, more scattered ions entering the hole.

A step with fixed flows sees all three drift. Ramping the O₂, NF₃, or C₄F₆/C₄F₈ ratio within the step compensates.

### 7.3.2 Common Ramp Strategies

```
Strategy                          Goal                         Risk
───────────────────────────────────────────────────────────────────────────────
O₂ ramp up in ME2                 keep bottom open              mask loss, bow
NF₃ added late                    clean bottom polymer          bow in the lower
                                                                oxide
C₄F₆ ramp down / C₄F₈ up          shift polymer deeper          less neck
                                                                protection
Bias pulsing in the last third    reduce charging and twist     longer etch
Pressure ramp down                narrower ion angle at depth   lower rate
```

### 7.3.3 Sub-Stepping

Rather than continuous ramps, many recipes split the oxide steps into several sub-steps with fixed flows. Sub-steps are easier to control and log, and APC can adjust each one. A typical ME2 might be four sub-steps of 30–45 s, with O₂ rising and NF₃ added in the last.

---

## 7.4 Step Transitions

### 7.4.1 Keeping the Plasma On

Extinguishing the plasma between steps would let the hole charge, cool, and collect particles from the collapsing sheath. Capacitor hole recipes change chemistry with the plasma on. The transition has three parts:

```
Transition from ME1 to SN2 (illustrative):
  t = 0       MFC setpoints change
  0–0.8 s     gas line delay; old chemistry still in the chamber
  0.8–2.5 s   mixing; τ ≈ 6.6 ms in the gap, but the showerhead plenum and
              lines take ≈ 1 s to flush
  > 2.5 s     new chemistry stable
  RF: source and bias held; bias reduced or ramped if the new step needs it
```

### 7.4.2 Notches and Steps

If ME1 ends lean and the polymer film on the wall is thin when SN2 begins, the nitride step's chemistry briefly etches the oxide sidewall just above the support. If SN2 ends and ME2 begins lean, a notch can form under the support. Mitigations:

- End ME1 slightly rich and begin SN2 with a short polymer-building segment
- Overlap the gas changes so that Π moves smoothly
- Hold the bias constant across the transition so the ion angle does not change

### 7.4.3 Detecting the Support

The etch front reaches the middle support at different times in different holes. OES lines for N-containing products (CN at 387 nm) rise as the front enters the nitride and fall as it exits. In a 50:1 hole the signal is weak and smeared over seconds, so the step times are set by the ARDE model and checked against cross-sections rather than called by endpoint (Chapter 15).

---

## 7.5 Center/Edge Gas Tuning

### 7.5.1 Split Showerheads

The upper electrode is divided into a center zone and one or two outer zones, each fed through its own flow splitter. A **tuning gas** (often O₂, C₄F₆, or Ar) can be added to the outer zone alone.

```
Reference split (illustrative): center 55%, edge 45% of the main mix
Tuning gas: O₂ 0–8 sccm to the edge zone
```

### 7.5.2 Radial Responses

```
Radial sensitivities in ME2 (illustrative), edge (r = 140 mm) minus centre:

  Knob                         Δ bottom CD    Δ bow CD     Δ time to stop
  ─────────────────────────────────────────────────────────────────────────
  Edge O₂ +2 sccm              +0.4 nm        +0.2 nm      −1.5%
  Split +5% to center          −0.3 nm        −0.1 nm      +1.0%
  Edge zone T +3 °C (Ch. 8)    +0.2 nm        +0.4 nm      −0.5%
```

Gas mostly moves the bottom; temperature mostly moves the bow. With two knobs and two targets, a 2×2 solve gives both:

```
Target: raise the edge bottom CD by 0.6 nm without changing the edge bow.

  0.4 x + 0.2 y = 0.6      (x: edge O₂ in units of 2 sccm; y: edge T in 3 °C)
  0.2 x + 0.4 y = 0

  From the second: x = −2y → 0.4(−2y) + 0.2y = 0.6 → −0.6 y = 0.6 → y = −1
  x = 2

  → Edge O₂ +4 sccm and edge zone −3 °C
```

The solve needs the sensitivities to stay linear over the range used. Chapter 15 shows how APC applies it automatically.

---

## Summary and Key Takeaways

1. **Low pressure narrows the ions and lowers ARDE.** The reference runs at 18–20 mTorr. 30 mTorr raises k by about 25%.

2. **Step times follow from the ARDE curve.** G(h) = h + k h²/(2w) and each layer's own rate give 18, 86, 11, and 121 s; padding and overetch bring the recipe to 305 s.

3. **Ramp the lower oxide.** O₂ ramps from 35 to 42 sccm and NF₃ joins late, to keep the bottom open as the wafer's oxygen release falls.

4. **Change chemistry with the plasma on.** A step transition takes about 2.5 s to settle. Abrupt Π changes at support interfaces cause notches.

5. **Gas moves the bottom, temperature moves the bow.** A 2×2 solve of edge O₂ and edge temperature sets both at the wafer edge.

---

## Study Questions

1. Recompute the four step times of Section 7.2.2 with k = 0.024. By how many seconds does the recipe lengthen?

2. The upper oxide is thinned to 600 nm and the lower oxide thickened to 810 nm, keeping H = 1600 nm. Recompute G at the interfaces and the ME1 and ME2 times.

3. Design a three-sub-step ME2 with fixed O₂ in each sub-step that keeps Π between 0.36 and 0.39 throughout, using the wafer oxygen release falling linearly from 12 to 8 sccm.

4. The gas line delay into the chamber is 0.8 s and the plenum flush is 1.7 s. If the etch front moves at 330 nm/min at the bottom of ME2, how much depth is etched during an ME2 → BO transition before the BO chemistry is established?

5. Using the radial sensitivity table, find the edge O₂ and edge-temperature changes that lower the edge bow by 0.4 nm without changing the edge bottom CD.

---

**Next Chapter:** [Chapter 8: Wafer Temperature, Cryogenic Chucks & Radial Control](./08-temperature-cryo-radial.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
