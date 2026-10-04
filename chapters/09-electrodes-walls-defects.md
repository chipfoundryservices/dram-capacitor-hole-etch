# Chapter 9: Electrodes, Rings, Walls, Seasoning & Defects

## Overview

A capacitor hole chamber consumes itself. The silicon upper electrode is sputtered and etched by the plasma. The focus ring erodes under the full bias. The walls, the confinement rings, and the electrode collect fluorocarbon polymer, boron and phosphorus fluorides, and silicon compounds, and then release them. Every one of these changes moves the hole: the electrode's fluorine scavenging changes the polymer index, the ring's height changes the edge tilt, and the wall's state changes the radical balance of the next wafer. The particles and flakes these surfaces shed land on wafers and block holes.

This chapter follows the consumables through their life, describes waferless clean and seasoning, the particle and arcing defects of a high-power dielectric chamber, and the preventive-maintenance plan that keeps a fleet inside the hole specification.

**Learning Objectives:**
- Describe upper-electrode consumption and its effect on the polymer index and the bottom CD
- Compute drift in hole parameters over consumable life and the compensation needed
- Explain the role of the waferless autoclean and seasoning after maintenance
- Identify particle, flake, and arcing sources and their signatures on the wafer
- Build a preventive-maintenance schedule from consumable-life data

---

## 9.1 The Upper Electrode

### 9.1.1 Consumption

```
Reference electrode: single-crystal Si, 10 mm thick, ≈ 1000 gas holes,
                     0.5 mm diameter
Consumption: ≈ 20 µm per RF hour at full power (face recession)
Gas-hole widening: ≈ 1.5 µm per RF hour in diameter (holes erode faster
                   at their exits)
```

The face recession is small compared with the 10 mm thickness. The **gas holes** limit the life. As they widen, the pressure drop across the showerhead falls, the jet velocity into the gap falls, and gas flows more freely through the holes nearest the inlet. The radial gas distribution shifts.

### 9.1.2 Fluorine Scavenging

The silicon surface consumes fluorine (Si + 4F → SiF₄). As the electrode ages, its surface roughens and its effective area grows, so it consumes slightly more fluorine. Its temperature also drifts with the cooling path. Both raise the polymer index.

```
Illustrative drift over electrode life (no compensation):
  Electrode RF hours      0        200       400
  Π (main etch)           0.380    0.388     0.396
  Bottom CD               ref      −0.4 nm   −0.8 nm
  Not-open rate           ref      ×1.6      ×2.5
  Bow CD                  ref      −0.2 nm   −0.4 nm
```

APC compensates with an O₂ offset that grows with electrode RF hours (Chapter 15): about +1.5 sccm per 100 RF hours restores Π.

### 9.1.3 Electrode Material

Silicon electrodes of different resistivity and crystal orientation erode differently, and their sheath voltage depends on their resistivity. A new electrode from a different lot can shift the process. Electrodes are qualified by lot, and a chamber's first wafers after an electrode change are checked against its last wafers before it.

---

## 9.2 The Focus Ring and Edge Parts

Chapter 8 described ring erosion and edge tilt. Ring life also limits the edge **bottom CD** and **bow**, because the ring's surface area and temperature change the local radical and ion supply at the wafer edge.

```
Ring life (illustrative):
  Si ring: ≈ 3 µm per RF hour at the top surface; life ≈ 300 RF hours with
           lift compensation (limited by shape change, not height)
  SiC ring: ≈ 1.5 µm per RF hour; life ≈ 600 RF hours; higher cost,
            different edge chemistry (C from SiC)
```

The edge ring, the cover ring, and the chuck's edge are also eroded. Erosion of the chuck edge exposes the chuck to the plasma and limits its life. Replacing a chuck is a major maintenance event.

---

## 9.3 Walls and Polymer

### 9.3.1 Wall Deposits

Every wafer leaves fluorocarbon polymer, SiOₓFᵧ, and B/P compounds on the walls, the confinement rings, and the upper electrode periphery. The deposit thickens with each wafer.

```
Wall deposit growth (illustrative):
  ≈ 20–50 nm of fluorocarbon polymer per wafer on the confinement rings
  without clean
```

A thickening wall deposit consumes fewer fluorocarbon radicals than a clean wall and releases fluorine and carbon under ion bombardment. The plasma composition drifts from wafer to wafer, and the first wafer after a clean differs from the tenth.

### 9.3.2 Waferless Autoclean

```
Reference waferless autoclean (WAC), after every wafer:
  O₂ 1000 sccm (+ NF₃ 50 sccm), 200 mTorr, source 3 kW, no bias
  60 s, endpoint on CO (483 nm) and O (777 nm) emission stabilizing
```

The WAC removes the polymer laid down by the previous wafer, so every wafer starts with the same wall. It costs about 60 s per wafer, nearly 15% of the cycle (Chapter 5). Without it, the wall drift would move the bottom CD by about 0.5 nm over a 25-wafer lot.

### 9.3.3 Seasoning

