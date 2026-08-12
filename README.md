# CaptainDev SaaS Technical Assessment

This repository contains the standalone brief and product, architecture, security, and UX contracts for a fictional SaaS product named **NOVA**. All names, organizations, and visual assets in this repository are synthetic assessment material.

## Suggested timing

There is no hard submission deadline. Because the role is intended to start by late August or early September, submitting by **Wednesday, 19 August 2026** is strongly encouraged so that reviews and interviews can be completed promptly. Record your actual start and finish times honestly in `SUBMISSION.md`.

## Read in this order

1. [ASSESSMENT.md](ASSESSMENT.md) — mission, scope, deliverables, quality gates, and submission protocol.
2. [Product requirements](docs/product/PRODUCT-REQUIREMENTS.md) — complete product context with explicit assessment markers.
3. [Assessment traceability](docs/product/ASSESSMENT-TRACEABILITY.md) — exact requirements, architecture decisions, and minimum verification applicable to the exercise.
4. [Architecture](docs/architecture/ARCHITECTURE.md) — complete target architecture with explicit assessment markers.
5. [Security invariants](docs/architecture/SECURITY-INVARIANTS.md) — blocking isolation and authorization rules.
6. [UX reference pack](docs/ux/README.md) — applicable mockups and interpretation rules.

## Getting started

You may choose the exact project bootstrap details while respecting the prescribed stack and architectural invariants. Document any deliberate deviation and its rationale.

Your implementation must expose documented commands for installation, database migration, local startup, unit tests, integration tests, end-to-end tests, linting/type checking, and production build.

The assessment requires real invitation and password-reset email through [Resend](https://resend.com/). Create a free Resend account, configure a verified sender or domain according to Resend's current requirements, and inject the API key through environment configuration. Never commit credentials. Automated local and CI tests must use the deterministic adapter described by the architecture and must not send external email.

## AI-assisted workflow

This assessment is intentionally designed to be completed with an AI coding assistant. CaptainDev primarily uses Codex, but you may use Codex, Claude Code, Cursor, or any other coding agent you work effectively with.

The supplied PRD and architecture were prepared using the [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) and remain the source of truth for the exercise. CaptainDev often uses BMAD's full planning and delivery workflow on security-sensitive projects. For a straightforward SaaS implementation, however, installing or running BMAD is **optional**: you may use a leaner development loop if it helps you deliver faster. If you do use BMAD, Dev Loop Automation is a reasonable way to avoid repeating planning ceremonies that have already been completed.

Whichever workflow you choose, work in small vertical slices: implement, run the relevant checks, inspect failures, correct them, and repeat. Document your main AI-assisted workflow and the important decisions you made.

AI use does not lower the delivery bar, but you are not expected to manually review every generated line. Instead, build a strong executable validation harness that gives the AI fast and trustworthy feedback: strict type and lint checks, focused unit tests, real-database integration tests, end-to-end journeys, negative security cases, deterministic fixtures, and repeatable CI. The harness must be reliable and sufficiently comprehensive to detect incorrect behavior and regressions while you iterate. You remain responsible for protecting secrets, investigating failures, validating the final behavior, and delivering a complete runnable submission. Document the main AI-assisted workflow, validation strategy, and known limitations in `SUBMISSION.md`; a raw prompt transcript is not required.

## Source precedence

If documents appear to conflict, use this order:

1. `ASSESSMENT.md` for assessment scope, suggested timing, and deliverables;
2. `docs/architecture/SECURITY-INVARIANTS.md` for security requirements;
3. `docs/product/PRODUCT-REQUIREMENTS.md` for behavior;
4. `docs/architecture/ARCHITECTURE.md` for implementation structure;
5. UX mockups for visual intent only.

Ask for clarification when a conflict cannot be resolved by this order. Do not silently weaken a requirement.
