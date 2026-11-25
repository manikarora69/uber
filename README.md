# Uber Ride Hailing

Product planning workspace for an end-to-end rider ride-hailing experience. The repository captures the initiative brief, product requirements, an approved epic and story breakdown, and the BMAD agent tooling used to create and maintain those artifacts.

> **Project state:** This repository currently contains planning and workflow materials. It does not contain a runnable rider application, backend service, or deployment configuration.

## What’s here

| Path | Purpose |
| --- | --- |
| `input/` | Source initiative brief that defines the product problem and desired rider experience. |
| `_bmad-output/initiative-uber-core-ride-hailing-experience/` | Initiative, PRD, review materials, epics, and implementation-ready story files. |
| `_bmad-output/uber-ride-hailing-story-map-proposal.md` | Story map proposal describing the rider journey and epic split. |
| `output.txt` | Earlier generated proposal text; retained as project history/reference. |
| `_bmad/` | Project-local BMAD configuration, scripts, and rendered agent resources. |
| `.agents/skills/` | Agent skill definitions and supporting references used by this workspace. |
| `skills-lock.json` | Locked skill package metadata for the installed agent skills. |

## Product scope

The initiative describes a complete rider journey:

1. Open the app and access an account.
2. Set pickup and destination, then check route serviceability.
3. Compare ride options and understand fare conditions.
4. Submit one ride request, follow matching, and coordinate pickup.
5. Track the trip, share it, and reach safety help.
6. Pay, review the completed trip, rate it, or resolve an issue.

The detailed acceptance criteria and open launch questions are recorded in the story files under `_bmad-output/initiative-uber-core-ride-hailing-experience/tickets/`. The PRD is the main source for product requirements; the input brief is the source for the initiative framing.

## Getting started

There is no application to install or run yet. To explore the current work, start with:

1. [`input/initiative-uber-core-ride-hailing-experience.md`](input/initiative-uber-core-ride-hailing-experience.md)
2. The PRD at `_bmad-output/initiative-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience/prd-uber-core-ride-hailing-experience.md`
3. The epic and story documents under `_bmad-output/initiative-uber-core-ride-hailing-experience/tickets/`
4. [`_bmad-output/uber-ride-hailing-story-map-proposal.md`](_bmad-output/uber-ride-hailing-story-map-proposal.md)

## Development status

The current deliverable is a product specification and backlog, not executable software. The story breakdown identifies the work needed to establish an app scaffold, authentication, trip setup, ride selection, matching, in-trip visibility and safety, payment, and aftercare. Technical stack, supported launch regions, and other unresolved decisions should be settled before application implementation begins.

No build, test, or deployment commands are defined in this repository yet.

## Contributing

When updating the product scope, keep the initiative brief, PRD, epics, and story acceptance criteria aligned. Record unresolved assumptions as open questions in the relevant product artifacts rather than presenting them as settled behavior. For code contributions, add the application and its build/test instructions once implementation starts.

## License

No license has been declared for this repository. All rights remain with their respective owners until a license is added.
