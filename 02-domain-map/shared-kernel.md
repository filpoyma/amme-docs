# Shared Kernel

The shared kernel is intentionally small. It contains stable technical primitives and value objects, not a grab-bag of business entities.

| Shared concept | Meaning |
| --- | --- |
| Identifier | Typed immutable identifier, usually UUID. |
| Money | Amount plus ISO currency; arithmetic and rounding are explicit. |
| Date range / time range | Inclusive/exclusive semantics defined once before implementation. |
| Local date-time and timezone | A centre timezone is configured; stored instants remain unambiguous. |
| Email and phone | Validated contact values, not loose strings. |
| Address and country code | Structured postal/location values. |
| Audit metadata | Created/updated timestamps and actor attribution. |
| Actor reference | Human, system, AI agent or integration identity. |
| Correlation and causation IDs | Trace one workflow and the event that caused a later event. |
| Pagination and sorting contract | Shared query boundary conventions. |

Do not put `Guest`, `Booking`, `Invoice`, status enums or repository interfaces in the shared kernel. Those belong to their owners and would turn the kernel into hidden coupling.
