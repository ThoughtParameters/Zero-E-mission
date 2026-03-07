# Linear Power Generators

## What Is a Linear Power Generator?

A **linear power generator** (LPG) converts linear (back-and-forth) mechanical motion directly
into electrical energy without requiring a rotary crankshaft or gearbox. Where a conventional
rotary generator converts circular shaft motion to electricity, a linear generator uses a
translator (the moving part) that travels along a straight axis through a stator winding to
induce an alternating electromotive force.

### Basic Principles

Linear generators operate on the same electromagnetic induction principle as rotary generators
(Faraday's Law), but the geometry is fundamentally different:

| Feature | Rotary Generator | Linear Generator |
|---|---|---|
| Moving part | Rotating shaft | Translating armature (rod/piston) |
| Gearbox / crankshaft | Required to convert linear → rotary | Not required |
| Friction losses | Significant (bearings, gears) | Minimal (frictionless magnetic bearings possible) |
| Primary energy input | Torque | Linear force |
| Stroke length | Continuous rotation | Defined stroke (mm to metres) |

---

## How a Linear Generator Works

```
  ┌───────────────────────────────────┐
  │         Stator Windings           │
  │  ╔═══╗   ╔═══╗   ╔═══╗   ╔═══╗  │
  │  ║   ║   ║   ║   ║   ║   ║   ║  │
  │  ║   ║   ║   ║   ║   ║   ║   ║  │
  │  ╚═══╝   ╚═══╝   ╚═══╝   ╚═══╝  │
  │       ←──── Translator ────→     │
  │    [Permanent Magnets / Piston]   │
  └───────────────────────────────────┘
            ↕  Linear motion
```

1. **Translator** – Contains permanent magnets (or an electromagnet) mounted on a rod or piston.
2. **Stator** – Consists of coil windings arranged along the axis of travel.
3. **Linear motion input** – A piston driven by combustion, wave motion, free-piston
   expansion, or spring resonance pushes the translator back and forth.
4. **Induced voltage** – As the magnets pass through the coil windings, alternating current
   is induced. A power-conditioning unit (rectifier + inverter) converts this to usable AC or DC.

---

## Types of Linear Generators

### 1. Free-Piston Linear Generator (FPLG)

A combustion chamber drives a piston directly connected to the translator. There is no
crankshaft; the piston oscillates between combustion and spring/bounce forces.

**Advantages:**
- High efficiency (up to 40–45 % indicated thermal efficiency)
- Flexible fuel capability (hydrogen, natural gas, biogas)
- Scalable from a few kW to hundreds of kW

**Applications:** Range extenders for electric vehicles, combined heat-and-power (CHP) units,
off-grid power nodes.

### 2. Wave Energy Linear Generators

Buoys or submerged translators rise and fall with ocean or lake waves, driving an LPG to
produce electricity.

**Advantages:**
- No fuel required; wave energy is renewable and predictable
- Low maintenance due to absence of rotating parts

### 3. Stirling Engine Linear Generators

A Stirling engine uses heat differentials (solar, biomass, waste heat) to drive a piston in
a closed-cycle thermodynamic process, with the piston connected directly to an LPG.

**Advantages:**
- Can use virtually any heat source (solar concentrator, combustion, geothermal)
- Very quiet operation
- No combustion products emitted (when solar-heated)

### 4. Resonant Spring-Mass Linear Generators

A mass-spring resonant system sustains oscillation at its natural frequency, minimising
energy input to maintain motion. Small resonant LPGs are used in energy harvesting from
ambient vibration.

---

## Linear Generators in Hydrogen Power Systems

When paired with a **hydrogen fuel cell** or a **hydrogen combustion free-piston engine**, a
linear generator forms a zero-emission power node:

```
  Hydrogen → Free-Piston Engine → Linear Generator → Power Conditioning → Grid / Battery
                     ↑
            (No crankshaft, no gearbox)
```

Hydrogen combustion in air produces water vapour as its primary by-product with no CO₂,
CO, or particulate matter. However, the high flame temperatures of H₂ combustion can
generate nitrogen oxides (NOx) from atmospheric nitrogen. NOx formation is mitigated
through strategies such as lean-burn combustion, exhaust-gas recirculation (EGR), or
water/steam injection—making the FPLG + LPG combination one of the cleanest mechanical
power generation options available. For truly zero tailpipe pollutants, hydrogen fuel
cells (which react H₂ electrochemically rather than via combustion) eliminate NOx
entirely and can be used in place of or alongside an FPLG.

See [Solar Photovoltaic and Hydrogen Power Generation](./solar-photovoltaic-hydrogen-power.md)
for details on producing the hydrogen feedstock from solar energy and atmospheric water.

---

## Performance Characteristics

| Parameter | Typical Range |
|---|---|
| Power output | 1 kW – 500 kW (depends on stroke and force) |
| Electrical efficiency | 85 – 95 % (mechanical → electrical) |
| Overall system efficiency | 30 – 45 % (fuel → electrical, FPLG) |
| Operating frequency | 10 – 100 Hz |
| Stroke length | 20 mm – 2 000 mm |
| Maintenance interval | > 10 000 hours (no gearbox wear) |

---

## Advantages for Off-Grid Zero-Emission Systems

1. **Simplified mechanical design** – Removal of the crankshaft reduces component count,
   weight, and maintenance requirements.
2. **Multi-fuel flexibility** – A single unit can switch between hydrogen, biogas, or
   natural gas, allowing a community to transition fuels as production capacity grows.
3. **Scalability** – Multiple small linear generators can be combined in parallel banks
   to match demand, providing redundancy.
4. **Integration with renewable storage** – Excess solar/wind energy can electrolyse water
   to hydrogen (stored locally), which an FPLG converts back to electricity on demand.
5. **Low noise profile** – Important for residential and healthcare settings.

---

## Further Reading

- [Atmospheric Water Generation](./atmospheric-water-generation.md)
- [Solar Photovoltaic and Hydrogen Power Generation](./solar-photovoltaic-hydrogen-power.md)
- [Water Waste Management in Rural Areas](./water-waste-management-rural.md)
