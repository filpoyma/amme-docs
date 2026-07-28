# Ownership

The owner alone validates and changes a concept's authoritative state. Other modules hold identifiers, snapshots or read projections only.

| Concept | Owner | Notes |
| --- | --- | --- |
| User, role, permission | Identity & access | Employee profile is not an access-control record. |
| Lead, guest, preference, loyalty, conversation | CRM | A person may be both a guest and retreat participant. |
| Booking, stay, reservation item | Booking | A booking is the commitment; a stay is actual occupancy. |
| Room, category, room readiness, maintenance | Accommodation | Booking requests allocation; it does not mutate a room. |
| Service definition, resource capacity, generic availability | Service catalogue & scheduling | Delivery details belong to specialist modules. |
| Wellness appointment and outcome | Wellness & activities | |
| Menu, F&B order and kitchen ticket | Kitchen & F&B | |
| Retreat programme and participant registration | Retreats & events | Event attendance belongs here too. |
| Transfer and excursion execution | Transfers & excursions | |
| Product, stock movement, supplier and purchase | Inventory & procurement | |
| Folio, invoice, payment, refundable deposit, refund, expense and daily close | Finance | A folio collects charges; an invoice is a fixed payment document. Deposits are tracked as refundable guest balances, not revenue. Simplified cashflow accounting; no general ledger yet. |
| Employee, shift and generic task | Staff & operations | Housekeeping and maintenance own their specialised lifecycle. |
| Notification delivery | Notifications & communications | Message content may originate elsewhere. |
| File storage metadata and access grants | Files & documents | Business modules own meaning and retention policy. |
| Rule and workflow execution | Automation | Rules invoke owners through commands. |
| Agent execution, AI proposal and AI action record | AI workforce | The affected business state stays with its owner. |
| KPI and report projection | Analytics | Read-only. |
