# Appendix F: Endpoint & Metrology Reference

Quick reference for the endpoint signals and metrology used to control the capacitor hole etch (Chapter 15). Precision values are illustrative 1σ figures for a production-qualified method.

---

## F.1 Endpoint Signals by Step

```
Step   Signal (λ, nm)          Behaviour                      Use
──────────────────────────────────────────────────────────────────────────────────
SN1    CN 387 ↓, CO 483 ↑      sharp (shallow holes)           can call step end
ME1    CO 483 steady, slow ↓   falls with ARDE                 rate monitor
SN2    CN 387 ↑ then ↓         smeared over 5–10 s             confirm; time-based
ME2    CO 483 knee             median arrival at the stop      overetch reference,
                                                                lot monitor
BO     CN 387 ↓                gradual (2.5–20 nm left)        confirm clearing
WAC    CO 483 ↓, O 777 ↑       walls clean when flat           WAC endpoint
```

---

## F.2 Metrology Methods

```
Method        Quantity                    Precision       Sample            Destructive
──────────────────────────────────────────────────────────────────────────────────────────
CD-SEM        top CD                      0.3 nm          13–25 sites/wf    no
              circularity                 0.01
              striation (edge rough.)     0.3 nm
HV-SEM        bottom CD                   0.5 nm          9 sites, ≥ 2000   no
              bottom placement per hole   0.5–1.0 nm      holes per site
OCD           top, bow, mid, bottom CD    0.3–0.8 nm      13 sites/wf       no
              depth                       5 nm            (model-dependent)
CD-SAXS       average profile             0.2–0.5 nm      5 sites/wf        no
              average tilt                0.01°           (slow)
FIB-SEM       full profile, gouge,        1 nm            few holes          yes
              side punch, notch
TEM           interfaces, residues        0.2 nm          few holes          yes
VC e-beam     not-open, bridged           count           ≈ 10⁸ holes/h      no
Film metrology mold, ACL thickness        0.3%            49 sites           no
```

---

## F.3 Electrical Monitors

```
Structure                       Quantity                      Sensitive to
───────────────────────────────────────────────────────────────────────────────
Capacitor array (10⁴–10⁶)       average C_s                   depth, CD, EOT
Comb between capacitor rows      leakage / short               bridging (bow, twist)
Capacitor chain through pads     resistance / opens            not-open, contact
BL–SN leakage structure          leakage                       side punch
Bit map at wafer test            single, pair, cluster,        all of the above
                                 column fails
```

---

## F.4 Sampling Plan (Reference)

```
Per lot per chamber:   CD-SEM top (1 wafer), OCD (1 wafer), CO knee (all
                       wafers, automatic)
Per day per chamber:   HV-SEM (1 wafer), VC 2 dies (1 wafer), CD-SAXS
                       (1 wafer, calibration)
Per week per chamber:  cross-section (1 wafer)
After every PM:        full qualification (Appendix C.2)
```

---

## F.5 Measurement Pitfalls

```
Pitfall                                     Consequence / fix
──────────────────────────────────────────────────────────────────────────────
OCD model with too few profile parameters   bow hidden in "average CD"; recalibrate
                                            with CD-SAXS and cross-sections
HV-SEM charging of the mold                 bottom image shifts; use low dose,
                                            fixed scan direction, and a reference
                                            hole set
Cross-section not through hole centres      CDs underestimated; use FIB slice
                                            series or TEM with tilt
VC inspection after an incomplete clean     residue mimics not-open; review sample
                                            by SEM before attributing to the etch
Measuring tilt only at r ≤ 140 mm           misses the steepest edge tilt; include
                                            r = 145–147 mm
```
