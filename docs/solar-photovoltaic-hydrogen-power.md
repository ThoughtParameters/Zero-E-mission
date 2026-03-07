# Solar Photovoltaic and Hydrogen Power Generation Using Linear Generators

## Overview

This document describes an integrated zero-emission power and water system that combines:

1. **Solar photovoltaic (PV) generation** – harvests sunlight as direct-current electricity.
2. **Atmospheric water generation (AWG)** – produces pure water from ambient air.
3. **Water electrolysis** – splits water into hydrogen (H₂) and oxygen (O₂) using surplus
   solar electricity.
4. **Hydrogen storage** – buffers energy across hours, days, or seasons.
5. **Linear power generation** – converts stored hydrogen back to electricity on demand via
   a free-piston linear generator (FPLG), with water vapour as the only exhaust product.

This closed-loop approach addresses the primary challenge of solar power – intermittency –
while producing zero greenhouse-gas emissions and zero liquid waste.

---

## System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                     SOLAR + HYDROGEN MICROGRID                      │
│                                                                     │
│   ☀️ Solar PV Array                                                  │
│        │                                                            │
│        ▼                                                            │
│   DC Bus (MPPT Charge Controller)                                   │
│        │               │                                           │
│        ▼               ▼                                           │
│   Battery Bank    Electrolyser ◄────── AWG Unit (water supply)     │
│   (short-term)         │                                           │
│                        ▼                                           │
│                  H₂ Storage Tank                                   │
│                        │                                           │
│                        ▼                                           │
│             Free-Piston Linear Generator (FPLG)                    │
│                        │                                           │
│                        ▼                                           │
│             AC/DC Power Conditioning                               │
│                        │                                           │
│             ┌──────────┴──────────┐                               │
│             ▼                     ▼                               │
│        Local Grid            Battery Top-up                       │
└─────────────────────────────────────────────────────────────────────┘
```

### Energy Flow Summary

| Condition | Primary Power Source | Storage Action |
|---|---|---|
| Sunny day, low demand | Solar PV | Charge battery; electrolyse surplus water → H₂ |
| Sunny day, high demand | Solar PV + battery | Minimal storage |
| Night / cloudy, low demand | Battery | - |
| Night / cloudy, high demand | Battery + FPLG (H₂) | Draw from H₂ tank |
| Extended low-sun period | FPLG (H₂) | Draw from H₂ tank |

---

## 1. Solar Photovoltaic Generation

### How Solar PV Works

A solar PV cell is a semiconductor device that converts photons from sunlight into DC
electricity via the photovoltaic effect. Multiple cells are combined into **panels**;
panels are combined into **arrays**. A **Maximum Power Point Tracking (MPPT)** charge
controller extracts the maximum available power from the array at any given irradiance level.

### Sizing for a Community Microgrid

```
Daily energy requirement (kWh) ÷ Peak sun hours ÷ Panel efficiency factor = Array size (kWp)
```

**Example:**
- Community demand: 50 kWh/day
- Location peak sun hours: 5 h/day
- System losses (inverter, cable, temperature): 20 %
- Required array: 50 ÷ 5 ÷ 0.80 = **12.5 kWp**

### Panel Technology Comparison

| Type | Efficiency | Cost | Durability | Best Use Case |
|---|---|---|---|---|
| Monocrystalline silicon | 20 – 24 % | Higher | Excellent (25+ yr) | Space-constrained rooftops |
| Polycrystalline silicon | 15 – 18 % | Medium | Excellent | Open ground-mount arrays |
| Thin-film (CdTe / CIGS) | 10 – 14 % | Lower | Good (20+ yr) | Large-area low-cost deployments |
| Bifacial | 22 – 26 % | Higher | Excellent | Reflective ground surfaces |

---

## 2. Water Electrolysis: Producing Hydrogen from Solar Energy

### What Is Electrolysis?

Electrolysis passes a direct current through water (with an electrolyte to improve
conductivity), splitting water molecules into hydrogen gas at the cathode and oxygen gas
at the anode:

```
2 H₂O  →  2 H₂ + O₂
(electrolysis, powered by solar DC electricity)
```

### Electrolyser Types

| Type | Operating Temp. | Efficiency | Notes |
|---|---|---|---|
| **Proton Exchange Membrane (PEM)** | 20 – 80 °C | 65 – 80 % | Fast response; ideal for intermittent solar input |
| **Alkaline (AWE)** | 60 – 90 °C | 60 – 75 % | Low cost; proven at scale |
| **Solid Oxide (SOEC)** | 700 – 900 °C | 80 – 90 % | High efficiency; requires stable heat source |

For a solar-powered off-grid community, a **PEM electrolyser** is the preferred choice
because it can start and stop rapidly in response to variable solar output, tolerates the
pure water produced by AWG units, and has a compact footprint.

### Water Source: Atmospheric Water Generation

Using AWG-produced water (from units such as the WaterCube 100/1000 — see
[Atmospheric Water Generation](./atmospheric-water-generation.md)) as the electrolyser
feedstock offers critical advantages:

- **No ground or surface water is consumed**, preserving local hydrological resources.
- **Water purity is guaranteed** – AWG units with RO filtration produce near-distilled
  quality water that is ideal for PEM electrolysers.
- **The system is location-independent** – it requires only sunlight and air, making it
  viable in remote or water-scarce regions.

### Hydrogen Yield

A PEM electrolyser consumes roughly **50 kWh of electricity per kilogram of hydrogen**
produced. One kilogram of hydrogen contains approximately 33 kWh of usable energy
(lower heating value).

| Solar Input (kWh/day) | H₂ Produced (kg/day) | Equivalent Energy Stored (kWh) |
|---|---|---|
| 10 | 0.17 | 5.6 |
| 50 | 0.83 | 27.4 |
| 100 | 1.67 | 55.1 |

---

## 3. Hydrogen Storage

Produced hydrogen can be stored using several methods depending on scale and safety
requirements:

| Method | Energy Density | Pressure / Temp. | Infrastructure Cost |
|---|---|---|---|
| Compressed gas (Type IV cylinder) | 5 – 13 MJ/L | 350 – 700 bar | Medium |
| Metal hydride tanks | 10 – 15 MJ/kg | Near ambient | Higher (material cost) |
| Liquid hydrogen | 8.5 MJ/L | −253 °C | Very high (cryogenic) |
| Chemical carriers (ammonia, LOHC) | Variable | Ambient | Higher (conversion plant) |

For small-to-medium off-grid communities, **compressed gas storage at 350 bar** in Type IV
composite cylinders offers the best balance of safety, cost, and practicality. Metal hydride
tanks are an alternative where pressure safety is a concern.

---

## 4. Linear Power Generation from Hydrogen

### Free-Piston Linear Generator (FPLG) with Hydrogen Fuel

When solar generation is insufficient (night, cloud cover, seasonal), stored hydrogen is
fed to a **Free-Piston Linear Generator (FPLG)**. Hydrogen combustion in the piston chamber
drives the translator back and forth through the stator windings, directly producing
electricity with no crankshaft:

```
H₂ + ½ O₂ → H₂O + Heat → Piston motion → Linear generator → AC electricity
```

The **primary combustion product is water vapour**, with no CO₂, CO, or particulate
matter. However, burning hydrogen in air at high flame temperatures can produce nitrogen
oxides (NOx) from atmospheric nitrogen. NOx formation is controlled through lean-burn
combustion strategies, exhaust-gas recirculation (EGR), or water/steam injection. Where
truly zero tailpipe pollutants are required, a **hydrogen fuel cell** can replace or
supplement the FPLG: fuel cells convert H₂ to electricity electrochemically (H₂ + ½O₂
→ H₂O + electricity) with no combustion, eliminating NOx production entirely.

See [Linear Power Generators](./linear-power-generators.md) for the full technical breakdown
of FPLG operation.

### System Efficiency Chain

```
Solar PV (20%) → MPPT (98%) → Electrolyser PEM (75%) → H₂ Storage (95%) → FPLG (40%) → Power conditioning (95%)

