# Assessment Traceability Matrix

## Purpose

This matrix separates the complete NOVA product context from the requirements that must be delivered during the technical assessment. It is not a task decomposition. The candidate remains responsible for planning implementation and tests.

The full target is the two modules defined in [ASSESSMENT.md](../../ASSESSMENT.md). Priority A is executable and required. Priority B must be implemented when time permits or otherwise designed and reported honestly in `SUBMISSION.md`.

## Requirement mapping

| Requirement | Assessment capability | Priority | Main architecture decisions | Minimum verification |
| --- | --- | --- | --- | --- |
| FR-001 | Server-persisted web SaaS | A | AD-05, AD-20, AD-22, AD-24 | Clean bootstrap, migration, logout/login persistence, build and CI |
| FR-002 | Strict Organization isolation | A | AD-01, AD-03, AD-04, AD-27 | Forced-RLS negative tests for read, write, search, counts, and relations using Organizations A and B |
| FR-003 | First-party authentication and least privilege | A | AD-02, AD-20, AD-31, AD-35, AD-42, AD-46 | Password hashing, neutral throttled login, session rotation/revocation, real invitation/reset delivery, direct API authorization, unknown capability, and stale-access tests |
| FR-004 | Organization provisioning and lifecycle | A; terminal follow-up B | AD-05, AD-06, AD-15, AD-26, AD-37 | Provisioning/activation/suspension/reactivation tests, owner invariant, safe evidence |
| FR-005 | Narrow platform user intervention | B | AD-02, AD-26, AD-37 | One-Organization transaction, reason and recent-auth checks, no business enumeration |
| FR-006 | Separate commercial and access status | A | AD-05, AD-06, AD-30, AD-38 | Independent state transitions and lost-update tests |
| FR-009 | Organization → Company → Business Scope hierarchy | A | AD-01, AD-04, AD-27, AD-30 | Tenant-safe constraints, authorized hierarchy access, blocked Company cascade |
| FR-026 | Responsive web delivery | A | AD-20, AD-31 | Critical journeys at 360 px and desktop, keyboard operation, no global horizontal scroll |
| FR-089 | Collaborative administration lifecycle | A; promotion/transfer B | AD-05, AD-06, AD-35, AD-36, AD-37, AD-40, AD-41 | Invitation, grant, suspension/reactivation, last-Administrator, promotion and transfer tests |
| FR-096 | Business Scope identity | A | AD-01, AD-07, AD-27 | Required identity fields, server-derived provenance, authorized filtering |
| FR-114 | Search and selected-context clarity | A | AD-02, AD-20, AD-31 | Server-side authorized search, neutral empty result, late-response/context-switch behavior |
| FR-115 | Guided duplicate-aware scope creation | A | AD-05, AD-06, AD-27 | Review-before-create flow and concurrent duplicate prevention |
| FR-116 | Presets and effective-access view | A | AD-02, AD-31, AD-35, AD-41 | Versioned preset resolution, adjustable grants, access-loss preview, stale mutation refusal |
| NFR-001 | Blocking tenant isolation | A | AD-01, AD-03, AD-27 | Same-connection A → B → A and missing-context PostgreSQL tests |
| NFR-002 | Secure server authorization | A | AD-02, AD-31, AD-35, AD-41, AD-42 | UI and direct API produce the same refusal; access epoch enforced |
| NFR-003 | Transport and secret hygiene | A | AD-22, AD-23, AD-45 | Secret scan, synthetic data, minimized logs and errors |
| NFR-005 | Environment separation | A | AD-22, AD-24 | Isolated local/test configuration with no production dependency |
| NFR-006 | Operational signals | A | AD-15, AD-23, AD-37 | Structured errors and lifecycle evidence with correlation IDs |
| NFR-010 | Responsive/browser compatibility | A | AD-20, AD-31 | Documented browser target and responsive end-to-end checks |
| NFR-011 | Functional accessibility | A | AD-31 | Keyboard, focus, labels, errors, and non-color-only meaning |
| NFR-015 | Delivery documentation | A | AD-24, AD-45 | Clean-clone commands, CI, architecture notes, honest limitations |
| NFR-017 | Future integration boundary | A at boundary level | AD-04, AD-07, AD-08, AD-30 | Domain model has no provider dependency; no real connector required |
| NFR-018 | Resend transactional email | A | AD-05, AD-06, AD-22, AD-23, AD-46 | Template/schema validation, deterministic adapter tests, idempotency tests, and real invitation/reset smoke delivery to a reviewer-controlled mailbox |

## Critical end-to-end journeys

1. The securely bootstrapped Platform Administrator logs in with first-party credentials, provisions an Organization, and sends the initial-owner invitation.
2. The matching owner accepts once; the Organization activates with exactly one owner and an Administrator membership.
3. The owner creates a Company and a duplicate-aware Business Scope.
4. The owner invites a User with explicit capabilities and scope; the matching User accepts once and sees only authorized records.
5. The owner reduces access or suspends the User; direct API calls and an already-open session lose access immediately.
6. The owner reactivates the User with only current grants.
7. Organization A cannot read, search, count, mutate, export, or reference Organization B data.
8. Login throttling, session fixation prevention, logout, expiry, and suspension revoke access as specified without leaking credentials or account existence.
9. Password-reset requests are neutral; the single-use token expires at the exact boundary, and successful reset revokes every session for the identity.

Promotion, ownership transfer, advanced platform intervention, and terminal-disablement follow-up follow the Priority B rule in `ASSESSMENT.md`. Real transactional delivery through Resend is Priority A.

## Evidence expected in the submission

- requirement IDs referenced in relevant test names or test descriptions;
- migration and policy files for database invariants;
- CI output for lint/type checks, unit, PostgreSQL integration, end-to-end, and build;
- `SUBMISSION.md` listing delivered scope, deferred items, known risks, and the accessible Loom demonstration link;
- a Loom video of no more than 10 minutes showing the running platform, the implemented modules and features, and the principal functional journeys working end to end, using only synthetic data and exposing no secrets, tokens, private links, or sensitive configuration;
- a private submission repository accessible to the GitHub user `mbouzian42` throughout the review process;
- safe evidence of the Resend configuration and successful invitation/reset smoke delivery, without exposing addresses, links, tokens, or secrets.
