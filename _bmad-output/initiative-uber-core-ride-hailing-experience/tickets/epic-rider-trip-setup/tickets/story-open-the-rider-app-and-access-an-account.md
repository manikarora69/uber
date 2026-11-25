---
tracker_id: ""
id: 1
type: story
title: "Open the rider app and access an account"
parent: "epic-rider-trip-setup"
covers: ["R1"]
sources: []
companions: []
after: []
assignee: ""
refined: true
hitl: false
risk: "high"
---

# Open the rider app and access an account

## Description

As a rider, I want to register or sign in securely so that I can start booking.

## Verify

Given a clean baseline build, when it is deployed and opened, then the rider sees sign-in and registration entry points.

## References

- parent — epic-rider-trip-setup/epic-rider-trip-setup.md#Requirements
- initiative — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements

## Acceptance criteria

1. **Criterion 1** (R1)
   **Given** a clean baseline build
   **When** it is deployed and opened
   **Then** the rider sees sign-in and registration entry points.
2. **Criterion 2** (R1)
   **Given** a supported phone number and valid verification code
   **When** verification succeeds
   **Then** the rider receives an authenticated session.
3. **Criterion 3** (R1)
   **Given** an invalid or expired code
   **When** submitted
   **Then** no session is created and the rider sees a recoverable error.
4. **Criterion 4** (R1)
   **Given** an account-recovery attempt
   **When** the phone number is or is not registered
   **Then** the response does not reveal registration status.

## Boundaries

- Adjacent behavior owned by sibling stories stays intact; this story implements only the outcome above.
- Must preserve idempotency, privacy, accessibility, and market-specific behavior where applicable.

## Notes

- Open question: OQ-7 supported OS/device and accessibility scope.
