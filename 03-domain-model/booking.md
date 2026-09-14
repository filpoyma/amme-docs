# Booking Model

## Master Booking aggregate

`MasterBooking` is the commercial container for one enquiry or agreement. It owns the booking contact, participating guest references, applicable commercial/cancellation policy snapshots, linked room reservations and a reference to the primary folio. It supports families, groups and full-villa bookings without forcing each room into a separate commercial agreement.

It must not become a second room calendar. Room occupancy and lifecycle live in its `RoomReservation` entities; physical allocation is owned by Accommodation.

## Room Reservation entity

Each `RoomReservation` belongs to one master booking and has independent:

- requested category and confirmed room reference;
- arrival/departure period, including day-use where applicable;
- guest stays with individual from/to dates;
- occupancy and selected room configuration;
- price and cancellation-policy snapshots;
- lifecycle state and end-state reason;
- approved early check-in, late checkout, extension and move history.

At `Confirmed`, it must reference a specific physical room through an active Room Allocation. A room-reservation extension updates this entity and requires Accommodation to validate its revised allocation.

## Hold aggregate

`Hold` reserves capacity in a **room category**, never an unspecified confirmed room. It records guest/contact reference, requested period, category, expiry deadline, actor, reason and source. It becomes unavailable automatically when expired; an expired hold is represented as `Cancelled` with reason `hold expired`.

Normal human-created holds expire after 24 hours. Manager-approved group, retreat or full-villa holds may expire after up to 48 hours. A guest may have at most three active human-created holds. AI may create one active 15-minute hold and cannot extend it.

## Confirmation and cancellation

Reception, Manager and Owner may confirm accommodation bookings. Confirmation requires guest name, phone/WhatsApp, dates, guest count, a valid physical-room allocation and the applicable payment condition. Passport, agreement and full payment are not universal confirmation prerequisites.

Only a Manager may restore a cancelled reservation, and only after availability is validated again. No-show is recorded by staff after the agreed deadline and contact attempt; a Manager decides whether to release later nights.