After a wet clean or a parts change, the chamber walls are bare. A bare wall consumes radicals differently and holds a different charge. Seasoning wafers (blanket oxide or patterned dummies) run the reference recipe until the plasma reaches its steady wall state.

```
Seasoning after PM (illustrative):
  10–20 dummy wafers through the full recipe + WAC
  Pass criteria: OES ratios (CF₂/Ar, O/Ar, SiF/Ar) within 1% of the
                 pre-PM baseline; blanket rate within 1%
  Then qualification: patterned wafer, cross-section or HV-SEM for bow,
                 bottom CD, not-open; particle wafer
```

---

## 9.4 Particles, Flakes, and Arcing

### 9.4.1 Particle Sources

```
Source                             Signature on the wafer
────────────────────────────────────────────────────────────────────────────
Wall/confinement-ring flakes       large (≥ 100 nm) particles, often clustered
(polymer that cracks after many    near the edge; blocks dozens of holes each
cycles)
Upper-electrode particles (Si,     small particles across the wafer, increasing
eroded gas-hole rims)              late in electrode life
Plasma-suspended particles         drop when the plasma is turned off;
released at plasma off             "ring" pattern or centre cluster
Backside particles from the chuck  local defocus/arcing marks, clamping faults
```

A particle that lands on the mask before or during the etch masks every hole under it. A 100 nm particle covers about four holes; a 300 nm flake covers about 40. Each blocked hole becomes a not-open defect. Particles are therefore a direct contributor to the not-open rate of Chapter 12.

```
Not-open defects from particles (illustrative):
  10 adders ≥ 100 nm per wafer, average 10 blocked holes each
  → 100 not-open holes per wafer, over ≈ 150 dies → ≈ 0.7 per die
  Compared with the spec of ≈ 170 per die (1×10⁻⁸ per hole): small but
  clustered, and therefore harder to repair
```

### 9.4.2 Plasma-Off Management

At the end of the etch, particles trapped in the plasma's electrostatic potential well fall onto the wafer if the plasma is turned off abruptly. The recipe ends with a low-power, high-flow segment that sweeps particles toward the pump before the RF is turned off.

### 9.4.3 Arcing

At kilovolt bias, arcs can strike between the wafer edge and the ring, through pinholes in the chuck dielectric, or across contaminated surfaces. An arc melts a crater on the wafer or the part, sprays particles, and can damage dies over a large area. Arc detection monitors fast transients in the RF voltage and current, and the chamber is stopped on repeated events.

---

## 9.5 Preventive Maintenance

```
Reference PM schedule (illustrative):

  Event                         Interval           Duration   Requalification
  ─────────────────────────────────────────────────────────────────────────────
  Ring lift adjustment          automatic, ≤ 25 µm  —          none
  Focus ring change             300 RF h (Si)       4 h        season + qual
  Confinement rings wet clean   400 RF h            6 h        season + qual
  Upper electrode change        500 RF h            8 h        season + qual +
                                                               chamber matching
  Chuck change                  ≈ 3000 RF h         24 h       full requal
```

At 305 s of RF per wafer, 300 RF hours is about 3500 wafers. Aligning ring changes with confinement and electrode changes reduces the number of separate requalifications. Chambers in a fleet are staggered so that their consumables are not all new or all old at once, which keeps the fleet's average profile steady.

---

## Summary and Key Takeaways

1. **The electrode's gas holes limit its life.** They widen by about 1.5 µm per RF hour and shift the radial gas distribution.

2. **An aging electrode raises the polymer index.** Without compensation, the bottom CD falls by about 0.8 nm and the not-open rate rises by 2.5× over 400 RF hours.

3. **Clean after every wafer.** A 60 s WAC costs 15% of the cycle but holds the wall state steady.

4. **Season after every PM.** 10–20 dummies bring the walls to steady state, checked by OES ratios and blanket rate.

5. **Particles become not-opens.** A 300 nm flake on the mask blocks about 40 holes.

6. **Arcs are a high-bias failure mode.** They are detected by fast RF transients and stop the chamber.

---

## Study Questions

1. With Π rising by 0.004 per 100 RF hours, what O₂ offset per 100 RF hours restores Π in the reference main etch? Check against the 1.5 sccm per 100 RF hours quoted in the text.

2. A chamber skips the WAC to gain throughput. If the bottom CD drifts by −0.02 nm per wafer through a 25-wafer lot, what is the drift at the last wafer? Is it acceptable under the ±2 nm bottom CD spec?

3. How many 32 nm holes on a 45 nm hexagonal pitch lie under a circular particle 300 nm in diameter? (Use the area per hole of 1754 nm².)

4. A fab runs 20 chambers at 8.8 wafers/h with 80% availability. How many focus-ring changes per month does it perform?

5. A new upper-electrode lot with lower resistivity raises the upper sheath voltage. In which direction would you expect Π and the bottom CD to move? What measurement would confirm it?

---

**Next Chapter:** [Chapter 10: Bowing, Necking & Hole Profile Control](./10-bowing-necking-profile.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
