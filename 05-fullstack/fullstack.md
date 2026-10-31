# Full-Stack: Data, Access Rules, Edge Cases, Deploy

> Module 5 · Full-Stack. Add data schemas, access rules, and edge cases; stress-test and deploy.

## Deployed link

_The working, shareable link that survives real users._

https://account-risk-rohit-30.rohit-tippani93.chatgpt.site/

## Data schema

| Entity | Key fields | Notes |
|---|---|---|
| Accounts | id, name, created_by, created_at | Represents a workspace. A personal workspace is created when its owner saves their first invitation. |
| Invitations | id, account_id, email, recipient_name, invited_by, status, invited_at, expires_at | Stores saved invitation records. Email delivery and acceptance are not connected yet. |

## Access rules

_Who can see / do what? Where are the auth boundaries?_

Supabase Auth handles signup and login. Row-level security restricts personal records to the signed-in user: for invitations, the invited_by field must match their authenticated user ID. Only an authorized workspace owner can create an invitation. Some shared analytics tables remain inaccessible because they don’t have an individual owner.

## Edge cases hardened

| Case | Before | After |
|---|---|---|
| Empty / first-run state | Team Workspace displayed sample teammates. | Shows “No invitations yet” when there are no saved records, with an option to add one. |
| Bad / malicious input | Invitation entries were simulated in the browser. | The server validates the email and name, checks the signed-in owner, and rejects duplicate pending invitations. |
| Failure / offline | Simulated timers drove loading and failure states. | The live invitation list shows an error and Retry if it can’t load. An uncertain save can be retried with the same request key to avoid duplicates. |

## Stress test results

_What you threw at it, and what held / broke._

1. Checked with new email and confirmed empty states
2. Submitted multiple times and ensured no duplicates are created
3. Tested UI acknowledgment of internet disconnection or hang
