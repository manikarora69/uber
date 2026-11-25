---
tracker_id: ""
id: 2
type: epic
title: "Ride options and fare transparency"
parent: "initiative-uber-core-ride-hailing-experience"
covers: ["R5", "R6"]
sources: ["_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md"]
companions: []
after: [{epic: 1, needs: "Epic 1 provides an authenticated rider and a serviceable route."}]
assignee: ""
refined: true
hitl: false
risk: high
---

# Ride options and fare transparency

## Description

A rider can compare available rides and confirm the displayed price conditions before requesting.   This epic derives its scope from the initiative requirements.

## Outcome

A rider can compare available rides and confirm the displayed price conditions before requesting.  

## Requirements

- R5 (parent R5): Rider can compare eligible ride categories by fare estimate/range, pickup ETA, and relevant attributes before confirming.
- R6 (parent R6): Product discloses fare components, fees, and dynamic pricing before confirmation and captures rider confirmation for high-demand pricing.

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

- This epic owns R5, R6; adjacent capabilities stay with the other initiative epics.
- Must not change adjacent epic outcomes or silently weaken initiative constraints.

## References

- parent — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements and Constraints
- prd — _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md, relevant FR/RULE sections

## Notes

- Open question: Epic 1 provides an authenticated rider and a serviceable route.
