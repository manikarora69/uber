---
tracker_id: ""
id: 4
type: epic
title: "In-trip visibility and safety"
parent: "initiative-uber-core-ride-hailing-experience"
covers: ["R12", "R13", "R14"]
sources: ["_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md"]
companions: []
after: [{epic: 3, needs: "Epic 3 provides a matched driver and active trip state."}]
assignee: ""
refined: true
hitl: false
risk: high
---

# In-trip visibility and safety

## Description

A rider can follow an active trip, share approved information, and reach market-supported safety help.   This epic derives its scope from the initiative requirements.

## Outcome

A rider can follow an active trip, share approved information, and reach market-supported safety help.  

## Requirements

- R12 (parent R12): During a trip, rider can view status, destination, route, and estimated arrival, with last-update time when data is stale.
- R13 (parent R13): Rider can share approved trip information with a trusted contact and access emergency assistance and support during a trip.
- R14 (parent R14): Product gives rider a prominent way to report driver/vehicle mismatch or another urgent safety concern before or during a trip.

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

- This epic owns R12, R13, R14; adjacent capabilities stay with the other initiative epics.
- Must not change adjacent epic outcomes or silently weaken initiative constraints.

## References

- parent — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements and Constraints
- prd — _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md, relevant FR/RULE sections

## Notes

- Open question: Epic 3 provides a matched driver and active trip state.
