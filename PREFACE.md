# Preface: The Etch That Builds the Capacitor

## Why This Book Exists

Most holes in a chip are wires. A contact hole carries current from one layer to the next, and it only has to be open and land on its target. The DRAM storage-node hole is different. It is not a wire. It is a mould for the capacitor that holds the bit, and the charge the cell can store depends on its sidewall area. The hole has to be as deep as the mold allows, as wide as its neighbours allow, straight from top to bottom, and open onto a landing pad hidden 1.6 µm below the mask. There are about seventeen billion such holes on a 16 Gb die. One hole that fails in any of these ways is one cell that fails.

DRAM capacitor hole etch has been a defining process since the capacitor moved above the bit line and grew upward. Each generation shrinks the cell footprint, but the sense amplifier still needs roughly the same charge. The capacitor has therefore grown taller as it has grown thinner. In the 1990s the aspect ratio was about 10:1. In the reference 1b-class process of this book the hole is 1.6 µm deep and 28 nm wide on average, an aspect ratio near 57:1 at its average diameter. The holes sit on a 45 nm hexagonal lattice. The oxide between two neighbours is 13 nm at the top and must stay above about 6 nm all the way down.

The method, a fluorocarbon oxide etch through a carbon mask, looks routine. It asks a great deal of the plasma:

1. **Depth against a falling rate.** The etch rate at the bottom of a 50:1 hole is less than half the rate at the top. Ions lose their way, neutrals stick to the walls before they reach the bottom, and polymer precursors pile up where the ions are weakest. The last 500 nm of depth takes two-thirds as long as the first 1100 nm.

2. **Diameter that becomes depth.** At fixed time, a hole 1 nm narrower ends about 15 nm shallower. The honeycomb patterning puts different holes in slightly different CD families, so the etch has to overetch enough to open the smallest.

3. **A straight wall under a hot sheath.** Ions arrive with several kiloelectronvolts. Those that strike the mask facet or are deflected by charge on the wall hit the sidewall below the neck and carve a bow. The wall between holes is so thin that a few nanometres of bow on each side shorts two capacitors.

4. **A bottom that must not wander.** A hole that bends by a fraction of a degree drifts sideways by tens of nanometres over its depth. The landing pad is only 26 nm wide. Twisting and tilting are placement errors the lithography tool cannot correct.

5. **A mask that must last.** About 1.6 µm of oxide and nitride must be removed through 1.4 µm of amorphous carbon. The selectivity is about four. Where the mask thins or faceted shoulders form, the top of the hole widens and the bow below it grows.

6. **Every hole open.** At the bottom, the etch must clear a 20 nm silicon nitride stop and touch tungsten without driving into it. A hole that stops in the nitride is a dead cell. The fab tolerates not-open defects at a rate below one in ten million holes.

This book treats the capacitor hole as a **three-dimensional structure built by the plasma**, not as a contact hole that happens to be deep.

---

## Unique Aspects of DRAM Capacitor Hole Etch

### 1. The Feature Is the Device

The capacitor is the hole. Its depth, average diameter, and profile set the cell capacitance, and its sidewall becomes the electrode surface. A recipe change that shifts the average diameter by 1 nm changes capacitance by about 3.5%.

### 2. A Lattice, Not a Feature

The holes are not isolated. They form a dense honeycomb, and every hole has six neighbours at 45 nm. Bridging, support-layer integrity, and the mechanical strength of the mold after the oxide is removed depend on the wall between holes, not on the hole alone.

### 3. The Mold Has Layers

The mold is not a single oxide. Nitride supports at the top and middle hold up the tall electrodes after the oxide is removed. Each support is a different material, so the etch changes rate and polymer balance as it passes through. Steps, notches, and bow peaks often sit at these interfaces.

### 4. The Highest Power in the Fab

Capacitor hole etch runs at bias powers of 10–20 kW and sheath voltages of several kilovolts. Electrodes, rings, and chuck surfaces wear at rates far above other etch steps, and the hole profile follows the hardware as it ages.

### 5. Yield Lives at the Bottom

