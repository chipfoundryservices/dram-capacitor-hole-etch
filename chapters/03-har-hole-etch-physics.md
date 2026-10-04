# Chapter 3: High-Aspect-Ratio Hole Etch Physics

## Overview

An oxide etch on an open surface is controlled by two fluxes: ions that bring energy, and fluorocarbon neutrals that bring the fluorine and carbon. The rate is set by their balance. In the capacitor hole, both fluxes must travel down a tube 28 nm wide and 1.6 µm long before they do any work. Ions that are not almost perfectly vertical strike the wall. Neutrals bounce down the tube and are lost to the wall, or arrive at the bottom thinned out. Electrons cannot follow the ions down, so the hole charges. Every one of these effects grows with depth.

This chapter builds the physics of the hole from the entrance down: the ion energy and angle at the wafer, the acceptance angle of the hole, neutral transport and the Coburn–Winters model, ARDE and the time-to-depth curve with its CD sensitivity, charging and ion deflection, and loading by the large open area of the array.

**Learning Objectives:**
- Estimate the ion flux and etch yield needed for the reference oxide rate
- Estimate the ion angular spread from the sheath and compare it with the hole acceptance angle
- Apply the Clausing transmission and the Coburn–Winters model to a 57:1 hole
- Compute the time-to-depth curve, the bottom rate, and the depth sensitivity to CD
- Estimate charging potentials and the ion deflection they cause
- Estimate global and local loading from the hole open area

---

## 3.1 Fluxes at the Wafer

### 3.1.1 What an Oxide Etch Needs

```
Reference open-area TEOS rate: ER₀ = 600 nm/min = 10 nm/s
SiO₂ molecular density: 2.27×10²² cm⁻³ (2.27×10²¹ per cm² per 100 nm)

Removal flux: 10×10⁻⁷ cm/s × 2.27×10²² cm⁻³ = 2.27×10¹⁶ SiO₂ cm⁻² s⁻¹

Ion-driven fluorocarbon etch yield at ≈ 3 keV with a thin CFₓ film:
  Y ≈ 3 SiO₂ per ion (illustrative; rises roughly as √E above threshold)
Ion flux needed: 2.27×10¹⁶ / 3 = 7.6×10¹⁵ cm⁻² s⁻¹  → J_i ≈ 1.2 mA/cm²

Each SiO₂ needs ≈ 4 F (to SiF₄) and supplies 2 O that must be removed
as CO, COF₂, or O-containing products:
  Fluorine needed ≈ 9×10¹⁶ F cm⁻² s⁻¹ (from CFₓ, F, and ion fragments)
```

The ion energy is far above the threshold for oxide sputtering (about 50 eV with fluorocarbon). The etch is **energy-driven**: each ion supplies energy that a thin fluorocarbon film converts into volatile products. As long as the film supplies enough fluorine and the ions arrive, the rate tracks the ion flux. In the hole, both conditions weaken with depth.

### 3.1.2 Power Delivered to the Surface

```
Ion power density: J_i × ⟨E_i⟩ = 1.2×10⁻³ A/cm² × 3000 V = 3.6 W/cm²
Over a 300 mm wafer (707 cm²): ≈ 2.5 kW into the wafer from ions alone
```

This heat must be removed through the chuck (Chapter 8). It also explains the wear of every surface the ions strike, including the focus ring at the wafer edge (Chapter 9).

---

## 3.2 Ion Energy and Angle

### 3.2.1 The Low-Frequency Sheath

The bias is applied at 400 kHz with a peak-to-peak voltage near 7 kV. The ion transit time across the sheath is comparable to, or longer than, part of the RF period, so ions see a time-varying sheath. The resulting ion energy distribution (IED) is broad and bimodal, with peaks near the minimum and maximum sheath voltages.

```
Reference sheath (illustrative):
  V_pp ≈ 7.0 kV, DC self-bias of the wafer ≈ −3.0 kV
  Sheath voltage swings ≈ 0.1 kV to ≈ 6 kV over the cycle
  Ion transit time for Ar⁺ across a 4 mm sheath at kV energies ≈ 0.3–0.5 µs
  RF period at 400 kHz: 2.5 µs → ions follow a large part of the swing

IED: bimodal, low peak ≈ 0.3–0.8 keV, high peak ≈ 5–6 keV,
     mean ⟨E_i⟩ ≈ 3 keV
```

