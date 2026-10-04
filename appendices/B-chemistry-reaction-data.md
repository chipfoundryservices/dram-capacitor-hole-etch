# Appendix B: Chemistry & Reaction Data

Data for the gases, radicals, products, and reactions of capacitor hole etch. Values are representative and rounded; use them for estimates and for designing experiments.

---

## B.1 Feed Gases

```
Gas      Formula      M (g/mol)  C/F    bp (°C)   Role                        GWP₁₀₀ (approx.)
───────────────────────────────────────────────────────────────────────────────────────────────
C₄F₆     CF₂=CF–CF=CF₂ 162.0      0.67   6         sidewall/mask protection   < 1 (short-lived)
C₄F₈     c-C₄F₈       200.0      0.50   −6        CF₂ source, deep polymer    ≈ 9500
C₅F₈     c-C₅F₈       212.0      0.63   27        alternative to C₄F₆        < 100
CF₄      CF₄          88.0       0.25   −128      F-rich etch                 ≈ 6600
CHF₃     CHF₃         70.0       0.33   −82       nitride, BO step            ≈ 12,400
CH₂F₂    CH₂F₂        52.0       0.50   −52       nitride steps               ≈ 680
NF₃      NF₃          71.0       —      −129      F source, cleaning          ≈ 16,100
O₂       O₂           32.0       —      −183      polymer control             —
Ar       Ar           39.9       —      −186      ion source, dilution        —
COS      COS          60.1       —      −50       sidewall passivation        —
SiCl₄    SiCl₄        169.9      —      58        sidewall passivation        —
HF       HF           20.0       —      20        cryogenic chemistry         —
```

C₄F₆ is valued not only for selectivity but also for its short atmospheric lifetime. Abatement of C₄F₈, CHF₃, and NF₃ is required.

---

## B.2 Key Radicals and Sticking Coefficients

```
Species     Main sources                 Sticking on polymer      Where it acts
                                         wall (illustrative)
──────────────────────────────────────────────────────────────────────────────────
F           CF₄, NF₃, C₄F₈               ≈ 0.01 (wall); β ≈ 0.01   bottom etch; thins films
CF₂         C₄F₈, CH₂F₂                  ≈ 0.005–0.02              deep sidewall, bottom film
CF          C₄F₆, C₄F₈                   ≈ 0.1–0.3                 neck, mask, upper wall
C₂F₂, C₃F₃  C₄F₆                         ≈ 0.2–0.5                 mask top, neck
O           O₂, wafer oxide              ≈ 0.05 (on polymer)       removes polymer; mask
H           CH₂F₂, CHF₃, H₂, HBr         —                          scavenges F; nitride
```

---

## B.3 Surface Reactions

```
SiO₂ + CₓFᵧ film + ion  →  SiF₄↑ + CO↑ / COF₂↑
  overall: SiO₂ + 2CF₂  →  SiF₄ + 2CO

Si₃N₄ + CₓFᵧ film + ion  →  SiF₄↑ + CN↑ / FCN↑ / N₂↑
  nitride removes carbon less efficiently than oxide (no O)

C (mask) + O  →  CO↑
C (mask) + ion  →  sputtered C (redeposits)

W + 6F  →  WF₆↑  (bp 17 °C; landing pad attack)
W + O + F  →  WOF₄ (bp 186 °C), WO₂F₂ (residues)

BPSG: B₂O₃ + F → BF₃↑ (volatile);  P₂O₅ + F → POF₃↑, PF₅↑
  (B, P fluorides partly redeposit on walls)

Cryogenic HF:  SiO₂ + 4HF(ads)  →  SiF₄↑ + 2H₂O(ads)   (ion-assisted,
               water-catalysed)
               Si₃N₄ + HF  →  (NH₄)₂SiF₆ residue (sublimes > 100 °C)
```

---

## B.4 Product Volatility

```
Product      bp / sublimation (°C)   Note
────────────────────────────────────────────────────
SiF₄         −86 (subl.)             main Si product
CO           −191                    main O product
COF₂         −85
CN / FCN     −46 (FCN)               nitride marker
BF₃          −100
POF₃         −40
WF₆          17
WOF₄         186                      residue on pad
(NH₄)₂SiF₆   ≈ 320 (decomp. > 100)    nitride residue, cryogenic
```

---

## B.5 OES Lines

```
Species   λ (nm)   Use
──────────────────────────────────────────────────────────────────
CN        387.1    nitride steps; support and stop transitions
N₂        337.1    nitride (weak)
CO        483.5    oxide etch; arrival at the stop (knee)
SiF       440      Si-containing etch
CF₂       251.9    polymer precursor (UV)
F         703.7    F actinometry (with Ar 750.4)
O         777.4    O; WAC endpoint
H         656.3    H-containing steps
Ar        750.4    actinometer
```

---

## B.6 Polymerization Index Quick Reference

```
Π = (C_feed − O_feed − O_wafer) / F_feed       (atoms per unit time)

Contribution per 1 sccm:
  Gas       C     F     O     ΔΠ in reference ME (F_feed = 400)
  C₄F₆      4     6     0     ≈ +0.004 (raises C and F)
  C₄F₈      4     8     0     ≈ +0.002
  O₂        0     0     2     −0.005
  NF₃       0     3     0     ≈ −0.003 (F only)
  CH₂F₂     1     2     0     ≈ +0.0006 (H also scavenges F; effective
                                   Π rises more)

Working range (reference chamber): 0.30–0.45
```
