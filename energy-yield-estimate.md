# Energy Yield Estimate — Solar PV Engineering Portfolio

**STATUS: ILLUSTRATIVE CALCULATION.** Uses standard public reference values. Not an approved engineering design.

## Inputs

| Parameter | Value | Source |
|---|---|---|
| DC capacity | 1 MWp | Fictional sample project |
| Local solar resource (POA — Plane of Array irradiance) | 1800 kWh/m²/year | Illustrative; varies by location |
| Performance ratio (PR) | 80 % | Typical mid-range for well-designed fixed-tilt system |

## Calculation

```
Annual energy = DC capacity × solar resource × performance ratio
             = 1000 kWp × 1800 kWh/m²/year × 0.80
             = 1,440,000 kWh/year
             = 1440 MWh/year
```

## Specific Yield

```
Specific yield = Annual energy / DC capacity
               = 1440 kWh/kWp/year
```

This is within the typical range of 1100–1700 kWh/kWp/year for fixed-tilt systems in sunny climates.

## Performance Ratio Breakdown (illustrative)

| Loss component | Loss (%) | Resulting PR |
|---|---|---|
| Inverter efficiency | 2.5 % | 97.5 % |
| Temperature losses | 7.0 % | 90.7 % |
| Soiling losses | 3.0 % | 88.0 % |
| Cable losses (DC + AC) | 2.0 % | 86.2 % |
| Mismatch losses | 1.5 % | 84.9 % |
| Availability losses | 1.5 % | 83.6 % |
| Shading losses | 3.5 % | 80.7 % |
| **Total PR** | | **80.7 %** |

## Caveats

- The 1800 kWh/m²/year value is illustrative. Actual solar resource varies by location and should be sourced from a local TMY (Typical Meteorological Year) file or solar atlas.
- The 80 % PR is illustrative. Actual PR depends on module temperature, inverter efficiency, soiling rate, cable lengths, and shading.
- This calculation does not include module degradation (typically 0.5–0.7 %/year) or annual performance drift.

## Year-1 vs. Year-25 Estimate (illustrative)

```
Year 1: 1440 MWh/year
Year 25 (assuming 0.55 %/year degradation): 1440 × (1 - 0.0055)^24 = 1440 × 0.877 = 1263 MWh/year
```

25-year cumulative energy (assuming linear degradation):

```
Cumulative = 1440 × 25 × (1 - 0.0055 × 24/2) ≈ 33,800 MWh
```

(Assumes 0.55 %/year degradation, linear; verify against module warranty terms.)

## Disclaimer

This calculation is for portfolio demonstration. It is not a substitute for a project-specific yield analysis using TMY data and a PVsyst-style simulation.
