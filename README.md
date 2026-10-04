# Book #29: DRAM Capacitor Hole Etch — High-Aspect-Ratio Storage-Node Etch Through the Mold Stack for 6F² DRAM

## Overview

**Book #29** is a technical reference on **DRAM capacitor hole etch**, also called storage-node (SN) hole etch or mold etch. This plasma etch cuts a hole for every cell, about seventeen billion of them on a 16 Gb die, through a mold of silicon oxide and silicon nitride about 1.6 µm thick. Each hole lands on a storage-node landing pad no wider than itself. In the reference 1b-class 6F² array, the holes sit on a hexagonal lattice with a 45 nm pitch. Each hole opens at 32 nm, must still be at least 22 nm wide at the bottom, and keeps a wall of oxide only 13 nm thick between itself and its six neighbours. The aspect ratio is about 50:1. The hole later receives a TiN bottom electrode, a high-k dielectric, and a top plate. Its depth and diameter set the cell capacitance, roughly 10 fF.

The etch is one of the most demanding in semiconductor manufacturing. The hole has to be **deep**, because capacitance scales with sidewall area and the cell footprint keeps shrinking. It has to be **straight**, because a 2 nm bow at mid-depth turns the 13 nm wall into a 9 nm wall, and when two neighbouring holes bow toward each other the electrodes short. It has to be **vertical and in place**, because a hole that twists or tilts by 1° moves its bottom 28 nm sideways and misses a landing pad 26 nm wide. It has to be **open**, because a single hole that stops in the bottom nitride is a dead cell, and repair redundancy covers only a few thousand of them. And the hard mask has to **outlast** the etch: about 1.6 µm of oxide and nitride must come out before roughly 1.4 µm of amorphous carbon is gone.

The basic method is easy to state. Pattern a honeycomb of holes into a thick amorphous-carbon hard mask. Etch through the top nitride support, the upper oxide, the middle nitride support, the lower oxide, and the bottom etch-stop nitride in a fluorocarbon plasma. Use a capacitively coupled chamber with several kilovolts of low-frequency bias, so that ions arrive nearly vertical and with enough energy to reach the bottom of a 50:1 hole. Balance polymer deposition so the sidewall is protected without closing the hole. Stop on the tungsten landing pad. **Every one of seventeen billion holes must be open, straight, on its pad, and separated from its neighbours.**

Doing it in production is hard. The etch rate at the bottom of the hole falls by more than half as the hole deepens, so the last third of the depth takes about 70% as long as the first two-thirds. Every nanometre of hole diameter becomes about 15 nm of depth at fixed time. Ions that are deflected by charge on the hole walls or scattered off the mask facet strike the sidewall below the neck and produce the bow. Small asymmetries in the mask, in polymer deposition, or in charging bend the hole sideways, and those bends grow with depth. The chamber runs at the highest bias power of any etch in the fab. Its electrodes, focus ring, and walls wear and change over hundreds of RF hours, and the hole moves with them. This book covers the physics, chemistry, equipment, and production engineering that make DRAM capacitor hole etch work.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing high-aspect-ratio hole recipes; controlling etch depth, bottom CD, bowing, twisting, not-open defects, mask budget, and landing-pad gouging
- **Equipment Engineers**: specifying high-power dual- and triple-frequency capacitively coupled dielectric chambers, low-frequency and tailored-waveform bias, cryogenic and low-temperature chucks, and focus-ring compensation; managing electrode wear, polymer walls, seasoning, and particles
- **Integration Engineers**: setting mold height, support-layer positions, hole CD, and landing-pad size against capacitance, bridging, and overlay; designing the hard-mask, etch, clean, and electrode sequence
- **Device Engineers**: understanding how hole errors become low cell capacitance, bit failures, electrode shorts, leakage, and retention tails
- **Researchers**: studying ion transport and charging in 50:1 to 100:1 holes, cryogenic and hydrogen-fluoride chemistries, pulsed and tailored bias, and capacitor holes for 4F² vertical-channel and 3D DRAM