Both peaks matter. The high-energy ions do most of the etching at the bottom of the hole. The low-energy ions are deflected more easily, deposit charge on the upper walls, and help form polymer-free regions near the neck. Chapter 6 shows how tailored waveforms narrow the IED toward the high-energy end.

### 3.2.2 Angular Spread

An ion that falls collisionlessly through a sheath of voltage V gains a vertical velocity much larger than its thermal velocity:

```
Collisionless spread:
  θ ≈ √(T_i⊥ / E_i)     (T_i⊥: transverse ion temperature at the sheath
                           edge, ≈ 0.05 eV)
  E_i = 3000 eV:  θ ≈ √(0.05/3000) = 4.1×10⁻³ rad = 0.23°
```

At 20 mTorr the sheath is weakly collisional. Charge-exchange collisions with Ar create ions that start partway down the sheath with zero velocity and a fresh random direction:

```
Ar neutral density at 20 mTorr, 300 K:  n = p/kT = 2.67 Pa / (1.38×10⁻²³ × 300)
                                          = 6.4×10²⁰ m⁻³
Ar⁺/Ar charge-exchange cross section at kV: σ_cx ≈ 3×10⁻¹⁹ m²
Mean free path: λ = 1/(nσ) = 1/(6.4×10²⁰ × 3×10⁻¹⁹) = 5.2 mm
Sheath thickness (high-voltage Child law, n_e ≈ 2×10¹⁶ m⁻³, T_e ≈ 3 eV,
  6 kV): s ≈ 4 mm  → s/λ ≈ 0.8
Fraction of ions crossing without a collision: exp(−0.8) ≈ 0.45
```

About half of the ions arrive at full energy with a very narrow angle. The rest arrive with less energy and a wider spread, because they were born inside the sheath. The angular distribution of the energetic part has a root-mean-square half-angle of roughly 0.3–0.6°. The low-energy, wide-angle tail carries most of the off-axis ions.

### 3.2.3 The Acceptance Angle of the Hole

```
An ion entering the centre of a hole of width w can reach depth h
without striking the wall if its angle θ < arctan(w / (2h)) (from centre)
or θ < arctan(w/h) (from the far edge).

Mask + mold at the end of the etch: h = 0.73 (ACL) + 1.60 = 2.33 µm
  w = 28 nm:  arctan(28/2330) = 0.69°  (edge-to-edge)
              arctan(14/2330) = 0.34°  (from the centre)
At mid-mold (h = 0.73 + 0.80 = 1.53 µm): 1.05° / 0.52°
```

The acceptance angle of the finished hole is comparable to the angular spread of the energetic ions. A large fraction of the ions that enter the hole therefore strike the wall at grazing angles somewhere along the way. At kilovolt energies and grazing angles of under a degree, many of them reflect specularly from the wall and continue down. This **specular reflection** is what lets the hole be etched at all at 50:1. It also means that the wall's shape, charge, and polymer decide where those reflected ions go (Chapter 10).

---

## 3.3 Neutral Transport

### 3.3.1 Free-Molecular Flow

At 20 mTorr the neutral mean free path is several millimetres, about 10⁵ times the hole diameter. Inside the hole, neutrals move in straight lines between wall collisions. On each wall collision a neutral either sticks (and becomes polymer or etches the wall) with probability s, or re-emits in a random direction.

### 3.3.2 The Clausing Transmission

For a tube of length L and diameter d with non-sticking, diffusely re-emitting walls, the probability that a molecule entering the top reaches the bottom is the Clausing factor K:

```
Long-tube limit:   K ≈ 4d / (3L)   (accurate for L/d > 10)
Reference, full depth (L/d = 1600/28 = 57):
  K ≈ 4 / (3 × 57) = 0.023
At mid-depth (L/d = 29): K ≈ 0.046
```

### 3.3.3 The Coburn–Winters Model

