# Defense In Depth

When a bug is caused by invalid data or unsafe state, validate at more than one meaningful layer.

## Typical Layers

- entry validation
- business logic validation
- environment guards
- durable observability

The goal is not one lucky check. The goal is to make the bug structurally harder to repeat.