The material assumes a working knowledge of plasma physics (Books #1–5), fluorocarbon dielectric etch (Books #6–10), and advanced plasma engineering (Books #11–15). Book #25 (3D NAND High-Aspect-Ratio Oxide/Nitride Stack Etch) covers the closest relative of this etch, a deeper hole through alternating oxide and nitride. Book #26 (DRAM Isolation Trench Etch) and Book #27 (DRAM Word-Line Conductor Etch) describe the 6F² array beneath the capacitor. The companion volumes *DRAM Bit-Line Contact Etch*, *Carbon Hard Mask Etch*, and *Contact Hole Etch* cover the landing-pad contact, the mask open, and lower-aspect-ratio oxide holes.

---

## Technical Scope

### Core Concepts Covered

**Architecture & Geometry:**
- The 1T1C cell and why the capacitor is a tall cylinder or pillar
- The honeycomb storage-node layout on a hexagonal lattice; pitch, CD, and wall thickness
- Cell capacitance from hole depth, diameter, and dielectric EOT
- Landing pads, storage-node contacts, and the overlay budget at the hole bottom

**The Incoming Stack:**
- The mold: top, middle, and bottom silicon nitride supports; doped and undoped oxide layers
- The amorphous-carbon hard mask, its SiON cap, and the mask-open etch
- Honeycomb patterning by EUV or by double self-aligned double patterning
- Incoming stress, wafer bow, and mold film variation

**Etch Physics & Chemistry:**
- Ion energy and angular distributions under a multi-kilovolt sheath
- Neutral and ion transport in a 50:1 hole; ARDE and the time-to-depth curve
- Surface charging of the hole and ion deflection
- Fluorocarbon chemistry: C₄F₆, C₄F₈, CH₂F₂, O₂, Ar, NF₃; polymer balance; oxide, nitride, and carbon selectivity
- Hydrogen-fluoride and cryogenic chemistries

**Equipment Design:**
- High-power dual- and triple-frequency capacitively coupled chambers
- Low-frequency bias, pulsing, and tailored voltage waveforms
- Gas delivery, polymer control, and multi-step recipes through support layers
- Electrostatic chucks for high-power and low-temperature operation; radial control and focus rings
- Electrode, ring, and wall wear; seasoning; particles

**Process Phenomena:**
- Bowing, necking, and the hole profile; top CD, bow CD, bottom CD
- Twisting, tilting, and hole placement at the bottom
- Not-open holes, etch stop, the bottom nitride, and landing-pad gouging
- Charging, mask faceting, striation, and hole distortion
- Advanced schemes: cryogenic etch, mold stacks taller than 2 µm, multi-tier holes, and capacitors for 4F² and 3D DRAM

**Production Integration:**
- Endpoint from the bottom of a 50:1 hole; depth by time and APC
- CD-SEM, high-voltage SEM, OCD, X-ray scatterometry, and electrical monitors
- Post-etch strip, clean, electrode deposition, and mold removal as customers
- Yield signatures, throughput, and cost of ownership

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Capacitor structures:** single-sided TiN pillar capacitors in a nitride-supported mold (primary focus); double-sided cylinders; multi-tier stacked molds
- **Process sequence:** Capacitor hole etch follows the landing-pad module and the mold and hard-mask depositions, and the hole patterning and mask open. It comes before the strip and clean, bottom-electrode deposition, support opening, mold removal, dielectric, and plate
- **Manufacturing scale:** 300 mm wafers, one capacitor hole etch per wafer, about 5 min of etch inside a 7–8 min chamber cycle, a large fleet of high-power dielectric chambers per DRAM fab

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The DRAM Cell & the Role of the Capacitor Hole**
- The 1T1C cell, the sense signal, and the capacitance target
- The honeycomb layout and the geometry of a capacitor hole
- Capacitance from depth, diameter, and EOT
- Where the hole etch sits in the flow, and its specification sheet

**Chapter 2: The Mold Stack, Support Layers & Hard Mask**
- Oxide layers, nitride supports, and the bottom etch stop
- The amorphous-carbon hard mask and the mask budget
- Honeycomb patterning and the mask open
- Stress, wafer bow, and incoming variation

**Chapter 3: High-Aspect-Ratio Hole Etch Physics**
- Ion energy and angle at the hole entrance
- Neutral and ion transport to the bottom of a 50:1 hole
- ARDE, the time-to-depth curve, and its CD sensitivity
- Charging of the hole and ion deflection

**Chapter 4: Fluorocarbon Chemistry, Polymer Balance & Selectivity**
- C₄F₆, C₄F₈, and hydrofluorocarbons; the CFₓ and F balance
- Polymer at the hole bottom, on the sidewall, and on the mask
- Selectivity to carbon, nitride, and the landing pad
- Oxygen, NF₃, and hydrogen; HF-based chemistry

### Part II: Hardware Design (5 Chapters)

**Chapter 5: High-Power Capacitively Coupled Dielectric Chambers**
- Why capacitor holes are etched in CCP chambers
- Dual and triple frequency; power and sheath voltage
- Pumping, residence time, and polymer precursors
- Throughput, fleet size, and chamber matching

**Chapter 6: Low-Frequency Bias, Pulsing & Tailored Waveforms**
- Ion energy distributions at 400 kHz to 2 MHz
- Bias pulsing and charge relaxation
- Tailored and DC-augmented waveforms
- Power limits, arcing, and component stress

**Chapter 7: Gas Delivery, Polymer Control & Multi-Step Recipes**
- Pressure, flow, and residence time at high power
- Recipe steps through the top support, oxides, middle support, and bottom stop
- Ramped and switched gas chemistry with depth
- Center/edge gas tuning

**Chapter 8: Wafer Temperature, Cryogenic Chucks & Radial Control**
- Temperature dependence of polymer, etch rate, and selectivity
- Heat load at 15 kW and multi-zone chucks
- Low-temperature and cryogenic operation
- Focus rings, edge tilt, and radial hole control

**Chapter 9: Electrodes, Rings, Walls, Seasoning & Defects**
- Upper-electrode and focus-ring wear and their effect on the hole
- Polymer walls, dry clean, and seasoning
- Particles, flakes, and arcing
- Preventive maintenance and RF-hour life

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Bowing, Necking & Hole Profile Control**
- How a bow forms: scattered and deflected ions
- Necking at the mask and the bow-neck tradeoff
- The bow budget and hole-to-hole bridging
- Bow control by chemistry, power, and steps

**Chapter 11: Twisting, Tilting & Hole Placement at the Bottom**
- Twisting from asymmetric mask, polymer, and charge
- Tilting from the sheath at the wafer edge
- The bottom-placement budget and landing-pad overlay
- Detection and correction

**Chapter 12: Not-Open Holes, the Bottom Etch Stop & Landing-Pad Interface**
- Etch stop by polymer and charge in the last 300 nm
- Bottom CD and the minimum contact area
- Opening the bottom nitride; gouging the pad
- The defect density of not-open holes and repair

**Chapter 13: Charging, Mask Integrity, Striation & Hole Distortion**
- Charge on the hole wall and at the bottom
- Mask erosion, facets, and the remaining mask
- Striation, circularity, and hole distortion
- Support-layer roughness and bridging

**Chapter 14: Advanced Schemes — Cryogenic Etch, Taller Molds, Multi-Tier Holes, 4F² & 3D DRAM**
- Cryogenic and HF-based hole etch
- Molds beyond 2 µm and aspect ratios beyond 70:1
- Two-tier holes and their alignment
- Capacitors for 4F² vertical-channel and 3D DRAM

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Endpoint, Metrology & Advanced Process Control**
- Endpoint from the bottom of a 50:1 hole; depth by time
- Top, bottom, and bow CD; HV-SEM, OCD, and X-ray metrology
- Electrical monitors of capacitance, shorts, and opens
- Feed-forward and feedback APC

**Chapter 16: Post-Etch Integration, Yield & Cost of Ownership**
- Strip, clean, and queue time
- Electrode deposition, support opening, and mold removal
- Defect modes and yield signatures
- Throughput, consumables, and cost-of-ownership modeling

---

## Key Technical Themes

1. **Area is capacitance.** The cell holds about 10 fF because the hole is 1.6 µm deep. Every 100 nm of depth is about 0.6 fF, and every nanometre of average diameter is about 0.35 fF.
2. **The hole slows itself down.** At 50:1 the bottom etches at less than half the open-area rate. A 1 nm smaller hole ends 15 nm shallower at the same time.
3. **The wall is 13 nm.** Holes on a 45 nm hexagonal pitch leave thin oxide between them. A bow of a few nanometres on each side, in two neighbouring holes, bridges them.
4. **A small angle is a large miss.** A hole bent by 1° at mid-depth lands 14 nm off centre. Twisting and tilting are placement errors that overlay metrology cannot see.
5. **One closed hole is one dead cell.** Not-open holes must stay well below one per million. The last 10% of the depth decides yield.
6. **The mask is a consumable.** About 1.6 µm of dielectric must be removed with selectivity to carbon of only about 4. The mask that remains, and its shape, sets the top of the hole and the rate of the bow.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheath physics, ion energy and angular distributions, radical generation and transport
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): fluorocarbon polymer, oxide/nitride selectivity, CCP dielectric etch
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, pulsing, gas delivery, temperature control, endpoint detection
- **Book #23** (Contact Hole Etch): lower-aspect-ratio oxide holes and their landing
- **Book #24** (3D NAND Slit Etch): high-aspect-ratio slots through oxide/nitride
- **Book #25** (3D NAND High-Aspect-Ratio Oxide/Nitride Stack Etch): the closest relative of this etch; channel holes at 60:1 and beyond
- **Book #26** (DRAM Isolation Trench Etch): the 6F² cell and the active areas
- **Book #27** (DRAM Word-Line Conductor Etch): the buried word line and the gate edge under the storage-node junction
- **Companion volumes:** *DRAM Bit-Line Contact Etch*, *DRAM Bit-Line Stack Etch*, which form the bit line that the storage-node contacts pass between; *Carbon Hard Mask Etch*, which covers the mask open; *Silicon Nitride Etch*, which covers the supports

