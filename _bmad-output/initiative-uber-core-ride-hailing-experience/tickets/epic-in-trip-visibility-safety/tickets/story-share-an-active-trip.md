---
tracker_id: ""
id: 2
type: story
title: "Share an active trip"
parent: "epic-in-trip-visibility-safety"
covers: ["R13"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Share an active trip

## Description

As a rider, I want to share approved trip details with someone I trust so that they can follow my journey.

## Verify

Given an active trip, when the rider selects sharing, then an available sharing method can be chosen from the trip screen.

## References

- parent — epic-in-trip-visibility-safety/epic-in-trip-visibility-safety.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R13)
   **Given** an active trip
   **When** the rider selects sharing
   **Then** an available sharing method can be chosen from the trip screen.
2. **Criterion 2** (R13)
   **Given** a share is created
   **When** the trusted contact opens it
   **Then** only approved trip information is exposed.
3. **Criterion 3** (R13)
   **Given** the share reaches its configured expiration
   **When** the contact opens the old share
   **Then** trip details are no longer available.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-6 sharing capabilities; OQ-9 privacy/retention policy.