Capacitance, bow, and twisting are statistical properties of billions of holes. Not-open holes are rare events in a tail. Production control must watch both: the mean profile from scatterometry and cross-sections, and the parts-per-billion tail from electrical tests and high-voltage SEM.

---

## Why This Book Is Organized This Way

Book #29 follows the same four-part structure as Books #19–27:

**Part I: Fundamentals (Chapters 1–4)**
- Why the capacitor is a tall hole and what sets its size, how the mold and mask are built, the physics of high-aspect-ratio hole etch, and the fluorocarbon chemistry that balances etch and protection

**Part II: Hardware (Chapters 5–9)**
- The high-power CCP chambers, low-frequency and tailored bias, gas and recipe structure, temperature and edge control, and the wear and wall management that let one chamber etch billions of straight holes across a wafer

**Part III: Phenomena (Chapters 10–14)**
- Bowing and necking, twisting and tilting, not-open holes and the landing pad, charging and mask integrity, and advanced capacitor schemes

**Part IV: Production (Chapters 15–16)**
- Endpoint, metrology, APC, the integration steps that use the hole, yield, and cost

### Reading Paths

**Process Engineers:** Chapters 3, 4, 7, 10, 11, 12  
→ Recipe design, ARDE, polymer balance, bow, twisting, bottom opening

**Equipment Engineers:** Chapters 5–9, 15  
→ Reactor selection, bias and waveforms, gas and temperature control, consumable wear, endpoint hardware

**Integration Engineers:** Chapters 1, 2, 11, 12, 14, 16  
→ Capacitance budget, mold design, placement budget, landing pad, multi-tier holes, downstream steps

**Device Engineers:** Chapters 1, 10, 12, 16  
→ How hole errors become low capacitance, shorts, opens, and retention failures

**Researchers:** Chapters 3, 4, 6, 13, 14  
→ HAR transport and charging, fluorocarbon and HF chemistry, tailored waveforms, cryogenic etch

---

## Key Questions This Book Answers

1. **Why must the capacitor hole be 1.6 µm deep, and how much capacitance does each nanometre of depth and diameter buy?**
2. **Why does the etch slow down as the hole deepens, and how much does hole CD change the final depth?**
3. **Where does the bow come from, and how close can it come to the neighbouring hole?**
4. **Why do holes twist and tilt, and how far can the bottom move before it misses the landing pad?**
5. **What closes a hole in the last 300 nm, and how is the not-open rate held below one in ten million?**
6. **How long does the carbon mask last, and how does its shape change the profile below it?**
7. **How is the arrival at the bottom of a 50:1 hole detected, and how is the hole measured?**
8. **How do cryogenic etch, taller molds, two-tier holes, 4F² vertical-channel cells, and 3D DRAM change the capacitor etch?**
9. **What does the capacitor hole etch cost per wafer, and how does that compare with what it costs when it goes wrong?**

---

## How to Read This Book

**Complete study (2–3 weeks):** Read Part I closely, then work through Parts II and III in order. Finish with Part IV.

**Focused study (3–5 days):** Read Chapters 1 and 3, then follow the reading path for your role.

**Reference mode:** Go straight to the chapter you need. Use the INDEX, GLOSSARY, and the Appendix G troubleshooting guide.

**Every chapter includes:**
- Learning objectives
- Quantitative models with worked numerical examples
- Representative production values, labelled as illustrative where appropriate
- Summary and key takeaways
- Study questions

**Appendices provide:**
- A: Mold, mask, pad, and chamber material properties
- B: Etch chemistry and reaction data
- C: Standard operating procedures
- D: Process windows and lookup tables
- E: Hole geometry, transport, placement, and capacitance calculations
- F: Endpoint and metrology reference
- G: Troubleshooting guide

---

## A Note on Data and Depth

The relationships in this book (sheath physics, ion angular distributions, free-molecular transport, fluorocarbon surface kinetics, surface charging, parallel-plate capacitance) are well established in the literature. The specific numbers in recipes, tables, and worked examples are **representative**. They are chosen to be physically consistent and close to typical practice, but they are not qualified conditions for any particular tool, layout, or node. Where a value is illustrative, the text says so and shows the arithmetic, so readers can repeat the analysis with their own measurements.

