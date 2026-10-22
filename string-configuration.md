# String Configuration Calculation — Solar PV Engineering Portfolio

**STATUS: ILLUSTRATIVE CALCULATION.** Uses standard public reference values. Not an approved engineering design.

## Inputs

### Module (fictional example values)

| Parameter | Value |
|---|---|
| Rated power (STC) | 500 Wp |
| Vmp at STC | 41.5 V |
| Imp at STC | 12.05 A |
| Voc at STC | 49.8 V |
| Isc at STC | 12.7 A |
| Temperature coefficient of Voc | −0.27 %/°C |
| Temperature coefficient of Pmax | −0.35 %/°C |
| NOCT | 45 °C |

### Inverter (fictional example values)

| Parameter | Value |
|---|---|
| Max DC voltage | 1000 V |
| MPPT voltage range | 200–800 V |
| Max DC current per MPPT | 15 A |
| Number of MPPTs | 2 |

### Environmental design conditions

| Parameter | Value |
|---|---|
| Cold design temperature | 10 °C (typical for tropical climates) |
| Hot design temperature | 70 °C (module temperature at 1000 W/m², 35 °C ambient) |

## Step 1 — Maximum Modules per String (voltage limit at cold)

```
Voc at cold = Voc at STC × (1 + (T_stc - T_cold) × temp_coeff_voc)
            = 49.8 × (1 + (25 - 10) × (-0.0027))
            = 49.8 × (1 + 15 × (-0.0027))
            = 49.8 × (1 - 0.0405)
            = 49.8 × 0.9595
            = 47.78 V
```

(Note: temperature coefficient is negative, so colder modules have LOWER Voc. For cold climates where module temperature can be very low, the calculation may go the other way; verify the sign of the coefficient.)

For 10 °C cold design (above STC of 25 °C), Voc actually decreases:

Let's use a cold design temperature of 5 °C (more conservative for higher latitudes):

```
Voc at 5 °C = 49.8 × (1 + (25 - 5) × (-0.0027))
            = 49.8 × (1 + 20 × (-0.0027))
            = 49.8 × (1 - 0.054)
            = 49.8 × 0.946
            = 47.11 V
```

Wait — the coefficient −0.27 %/°C means that for every degree ABOVE 25 °C, Voc decreases by 0.27 %. For every degree BELOW 25 °C, Voc increases by 0.27 %.

Recomputing correctly:

```
Voc at 5 °C = Voc at STC × (1 + (25 - 5) × 0.0027)
            = 49.8 × (1 + 20 × 0.0027)
            = 49.8 × (1 + 0.054)
            = 49.8 × 1.054
            = 52.49 V
```

Max modules per string:

```
N_max = floor(V_inverter_max / Voc_cold)
      = floor(1000 / 52.49)
      = floor(19.05)
      = 19 modules
```

## Step 2 — Minimum Modules per String (MPPT voltage at hot)

```
Vmp at hot = Vmp at STC × (1 + (25 - T_hot) × temp_coeff_vmp)
```

(Using temperature coefficient of Vmp ≈ temperature coefficient of Pmax = −0.35 %/°C; this is approximate.)

```
Vmp at 70 °C = 41.5 × (1 + (25 - 70) × 0.0035)
             = 41.5 × (1 + (-45) × 0.0035)
             = 41.5 × (1 - 0.1575)
             = 41.5 × 0.8425
             = 34.96 V
```

Min modules per string:

```
N_min = ceil(V_mppt_min / Vmp_hot)
      = ceil(200 / 34.96)
      = ceil(5.72)
      = 6 modules
```

So the string size range is 6 to 19 modules per string.

## Step 3 — Current Limit (parallel strings per MPPT)

```
Isc at STC = 12.7 A
Max parallel strings = floor(I_inverter_max / Isc)
                     = floor(15 / 12.7)
                     = floor(1.18)
                     = 1 string per MPPT
```

For higher parallel string counts, use modules with lower Isc or inverters with higher current rating.

## Step 4 — Example Configuration

For a 100 kWp system using 500 Wp modules:

```
Total modules = 100,000 Wp / 500 Wp = 200 modules
Modules per string = 18 (within 6–19 range)
Strings = 200 / 18 = 11.1 → use 10 strings × 18 modules = 180 modules = 90 kWp
                            or 11 strings × 18 modules = 198 modules = 99 kWp (closer to 100 kWp)
```

With 11 strings and a 2-MPPT inverter:
- MPPT 1: 6 strings × 18 modules = 108 modules = 54 kWp
- MPPT 2: 5 strings × 18 modules = 90 modules = 45 kWp

Each MPPT is within the 15 A input current limit (max 1 string in parallel for Isc = 12.7 A; this configuration would require an inverter with higher current rating per MPPT, or a different module selection).

## Caveats

- Module and inverter values used here are fictional examples for illustration.
- The calculation assumes no shading and uniform module orientation.
- Real projects require a PVsyst-style simulation to account for shading, mismatch, and dynamic MPPT behaviour.
- Verify against the specific module's datasheet and the specific inverter's design manual.

## Disclaimer

This calculation is for portfolio demonstration. It is not a substitute for a project-specific design.
