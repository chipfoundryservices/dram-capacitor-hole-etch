# Chapter 5: High-Power Capacitively Coupled Dielectric Chambers

## Overview

Capacitor holes are etched in capacitively coupled plasma (CCP) chambers built for dielectric etch at very high bias power. Two parallel electrodes a few centimetres apart hold the plasma. The upper electrode is a silicon showerhead that feeds the gas. The lower electrode is the electrostatic chuck that holds the wafer. A high-frequency source sustains the plasma, and a low-frequency bias drives the sheath above the wafer to several kilovolts. The design looks simple. Its challenges are scale and power: about 15 kW of RF into a gap of two litres, delivered uniformly across 300 mm, for millions of wafers.

This chapter explains why CCP is the reactor of choice for the capacitor hole, how dual- and triple-frequency operation separates density from ion energy, where the power goes, how pumping sets residence time and polymer chemistry, and how the fleet is sized and matched.

**Learning Objectives:**
- Explain why CCP rather than ICP is used for capacitor hole etch
- Describe dual- and triple-frequency CCP and the role of each frequency
- Build a power balance for the reference chamber
- Compute gas residence time and its effect on fragmentation
- Estimate throughput and the size of a capacitor-hole etch fleet
- Describe chamber matching for a profile-critical etch

---

## 5.1 Why CCP

### 5.1.1 Dissociation and Selectivity

Inductively coupled plasmas (ICP) reach electron densities of 10¹¹–10¹² cm⁻³ at a few millitorr. At those densities, C₄F₆ and C₄F₈ are broken into small fragments and free fluorine. The plasma loses the large, sticky fragments that protect the mask and the sidewall, and becomes too fluorine-rich for high selectivity to carbon and nitride. CCP runs at 10¹⁰–10¹¹ cm⁻³ and 15–40 mTorr, where the dissociation is gentler and the residence time shorter. The fluorocarbon chemistry of Chapter 4 relies on this.

```
Typical regimes (illustrative):
                     ICP (conductor)       CCP (capacitor hole)
  Pressure           3–20 mTorr            15–40 mTorr
  n_e                3×10¹¹ cm⁻³           2–5×10¹⁰ cm⁻³
  F / CF₂ ratio      high                  low
  Max bias           ≈ 1–2 kW, ≤ 1 kV      10–20 kW, 5–10 kV
  Gap                10–20 cm              2.5–4 cm
```

### 5.1.2 Uniformity and Large Area

A CCP gap of a few centimetres gives a nearly one-dimensional plasma over the wafer. The ion flux is uniform to a few percent without complex coil design. The narrow gap also keeps the gas residence time short and makes the upper electrode an active surface: it is a source of silicon, a scavenger of fluorine, and a sink for polymer.

### 5.1.3 High Bias Power

Most of the RF power in a capacitor-hole chamber goes into the bias. CCP chambers are built to accept it: thick dielectric layers in the chuck, wide RF feeds, high-voltage-rated edge components, and ceramic insulators designed against arcing at kilovolt sheath voltages.

---

## 5.2 Dual and Triple Frequency

### 5.2.1 Separating Density from Energy

In a single-frequency CCP, the same RF voltage drives both ionization and the sheath, so density and ion energy cannot be set separately. Dual-frequency CCP applies two frequencies:

```
High frequency (source): 40–100 MHz
  - Displacement current through the sheath is large; electron heating in
    the sheath is efficient
  - Sets n_e and the ion flux
  - Applied to the upper or lower electrode

Low frequency (bias): 0.4–2 MHz
  - Ions follow part of the RF cycle; the sheath voltage swings by kV
  - Sets the ion energy distribution
  - Applied to the lower electrode (chuck)
```

```
Reference chamber (illustrative):
  40 MHz source, 2.5 kW, on the lower electrode
  400 kHz bias, 12 kW, on the lower electrode
  Upper electrode grounded (or with negative DC superposition, Chapter 6)
  Gap 30 mm; 20 mTorr
```

