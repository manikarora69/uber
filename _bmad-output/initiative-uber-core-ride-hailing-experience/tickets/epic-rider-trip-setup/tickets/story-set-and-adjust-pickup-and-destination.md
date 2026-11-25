---
tracker_id: ""
id: 2
type: story
title: "Set and adjust pickup and destination"
parent: "epic-rider-trip-setup"
covers: ["R3"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Set and adjust pickup and destination

## Description

As a rider, I want to set my pickup and destination using location, search, or the map so that I can define where I need to go.

## Verify

Given foreground location permission and adequate location accuracy, when the rider opens trip setup, then current location is suggested as pickup and can be reviewed or moved.

## References

- parent — epic-rider-trip-setup/epic-rider-trip-setup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R3)
   **Given** foreground location permission and adequate location accuracy
   **When** the rider opens trip setup
   **Then** current location is suggested as pickup and can be reviewed or moved.
2. **Criterion 2** (R3)
   **Given** location permission is denied or unavailable
   **When** the rider sets a pickup
   **Then** manual search and map selection remain available.
3. **Criterion 3** (R3)
   **Given** the rider selects a search result or moves a pin
   **When** the selection is confirmed
   **Then** the displayed address and selected coordinates update together.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-1 launch zones; OQ-7 supported devices/network and languages; OQ-12 observed rider journeys.
