# Chapter 4: Fluorocarbon Chemistry, Polymer Balance & Selectivity

## Overview

Every useful oxide etch in a fluorocarbon plasma is a balance between deposition and removal. The plasma makes fluorocarbon fragments that deposit as a thin polymer film on every surface. Ions drive reactions in the film that etch whatever lies under it. On oxide, the oxygen in the substrate helps burn the film away, so the film stays thin and the oxide etches. On nitride and carbon, there is less or no oxygen to help, so the film grows thicker and the etch slows. That difference is selectivity. On the sidewall of the hole, where ions are few, the film protects the wall. At the bottom, where ions are many but the neutral supply is thin, the film must be just thick enough to supply fluorine and no thicker.

This chapter develops the chemistry for the capacitor hole: the fluorocarbon gases and the fragments they make, the steady-state film and the rate it allows, the selectivity to the carbon mask, to nitride, and to tungsten, the roles of oxygen, NF₃, and hydrogen, and the hydrogen-fluoride chemistries that are replacing part of the fluorocarbon at the newest nodes.

**Learning Objectives:**
- Compare C₄F₆, C₄F₈, CH₂F₂, and CHF₃ by C/F ratio and the fragments they make
- Compute a polymerization index for a gas mix, including oxygen from the wafer
- Use the steady-state film model to explain oxide, nitride, and carbon etch rates
- Explain why selectivity to the mask falls at the hole top and rises at the bottom
- Choose chemistries for the support layers, the bottom stop, and the landing on tungsten
- Describe how HF-containing chemistry changes the etch at low temperature

---

## 4.1 The Gases

### 4.1.1 Feed Gases and Their Fragments

```
Gas        C/F    Main fragments in a dense plasma (illustrative)
──────────────────────────────────────────────────────────────────────
CF₄        0.25   CF₃, CF₂, F (fluorine-rich; little polymer)
CHF₃       0.33   CF₂, CF₃, HF, H (moderate polymer; nitride-capable)
C₄F₈       0.50   CF₂ (dominant), C₂F₄, CF, F
CH₂F₂      0.50   CHF, CF₂, HF, H (polymerizing; strongly nitride-capable)
C₄F₆       0.67   C₃F₃, C₂F₂, CF, CF₂ (highly polymerizing; few F)
C₅F₈       0.63   similar to C₄F₆
NF₃        —      N, F (fluorine source; polymer cleaner)
O₂         —      O (polymer remover); CO, COF₂ products
Ar         —      Ar⁺ (the main ion; dilutes)
```

The ions are mostly Ar⁺ (often 70–90% of the ion flux in a heavily diluted mix). Fluorocarbon ions such as CF₃⁺ and C₂F₄⁺ make up the rest. At kilovolt energies a fluorocarbon ion fragments on impact and delivers its carbon and fluorine directly into the film, which matters at the bottom of the hole where neutrals are scarce.

### 4.1.2 Why C₄F₆ Dominates

C₄F₆ (hexafluoro-1,3-butadiene) has a high C/F ratio and makes large, unsaturated fragments with high sticking coefficients. These deposit preferentially on the mask top and the upper walls (Chapter 3, Section 3.3.3), protecting both. Its fragments also deposit on nitride and carbon more than on oxide. It gives the highest selectivity to the ACL and the most sidewall protection of any common gas. Its cost is that too much of it closes the hole: excess carbon builds up at the neck and at the bottom.

C₄F₈ makes mostly CF₂, a less sticky radical that reaches deeper into the hole. Mixing C₄F₆ and C₄F₈ sets the depth profile of polymer: more C₄F₆ protects the top and neck, more C₄F₈ supplies the lower wall and the bottom.

---

## 4.2 The Polymerization Index

### 4.2.1 A Carbon–Oxygen–Fluorine Balance

A simple bookkeeping number captures much of the behavior. Each oxygen atom can remove one carbon atom as CO. The carbon left over, per fluorine, measures the tendency to deposit:

