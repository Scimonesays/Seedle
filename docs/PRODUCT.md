# Seedle Product Definition

## Product statement

Seedle is a household-scale autonomous food system. A user supplies seeds, water, nutrient concentrates, electrical/solar energy, and replaceable fabrication feedstock. Seedle manages overlapping crop cycles so a household receives a predictable rolling harvest with minimal gardening labor.

The first household product goal is **one fresh meal per day**, not complete nutritional independence.

Before that, Seedle is developed through **Seedle P1**, a 1–5 plant prototype whose job is to prove the autonomous growing and maintenance loops at small scale.

## Seedle P1

Seedle P1 maintains **1–5 plants simultaneously**. It is the reference development platform for:

- hydroponic control
- GrowSpec execution
- plant-state sensing
- compact crop-head motion
- tool changing
- serviceable grow cells
- safe pruning/harvest experiments
- maintenance-access experiments
- telemetry and community-data formats

P1 is intentionally not sized to feed a person. Scaling comes only after these loops are dependable.

## Seedle One

### User promise

1. Load approved seeds and nutrient concentrates.
2. Choose household size, meal target, preferences, allergies/exclusions, and desired crop mix.
3. Seedle plans staggered crop cycles.
4. Seedle grows, inspects, tends, harvests, cleans, and replants supported crops.
5. Seedle learns what is actually consumed and adapts future production.
6. The owner expands capacity by adding standardized modules rather than replacing the system.

### Inputs

- water
- seeds
- nutrient concentrates / mineral inputs
- sunlight
- supplemental electricity
- printable feedstock
- standardized non-printable components ("vitamins")
- occasional sanitation/maintenance consumables

### Outputs

- edible harvested produce
- crop/household performance data
- biomass/root waste for external or future recycling
- failed printable parts for recycling where validated

## Non-goals for V1

Seedle One does not claim:

- to supply every calorie or micronutrient required by a human
- to eliminate all human maintenance
- to manufacture motors, batteries, semiconductors, solar cells, sensors, or other non-printable components
- to support every crop
- to operate without safety inspection
- to perform unrestricted self-modification
- to guarantee daily harvests before sufficient production history exists

## Design principles

### 1. Biology drives the schedule

Calendar time is context, not truth. Crop actions should depend on measured plant state, confidence, and safe biological windows.

### 2. Natural light first

Use sunlight whenever useful. Supplemental light fills a measured deficit rather than following a fixed timer alone.

### 3. Closed-loop fluid control

Nutrient recipes express biological targets. SeedOS measures, doses incrementally, mixes, waits, re-measures, and stops on disagreement.

### 4. Stagger growth for continuity

SeedOS plans a rolling harvest queue rather than maximizing simultaneous yield.

### 5. Family Adapt

Production planning learns from:

- harvest weight/count
- food-bin removal
- waste/spoilage
- recipe selection
- explicit user feedback
- household occupancy targets
- seasonal demand

The system must always let the user override learned preferences.

### 6. Modular by default

Every replaceable component should have a stable interface, identity, version, service procedure, and compatibility contract.

### 7. Print what benefits from printing

Printing is a manufacturing tool, not a religion. Structural or wet-path parts must use materials and processes validated for their actual loads, temperatures, UV exposure, sanitation requirements, and food/water contact.

### 8. Robotic maintenance access is part of geometry

If a serviceable component cannot be robotically reached, inspected, isolated, removed, replaced, cleaned, and recalibrated, it is not considered closed-loop.

Components therefore require:

- a defined service face
- access clearance
- a service path
- standardized disconnects where practical
- safe isolation
- an installation/removal procedure
- post-install verification

### 9. Separate crop work from machine work

The overhead crop gantry is optimized for plants. The maintenance network is optimized for service, fabrication, fluid hardware, and repairs.

### 10. Evidence beats popularity

Community designs and grow recipes are not promoted because they are popular. Recommendations should be based on compatible, comparable real-world outcomes with uncertainty recorded.

## Physical identity

The visible product should feel like a compact conservatory rather than industrial farm equipment.

Above the grow deck:

- plants
- transparent/beautiful enclosure
- active solar-shutter dome
- crop gantry
- minimal visible plumbing

Below/within the service plinth:

- reservoirs
- pumps
- nutrient dosing
- batteries/power electronics
- compute
- fabrication
- spare modules
- filters
- waste handling

Service bays remain accessible externally for human recovery and emergency service even when robotic maintenance is available.

## Naming

- **Seedle** — physical product/system
- **SeedOS** — operating system and planner
- **GrowSpec** — crop execution specification
- **ModuleSpec** — physical-module capability/service specification
- **Family Adapt** — household preference and demand model
