---
tracker_id: ""
id: 1
type: story
title: "Compare available ride options"
parent: "epic-ride-options-and-fare-transparency"
covers: ["R5"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "medium"
---

# Compare available ride options

## Description

As a rider, I want to compare eligible ride categories, pickup ETAs, and attributes so that I can choose an option that fits my trip.

## Verify

Given a serviceable route, when ride options load, then only currently eligible and available categories are selectable.

## References

- parent — epic-ride-options-and-fare-transparency/epic-ride-options-and-fare-transparency.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R5)
   **Given** a serviceable route
   **When** ride options load
   **Then** only currently eligible and available categories are selectable.
2. **Criterion 2** (R5)
   **Given** an eligible category
   **When** it is displayed
   **Then** its fare estimate or range, pickup ETA, and relevant attributes appear in local formatting.
3. **Criterion 3** (R5)
   **Given** the rider selects a category
   **When** the choice is made
   **Then** the request summary reflects that selection.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-1 launch zones, OQ-2 MVP categories, OQ-7 localization/device scope, OQ-8 metric baselines.
