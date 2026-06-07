# Decisions — noribento

Locked architectural decisions. Treat as constraints; relitigate only with explicit owner direction.

## D1 — Standalone-first (inherited prime directive #10)
**Decision:** noribento runs fully on its own; norikit ecosystem integrations are **optional,
availability-gated progressive enhancements** — never hard dependencies.
**Rationale:** ecosystem mission directive #10 — usable standalone, better together.

## D2 — Platform posture: unix-first, cross-system
**Decision (owner, 2026-06-07):** noribento — **and all of its tooling** — is **unix-first
and cross-system**. The product and every build/dev tool must run across unix-like systems
(**Linux primary, macOS supported**), and the ecosystem setup must work on every supported
system. macOS-specific capabilities are **optional, availability-gated enhancements** layered
on the cross-system core — never the floor, never required.
**Rationale:** Reverses the prior native-macOS-only framing. Applies the standalone-first
pattern ([D1](#d1--standalone-first-inherited-prime-directive-10)) at the platform level —
*runs everywhere unix, better on Mac* — and is consistent with mission directive #1 ("native
to the platform you target," not macOS-forever) and directive #5 (graceful degradation: gate
OS-specific capability behind availability checks; degraded, not broken).
**Implications:**
- No hard dependency on macOS-only APIs on the common path; any such use must be
  capability-gated with a working cross-system fallback.
- Tooling/CI must be POSIX-portable — no macOS-only assumptions (paths, `osascript`,
  Apple-only toolchains) in anything on the common path. CI targets a cross-system matrix
  (Linux-primary, macOS-supported).
- The OS floor and per-platform display-server integration (X11/Wayland on Linux, the macOS
  window-server path) are detailed under [D3](#d3--stack--uiconfig--pending) / architecture
  as the stack lands.
**Ecosystem follow-up (out of this repo):** the org-level reversal of mission directive #1
and the "native macOS suite" framing lives in `norikit/norikit/ai-docs/` and is tracked
separately.

## D3 — Stack & UI/config — *pending*
_Pending owner input (language/stack, rendering/UI approach, config model, noriglaze
integration). The platform posture is settled by [D2](#d2--platform-posture-unix-first-cross-system);
record the remaining day-one decisions here and mirror the headlines in CLAUDE.md._
