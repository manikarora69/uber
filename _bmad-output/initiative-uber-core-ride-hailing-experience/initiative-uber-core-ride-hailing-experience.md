---
type: initiative
title: Uber Core Ride-Hailing Experience
parent: none
sources:
  - _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md
companions:
  - _bmad-output/uber-ride-hailing-story-map-proposal.md
risk: high
---

# Uber Core Ride-Hailing Experience

## Description

Deliver a new public rider app that lets people request and complete an on-demand ride with clear pricing, reliable pickup/trip information, and accessible support. This initiative derives its capabilities and constraints from the product PRD; it is a proposed Uber-like product specification, not an official Uber internal plan.

## Outcome

Riders can complete a suitable trip with understandable pricing and a clear route to help; success is improved request fulfillment and trip completion without weakening safety reporting and response guardrails (SM-2, SM-4, SM-7).

## Requirements

- R1 (prd FR-1): Rider can register, authenticate, recover access, and maintain a valid session using market-supported verification.
- R2 (prd FR-2): Rider can review completed and cancelled trips with route summary, status, fare, and receipt when applicable.
- R3 (prd FR-3): Rider can set and adjust pickup and destination using location, search, or map selection, with manual pickup when location permission is denied.
- R4 (prd FR-4): Product validates serviceability and route feasibility before request submission, explains unsupported locations, and offers recovery.
- R5 (prd FR-5): Rider can compare eligible ride categories by fare estimate/range, pickup ETA, and relevant attributes before confirming.
- R6 (prd FR-6): Product discloses fare components, fees, and dynamic pricing before confirmation and captures rider confirmation for high-demand pricing.
- R7 (prd FR-7): Rider can submit a uniquely identified request once; repeated submissions do not create duplicate active requests.
- R8 (prd FR-8): Product reports matching progress, match/no-driver outcome, driver cancellation, and recovery without stale request state.
- R9 (prd FR-9): After match, rider can view available driver/vehicle identifiers, current pickup ETA, and approach state.
- R10 (prd FR-10): Rider can coordinate pickup and reach the driver through supported in-app communication, masking personal contact details where supported.
- R11 (prd FR-11): Rider can cancel and understand any applicable fee before confirming cancellation where feasible.
- R12 (prd FR-12): During a trip, rider can view status, destination, route, and estimated arrival, with last-update time when data is stale.
- R13 (prd FR-13): Rider can share approved trip information with a trusted contact and access emergency assistance and support during a trip.
- R14 (prd FR-14): Product gives rider a prominent way to report driver/vehicle mismatch or another urgent safety concern before or during a trip.
- R15 (prd FR-15): After completion, rider can see final fare and an itemized receipt consistent with the payment record.
- R16 (prd FR-16): Product reports payment success/failure and supports safe retry or eligible alternative without duplicate successful charges.
- R17 (prd FR-17): Rider can rate a completed trip and report safety, conduct, lost-item, fare, payment, or trip issues in context.
- R18 (prd FR-18): Rider can track support responses/case status and find localized self-service help with escalation.

## Constraints

- C1 (prd RULE-1): A request requires an authenticated rider, valid pickup/destination, eligible category, and market-approved payment arrangement.
- C2 (prd RULE-2): Only eligible, available, policy-compliant drivers may receive requests; a driver holds at most one active trip, subject to policy.
- C3 (prd RULE-3): Request creation and payment processing are idempotent; retries do not duplicate active bookings or successful charges.
- C4 (prd RULE-4): A trip starts only after driver start and any configured pickup verification.
- C5 (prd RULE-5): Estimates are not final fares unless fixed-price; dynamic pricing and fees are disclosed under approved policy and local requirements.
- C6 (prd RULE-6): Emergency assistance must not imply guaranteed dispatch unless a supported local integration provides it.
- C7 (prd RULE-7): On location/network/notification failure, preserve request/trip state, show staleness, and provide recovery.
- C8 (prd RULE-8): Core controls support screen readers, text scaling, sufficient contrast and touch targets; color alone never conveys state.
- C9 (prd RULE-9): Minimize and protect personal/location data, restrict access, approve retention, and keep direct identifiers out of general analytics.
- C10 (prd RULE-10): Configure language, currency, date/time, address formats, ride attributes, and disclosures by enabled market.
- C11 (prd RULE-11): Before public pilot, critical journeys have logs, metrics, traces, alerts, and operational dashboards.

