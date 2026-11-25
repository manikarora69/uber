---
tracker_id: ""
id: 2
type: story
title: "Rate a trip and resolve an issue"
parent: "epic-trip-completion-and-aftercare"
covers: ["R17", "R18"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Rate a trip and resolve an issue

## Description

As a rider, I want to rate a completed trip, report an issue, and track support so that I can give feedback and get a response.

## Verify

Given a completed trip, when the rider submits a rating, then one rating is associated with that trip; optional structured/free-text feedback can be added.

## References

- parent — epic-trip-completion-and-aftercare/epic-trip-completion-and-aftercare.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R17)
   **Given** a completed trip
   **When** the rider submits a rating
   **Then** one rating is associated with that trip
2. **Criterion 2** (R17)
   **Given** the rider reports a safety, conduct, lost-item, fare, payment, or trip issue
   **When** the report is submitted
   **Then** it is linked to the correct trip and the rider receives confirmation.
3. **Criterion 3** (R18)
   **Given** support case tracking is enabled
   **When** the case changes
   **Then** the rider can view the response and current status

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-6 safety queues, OQ-9 data retention, OQ-10 response commitments.
