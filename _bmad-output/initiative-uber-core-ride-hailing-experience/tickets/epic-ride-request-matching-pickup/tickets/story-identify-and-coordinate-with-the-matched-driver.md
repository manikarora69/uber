---
tracker_id: ""
id: 3
type: story
title: "Identify and coordinate with the matched driver"
parent: "epic-ride-request-matching-pickup"
covers: ["R9", "R10"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Identify and coordinate with the matched driver

## Description

As a rider, I want to see the matched driver's details and approach and contact them safely so that I can meet the correct vehicle.

## Verify

Given a driver accepts, when the match is shown, then the driver's name and photo where available, plus vehicle make, model, color, and registration identifier as permitted by market policy, are displayed.

## References

- parent — epic-ride-request-matching-pickup/epic-ride-request-matching-pickup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R9)
   **Given** a driver accepts
   **When** the match is shown
   **Then** the driver's name and photo where available, plus vehicle make, model, color, and registration identifier as permitted by market policy, are displayed.
2. **Criterion 2** (R9)
   **Given** driver location updates arrive
   **When** the vehicle approaches
   **Then** the map and pickup ETA update without the rider reopening the screen.
3. **Criterion 3** (R10)
   **Given** the rider contacts the driver
   **When** an in-app channel is supported
   **Then** contact uses that channel and masks personal contact details where supported.
4. **Criterion 4** (R10)
   **Given** pickup PIN verification is enabled
   **When** the trip is started
   **Then** required verification is complete first.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-5 pickup PIN policy; OQ-6 market safety/communications capabilities; OQ-7 localization and supported devices.
