# Condition-Based Waiting

Do not guess timing with arbitrary sleeps when you can wait for the actual condition you care about.

## Use When

- tests are flaky because of timing
- async work must complete before assertion
- browser or integration flows race under load

## Rule

Wait for the state, event, or observable condition directly.
