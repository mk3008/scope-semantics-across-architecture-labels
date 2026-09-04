# Business-process consistency dogfood preregistration

This longitudinal research-only study observes a PostgreSQL-backed business application as activities are added. It does not create an architecture, a DDD alternative, terminology, rules, or a product decision.

The model uses established terms: business process, activity, performer, data model, business rule, precondition, postcondition, invariant, integrity constraint, consistency, satisfiability, under-specification, reachability, and soundness. No Domain/DDD premise applies.

## Stack

Node.js ESM, the `pg` PostgreSQL driver, raw SQL, PostgreSQL 16, Docker Compose, and Node integration tests are fixed. This uses actual relational DDL and avoids ORM/query-builder/schema-generation behavior. Docker is available in this environment; no simpler substitute is used.

## Study procedure

All DDL, stage packets, common prompts, and cumulative acceptance tests are frozen before Stage 1. Each implementation and refactoring task is a fresh Terra/medium task. Each cross-activity review is a fresh Sol/medium, read-only task. Workers receive only their current cumulative state and current-stage packet; they do not receive future packets, prior research conclusions, or other-arm material.

Structural guidance is exactly:

`For physical placement, choose the narrowest meaningful semantic boundary that owns the decision and contains its current required consumers.`

No expected tree, layer, or shared-code objective is supplied. After every implementation: behavior verification, cross-activity consistency review, then (if no blocker) fresh refactoring. A consistency review must exhaust all discoverable current-snapshot blockers; under-specification, inconsistency, or data-model insufficiency stops later stages pending an appended human decision.
