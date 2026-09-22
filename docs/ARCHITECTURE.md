# Seedle Architecture

## Overview

Seedle is a cyber-physical system with four interacting planes:

1. **Biology plane** — crops, roots, nutrient solution, light, climate.
2. **Motion plane** — crop gantry, tool changer, maintenance network, service lifts.
3. **Utility plane** — water, nutrients, air, energy, drainage, sanitation.
4. **Control plane** — SeedOS, GrowSpec runtime, ModuleSpec registry, safety supervisor, data/evidence system.

## Physical layers

```text
┌──────────────── ACTIVE DOME ────────────────┐
│ rotating solar shutters / vents / weather  │
├─────────────────────────────────────────────┤
│ OVERHEAD CROP GANTRY                        │
│ camera / seeder / cutter / gripper / etc.  │
├──────────────── GROW DECK ──────────────────┤
│ modular crop cells / root chambers          │
├──────────── UNDER-BED SERVICE PLANE ────────┤
│ drains / valves / sensors / manifolds       │
├──────────── MAINTENANCE NETWORK ────────────┤
│ access rails / lift / maintainer arm        │
├──────────────── SERVICE CORE ───────────────┤
│ water / nutrients / compute / power / print │
│ spares / cleaning / waste / recovery        │
└─────────────────────────────────────────────┘
```

## Robotic roles

### Crop gantry

Primary responsibilities:

- seed placement
- visual inspection
- supported pruning/topping
- supported pollination
- crop training
- harvesting
- grow-cell cleaning tasks that are safe from above
- tool exchange

The crop gantry should remain light and precise. It should not carry heavy batteries, large pumps, or general-purpose maintenance tooling.

### Maintenance network

The maintenance system is not merely a handoff arm. It is a **top-to-bottom service-access network**.

It may include:

- lower maintainer arm
- vertical service lift/spine
- under-bed service carriage
- upper service carriage
- removable/repositionable grow modules
- shared calibration/inspection docks

Primary responsibilities:

- pump/filter/valve replacement
- printed-part handling
- module disassembly/reassembly where supported
- service of crop tools
- root/debris handling
- inspection of under-bed plumbing
- access to roof/shutter actuators
- calibration
- spare-part inventory movement

### Access rule

Every serviceable module declares:

- service actor
- service face
- minimum clearances
- approach direction
- isolation steps
- disconnect interfaces
- removal path
- installation path
- calibration/test procedure

A future CAD validator should reject a system layout if a required service envelope intersects permanent structure or another non-removable module.

## Grow modules

Use crop cells rather than permanent beds where possible.

Candidate classes:

- **S** — greens/herbs/small roots
- **M** — peppers/tomatoes/strawberries/beans
- **L** — large root volume / high-calorie crop experiments

The root interface should minimize permanent media and avoid trapping mature roots in fine mesh. Preferred direction:

- crown support above
- dark root chamber below
- smooth/openable internal geometry
- controlled root separation between cells
- sacrificial/root-cut release where biologically appropriate
- coarse root/debris capture before pumps
- automated wash/sanitize/inspect cycle

## Active dome

The roof is a multi-purpose system:

- admit natural light
- modulate crop light
- shade when necessary
- collect solar electricity
- close against weather
- contribute to nighttime insulation
- support ventilation strategy

Each shutter is a replaceable module. SeedOS allocates incoming sunlight between biological demand and electrical generation.

## Fluid system

High-level loop:

```text
water source
   ↓
treatment / storage
   ↓
mix reservoir ← nutrient dosing
   ↓
distribution
   ↓
root zones
   ↓
coarse root/debris separation
   ↓
filtration / optional sanitation
   ↓
return reservoir
   ↺
```

Nutrient and pH additions are bounded closed-loop operations:

1. measure
2. validate sensors
3. calculate conservative dose
4. dose
5. mix
6. wait
7. re-measure
8. stop on anomaly

## Compute architecture

### Safety supervisor

Highest local authority for:

- emergency stop
- actuator limits
- collision envelopes
- maximum dosing
- thermal limits
- battery/power limits
- leak/flood response
- cutting-tool interlocks

GrowSpec cannot override the safety supervisor.

### SeedOS planner

Owns:

- household meal target
- crop portfolio
- staggered sowing
- projected harvest queue
- resource allocation
- Family Adapt
- expansion planning

### GrowSpec runtime

Turns crop state into requested capabilities, e.g.:

- inspect growth tip
- provide remaining daily light
- maintain solution target
- pollinate compatible flower
- cut above verified node
- harvest fruit meeting ripeness criteria

### Capability resolver

Maps requested capabilities to installed modules.

A GrowSpec should request `cut_stem`, not hard-code a specific tool model.

### Module registry

Tracks:

- installed module identity/version
- capabilities
- service state
- calibration
- runtime hours/cycles
- predicted maintenance
- compatibility
- provenance

## Data hierarchy

```text
Household Model
    ↓
Production Plan
    ↓
Crop Instance
    ↓
GrowSpec + measured state
    ↓
Capability request
    ↓
ModuleSpec capability resolver
    ↓
Safety supervisor
    ↓
hardware
```

## Offline-first behavior

Food production cannot depend on cloud availability.

Local SeedOS must retain enough information to:

- keep plants alive
- maintain safe fluid chemistry
- execute already-installed GrowSpecs
- perform safe shutdown/recovery
- preserve local logs

Community synchronization is additive, not a dependency for basic operation.
