# Seedle Build Requirements

This document defines what is required to physically build **Seedle P1**, the 1–5 plant prototype, and what additional systems are required later to reach the full Seedle vision.

The purpose of P1 is not to feed a household. It is to prove the smallest complete autonomous growing loop using the same architectural ideas that can later scale.

---

# 1. Build target

## Seedle P1

Capacity:

- 1–5 simultaneous plants
- hydroponic / media-minimized root zones
- shared or zoned nutrient solution
- automatic light control
- automatic nutrient monitoring and bounded dosing
- camera-based plant inspection
- compact crop-head motion above the plants
- tool docking
- removable grow modules
- basic robotic/service access
- SeedOS + GrowSpec + ModuleSpec
- local telemetry and event logging
- safe manual recovery

P1 should be compact enough to fit on:

- a bench
- rolling cart
- dedicated stand
- small indoor test enclosure

The physical prototype should be modular so subsystems can be replaced without rebuilding the entire machine.

---

# 2. What should NOT be built first

Do not spend early prototype money on:

- full-size greenhouse dome
- large solar array
- household-scale battery system
- full autonomous maintainer arm
- plastic shredder/recycler
- meal-per-day capacity
- large harvest refrigerator
- dozens of grow cells
- custom production circuit boards
- custom injection-molded parts
- decorative exterior shell

Those belong after P1 proves the core growing and automation loops.

---

# 3. Structural system

P1 needs a rigid frame supporting the grow deck, overhead motion system, lights, cameras, and service access.

## Required

- aluminum extrusion, tube, or equivalent rigid frame
- corner brackets / printed structural connectors where appropriate
- adjustable feet or rolling-locking casters
- upper bridge support for crop gantry
- lower shelf/service bay
- removable side/service panels
- drip/water containment tray

## Design requirements

The frame must:

- resist gantry movement without excessive flex
- tolerate wet/humid operation
- provide open maintenance access
- allow removal of every grow cell
- provide cable and tube routing
- keep electrical equipment away from likely leak paths
- leave room for future service rails or maintainer mechanisms

---

# 4. Grow deck and plant modules

P1 should use individual grow cells rather than one permanent grow bed.

## Quantity

Build:

- 1 initial cell
- expand to 5 identical or compatible cells

## Each grow cell requires

- upper plant/crown support
- dark root chamber
- removable/openable root cartridge or chamber
- nutrient inlet
- return/drain outlet
- overflow path
- root/debris guard
- cell identification marker
- service latch
- defined robotic/manual grasp point
- drainable geometry
- wash/sanitize access

## Root chamber design goals

Avoid fine permanent mesh that mature roots can weave through.

Prefer:

- smooth walls
- large openings
- openable clamshell geometry
- removable crown collar
- root separation between neighboring plants
- downward gravity release
- accessible root cutting/release path where appropriate

## Printed parts

Likely printable:

- crown collars
- grow-cell housings
- root-chamber shells
- clips
- brackets
- tube guides
- sensor holders
- drain guards
- service latches
- camera markers

Wet-path printed materials must be treated as experimental until the chosen material/process is validated for the intended water, nutrient, temperature, sanitation, and food-contact conditions.

---

# 5. Water and hydroponic system

## Required hardware

- main reservoir
- reservoir lid
- circulation pump
- aeration pump or equivalent oxygenation
- air stone/diffuser if used
- distribution manifold
- tubing
- return plumbing
- shutoff valves
- check valves where required
- quick-disconnects
- drain valve
- overflow protection
- coarse root/debris screen
- replaceable filter stage
- leak tray
- leak sensors

## Recommended P1 architecture

```text
reservoir
   ↓
circulation pump
   ↓
distribution manifold
   ↓
1–5 grow cells
   ↓
root/debris separation
   ↓
filter
   ↓
reservoir
   ↺
```

The plumbing should be visible and serviceable during P1.

Do not hide tubing behind permanent panels.

---

# 6. Nutrient dosing system

P1 should eventually support closed-loop nutrient control, but this should be added incrementally.

## Sensors

At minimum:

- EC sensor
- pH sensor
- nutrient solution temperature sensor
- reservoir level sensor

Useful later:

- dissolved oxygen
- flow sensor
- individual cell flow confirmation

## Dosing hardware

Potential dosing channels:

- nutrient concentrate A
- nutrient concentrate B
- pH adjustment channel(s), only with strong safety limits
- makeup water

