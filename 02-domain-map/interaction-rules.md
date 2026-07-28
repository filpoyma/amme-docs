# Approved Interaction Rules

These decisions resolve the operating questions raised after Event Storming. They are the current source of truth for cross-domain behaviour and must be refined into invariants, state machines and commands in later stages.

## 1. Booking, availability and rooms

- A booking is confirmed only when an authorised human user confirms it **and** its required payment condition is met. A guest message, draft, unreviewed payment or AI action never confirms a booking.
- Standard accommodation normally requires a 50% prepayment. The balance and refundable security deposit are due at check-in unless the contract says otherwise. Small events, sauna and wellness services normally require 100% prepayment.
- A manager may approve a confirmed booking without prepayment. This exception must record the approver, reason and payment deadline; it has the same availability priority as another confirmed booking.
- A draft does not reserve capacity. An active temporary hold, confirmed booking, owner use, maintenance, cleaning/inspection or manual block does.
- A human-created hold lasts up to 24 hours; a group, retreat or full-villa hold may last up to 48 hours when approved by a manager. It expires automatically when its deadline passes; only a manager may extend it with a reason.
- AI may create one active temporary hold for a guest for at most 15 minutes. AI cannot extend a hold.
- A confirmed accommodation booking must contain a specific room. The system does not permit a `confirmed, room pending` state.
- A full-villa or retreat buyout blocks all included rooms. A room cannot be simultaneously sold through the buyout and an individual booking.
- Availability priority is: confirmed booking (including an approved no-prepayment exception), confirmed group/retreat accommodation, a confirmed extension created before the next sale, temporary holds in creation order, then unconfirmed requests. A manager or owner makes the final conflict decision; the system never silently cancels a confirmed booking for a more profitable sale.

## 2. Group bookings, stays and exceptions

- One master booking may contain several room reservations and guests. Each room reservation retains its own dates, occupants, price and status, so it can be amended, moved, extended or cancelled independently.
- Cancelling one room in a group booking is allowed. The system recalculates group pricing and discounts according to the applied commercial policy.
- A guest may be moved after check-in by a manager, administrator or owner. The reason is mandatory and the prior room assignment remains in history. A higher-priced move calculates a charge for remaining nights unless a manager records an approved complimentary upgrade; a lower-priced move produces a credit/refund or requires the guest's agreement to keep the price.
- Early check-in and late checkout need availability and manager/administrator approval. They are recorded on the booking even if dates do not change; a paid or complimentary exception is explicit. Late checkout shifts housekeeping work and warns of conflicts.
- A no-show is recorded by a staff member after the agreed arrival deadline and an attempted contact. Releasing current or future nights requires a manager decision. Retention follows the booked cancellation policy; it is not an automatic payment operation.

## 3. Room operations and checkout

- Checkout closes the guest-facing stay only after the administrator records it and the guest account is closed. Operational availability begins only after a housekeeping/assigned-staff inspection.
- After checkout, a room is `dirty` or `inspection pending`, not available. Cleaning, inspection, active stay, confirmed maintenance, repair, sanitation, owner use and manual block prevent sale.
- A manager may remove a cleaning/inspection block after an actual check. A room with a safety or material technical defect cannot be sold as an exception. A minor defect may be accepted only when the guest is notified and the decision is recorded.
- Photos are required after repair, an incident, a complaint, damage, deep cleaning and before/after a long group rental. They are optional for ordinary turnovers. A manager, administrator or assigned supervisor accepts the result; rejected work returns to `rework` with a comment, deadline and owner.

## 4. Guests, services and capacity

- One CRM person profile can be a guest, participant, day-event visitor, payer and organiser contact. Roles and participations are linked to that profile; sensitive health and financial information have stricter access scopes.
- Accommodation, wellness, dining, transfers, excursions and events use the same guest identity, payment and communications boundaries, but remain separate operational records. A service request does not block a room.
- A service without a free practitioner, place or resource is `requested`/`waitlisted`, never confirmed. It records desired time, acceptable range and priority. Moving a guest from waitlist requires guest consent, available capacity and the required payment condition.
- On a confirmed cancellation or recorded service no-show, the resource slot is released. The system may calculate a recommended refund, but only an authorised human finance user can execute it.
- A retreat is a commercial product with programme, capacity, packages, hosts, budget and cancellation rules. Retreat participation and accommodation are independent: a participant may stay elsewhere and a resident guest need not join the retreat.

