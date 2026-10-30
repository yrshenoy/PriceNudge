# PriceNudge documentation

This folder contains the product and engineering documentation for **PriceNudge**.

## Current specification

- [Functional & Technical Specification — V1.3](requirements/functional-technical-spec-v1.3.md): product rules, V1/V2 scope, receipt-first onboarding, workflow details, data model, monitoring architecture, proposed API, screens, acceptance criteria, and open decisions.

## Visual workflows

The specification includes Mermaid diagrams at the relevant requirements sections. Editable source files are also available:

- [Receipt-first guest onboarding](diagrams/01-receipt-first-onboarding.mmd)
- [Price matching and policy-aware alerts](diagrams/02-price-matching-and-alerts.mmd)
- [Monitoring event lifecycle](diagrams/03-monitoring-event-lifecycle.mmd)
- [Privacy and consent boundaries](diagrams/04-privacy-and-consent-boundaries.mmd)

## Deferred features and future roadmap

- [Deferred Features & Product Roadmap](roadmap.md): all 21 deferred use cases, reasons for deferral, V1 limitations, potential V2 dependencies, and cross-location/channel expansion. V2 is a candidate scope, **not a committed release date**.

## Document status

- **Source:** latest owner-edited V1.3 Word document, adapted for GitHub Markdown.
- **Clarification incorporated:** verified merchant policy → an editable price-adjustment claim draft may be provided; unknown/unverified merchant policy → informational lower-price alert only, **no claim draft**.
- **Approved product decisions:** indicated as **AGREED**.
- **Engineering recommendations requiring confirmation:** indicated as **PROPOSED**.
- **Scope:** V1 focuses on peer-contributed receipts and same-store same-channel matching; no retail integrations or price scraping.

## Suggested future docs

- `architecture/` — architecture decision records and system diagrams.
- `api/` — API contracts and schemas.
- `use-cases/` — granular product acceptance criteria and delivery backlog.

Please avoid committing real customer receipts, private personal data, credentials, or API keys.
