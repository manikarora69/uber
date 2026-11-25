---
tracker_id: ""
id: 1
type: story
title: "Track trip progress"
parent: "epic-in-trip-visibility-safety"
covers: ["R12"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Track trip progress

## Description

As a rider, I want current trip status, route, destination, and ETA so that I can follow my journey.

## Verify

Given a trip is active, when trip data is current, then the rider sees status, destination, route, and estimated arrival.

## References

- parent — epic-in-trip-visibility-safety/epic-in-trip-visibility-safety.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R12)
   **Given** a trip is active
   **When** trip data is current
   **Then** the rider sees status, destination, route, and estimated arrival.
2. **Criterion 2** (R12)
   **Given** location/network updates stop
   **When** the trip screen remains open
   **Then** last-known information remains visible with its last update time.
3. **Criterion 3** (R12)
   **Given** connectivity returns
   **When** current trip state is retrieved
   **Then** the rider sees the authoritative state rather than a stale local state.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-7 device/network scope, OQ-11 performance and recovery budgets.
