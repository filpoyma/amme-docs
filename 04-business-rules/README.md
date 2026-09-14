# Business Rules

This stage turns the approved operating policy into enforceable rules. Each rule states the condition, required system outcome, authorised exception and audit evidence. State transitions remain the subject of the next stage.

## Rule groups

1. [Booking and commercial policy](booking-and-commercial.md)
2. [Accommodation and guest stay](accommodation-and-stay.md)
3. [Finance and settlement](finance-and-settlement.md)
4. [Guest safety, services and house rules](guest-services-and-house-rules.md)
5. [Authority, privacy and service levels](authority-privacy-and-sla.md)

## Principles

- Configuration such as cancellation bands, deposits, discount limits, tax rates and SLA targets is versioned policy, never invisible code.
- An exception requires a named authorised actor, reason and evidence where relevant.
- `Payment Overdue` is a Finance condition. It permits an authorised cancellation decision; it does not itself cancel a reservation.
- Any monetary amount in this stage is IDR.
