# Domain Map

This stage converts the event map into bounded business modules. It defines responsibility and collaboration; it does **not** define tables, endpoints, screens or microservices.

AMME is a modular monolith for one retreat centre, not a multi-tenant PMS. A module is a business boundary with owned data and public contracts, not merely a folder.

## Outcomes

- A stable list of bounded contexts.
- One owner for every important business concept.
- Explicit dependency rules and cross-domain events.
- A small shared kernel that prevents accidental duplication of basic value types.

## Reading order

1. [Architecture principles](architecture-principles.md)
2. [Module map](module-map.md)
3. [Bounded contexts](bounded-contexts.md)
4. [Ownership](ownership.md) and [dependencies](dependency-map.md)
5. [Interaction rules](interaction-rules.md) — approved business decisions that govern collaboration between modules.
6. Supporting maps: [master data](master-data.md), [operations](operational-domains.md), [intelligence](intelligence-domains.md), [cross-domain events](cross-domain-events.md) and [future expansion](future-expansion.md).

## Non-goals

- No distributed services or event sourcing.
- No generic `service` inheritance hierarchy in PostgreSQL; service capabilities will use composition in the domain model.
- No claim that every initial Event Storming candidate is approved. Later stages must refine owners, invariants and policies.
