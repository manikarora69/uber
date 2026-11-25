---
tracker_id: ""
id: 3
type: story
title: "Reach safety help and report a mismatch"
parent: "epic-in-trip-visibility-safety"
covers: ["R14"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Reach safety help and report a mismatch

## Description

As a rider, I want to reach emergency/support options and report a driver or vehicle mismatch so that I can act when I feel unsafe.

## Verify

Given an active trip, when the rider opens safety help, then market-supported emergency and support actions are visible and accessible.

## References

- parent — epic-in-trip-visibility-safety/epic-in-trip-visibility-safety.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R14)
   **Given** an active trip
   **When** the rider opens safety help
   **Then** market-supported emergency and support actions are visible and accessible.
2. **Criterion 2** (R14)
   **Given** the rider reports a driver/vehicle mismatch
   **When** the report is submitted
   **Then** the trip context is attached and the rider receives a clear confirmation or next step.
3. **Criterion 3** (R14)
   **Given** emergency dispatch is not integrated for the market
   **When** assistance guidance is shown
   **Then** it does not promise dispatch that the product cannot provide.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-6 emergency/support capabilities and OQ-10 response/escalation coverage.
