# Domain Model

This stage translates the approved Domain Map into business aggregates. It deliberately defines behaviour, ownership and invariants before PostgreSQL tables, HTTP endpoints or screens.

## Scope

The first model covers the transactional core of AMME:

1. CRM identities and parties.
2. Booking, holds, room reservations and stays.
3. Accommodation, room allocation and operational blocks.
4. Finance: folios, invoices, payments and refundable deposits.
5. Service catalogue, resources, packages and the initial specialist service aggregates.

Restaurant orders and excursions remain chargeable service line items in the MVP. They become dedicated aggregates only when their operational workflow needs it.

## Reading order

1. [Core model](core-model.md)
2. [CRM](crm.md)
3. [Booking](booking.md)
4. [Accommodation](accommodation.md)
5. [Finance](finance.md)
6. [Services and scheduling](services.md)
7. [Cross-aggregate invariants](invariants.md)

## Modelling rules

- An aggregate owns its consistency rules and changes only through its own commands.
- References across aggregates use IDs and immutable snapshots, never shared mutable entities.
- A status belongs to the smallest thing whose lifecycle it represents. A mixed group booking does not pretend to have one room-reservation status.
- Current state remains authoritative. Events record completed facts and are not the primary persistence model.