Round-trip solar → stored H₂ → electricity ≈ 20% × 0.98 × 0.75 × 0.95 × 0.40 × 0.95 ≈ 5.3%
```

This round-trip efficiency is lower than direct battery storage (~80–90 % round-trip),
but hydrogen excels as **seasonal and long-duration storage** where battery capacity would
be prohibitively expensive. The optimal design uses batteries for short-term buffering
(hours) and hydrogen for multi-day or seasonal reserves.

---

## 5. Integrated System Benefits

| Benefit | Description |
|---|---|
| **Zero net emissions** | Solar energy input; water vapour output from H₂ combustion; no fossil fuels |
| **Water & power co-production** | AWG produces both drinking water and electrolyser feedstock |
| **Energy independence** | No grid connection, pipeline, or fuel delivery chain required |
| **Resilience** | Multi-layer storage (battery + H₂) handles extended cloudy periods |
| **Scalable** | Modular PV arrays, electrolyser stacks, and FPLG units can grow with demand |
| **Minimal maintenance** | No rotating gearbox in FPLG; PV panels have 25-year warranties |

---

## 6. Example Community-Scale Deployment

**Community profile:** 100 households (~400 people), rural location, 5 peak sun hours/day.

| Component | Specification |
|---|---|
| Solar PV array | 80 kWp (monocrystalline, ground-mounted) |
| Battery bank | 200 kWh (lithium iron phosphate) |
| AWG units | 2 × WaterCube 1000 (2 000 L/day total) |
| PEM electrolyser | 30 kW (uses surplus solar) |
| H₂ storage | 200 kg (compressed, 350 bar) |
| FPLG units | 2 × 20 kW (40 kW peak dispatch) |
| Daily electricity output | ~320 kWh/day |
| Daily water output (drinking) | 2 000 L (5 L/person/day) |

---

## Further Reading

- [Atmospheric Water Generation](./atmospheric-water-generation.md)
- [Linear Power Generators](./linear-power-generators.md)
- [Water Waste Management in Rural Areas](./water-waste-management-rural.md)
