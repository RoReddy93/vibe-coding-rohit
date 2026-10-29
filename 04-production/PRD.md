# Living PRD

> Module 4 · Production Specs. Refactor for readability; extract a living PRD that stays true as the build evolves.

## Problem

_What user problem does this solve? Tie to the validated hypothesis._

New B2B SaaS accounts struggle to experience useful team collaboration early enough to justify continued use. The supplied customer feedback points to three problems: low team adoption, slow discovery of value, and an inability to demonstrate measurable impact.

The supplied baselines are 22% week-one activation, 6.2 days median time-to-first-value against a 1-day target, and $1.1M ARR at risk in the next renewal window. Their underlying sources, measurement periods, and sample sizes have not been verified.

The hypothesis is not yet validated: a guided week-one path that helps an owner identify an onboarding bottleneck and a teammate complete a specific fix will increase activation above 40% and reduce 90-day churn versus control. The prototype demonstrates the proposed workflow; it does not establish either outcome.

## Users & jobs

- **Primary user:** Primary: new account owner / customer success lead
- **Job to be done:** | User | Job to be done | |---|---| | **Primary: new account owner / customer success lead** | Identify where onboarding stalls and coordinate a useful first action with a teammate in week one. | | Invited teammate | Understand the evidence, complete an assigned fix, and verify that it works. | | Product manager | Monitor invitations, activation, and retention to determine whether guided onboarding improves outcomes. |

## Scope

- **In:** Five connected screens: Opportunity, Week-one Path, Experiment Readout, Team Workspace, and PM Dashboard.
Guided bottleneck identification, assignment, teammate role switching, verification, and owner completion view.
Simulated invitations with pending/accepted states and a quick-start template.
Local event history and perceived-value feedback.
Loading skeletons, empty state, invite errors with retry, and dashboard connection-lost messaging.
Illustrative treatment/control metrics and explicit experiment decision criteria.
- **Out (explicitly):** Authentication, real user identities, permissions, and actual multi-user collaboration.
Email delivery, live product integrations, or production changes.
Shared backend storage or production analytics.
Actual experiment assignment, statistical analysis, or measured retention results.
Verified business impact from completing simulated actions.

## Requirements

| # | Requirement | Priority | Acceptance criteria |
|---|---|---|---|
| 1 | Present customer context and hypothesis | Must | Opening screen displays all three supplied quotes, supplied metrics, and activation/retention success criteria. |
| 2 | Identify an onboarding bottleneck | Must | Owner reviews the sample funnel and selects first-report creation; another selection produces corrective feedback. |

## Data & events

_What gets stored, what gets tracked._

| Data | Current implementation | Needed for a live test |
|---|---|---|
| Customer quotes and baseline metrics | Supplied content rendered on screen; provenance unverified | Source, measurement period, population, and metric definitions |
| Usage funnel | Fictional 20-account cohort | Timestamped account-level product usage |
| Team membership and invitations | Browser-local records; acceptance simulated | Verified identities, invitation delivery, acceptance timestamps, permissions |
| Assignments and verification | Local state; no real product change | Persistent task ownership, completion evidence, and verification |
| Interaction events | Stored in browser localStorage | Durable, deduplicated analytics with account ID, user ID, role, and timestamps |
| PM cohort metrics | Static illustrative fixtures | Randomized account assignment and measured cohort outcomes |

## Open questions

Does completing this collaborative workflow predict customer value and retention, or merely task completion?
Is changing an onboarding checklist an appropriate action for the intended customer’s role and permissions?
How was the original 22% activation baseline defined, and is it comparable with the proposed two-person definition?
What evidence should qualify a real fix as implemented and verified?
When does the seven-day window start, and how should late invitations or reassigned tasks be handled?
What are baseline 90-day churn, minimum meaningful improvement, required sample size, and experiment duration?
How should churn be defined for annual contracts that do not renew within 90 days?
What guardrails will detect increased workload, support burden, or low-quality invitations?
