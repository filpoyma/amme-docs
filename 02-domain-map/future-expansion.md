# Future Expansion

These are explicit possibilities, not commitments. They must not distort the single-centre MVP.

| Possible expansion | Why it is deferred | Architectural implication when approved |
| --- | --- | --- |
| Multiple properties or SaaS tenancy | Adds isolation, configuration and reporting complexity. | Define property ownership and migration strategy; do not bolt on `tenant_id`. |
| OTA/channel-manager integration | Requires external availability, rate and cancellation reconciliation. | Add an integration boundary and idempotent synchronisation model. |
| Public guest portal and mobile app | Needs distinct identity, consent and guest-facing workflows. | Expose deliberate query/command contracts. |
| POS and payment-terminal integration | Changes order/payment reconciliation. | Treat provider transactions as external evidence, not invoice state. |
| Statutory accounting | Requires a chart of accounts and double-entry ledger. | Extend Finance as a dedicated bounded context. |
| Public API / marketplace | Requires versioning, quotas, consent and partner governance. | Publish stable contracts only after internal boundaries prove stable. |
| Advanced forecasting and optimisation | Depends on enough clean historic data. | Keep predictions read-only and explainable. |