Hardware:

- small calibrated peristaltic dosing pumps
- chemical-resistant tubing
- individual chemical containers
- labeled connections
- anti-siphon protection
- spill containment

## Control rule

The controller must:

1. measure
2. validate readings
3. calculate a bounded dose
4. dose a small amount
5. mix
6. wait
7. measure again
8. stop on disagreement

No GrowSpec may directly command an arbitrary pump duration.

---

# 7. Environmental sensors

P1 should measure:

- air temperature
- relative humidity
- root solution temperature
- ambient/light intensity
- reservoir level
- leak state

Useful expansion sensors:

- CO₂
- leaf temperature
- dissolved oxygen
- water flow
- pressure
- individual cell temperature
- enclosure temperature zones

---

# 8. Lighting system

P1 needs supplemental LED lighting even if it is tested near natural sunlight.

## Required

- dimmable horticultural LED fixture or bars
- mounting structure
- controllable power driver
- light sensor / PAR-capable measurement strategy if practical
- fixture temperature monitoring
- independent over-temperature cutoff

## SeedOS behavior

Lighting should eventually be controlled by crop demand rather than only clock time.

The system should record:

- natural light received
- supplemental light delivered
- active photoperiod
- energy consumed

P1 can begin with simpler control and move toward DLI-based operation after sensing is validated.

---

# 9. Crop observation and machine vision

## Required

- overhead RGB camera
- controlled inspection lighting
- stable camera mount
- fiducial/position markers
- local image storage for debugging

Useful later:

- second side-view camera
- root-zone inspection camera
- depth camera
- multispectral camera

## Vision jobs

Eventually:

- plant presence
- growth tracking
- node detection
- flower detection
- fruit detection
- ripeness estimate
- leaf health
- target selection for pruning
- post-action verification

P1 should begin with simple repeatable camera geometry before attempting complex AI vision.

---

# 10. Crop gantry

The crop head must operate over all 1–5 plant positions.

## Required motion

A small P1 can use:

- XY motion with fixed tool height
- XYZ motion if vertical positioning is necessary

## Likely components

- stepper motors
- motor drivers
- belts or lead screws
- linear rails / rollers
- limit switches or homing sensors
- position reference markers
- cable management
- rigid carriage
- tool mount

## Requirements

- repeatable addressing of every grow cell
- safe homing
- known work envelope
- collision limits
- current/force monitoring where possible
- manual emergency release/recovery

---

# 11. Tool changer

P1 does not need every final Seedle head.

Start with a small universal tool interface.

## Initial tools

### Tool 1 — camera/inspection head

Functions:

- plant inspection
- calibration
- target confirmation

### Tool 2 — seed/placement head

Functions:

- seed pickup
- placement into crown/start position

### Tool 3 — simple non-cutting manipulator

Functions:

- move light plant supports
- interact with calibration targets
- test docking mechanics

## Later tools

- pollination/vibration head
- soft gripper
- scissors/cutter
- harvest gripper
- cleaning head
- root-release tool

## Tool interface requirements

- mechanical alignment
- positive lock
- tool identity
- power
- data if required
- optional air/fluid interface
- robotic pickup/release
- known calibration offset

---

# 12. Maintenance-access system

P1 does not need a full autonomous maintainer arm, but it must be physically designed around future robotic maintenance.

## P1 must include

- defined service faces
- removable modules
- front/side access to pumps and filters
- under-cell service access
- standardized quick-disconnects
- maintenance clearance
- service lift/slot concept if used later
- external human recovery access

## Serviceable modules should include

- pump cartridge
- filter cartridge
- sensor cartridge
- grow cell
- tool head
- camera
- lighting module
- valve assembly

## Every module should eventually declare

- who services it
- approach direction
- service face
- clearance
- isolation steps
- disconnects
- removal path
- install path
- calibration procedure
- verification procedure

---

# 13. Computer and control hardware

P1 should separate high-level planning from real-time hardware control.

## High-level computer

Possible class:

- Raspberry Pi
- mini PC
- similar Linux-capable SBC

Responsibilities:

- SeedOS
- GrowSpec runtime
- database
- web UI
- camera processing
- telemetry
- planning
- network/community synchronization

## Real-time controller

Possible class:

- ESP32
- RP2040
- STM32
- equivalent microcontroller

Responsibilities:

- pump/valve control
- sensor reads
- stepper/servo control
- hard timing
- watchdog
- emergency/fail-safe states

