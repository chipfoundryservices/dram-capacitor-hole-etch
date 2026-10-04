# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM capacitor hole etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Not-Open Rate Up (Whole Wafer, Radially Smooth)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Upper electrode late in life; Π up      Electrode RF hours; CF₂/Ar up;      Apply/verify O₂ age
   (Ch. 9.1)                               bottom CD down                      offset; change electrode
2. O₂ MFC low or NF₃ step missing          MFC readback; recipe log; CO knee   Fix MFC; restore step
   (Ch. 4.5, 7.2)                          later
3. Mask CD small, not fed forward          Mask-open CD; APC log               Fix feed-forward
   (Ch. 15.4)
4. Pulsing or DC superposition fault       Generator logs; V_pp pattern        Repair; requalify
   (Ch. 6)
5. Mold thicker (lower oxide) not fed      Film metrology                      Feed-forward time
   forward
```

## G.2 Not-Open Holes Clustered

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Particles/flakes from rings or walls    SEM review: particle at cluster     Wet clean; check
   (Ch. 9.4)                               centre; adders on particle wafer    confinement rings
2. Mask defects (scum, missing holes)      Pre-etch mask inspection;           Litho/mask-open
   (Ch. 12.1.4)                            cluster shape follows litho field   corrective action
3. Plasma-off particle drop                Ring or centre pattern              Restore end-of-recipe
                                                                                purge segment
```

## G.3 Bow Too Large (Site Means > 34 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wafer too warm (He leak, zone fault,    He flow/leak by zone; zone temps;   Restore; chuck check
   chuck aging) (Ch. 8)                    radial bow pattern
2. Π low in ME1 (O₂ high, C₄F₆ low,        MFC readback; OES CF₂/Ar            Fix flow; adjust
   new electrode) (Ch. 4, 9)
3. Mask thin/faceted early (thin ACL       ACL thickness in; remaining ACL     Feed-forward; mask
   lot, high-erosion chamber) (Ch. 13.2)   after etch low                      thickness spec
4. Bias waveform fault (tailored → sine,   Waveform readback; IED monitor      Repair generator
   low-energy fraction up) (Ch. 6.3)
5. Wet clean over-etching the oxide        Pre/post-clean CD                   Clean recipe/time
   (Ch. 16.1)
```

## G.4 Bottom CD Small (Not Yet Not-Open)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Π drift up (electrode age, walls)       See G.1                             O₂ offset
2. Wafer too cold                          Zone temps                          Restore setpoints
3. Pressure high (confinement ring gap)    Pressure readback; ring gap         Recalibrate
4. Overetch short (APC)                    APC log; CO knee timing             Fix APC input
```

## G.5 Edge Tilt Out of Spec

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Ring lift not tracking erosion          Ring RF hours vs lift position      Recalibrate lift
   (Ch. 8.5)                                                                    (App. C.3)
2. Ring changed, not calibrated            PM log                              Lift calibration
3. Mask-open tilt changed (Ch. 11.4.2)     HV-SEM of mask holes before etch    Fix mask-open chamber
4. Wafer bow high (edge gap)               Incoming bow                        Stress balance (Ch. 2.4)
```

## G.6 Twist Increased (Interior)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Pulsing/DC superposition off or weak    Generator, DC supply logs           Repair
   (Ch. 6)
2. Mask holes less round (SADP rounding    Mask-hole circularity (CD-SEM)      Restore rounding step
   step drift) (Ch. 11.2.2)
3. Π high in ME2 (asymmetric polymer)      OES; bottom CD also small           O₂ / NF₃ adjust
4. Lower-oxide doping change (wall         Film dopant metrology               Deposition fix
   conductivity) (Ch. 13.1.2)
```

## G.7 Pad Gouge or Side Punch Too Deep

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. BO step too long or too F-rich          Recipe; CHF₃/O₂ readback            Restore BO
   (Ch. 12.3)
2. Main overetch too long (more holes      APC overetch log                    Fix APC
   arriving early with thin nitride)
3. Bottom stop thin (incoming)             Film metrology                      Feed-forward BO time
4. Placement offset large (side punch      HV-SEM placement                    Fix tilt/overlay
   only) (Ch. 11)
```

## G.8 Remaining Mask Too Thin (< 500 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Incoming ACL thin or soft               ACL thickness, density              Deposition fix
2. O₂ high / bias high                     Readbacks                           Restore
3. Etch time extended by APC (thick mold,  APC log                             Review limits; mask
   small mask CD)                                                              spec
4. Wafer too warm                          Zone temps                          Restore
```

## G.9 First-Wafer Effect After Idle or PM

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Walls not seasoned                      OES ratios vs baseline              Season (App. C.2)
2. Chuck thermal transient                 Wafer temp log; bow on first wafer  Pre-heat/dummy wafer
3. WAC skipped or short                    WAC endpoint time                   Restore WAC
```

## G.10 Chamber-to-Chamber Mismatch

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Different consumable ages               RF hours of electrode, ring         Stagger PM; age offsets
2. Electrode lot resistivity               Electrode lot records               Lot-specific constant
3. RF calibration (V_pp at the wafer)      Calibration wafer / probe           Recalibrate
4. Gap or confinement-ring differences     Mechanical check                    Re-shim
```
