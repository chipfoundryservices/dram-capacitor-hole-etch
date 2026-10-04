# Chapter 6: Low-Frequency Bias, Pulsing & Tailored Waveforms

## Overview

The capacitor hole is etched by ions that have fallen through several kilovolts of sheath. The bias system decides how many kilovolts, how the energy is spread across the ion population, and what happens to the charge those ions leave in the hole. A continuous 400 kHz sine wave gives a broad, bimodal energy distribution and continuous charging. Pulsing the bias lets the hole discharge between bursts. Tailored waveforms concentrate the ions at the high-energy end. A negative DC voltage on the upper electrode adds a beam of electrons that can reach the hole bottom. Each of these trades power, complexity, and component stress for a straighter, more open hole.

This chapter develops the ion energy distribution under low-frequency bias, bias pulsing and charge relaxation, tailored and DC-augmented waveforms, and the limits on how far the bias can be pushed.

**Learning Objectives:**
- Explain how bias frequency sets the width of the ion energy distribution
- Estimate the sheath voltage and mean ion energy from bias power and ion current
- Describe synchronized and bias-only pulsing and compute duty-averaged quantities
- Estimate charge relaxation in the off phase
- Describe tailored voltage waveforms and DC superposition and their effect on the IED and on charging
- List the failure modes that limit bias voltage

---

## 6.1 The Ion Energy Distribution

### 6.1.1 Frequency and IED Width

Whether ions follow the RF sheath voltage depends on the ratio of their transit time across the sheath, τ_ion, to the RF period, τ_RF:

```
τ_ion / τ_RF ≪ 1   (low frequency):  ions see the instantaneous voltage →
                                     broad, bimodal IED spanning ≈ V_min to V_max
τ_ion / τ_RF ≫ 1   (high frequency): ions see the average → narrow IED at ⟨V⟩

IED width for a sinusoidal bias of amplitude V_rf, high-frequency limit
(τ_ion ≫ τ_RF):
  ΔE ≈ (8 / 3π) · e V_rf · (τ_RF / τ_ion)
At low frequency the formula fails and ΔE approaches the full swing, ≈ 2 e V_rf
```

```
Reference sheath (illustrative), Ar⁺, s ≈ 4 mm, ⟨V⟩ ≈ 3 kV:
  τ_ion ≈ 3 s √(m / 2e⟨V⟩)
        = 3 × 4×10⁻³ × √(6.64×10⁻²⁶ / (2 × 1.6×10⁻¹⁹ × 3000))
        = 1.2×10⁻² × 2.63×10⁻⁷ = 3.2×10⁻⁷ s = 0.32 µs

  Bias        τ_RF (µs)    τ_ion/τ_RF    IED
  ───────────────────────────────────────────────────────
  400 kHz     2.50         0.13          broad, bimodal (0.3–6 keV)
  2 MHz       0.50         0.64          bimodal, narrower
  13.56 MHz   0.074        4.3           narrow, near ⟨V⟩
```

At 400 kHz, the ions sample almost the whole sheath waveform. The reference IED spans from a few hundred eV to nearly 6 keV. A lower frequency gives a higher maximum energy for the same power, because the peak sheath voltage is closer to V_pp, and it is the highest-energy ions that reach the bottom of the hole with enough energy left after grazing reflections.

### 6.1.2 Power, Voltage, and Current

At low frequency, most of the bias power is carried by the ion current through the sheath, plus secondary electrons accelerated back out:

```
P_bias ≈ (1 + γ_eff) I_ion ⟨V_sheath⟩ + losses

Ion current to the wafer + ring: I_ion ≈ 1.2 mA/cm² × 950 cm² ≈ 1.1 A
⟨V⟩ ≈ 3 kV, γ_eff ≈ 0.5 (secondaries + other loads, illustrative)
P ≈ 1.5 × 1.1 × 3000 ≈ 5.0 kW at the electrode surface

Remainder of the 12 kW: matching network, chuck dielectric loss,
stray capacitance to ground, and power coupled into the bulk plasma
```

Doubling the bias power does not double the ion energy. Part of the extra power raises the density (Chapter 5) and so the current. In the reference chamber, ⟨V⟩ scales roughly as P^0.6 at constant source power.

---

## 6.2 Bias Pulsing

### 6.2.1 Modes

