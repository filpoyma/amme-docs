# AMME Docs

Product and architecture knowledge base for **AMME** — an AI-first operating system for a small hospitality and retreat centre: 10 rooms, kitchen and service, pool, sauna, yoga shala, retreats, day events, airport transfers and excursions.

## Repository map

- `00-product/` — product intent and shared language.
- `01-event-storming/` — the evolving domain-event map.
- `02-domain-map/` — module boundaries, ownership and allowed dependencies.
- `03-domain-model/` — core aggregates, entities, value objects and invariants.
- `04-business-rules/` — approved operational policies, approvals and exceptions.
- Later stages are deliberately not pre-created: each is added when its inputs are stable.

## Roadmap

1. `00-product-vision`
2. `01-event-storming`
3. `02-domain-map`
4. `03-domain-model`
5. `04-business-rules`
6. `05-state-machines`
7. `06-command-model`
8. `07-read-models`
9. `08-database`
10. `09-api`
11. `10-ui`
12. `11-ai`
13. `12-telegram`
14. `13-automation`
15. `14-deployment`

## Working rule

An event records a completed, observable fact in the past tense. It is not a screen, command, wish, or database mutation. AI decisions and human overrides are recorded separately so that automation remains auditable.

See [Event Storming](01-event-storming/README.md) to start.
The current architecture stage is [Business Rules](04-business-rules/README.md).