The separation is not perfect. At kilovolt bias, the low-frequency sheath swings through most of the gap's sheath region and modulates electron heating by the source. Secondary electrons released from the wafer by keV ions are accelerated back through the sheath and add ionization. Raising the bias therefore raises the density too, typically by 10–30% for a doubling of bias power.

### 5.2.2 Triple Frequency

Some chambers add a third frequency, for example 13.56 MHz or 2 MHz between the source and the 400 kHz bias. Two bias frequencies together shape the ion energy distribution: the lower one sets the maximum energy and the higher one fills in the middle. Chapter 6 develops this.

---

## 5.3 Where the Power Goes

```
Reference power balance (illustrative, 14.5 kW delivered):

  Delivered:  source 2.5 kW + bias 12.0 kW = 14.5 kW

  Ion power to the wafer: J_i ⟨E_i⟩ A
    = 1.2 mA/cm² × 3.0 kV × 707 cm²                  ≈ 2.5 kW
  Ion power to the focus ring and edge (≈ 250 cm² at
    a slightly lower sheath voltage)                    ≈ 0.8 kW
  Secondary-electron beams from the wafer and ring
    (γ ≈ 0.1–0.2 at keV) absorbed in the plasma and
    at the upper electrode                               ≈ 1.5 kW
  Ion power to the upper electrode (lower sheath
    voltage, large area)                                 ≈ 1.5 kW
  Electron heating, ionization, excitation, dissociation ≈ 3.0 kW
  Losses in match, feeds, chuck dielectric, and
    stray capacitance (heat)                             ≈ 5.2 kW
```

The balance shows why capacitor-hole chambers run hot. Only about a sixth of the delivered power reaches the wafer as ions. Most of the rest heats electrodes, rings, and RF components, which must be cooled, and some of it ends up as wear on surfaces that ions strike (Chapter 9).

---

## 5.4 Pumping and Residence Time

### 5.4.1 Residence Time

```
Gas flow (reference main etch): C₄F₆ 40 + C₄F₈ 20 + O₂ 35 + Ar 400
  = 495 sccm ≈ 500 sccm
  1 sccm = 1.69×10⁻³ Pa·m³/s → Q = 0.845 Pa·m³/s

Plasma volume: π (0.15 m)² × 0.030 m = 2.1×10⁻³ m³
Pressure: 20 mTorr = 2.67 Pa

τ = p V / Q = 2.67 × 2.1×10⁻³ / 0.845 = 6.6 ms
```

A residence time of a few milliseconds limits how far a C₄F₆ molecule is broken down before it leaves. Longer residence (lower flow at the same pressure) produces more small fragments and more F. Shorter residence keeps large fragments and raises the polymer tendency. Flow is therefore a chemistry knob, not just a supply rate.

### 5.4.2 Pumping Speed

```
Effective pumping speed at the chamber: S = Q / p = 0.845 / 2.67
  = 0.32 m³/s = 320 L/s
```

The turbomolecular pump is much larger, typically 2000–3000 L/s, but conductance through the confinement rings and the pumping port reduces the effective speed. The confinement rings, stacked quartz or silicon rings around the gap, keep the plasma between the electrodes and set the pressure in the gap. Their spacing is adjusted to control pressure independently of flow.

### 5.4.3 Etch Products

```
Early in the etch (Chapter 3): SiF₄ ≈ 9 sccm, O (as CO, COF₂) ≈ 18 sccm
  → products are ≈ 5% of the feed
```

Products redeposit on the upper electrode and walls. SiF₄ is benign. Boron and phosphorus fluorides from the BPSG etch are less volatile and add to the wall film in the lower-oxide step.

---

## 5.5 The Upper Electrode and Confinement

