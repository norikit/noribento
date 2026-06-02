# Sources

Product code lives here. Organize it by **responsibility — one directory per architectural
layer**, each named for what it *does* (not by file type).

Always keep:

- a **single, clear entry point** (the app bootstrap), and
- a **headless self-test path** — a mode that exercises the core invariants without a
  GUI/window, so CI can run it.

Throwaway PoC/research code does **not** belong here — it lives in `tasks/<id>/code/`.

> Delete this README once real source exists (or keep a short orientation note). Add your
> stack's build manifest at the repo root and wire `Sources/` + `Tests/` into it.