Capacitor hole etch takes the oxide contact hole of Book #23 and asks it to be thirty times deeper, on a pitch closer than any other hole in the chip, seventeen billion times over.

---

## File Organization

```
dram-capacitor-hole-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-dram-cell-capacitor-architecture.md
│   ├── 02-mold-stack-hard-mask.md
│   ├── 03-har-hole-etch-physics.md
│   ├── 04-fluorocarbon-chemistry-selectivity.md
│   ├── 05-ccp-dielectric-chamber.md
│   ├── 06-low-frequency-bias-pulsing.md
│   ├── 07-gas-polymer-multistep.md
│   ├── 08-temperature-cryo-radial.md
│   ├── 09-electrodes-walls-defects.md
│   ├── 10-bowing-necking-profile.md
│   ├── 11-twisting-tilting-placement.md
│   ├── 12-not-open-landing-pad.md
│   ├── 13-charging-mask-striation.md
│   ├── 14-advanced-capacitor-schemes.md
│   ├── 15-endpoint-metrology-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-reaction-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-hole-geometry-capacitance-calculations.md
    ├── F-endpoint-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Storage-node capacitor hole etch for 6F² DRAM through nitride-supported oxide molds (primary focus)  
✅ The mold, support layers, and hard mask as inputs to the etch  
✅ Cryogenic, HF-based, and tailored-waveform approaches; taller and multi-tier molds  
✅ Equipment design, chamber control, and production integration  
✅ The processes that use the hole (strip, electrode, support open, mold removal) as customers of the etch  
✅ Capacitance, shorts, opens, retention, and cost of ownership  

### What This Book Does NOT Cover
❌ The amorphous-carbon mask-open etch in detail (see *Carbon Hard Mask Etch*)  
❌ Landing-pad, storage-node contact, and bit-line etches, beyond what the hole lands on  
❌ High-k dielectric and electrode deposition chemistry in detail  
❌ 3D NAND channel holes, except as comparison (see Book #25)  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established plasma physics, published literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect: a 1b-class 6F² array (F = 17 nm, cell area 1734 nm²), storage-node holes on a 45 nm hexagonal pitch, 32 nm top CD, 28 nm average CD, 24 nm bottom CD at the pad, a 1.60 µm mold (120 nm top SiN support, 650 nm upper oxide, 50 nm middle SiN support, 760 nm lower oxide, 20 nm bottom SiN etch stop), a 1.40 µm amorphous-carbon mask, a W landing pad 26 nm wide, and a ZrO₂-based dielectric with EOT 0.50 nm. The ARDE, bow, placement, and capacitance numbers in Chapters 1, 3, 10, 11, and 12 come from closed-form models written out in Appendix E. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #29 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-dram-cell-capacitor-architecture.md)**: The DRAM Cell & the Role of the Capacitor Hole

---

**Book #29 Version:** 1.0  
**Last Updated:** 2026-10-04  
**Series:** ChipFoundryServices Technical Series