## 5. Folios, invoices, payments and deposits

- Finance owns the **folio**, **invoice**, payment allocation, refundable deposit and refund. A folio collects charges during a stay or commercial relationship; an invoice is a fixed payment document generated from selected charges. Adding a later meal does not edit an already issued invoice.
- One payer may receive an invoice covering multiple rooms, guests, services or retreat components. One booking may be related to several invoices, such as prepayment, balance, deposit and incidentals. Invoice lines keep references to the booking, guest, retreat or service they settle.
- A payer can be the primary guest, another person, company, retreat organiser or agent. The payer profile is distinct from the stay's primary guest contact.
- Services may be charged to a guest folio and paid at checkout, unless their policy requires prepayment. Each charge records date, quantity, price, performer, fulfilment status and author.
- Kitchen orders may be paid immediately, charged to an active stay, included in a package or marked complimentary. Charging to room requires an active stay and guest confirmation by signature, PIN, message or equivalent recorded proof; kitchen staff may not add an unconfirmed verbal charge.
- The operating currency is IDR. The refundable security deposit is considered received after payment and is held in the hotel's account, while the system records it separately as the guest's refundable balance rather than revenue. Damage retention needs an authorised, auditable decision.
- Cancellation and no-show outcomes are policy-driven per product and contract. The system does not automatically issue a refund. Accommodation prepayment is normally non-refundable within 30 days, subject to contract and approved rescheduling; wellness/transfers use their own deadline (normally 24 hours); day events and sauna are normally non-refundable but may permit participant transfer.
- Daily close is started by an administrator or manager. It reconciles cash, transfers, card/online payments, room charges, refunds, discounts, unpaid items and cash balance. A closed day is not normally edited; corrections use a current-day reversal, refund, adjustment or extra charge with reason and approval. Only owner/finance administration may reopen a day, with a full audit record.

## 6. Inventory, tasks and authority

- Standard kitchen recipes consume inventory automatically. Manual movements cover actual variances, spoilage, staff meals, complimentary items, test dishes and non-recipe products; every adjustment has a reason and actor. Stocktakes reconcile calculated and physical quantity.
- Tasks can be assigned to a named employee, role/team, or team first and a specific employee on acceptance. They have priority, acknowledgement deadline and completion deadline. Unaccepted tasks notify the team and escalate to the manager; critical tasks escalate immediately.
- Staff can create an expense or purchase request. Initial approval limits are configurable: up to 500,000 IDR for the responsible shift person in an approved category; 500,001–3,000,000 IDR for the manager; above 3,000,000 IDR, free accommodation, non-standard complimentary service, discounts over 10%, large write-offs and large refunds for the owner. A person cannot approve their own request above the small operational limit. All actions include supporting evidence, category, reason and approver.

## 7. AI, communications and privacy

- AI may answer approved routine questions, collect guest data, suggest availability, draft requests, send approved reminders, make the limited temporary hold above and add a guest to a waitlist. It may not confirm, cancel or change a booking/service; move rooms; change practitioner schedules; issue a discount, complimentary service, refund or payment transfer; access health data; or send complaint/safety communication without human approval.
- Version 1 uses WhatsApp, Telegram and email. Instagram is a later inbound-lead channel. CRM keeps a channel-independent communication history linked to the person, conversation, booking, payment context and consent.
- Immediate escalation covers utility/security incidents, an unusable room or sauna, double booking, a guest without a ready room at check-in, material non-payment or chargeback, severe complaint, missing guest, conflict/rule breach, delayed critical cleaning, cancellation affecting a programme, and suspected data leak.
- Passport/identity documents, payment data, health information, allergies, dietary constraints, contact data and stay history are sensitive. Access follows least privilege: kitchen sees only relevant allergy constraints; practitioners see only the health information needed for the procedure. Access, download and changes are logged; documents must not persist in personal phones or open chats.
- Marketing consent is voluntary, separate from service communications and revocable. Photo/video consent is separate as well. Retention periods are defined separately for identity documents, financial records, health information and communications; their exact durations require Indonesian legal review before implementation.
