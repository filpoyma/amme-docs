# Architecture Principles

## Modular monolith first

AMME ships as one deployable application and one PostgreSQL database. Modules keep logical boundaries, private write models and explicit contracts so they can evolve independently. Splitting into microservices is not a current goal.

## Business modules, not technical layers

Code and documentation are organised by domain (`booking`, `finance`, `wellness`), not global `controllers`, `services` and `repositories` directories. Technical infrastructure may be shared, but it never owns business rules.

## Commands, queries and events

Cross-module collaboration has only three forms:

- **Command**: ask the owning module to perform an action and enforce its invariants.
- **Query**: read an explicitly exposed projection; never write another module's records.
- **Domain event**: publish a completed fact for independent subscribers.

An event is not a command and subscribers must not assume they are the only consumer.

## State plus event journal

Current aggregate state is authoritative. `domain_events` and an outbox provide auditability, automation and integration delivery; they do not replace the transactional model with full event sourcing.

## Composition over inheritance

The catalogue may classify a service as accommodation, wellness, food, transfer, excursion, retreat or event. Specific capabilities and scheduling rules are composed, rather than encoded in a brittle database inheritance tree.

## One centre, explicit future boundaries

All records belong to the single operated centre. Do not add `tenant_id` everywhere prematurely. A future multi-property decision requires a dedicated redesign, not a dormant pseudo-SaaS layer.

## Accountable AI

AI is an actor, never an implicit superuser. It uses the same commands and permissions as staff, records policy/evidence/confidence, and escalates money, safety, privacy and exceptional guest-care decisions according to policy.

## Database is a persistence concern

PostgreSQL implements the model; table shape does not define business language. Modules must not reach into another module's private tables.
