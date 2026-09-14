# CRM Model

## Person aggregate

`Person` is the canonical profile for an individual. A person may simultaneously be a lead, staying guest, retreat participant, day-event visitor, payer and organiser contact; these are roles in context, not duplicate profiles.

It owns:

- legal/display name;
- contact methods and their verification state;
- guest preferences and consents;
- links to identity documents and health-information access scopes;
- deduplication/merge history.

For a lead, name and phone are required. For a guest, name and phone are required; email is recommended. Passport and medical data are not prerequisites for creating the profile, but may be required by a later check-in or service policy.

## Organisation aggregate

`Organisation` represents a company, agent or retreat organiser. It owns company name, contact person reference, tax ID where applicable and business contacts. It is distinct from the individual person profile.

## Party references and privacy

Booking stores `PersonId` references for guests and contacts. Finance uses a `PartyReference` plus an immutable `BillToSnapshot` on an issued invoice, so later edits to a person or company do not alter historical billing documents.

Sensitive health and document data is not copied into Booking, Finance or general communication projections. Those modules receive only the minimum allowed reference or derived constraint, such as a kitchen-safe allergy instruction.
