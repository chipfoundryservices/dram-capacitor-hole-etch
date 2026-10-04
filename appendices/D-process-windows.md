# Appendix D: Process Windows & Lookup Tables

Reference recipe, windows, and sensitivity tables for the DRAM capacitor hole etch. All values are illustrative and belong to the reference process of this book.

---

## D.1 Reference Recipe

```
Step  Layer          Time  P     Src/Bias   Gases (sccm)                          T_wafer
                     (s)   (mT)  (kW)
──────────────────────────────────────────────────────────────────────────────────────────
SN1   top SiN        20    20    2.0 / 8    CH₂F₂ 30, C₄F₈ 15, O₂ 25, Ar 300       20 °C
ME1   upper oxide    90    20    2.5 / 12   C₄F₆ 40, C₄F₈ 20, O₂ 35, Ar 400        20 °C
SN2   middle SiN     15    20    2.5 / 12   CH₂F₂ 25, C₄F₈ 20, O₂ 30, Ar 350       20 °C
ME2   lower oxide    150   18    2.5 / 12   C₄F₆ 40, C₄F₈ 20, O₂ 35→42,            20 °C
                                 (pulsed    NF₃ 0→6 (last 60 s), Ar 400
                                 last 60 s)
BO    bottom SiN     30    25    2.0 / 8    CHF₃ 40, O₂ 15, Ar 300                 20 °C
──────────────────────────────────────────────────────────────────────────────────────────
Total 305 s;  40 MHz source / 400 kHz bias;  He 30 Torr (inner) / 35 Torr (outer)
WAC after every wafer: O₂ 1000 + NF₃ 50, 200 mT, 3 kW source, 60 s
```

---

## D.2 Process Windows (Main Etch)

```
Parameter              Window              Edge of window failure
──────────────────────────────────────────────────────────────────────────────
Π (main etch)          0.33–0.43           low: bow, mask loss; high: not-open,
                                           small bottom
O₂ (ME1/ME2)           30–45 sccm          see Π
Pressure               15–22 mTorr         low: low rate, mask facet; high:
                                           ARDE, bow
Bias power             10–14 kW            low: ARDE, not-open; high: mask,
                                           arcing, ring wear
Wafer T                10–30 °C            low: small bottom; high: bow
Overetch (ME2)         20–40 s             short: not-open; long: gouge, side
                                           punch, mask
BO time                25–40 s             short: nitride left; long: gouge,
                                           side punch
```

---

## D.3 Sensitivity Table (per unit change)

```
Knob (per unit)          Bottom CD   Bow CD    Neck CD   Top CD    ACL loss   Not-open    Twist 3σ
                         (nm)        (nm)      (nm)      (nm)      (nm)       (factor)    (nm)
─────────────────────────────────────────────────────────────────────────────────────────────────
O₂ +1 sccm (ME)          +0.16       +0.10     +0.06     +0.03     +8         ÷1.25       +0.02
C₄F₆ +1 sccm (ME1)       −0.08       −0.10     −0.08     −0.02     −4         ×1.15       −0.02
NF₃ +1 sccm (late ME2)   +0.17       +0.05     0         0         +3         ÷1.3        0
Wafer T +1 °C            +0.07       +0.13     +0.05     +0.03     +3         ÷1.05       +0.02
Pressure +1 mTorr        −0.08       +0.08     −0.04     0         −4         ×1.1        +0.05
Bias +1 kW               +0.15       +0.10     +0.05     +0.05     +25        ÷1.3        −0.08
ME2 overetch +1 s        +0.03       0         0         +0.01     +1.75      ÷1.07       0
Edge O₂ +1 sccm          +0.2 edge   +0.1 edge 0         0         small      —           0
Ring 100 µm low          —           —         —         —         —          —           tilt +0.08°
```

---

## D.4 Lookup: ARDE Curve (Reference Chemistry, TEOS-Equivalent)

```
ER₀ = 600 nm/min, k = 0.020, w = 28 nm

h (nm)   A      ER/ER₀   G(h) (nm)   t (min)   ∂h/∂w (nm/nm)
──────────────────────────────────────────────────────────────
 200     7.1    0.875     214        0.36       0.4
 400    14.3    0.778     457        0.76       1.6
 600    21.4    0.700     729        1.21       3.2
 800    28.6    0.636    1029        1.71       5.2
1000    35.7    0.583    1357        2.26       7.4
1200    42.9    0.538    1714        2.86       9.9
1400    50.0    0.500    2100        3.50      12.5
1600    57.1    0.467    2514        4.19      15.2
2000    71.4    0.412    3429        5.71      21.0
```

---

## D.5 Lookup: Capacitance

```
C_s = 3.453×10⁻¹¹ × π × CD_avg × H_eff / EOT   (F, SI units)
Reference H_eff = H − 20 − 0.70 × 170 = H − 139 nm; EOT 0.50 nm

                       CD_avg (nm)
H (nm)        24      26      28      30
──────────────────────────────────────────
1400         6.6     7.1     7.7     8.2
1600         7.6     8.2     8.9     9.5
1800         8.6     9.4    10.1    10.8
2000         9.7    10.5    11.3    12.1
(fF; scale by 0.50 / EOT for other EOT)
```

---

## D.6 Lookup: Bottom Placement from Tilt

```
x = H tan α (H = 1600 nm)
α:    0.02°   0.05°   0.10°   0.15°   0.20°   0.30°
x:    0.6     1.4     2.8     4.2     5.6     8.4   (nm)
```
