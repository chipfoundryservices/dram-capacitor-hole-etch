# Appendix A: Material Properties

Properties of the mold, mask, pad, electrode, and chamber materials met in DRAM capacitor hole etch. Values are representative room-temperature values from the literature, rounded for estimates. Thin-film values depend strongly on the deposition process and are given as typical ranges.

---

## A.1 Mold Dielectrics

```
Property                     PE-TEOS SiO₂   BPSG            Thermal SiO₂   LPCVD Si₃N₄    PECVD SiN
──────────────────────────────────────────────────────────────────────────────────────────────────────
Density (g/cm³)              2.15–2.25      2.2–2.3         2.27           3.0–3.1        2.5–2.8
Molecular density            2.2×10²²       ≈ 2.2×10²²      2.27×10²²      1.3×10²²       ≈ 1.2×10²²
  (cm⁻³, SiO₂ / Si₃N₄ units)
Dielectric constant          4.0–4.2        4.0–4.3         3.9            7.5            6.5–7.5
Refractive index (633 nm)    1.45–1.46      1.45–1.47       1.457          2.01           1.9–2.0
Film stress (MPa)            −100 to −250   −50 to +50      −300           +1000 (tens.)  −200 to +300
                             (comp.)                                                       (tunable)
Dopants                      —              B 3–5 wt%,      —              —              H 10–25 at.%
                                            P 3–5 wt%
Plasma etch rate vs TEOS     1.00           1.10–1.25       0.95           0.6–0.8 (in    0.7–0.9
  (reference main etch)                                                     oxide steps)
Wet etch rate in dilute HF   1.0            3–5             0.7            0.02–0.05      0.05–0.2
  (relative)
```

---

## A.2 Hard-Mask Materials

```
Property                     PECVD ACL       High-density    B-doped C       W-doped C      SiON cap
                             (reference)     ACL
───────────────────────────────────────────────────────────────────────────────────────────────────────
Density (g/cm³)              1.7–1.9         2.0–2.2         2.0–2.3         2.5–3.5        2.2–2.5
H content (at.%)             15–25           5–15            5–15            5–10           5–15
sp³ fraction                 30–40%          40–60%          —               —              —
Stress (MPa)                 −200 to −400    −400 to −1000   −300 to −800    −500 to −1000  −200 to +200
Extinction k at 633 nm       0.3–0.5         0.5–0.8         0.4–0.7         > 1            ≈ 0
Oxide:mask selectivity       ≈ 5.5           ≈ 7             ≈ 9             ≈ 12           —
  (reference main etch,
  blanket)
Strip                        O₂ ash          O₂ ash          O₂ + F          wet + dry      F-based etch
```

---

## A.3 Pad and Electrode Conductors

```
Property                     W              TiN (CVD/ALD)      Ru
───────────────────────────────────────────────────────────────────────────
Density (g/cm³)              19.25          4.8–5.2            12.45
Atomic density (cm⁻³)        6.31×10²²      ≈ 5.0×10²²         7.42×10²²
Resistivity (µΩ·cm)          5.3 bulk;      80–200 (thin       7.1 bulk
                             8–15 thin      CVD, Cl-dependent)
Work function (eV)           4.5–4.6        4.5–4.8            4.7–4.8
Young's modulus (GPa)        ≈ 410          ≈ 250–450          ≈ 450
Fluoride volatility          WF₆ bp 17 °C   TiF₄ subl. 284 °C  RuF₅ bp 227 °C
Chloride volatility          WCl₆ bp 347 °C TiCl₄ bp 136 °C    —
```

---

## A.4 Capacitor Dielectrics

```
Material              k (film)    Band gap (eV)   Typical role
────────────────────────────────────────────────────────────────────────
ZrO₂ (tetragonal)     35–45       5.8             main high-k layer
Al₂O₃                 8–9         8.8             leakage-blocking interlayer
HfO₂                  20–25       5.7             alternative
TiO₂ (rutile)         80–100      3.0             next-generation (on Ru)
SrTiO₃                100–200     3.2             research

Reference stack ZrO₂/Al₂O₃/ZrO₂ (ZAZ), physical ≈ 5.5 nm, EOT ≈ 0.50 nm
```

---

## A.5 Chamber Materials

```
Part                  Material             Erosion (illustrative)        Notes
──────────────────────────────────────────────────────────────────────────────────────────
Upper electrode       single-crystal Si    15–25 µm/RF h (face);         F scavenger;
                      or SiC               gas holes +1.5 µm/RF h        resistivity matters
Focus ring            Si or SiC            Si ≈ 3 µm/RF h;               sets edge tilt
                                           SiC ≈ 1.5 µm/RF h
Confinement rings     quartz or Si         slow; collect polymer         set gap pressure
ESC top               Al₂O₃ or AlN         edge erosion; dielectric      chuck life ≈ 3000 RF h
                      ceramic              wear
Chamber liners        anodized Al, Y₂O₃    slow; Y₂O₃ resists F          particles if coatings
                      coatings                                            crack
```

---

## A.6 Physical Constants and Conversions Used

```
ε₀ = 8.854×10⁻¹² F/m;  ε₀ × 3.9 = 3.453×10⁻¹¹ F/m
e = 1.602×10⁻¹⁹ C;  k_B = 1.381×10⁻²³ J/K;  amu = 1.661×10⁻²⁷ kg
1 sccm = 4.48×10¹⁷ molecules/s = 1.69×10⁻³ Pa·m³/s (at 273 K)
1 mTorr = 0.1333 Pa
Ar mass 39.95 u;  CF₃⁺ 69 u;  F 19 u
Silicon wafer: 300 mm, 775 µm, 128 g, c_p 0.70 J/g·K, E 130 GPa, ν 0.28
```
