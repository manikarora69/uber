---
tracker_id: ""
id: 1
type: story
title: "Pay and review a completed trip"
parent: "epic-trip-completion-and-aftercare"
covers: ["R2", "R15", "R16"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Pay and review a completed trip

## Description

As a rider, I want a clear final fare, payment result, and receipt so that I can verify and retain the trip record.

## Verify

Given a trip completes, when the final fare is available, then the rider sees an itemized fare consistent with the payment record, plus trip date, route summary, payment method, and support path on the receipt.

## References

- parent — epic-trip-completion-and-aftercare/epic-trip-completion-and-aftercare.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R15)
   **Given** a trip completes
   **When** the final fare is available
   **Then** the rider sees an itemized fare consistent with the payment record, plus trip date, route summary, payment method, and support path on the receipt.
2. **Criterion 2** (R16)
   **Given** payment succeeds or fails
   **When** processing completes
   **Then** the payment state is explicit and an eligible retry or alternative is available after failure.
3. **Criterion 3** (R16)
   **Given** payment is retried
   **When** the same transaction is processed again
   **Then** no duplicate successful charge is created.
4. **Criterion 4** (R2)
   **Given** a completed or cancelled trip appears in history
   **When** the rider opens it
   **Then** route summary, date, status, fare, and receipt access are available where applicable.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-3 payment methods, OQ-4 fare policy, OQ-11 performance/recovery budgets.
