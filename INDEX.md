# Index: Book #29 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 22–30 hours for the complete book; 5–10 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the cell and its capacitance, the mold and mask, high-aspect-ratio hole physics, fluorocarbon chemistry |
| II | 5–9 | Hardware: high-power CCP chamber, low-frequency bias and waveforms, gas and multi-step recipes, temperature and edge tilt, consumables and defects |
| III | 10–14 | Phenomena: bow and neck, twisting and tilting, not-open holes and the pad, charging and mask integrity, advanced schemes |
| IV | 15–16 | Production: endpoint, metrology, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The DRAM Cell & the Role of the Capacitor Hole](./chapters/01-dram-cell-capacitor-architecture.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** Why is the capacitor a 1.6 µm hole, and what must the etch deliver?

**Key Topics:**
- Sense signal, the 8–10 fF target, and the 31 fA retention budget
- The 45 nm honeycomb, the 13 nm wall, and the 46% open fraction
- Capacitance from depth, average CD, and EOT (8.9 fF reference)
- The bottom-placement budget (|Δ| ≤ 9 nm) and the bottom CD as a contact
- The specification sheet

**Critical Equations:** ΔV_BL = (V_DD/2)C_s/(C_s + C_BL); C_s = ε₀·3.9·π·CD_avg·H_eff/EOT; overlap = 25 − |Δ|  
**Study Questions:** 6

---

### Chapter 2: [The Mold Stack, Support Layers & Hard Mask](./chapters/02-mold-stack-hard-mask.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration roles  
**Focus:** What does the etch inherit, and how long can it run?

**Key Topics:**
- Five-layer mold; why the lower oxide is doped
- Supports and pillar stability; the bottom stop
- ACL mask budget: blanket selectivity 5.5, effective 2.6, ≈ 730 nm left
- Double SADP vs EUV; CD families
- Stoney bow from the mask (≈ 260 µm unbalanced)

**Critical Equations:** Effective selectivity = H/ACL lost; κ = 6σ_f t_f(1 − ν)/(E t_s²)  
**Study Questions:** 6

---

### Chapter 3: [High-Aspect-Ratio Hole Etch Physics](./chapters/03-har-hole-etch-physics.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment/Research  
**Focus:** Why does the hole slow down, and how does CD become depth?

**Key Topics:**
- Ion flux and yield; 2.5 kW of ion power into the wafer
- IED and angle under a 7 kV sheath; acceptance angle ≈ 0.7°
- Clausing and Coburn–Winters transport
- ARDE: k = 0.020, bottom at 47%, ∂h/∂w = 15.2 nm/nm
- Charging and deflection; global loading by released oxygen

**Critical Equations:** ER = ER₀/(1 + kA); t = [h + kh²/(2w)]/ER₀; θ ≈ E⊥L/(2E_i)  
**Study Questions:** 6

---

### Chapter 4: [Fluorocarbon Chemistry, Polymer Balance & Selectivity](./chapters/04-fluorocarbon-chemistry-selectivity.md)
**Estimated Time:** 65 min | **Difficulty:** Intermediate | **Reading Level:** Process/Research  
**Focus:** How does chemistry balance protection against opening?

**Key Topics:**
- C₄F₆ vs C₄F₈; the polymerization index Π
- The steady-state film and selectivity to SiN, ACL, and W
- Support and BO chemistries
- O₂, NF₃, H; HF chemistry at low temperature

**Critical Equations:** Π = (C − O_feed − O_wafer)/F; ER ∝ exp(−t_fc/λ_E)  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [High-Power Capacitively Coupled Dielectric Chambers](./chapters/05-ccp-dielectric-chamber.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment  
**Key Topics:** CCP vs ICP; dual/triple frequency; power balance (2.5 of 14.5 kW to the wafer as ions); residence time 6.6 ms; fleet of 20 chambers; matching  
**Study Questions:** 5

### Chapter 6: [Low-Frequency Bias, Pulsing & Tailored Waveforms](./chapters/06-low-frequency-bias-pulsing.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Research  
**Key Topics:** τ_ion/τ_RF and IED width; pulsing and charge relaxation; tailored waveforms; DC superposition; voltage limits  
**Study Questions:** 5

### Chapter 7: [Gas Delivery, Polymer Control & Multi-Step Recipes](./chapters/07-gas-polymer-multistep.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process  
**Key Topics:** Pressure and dilution; the five-step recipe from G(h); O₂/NF₃ ramps; step transitions and notches; center/edge 2×2 tuning  
**Study Questions:** 5

### Chapter 8: [Wafer Temperature, Cryogenic Chucks & Radial Control](./chapters/08-temperature-cryo-radial.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** +0.13 nm bow per °C; heat balance (4.5 W/cm², 30 K He drop); time constants; zones; cryogenic chucks; ring wear and edge tilt (0.08° per 100 µm)  
**Study Questions:** 5

### Chapter 9: [Electrodes, Rings, Walls, Seasoning & Defects](./chapters/09-electrodes-walls-defects.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Equipment  
**Key Topics:** Electrode consumption and Π drift; ring life; WAC and seasoning; particles as not-opens; arcing; PM schedule  
**Study Questions:** 5

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Bowing, Necking & Hole Profile Control](./chapters/10-bowing-necking-profile.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration  
**Key Topics:** Reference profile; neck formation; reflection model Δz ≈ w/tan(2φ); wall at the bow and bridging; bow–bottom trade and the knobs that break it  
**Study Questions:** 5

### Chapter 11: [Twisting, Tilting & Hole Placement at the Bottom](./chapters/11-twisting-tilting-placement.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Key Topics:** Twisting as an instability; onset at A ≈ 28; constant and growing-angle models; edge and mask tilt; placement budget and tails; HV-SEM; correction  
**Study Questions:** 5

### Chapter 12: [Not-Open Holes, the Bottom Etch Stop & Landing-Pad Interface](./chapters/12-not-open-landing-pad.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Device  
**Key Topics:** Polymer stop and taper closure; nitride left per hole; gouge 2.5–7 nm; side punch; not-open budget (8×10⁻⁹); VC inspection  
**Study Questions:** 6

### Chapter 13: [Charging, Mask Integrity, Striation & Hole Distortion](./chapters/13-charging-mask-striation.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Key Topics:** Charge profile; wall RC ≈ 1 ms; mask evolution and facets; mask materials; striation; circularity; support webs  
**Study Questions:** 5

### Chapter 14: [Advanced Schemes — Cryogenic Etch, Taller Molds, Multi-Tier Holes, 4F² & 3D DRAM](./chapters/14-advanced-capacitor-schemes.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Key Topics:** Cryogenic HF (1.95 min); 2.0 µm molds (+36% time, 1.5–3× twist); two-tier holes; cylinder vs pillar; 4F² holes on a 30 nm grid; 3D DRAM  
**Study Questions:** 5

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Endpoint, Metrology & Advanced Process Control](./chapters/15-endpoint-metrology-apc.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Equipment  
**Key Topics:** OES by step; the CO knee; CD-SEM, HV-SEM, OCD, CD-SAXS, cross-section; electrical monitors; feed-forward; 2×2 feedback; consumable offsets  
**Study Questions:** 5

### Chapter 16: [Post-Etch Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Key Topics:** Ash and clean; TiN fill and voids; support opening and mold removal; bit-map signatures; repair budget; ≈ $25 per wafer vs the value of yield  
**Study Questions:** 5

---

## Appendices

| Appendix | Content |
|----------|---------|
| [A](./appendices/A-material-properties.md) | Mold, mask, pad, dielectric, and chamber materials; constants |
| [B](./appendices/B-chemistry-reaction-data.md) | Gases, radicals, reactions, product volatility, OES lines, Π quick reference |
| [C](./appendices/C-standard-procedures.md) | Depth series, PM qualification, ring calibration, HV-SEM twist, VC monitoring, WAC |
| [D](./appendices/D-process-windows.md) | Reference recipe, windows, sensitivity table, ARDE, capacitance, and tilt lookups |
| [E](./appendices/E-hole-geometry-capacitance-calculations.md) | All closed-form models with reference values |
| [F](./appendices/F-endpoint-metrology-reference.md) | Endpoint signals, metrology methods, sampling plan, pitfalls |
| [G](./appendices/G-troubleshooting-guide.md) | Symptom-driven troubleshooting |
| [Glossary](./GLOSSARY.md) | Terminology |

---

## Reading Paths by Role

### Process Engineer (≈ 9 hours)
Chapters 1, 3, 4, 7, 10, 11, 12 → Appendices D, G

### Equipment Engineer (≈ 8 hours)
Chapters 3, 5, 6, 7, 8, 9, 15 → Appendices A, C

### Integration Engineer (≈ 8 hours)
Chapters 1, 2, 10, 11, 12, 14, 16 → Appendix E

### Device Engineer (≈ 5 hours)
Chapters 1, 10, 12, 16

### Researcher (≈ 10 hours)
Chapters 3, 4, 6, 10, 11, 13, 14 → Appendices B, E

---

## Cross-Reference Map to Other Books

| Book | Title | Used in |
|------|-------|---------|
| #1–5 | Plasma Physics & Chemistry Fundamentals | Ch. 3, 6 (sheaths, IED, transport) |
| #6–10 | Dielectric Etch & Fluorocarbon Chemistry | Ch. 4, 7 |
| #11–15 | Advanced Plasma Engineering | Ch. 5–9, 15 |
| #23 | Contact Hole Etch | Ch. 3, 12 |
| #24 | 3D NAND Slit Etch | Ch. 14 |
| #25 | 3D NAND High-Aspect-Ratio Oxide/Nitride Stack Etch | Ch. 3, 10, 11, 14 |
| #26 | DRAM Isolation Trench Etch | Ch. 1 |
| #27 | DRAM Word-Line Conductor Etch | Ch. 1 |
| Companion | DRAM Bit-Line Contact Etch; DRAM Bit-Line Stack Etch | Ch. 1, 12 |
| Companion | Carbon Hard Mask Etch | Ch. 2, 13 |
| Companion | Silicon Nitride Etch | Ch. 2, 7 |

---

## Study Questions Summary

**Total Study Questions:** 85 (5–6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Signal and capacitance, wall and pitch, mask budget, ARDE and CD sensitivity, polymer index, residence time and power, pulsing and charge, step times, heat and tilt, consumable drift, bow geometry, twist growth, gouge and side punch, mask facets, cryogenic and taller molds, APC, cost

Examples:
- Compute C_s from the hole profile and support loss
- Compute the effective mask selectivity from the step table
- Fit ER₀ and k from a depth series
- Show why a 1 nm smaller hole ends 15 nm shallower
- Derive the five step times from G(h)
- Solve the 2×2 edge tuning for O₂ and temperature
- Place the bow from the neck taper
- Compare twist for 1.6 and 2.0 µm molds
- Compute gouge and side punch for early and late holes
- Compare the etch cost with the value of 1% yield

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-04  
**Next:** Begin [Chapter 1: The DRAM Cell & the Role of the Capacitor Hole](./chapters/01-dram-cell-capacitor-architecture.md)
