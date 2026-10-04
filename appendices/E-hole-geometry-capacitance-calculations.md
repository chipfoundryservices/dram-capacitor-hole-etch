# Appendix E: Hole Geometry, Transport, Placement & Capacitance Calculations

The closed-form models used in this book, with the reference values substituted. Chapter references point to the derivations and discussion.

---

## E.1 Layout and Geometry (Chapter 1)

```
Hexagonal lattice, pitch p:
  area per site        = (√3/2) p²                 → 1754 nm² at p = 45 nm
  row spacing          = (√3/2) p                  → 39.0 nm
  triple-point distance = p / √3                    → 26.0 nm
Wall on the line of centres:   t_wall = p − CD
Open fraction at a given CD:   (π/4) CD² / ((√3/2) p²)   → 0.46 at 32 nm

Pitch from cell area (one hole per cell):  p = √(A_cell / 0.866)
  6F², F = 17 nm → 44.7 nm;  4F², F = 15 nm → 32.2 nm
```

---

## E.2 ARDE and Time to Depth (Chapter 3)

```
ER(A) = ER₀ / (1 + k A),   A = h / w

Time to depth:            t(h) = G(h) / ER₀,   G(h) = h + k h² / (2w)
Step time between depths: Δt = [G(h₂) − G(h₁)] / ER_layer

Depth at fixed time:      h = (w/k) [ √(1 + 2 k ER₀ t / w) − 1 ]

CD sensitivity at fixed time:
  ∂h/∂w = (k h² / (2 w²)) / (1 + k h / w)

Reference (ER₀ 600 nm/min, k 0.020, w 28 nm):
  G(1600) = 2514 nm → 4.19 min; ER/ER₀ at 1600 = 0.467; ∂h/∂w = 15.2 nm/nm

Fitting a depth series: plot ER₀ t vs h; or fit t/h = (1/ER₀)(1 + (k/2w) h)
  → intercept 1/ER₀, slope k / (2 w ER₀)
```

---

## E.3 Neutral Transport (Chapter 3)

```
Clausing factor, long tube (L/d > 10):   K ≈ 4 d / (3 L)
  L/d = 57 → K = 0.023

Coburn–Winters (non-sticking walls):
  Γ_bottom / Γ_top = K / (K + β (1 − K))

Wall-loss decay length (s_w ≪ 1, illustrative):
  λ_w ≈ d / √(2 s_w)
```

---

## E.4 Ion Angle, Acceptance, and Deflection (Chapters 3, 6)

```
Collisionless angular spread:      θ ≈ √(T_i⊥ / E_i)
Charge-exchange mean free path:    λ = 1 / (n σ_cx),  n = p / (k_B T)
Fraction crossing the sheath without collision: exp(−s/λ)

Acceptance angle, hole of width w and total depth h (mask + mold):
  edge to edge:  arctan(w / h);   from centre: arctan(w / (2h))

Ion transit time across a sheath (rough):  τ_ion ≈ 3 s √(m / (2 e V))

Lateral deflection by a field E⊥ over length L:  θ ≈ E⊥ L / (2 E_i)
Lateral shift over a further depth D:            x ≈ D tan θ
```

---

## E.5 Bow Geometry (Chapter 10)

```
Specular reflection from a wall tilted φ from vertical: outgoing angle 2φ
Depth below the reflection point at which the far wall is struck:
  Δz ≈ w / tan(2φ)
  Reference neck φ = 2.5°, w = 30 nm → Δz = 343 nm

Wall at the bow between neighbours:
  t = p − (b₁ + b₂)/2 − |Δ|
  σ_t = √(σ_b² / 2 + σ_Δ²)
```

---

## E.6 Twist and Tilt (Chapter 11)

```
Tilt:                    x = H tan α
Twist, constant angle:   x = θ_t (H − h₀);  σ_x = σ_θ (H − h₀)
Twist, growing angle:    θ(h) = θ₀ exp((h − h₀)/L_g)
                         x = θ₀ L_g [exp((H − h₀)/L_g) − 1]

Reference: σ_x = 1.67 nm (3σ = 5 nm), h₀ = 800 nm:
  constant-angle σ_θ = 0.12°;  growth model (L_g 400 nm) σ_θ₀ = 0.037°
Mold height scaling (onset fixed): constant angle ∝ (H − h₀);
  growth ∝ exp((H − h₀)/L_g) − 1
```

---

## E.7 Contact Overlap at the Bottom (Chapters 1, 11)