```
Γ_bottom / Γ_top = K / (K + β (1 − K))

β: probability that a molecule hitting the bottom is consumed

Reference, full depth (K = 0.023):
  Species       β        Γ_bottom/Γ_top
  ─────────────────────────────────────
  F             0.01     0.70
  CF₂           0.05     0.32
  CF / C₂F₄...  0.20     0.11
  O             0.05     0.32
```

The model assumes non-sticking walls. Real walls are coated with fluorocarbon polymer and do consume radicals. A wall sticking coefficient s_w shortens the effective transport length:

```
With wall loss, a characteristic decay length for the flux along the hole:
  λ_w ≈ d / √(2 s_w)  (diffusion-reaction balance for s_w ≪ 1, illustrative)
  CF₂ with s_w = 0.005: λ_w ≈ 28 / √0.01 = 280 nm
  → the polymer precursor flux falls by e every ≈ 280 nm along the wall
```

High-sticking polymer precursors such as CF and C₂ deposit near the top of the hole and are almost absent at the bottom. Low-sticking species such as CF₂ and F reach deeper. The fluorocarbon chemistry of Chapter 4 is chosen, in part, to put the right precursors at each depth.

### 3.3.4 Why Neutral Starvation Matters

At the bottom of the hole the ion flux has also fallen, by loss to the walls and by deflection. The rate depends on which falls faster. If the neutral flux falls faster, the bottom is starved of fluorine and the yield per ion drops. If the ion flux falls faster, the bottom collects polymer and the etch can stop. The neutral-to-ion flux ratio at the bottom, not the absolute flux, decides the outcome (Chapter 12).

---

## 3.4 ARDE and the Time-to-Depth Curve

### 3.4.1 The Linear ARDE Form

Measured hole depths against time fit a simple form well over the reference range:

```
ER(A) = ER₀ / (1 + k A),   A = h / w

Reference: k = 0.020 (TEOS-equivalent, w = 28 nm average CD)

  Depth (nm)    A      ER / ER₀
  ─────────────────────────────
    100         3.6     0.93
    400        14.3     0.78
    800        28.6     0.64
   1200        42.9     0.54
   1600        57.1     0.47
```

At full depth the bottom etches at 47% of the open-area rate.

### 3.4.2 Time to Depth

```
dh/dt = ER₀ / (1 + k h / w)

Integrate from 0 to h:
  t(h) = [h + k h² / (2w)] / ER₀

Reference (TEOS-equivalent, ER₀ = 600 nm/min, w = 28 nm, k = 0.020):
  k / (2w) = 0.020 / 56 = 3.57×10⁻⁴ nm⁻¹

  h (nm)     h + k h²/(2w)     t (min)
  ──────────────────────────────────────
   400        457               0.76
   800        1029              1.71
  1067        1474              2.46   (two-thirds depth)
  1200        1714              2.86
  1600        2514              4.19
```

The last third of the depth takes 4.19 − 2.46 = 1.73 min, about 70% of the time needed for the first two-thirds.

In the real stack, the nitride supports etch more slowly and the lower oxide more quickly. Chapter 7 converts the curve into step times using rate ratios of 0.70 (SiN) and 1.17 (BPSG). The result is the reference sequence of Chapter 2: 90 s for the upper oxide, 121 s for the lower oxide to reach the stop, and 29 s of overetch.

### 3.4.3 Depth Sensitivity to CD

At fixed time, a narrower hole has a higher aspect ratio at every depth:

```
h + k h² / (2w) = ER₀ t   (fixed)

Differentiate with respect to w at fixed t:
  dh (1 + k h / w) − (k h² / (2 w²)) dw = 0
  ∂h/∂w = (k h² / (2 w²)) / (1 + k h / w)

Reference at h = 1600 nm, w = 28 nm:
  numerator:   0.020 × 1600² / (2 × 28²) = 51,200 / 1568 = 32.7
  denominator: 1 + 0.020 × 1600 / 28 = 2.14
  ∂h/∂w = 15.2 nm per nm
```