## Done when

- The end-to-end rider journey from account access through trip completion and recourse is demonstrable in each enabled pilot zone (R1–R18).
- Fare estimates, pricing disclosures, final fares, receipts, and payment records reconcile; request/payment retries produce no duplicate active booking or successful charge (R6–R7, R15–R16, C3–C5).
- Fulfillment, time-to-match, ETA accuracy, trip completion, and payment success are baselined and have approved pilot targets and guardrails (SM-1–SM-5).
- Safety flows and severity-aware incident/response monitoring are operational before public pilot (R13–R14, SM-7, C6, C11).
- Market-specific privacy, accessibility, localization, support, rollback, and critical-service budgets are approved before pilot expansion (C7–C11, OQ-7–OQ-11).

## Boundaries

The first release excludes a driver app rebuild; adjacent food, freight, transit, bike/scooter, or car rental products; fleet ownership or employment models; replacing emergency services; corporate travel; and market-specific products not selected for launch. Scheduled rides, multiple stops, family profiles, promotions, memberships, loyalty, business profiles, multimodal mobility, and personalized recommendations are deferred.

- Touch point: Maps, search, geocoding, routing, and location quality — consumed/configured by the rider trip-setup epic; owner: epic-rider-trip-setup.
- Touch point: Market fare rules and eligible ride-category configuration — used to price and display options; owner: epic-ride-options-and-fare-transparency.
- Touch point: Driver eligibility, availability, and marketplace dispatch — consumed by request and match; owner: epic-ride-request-matching-pickup.
- Touch point: In-trip location feed, trip-sharing, and safety escalation — consumed/configured for active trips; owner: epic-in-trip-visibility-safety.
- Touch point: Payment processing/reconciliation, trip history, and support case management — consumed after completion; owner: epic-trip-completion-and-aftercare.
- Tracer path: authenticate and set a serviceable trip → compare price/options → request and meet a matched driver → track/share the trip → pay, receive a receipt, and get help.

## References

- prd — _bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md, Vision through Open questions.
- story-map — _bmad-output/uber-ride-hailing-story-map-proposal.md, approved epic split and source proposal for story tickets.

## Notes

- Assumption: India is the primary market, inherited from the PRD; launch cities and operating zones are unconfirmed.
- Assumption: Android and iOS are core platforms and mobile web is limited support; supported versions/devices are unconfirmed.
- Assumption: Proposed risk is high because public safety, payment, privacy, and marketplace failures materially affect riders and launch readiness.
- Open question: OQ-1 — Product + Operations: confirm launch cities, zones, and market sequence before pilot scope; blocks serviceability, categories, and rollout.
- Open question: OQ-2 — Product + Marketplace + Operations: select MVP categories and eligibility before option/matching refinement; blocks R5, R8, and R9.
- Open question: OQ-3 — Product + Payments: confirm supported payment methods/cash arrangement before booking and payment contracts; blocks R7, R15, and R16.
- Open question: OQ-4 — Product + Payments + Legal: approve dynamic pricing and fee policies/disclosures before fare and cancellation build; blocks R6 and R11.
- Open question: OQ-5 — Product + Trust & Safety + Operations: decide pickup PIN policy before pickup design; blocks R10 and C4.
- Open question: OQ-6 — Trust & Safety + Support + Operations: inventory emergency, trip-sharing, and support capabilities before safety epic/pilot; blocks R13 and R14.
- Open question: OQ-7 — Product + Design + Engineering: set OS/device/network/language/accessibility scope before experience/release scope; blocks C8 and C10.
- Open question: OQ-8 — Product + Data + Operations: set baselines, targets, guardrails, and pilot stop rules before pilot; blocks SM-1 through SM-8.
- Open question: OQ-9 — Legal/Compliance + Privacy: define consent, retention, deletion, and data access per market before production data collection; blocks C9 and launch.
- Open question: OQ-10 — Support + Operations + Trust & Safety: set response commitments, escalation, and capacity before beta/pilot; blocks R13 and R14.
- Open question: OQ-11 — Engineering + Product: set latency, availability, and recovery budgets before technical design/pilot; blocks performance and availability gates.
- Open question: OQ-12 — Product Research + Design: capture named rider sessions before UX sign-off; validates UJ-1 and R3 through R18.

- Decision: 2026-11-24 — Approved the five-epic initiative split and the 13 stories with their acceptance criteria; official epic and story ticket files were generated.
