---
tracker_id: ""
id: 3
type: story
title: "Check route serviceability"
parent: "epic-rider-trip-setup"
covers: ["R4"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "medium"
---

# Check route serviceability

## Description

As a rider, I want the app to validate pickup and destination before I request so that I know whether the trip can be served.

## Verify

Given a serviceable pickup and destination, when validation completes, then trip setup can continue to ride options.

## References

- parent — epic-rider-trip-setup/epic-rider-trip-setup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R4)
   **Given** a serviceable pickup and destination
   **When** validation completes
   **Then** trip setup can continue to ride options.
2. **Criterion 2** (R4)
   **Given** an unsupported pickup, destination, or route
   **When** validation completes
   **Then** the rider sees a clear explanation and can edit the location.
3. **Criterion 3** (R4)
   **Given** the app suggests a nearby pickup
   **When** the rider has not confirmed it
   **Then** the suggested location is not silently substituted.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-1 launch zones and OQ-12 rider research.
