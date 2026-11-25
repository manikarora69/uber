---
tracker_id: ""
id: 1
type: story
title: "Submit one ride request"
parent: "epic-ride-request-matching-pickup"
covers: ["R7"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Submit one ride request

## Description

As a rider, I want my confirmed ride request to be created once so that retries do not book duplicate rides.

## Verify

Given a valid authenticated rider, serviceable route, selected category, and eligible payment arrangement, when the rider confirms, then one uniquely identified request is created.

## References

- parent — epic-ride-request-matching-pickup/epic-ride-request-matching-pickup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R7)
   **Given** a valid authenticated rider, serviceable route, selected category, and eligible payment arrangement
   **When** the rider confirms
   **Then** one uniquely identified request is created.
2. **Criterion 2** (R7)
   **Given** the same request submission is repeated
   **When** the same idempotency key is received
   **Then** the existing request is returned and no second active request is created.
3. **Criterion 3** (R7)
   **Given** required request data is missing or invalid
   **When** submission is attempted
   **Then** the request is not created and the rider is told what to correct.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-1 zones, OQ-2 categories, OQ-3 payment arrangements.