## Important architecture rule

The high-level computer requests bounded actions.

The real-time/safety controller owns local physical limits.

---

# 14. Electrical system

## Required

- AC input or bench power source
- fused main input
- low-voltage DC power supplies
- separate logic and higher-current rails where useful
- terminal blocks
- labeled wiring
- cable glands
- strain relief
- relay/MOSFET modules appropriate to loads
- emergency stop
- disconnect switch
- leak-safe cable routing
- grounded metal structure where appropriate
- protected lighting power
- protected pump power

## Prototype philosophy

P1 should be easy to inspect electrically.

Avoid a sealed custom wiring harness until the circuit is stable.

---

# 15. Safety hardware

P1 should include physical safeguards from the beginning.

## Minimum

- emergency stop
- main power disconnect
- reservoir overflow path
- leak detection
- drip containment
- independent maximum-temperature protection for lights/heaters
- bounded dosing
- chemical containers physically separated
- cutting tools omitted until later guarded phase
- motion homing/limits
- accessible manual drain
- external manual service access

## Before adding scissors/cutters

Add:

- guarded tool dock
- tool presence detection
- positive target confirmation
- collision/exclusion zones
- safe retract behavior
- dedicated hardware/software interlock

---

# 16. 3D-printing capability

P1 should be designed around local fabrication.

## Required equipment

- reliable FDM printer
- appropriate nozzle sizes
- filament drying/storage
- digital calipers
- deburring tools
- heat-set insert tooling if inserts are used
- spare nozzles
- build surfaces
- filament/material samples

## Likely printable parts

- grow cells
- root modules
- tool bodies
- camera mounts
- brackets
- sensor holders
- cable/tube guides
- quick-change prototypes
- actuator housings
- calibration fixtures
- service handles

## Materials to experiment with

Material choice must be validated for each use.

Possible prototype materials may include:

- PETG
- ASA
- PP
- other suitable engineering polymers

Do not assume a filament is acceptable for long-term nutrient-water or food-contact use solely because the base polymer is commonly used elsewhere.

---

# 17. Fabrication tools

Useful workshop equipment:

- FDM printer
- soldering iron
- multimeter
- wire stripper/crimper
- ferrule crimper
- heat gun
- drill/driver
- drill bits
- taps/dies if metal threads are used
- hex keys
- screwdrivers
- small wrenches
- digital calipers
- ruler/tape measure
- square
- tubing cutter
- hobby knife
- deburring tool
- flush cutters
- zip ties / cable management
- label maker
- small scale
- measuring cylinders/syringes for calibration
- buckets/trays for wet testing

Helpful later:

- oscilloscope
- bench power supply
- logic analyzer
- thermal camera
- torque driver
- load cell
- force gauge

---

# 18. Software required

The exact implementation stack can be selected later, but P1 needs these software capabilities.

## SeedOS core

- device/module registry
- GrowSpec parser/validator
- crop-instance state
- scheduler
- telemetry/event store
- safety status
- resource state
- light controller
- nutrient controller
- motion task planner
- capability resolver
- manual override/recovery UI

## Simulation

Before real hardware:

- virtual grow cells
- virtual sensors
- virtual reservoir
- virtual tools
- virtual actuator state
- fault injection
- deterministic time
- replayable logs

## Web/app UI

At minimum:

- current plants
- plant stage
- sensor state
- reservoir state
- lighting state
- active/pending actions
- alarms
- manual safe controls
- maintenance state
- event history

## Data formats

- GrowSpec
- ModuleSpec
- device telemetry
- crop events
- harvest events
- maintenance events
- calibration records
- fault records

---

# 19. Development consumables

Keep on hand:

- seeds for selected prototype crops
- hydroponic nutrients
- pH calibration solutions
- EC calibration solution
- pH probe storage solution
- distilled/deionized water for calibration where required
- tubing
- fittings
- spare pumps
- spare sensors/probes
- filters
- food-safe/suitable cleaning materials
- gloves
- labels
- filament
- fasteners
- electrical connectors
- fuses

---

# 20. First crops

P1 should not begin with the most mechanically difficult crops.

Good early targets should have:

- compact size
- short crop cycle
- well-understood hydroponic behavior
- easy visual inspection
- manageable root volume
- simple manual harvest while automation is developed

A sensible progression is:

1. leafy green / herb for fluid and light control
2. compact flowering/fruiting plant for pollination and vision
3. compact tomato/pepper-type crop for pruning/harvest experiments

