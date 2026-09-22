# Seedle Safety Model

Seedle contains water, electricity, batteries, moving machinery, cutting tools, pumps, nutrients, heaters/lights, and food-contact systems. Safety must be architectural.

## Authority hierarchy

```text
Emergency / hardwired protection
        ↓
Safety supervisor
        ↓
Motion / fluid / energy controllers
        ↓
SeedOS capability layer
        ↓
GrowSpec / household plan
        ↓
community content
```

Lower layers cannot override higher safety authority.

## Minimum hazard classes

### Motion

- pinch/crush
- unexpected gantry movement
- collision with service robot
- dropped modules

Controls:

- bounded work envelopes
- position verification
- current/force limits
- guarded service modes
- safe homing
- independent stop path

### Cutting tools

Controls:

- tool identity verification
- guarded parking
- no free-form community motor commands
- vision target confidence threshold
- exclusion zones
- approach verification
- post-cut inspection
- abort/retract behavior

### Water and electricity

Controls:

- separated wet/dry zones
- leak detection
- drain paths
- isolated low-voltage wet-zone distribution where practical
- ground-fault protection as appropriate
- battery compartment separation
- no water line routed such that one leak can flood the power bay

### Nutrient/pH dosing

Controls:

- bounded maximum dose per action/time window
- independent volume accounting
- sensor plausibility checks
- mix/wait/re-measure
- lockout on disagreement
- manual recovery
- chemical incompatibility rules

### Lighting/heat

Controls:

- temperature feedback
- over-temperature cutoff
- fixture/module identity
- plant-safe and enclosure-safe limits
- fire-conscious materials and clearances

### Food/water contact

Production materials/processes must be validated for the intended contact conditions, cleaning chemistry, temperature, and lifetime.

Do not equate “printable” with “sanitary.”

### Biological hazards

Track:

- standing-water risk
- pathogen/sanitation cycles
- diseased crop isolation
- mold/humidity
- root decomposition
- cross-contamination from cutting tools

## Fail-safe crop survival

A sophisticated automation failure should not immediately kill the garden.

Preferred fallbacks:

- gravity or redundant emergency water path where practical
- independent aeration reserve
- battery-backed control for safe shutdown
- passive ventilation/safe shutter pose
- enough local state to maintain basic crop life offline

## Human recovery

Even a highly autonomous Seedle requires external manual access for:

- emergency stop
- power isolation
- drain
- battery service
- reservoir cleaning
- service bay access
- robot recovery

Closed-loop autonomy must not make the machine impossible to safely repair by a trained human.
