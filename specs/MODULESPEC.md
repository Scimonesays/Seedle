# ModuleSpec v0.1

ModuleSpec describes a physical Seedle module so SeedOS can identify, use, service, and evaluate it.

## Goals

A ModuleSpec answers:

- What is this?
- What capabilities does it provide?
- What resources does it require?
- Where and how may it be installed?
- Which systems are compatible?
- How is it isolated?
- How can a robot access/remove/install it?
- How is it calibrated/tested?
- What should happen when it fails?

## Required concepts

### Identity

- module type
- model
- version
- immutable release identifier
- designer/source

### Capabilities

Examples:

- `inspect_rgb`
- `cut_stem`
- `pump_solution`
- `measure_ec`
- `measure_ph`
- `rotate_shutter`

### Interfaces

Possible interfaces:

- power
- data
- fluid
- air
- mechanical
- optical

Interfaces should reference standardized connector definitions rather than free-form prose once those standards exist.

### Service geometry

A module declares:

- service actor
- service face
- approach direction
- clearances
- mass
- grasp points
- latch type
- removal travel
- neighboring keep-out envelope

### Isolation

Before removal, a module may require:

- electrical isolation
- fluid valve closure
- pressure release
- drain
- cutter lock
- thermal cooldown

### Service procedure

ModuleSpec references structured procedures for:

- inspect
- remove
- install
- calibrate
- functional test
- sanitize where relevant

### Lifetime

Track:

- install date
- operating hours
- cycles
- calibration drift
- predicted service
- observed failures

## Example philosophy

A pump cartridge should not be “a pump hidden under the bed.”

It should be:

> a front-serviceable fluid module with standardized inlet/outlet quick-connects, a keyed power/data backplane, an isolation sequence, a robotic grasp surface, a defined removal path, and a post-install prime/flow test.

That distinction is what allows Seedle to close the maintenance loop.
