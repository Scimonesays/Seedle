# Seedle

**Seedle is an autonomous, modular food-growing machine designed to turn seeds, water, nutrients, light, energy, and printable material into a dependable daily harvest with minimal human labor.**

The first commercial target is deliberately narrow:

> **Load the machine. Seedle plans, grows, tends, harvests, cleans, replants, and adapts toward at least one fresh meal per day.**

Seedle combines a beautiful controlled-environment grow dome with an overhead crop robot, a top-to-bottom robotic maintenance network, hydroponic grow modules, solar-shutter energy management, local fabrication, and a software platform called **SeedOS**.

## Core ideas

- **SeedOS** — the machine operating system and household food planner.
- **GrowSpec** — a machine-readable crop lifecycle: germination, light, nutrients, training, pruning, pollination, harvest, cleanup, and replanting.
- **ModuleSpec** — a machine-readable description of every serviceable hardware module: capabilities, interfaces, access direction, removal/install/calibration procedures, compatibility, and lifecycle data.
- **Family Adapt** — learns what a household actually eats, what it wastes, which recipes it uses, and how much capacity it needs.
- **Community Intelligence** — verified GrowSpec and ModuleSpec improvements are tested against real outcomes before being recommended.
- **Printable-first hardware** — print what is practical; standardize the non-printable “vitamins”; design every serviceable part for robotic inspection and replacement.
- **Closed-loop maintainability** — if the machine cannot reach, inspect, isolate, remove, replace, clean, and recalibrate a serviceable part, that part is not considered closed-loop.
- **Natural-light first** — rotating solar shutters allocate sunlight between the plants, thermal control, weather protection, and electrical generation; supplemental lighting fills only the measured deficit.
- **Hydroponic, media-minimized growing** — reusable/openable root modules avoid permanent soil and are designed around automated root release, cleaning, and crop turnover.

## Prototype contract — Seedle P1

The first physical Seedle is deliberately small: **1–5 plants**.

Its purpose is not to make a meal every day yet. Its purpose is to prove that the core Seedle loop works on real living plants:

> **maintain 1–5 plants from seed/seedling through growth, tending, harvest, turnover, and replanting with progressively less human intervention.**

The prototype should fit on a bench, cart, or compact stand and preserve the same architecture intended for larger Seedle systems: GrowSpec, ModuleSpec, tool changing, hydroponics, machine vision, serviceability, and safe closed-loop control.

## Seedle One — future product contract

Seedle One is the first household-scale product target.

**Primary outcome:** maintain a rolling queue capable of producing approximately one fresh meal per day.

Seedle P1 does **not** need to hit this output. P1 exists to prove the biological, robotic, and maintenance loops before scaling plant count.

The machine should:

1. Accept seeds, water, nutrients, and replaceable/printable materials.
2. Schedule overlapping crop cycles to avoid feast/famine harvest timing.
3. Measure plant state rather than rely only on calendar days.
4. Control nutrient solution, light, climate, and irrigation from biological targets.
5. Automatically change crop tools.
6. Inspect, train, prune, pollinate, and harvest supported crops.
7. Clean and reset supported grow modules.
8. Track harvested food, use, waste, and recipe demand.
9. Re-plan future crops around household behavior.
10. Detect faults and route maintainable components through a robotic service path.
11. Support versioned physical upgrades without replacing the whole machine.
12. Record evidence so the community can learn what actually works.

## System layers

```text
                  ACTIVE SOLAR-SHUTTER DOME
                    light / weather / energy
                              │
                    OVERHEAD CROP GANTRY
                              │
                 plants + modular grow cells
                              │
               service access / transfer plane
                              │
             top-to-bottom maintenance network
                              │
        ┌────────────── SERVICE CORE ──────────────┐
        │ water │ nutrients │ power │ compute      │
        │ print │ spares    │ clean │ waste       │
        └─────────────────────────────────────────┘
```

The crop robot is optimized for plants. The maintenance system is optimized for machinery. Components are arranged around robotic access, not around human hand access after assembly.

## Repository map

- `docs/PRODUCT.md` — product definition and non-negotiable design principles.
- `docs/ARCHITECTURE.md` — physical, robotic, software, and data architecture.
- `docs/MVP.md` — staged prototype plan and acceptance criteria.
- `docs/COMMUNITY.md` — community upgrade and evidence model.
- `docs/SAFETY.md` — safety model and hard limits.
- `specs/GROWSPEC.md` — GrowSpec standard.
- `specs/MODULESPEC.md` — ModuleSpec standard.
- `schemas/growspec.schema.json` — initial machine-readable schema.
- `schemas/modulespec.schema.json` — initial machine-readable schema.
- `examples/growspec/tiny-tim-tomato.yaml` — illustrative crop program.
- `CONTRIBUTING.md` — contribution rules.
- `AGENTS.md` — engineering/AI-agent guardrails.

## Development philosophy

Seedle is a safety-relevant cyber-physical system. The project should progress from **simulation → benchtop rigs → guarded hardware → limited crop automation → autonomous operation**. No software model should be allowed to issue unconstrained actuator, dosing, heating, cutting, or charging commands.

The long-term vision is ambitious; the implementation should stay brutally testable.

## Status

**Phase 0 — definition and architecture.**

No claim is made yet that Seedle can autonomously deliver the full product promise. This repository begins by defining the interfaces and evidence needed to prove it.
