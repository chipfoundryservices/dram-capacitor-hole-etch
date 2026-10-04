# Chapter 8: Wafer Temperature, Cryogenic Chucks & Radial Control

## Overview

Temperature sets how much polymer sticks to the sidewall, how fast the mask erodes, and, at low temperature, whether HF and other species condense on the oxide. In the capacitor hole, a few degrees of wafer temperature move the bow by a fraction of a nanometre, and the wafer receives several watts per square centimetre from the plasma. The electrostatic chuck must remove that heat, hold the wafer at a set temperature in several radial zones, and do so within the first seconds of each step. At the wafer edge, the chuck and the focus ring must also keep the sheath flat, because a bent sheath tilts every hole at the edge.

This chapter covers the temperature dependence of the etch, the heat balance at 15 kW, multi-zone chucks, low-temperature and cryogenic operation, and the focus ring and edge tilt.

**Learning Objectives:**
- Describe how wafer temperature changes polymer, bow, bottom CD, and mask erosion
- Compute the wafer heat flux and the backside gas conductance needed to hold temperature
- Estimate the thermal time constant of the wafer and the chuck
- Use multi-zone temperature for radial bow control
- Describe cryogenic chucks and their consequences for the etch
- Explain edge tilt from the sheath at the focus ring and compute its effect on bottom placement

---

## 8.1 Temperature Dependence of the Etch

### 8.1.1 Polymer and Bow

The sticking coefficient of fluorocarbon radicals on the sidewall falls as temperature rises. A warmer wafer has a thinner sidewall film, and the bow grows. The mask and the neck also receive less polymer.

```
Temperature sensitivities in the main etch, near 20 °C (illustrative):

  Quantity                  per +1 °C
  ───────────────────────────────────────
  Bow CD                    +0.13 nm
  Bottom CD                 +0.07 nm
  Top (neck) CD             +0.05 nm
  ACL erosion rate          +0.6 nm/min
  Oxide open-area rate      ≈ +0.1%
```

The oxide rate itself changes little, because the etch is ion-driven. Temperature acts through the polymer.

### 8.1.2 Why Not Run Cold?

A colder wafer has a thicker sidewall film, a smaller bow, and a better mask. It also has a thicker film at the neck and at the bottom, so the bottom CD shrinks and the not-open rate rises. Near 20 °C, the reference process balances bow against bottom opening. Below 0 °C, the chemistry begins to change qualitatively as HF, water, and fluorocarbon species start to condense, which is the basis of cryogenic etch (Section 8.4).

---

## 8.2 The Heat Balance

### 8.2.1 Heat Flux to the Wafer

```
Ion power (Chapter 5):                         2.5 kW
Other heat (radical recombination, radiation
  from the hot upper electrode, electron flux): ≈ 0.7 kW
Total into the wafer:                           ≈ 3.2 kW
Per unit area: 3200 / 707 = 4.5 W/cm²
```

### 8.2.2 Removing the Heat

The wafer sits on a ceramic electrostatic chuck. Helium at 20–40 Torr fills the microscopic gap between the wafer back and the chuck surface and carries the heat.

```
Heat path (illustrative):
  wafer → He gap (h_gap) → ceramic (≈ 1 mm Al₂O₃, k ≈ 30 W/m·K) →
  bond layer → aluminium base with coolant channels

He gap conductance at 30 Torr: h_gap ≈ 0.15 W/cm²·K
  ΔT (wafer − chuck surface) = 4.5 / 0.15 = 30 K
Ceramic:  ΔT = q t / k = 4.5×10⁴ W/m² × 1×10⁻³ m / 30 = 1.5 K
Bond and base: ≈ 3 K

To hold the wafer at 20 °C: chuck surface ≈ −10 °C; coolant ≈ −15 °C
```

The largest drop is across the helium gap. Its conductance depends on helium pressure, surface roughness, and contact area, and it is the main way temperature is tuned quickly.

### 8.2.3 Thermal Time Constants

