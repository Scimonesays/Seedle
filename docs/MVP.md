# Seedle MVP Roadmap

Seedle should not begin by building the dome. It should prove the difficult control loops in increasing levels of physical risk.

## Phase 0 — Definitions

**Goal:** freeze vocabulary and interfaces.

Deliverables:

- product contract
- GrowSpec v0.1
- ModuleSpec v0.1
- safety architecture
- simulator requirements
- telemetry/event model

Exit condition: one crop lifecycle can be represented without hardware-specific commands.

## Phase 1 — SeedOS simulator

Build a software-only environment containing:

- virtual grow cells
- virtual crop state
- weather/natural-light input
- nutrient reservoir model
- energy budget
- staggered crop scheduler
- daily harvest projection
- tool/capability resolver
- failure injection

Minimum demonstration:

> Given a meal target and crop library, SeedOS schedules overlapping crop cycles and keeps a rolling projected harvest queue without directly commanding imaginary hardware.

## Phase 2 — Single hydroponic cell

One real crop cell with:

- reservoir
- pump
- EC/pH/temperature sensing
- lighting
- camera
- environmental sensing
- hard safety cutoffs

No cutting tool.

Exit condition:

- GrowSpec drives a crop from seedling to manual harvest.
- Telemetry shows every control decision and safety bound.
- Fluid faults can be injected without unsafe dosing.

## Phase 3 — Multi-cell staggered growing

8–16 cells.

Prove:

- overlapping plant ages
- resource sharing
- daily/rolling harvest forecasting
- automatic seeding for supported crop
- natural-light accounting
- Family Adapt prototype using simulated/explicit consumption events

## Phase 4 — Crop gantry

Add:

- XY/XYZ positioning
- camera
- tool docking
- seeding head
- non-cutting inspection/manipulation tool

Exit condition:

- repeatable cell addressing
- automatic tool identity verification
- collision-safe movement
- calibration recovery

## Phase 5 — Controlled cutting and harvest

Only after guarded test rigs.

Add:

- scissors/cutter
- soft gripper
- vision-based verified cut target
- post-action inspection
- safe abort

Start with crops that present mechanically simple harvest geometry.

## Phase 6 — Maintenance-access demonstrator

Build a vertical slice containing:

- one grow cell
- under-bed valve/sensor
- service spine
- maintainer manipulator or carriage
- replaceable pump/valve cartridge
- fabrication handoff

Exit condition:

> A deliberately failed replaceable module can be isolated, removed, replaced, tested, and returned to service without human access inside the mechanism.

## Phase 7 — Environmental enclosure

Add:

- dome/enclosure prototype
- active ventilation
- representative rotating solar shutter section
- thermal model
- rain/leak management
- service access

## Phase 8 — Seedle Alpha

Integrate enough cells and crop types to demonstrate continuous useful harvest.

Alpha target:

- autonomous staggered production
- supported automatic harvest
- household food queue
- modular expansion
- community data export
- safe fallback modes

## Metrics

Seedle should be evaluated on more than yield.

Track:

- edible kcal/day
- edible mass/day
- harvest continuity
- protein/fat contribution
- yield per m²
- yield per kWh
- yield per liter of makeup water
- nutrient input per edible kg
- labor minutes/week
- intervention frequency
- tool-change success
- harvest success
- crop loss
- module failure rate
- repair success
- root clogging events
- wasted food
- user-selected recipe fulfillment
