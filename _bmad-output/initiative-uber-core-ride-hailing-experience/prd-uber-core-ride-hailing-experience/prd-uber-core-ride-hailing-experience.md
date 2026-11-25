---
title: Uber Core Ride-Hailing Rider Experience
template: prd
version: 1.1.0
status: final
created: 2026-11-24
updated: 2026-11-24
---

# Uber Core Ride-Hailing Rider Experience

## Table of Contents

- [Document purpose](#document-purpose) — audience and source
- [Vision](#vision) — rider outcome
- [Users and journeys](#users-and-journeys) — needs and flow
- [Glossary](#glossary) — domain terms
- [Features and requirements](#features-and-requirements) — rider capabilities
- [Rules](#rules) — marketplace and pricing
- [Non-goals](#non-goals) — exclusions
- [MVP scope](#mvp-scope) — first release and deferrals
- [Success metrics](#success-metrics) — outcomes and guardrails
- [Quality and constraints](#quality-and-constraints) — resilience and privacy
- [Experience and platform](#experience-and-platform) — mobile rider experience
- [Stakeholders, risks and rollout](#stakeholders-risks-and-rollout) — teams and gates
- [Integrations and operations](#integrations-and-operations) — dependencies
- [Data and compliance](#data-and-compliance) — data handling
- [SLOs and performance budgets](#slos-and-performance-budgets) — launch budgets
- [Open questions](#open-questions) — decisions and owners
- [Assumptions](#assumptions) — inherited source assumptions

## Document purpose

This initiative-level PRD gives product, design, engineering, marketplace, safety, payments, operations, and support teams shared outcomes and capability boundaries for a new Uber-like rider app for public launch. It distills the supplied [source brief](/Users/manik.arora/Desktop/class/input/uber_ride_hailing_prd.md); detailed screen behavior, service design, failure handling, and story acceptance criteria belong in downstream epics and stories.

The source covers an on-demand mobility marketplace and the rider journey from account access through support. This is a proposed specification, not an official Uber internal document. It remains a draft until market, policy, metric, and operations decisions are resolved.

## Vision

A rider can request a suitable ride, understand likely cost and pickup time, identify the driver and vehicle, follow the trip, and get help when needed.

Rider confidence depends on reliable matching and accurate trip information; marketplace health depends on fulfilling requests and completing trips. MVP covers the core journey plus the trust, safety, payment, and support capabilities needed for public use.

MVP is the end-to-end core ride journey; scheduled rides, loyalty, and multimodal options are deferred.

## Users and journeys

### Users and jobs

- **Everyday commuter:** needs a predictable pickup and arrival time, clear pricing, and repeatable booking.
- **New or occasional rider:** needs guidance, transparent instructions, and confidence in driver identity.
- **Safety-conscious rider:** needs visible driver and vehicle details, trip sharing, and accessible emergency and support entry points.
- **Accessibility-conscious rider:** needs accurate ride attributes and an inclusive way to communicate requirements.
- **Price-sensitive rider:** needs comparable ride options and a clear total-cost estimate.

### UJ-1 — Source-provided rider booking-to-support flow

The source flow has a rider open the app, confirm a current or manual pickup, select a destination, compare ride categories and estimates, choose payment, and request a ride. After matching, the rider verifies driver and vehicle details, coordinates pickup, follows the trip, then receives the final fare and receipt and can rate or report an issue. Value lands when the rider completes the intended trip with understandable pricing and access to help. Recovery states include no drivers, cancellation, network loss, payment failure, uncertain location, and safety support.

This is an abstract source flow, not a validated session with a named rider. Research must capture observed journeys before downstream teams treat it as a complete UX specification.

## Glossary

- **Rider:** authenticated person requesting or taking a trip.
- **Driver-partner:** eligible, available driver who can accept a request.
- **Request:** unique attempt to book a ride from pickup to destination.
- **Trip:** journey after a matched driver starts it, through completion or recovery.
- **Ride category:** market-configured service option with eligibility, vehicle attributes, estimate, and availability.
- **Fare estimate:** pre-request price or range; not final unless explicitly fixed-price.
- **Final fare:** amount calculated after completion under the market tariff and disclosed conditions.
- **Marketplace:** services and operations connecting requests to eligible drivers and maintaining trip state.
- **MVP:** minimum viable product; the first public release defined here.
- **SLO:** service-level objective for reliability or performance.

## Features and requirements

These initiative capabilities are refined into testable acceptance criteria, screens, edge cases, and service behavior in epics. P0 is required for public release; P1 follows unless launch validation makes it necessary sooner.

### 1. Account and trip access

Riders need secure access without exposing whether another person's phone number has an account.

- **FR-1 (P0):** A rider can register, authenticate, recover account access, and maintain a valid session using the market-supported verification flow.
- **FR-2 (P0):** A rider can review completed and cancelled trips with route summary, status, fare, and receipt where applicable.

### 2. Pickup, destination, and ride choice

Riders need to enter a serviceable trip and compare choices before commitment.

- **FR-3 (P0):** A rider can set and adjust pickup and destination through location, search, and map selection, including a manual pickup path when location permission is denied.
- **FR-4 (P0):** The product validates route and serviceability before request submission and explains unsupported locations with a recovery action.
- **FR-5 (P0):** A rider can compare eligible ride categories using a fare estimate or range, pickup ETA, and relevant category attributes before confirming.
- **FR-6 (P0):** The product discloses known fare components, applicable fees, and dynamic pricing conditions before confirmation, with an explicit rider confirmation when a high-demand price applies.

### 3. Request, matching, and pickup

Riders need clear request status and a reliable way to identify and meet their driver.

- **FR-7 (P0):** A rider can submit a request once with a unique identifier; repeated submissions for the same action do not create duplicate active requests.
- **FR-8 (P0):** The product reports matching progress, match outcome, driver cancellation, no-driver outcome, and recovery options without leaving the rider in a stale state.
- **FR-9 (P0):** After match, the rider can view the available driver and vehicle identifiers, current pickup ETA, and approach state.
- **FR-10 (P0):** A rider can coordinate pickup and reach the driver through supported in-app communication, with personal contact details masked where supported.
- **FR-11 (P0):** A rider can cancel a request and understand any applicable fee before confirming cancellation where feasible.

### 4. In-trip experience and safety

Riders need current trip context, sharing, and help.

- **FR-12 (P0):** During a trip, the rider can view status, destination, route, and estimated arrival, with the last update time shown when data is stale.
- **FR-13 (P0):** A rider can share approved trip information with a trusted contact and can access emergency assistance and support from the active-trip experience.
- **FR-14 (P0):** The product gives the rider a prominent way to report a driver or vehicle mismatch or another urgent safety concern before or during a trip.

### 5. Payment, completion, and recourse

Riders need a clear trip close and a way to resolve charges or service problems.

- **FR-15 (P0):** After completion, the rider can see the final fare and an itemized receipt consistent with the payment record.
- **FR-16 (P0):** The product reports payment success or failure and supports a safe retry or eligible alternative without duplicate successful charges.
- **FR-17 (P0):** A rider can rate a completed trip and report safety, conduct, lost-item, fare, payment, or trip issues in the context of the relevant trip.
- **FR-18 (P1):** A rider can track support responses and case status, and find localized self-service help with escalation when self-service is insufficient.

## Rules

- **RULE-1:** A ride request requires an authenticated rider, valid pickup and destination, eligible ride category, and market-approved payment arrangement.
- **RULE-2:** Only drivers meeting eligibility, availability, vehicle, and market-policy requirements may receive a request; one driver may hold only one active trip at a time, subject to marketplace policy.
- **RULE-3:** Request creation and payment processing are idempotent: repeated requests or retries must not produce duplicate active bookings or duplicate successful charges.
- **RULE-4:** A trip enters the in-trip state only after the driver starts it and any configured pickup verification is complete.
- **RULE-5:** Estimates are not final fares unless explicitly defined as fixed-price. Dynamic pricing and any cancellation, waiting, toll, or other charge must be disclosed under approved product policy and applicable local requirements.
- **RULE-6:** Emergency assistance must not imply guaranteed dispatch unless a supported local integration provides that service.

## Non-goals

The first release excludes a driver app rebuild; adjacent food, freight, transit, bike/scooter, or car rental products; fleet ownership or employment models; replacing emergency services; corporate travel; and market-specific products not selected for launch.

## MVP scope

### In scope

- Account registration, login, recovery, and trip history.
- Current or manual pickup entry; destination search and map selection; serviceability validation.
- Eligible ride category comparison, fare estimate, pickup ETA, and request confirmation.
- Request submission, driver matching, driver and vehicle details, pickup coordination, cancellation, and recovery.
- In-trip status and route visibility, trip sharing, emergency assistance entry point, and support access.
- Final fare, market-approved cash and at least one supported digital payment method, receipt, rating, and basic issue reporting.
- Core rider-facing safety and privacy controls required to verify driver/vehicle identity and get help.

### Deferred

- **Phase 2:** scheduled rides, multiple stops and destination changes, saved places and family profiles, promotions and loyalty, accessibility-specific ride preferences, richer support case management, and more localized payments.
- **Phase 3:** multimodal mobility, business profiles, personalized ride recommendations, advanced subscriptions, and proactive disruption assistance.

The source proposes the complete core ride journey for MVP. Public rollout is limited to zones, categories, and payment methods with validated driver supply and support readiness; specifics remain open below.

## Success metrics

Set baselines and numeric targets by market, city, category, OS, rider tenure, payment method, and time of day before a pilot. The source provides directions only, not approved numeric targets.

| ID | Outcome measure | Direction / target | Counter-metric or guardrail |
|---|---|---|---|
| **SM-1** | Search-to-request conversion: requests divided by riders viewing options | Improve against baseline | Rider cancellation and support-contact rates must not worsen as conversion rises |
| **SM-2** | Request fulfillment: valid requests completed | Improve | Monitor unfulfilled demand and driver cancellation by zone and category |
| **SM-3** | Time to match and pickup ETA accuracy | Reduce time and error | Do not shift burden through increased rider or driver cancellations |
| **SM-4** | Trip completion rate: completed trips divided by accepted trips | Improve | Monitor safety reports and unresolved trip-state errors |
| **SM-5** | Payment success rate for completed trips | Increase | Duplicate successful charges must remain at zero; track unresolved payment issues |
| **SM-6** | 30-day rider retention | Improve | Track cohort differences and support burden |
| **SM-7** | Safety incident rate and response time, severity-weighted | Reduce incidents and response delay | Do not treat lower reporting volume alone as evidence of improved safety |
| **SM-8** | Crash-free sessions and critical-journey availability | Maintain high reliability | Monitor failed requests, stale trip state, and payment recovery |

## Quality and constraints

- **RULE-7 — Recovery:** when location, network, or notifications fail, preserve request/trip state, show when data is stale, and provide a relevant recovery path.
- **RULE-8 — Accessibility:** core booking, pickup, trip, payment, and support actions work with screen readers, text scaling, sufficient contrast, and touch targets; color alone never conveys state.
- **RULE-9 — Privacy and security:** minimize personal and precise location data, encrypt it in transit and at rest, restrict access, and approve retention before use; general analytics exclude raw phone numbers and exact home addresses.
- **RULE-10 — Localization:** configure language, currency, date/time, address formats, ride attributes, and required disclosures for each enabled market.
- **RULE-11 — Operational visibility:** before public pilot, instrument critical booking, matching, trip, payment, and support journeys with logs, metrics, traces, alerts, and dashboards.

## Experience and platform

The source proposes a mobile-first rider experience on Android and iOS, with limited mobile web support. This remains a source assumption until product scope and device support are confirmed. Core surfaces include account access; home map and pickup/destination search; ride options; request and match state; driver approach and pickup; active trip; completion and receipt; rating and support; and safety assistance.

The rider should see a clear next action, understandable pricing and cancellation language, explicit loading/empty/error/offline/success states, and preserved booking state when the app backgrounds or disconnects. Permission prompts explain their purpose and preserve a manual path where possible. Dynamic text, assistive technology, contrast, and accessible controls are required.

## Stakeholders, risks and rollout

### Cross-functional partners

| Partner | Contribution needed |
|---|---|
| Product, design, and research | Scope, journey research, usability, accessibility, and localization |
| Rider app engineering | Booking and trip experience, app state, offline behavior |
| Backend/platform and marketplace | Accounts, requests, matching, trip state, fare, and APIs |
| Maps/location | Search, geocoding, routing, maps, location quality, and ETA |
| Driver operations | Driver eligibility, supply readiness, vehicle data, and market policies |
| Payments/finance | Methods, reconciliation, refunds, receipts, and fraud controls |
| Trust & Safety and customer support | Incident policies, escalation, support taxonomy, staffing, and response |
| Legal/compliance and privacy | Market-specific transport, consumer, payment, consent, and retention review |
| Data/analytics | Metric definitions, instrumentation, dashboards, and experimentation |
| Marketing/CRM | Rider education and lifecycle communications |

### Principal risks

- **Insufficient driver supply:** limit pilots to supply-ready zones and monitor fulfillment by zone/category.
- **Ambiguous pickup or unstable ETA:** support pin adjustment, landmarks, location confidence, and ETA calibration.
- **Fare confusion:** show estimate components, pricing conditions, and an itemized final receipt.
- **Payment failure or duplicate charge:** support safe retry and reconciliation with trip history.
- **Safety incident or weak escalation:** validate in-market safety flows, queue ownership, incident response, and auditability before launch.
- **Privacy exposure:** minimize location and personal data, enforce access control, and define retention before production use.
- **Support overload:** validate capacity, issue triage, and human escalation before opening each rollout gate.

### Rollout gates

1. **Internal alpha:** core journey and operational monitoring work in a controlled environment.
2. **Closed beta:** invited riders in selected operating zones; validate usability, pricing comprehension, pickup, and recovery.
3. **City pilot:** limited traffic after supply, payments, safety, support, analytics, legal/privacy, accessibility, and rollback readiness are approved.
4. **Progressive rollout:** expand by cohort and geography while success and guardrail metrics remain within approved thresholds.
5. **General availability:** broaden only after pilot outcomes and operating readiness are reviewed.

Specific owners, dates, cohort sizes, and numerical gate thresholds remain open; the source does not provide them.

## Integrations and operations

The rider experience depends on accounts, maps/location, fare calculation, matching, driver/vehicle records, trip state, masked communications, notifications, payment/reconciliation, support, safety escalation, analytics, and market operations. The source names no vendors or internal services.

Before pilot, Operations must define supply readiness, cancellation and fee policies, incident escalation, support coverage, payment reconciliation/refunds, and rollback controls. In-app state remains authoritative when notifications are delayed or missing.

## Data and compliance

Data includes account details, precise location, driver/vehicle identifiers, trip state, payments, communications, ratings, and support/safety reports. Minimize collection, restrict access, exclude direct identifiers from general analytics, and define retention, consent, deletion, and audit controls per market before launch.

The source names no legal regime or retention period. Legal, privacy, payments, and local operations must identify applicable obligations and approve disclosures, data handling, emergency guidance, and records per market; this PRD makes no specific regulatory claim.

## SLOs and performance budgets

Before pilot, Engineering and Product must set median (p50) and 95th-percentile (p95) budgets for critical reads and interactions, availability objectives for booking/matching/trip/payment, supported devices, minimum network assumptions, and recovery expectations. The source sets no values. Budgets should reflect pilot evidence and include graceful degradation.

## Open questions

| ID | Decision needed | Owner | Needed by / blocked work |
|---|---|---|---|
| **OQ-1** | Confirm launch city/cities, operating zones, and market sequence. | Product + Operations | Before pilot scope and market configuration; blocks serviceability, categories, and rollout. |
| **OQ-2** | Select MVP ride categories and their eligibility/attributes. | Product + Marketplace + Operations | Before option design and matching refinement; blocks FR-5, FR-8, and FR-9. |
| **OQ-3** | Confirm supported payment methods and the market-approved cash arrangement. | Product + Payments/Finance | Before payment and booking contracts; blocks FR-7 and FR-15–16. |
| **OQ-4** | Approve dynamic pricing, cancellation, waiting, toll, and other fee policies and disclosures. | Product + Payments + Legal | Before fare UX and cancellation implementation; blocks FR-6 and FR-11. |
| **OQ-5** | Decide whether pickup PIN verification is required, optional, or market-dependent. | Product + Trust & Safety + Operations | Before pickup design; blocks FR-10 and RULE-4. |
| **OQ-6** | Inventory available safety, emergency assistance, trip-sharing, and support capabilities by market. | Trust & Safety + Support + Operations | Before safety epic and pilot readiness; blocks FR-13–14. |
| **OQ-7** | Set supported OS/device versions, minimum network conditions, launch languages, and accessibility bar. | Product + Design + Engineering | Before experience design and release scope; blocks RULE-8, RULE-10, and platform commitments. |
| **OQ-8** | Establish metric baselines, numeric targets, guardrail thresholds, and pilot stopping rules. | Product + Data/Analytics + Operations | Before pilot approval; blocks SM-1–8 rollout gates. |
| **OQ-9** | Define market-specific consent, location retention, deletion, and data access requirements. | Legal/Compliance + Privacy | Before production data collection; blocks RULE-9 and launch approval. |
| **OQ-10** | Set support response-time commitments, escalation coverage, and capacity for each pilot zone. | Support + Operations + Trust & Safety | Before closed beta/city pilot; blocks FR-13–14 and rollout approval. |
| **OQ-11** | Set measurable latency, availability, and recovery budgets for critical journeys. | Engineering + Product | Before technical design and pilot; blocks performance and availability gate definitions. |
| **OQ-12** | Capture and validate named rider sessions for commuter, new/occasional, safety-conscious, price-sensitive, and accessibility-conscious needs. | Product Research + Design | Before downstream UX sign-off; validates UJ-1 and FR-3–18. |

## Assumptions

- India is the primary market assumption, inherited from the source brief; no launch city or operating zone is confirmed.
- Android and iOS are core platforms and mobile web has limited support, inherited from the source; device/version commitments remain open.
- The product specification is proposed and is not an official Uber internal document.
- The source's core end-to-end rider flow is representative enough to organize initiative capabilities, but it is not a validated named-person journey.
- No numeric success targets, SLOs, legal obligations, market policies, support commitments, vendor integrations, or launch dates are approved in the source.