```
Wafer: mass 128 g, c_p 0.70 J/g·K → C_w = 90 J/K
  τ_w = C_w / (h_gap A) = 90 / (0.15 × 707) = 0.85 s

Chuck top ceramic and base: C ≈ 5–10 kJ/K, coupled to coolant
  τ_chuck ≈ 20–60 s
```

The wafer follows a change in heat flux within about a second. The chuck surface follows over tens of seconds. When the bias steps from 8 kW (SN1) to 12 kW (ME1), the wafer heats by a few degrees for the first half-minute while the chuck catches up. Recipes often hold a higher He pressure or a lower chuck setpoint at the start of high-power steps to cancel this transient.

---

## 8.3 Multi-Zone Chucks

### 8.3.1 Zones

```
Reference chuck (illustrative):
  Coolant: one loop, −15 °C
  Heaters: 4 radial zones (r < 75, 75–120, 120–140, > 140 mm) embedded in
           the ceramic; each can raise its zone by 0–15 K above the
           coolant-limited temperature
  He: 2 zones (inner, outer), independently set at 15–40 Torr
```

Many recent chucks add tens to hundreds of small heater cells for fine azimuthal and radial correction.

### 8.3.2 Radial Bow Control

The bow has a radial signature from the radial ion flux, the edge sheath, and the edge gas mix. Because temperature moves the bow strongly and the bottom only weakly (Section 8.1.1), heater zones are the primary knob for a flat bow profile. Gas tuning then sets the bottom (Chapter 7, Section 7.5).

```
Example: the bow at r = 130 mm is 0.5 nm larger than at the centre.
  Lower zone 3 by 0.5 / 0.13 = 3.8 K
  Bottom CD in zone 3 moves by −0.07 × 3.8 = −0.27 nm (correct with gas)
```

---

## 8.4 Low-Temperature and Cryogenic Operation

### 8.4.1 What Changes Below 0 °C

```
Wafer temperature regimes (illustrative):
  +20 to +40 °C   conventional fluorocarbon; polymer-protected sidewall
  −20 to 0 °C     thicker polymer; HF begins to adsorb on oxide
  −60 to −40 °C   HF/H₂O adsorbed layer on the oxide; very high oxide rate;
                  sidewall protected by condensed species and low reactivity
  < −80 °C        classical cryogenic Si etch regime (SF₆/O₂); for oxide,
                  condensation of C₄F₈ and products can close holes
```

### 8.4.2 Cryogenic Chucks

A chuck that holds the wafer at −60 °C under 4.5 W/cm² needs its surface near −90 °C, given the 30 K helium drop. This requires a chiller with a low-temperature heat-transfer fluid or a refrigerant loop, insulation of the chuck from the chamber body, and seals and bond layers rated for the cold. The chamber walls must stay warm, or etch products and HF condense on them.

```
Cryogenic chuck considerations:
  Bond layer and ceramic must tolerate ΔT ≈ 150 K cycling
  Moisture on the wafer before etch must be removed (it would freeze)
  Wafer must be warmed before leaving vacuum, or water condenses
  Heater zones must work against a much colder coolant (less authority)
  Transfer and dechuck at low temperature: residual charge, sticking
```

Cryogenic etch is covered as an advanced scheme in Chapter 14.

---

## 8.5 The Focus Ring and Edge Tilt

### 8.5.1 The Edge Sheath

At the edge of the wafer, the sheath above the wafer meets the sheath above the focus ring. If the ring surface and the wafer surface do not sit at the same effective electrical height, the sheath bends. Ions crossing a bent sheath acquire a radial velocity component and strike the wafer at an angle. Every hole near the edge then **tilts**.

```
Edge geometry (schematic):

  plasma
  ─────────────────────────╮
                           ╰───────────── sheath edge over the ring
  ═════════ wafer ═════════  ┃
                             ┃ ring (Si or SiC), top lower than the
                             ┃ effective wafer height after erosion
  ions near the wafer edge are tilted outward
```

### 8.5.2 Tilt and Ring Wear

