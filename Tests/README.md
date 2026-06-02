# Tests

Tests mirror [`Sources/`](../Sources/), focused on the invariants that actually matter
(safety rules, correctness of core logic). They run in CI.

Pair unit tests with the **headless self-test** mode (see `Sources/`) for behavior that's
awkward to unit-test but still checkable without a GUI.

> Delete this README once real tests exist.
