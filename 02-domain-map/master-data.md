# Master Data

Master data is relatively stable configuration reused by operational transactions. Ownership is still explicit; it is not a global mutable dictionary.

| Master data | Owner |
| --- | --- |
| Centre profile, operating timezone, policies | Identity & access / settings |
| Roles and permission definitions | Identity & access |
| Room categories and rooms | Accommodation |
| Service catalogue, packages, price lists and resources | Service catalogue & scheduling |
| Employees, roles in operations and skills | Staff & operations |
| Product catalogue, units of measure, suppliers and storage locations | Inventory & procurement |
| Payment methods, tax configuration and expense categories | Finance |
| Notification templates and channel configuration | Notifications & communications |
| Countries, nationalities, languages and currencies | Shared reference data |

Rates, availability and stock are operational state, not master data. A price list can be master data; a quoted booking price is an immutable commercial snapshot.

The operating and settlement currency for the first version is **IDR**. Multi-currency support is deferred; no USD deposit or exchange-rate logic is implied by this map.
