---
tracker_id: ""
id: 3
type: epic
title: "Ride request, matching, and pickup"
parent: "initiative-uber-core-ride-hailing-experience"
covers: ["R7", "R8", "R9", "R10", "R11"]
sources: ["_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md"]
companions: []
after: [{epic: 2, needs: "Epic 2 provides a selected category and rider-confirmed price."}]
assignee: ""
refined: true
hitl: false
risk: high
---

# Ride request, matching, and pickup

## Description

A rider can create one request, understand matching and cancellation outcomes, and identify and meet the matched driver.   This epic derives its scope from the initiative requirements.

## Outcome

A rider can create one request, understand matching and cancellation outcomes, and identify and meet the matched driver.  

## Requirements

- R7 (parent R7): Rider can submit a uniquely identified request once; repeated submissions do not create duplicate active requests.
- R8 (parent R8): Product reports matching progress, match/no-driver outcome, driver cancellation, and recovery without stale request state.
- R9 (parent R9): After match, rider can view available driver/vehicle identifiers, current pickup ETA, and approach state.
- R10 (parent R10): Rider can coordinate pickup and reach the driver through supported in-app communication, masking personal contact details where supported.
- R11 (parent R11): Rider can cancel and understand any applicable fee before confirming cancellation where feasible.

## Constraints

- C1 (prd RULE-1): A request requires an authenticated rider, valid pickup/destination, eligible category, and market-approved payment arrangement.
- C2 (prd RULE-2): Only eligible, available, policy-compliant drivers may receive requests; a driver holds at most one active trip, subject to policy.
- C3 (prd RULE-3): Request creation and payment processing are idempotent; retries do not duplicate active bookings or successful charges.
- C5 (prd RULE-5): Estimates are not final fares unless fixed-price; dynamic pricing and fees are disclosed under approved policy and local requirements.
- C7 (prd RULE-7): On location/network/notification failure, preserve request/trip state, show staleness, and provide recovery.
- C8 (prd RULE-8): Core controls support screen readers, text scaling, sufficient contrast and touch targets; color alone never conveys state.
- C9 (prd RULE-9): Minimize and protect personal/location data, restrict access, approve retention, and keep direct identifiers out of general analytics.
- C10 (prd RULE-10): Configure language, currency, date/time, address formats, ride attributes, and disclosures by enabled market.
- C11 (prd RULE-11): Before public pilot, critical journeys have logs, metrics, traces, alerts, and operational dashboards.

## Done when

- Stories in this epic are integrated and deployed with the rider journey checks passing.
- Epic requirements are met without violating the listed market, safety, privacy, accessibility, and reliability constraints.
- Operations can observe the epic’s critical journey and failures in the public-launch environment.

## Boundaries

- This epic owns R7, R8, R9, R10, R11; adjacent capabilities stay with the other initiative epics.
- Must not change adjacent epic outcomes or silently weaken initiative constraints.

## References

- parent — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements and Constraints
- prd — _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md, relevant FR/RULE sections

## Notes

- Open question: Epic 2 provides a selected category and rider-confirmed price.
