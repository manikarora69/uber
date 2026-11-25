---
tracker_id: ""
id: 5
type: epic
title: "Trip completion and aftercare"
parent: "initiative-uber-core-ride-hailing-experience"
covers: ["R2", "R15", "R16", "R17", "R18"]
sources: ["_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md"]
companions: []
after: [{epic: 4, needs: "Epic 4 provides a completed trip and final trip state."}]
assignee: ""
refined: true
hitl: false
risk: high
---

# Trip completion and aftercare

## Description

A rider can pay for a completed trip, find the fare and receipt later, and get recourse for a trip issue.   This epic derives its scope from the initiative requirements.

## Outcome

A rider can pay for a completed trip, find the fare and receipt later, and get recourse for a trip issue.  

## Requirements

- R2 (parent R2): Rider can review completed and cancelled trips with route summary, status, fare, and receipt when applicable.
- R15 (parent R15): After completion, rider can see final fare and an itemized receipt consistent with the payment record.
- R16 (parent R16): Product reports payment success/failure and supports safe retry or eligible alternative without duplicate successful charges.
- R17 (parent R17): Rider can rate a completed trip and report safety, conduct, lost-item, fare, payment, or trip issues in context.
- R18 (parent R18): Rider can track support responses/case status and find localized self-service help with escalation.

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

- This epic owns R2, R15, R16, R17, R18; adjacent capabilities stay with the other initiative epics.
- Must not change adjacent epic outcomes or silently weaken initiative constraints.

## References

- parent — _bmad-output/initiative-uber-core-ride-hailing-experience/initiative-uber-core-ride-hailing-experience.md#Requirements and Constraints
- prd — _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md, relevant FR/RULE sections

## Notes

- Open question: Epic 4 provides a completed trip and final trip state.
