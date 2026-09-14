# Accommodation Model

## Room aggregate

`Room` represents one physical room. It owns its identifier, category, capacity, child/extra-bed rules and supported `RoomConfiguration` values such as King, Twin or King plus Extra Bed. A configuration is valid only if the room explicitly supports it.

Operational presentation states are `Available`, `Occupied`, `Dirty` and `Out of Service`. They are not sufficient for sales decisions by themselves: sellability is derived from allocations and active blocks.

## Room Allocation aggregate

`RoomAllocation` is the authoritative assignment of one confirmed Room Reservation to one Room for a precise period. It records allocation source, reservation reference, room, time range, configuration and a retained history of releases/reassignments.

Booking requests creation, amendment or release. Accommodation validates conflicts and publishes the resulting fact. A move after check-in releases the old allocation only from the move time and creates a new allocation; it never rewrites history.

## Operational Block aggregate

`OperationalBlock` makes a room unavailable independently of commercial reservations. Reasons include cleaning, inspection, maintenance, repair, sanitation, owner use and a manual block. It records its period, reason, creator, evidence where needed and release/approval information.

Safety or material technical blocks cannot be overridden for sale. A manager may release a cleaning/inspection block after actual checking, or allow sale with a documented minor defect and prior guest notification.

## Availability

Category availability is a derived result of Rooms, active Room Allocations and Operational Blocks. A confirmed reservation requires a concrete room allocation even though its earlier hold only reserved category capacity. No two active allocations may overlap for the same room and time range.