A hole 1 nm narrower is 15 nm shallower at the moment the reference hole reaches the stop. This is the most important single number for overetch. A hole that is 3σ narrow in an EUV distribution (σ = 1 nm) is 45 nm behind. A double-SADP family 1 nm narrow is 15 nm behind. The overetch must cover both.

```
Overetch needed to bring a hole Δw narrow to full depth:
  Δt = (∂h/∂w × Δw) / ER_bottom,  ER_bottom = 0.47 × ER₀ (lower oxide:
       0.47 × 700 = 330 nm/min)
  Δw = 3 nm (3σ EUV): 45 nm / 330 nm/min = 8.2 s
  Plus stop-thickness margin and wafer-edge offset → reference 29 s
```

### 3.4.4 What k Means

The coefficient k is not a constant of nature. It bundles ion loss to the walls, neutral starvation, polymer accumulation, and charging. Its value rises with:

- **Higher pressure** (more ion scattering and wider angle) — Chapter 7
- **More polymerizing chemistry** (more deposition at the bottom) — Chapter 4
- **Lower ion energy** (more deflection, lower yield at grazing reflection) — Chapter 6
- **Higher wafer temperature** for some chemistries (less sidewall polymer, more ion loss into the wall) — Chapter 8

A recipe change that lowers k by 0.002 shortens the etch by about 5% and reduces ∂h/∂w by about 8%.

---

## 3.5 Charging

### 3.5.1 Why the Hole Charges

Ions arrive almost vertically. Electrons arrive nearly isotropically, with a few electronvolts of energy, during the brief part of each RF cycle when the sheath collapses. Electrons with an isotropic distribution cannot reach the bottom of a 57:1 hole; they strike the upper walls. The result is the **electron shading** effect:

```
Upper wall: collects electrons → charges negative
Bottom:     collects ions without matching electrons → charges positive
```

The bottom charges until it repels enough ions to bring the ion and electron currents into balance. Because the energetic ions carry several kiloelectronvolts, the bottom potential needed to stop them is far higher than anything the dielectric wall can hold. Instead, the bottom reaches a potential of tens to a few hundred volts, set by leakage through the wall and by the electron current that does arrive.

```
Illustrative bottom potentials (oxide hole, landing on nitride over W):
  CW bias at kV, 50:1 hole:            V_bottom ≈ 100–300 V
  Bias pulsed with negative-ion or
  electron injection in the off phase: V_bottom ≈ 20–60 V
```

### 3.5.2 Deflection

A bottom potential of 200 V barely slows a 3 keV ion. What matters is the **lateral** field from asymmetric charge on the walls. If one side of the hole is charged slightly differently from the other, energetic ions are bent sideways.

```
Lateral deflection of an ion of energy E_i (in eV) passing a length L
of lateral field E⊥:
  θ ≈ E⊥ L / (2 E_i)

Example: a 2 V asymmetry across a 28 nm hole, E⊥ ≈ 2 V / 28 nm = 7×10⁷ V/m,
acting over L = 200 nm:
  θ ≈ 7×10⁷ × 2×10⁻⁷ / (2 × 3000) = 2.3×10⁻³ rad = 0.13°

Lateral shift of the etch front over the remaining 800 nm:
  800 × tan(0.13°) = 1.9 nm
```

A small, persistent asymmetry in wall charge can therefore move the bottom of the hole by several nanometres. If the asymmetry has a random sign hole to hole, the result is **twisting** (Chapter 11). If it has a systematic direction, the bottom is displaced in that direction everywhere. Low-energy ions, deflected far more easily (θ ∝ 1/E_i), strike the walls near the top and contribute to the bow (Chapter 10).

### 3.5.3 Charge Relief

Charging is relieved by:

1. **Bias pulsing** with an off phase long enough for electrons and negative ions to reach the bottom (Chapter 6)
2. **Sidewall conduction** through a thin, slightly conductive polymer or a doped oxide (Chapter 13)
3. **Higher ion energy**, which reduces deflection for a given field
4. **Neutralization by secondary electrons** emitted from the bottom

---

## 3.6 Loading

### 3.6.1 Global Loading

At the top of the mold, 46% of the array area is hole. With an array efficiency of 55%, about a quarter of the wafer is etching oxide at the open-area rate early in the etch. The products (SiF₄, CO, COF₂) and the oxygen they release change the plasma.