```
1-D overlap width: (w_hole + w_pad)/2 − |Δ|, capped at min(w_hole, w_pad)
  Reference: 25 − |Δ|;  overlap ≥ 16 nm → |Δ| ≤ 9 nm

2-D overlap area of a hole bottom (radius r₁) and a pad top approximated
as a circle (radius r₂), centres a distance d apart (r₂ − r₁ < d < r₁ + r₂):

  A = r₁² cos⁻¹((d² + r₁² − r₂²)/(2 d r₁)) + r₂² cos⁻¹((d² + r₂² − r₁²)/(2 d r₂))
      − ½ √((−d + r₁ + r₂)(d + r₁ − r₂)(d − r₁ + r₂)(d + r₁ + r₂))

Reference r₁ = 12 nm, r₂ = 13 nm:
  d (nm)    A (nm²)    fraction of the full bottom (452 nm²)
  ───────────────────────────────────────────────────────────
   0         452        1.00
   5         365        0.81
   9         270        0.60
  15         140        0.31

Interface resistance: R = ρ_c / A,  ρ_c ≈ 1×10⁶ Ω·nm² (illustrative)
  d = 9 nm: R ≈ 3.7 kΩ (vs. 2.2 kΩ centred)
```

---

## E.8 Capacitance (Chapter 1)

```
C_s = ε₀ · 3.9 · A / EOT,   A = π · CD_avg · H_eff
H_eff = H − t_stop − (1 − f_open) × (t_top + t_mid),  f_open ≈ 0.30

Reference: H_eff = 1461 nm; C_s = 8.88 fF
Sensitivities: ∂C/∂H = C/H_eff;  ∂C/∂CD = C/CD_avg;  ∂C/∂EOT = −C/EOT

Sense signal: ΔV_BL = (V_DD/2) · C_s / (C_s + C_BL)
Retention current limit: I_max = f_loss · C_s V_DD/2 / t_REF
```

---

## E.9 Bottom Stop, Gouge, and Side Punch (Chapter 12)

```
Nitride left after the main overetch, for a hole arriving t_a before the
end of ME2:
  t_SiN,left = t_stop − r_SiN,ME2 × t_a      (r_SiN,ME2 ≈ 36 nm/min)

BO step of length T_BO, SiN rate r_N, W rate r_W:
  time to clear: t_c = t_SiN,left / r_N
  W gouge:       g = r_W × (T_BO − t_c)
  side punch:    s = r_N × (T_BO − t_c)     (into pad-isolation SiN)

Reference: T_BO = 30 s, r_N = 60 nm/min, r_W = 15 nm/min
  t_left 2.5 nm: g = 6.9 nm, s = 27.5 nm
  t_left 20 nm:  g = 2.5 nm, s = 10 nm

Taper: CD_bot = CD_start − 2 L tan α
```

---

## E.10 Charging (Chapters 6, 13)

```
Coaxial capacitance of a hole segment of length L:
  C ≈ 2π ε₀ ε_r L / ln(r_out / r_in)
  L = 50 nm, ε_r 3.9, r_out/r_in 1.8 → 1.8×10⁻¹⁷ F

Electron arrival at the bottom: Γ_e ≈ ¼ n_e v̄_e × f_transmit × A_bottom
Wall RC: τ = R_□ (L / circumference) × C
```

---

## E.11 Heat, Stress, and Gas (Chapters 2, 5, 8)

```
Wafer heat flux: q = (P_ion + P_other) / A_wafer
Temperature drop across the He gap: ΔT = q / h_gap
Wafer thermal time constant: τ_w = m c_p / (h_gap A)

Stoney curvature: κ = 6 σ_f t_f (1 − ν) / (E t_s²);  sag δ = κ D² / 8

Residence time: τ = p V / Q  (Q in Pa·m³/s; 1 sccm = 1.69×10⁻³ Pa·m³/s)
Polymerization index: Π = (C − O_feed − O_wafer) / F
Oxygen from the wafer: 2 × (open fraction) × A_wafer × (removal flux)
```

---

## E.12 APC (Chapter 15)

```
Feed-forward ME2 time: Δt = (∂h/∂w × Δw_mask + Δt_mold) / ER_bottom
Feedback: offset_{k+1} = offset_k − λ G⁻¹ e_k

Reference G (rows: bottom CD, bow; columns: O₂ sccm, wafer T °C):
  [ 0.16  0.07 ]
  [ 0.10  0.13 ]     det = 0.0138
```
