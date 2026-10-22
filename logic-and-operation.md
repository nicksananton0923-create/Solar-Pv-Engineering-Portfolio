# Logic and Operation — Solar PV Engineering Portfolio

## Sizing Logic

System sizing starts with the target annual energy (kWh/year) or the available land area (m²). For a target annual energy:

```
DC capacity (kWp) = target annual energy (kWh/year) / [local solar resource (kWh/m²/year) × performance ratio]
```

For an available land area:

```
DC capacity (kWp) = available area (m²) × ground coverage ratio × module efficiency × 1000 W/m² / 1000
```

Ground coverage ratio (GCR) is typically 0.4–0.6 for fixed-tilt systems and 0.3–0.5 for tracker systems (to limit inter-row shading).

## String Configuration Logic

A string's voltage must satisfy:

- `V_oc × N_modules × (cold temperature correction) ≤ inverter max input voltage`
- `V_mpp × N_modules ≥ inverter min MPP voltage` (under hot conditions)
- `I_sc × N_strings ≤ inverter max input current`

Typical string sizes: 18–26 modules per string for 1000 V systems, 30+ modules for 1500 V systems.

## Energy Yield Estimation

```
Annual energy (kWh) = DC capacity (kWp) × local solar resource (kWh/m²/year) × performance ratio
```

Performance ratio (PR) accounts for:
- Inverter efficiency (~97–98 %)
- Temperature losses (~5–10 %)
- Soiling losses (~2–5 %)
- Cable losses (~1–3 %)
- Shading losses (site-specific)
- Availability losses (~1–2 %)
- Module degradation (~0.5–0.7 %/year)

Typical PR: 75–85 % for well-designed systems.
