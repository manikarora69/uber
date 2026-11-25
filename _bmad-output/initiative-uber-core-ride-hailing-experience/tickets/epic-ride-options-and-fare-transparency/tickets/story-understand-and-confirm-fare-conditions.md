---
tracker_id: ""
id: 2
type: story
title: "Understand and confirm fare conditions"
parent: "epic-ride-options-and-fare-transparency"
covers: ["R6"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Understand and confirm fare conditions

## Description

As a rider, I want to see known fare components and any high-demand price before requesting so that I can make an informed choice.

## Verify

Given an estimate is shown, when the rider reviews it, then known fare components and applicable fees are available before confirmation.

## References

- parent — epic-ride-options-and-fare-transparency/epic-ride-options-and-fare-transparency.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R6)
   **Given** an estimate is shown
   **When** the rider reviews it
   **Then** known fare components and applicable fees are available before confirmation.
2. **Criterion 2** (R6)
   **Given** dynamic/high-demand pricing applies
   **When** the rider reviews the request
   **Then** the applicable price or multiplier is disclosed before the request is submitted.
3. **Criterion 3** (R6)
   **Given** dynamic/high-demand pricing applies
   **When** the rider has not confirmed the displayed offer
   **Then** the request is not submitted.
4. **Criterion 4** (R6)
   **Given** the final fare may differ
   **When** the estimate is presented
   **Then** the conditions under which it may change are disclosed.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-2 categories, OQ-4 fare/fee policy, OQ-8 targets and guardrails.
