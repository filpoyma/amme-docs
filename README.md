# AMME Docs

Product and architecture knowledge base for **AMME** — an AI-first operating system for a small hospitality and retreat centre: 10 rooms, kitchen and service, pool, sauna, yoga shala, retreats, day events, airport transfers and excursions.

## Repository map

- `00-product/` — product intent and shared language.
- `01-event-storming/` — the evolving domain-event map; the current priority.
- `02-domain/` through `11-adr/` — implementation-facing specifications, added once the event model stabilises.

## Working rule

An event records a completed, observable fact in the past tense. It is not a screen, command, wish, or database mutation. AI decisions and human overrides are recorded separately so that automation remains auditable.

See [Event Storming](01-event-storming/README.md) to start.
