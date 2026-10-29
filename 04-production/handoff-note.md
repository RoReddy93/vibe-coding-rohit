# Engineering Handoff Note

> Module 4 · Production Specs. Open the black box, make the build legible to an engineer.

## What this is

_One paragraph an engineer can read in 60 seconds._

The Retention Engine is a five-screen, clickable prototype testing whether guided collaboration in week one improves activation and eventually reduces 90-day churn. The owner identifies an onboarding bottleneck, assigns a fix, and switches to a simulated teammate who implements and verifies it. Activation requires both role actions; invitations alone do not count. Supporting screens cover team invitations, experiment evidence, and PM monitoring. It runs as static HTML/CSS/JavaScript, with browser-local persistence and no backend. Customer quotes and baseline metrics came from the brief; usage data, invitations, cohort results, and collaboration are simulated. Treat this as an interaction specification, not a production implementation or validated experiment.

## Architecture (plain language)

- **Frontend:** Frontend	Five named screen functions render HTML. Files are grouped under dist/features/ by Opportunity, Week-one Path, Experiment Readout, Team Workspace, and PM Dashboard.
- **Backend / data:** Backend	None. No authentication, shared database, email service, analytics pipeline, or product integration.
- **Key flows:** Activation: identify bottleneck → assign fix → switch roles → review evidence → implement → verify → complete → return to owner.
Team: create sample invitation → pending → simulate acceptance. Acceptance does not trigger activation.
PM monitoring: inspect illustrative invitation/completion metrics and owners without invitations; retention remains pending.
Recovery: loading skeletons, preserved invite inputs with Retry, and connection-lost messaging with Reconnect.

## What's solid vs. what's duct tape

| Area | State | Notes |
|---|---|---|
| Screen names and feature folders map to the PRD. | solid | _____ |
| Role switching does not verify two distinct users or enforce the seven-day window. | rough | _____ |

## Risks & assumptions for the team

Unvalidated mechanism: completing a collaborative task may not predict customer value or retention.
Baseline comparability: the supplied 22% activation definition may differ from the proposed two-person definition.
Simulated implementation: adding and verifying the starter report does not modify a real customer product.
Data isolation: localStorage is browser-specific; changes are neither shared nor authoritative.
Measurement gaps: production needs distinct user/account IDs, timestamps, deduplication, cohort assignment, and server-side activation rules.
Retention uncertainty: baseline churn, sample size, meaningful effect, and treatment of annual contracts remain unresolved.
Security: real deployment needs authentication, account permissions, input validation, and appropriate handling of invitation details.

## How to run it

```
from the repository root:
python -m http.server 8000 --directory dist

Open http://localhost:8000. No dependency installation or build step is required.

Run regression checks:
node tests/refactor.test.cjs

Direct routes: #context, #path, #experiment, #team, and #pm.

Expand Prototype testing controls to replay skeletons, preview no teammates, fail an invitation, or simulate disconnection. For a clean session, clear localStorage keys retention-engine-two-v1 and retention-team-v1.
```
