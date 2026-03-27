# Manual Test Scenarios for Salesforce QA

Use this reference to quickly generate scenario packs during planning.

## 1) Lead-to-Opportunity (Sales Cloud)

- Create lead with minimum required fields.
- Convert lead to Account + Contact + Opportunity.
- Validate mapped fields after conversion.
- Confirm duplicate rule behavior during convert.
- Negative: conversion blocked when mandatory downstream field missing.

## 2) Case Management (Service Cloud)

- Create case from agent console.
- Validate assignment rule routing.
- Trigger escalation after SLA threshold.
- Close case and verify required close fields.
- Negative: unauthorized user cannot edit restricted case fields.

## 3) Flow Automation

- Trigger record-triggered flow on create/update.
- Validate decision branches for all major paths.
- Confirm rollback behavior on flow fault.
- Verify fault email/log details are useful.
- Bulk test with multiple records.

## 4) Security and Access

- Profile-only user can see only allowed tabs/objects.
- Permission set grants incremental object/field access correctly.
- Record sharing via role hierarchy behaves as expected.
- Private object records hidden from unrelated users.
- Negative: API user with limited permissions gets expected authorization errors.

## 5) Integration Touchpoints

- Outbound callout payload format is correct.
- Failed callout retry/dead-letter flow works.
- Inbound API upsert maps to correct external IDs.
- Invalid payload returns meaningful error.
- Idempotency: duplicate inbound messages do not create duplicates.

## 6) Reporting and Dashboards

- Record appears in correct report with intended filters.
- Dashboard visibility obeys running user settings.
- Cross-filter/subscription behavior is correct.
- Historical trending/snapshot logic (if used) is accurate.
- Negative: restricted records are excluded for limited users.