```
Mode A, synchronized: source and bias pulsed together (on/off)
Mode B, bias-only:    source CW; bias pulsed on/off
Mode C, multi-level:  source high/low, bias on/off, with an offset

Reference pulsing (illustrative), Mode B:
  frequency 2 kHz (period 500 µs); bias duty 40% (200 µs on, 300 µs off)
```

Pulsed operation must deliver the same average ion energy and flux. Peak power during the on phase is therefore higher than the CW power:

```
To keep the time-averaged bias power at 12 kW with 40% duty:
  P_on = 12 / 0.40 = 30 kW   — beyond most generators

In practice the average power falls and the etch time rises:
  P_on = 20 kW, duty 40% → average 8 kW
  Ion energy during on: ⟨V⟩ ≈ 3 kV × (20/12)^0.6 ≈ 4.1 kV
  Ion flux averaged over the cycle falls to ≈ 0.4 × 1.25 = 0.5 of CW
  (density rises ≈ 25% with the higher on-power)
  Open-area rate ≈ 0.5 × √(4.1/3.0) ≈ 0.58 of CW
```

Pulsing costs etch rate. It is used where it pays back in straightness and opening, typically for the lower part of the hole.

### 6.2.2 Charge Relaxation in the Off Phase

During the off phase, the sheath above the wafer collapses to a few volts. Electrons, and in electronegative fluorocarbon plasmas negative ions, can then reach deeper into the hole.

```
Charge at the hole bottom at the end of an on phase (illustrative):
  V_bottom ≈ 200 V, bottom area (π/4)(24 nm)² = 452 nm²
  Local capacitance of the bottom to the surrounding wall:
    C ≈ 2π ε₀ ε_r L / ln(r_out/r_in) for a coaxial segment, L ≈ 50 nm,
    ε_r = 3.9, r_out/r_in ≈ 1.8 → C ≈ 1.8×10⁻¹⁷ F
  Charge: Q = C V ≈ 3.7×10⁻¹⁵ C ≈ 23,000 elementary charges

Electron flux into the hole during the off phase:
  Γ_e ≈ ¼ n_e v̄_e ≈ ¼ × 2×10¹⁶ m⁻³ × 1×10⁶ m/s = 5×10²¹ m⁻² s⁻¹
  Fraction reaching the bottom of a 57:1 hole (Clausing, ≈ 0.023,
  enhanced by the positive bottom): ≈ 0.05
  Bottom area 4.5×10⁻¹⁶ m² → arrival rate ≈ 5×10²¹ × 0.05 × 4.5×10⁻¹⁶
    = 1.1×10⁵ electrons/s at the bottom
  Time to neutralize 23,000 charges ≈ 0.2 s
```

The estimate shows that thermal electrons alone cannot discharge the bottom within a 300 µs off phase. What does work:

1. **Negative ions.** In the afterglow, the electron density drops and the sheath collapses. Negative ions (F⁻, CF₃⁻), trapped in the bulk during the on phase, reach the wafer. A positive bottom attracts them strongly.
2. **Wall conduction.** Some charge leaks through the polymer-coated sidewall to the conductive pad or to the walls of neighbouring holes.
3. **Ballistic electrons** from a negatively biased upper electrode (Section 6.4).

Pulsing also reduces the time-averaged charge simply because the ion current stops. The net effect, measured by the not-open rate and by twisting, is a substantial improvement for the lower half of the hole.

---

## 6.3 Tailored Waveforms

### 6.3.1 The Idea

A sine wave spends most of its time away from its peak. Ions that arrive during the low-voltage part of the cycle have low energy. They etch little at the bottom, are deflected easily, and add to the bow. A tailored waveform shapes the voltage so the sheath sits near a set value most of the cycle, with a short reset during which electrons reach the wafer and neutralize the surface charge.

```
Pulsed-DC-like bias waveform (schematic, wafer potential):

  0 ─┐   ┌─┐   ┌─┐   ┌─      short positive excursion: electrons reach the
     │   │ │   │ │   │       wafer surface (reset)
     │   │ │   │ │   │
     └───┘ └───┘ └───┘       long negative plateau: ions accelerated at a
    −V₀  (slight ramp to                  nearly constant sheath voltage
          compensate surface charging)
```

As the wafer surface charges during the plateau, the effective sheath voltage would fall. A negative voltage ramp during the plateau compensates, so the IED stays narrow.