```
Oxide removal rate across the wafer, early in the etch:
  0.25 × 707 cm² × 2.27×10¹⁶ cm⁻² s⁻¹ = 4.0×10¹⁸ SiO₂/s
  Oxygen released: 2 × 4.0×10¹⁸ = 8.0×10¹⁸ O/s

Converting with 1 sccm = 4.48×10¹⁷ molecules/s:

  O released: 8.0×10¹⁸ / 4.48×10¹⁷ = 18 sccm of O atoms (≈ 9 sccm O₂-equivalent)
  SiF₄ produced: 4.0×10¹⁸ / 4.48×10¹⁷ = 9 sccm
  Reference O₂ feed: 35 sccm → the wafer adds about a quarter as much oxygen
  as the gas supply
```

The oxygen released from the oxide burns polymer. As the hole deepens and the bottom rate falls, the oxygen release falls with it, and the plasma becomes more polymerizing late in the etch. This drift, intrinsic to the etch, is one reason the recipe is split into steps with different O₂ (Chapter 7).

### 3.6.2 Product-to-Product Loading

A product with a different array efficiency releases a different amount of oxygen. A 10% change in open area changes the oxygen release by about 1 sccm O₂-equivalent, enough to shift the polymer balance and the bottom CD measurably. Recipes are qualified per product, and APC carries a product constant (Chapter 15).

### 3.6.3 Local Loading

Within a die, the array edge and the dummy holes that surround it see fewer neighbours. Their local neutral supply is slightly richer, and they are often designed as dummies precisely because they etch differently. Chapter 10 returns to the array-edge profile.

---

## Summary and Key Takeaways

1. **The etch is energy-driven.** About 1.2 mA/cm² of ions at 3 keV mean energy etch 600 nm/min of TEOS. About 2.5 kW enters the wafer as ion power.

2. **The hole accepts less than a degree.** The finished hole accepts ions within about 0.7° edge to edge. The energetic ions spread by roughly 0.3–0.6°, so many graze the wall and reflect.

3. **Neutrals thin out with depth.** The Clausing factor at full depth is 0.023. Sticky polymer precursors stay near the top; F and CF₂ reach the bottom.

4. **ARDE halves the rate.** With k = 0.020, the bottom etches at 47% of the open-area rate. The last third of the depth takes 70% as long as the first two-thirds.

5. **Width becomes depth.** ∂h/∂w ≈ 15 nm/nm at full depth. The overetch must cover the narrowest family and the CD tail.

6. **The hole charges.** Electron shading leaves the bottom positive and the walls unevenly charged. A 2 V lateral asymmetry can move the bottom by about 2 nm.

7. **The wafer is a gas source.** The etched oxide releases oxygen equal to about a quarter of the O₂ feed, and this falls as the hole deepens.

---

## Study Questions

1. The bias is raised so that ⟨E_i⟩ = 4 keV at the same ion flux. If Y rises as √E, what is the new open-area rate? What ion power density reaches the wafer?

2. Compute the Clausing factor and the bottom-to-top flux ratio for CF₂ (β = 0.05) at depths of 400, 800, and 1600 nm in a 28 nm hole. Plot the trend.

3. Using the linear ARDE form with k = 0.025, compute t(1600) and ∂h/∂w at full depth. Compare with the reference.

4. A depth series in TEOS gives 470 nm at 1.0 min and 830 nm at 2.0 min with w = 28 nm. Fit ER₀ and k.

5. A wall-charge asymmetry of 3 V across the hole acts over 300 nm in the lower oxide, 600 nm above the bottom. For 3 keV ions, estimate the deflection angle and the lateral shift at the bottom. Repeat for 500 eV ions.

6. A new product has an array efficiency of 0.60 instead of 0.55. Estimate the change in oxygen release early in the etch, in sccm O₂-equivalent, and say in which direction the bottom CD will move if the recipe is unchanged.

---

**Next Chapter:** [Chapter 4: Fluorocarbon Chemistry, Polymer Balance & Selectivity](./04-fluorocarbon-chemistry-selectivity.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
