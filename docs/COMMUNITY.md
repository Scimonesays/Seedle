# Seedle Community Intelligence

Seedle's community system exists to improve real-world growing and hardware through evidence.

It is not an unrestricted remote-execution marketplace.

## Shared asset classes

### GrowSpecs

Versioned crop lifecycle specifications.

### ModuleSpecs

Versioned descriptions of physical modules, capabilities, service procedures, and compatibility.

### Designs

CAD/mesh/source files associated with a ModuleSpec.

### Outcome bundles

Anonymized, consented observations such as:

- crop/cultivar
- compatible hardware versions
- climate/environment class
- resource use
- harvest quantity
- crop health events
- failure modes
- maintenance
- recipe fulfillment

## Release states

Suggested progression:

1. **Draft** — author work only.
2. **Experimental** — explicitly opt-in; bounded to compatible systems.
3. **Community tested** — minimum comparable evidence threshold reached.
4. **Verified** — validation criteria and review passed.
5. **Recommended** — statistically and operationally preferable for a defined context.
6. **Deprecated/withdrawn** — known defect, safety issue, or superseded version.

Popularity alone must never produce `Recommended`.

## Hardware upgrade evaluation

A candidate module should be compared on metrics relevant to its function.

Example root cell:

- clean release rate
- clog rate
- sanitation cycle success
- print time
- material mass
- leak rate
- crop outcome
- service time
- failure rate

A design can be better in one dimension and worse in another. SeedOS should not compress all tradeoffs into a fake universal score.

## Grow recipe evaluation

Compare within compatible populations:

- cultivar
- hardware class
- environment
- crop stage
- production objective

Possible metrics:

- edible yield
- time to harvest
- energy
- water
- nutrient use
- disease/failure
- quality measurements where available

## Safety boundary

Community content may express desired crop/environment behavior but cannot bypass machine-level:

- actuator limits
- cutting interlocks
- dosing limits
- electrical/thermal limits
- battery safety
- sanitation requirements
- compatibility checks

## Privacy

Family Adapt data should default to local processing.

Community contribution should:

- be opt-in
- strip direct household identity where feasible
- report only fields required for the experiment
- allow withdrawal from future sharing
- distinguish raw local history from shared aggregate evidence

## Reproducibility

Each contributed result should reference immutable versions of:

- GrowSpec
- ModuleSpec(s)
- SeedOS release
- relevant calibration state
- crop/cultivar
- environment class

Otherwise the result cannot be meaningfully compared.
