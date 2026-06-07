# Architecture

The evolving system design for noribento — modules, data flow, threading, and any
render/update loop. Keep this current as the design changes (see the
[maintenance protocol](README.md)).

> Early-stage placeholder. Replace with the real design as it emerges. The locked
> constraints it must respect live in [decisions.md](decisions.md).

## Overview

<!-- One paragraph: what the system is and how its parts fit together. -->

## Modules

<!--
Product code is grouped by responsibility — one directory per architectural layer under
Sources/, named for what it does. List the layers here as they appear, e.g.:

- `Sources/noribento/<Layer>/` — <responsibility>
-->

## Data flow

<!-- How information moves through the system: inputs → processing → output/render. -->

## Concurrency / threading

<!-- Which work runs where; main-thread-safety rules; any serial queues or loops. -->

## Entry points

<!-- The app bootstrap, and the headless self-test path that CI runs without a GUI. -->

## Platform & portability

Per [D2](decisions.md#d2--platform-posture-unix-first-cross-system), the system is
**unix-first and cross-system** (Linux primary, macOS supported). Design implications:

- The core must not hard-depend on macOS-only APIs. Per-OS integration (e.g. the
  display-server / window-server layer — X11/Wayland on Linux vs the macOS window server)
  sits behind a platform boundary so the rest of the system is OS-agnostic.
- macOS-specific capabilities are **availability-gated enhancements** with a working
  cross-system fallback (degraded, not broken).
- Build/dev tooling and CI stay POSIX-portable and run on a cross-system matrix.