```
Illustrative comparison at equal average ion energy (3 keV):
                           400 kHz sine     tailored (400 kHz rep. rate)
  IED FWHM                 ≈ 5 keV           ≈ 0.6 keV
  Fraction of ions < 1 keV ≈ 25%             ≈ 3%
  Bow CD                   reference         −1.0 to −1.5 nm
  ARDE coefficient k       0.020             ≈ 0.017
```

### 6.3.2 Costs

Tailored waveforms require non-sinusoidal generators with fast switching at kilovolts, matching networks that pass harmonics, and chucks and feeds that tolerate fast voltage edges. Arcing and component stress increase with the slew rate. Matching the waveform at the wafer, after the chuck's capacitance and the feed inductance, requires a model of the transmission path or a measurement close to the wafer.

---

## 6.4 DC Superposition

A negative DC voltage of several hundred volts applied to the upper electrode does two things:

1. **Secondary electrons from the upper electrode** are accelerated through the upper sheath, cross the gap with energies of hundreds of eV, and arrive at the wafer nearly vertically during the sheath collapse. These **ballistic electrons** can enter deep holes and neutralize the positive bottom.
2. **Ion bombardment of the upper electrode** rises, which increases silicon sputtering and fluorine scavenging and so raises the polymer index (Chapter 4).

```
Illustrative effect of −900 V DC on the upper electrode:
  Ballistic electron current to the wafer: a few % of the ion current
  Not-open rate: ÷3–5
  Twisting σ: −15–25%
  Upper electrode consumption: +30–50% → shorter electrode life
```

DC superposition and bias pulsing work together. The ballistic electrons arrive mainly in the off phase or at the sheath minimum, when the wafer sheath is thin enough for them to reach it.

---

## 6.5 Limits on Bias Voltage

```
Failure modes at high bias (illustrative):
  Wafer-edge arcing to the focus ring or chuck at > 8–10 kV V_pp
  Breakdown of the ESC dielectric (local field at pinholes, lift-pin holes,
    and He holes)
  Arcing through backside particles or a poorly clamped wafer
  Generator and match component stress (voltage across capacitors)
  Accelerated wear of the focus ring and the chuck edge
  Mask sputtering and faceting rising faster than the oxide rate
```

The bias has risen with each DRAM generation because the hole has deepened. Its practical ceiling, around 10 kV V_pp in current chambers, is one reason the industry is turning to chemistry (HF at low temperature) and waveform shaping rather than more voltage to reach the next aspect ratio (Chapter 14).

---

## Summary and Key Takeaways

1. **Low frequency gives the highest energies.** At 400 kHz the ions follow the sheath swing, so the IED spans 0.3 to 6 keV.

2. **Bias power raises both energy and density.** ⟨V⟩ scales roughly as P^0.6 in the reference chamber.

3. **Pulsing costs rate and buys straightness.** A 40% duty at 20 kW peak gives about 58% of the CW rate, but the off phase lets negative ions and electrons reduce the bottom charge.

4. **Thermal electrons alone cannot discharge the bottom.** Negative ions, wall conduction, and ballistic electrons do most of the work.

5. **Tailored waveforms narrow the IED.** They cut the low-energy fraction from about 25% to a few percent and reduce the bow by about 1 nm, at the cost of more complex RF hardware.

6. **Bias voltage has a ceiling.** Arcing, chuck breakdown, and wear limit V_pp to roughly 10 kV in current chambers.

---

## Study Questions

1. Compute τ_ion for CF₃⁺ (mass 69 u) in the reference sheath and compare τ_ion/τ_RF at 400 kHz and 2 MHz. Which IED is broader?

2. A process uses bias pulsing at 1 kHz with 50% duty and 18 kW on-power. Using the scaling of Section 6.2.1, estimate the open-area rate relative to 12 kW CW.

3. Using the charge estimate of Section 6.2.2, what negative-ion flux into the bottom would neutralize 23,000 charges in 300 µs? Express it as a fraction of the ion flux during the on phase.

4. A tailored waveform reduces the fraction of ions below 1 keV from 25% to 3%. If low-energy ions are responsible for 60% of the lateral etch at the bow, estimate the reduction in bow CD from a reference bow of 3 nm per side.

5. Why does DC superposition shorten the life of the upper electrode? Estimate the change in electrode life if consumption rises by 40%.

---

**Next Chapter:** [Chapter 7: Gas Delivery, Polymer Control & Multi-Step Recipes](./07-gas-polymer-multistep.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
