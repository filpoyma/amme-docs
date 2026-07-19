# Bounded Contexts

## CRM

Owns prospect and guest relationship data from first contact onward. It does not own bookings, room availability, invoices or payment state.

## Booking

Owns the commitment to provide a set of reservation items and the lifecycle of booking and stay. It asks Accommodation to allocate rooms and Finance whether payment conditions are met; it never changes either directly.

## Accommodation

Owns physical rooms, room categories, allocation decisions, housekeeping readiness and maintenance. It does not sell rooms or collect money.

## Service catalogue & scheduling

Owns sellable service definitions, price/configuration and generic resource capacity. It is the common layer for accommodation, wellness, food, transfers, excursions, retreats and events, without pretending their delivery rules are identical.

## Delivery contexts

Wellness, Kitchen & F&B, Retreats & events, and Transfers & excursions each own specialised fulfilment. Inventory owns stock, not kitchen order status; Staff & operations owns cross-cutting task assignment, not the business outcome of a treatment or transfer.

## Finance

Owns receivables and cash movements: invoices, payment attempts/receipts, refunds, expenses, cashflow and close. The scope is simplified operational finance, not statutory double-entry accounting.

## Intelligence contexts

Automation, AI workforce and Analytics consume facts and public projections. They do not own guest, booking, room or financial truth. Notifications is a delivery capability with an auditable delivery lifecycle.