The ring is bombarded by the same ions as the wafer and erodes. As it thins, the sheath over it drops, and edge holes tilt outward.

```
Illustrative edge-tilt sensitivity at r = 147 mm:
  Tilt ≈ 0.08° per 100 µm of ring height below the matched height
Ring erosion: ≈ 3 µm per RF hour at the reference power

After 100 RF hours: 300 µm → tilt ≈ 0.24°
Bottom displacement: 1600 nm × tan(0.24°) = 6.7 nm
Spec: tilt ≤ 0.1° → displacement ≤ 2.8 nm
```

Without compensation, the ring would have to be changed every 40 RF hours. Compensation methods:

1. **Ring lift**: actuators raise the ring to keep its top at the matched height as it erodes.
2. **Ring bias tuning**: a separate RF or DC path to the ring adjusts its sheath voltage, and so the sheath height, without moving it.
3. **Ring material and shape**: SiC erodes more slowly than Si; stepped profiles keep the sheath edge in place longer.

### 8.5.3 Tilt Through the Etch

Tilt is not constant through the etch. As the hole deepens, the same tilt angle displaces the bottom more. And a tilt that changes during the etch, for example through ring heating, gives a hole that is bent rather than straight. Chapter 11 combines tilt with twisting in the bottom-placement budget.

---

## 8.6 Wafer Edge Temperature

The outermost few millimetres of the wafer overhang the chuck or sit over its sealing band, where the helium conductance is lower. The edge runs warmer.

```
Edge (r > 145 mm) helium conductance ≈ 70% of the interior
  ΔT across the gap at the edge = 4.5 / (0.7 × 0.15) = 43 K vs 30 K
  → edge wafer ≈ 13 K warmer unless the edge zone is cooled
  → bow at the edge ≈ +1.7 nm without correction
```

The outer heater zone is therefore often run below the others, or the outer He zone at higher pressure. Wafer bow (Chapter 2) changes the edge gap and so the edge temperature from wafer to wafer.

---

## Summary and Key Takeaways

1. **Temperature acts through polymer.** +1 °C raises the bow by about 0.13 nm and the bottom CD by about 0.07 nm, with almost no change in the oxide rate.

2. **The helium gap carries the heat.** At 4.5 W/cm² and 0.15 W/cm²·K, the wafer sits about 30 K above the chuck surface.

3. **The wafer responds in a second; the chuck in a minute.** Power steps cause temperature transients that recipes must cancel.

4. **Zones flatten the bow.** Heater zones are the main radial bow knob; gas sets the bottom.

5. **Cryogenic operation is a different process.** Below about −40 °C, adsorbed HF and condensed species change the chemistry and require new hardware.

6. **The ring sets the edge tilt.** About 0.08° per 100 µm of ring wear. Without lift or bias compensation, tilt would exceed 0.1° within 40 RF hours.

---

## Study Questions

1. The He pressure is raised so that h_gap = 0.20 W/cm²·K. What chuck surface temperature holds the wafer at 20 °C? What happens to the wafer temperature if the chuck setpoint is unchanged?

2. The bias steps from 8 to 12 kW at the start of ME1, and the wafer heat flux rises from 3.0 to 4.5 W/cm². If the chuck surface responds with τ = 40 s, estimate the wafer temperature overshoot at t = 5 s and at t = 30 s.

3. The bow at r = 140 mm is 0.6 nm larger than at the centre, and the bottom CD there is 0.3 nm smaller. Using the sensitivities of Sections 8.1 and 7.5, find the zone temperature and edge O₂ changes that correct both.

4. A ring lift system adjusts in 25 µm increments. What is the maximum tilt between adjustments, and the corresponding bottom displacement?

5. Estimate the chuck surface temperature needed to hold the wafer at −60 °C under 4.5 W/cm² with h_gap = 0.15 W/cm²·K. What does this imply for the coolant?

---

**Next Chapter:** [Chapter 9: Electrodes, Rings, Walls, Seasoning & Defects](./09-electrodes-walls-defects.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