```
Π = (C_feed − O_feed − O_wafer) / F_feed       (atoms per unit time)

Reference main etch (sccm):  C₄F₆ 40, C₄F₈ 20, O₂ 35, Ar 400
  C_feed = 4 × 40 + 4 × 20 = 240
  F_feed = 6 × 40 + 8 × 20 = 400
  O_feed = 2 × 35         = 70
  O_wafer (Chapter 3, Section 3.6.1): ≈ 18 early, ≈ 8 late

  Π (early) = (240 − 70 − 18) / 400 = 0.38
  Π (late)  = (240 − 70 − 8)  / 400 = 0.41
```

```
Illustrative regimes (this chamber, 20 mTorr, ⟨E_i⟩ ≈ 3 keV):
  Π < 0.25          lean: high rate, poor mask and nitride selectivity,
                    bow grows (little sidewall polymer)
  0.30 ≤ Π ≤ 0.45   working range for the capacitor hole
  Π > 0.50          rich: neck closes, bottom polymer, etch stop
```

The index ignores which fragments carry the carbon and where they deposit. It is still a useful first coordinate. A recipe change that adds 5 sccm O₂ lowers Π by 0.025. A product with less open area raises Π late in the etch because less oxygen comes from the wafer. A worn upper electrode made of silicon consumes fluorine and raises Π (Chapter 9).

---

## 4.3 The Steady-State Film

### 4.3.1 Film Thickness and Etch Rate

Under steady ion bombardment, a fluorocarbon film of thickness t_fc forms on the surface. The ions deliver energy through it. The thicker the film, the less energy reaches the substrate interface:

```
ER ≈ ER_max · exp(−t_fc / λ_E)

λ_E: energy attenuation length in the film, ≈ 1–2 nm for keV Ar⁺
     (illustrative 1.5 nm at 3 keV)

Typical film thickness at the bottom of an open area:
  SiO₂:  t_fc ≈ 0.5–1.0 nm   (substrate O helps remove the film)
  Si₃N₄: t_fc ≈ 1.5–2.5 nm   (N removes carbon less effectively, as CN)
  ACL:   t_fc ≈ 2–4 nm, and the substrate is itself carbon
  W:     t_fc ≈ 1–2 nm      (W forms volatile WF₆, but the film shields it)
```

```
Illustrative selectivity from film thickness (λ_E = 1.5 nm):
  SiO₂ (t_fc = 0.8):  exp(−0.53) = 0.59 of ER_max
  Si₃N₄ (t_fc = 1.8): exp(−1.20) = 0.30
  Ratio ≈ 2 from the film alone; with the lower intrinsic yield of SiN in
  fluorocarbon (≈ 0.6 of SiO₂ per ion), oxide:nitride ≈ 3.3 open-area
```

At the bottom of a deep hole the oxide:nitride selectivity is higher, about 8 in the reference main etch. Two effects combine. The bottom receives fewer oxygen atoms from the gas, so the oxide's own oxygen becomes relatively more important for keeping its film thin. And the ions that reach the bottom are fewer and somewhat lower in energy, which favours deposition over etch on the nitride. This is how the main etch can slow on the 20 nm bottom stop (Chapter 12).

### 4.3.2 The Mask

The ACL is pure carbon and hydrogen. Fluorocarbon films on it are not consumed by substrate oxygen. Its etch is mainly physical sputtering of carbon and chemical removal by O atoms from the gas.

```
ACL erosion paths:
  Sputtering by Ar⁺ at keV: Y_C ≈ 0.3–0.5 C atoms/ion with a film
  Chemical: C + O → CO; rate ∝ Γ_O at the mask top
  Deposition: CFₓ fragments add carbon back (C₄F₆ most strongly)

Reference: ACL erosion ≈ 110 nm/min in the oxide steps, ≈ 150 nm/min in
the nitride steps (less polymer, more F and H)
```

Raising O₂ to clear polymer from the bottom of the hole erodes the mask faster. This is the central conflict of the chemistry: **the oxygen that keeps the bottom open also eats the mask**. Chapter 7 shows how steps manage it.

### 4.3.3 The Sidewall

The sidewall receives few ions, mostly at grazing angles, and a neutral flux that falls with depth. Polymer builds up on it. Near the top, where sticky precursors arrive, the sidewall film can become thicker than a nanometre and narrows the opening. This is the **neck**. Below the neck, where the film is thin and the reflected and deflected ions strike, the wall etches laterally. This is the **bow** (Chapter 10).

