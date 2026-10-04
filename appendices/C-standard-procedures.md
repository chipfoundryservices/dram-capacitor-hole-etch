# Appendix C: Standard Operating Procedures

Procedures for characterizing, qualifying, matching, and maintaining the DRAM capacitor hole etch. Each procedure lists its purpose, the wafers and structures needed, the steps, and the acceptance criteria (illustrative). Adapt sample sizes and limits to the product and fab.

---

## C.1 Depth-Series Characterization (ER₀ and k)

**Purpose:** Extract the open-area rate ER₀ and the ARDE coefficient k of the oxide steps, and verify the step times of the reference recipe (Chapters 3, 7).

**Wafers:** 6 patterned wafers with the full mold and mask, from one mask-open lot; mask CD measured on all.

```
Steps:
1. Run SN1 + ME1 stopped at 30, 60, 90 s, and SN1 + ME1 + SN2 + ME2 stopped
   at 60 and 120 s into ME2 (5 wafers); one full-recipe wafer
2. Cross-section (FIB-SEM) at centre, r = 100 mm, and r = 145 mm: depth,
   top/neck/bow/bottom CD at each stop
3. CD-SAXS on the same sites (calibration of OCD)
4. Convert each depth to TEOS-equivalent using the layer rate ratios
   (SiN 0.70, BPSG 1.17) and fit
   ER₀ t = h + (k/2w) h²   (Appendix E.2) with w = local average CD

Acceptance (reference):
  ER₀ = 600 ± 20 nm/min; k = 0.020 ± 0.002
  Time to the stop (median hole) within ±4 s of the model
```

---

## C.2 Chamber Qualification After PM

**Purpose:** Release a chamber after a consumable change or wet clean (Chapter 9).

```
Steps:
1. Leak check; RF calibration (V_pp, phase) at three bias powers
2. Seasoning: 10–20 dummy wafers through the full recipe + WAC
3. OES baseline: CF₂/Ar, F/Ar, O/Ar, CO/Ar in ME1 within ±1% of the
   pre-PM chamber baseline
4. Blanket TEOS rate wafer: ER₀ within ±1.5% of baseline; uniformity
   ≤ 2% (1σ)
5. Particle wafer: adders ≥ 40 nm ≤ 10
6. Patterned qualification wafer:
     HV-SEM 9 sites: bottom CD, twist σ, edge tilt
     OCD 13 sites: bow, top CD
     Cross-section centre and edge: profile, gouge, side punch
     VC inspection on 2 dies: not-open count

Acceptance (reference):
  Bottom CD 24 ± 1 nm (site means); bow ≤ 34 nm (site means)
  Twist 3σ ≤ 5 nm; edge tilt ≤ 0.1° at r = 147 mm
  Gouge ≤ 10 nm; side punch ≤ 30 nm
  Not-open rate within 2× of the fleet median (pooled with the next
  week's production data)
```

---

## C.3 Focus-Ring Change and Lift Calibration

**Purpose:** Replace the focus ring and set the lift so the edge tilt is zero (Chapter 8).

```
Steps:
1. Install the ring; measure ring top height relative to the chuck surface
2. Run tilt-calibration wafers at three lift positions (−50, 0, +50 µm from
   the nominal matched height)
3. HV-SEM at r = 140, 145, 147 mm: mean radial displacement of hole bottoms
4. Fit tilt vs lift; set the lift to zero tilt at r = 147 mm
5. Load the erosion model (≈ 3 µm/RF h) into the lift controller

Acceptance: tilt at r = 147 mm within ±0.03°; radial tilt profile monotonic
```

---

## C.4 Twist and Placement Measurement by HV-SEM

**Purpose:** Measure the bottom-placement distribution (Chapter 11).

```
Steps:
1. Sample 9 sites per wafer (centre, 4 at r = 100 mm, 4 at r = 145 mm);
   at each site, image ≥ 2000 holes
2. For each hole, find the top-edge centre (SE image) and bottom centre
   (BSE image); compute d = bottom − top
3. Site mean of d → tilt vector; subtract
4. Residual distribution → twist σ (x and y), and the count of holes with
   |d − mean| > 10 nm (tail)
5. Correct σ for tool precision: σ_true² = σ_meas² − σ_tool²

Report: tilt map; twist σ by site; tail count per 10⁴ holes
```

---

## C.5 Not-Open Monitoring by Voltage Contrast

**Purpose:** Track the not-open rate per chamber (Chapter 12).

```
Steps:
1. After BO, ash, and clean, inspect 2 full dies per wafer on 1 wafer per
   chamber per day (≈ 3.4×10¹⁰ holes per chamber per day)
2. Classify dark holes: isolated (single), clustered (≥ 3 within 1 µm),
   edge-die
3. Review a sample by SEM to separate particles and mask defects from
   etch stops
4. Pool weekly; compute the etch-attributed rate with a 90% confidence
   interval

Alarm: etch-attributed rate > 2× fleet median for two consecutive weeks
```

---

## C.6 Waferless Autoclean Verification

**Purpose:** Confirm that the WAC restores the wall state (Chapter 9).

```
Steps:
1. Run the WAC with OES monitoring of CO (483 nm) and O (777 nm)
2. Record the time at which CO/Ar falls to within 5% of its final value
3. Compare with the baseline WAC endpoint time

Acceptance: WAC endpoint within ±15% of baseline; first-wafer ME1 CF₂/Ar
within ±1% of the lot mean
```
