# Solar PV Engineering Portfolio — Ground-Mounted Solar Projects

## Table of Contents
1. [Project Purpose](#1-project-purpose)
2. [Problem Statement](#2-problem-statement)
3. [Project Objectives](#3-project-objectives)
4. [Current Project Status](#4-current-project-status)
5. [Confirmed Technologies and Components](#5-confirmed-technologies-and-components)
6. [Proposed Components](#6-proposed-components)
7. [System Operation](#7-system-operation)
8. [Architecture or Workflow](#8-architecture-or-workflow)
9. [Installation or Setup Instructions](#9-installation-or-setup-instructions)
10. [Testing Status](#10-testing-status)
11. [Safety Considerations](#11-safety-considerations)
12. [Known Limitations](#12-known-limitations)
13. [Future Improvements](#13-future-improvements)
14. [Repository Structure](#14-repository-structure)
15. [Licence Information](#15-licence-information)
16. [Status Label Convention](#16-status-label-convention)

## 1. Project Purpose

This project provides an engineering documentation framework for ground-mounted solar photovoltaic (PV) projects. The framework covers site assessment, system sizing, string configuration, energy yield estimation, structural considerations, and commissioning documentation. The package includes illustrative calculation examples using standard public reference values (e.g. STC irradiance 1000 W/m², NOCT 45 °C, module temperature coefficient −0.40 %/°C) and a fictional sample project dataset. All calculations are explicitly labelled as **illustrative**, not as approved engineering designs.

## 2. Problem Statement

Ground-mounted solar PV projects require careful engineering documentation to support permitting, financing, construction, and commissioning. Without a consistent documentation framework, project files end up scattered across spreadsheets and emails, making it difficult to demonstrate compliance and to hand over to operations. A structured framework with illustrative calculations and templates makes the engineering documentation accessible and reproducible.

## 3. Project Objectives

- Provide a vendor-neutral framework for ground-mounted solar PV engineering documentation.
- Provide illustrative calculations for system sizing, string configuration, and energy yield.
- Provide CSV templates for module and inverter registers.
- Provide procedural documentation aligned with IEC 62548 (PV array design) and IEC 62446 (commissioning).
- Clearly label all calculations as illustrative, not as approved engineering designs.
- Provide a fictional sample project dataset for demonstration.

## 4. Current Project Status

| Item | Status |
|---|---|
| CSV templates | IMPLEMENTED |
| Illustrative calculation examples | IMPLEMENTED |
| Procedural documentation (IEC 62548 / 62446 aligned) | IMPLEMENTED |
| Approved engineering design | NOT VERIFIED (framework only) |
| Real project deployment | NOT YET TESTED |

## 5. Confirmed Technologies and Components

Confirmed technologies (standard public reference values used in calculations):

- STC (Standard Test Conditions): irradiance 1000 W/m², cell temperature 25 °C, AM1.5 spectrum
- NOCT (Normal Operating Cell Temperature): 45 °C at 800 W/m², 20 °C ambient, 1 m/s wind
- Typical module temperature coefficient: −0.40 %/°C (crystalline silicon)
- Typical inverter efficiency: 97–98 % (European weighting)
- Typical system performance ratio: 75–85 %
- Typical ground-mounted system DC/AC ratio: 1.1–1.3

These are textbook values for crystalline silicon PV modules and are used in the illustrative calculations. They are not specific to any module or inverter brand.

## 6. Proposed Components

| Component | Role | Notes |
|---|---|---|
| PV modules (crystalline silicon) | DC generation | Typical 400–550 Wp per module |
| String inverters or central inverters | DC to AC conversion | Typical 97–98 % European efficiency |
| Mounting structure (fixed-tilt or tracker) | Module support | Galvanised steel or aluminium |
| DC cabling (PV wire) | Module-to-inverter wiring | UV-resistant, double-insulated |
| AC cabling | Inverter-to-transformer wiring | Per local code |
| Transformer (if applicable) | Voltage step-up | Per project size |
| Earthing system | Electrical safety | Per IEC 62548 / local code |
| Surge protection | Lightning / surge protection | Per IEC 62305 / local code |
| Monitoring system | Performance tracking | Per vendor |

## 7. System Operation

A ground-mounted PV system operates in three stages: DC generation, DC-to-AC conversion, and AC export. PV modules generate DC power proportional to the incident irradiance and the module temperature (lower temperature = higher output). Strings of series-connected modules feed string inverters or central inverters. The inverter converts DC to AC at the appropriate voltage and frequency. The AC is then exported to the grid (grid-connected) or used locally (off-grid or hybrid). The system's annual energy yield depends on the local solar resource (kWh/m²/year), the system's DC capacity (kWp), and the system performance ratio (PR).

## 8. Architecture or Workflow

The system architecture for a typical ground-mounted PV project:

```
[PV modules] --> [DC strings] --> [DC combiner] --> [Inverter]
                                                          |
                                                          v
                                              [AC switchgear]
                                                          |
                                                          v
                                              [Transformer (if needed)]
                                                          |
                                                          v
                                              [Grid connection / Load]
```

Monitoring, earthing, and surge protection are cross-cutting systems that apply across the entire architecture.

## 9. Installation or Setup Instructions

This is a documentation framework. To use:

1. Review the templates in `templates/`.
2. Populate `module-register.csv` and `inverter-register.csv` with the project's actual modules and inverters.
3. Follow `procedures/site-assessment-methodology.md` to perform the site assessment.
4. Follow `procedures/system-sizing-methodology.md` to perform the system sizing.
5. Use `calculations/energy-yield-estimate.md` as a template for the project's energy yield estimate.
6. Use `calculations/string-configuration.md` as a template for the string configuration calculations.
7. Use `procedures/commissioning-checklist.md` for the commissioning process.

**Important:** The calculations in this framework are illustrative. A real project requires engineering review by a competent solar PV engineer and compliance with local electrical codes and grid-connection requirements.

## 10. Testing Status

All tests are currently **NOT YET TESTED** on a real project. Tests performed on the fictional sample:

1. CSV schema validation — TESTED — passes.
2. Calculation sanity check (energy yield vs typical PR range) — TESTED.
3. String configuration voltage check (max Voc vs inverter max input) — TESTED.
4. Real project deployment — NOT YET TESTED.
5. Grid-connection compliance — NOT YET TESTED.
6. Authority approval — NOT YET TESTED.

## 11. Safety Considerations

Solar PV systems present several safety hazards:

- **DC voltage.** PV strings generate DC voltage whenever illuminated. Even at low light, a 1000 V DC string can cause fatal electric shock. Use DC isolators and verify zero voltage before any work on DC wiring.
- **Arc flash.** DC arcs do not extinguish at zero crossing like AC arcs. Use arc-rated PPE and proper tools for any DC work.
- **High temperature.** PV modules can reach 70 °C+ in direct sun. Wear gloves.
- **Working at height.** Ground-mounted systems are typically low but may require working at height on mounting structures. Follow working-at-height procedures.
- **Electrical isolation.** The inverter must be isolated on both DC and AC sides before any work. Apply LOTO on both sides.
- **Earthing.** PV systems require a dedicated earthing system per IEC 62548 / local code. Earthing must be verified before energisation.
- **Lightning protection.** PV arrays are exposed to lightning. Surge protection devices (SPDs) are required per IEC 62305 / local code.

This framework is documentation only. Engineering review by a competent solar PV engineer is required for any real project.

## 12. Known Limitations

- All calculations are **illustrative**, not approved engineering designs.
- The framework does not constitute grid-connection approval.
- The framework does not constitute authority approval (e.g. from the local electricity regulator, fire marshal, planning authority).
- Standard reference values (STC, NOCT, temperature coefficients) are textbook values and may not match specific modules.
- Energy yield estimates are indicative and depend on local weather data that is not included in this framework.
- Structural design (mounting structure, foundation) is out of scope and requires a separate structural engineering design.
- Grid-connection study is out of scope and requires a separate study by the grid operator or an approved consultant.
- Environmental impact assessment is out of scope.
- This framework does not claim that the user holds a professional engineering qualification.

## 13. Future Improvements

- Add a Python script for energy yield calculation using TMY (Typical Meteorological Year) data.
- Add a PVsyst-style simulation output template.
- Add structural design templates for mounting structures.
- Add grid-connection study templates.
- Add environmental impact assessment templates.
- Add a financial model template (LCOE, payback, IRR).
- Add an O&M (operation and maintenance) manual template.

## 14. Repository Structure

```
14-solar-pv-engineering-portfolio/
├── README.md
├── LICENSE
├── docs/
│   ├── project-overview.md
│   ├── requirements.md
│   ├── system-architecture.md
│   ├── logic-and-operation.md
│   ├── components-and-bill-of-materials.md
│   ├── testing-and-validation.md
│   ├── safety-considerations.md
│   ├── development-roadmap.md
│   └── limitations.md
├── templates/
│   ├── module-register.csv
│   ├── inverter-register.csv
│   └── string-configuration.csv
├── calculations/
│   ├── energy-yield-estimate.md
│   ├── string-configuration.md
│   └── dc-cable-sizing.md
├── data/
│   └── sample-project-summary.csv
└── procedures/
    ├── site-assessment-methodology.md
    ├── system-sizing-methodology.md
    └── commissioning-checklist.md
```

## 15. Licence Information

Released under the MIT Licence. See the `LICENSE` file for the full text.

## 16. Status Label Convention

This project uses the following status labels throughout its documentation. Each label has a strict meaning and is not used interchangeably with any other label.

| Label | Meaning |
|---|---|
| **CONFIRMED** | Directly supported by available project information or inspected source code. |
| **PROPOSED** | A suggested design or implementation. Has not been verified against built hardware. |
| **NOT VERIFIED** | Information that has not been confirmed. Requires verification before use. |
| **IMPLEMENTED** | A feature or system that has actually been created and exists in the source code. |
| **TESTED** | A test that has genuinely been performed with recorded results. |
| **NOT YET TESTED** | Code, hardware, or functionality that still requires testing. |

If a section does not carry any status label, the content of that section is informational prose and does not make a claim of verification, testing, or implementation.

## Data and Confidentiality Notice

All sample data in this repository is **FICTIONAL**. Plant names use generic identifiers such as "Plant A", "Building 3", "Line 2", or "Western Plant". No real employer name, real equipment serial number, real employee name, real maintenance record, or any other confidential information is included. Templates are provided as reusable CSV schemas that can be populated with real site data by the adopting organisation. The fictional data is intended solely to demonstrate the template structure and calculation methodology.
