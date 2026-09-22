# Seedle MVP Roadmap

Seedle should not begin by building a meal-scale dome. The first physical prototype is **Seedle P1: a compact 1–5 plant machine**.

The goal of P1 is to prove autonomy on a few plants before scaling area, crop count, power, or structural complexity.

## Seedle P1 — prototype contract

**Capacity:** 1–5 simultaneous plants.

**Primary proof:** Seedle can maintain real plants using the same software and modular principles intended for the larger system.

P1 should prove, in stages:

- GrowSpec-driven plant lifecycle state
- hydroponic/root-zone control
- nutrient and pH sensing/control with hard limits
- natural/supplemental light accounting
- camera-based plant inspection
- crop-head positioning
- tool identification/change
- one or more safe plant interventions
- harvest detection for at least one supported crop
- removable/serviceable grow cells
- basic maintenance access
- telemetry and event history
- safe failure/recovery

P1 does **not** need:

- meal-per-day output
- a full-size dome
- a large battery bank
- full solar independence
- every crop-head type
- complete robotic self-repair
- plastic recycling
- family-scale crop planning

The architecture should allow those systems to be added later without throwing P1 away.

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

- 1–5 virtual grow cells
- virtual crop state
- weather/natural-light input
- nutrient reservoir model
- energy budget
- staggered crop scheduler
- tool/capability resolver
- failure injection

Minimum demonstration:

> Given 1–5 crop instances, SeedOS can maintain different biological stages concurrently, request the correct capabilities, account for light/nutrients, and recover safely from simulated faults.

## Phase 2 — Seedle P1 wet prototype

Build a compact real system supporting **1–5 hydroponic plants**.

Minimum hardware:

- 1–5 removable grow cells
- shared or zoned reservoir
- pump/aeration
- EC/pH/solution-temperature sensing
- air temperature/humidity sensing
- controllable supplemental lighting
- camera
- leak detection
- hard safety cutoffs
- local SeedOS computer/controller

No cutting tool is required initially.

Exit condition:

- GrowSpec drives at least one real plant from seedling to manual harvest.
- Multiple plants can be maintained at different stages.
- Telemetry shows every control decision and safety bound.
- Fluid faults can be injected without unsafe dosing.
- Any grow cell can be removed for service without dismantling the prototype.

## Phase 3 — P1 crop head

Add a compact overhead/bridge motion system appropriate for the 1–5 plant footprint.

Add:

- XY/XYZ positioning as required
- camera positioning
- tool docking
- seeding or placement head
- non-cutting inspection/manipulation tool

Exit condition:

- repeatable plant/cell addressing
- automatic tool identity verification
- collision-safe movement
- calibration recovery
- access to all 1–5 plant positions

## Phase 4 — Controlled plant intervention

Only after guarded test rigs.

Add one intervention at a time:

- soft gripper
- pollination/vibration
- training/support interaction
- scissors/cutter
- harvest transfer

Exit condition:

- each action requires a verified target
- action is logged
- post-action inspection occurs
- uncertain state causes safe abort, not a guessed action

Start with plants/crops that have simple, observable geometry.

## Phase 5 — P1 maintenance demonstrator

Close a small maintenance loop within the same 1–5 plant prototype.

Include:

- removable grow cell
- accessible under-cell valve/sensor
- maintainer access path
- replaceable pump/valve/sensor cartridge
- printed replacement component handoff or installation experiment

Exit condition:

> A deliberately failed replaceable module can be isolated, removed, replaced, tested, and returned to service without dismantling the machine.

Full autonomous self-repair is not required yet.

## Phase 6 — Staggered 1–5 plant operation

Use the limited capacity to prove scheduling logic.

Examples:

- one plant germinating
- one vegetative
- one flowering
- one fruiting
- one in harvest/turnover

Prove:

- overlapping plant ages
- resource sharing
- early/late growth replanning
- harvest-window forecasting
- automatic turnover for supported cells
- first Family Adapt experiments using explicit consumption/harvest events

This phase proves the scheduling idea even though five plants cannot yet provide a daily meal.

## Phase 7 — Environmental/solar demonstrators

Develop small representative sections rather than a full dome:

- one active ventilation section
- one rotating solar-shutter section
- light-transmission measurement
- thermal model
- weather-safe default pose
- robotic/manual service access

## Phase 8 — Scale beyond P1

Only after the 1–5 plant machine is reliable should Seedle expand toward:

- 8–16 plants
- larger crop variety
- stronger harvest automation
- larger service network
- modular grow extensions
- household meal queue
- active dome
- solar/battery integration

The meal-per-day product target belongs here, after the small system has proven the control loops.

## P1 success metrics

For the 1–5 plant prototype, prioritize reliability over food quantity.

Track:

- plant survival
- successful completed crop cycles
- intervention minutes/week
- sensor uptime
- dosing accuracy
- light-target tracking
- tool-change success
- motion positioning repeatability
- harvest-detection accuracy
- root-clogging events
- leak events
- module service time
- repair/replacement success
- number of human interventions
- unexplained failures
- data completeness

Food mass and calories should still be recorded, but they are **observations**, not the primary P1 success criterion.
