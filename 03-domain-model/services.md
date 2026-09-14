# Services and Scheduling Model

## Catalogue and capacity

`ServiceDefinition` is a sellable offer with price, cancellation-policy and payment-condition snapshots. `Resource` is a capacity unit such as a practitioner, treatment room, vehicle, seat or time slot. Scheduling exposes availability without giving other modules permission to mutate resource calendars.

`ServicePackage` owns a package price and an internal allocation across accommodation, meals, programme and extras. The package price is commercial truth for sale; the allocation supports fulfilment and reporting. The allocation must reconcile to the package price.

## Specialist aggregates in the MVP

| Aggregate | Owns |
| --- | --- |
| Wellness Appointment | guest, service, desired/confirmed time, practitioner/resource allocation, consent/checklist and fulfilment outcome |
| Transfer | guest/group, flight or route details, vehicle/driver allocation and completion outcome |
| Retreat Registration | participant, retreat/package, programme entitlement, payment condition and optional linked accommodation |

Restaurant and excursions begin as service charge line items with source references. This deliberately avoids premature dedicated models until their operations require their own independent lifecycle.

## Requests and waitlist

When capacity is absent, a `ServiceRequest` records the guest, desired time, acceptable range and priority. It may enter a waitlist but is not a confirmed appointment. Creating an actual appointment requires an authorised human confirmation, available resource capacity and the applicable payment condition.

Any change to price, dates, room category, package composition or cancellation policy needs recorded guest approval.
