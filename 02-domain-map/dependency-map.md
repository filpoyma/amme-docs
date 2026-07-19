# Dependency Map

## Rule

A module may depend on another module only through a public command, a documented query/projection, or subscribed domain events. Direct writes and private-table joins across modules are forbidden.

## Core dependency directions

| Consumer | May use | Reason |
| --- | --- | --- |
| CRM | Identity, Files, Notifications | actor identity, protected documents, communications |
| Booking | CRM, Service catalogue, Accommodation, Finance | guest reference, availability, allocation request, payment status query |
| Accommodation | Booking, Staff & operations, Notifications | allocation requests, work assignment and alerts |
| Wellness / Kitchen / Transfers | Booking, Service catalogue, Staff & operations, Inventory | entitlement, availability, work and stock consumption |
| Retreats & events | CRM, Booking, Service catalogue, Finance | participants, bookings, programme capacity, payment state |
| Finance | CRM, Booking, Notifications | counterparties, invoice context, payment requests |
| Automation and AI workforce | published events plus public commands/queries | orchestration without ownership of transactions |
| Analytics | documented read projections and events | reporting only; no operational writes |

## Event collaboration example

```text
Finance: Payment Received
  ├─ Booking updates eligibility/status under its own rules
  ├─ Automation evaluates approved workflows
  ├─ CRM updates the guest timeline projection
  ├─ Notifications may send a receipt
  └─ Analytics refreshes revenue projections
```

`Finance` does not directly confirm a booking; it reports payment receipt. Booking decides whether that fact meets its confirmation rule.

## Forbidden shortcuts

- Finance cannot set `booking.status`.
- Booking cannot mark an invoice paid.
- AI cannot bypass command handlers or permissions.
- Analytics cannot be used as an operational source of truth.
