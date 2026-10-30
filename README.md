# PriceNudge

**Prices drop. We'll let you know.**

> **Independent portfolio case study — concept and product design, not a live service.** PriceNudge is a hypothetical product concept developed to demonstrate product thinking, requirements definition, privacy-aware architecture, and engineering trade-offs. The documentation describes a proposed implementation, not a production deployment. Features, performance, retailer participation, and refund eligibility have not been validated or guaranteed.

PriceNudge is a proposed peer-powered post-purchase price-monitoring platform. Shoppers upload receipts, discover lower prices observed by other shoppers at the same store, and identify potential price-adjustment opportunities.

> **Status:** Version 1 functional/technical specification is a draft design baseline for this portfolio case study. PriceNudge has not been implemented or released.

## Version 1 at a glance

- **Receipt-first onboarding:** Preview extracted purchases without registering; create an account to save purchases and start monitoring.
- **Documented purchases:** Receipts or qualifying completed online-purchase documents; customers can review and correct extracted data.
- **Peer-powered discovery:** Consent-permitted anonymized price observations from other shoppers, not retailer integrations or live price scraping.
- **Strict comparability:** Identical verified product, merchant, physical store or regional online storefront, purchasing channel, unit basis, and currency.
- **Time-bounded monitoring:** Merchant-specific verified price-adjustment window, or a provisional **30 days from purchase** if the policy is unknown.
- **Historical backfill:** Late receipt uploads can be evaluated against existing peer observations whose transaction dates fall within the eligible window.
- **Clear eligibility language:** Verified-policy opportunities may include an editable claim draft; unknown-policy alerts are **informational only**, without a claim draft or refund guarantee.
- **Privacy by design:** Private source receipts, user-controlled sharing consent, temporary guest uploads, and administrator-executed deletion requests.

## Documentation

- [V1.3 Functional & Technical Specification](docs/requirements/functional-technical-spec-v1.3.md)
- [Deferred features and V2+ roadmap](docs/roadmap.md)
- [Documentation index](docs/README.md)

The current specification includes the agreed use-case scope, workflows, business rules, data model, monitoring architecture, HTTP API outline, screens, acceptance criteria, and unresolved engineering decisions.

## Development

Implementation structure, technology choices, and backlog will evolve from the specification. Proposed engineering details are marked **PROPOSED** in the document; approved product decisions are marked **AGREED**.

**Reminder:** A lower price on a peer receipt is a historical transaction observation, not proof of a current advertised price or a guaranteed refund.
