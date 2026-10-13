# MissionCart + SYNESIS project plan

## Scope and guardrails

One React/Vite/TypeScript repository will contain MissionCart and, later, the SYNESIS operations interface. A future FastAPI backend and SQLite database will be the shared source of truth. No real payment, marketplace, bank, or commerce-platform integration is implied; all future demo data must remain synthetic unless authorized connections are added.

## Phase 1 — MissionCart storefront foundation (current)

- Inspect and preserve the workspace; record the real baseline.
- Establish the React + Vite + TypeScript frontend if no usable application exists.
- Deliver a responsive product catalogue, search, category filters, product details, and local cart interactions with graceful image fallback.
- Keep sample catalogue data and the API boundary isolated; no backend, checkout, order history, or SYNESIS dashboard.

## Phase 2 — Shared transaction backend

- Implement FastAPI and SQLite with isolated database access.
- Add order and transaction-event records, including transaction ID, event type, timestamp, state, source platform, and order/payment identifiers.
- Expose MissionCart catalogue/order APIs and connect the frontend through the centralized API client.

## Phase 3 — Monitoring, fault injection, and diagnosis

- Normalize MissionCart events into the canonical schema.
- Add deterministic inconsistency detection, controlled fault injection, incident creation, evidence timelines, and evidence-based probable root-cause diagnosis.

## Phase 4 — Safe recovery and auditability

- Add idempotency keys, recovery permission checks, final-state verification, and immutable audit history.
- Never retry a payment whose outcome is uncertain; distinguish SUCCESS, FAILED, PENDING, and UNKNOWN.

## Phase 5 — Second source adapter

- Add a simulated Store B adapter with a different input format.
- Verify both MissionCart and Store B normalize into, and are processed by, the same monitoring engine.

## Phase 6 — SYNESIS operations dashboard

- Build the separate operations interface with transaction explorer, incidents, investigations, evidence timeline, recovery controls, results, audit history, and database-derived reliability metrics.

## Phase 7 — End-to-end validation and local-network readiness

- Test the mandatory purchase-to-recovery scenario end to end.
- Configure local-network frontend/API access, CORS, IP/port documentation, and fix critical integration issues.
- Reassess storage needs before public deployment; migrate from SQLite to managed PostgreSQL when deployment persistence or concurrency requires it.
