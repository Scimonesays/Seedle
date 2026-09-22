# GrowSpec v0.1

GrowSpec is Seedle's declarative crop-execution format.

A GrowSpec describes **biological goals, state transitions, and requested capabilities**. It must not encode arbitrary low-level motor, pump, heater, cutter, or dosing commands.

## Principles

1. Describe desired biological state.
2. Prefer measured stage/state over calendar-only triggers.
3. Request capabilities rather than hardware model numbers.
4. Every action must define verification and safe failure behavior.
5. Machine-level limits always override GrowSpec.
6. GrowSpecs are immutable once published; changes create a new version.

## Top-level sections

- identity
- crop
- compatibility
- environment
- lighting
- root_zone
- nutrition
- stages
- interventions
- harvest
- turnover
- evidence

## Stage model

A crop moves through named stages using measured predicates.

Typical stages:

- germination
- seedling
- vegetative
- flowering
- fruiting
- harvest_window
- turnover

Each stage can define:

- entry conditions
- exit conditions
- biological targets
- inspection cadence
- allowed interventions

## Capability requests

Examples:

- `inspect_rgb`
- `place_seed`
- `measure_solution`
- `provide_light`
- `vibrate_flower`
- `cut_stem`
- `soft_grasp`
- `transfer_harvest`
- `wash_cell`

SeedOS resolves capabilities to installed modules through ModuleSpec.

## Actions

Actions should be structured and verifiable.

Example:

```yaml
- id: top_primary_stem
  when:
    all:
      - metric: vision.node_count
        op: gte
        value: 5
      - metric: plant.health_score
        op: gte
        value: 0.90
  once: true
  requires:
    - inspect_rgb
    - cut_stem
  procedure:
    intent: cut_above_verified_node
    parameters:
      node: 5
  verify:
    - expected: cut_confirmed
      min_confidence: 0.97
  on_failure: safe_abort_and_request_review
```

The runtime converts this intent into a hardware-specific plan only after compatibility and safety checks.

## Lighting

GrowSpec should express plant demand such as:

- photoperiod bounds
- DLI target/range
- stage-specific targets

SeedOS combines measured natural light and supplemental light.

## Nutrition

GrowSpec expresses bounded targets such as:

- EC range/target
- pH range/target
- solution temperature
- optional stage-specific nutrient profile identifier

The GrowSpec does not say “run pump for 4.3 seconds.” The fluid controller determines bounded dosing from reservoir volume, concentrate identity, calibration, and current measurements.

## Evidence

A released GrowSpec should carry:

- author/source
- version
- compatible hardware assumptions
- evidence level
- known limitations
- outcome metrics where available