```
Sidewall film thickness along the hole (illustrative, reference main etch):
  Depth (nm)    film (nm)    lateral etch exposure
  ────────────────────────────────────────────────
  0–150         2.0–3.0      low (neck forms here)
  150–500       0.8–1.5      highest (bow region)
  500–1200      0.5–1.0      moderate
  1200–1600     0.3–0.6      low (few ions reach the wall here at angle)
```

---

## 4.4 Selectivity Targets for Each Material

### 4.4.1 Top and Middle Supports (SiN)

The oxide main-etch chemistry etches nitride slowly. Running it through the 120 nm top support would leave a thick polymer film, a narrow opening, and a long step. A separate nitride step is used:

```
Reference SN1 (top support) step (illustrative):
  CH₂F₂ 30 / C₄F₈ 15 / O₂ 25 / Ar 300 sccm
  Π = (C: 30 + 60 = 90; F: 60 + 120 = 180; O: 50) → (90 − 50)/180 = 0.22
  H from CH₂F₂ scavenges F as HF and helps break Si–N bonds
  SiN rate ≈ 420 nm/min; SiN:ACL ≈ 2.8
```

The middle-support step (SN2) uses a similar chemistry at 800 nm depth, where the ion flux is lower. Its main risk is a **notch**: when the main etch switches back to oxide chemistry below the support, the polymer balance changes abruptly. If the oxide step starts lean, it undercuts the nitride. If it starts rich, the hole narrows below the support (Chapter 10).

### 4.4.2 The Bottom Stop and the Pad

At the bottom, the main etch must slow on the 20 nm SiN stop across the wafer. Then a separate bottom-open (BO) step clears the stop and lands on the tungsten pad.

```
Reference BO step (illustrative):
  CHF₃ 40 / O₂ 15 / Ar 300 sccm, bias reduced to ≈ 8 kW
  SiN rate at the hole bottom ≈ 60 nm/min
  W rate at the hole bottom in this chemistry ≈ 15 nm/min
  W:SiN ≈ 0.25 → nitride:W selectivity ≈ 4
```

Tungsten forms volatile WF₆ (boiling point 17 °C), so a fluorine-rich step would gouge the pad. The BO chemistry is polymerizing enough that a fluorocarbon film shields the W once it is exposed, and short enough that the gouge stays within the 10 nm limit (Chapter 12).

### 4.4.3 The Wall Between Holes

The oxide wall between holes is also oxide. Every lateral nanometre etched there is lost wall. The sidewall must therefore be protected without narrowing the hole. Chemistry shifts that thicken the sidewall film (more C₄F₆, lower O₂) reduce the bow but close the neck and the bottom. This tradeoff is the **bow–neck–bottom triangle** that runs through Chapters 10 and 12.

---

## 4.5 Oxygen, NF₃, and Hydrogen

### 4.5.1 Oxygen

O₂ is the main control of polymer. It lowers Π, keeps the bottom open, and raises the bottom CD. It also erodes the mask, thins the sidewall film, and raises the bow. A typical response in the reference main etch:

```
Response to +5 sccm O₂ (illustrative):
  Π:              −0.025
  Bottom CD:      +0.8 nm
  Bow CD:         +0.5 nm
  ACL erosion:    +8 nm/min (+40 nm over the etch)
  Not-open rate:  ≈ ÷3
```

### 4.5.2 NF₃

A small NF₃ flow adds fluorine without oxygen. It cleans polymer from the hole bottom without attacking the mask as strongly as O₂ does, so it is often added late in the main etch, when the bottom is starved. Too much NF₃ thins all films and raises the bow.

### 4.5.3 Hydrogen

Hydrogen, from CH₂F₂, CHF₃, H₂, or HBr, scavenges fluorine as HF. Less free F means a more carbon-rich polymer that protects nitride and the mask better. Hydrogen also changes the nitride surface, helping it etch in the support steps. In the newest chemistries, hydrogen is added in larger amounts at low temperature, where HF forms and adsorbs on the oxide surface.

---

## 4.6 Hydrogen-Fluoride Chemistry

