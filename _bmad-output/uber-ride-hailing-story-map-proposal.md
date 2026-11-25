# Proposed Epics, User Stories, and Acceptance Criteria

**Status:** Approved epic split and story acceptance criteria; official ticket files created  
**Initiative:** Uber Core Ride-Hailing Experience  
**Source:** `_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md`

The workspace has no rider-app code to inspect. This split follows the PRD's product capabilities and the rider journey. The first epic starts with the platform baseline; each epic ends with an integrated, demonstrable product outcome. Open questions listed under stories are launch dependencies, not invented acceptance decisions.

## Epic 1 — Rider account and trip setup

**Initiative requirements:** R1, R3, R4  
**Outcome:** A rider can open the deployed app, access an account, enter a trip, and see whether the route is serviceable.  
**Dependency:** Opening epic; first story includes app scaffold, build/deploy path, and a visible account-entry screen.

### Story 1.1 — Open the rider app and access an account (P0, proposed risk: high)

As a rider, I want to register or sign in securely so that I can start booking.

**Acceptance criteria**

1. Given a clean baseline build, when it is deployed and opened, then the rider sees sign-in and registration entry points.
2. Given a supported phone number and valid verification code, when verification succeeds, then the rider receives an authenticated session.
3. Given an invalid or expired code, when submitted, then no session is created and the rider sees a recoverable error.
4. Given an account-recovery attempt, when the phone number is or is not registered, then the response does not reveal registration status.

**Open questions:** OQ-7 supported OS/device and accessibility scope.

### Story 1.2 — Set and adjust pickup and destination (P0, proposed risk: high)

As a rider, I want to set my pickup and destination using location, search, or the map so that I can define where I need to go.

**Acceptance criteria**

1. Given foreground location permission and adequate location accuracy, when the rider opens trip setup, then current location is suggested as pickup and can be reviewed or moved.
2. Given location permission is denied or unavailable, when the rider sets a pickup, then manual search and map selection remain available.
3. Given the rider selects a search result or moves a pin, when the selection is confirmed, then the displayed address and selected coordinates update together.

**Open questions:** OQ-1 launch zones; OQ-7 supported devices/network and languages; OQ-12 observed rider journeys.

### Story 1.3 — Check route serviceability (P0, proposed risk: medium)

As a rider, I want the app to validate pickup and destination before I request so that I know whether the trip can be served.

**Acceptance criteria**

1. Given a serviceable pickup and destination, when validation completes, then trip setup can continue to ride options.
2. Given an unsupported pickup, destination, or route, when validation completes, then the rider sees a clear explanation and can edit the location.
3. Given the app suggests a nearby pickup, when the rider has not confirmed it, then the suggested location is not silently substituted.

**Open questions:** OQ-1 launch zones and OQ-12 rider research.

## Epic 2 — Ride options and fare transparency

**Initiative requirements:** R5, R6  
**Outcome:** A rider can compare available rides and confirm the displayed price conditions before requesting.  
**Dependency:** Epic 1 provides an authenticated rider and a serviceable route.

### Story 2.1 — Compare available ride options (P0, proposed risk: medium)

As a rider, I want to compare eligible ride categories, pickup ETAs, and attributes so that I can choose an option that fits my trip.

**Acceptance criteria**

1. Given a serviceable route, when ride options load, then only currently eligible and available categories are selectable.
2. Given an eligible category, when it is displayed, then its fare estimate or range, pickup ETA, and relevant attributes appear in local formatting.
3. Given the rider selects a category, when the choice is made, then the request summary reflects that selection.

**Open questions:** OQ-1 launch zones, OQ-2 MVP categories, OQ-7 localization/device scope, OQ-8 metric baselines.

### Story 2.2 — Understand and confirm fare conditions (P0, proposed risk: high)

As a rider, I want to see known fare components and any high-demand price before requesting so that I can make an informed choice.

**Acceptance criteria**

