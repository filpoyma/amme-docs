# Event Storming

This is the source event map for AMME. The target is approximately **500 reviewed events**, developed context by context rather than invented as a flat checklist.

## Event types

| Type | What it records | Example |
| --- | --- | --- |
| Business event | A completed domain fact that changed the centre's state. | `Booking Confirmed` |
| AI decision event | A traceable AI conclusion or proposal; it does not itself change the business state. | `AI Proposed Room Assignment` |
| AI action event | A completed action the AI was authorised to take. | `AI Sent Quote` |
| Human decision / override | A completed staff decision that approves, rejects or replaces a proposal. | `Manager Overrode Price` |

## Modelling conventions

- Names are past tense and fact-based.
- An event is not duplicated merely because it has another notification channel.
- Causation, correlation, actor, policy version and source evidence should be captured in the eventual event envelope.
- AI events must identify the agent and policy; sensitive or financial actions require an approval policy.

## Context map

| Context | File | Initial events |
| --- | --- | ---: |
| CRM & Leads | [crm-leads.md](crm-leads.md) | 14 |
| Guests | [guests.md](guests.md) | 11 |
| Reservations | [reservations.md](reservations.md) | 17 |
| Stay | [stay.md](stay.md) | 15 |
| Housekeeping | [housekeeping.md](housekeeping.md) | 13 |
| Maintenance | [maintenance.md](maintenance.md) | 12 |
| Finance | [finance.md](finance.md) | 16 |
| Kitchen & F&B | [kitchen.md](kitchen.md) | 18 |
| Wellness & activities | [wellness.md](wellness.md) | 18 |
| Retreats | [retreats.md](retreats.md) | 16 |
| Airport transfers | [transfers.md](transfers.md) | 14 |
| Excursions | [excursions.md](excursions.md) | 15 |
| Inventory & procurement | [inventory-procurement.md](inventory-procurement.md) | 17 |
| Staff | [staff.md](staff.md) | 15 |
| Automation & messaging | [automation-messaging.md](automation-messaging.md) | 13 |
| AI workforce | [ai-workforce.md](ai-workforce.md) | 20 |
| Analytics & governance | [analytics-governance.md](analytics-governance.md) | 12 |

**Initial map: 266 event candidates.** Counts are planning numbers, not a claim that every candidate is final. Each event needs later review for invariant, owner, command, policy and integration boundary.