The upper electrode is a silicon (or silicon carbide) disc with hundreds of gas holes. Under the plasma it is bombarded by ions at a few hundred volts and slowly consumed. Silicon scavenges fluorine (Si + 4F → SiF₄), which raises the polymer index (Chapter 4, Section 4.2.1). As the electrode thins and its gas holes widen, the gas distribution and the F scavenging both change. Chapter 9 follows these effects through the electrode life.

```
Reference electrode (illustrative):
  Single-crystal Si, 10 mm thick, ≈ 1000 gas holes of 0.5 mm diameter
  Consumption ≈ 15–25 µm per RF hour at full power
  Life ≈ 400–600 RF hours (limited by hole widening, not thickness)
```

---

## 5.6 Throughput and the Fleet

### 5.6.1 Chamber Cycle

```
Reference wafer cycle (illustrative):
  Transfer in, chuck, gas and RF stabilize        25 s
  Etch (five steps)                               305 s
  Dechuck, transfer out                           20 s
  Waferless autoclean (WAC), per wafer            60 s
  ──────────────────────────────────────────────────────
  Total                                           410 s ≈ 6.8 min
  → 8.8 wafers/h per chamber at 100% utilization
```

### 5.6.2 Fleet Size

```
Fab start rate: 100,000 wafers/month
One capacitor hole etch per wafer: 100,000 / 720 h = 139 wafers/h
Chamber availability (PM, qualification, idle): 80%
Chambers needed: 139 / (8.8 × 0.80) = 19.7 → 20 chambers
On four-chamber platforms: 5 platforms (plus spare capacity)
```

A large fleet of identical chambers must etch the same hole. Every chamber's hole must fall inside the spec without per-chamber lithography or mask changes.

### 5.6.3 Chamber Matching

```
Matching metrics (illustrative, chamber to chamber, same lot):
  Bottom CD mean:       ±0.6 nm
  Bow CD mean:          ±0.5 nm
  Etch time to stop:    ±3%
  Edge tilt at 147 mm:  ±0.03°
  Not-open rate:        within 2× of fleet median
```

Matching uses hardware tolerances (gap, electrode material and resistivity, ring dimensions, RF calibration), recipe offsets (time, O₂, edge gas, edge temperature), and APC constants per chamber (Chapter 15). The hardest parameters to match are those that depend on consumables: electrode thickness, ring height, and wall state. Chambers at different points in their consumable life have different holes.

---

## Summary and Key Takeaways

1. **CCP keeps the fragments.** Moderate density and short residence preserve the large fluorocarbon fragments that protect the mask and the wall.

2. **Two frequencies, two jobs.** 40 MHz sets the density; 400 kHz sets the ion energy. They interact at kilovolt bias.

3. **Only a sixth of the power reaches the wafer as ions.** About 2.5 kW of 14.5 kW. The rest heats electrodes, rings, and RF components.

4. **Residence time is a chemistry knob.** About 6.6 ms in the reference chamber. Longer residence means more dissociation and less polymer.

5. **A fleet must make one hole.** About 20 chambers per 100,000 wafers per month, matched to within about half a nanometre in CD and a few hundredths of a degree in edge tilt.

---

## Study Questions

1. Compute the residence time if the Ar flow is cut to 200 sccm and the pressure held at 20 mTorr by closing the confinement rings. How would the polymer tendency change?

2. If the bias is raised to 15 kW and the ion power to the wafer scales with the bias, estimate the new ion power and the heat that must be removed through the chuck.

3. A fab adds a second capacitor-hole etch per wafer for a two-tier mold (Chapter 14), each 70% as long as the reference etch. How many additional chambers does a 100,000 wafers/month fab need?

4. Explain why the upper electrode's consumption raises the polymer index, and in which direction the bottom CD drifts over the electrode life if no compensation is applied.

5. A chamber shows a bottom CD 1.2 nm smaller than the fleet median. List three hardware causes and the measurement that separates them.

---

**Next Chapter:** [Chapter 6: Low-Frequency Bias, Pulsing & Tailored Waveforms](./06-low-frequency-bias-pulsing.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
