---
tracker_id: ""
id: 2
type: story
title: "Follow matching and recover from cancellation"
parent: "epic-ride-request-matching-pickup"
covers: ["R8", "R11"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Follow matching and recover from cancellation

## Description

As a rider, I want clear matching, no-driver, and cancellation states so that I know what happened and what I can do next.

## Verify

Given a request is pending, when matching is in progress, then the app shows that status and keeps it current.

## References

- parent — epic-ride-request-matching-pickup/epic-ride-request-matching-pickup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R8)
   **Given** a request is pending
   **When** matching is in progress
   **Then** the app shows that status and keeps it current.
2. **Criterion 2** (R8)
   **Given** no eligible driver accepts within the configured window
   **When** matching ends
   **Then** the rider sees the outcome and can retry or change category/pickup where supported.
3. **Criterion 3** (R8)
   **Given** a driver cancels after matching
   **When** the cancellation is received
   **Then** rematching starts where supported or the rider receives a clear recovery option
4. **Criterion 4** (R11)
   **Given** the rider chooses to cancel
   **When** a fee applies
   **Then** the fee is shown before confirmation

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-1 zones, OQ-2 categories, OQ-4 cancellation fees, OQ-5 pickup verification, OQ-10 support coverage.
