# Contributing to Seedle

Seedle welcomes design, software, horticulture, robotics, controls, manufacturing, data, and safety contributions.

## Start with the contract

Before proposing implementation changes, read:

- `README.md`
- `docs/PRODUCT.md`
- `docs/ARCHITECTURE.md`
- `docs/SAFETY.md`
- `specs/GROWSPEC.md`
- `specs/MODULESPEC.md`

## Contribution principles

- Do not invent horticultural numbers and present them as validated.
- Separate assumptions from measurements.
- Prefer capabilities over hardware-specific coupling.
- Preserve offline-safe operation.
- Do not let community files bypass safety limits.
- Serviceability is a design requirement, not an afterthought.
- Every new serviceable module should declare how it is reached, isolated, removed, installed, and verified.
- Every crop automation should define how success is verified and how failure becomes safe.

## Evidence labels

Use clear language:

- **concept** — design hypothesis
- **simulated** — tested only in software/model
- **bench-tested** — tested on a controlled rig
- **crop-tested** — completed real crop cycles
- **verified** — passed defined validation criteria

Do not blur these states.

## Changes to GrowSpec / ModuleSpec

Schema changes should include:

1. rationale
2. backward-compatibility impact
3. updated examples
4. validation tests once tooling exists

## Hardware files

Future hardware contributions should include source CAD whenever possible, not only exported meshes, plus:

- material
- print/manufacturing process
- orientation
- load/contact assumptions
- service geometry
- relevant safety considerations

## Security

Do not publish secrets, private household data, API keys, Wi-Fi credentials, or device credentials.
