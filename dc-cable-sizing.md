# DC Cable Sizing Calculation — Solar PV Engineering Portfolio

**STATUS: ILLUSTRATIVE CALCULATION.** Uses standard public reference values. Not an approved engineering design.

## Inputs (fictional example)

| Parameter | Value |
|---|---|
| String current (Imp) | 12 A |
| String length (module to DC combiner) | 30 m one-way |
| Cable type | PV wire, 1500 V DC rated, copper |
| Ambient temperature | 35 °C |
| Maximum voltage drop | 1.5 % |
| System voltage | 1000 V DC |

## Step 1 — Determine cable cross-section for voltage drop

```
Voltage drop = 2 × L × I × ρ / A
```

Where:
- L = one-way length (m) = 30 m
- I = current (A) = 12 A
- ρ = resistivity of copper = 0.0185 Ω·mm²/m at 20 °C
- A = cross-section (mm²)

Allowable voltage drop:

```
V_drop_max = 1000 V × 0.015 = 15 V
```

Required cross-section:

```
A = 2 × 30 × 12 × 0.0185 / 15
  = 13.32 / 15
  = 0.888 mm²
```

So the minimum cross-section by voltage drop is 0.89 mm². The next standard size up is 1.5 mm² or 2.5 mm².

## Step 2 — Current carrying capacity

The cable's current carrying capacity (CCC) must exceed the string current (with a safety margin). For a PV wire at 35 °C ambient, with typical derating factors:

```
CCC_required = I_string × 1.25 (safety factor) × 1.25 (PV overcurrent factor)
             = 12 × 1.25 × 1.25
             = 18.75 A
```

A 2.5 mm² PV wire typically has CCC of ~30 A at 30 °C ambient, derated to ~25 A at 35 °C. This exceeds 18.75 A and is acceptable.

## Step 3 — Selection

Selected cable: **PV wire, 2.5 mm² copper, 1500 V DC rated, UV-resistant.**

This satisfies both the voltage drop requirement (1.5 % max) and the current carrying capacity requirement.

## Caveats

- The calculation assumes a single-phase string current at STC. Real-world currents vary with irradiance.
- Cable routing, bundling, and ambient temperature affect the actual CCC; apply derating factors per local code (e.g. IEC 60364-5-52).
- The resistivity value (0.0185 Ω·mm²/m) is for copper at 20 °C; adjust for operating temperature.

## Disclaimer

This calculation is for portfolio demonstration. A real project requires engineering review by a competent electrical engineer and compliance with local electrical codes.