1. Given an estimate is shown, when the rider reviews it, then known fare components and applicable fees are available before confirmation.
2. Given dynamic/high-demand pricing applies, when the rider reviews the request, then the applicable price or multiplier is disclosed before the request is submitted.
3. Given dynamic/high-demand pricing applies, when the rider has not confirmed the displayed offer, then the request is not submitted.
4. Given the final fare may differ, when the estimate is presented, then the conditions under which it may change are disclosed.

**Open questions:** OQ-2 categories, OQ-4 fare/fee policy, OQ-8 targets and guardrails.

## Epic 3 — Ride request, matching, and pickup

**Initiative requirements:** R7–R11  
**Outcome:** A rider can create one request, understand matching and cancellation outcomes, and identify and meet the matched driver.  
**Dependency:** Epic 2 provides a selected category and rider-confirmed price.

### Story 3.1 — Submit one ride request (P0, proposed risk: high)

As a rider, I want my confirmed ride request to be created once so that retries do not book duplicate rides.

**Acceptance criteria**

1. Given a valid authenticated rider, serviceable route, selected category, and eligible payment arrangement, when the rider confirms, then one uniquely identified request is created.
2. Given the same request submission is repeated, when the same idempotency key is received, then the existing request is returned and no second active request is created.
3. Given required request data is missing or invalid, when submission is attempted, then the request is not created and the rider is told what to correct.

**Open questions:** OQ-1 zones, OQ-2 categories, OQ-3 payment arrangements.

### Story 3.2 — Follow matching and recover from cancellation (P0, proposed risk: high)

As a rider, I want clear matching, no-driver, and cancellation states so that I know what happened and what I can do next.

**Acceptance criteria**

1. Given a request is pending, when matching is in progress, then the app shows that status and keeps it current.
2. Given no eligible driver accepts within the configured window, when matching ends, then the rider sees the outcome and can retry or change category/pickup where supported.
3. Given a driver cancels after matching, when the cancellation is received, then rematching starts where supported or the rider receives a clear recovery option; the app does not remain in a stale matched state.
4. Given the rider chooses to cancel, when a fee applies, then the fee is shown before confirmation; after confirmation, the request status and fee outcome are clear.

**Open questions:** OQ-1 zones, OQ-2 categories, OQ-4 cancellation fees, OQ-5 pickup verification, OQ-10 support coverage.

### Story 3.3 — Identify and coordinate with the matched driver (P0, proposed risk: high)

As a rider, I want to see the matched driver's details and approach and contact them safely so that I can meet the correct vehicle.

**Acceptance criteria**

1. Given a driver accepts, when the match is shown, then the driver's name and photo where available, plus vehicle make, model, color, and registration identifier as permitted by market policy, are displayed.
2. Given driver location updates arrive, when the vehicle approaches, then the map and pickup ETA update without the rider reopening the screen.
3. Given the rider contacts the driver, when an in-app channel is supported, then contact uses that channel and masks personal contact details where supported.
4. Given pickup PIN verification is enabled, when the trip is started, then required verification is complete first.

**Open questions:** OQ-5 pickup PIN policy; OQ-6 market safety/communications capabilities; OQ-7 localization and supported devices.

## Epic 4 — In-trip visibility and safety

**Initiative requirements:** R12–R14  
**Outcome:** A rider can follow an active trip, share approved information, and reach market-supported safety help.  
**Dependency:** Epic 3 provides a matched driver and active trip state.

### Story 4.1 — Track trip progress (P0, proposed risk: high)

As a rider, I want current trip status, route, destination, and ETA so that I can follow my journey.

**Acceptance criteria**

1. Given a trip is active, when trip data is current, then the rider sees status, destination, route, and estimated arrival.
2. Given location/network updates stop, when the trip screen remains open, then last-known information remains visible with its last update time.
3. Given connectivity returns, when current trip state is retrieved, then the rider sees the authoritative state rather than a stale local state.