At low wafer temperature (below about 0 °C, and strongly at −40 to −60 °C), HF formed in the plasma or fed directly adsorbs on the oxide surface. Adsorbed HF and water form a thin reactive layer that greatly speeds the ion-assisted etch of SiO₂.

```
Illustrative effect of cryogenic HF-containing chemistry on oxide:
  Wafer temperature        +20 °C     −60 °C (HF/H₂/C₄F₈-based)
  Open-area oxide rate     600        1100 nm/min
  ARDE coefficient k       0.020      0.012
  Oxide:ACL selectivity    5.5        ≈ 6–8 (mask protected by condensed
                                       species)
```

The adsorbed layer forms on the bottom of the hole from neutral species that do not need to arrive by line of sight. This explains part of the lower ARDE. The cost is a new set of hardware (cryogenic chucks, Chapter 8), new residues (ammonium fluorosilicate on nitride, condensates on the walls), and a polymer-free sidewall that relies on low temperature, rather than film, to resist lateral etch. Chapter 14 treats cryogenic hole etch as an advanced scheme.

---

## 4.7 Residues and Their Effects

```
Residue                         Source                         Effect
──────────────────────────────────────────────────────────────────────────────
CFₓ polymer on sidewall         every step                     removed by ash; if
                                                                left, poor TiN
                                                                adhesion
Fluorinated carbon at bottom    BO step                        contact resistance
WOₓFᵧ on the pad                BO step, air exposure          contact resistance;
                                                                removed in wet clean
Boron/phosphorus fluorides      BPSG etch                      crystalline defects
                                                                if the queue to clean
                                                                is long (Chapter 16)
Sputtered ACL and Si from the   mask facet, Si electrode        hole-top residue,
upper electrode                                                 particles
```

---

## Summary and Key Takeaways

1. **C₄F₆ protects, C₄F₈ reaches.** C₄F₆ fragments stick near the top and protect the mask and neck. C₄F₈ makes CF₂, which reaches the lower wall and the bottom.

2. **Π is the first coordinate.** The reference main etch runs at Π ≈ 0.38–0.41, inside a working range of roughly 0.30–0.45. The wafer's own oxygen moves Π during the etch.

3. **Selectivity comes from the film.** The film stays thin on oxide and thick on nitride and carbon. The oxide:nitride ratio is about 3 on open area and about 8 at the bottom of the hole.

4. **Oxygen opens the bottom and eats the mask.** +5 sccm O₂ gains about 0.8 nm of bottom CD and costs about 40 nm of ACL and 0.5 nm of bow.

5. **Each material gets its own step.** The supports and the bottom stop use hydrofluorocarbon chemistries. The landing on W uses a polymerizing chemistry that protects the pad once it is exposed.

6. **HF chemistry changes the game at low temperature.** Adsorbed HF nearly doubles the oxide rate and lowers ARDE. The cost is cryogenic hardware and a different sidewall-protection mechanism.

---

## Study Questions

1. Compute Π for a main etch of C₄F₆ 45 / C₄F₈ 10 / O₂ 40 / Ar 400 sccm, with 12 sccm of O from the wafer. Is it inside the working range?

2. Using ER ∝ exp(−t_fc/λ_E) with λ_E = 1.5 nm, what film-thickness difference between oxide and nitride gives an oxide:nitride ratio of 8 if the intrinsic yield ratio is 1.7?

3. A recipe adds 10 sccm O₂ to the main etch. Using the response table of Section 4.5.1, estimate the changes in bottom CD, bow CD, and remaining ACL. Does the remaining ACL still meet 500 nm?

4. Why does a silicon upper electrode raise Π as it is consumed? Estimate the change in Π if the electrode consumes 10 sccm-equivalent of F atoms.

5. The BO step lands on W at 15 nm/min and the hole-to-hole spread in arrival at the W is 20 s. What is the gouge range across the holes? What must change to meet the 10 nm limit?

6. Explain in terms of line-of-sight transport why an adsorbed HF layer lowers the ARDE coefficient.

---

**Next Chapter:** [Chapter 5: High-Power Capacitively Coupled Dielectric Chambers](./05-ccp-dielectric-chamber.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