Throughout the book, a **reference process** ties the examples together:

```
Reference device:      1b-class DRAM, 6F² cell, buried-channel array transistor;
                       word-line pitch 34 nm, bit-line pitch 51 nm
                       (F = 17 nm, cell area 6F² = 1734 nm²)
Reference layout:      storage-node holes on a hexagonal lattice, pitch p = 45 nm
                       (one hole per cell: (√3/2)p² = 1754 nm² ≈ 6F²)
Reference hole:        top CD 32 nm (at the top of the mold), average CD 28 nm,
                       bottom CD 24 nm at the pad; wall at top 13 nm;
                       maximum bow CD 34 nm (spec); bottom CD ≥ 20 nm (spec)
Reference mold:        H = 1.60 µm total:
                         top SiN support      120 nm
                         upper oxide (TEOS)   650 nm
                         middle SiN support    50 nm
                         lower oxide (BPSG)   760 nm
                         bottom SiN stop       20 nm
Reference mask:        amorphous carbon (ACL) 1.40 µm + SiON 40 nm;
                       ≥ 500 nm ACL must remain at the end of the etch
Reference pad:         W landing pad, 26 nm wide at its top, on the storage-node
                       contact; pad gouge ≤ 10 nm
Reference capacitor:   single-sided TiN pillar, ZrO₂/Al₂O₃/ZrO₂ dielectric,
                       EOT 0.50 nm → C_s ≈ 9.7 fF for the full sidewall,
                       ≈ 8.9 fF after the supports and bottom stop
Reference etch:        dual-frequency CCP, 40 MHz source 2.5 kW, 400 kHz bias
                       12 kW (V_pp ≈ 7 kV, mean ion energy ≈ 3 keV);
                       20 mTorr; main etch C₄F₆/C₄F₈/O₂/Ar; wafer 20 °C;
                       open-area oxide rate ER₀ = 600 nm/min;
                       hole ARDE coefficient k = 0.020 (w = 28 nm)
                       → 4.2 min for 1.6 µm of TEOS-equivalent depth;
                       five-step recipe (top SiN, upper oxide, middle SiN,
                       lower oxide + overetch, bottom-stop open) ≈ 305 s
```

We assume you know basic plasma physics and the general behaviour of fluorocarbon oxide etch from earlier books. We do **not** assume you know DRAM cell architecture, honeycomb patterning, the mechanics of nitride-supported molds, the physics of hole charging at kilovolt sheath voltages, or the link between hole profile and cell capacitance.

---

## Organization of This Repository

1. **README.md**: overview, scope, file structure, cross-references
2. **PREFACE.md**: this document
3. **INDEX.md**: detailed chapter outline, reading paths, estimated times
4. **chapters/**: Chapters 1–16
5. **appendices/**: Appendices A–G
6. **GLOSSARY.md**: technical terminology

---

## Acknowledgments & Scope

Book #29 is part of the **ChipFoundryServices Technical Series**. It draws on:

- The published plasma etch literature on high-aspect-ratio contact and capacitor etch, fluorocarbon chemistry, ARDE, charging, bowing, twisting, and pulsed plasmas
- Classical results on free-molecular flow through tubes (Knudsen, Clausing) and on ion transport in collisionless and collisional sheaths
- Published descriptions of DRAM capacitor integration, support structures, and high-k dielectrics
- Representative industrial practice for DRAM storage-node modules
- The earlier books in this series, especially Books #23, #25, and #26

It is a **technical reference for professionals**. Background in plasma processing is assumed.

---

## Final Thought

A DRAM capacitor is a hole 28 nm wide and 1.6 µm deep, repeated seventeen billion times on a lattice so tight that the walls between the holes are thinner than the holes. The etch decides how deep it is, how straight, and whether it reaches the pad.

Mastering capacitor hole etch means seeing that **the hole is the capacitor, the depth slows the etch that makes it, and every ion that strays from vertical ends up in a neighbour's wall or a missed landing pad**. This book is meant to build that understanding.

---

**Welcome to Book #29: DRAM Capacitor Hole Etch — High-Aspect-Ratio Storage-Node Etch Through the Mold Stack for 6F² DRAM.**