**Open questions:** OQ-7 device/network scope, OQ-11 performance and recovery budgets.

### Story 4.2 — Share an active trip (P0, proposed risk: high)

As a rider, I want to share approved trip details with someone I trust so that they can follow my journey.

**Acceptance criteria**

1. Given an active trip, when the rider selects sharing, then an available sharing method can be chosen from the trip screen.
2. Given a share is created, when the trusted contact opens it, then only approved trip information is exposed.
3. Given the share reaches its configured expiration, when the contact opens the old share, then trip details are no longer available.

**Open questions:** OQ-6 sharing capabilities; OQ-9 privacy/retention policy.

### Story 4.3 — Reach safety help and report a mismatch (P0, proposed risk: high)

As a rider, I want to reach emergency/support options and report a driver or vehicle mismatch so that I can act when I feel unsafe.

**Acceptance criteria**

1. Given an active trip, when the rider opens safety help, then market-supported emergency and support actions are visible and accessible.
2. Given the rider reports a driver/vehicle mismatch, when the report is submitted, then the trip context is attached and the rider receives a clear confirmation or next step.
3. Given emergency dispatch is not integrated for the market, when assistance guidance is shown, then it does not promise dispatch that the product cannot provide.

**Open questions:** OQ-6 emergency/support capabilities and OQ-10 response/escalation coverage.

## Epic 5 — Trip completion and aftercare

**Initiative requirements:** R2, R15–R18  
**Outcome:** A rider can pay for a completed trip, find the fare and receipt later, and get recourse for a trip issue.  
**Dependency:** Epic 4 provides a completed trip and final trip state.

### Story 5.1 — Pay and review a completed trip (P0, proposed risk: high)

As a rider, I want a clear final fare, payment result, and receipt so that I can verify and retain the trip record.

**Acceptance criteria**

1. Given a trip completes, when the final fare is available, then the rider sees an itemized fare consistent with the payment record, plus trip date, route summary, payment method, and support path on the receipt.
2. Given payment succeeds or fails, when processing completes, then the payment state is explicit and an eligible retry or alternative is available after failure.
3. Given payment is retried, when the same transaction is processed again, then no duplicate successful charge is created.
4. Given a completed or cancelled trip appears in history, when the rider opens it, then route summary, date, status, fare, and receipt access are available where applicable.

**Open questions:** OQ-3 payment methods, OQ-4 fare policy, OQ-11 performance/recovery budgets.

### Story 5.2 — Rate a trip and resolve an issue (P1 for case tracking; proposed risk: high)

As a rider, I want to rate a completed trip, report an issue, and track support so that I can give feedback and get a response.

**Acceptance criteria**

1. Given a completed trip, when the rider submits a rating, then one rating is associated with that trip; optional structured/free-text feedback can be added.
2. Given the rider reports a safety, conduct, lost-item, fare, payment, or trip issue, when the report is submitted, then it is linked to the correct trip and the rider receives confirmation.
3. Given support case tracking is enabled, when the case changes, then the rider can view the response and current status; localized self-service help offers escalation where needed.

**Open questions:** OQ-6 safety queues, OQ-9 data retention, OQ-10 response commitments.

## Shared decisions and open dependencies

- **Architecture spine recommended:** define shared rider/request/trip identifiers and the contracts between trip setup, fare, matching, trip state, payment, communications, and support before the stories start. The workspace has no implementation code to resolve these contracts from. If this is declined, add a human-owned architecture decision story to Epic 1 and make dependent epics wait for it.
- **Market setup:** OQ-1 through OQ-11 remain initiative-level questions. Stories should not be started when their listed OQ blocks them; resolve the question or record a spike before work starts.
- **User evidence:** OQ-12 remains before UX sign-off. The PRD's rider flow is abstract, not an observed named-person session.
- **Quality:** every implementation story includes its own regression checks; a separate end-to-end ride-to-receipt suite can be added to the final epic after the build breakdown is approved.