Specific crop varieties and nutrient/light targets should be validated rather than guessed.

---

# 21. Suggested P1 physical layout

```text
            overhead light
                 │
      ┌─────────────────────┐
      │ compact XY/XYZ head │
      └─────────────────────┘
          ↓   ↓   ↓   ↓   ↓
        [1] [2] [3] [4] [5]
        grow cells / plants
      ───────────────────────
        under-cell plumbing
      ───────────────────────
       reservoir / pumps
       sensors / dosing
       computer / controller
       electrical service bay
```

Keep the machine open and visible during development.

A beautiful enclosure comes later.

---

# 22. P1 minimum viable BOM categories

The first purchasing plan should include roughly:

## Structure

- frame material
- brackets
- fasteners
- feet/casters
- drip tray

## Grow system

- 5 grow-cell prototypes
- reservoir
- lid
- tubing
- manifolds
- valves
- filters
- pumps
- aeration

## Sensors

- pH
- EC
- water temperature
- air temperature/humidity
- level
- leak
- light

## Control

- Linux SBC/mini PC
- microcontroller
- motor drivers
- relay/MOSFET outputs
- power supplies

## Motion

- stepper motors
- rails/rollers
- belts/lead screws
- homing switches
- carriage
- tool dock

## Vision

- camera
- inspection light

## Lighting

- dimmable grow light
- driver/controller

## Fabrication

- printer/material
- hardware inserts/fasteners
- printed prototype components

## Safety

- emergency stop
- fuses
- main disconnect
- containment
- protected electrical enclosures

## Calibration

- pH standards
- EC standard
- measurement tools

---

# 23. Full Seedle systems required later

Once P1 works reliably, the complete Seedle concept adds the following.

## Larger grow capacity

- modular 8/16+ cell extensions
- multiple nutrient zones
- larger crop gantry
- larger harvest queue

## Full maintenance robotics

- maintainer arm
- vertical service spine
- under-bed service carriage
- upper service carriage
- robotic module storage
- calibration/service stations
- part transfer system

## Active dome

- transparent structure
- rotating solar shutter blades
- shutter actuators
- weather sensing
- snow/wind strategy
- active vents
- insulation strategy
- thermal storage
- rainwater handling

## Energy

- solar array / solar shutters
- charge controller
- battery
- inverter if required
- DC distribution
- energy forecasting

## Fabrication cell

- enclosed printer
- automated print removal
- part inspection
- part storage
- vitamin inventory

## Future recycling

- failed-part sorting
- shredding
- drying
- pelletizing/extrusion
- material-quality tracking

This should come only after it is proven that recycling does not reduce part reliability below acceptable levels.

## Food handling

- harvest transfer
- food-safe collection bin
- optional cooled buffer
- crop-specific storage logic
- spoilage detection

## Household intelligence

- Family Adapt
- recipe demand
- usage learning
- capacity planning
- expansion recommendation

## Community system

- GrowSpec sharing
- ModuleSpec sharing
- design files
- evidence bundles
- compatibility testing
- staged validation
- verified upgrades

---

# 24. Recommended build order

## Step 1

Build software simulator.

## Step 2

Build one hydroponic grow cell manually.

## Step 3

Instrument that cell.

## Step 4

Let SeedOS control water/light/nutrient targets.

## Step 5

Expand to 3–5 grow cells.

## Step 6

Add overhead camera motion.

## Step 7

Add tool changer.

## Step 8

Add one non-cutting crop intervention.

## Step 9

Add guarded pruning/harvest tooling.

## Step 10

Add removable/serviceable fluid modules.

## Step 11

Demonstrate one closed maintenance loop.

## Step 12

Run multiple complete crop cycles.

## Step 13

Only then design the larger enclosure, solar roof, and household-scale system.

---

# 25. Definition of “P1 works”

Seedle P1 is successful when it can maintain 1–5 real plants through complete supported crop cycles while:

- controlling the root-zone environment
- accounting for light
- maintaining safe nutrient conditions
- tracking each plant individually
- moving its crop head repeatably
- changing supported tools
- making only verified plant interventions
- logging every important decision
- recovering safely from faults
- allowing modules to be serviced without dismantling the machine
- reducing human intervention with each iteration

The first victory is not pounds of food.

The first victory is:

> **five living plants being maintained by the same architecture that can eventually maintain fifty or five hundred.**
