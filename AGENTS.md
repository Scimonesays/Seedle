# Seedle Engineering Guardrails

These rules apply to AI agents and human automation working in this repository.

## Project truth

Seedle is currently an early-stage autonomous food-system project. Do not describe conceptual features as already working hardware.

## Never silently weaken safety

Do not:

- bypass interlocks
- remove dose limits
- convert verified actions into open-loop actuator commands
- weaken collision checks
- allow community content to execute arbitrary code on machine controllers
- treat unknown sensor values as safe defaults

## GrowSpec boundary

GrowSpec expresses biological intent and capability requests.

It must not contain arbitrary shell code, firmware commands, raw motor movements, unrestricted pump durations, or unbounded chemical dosing.

## ModuleSpec boundary

Every serviceable hardware module must eventually document:

- capabilities
- interfaces
- robotic service actor
- service face
- approach/clearance
- isolation
- removal
- installation
- verification

## Evidence discipline

Never fabricate:

- crop yields
- nutrient targets
- energy savings
- failure rates
- community test counts
- food output
- self-repair performance

Clearly mark examples and assumptions.

## Repository workflow

- Prefer small coherent commits.
- Do not create branches unless explicitly requested.
- Keep architecture docs synchronized with schema changes.
- Do not add external dependencies without a concrete need.
- Do not choose a production technology stack merely to make the repository look busy.
- Simulation and validation come before high-energy or cutting hardware.
