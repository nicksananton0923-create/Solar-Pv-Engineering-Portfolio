# System Sizing Methodology — Solar PV Engineering Portfolio

## Overview

This document describes the methodology for sizing a ground-mounted solar PV system.

## Inputs

- Available land area (m²)
- Local solar resource (kWh/m²/year)
- Target annual energy (kWh/year) — optional alternative input
- Module efficiency (%)
- Ground coverage ratio (GCR)
- Performance ratio (PR) estimate

## Step 1 — Calculate DC Capacity from Available Area

```
DC capacity (kWp) = available area (m²) × GCR × module efficiency × 1000 W/m² / 1000
```

Where GCR is typically 0.4–0.6 for fixed-tilt systems (to limit inter-row shading).

## Step 2 — Calculate AC Capacity (DC/AC ratio)

```
AC capacity (kW) = DC capacity (kWp) / DC-AC ratio
```

Typical DC-AC ratio: 1.1–1.3 (oversizing DC relative to AC increases inverter utilisation at the cost of clipping losses).

## Step 3 — Calculate Annual Energy

```
Annual energy (kWh) = DC capacity (kWp) × solar resource (kWh/m²/year) × PR
```

Typical PR: 75–85 %.

## Step 4 — Verify Against Target

If a target annual energy was specified, verify that the calculated annual energy meets the target. If not, adjust DC capacity, GCR, or PR assumptions and re-calculate.

## Worked Example (illustrative)

- Available area: 5000 m²
- Solar resource: 1800 kWh/m²/year
- Module efficiency: 20 %
- GCR: 0.5
- PR: 80 %
- DC-AC ratio: 1.25

```
DC capacity = 5000 × 0.5 × 0.20 × 1000 / 1000 = 500 kWp
AC capacity = 500 / 1.25 = 400 kW
Annual energy = 500 × 1800 × 0.80 = 720,000 kWh/year = 720 MWh/year
Specific yield = 720 / 500 = 1440 kWh/kWp/year
```

## Caveats

- The GCR and PR are typical values; project-specific values should be used.
- Shading, soiling, and temperature effects must be simulated using a tool like PVsyst for bankable estimates.
- Module efficiency varies by module selection; verify against the specific module's datasheet.

## Disclaimer

This methodology is for portfolio demonstration. A real project requires engineering review and a PVsyst-style simulation.
