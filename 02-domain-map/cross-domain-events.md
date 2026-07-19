# Cross-Domain Events

The Event Storming stage remains the complete candidate list. This document identifies high-value facts that cross ownership boundaries and therefore need stable envelopes, idempotent consumers and documented policies.

| Publishing owner | Event | Likely subscribers | Boundary rule |
| --- | --- | --- | --- |
| CRM | Lead Created | AI workforce, Notifications, Analytics | Subscribers never mutate the lead directly. |
| Booking | Booking Created / Booking Confirmed / Booking Cancelled | Accommodation, Finance, Staff & operations, Analytics | Finance reacts with billing policy; Booking owns status. |
| Accommodation | Room Assigned / Room Ready / Maintenance Reported | Booking, Staff & operations, Notifications | A room assignment is an allocation fact, not booking confirmation. |
| Finance | Invoice Issued / Payment Received / Payment Failed / Refund Issued | Booking, CRM, Notifications, Automation, Analytics | Booking decides whether payment changes eligibility. |
| Wellness | Session Booked / Session Completed | Booking, CRM, Finance, Analytics | Delivery owns completion evidence. |
| Kitchen & F&B | Order Created / Order Ready / Order Delivered | Notifications, Inventory, Finance, Analytics | Inventory records its own consumption transaction. |
| Inventory | Minimum Stock Reached / Product Received | Kitchen & F&B, Staff & operations, Finance, Automation | Stock thresholds trigger workflows, not automatic purchases by default. |
| Staff & operations | Task Completed / Shift Finished | Accommodation, Analytics, Automation | Completion refers to the task, not necessarily underlying business acceptance. |
| Automation | Automation Execution Completed / Failed | AI workforce, Notifications, Analytics | Workflow telemetry does not replace domain facts. |
| AI workforce | AI Proposal Created / AI Action Completed | owning module, Staff & operations, Analytics | The owner records the business result separately. |

## Event envelope minimum

Every published event later needs an immutable ID, name/version, occurred-at timestamp, aggregate reference, actor reference, correlation ID, causation ID and schema-versioned payload. Delivery state belongs to the outbox/consumer, not the event fact itself.
