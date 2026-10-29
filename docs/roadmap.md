# PriceNudge — Deferred Features & Product Roadmap

**Status:** Planning document · **Updated:** October 29, 2026  
**Baseline:** [V1.3 Functional & Technical Specification](requirements/functional-technical-spec-v1.3.md)  
**Scope:** Deliberate V1 exclusions and proposed V2+ capabilities; **not a committed implementation schedule**.

## Purpose

- Record features intentionally **deferred from V1**, including why and what the initial release supports instead.
- Keep future ideas distinct from accepted V1 business rules; deferment is **not** a promise of V2 delivery.
- Preserve use-case identifiers (UC-xxx) for traceability to the V1 specification.
- Reassess these candidates after onboarding, receipt-processing quality, price-observation coverage, and operational reliability are measured.

## V1 boundary — what ships first

- **Peer-powered evidence:** Receipt or qualifying completed-online-purchase document required; guest receipt previews before registration; confirmed, consent-permitted purchases generate peer price observations.
- **Same-store matching only:** Identical verified product, merchant, physical store or regional online storefront, channel, unit basis, and currency. Online store pickup is evaluated as an online purchase.
- **Monitoring:** Verified merchant policy determines the adjustment window. Where unknown, use a **provisional 30-day window from the original transaction** and mark observations **informational / eligibility unverified**. Late uploaded receipts backfill eligible historical peer observations; expired purchases stop active matching.
- **Customer assistance:** Lower-price alerts and historical price charts; editable claim drafts **only for verified merchant policies**, subject to usual caveats. Unknown-policy alerts **do not create claim drafts**.
- **Privacy and reliability:** Consent choice before peer contribution; private source evidence; customer stops individual purchase monitoring; administrators execute data-deletion requests; baseline correctness, deduplication, security and auditability remain mandatory.
- **English UI in V1**, while data handling is designed for multiple regions, currencies and time zones.

## Deferred use cases — 21 catalogued V2 candidates

Each entry describes the future capability, why it was deferred, the **V1 behavior/limitation**, and the likely **dependencies for reconsideration**.

### A. Advanced receipt processing, returns and price evidence (6)

#### UC-018 — Advanced handling of unidentified products
- **Future capability:** Resolve ambiguous or missing product identifiers and hard-to-match descriptions.
- **Why deferred:** Low-confidence product identity can generate false cross-product price-drop alerts.
- **V1 behavior:** Match only products with verified identifiers/mappings; other receipt lines remain unsupported and unmonitored, while valid sibling items proceed.
- **Dependencies:** Better product catalogue coverage, exception review UX, verified matching strategy, and measurement of unsupported-item rates.

#### UC-021 — Returns and refunds processing
- **Future capability:** Partial returns, quantity adjustments, refund receipts, and refund-aware eligible quantities.
- **Why deferred:** Returns introduce additional documents, financial corrections and linked transaction state.
- **V1 behavior:** Customer may stop monitoring an **individual returned item** via UC-010; this does not delete purchase history or automatically reconcile partial refunds.
- **Dependencies:** Return-event and quantity model, evidence ingestion, policy semantics, recalculation of existing opportunities and claims.

#### UC-063 — Complex promotional and unusual-quantity pricing
- **Future capability:** Multi-buy offers, weighted/unusual units, coupons, loyalty discounts and sophisticated discount allocation.
- **Why deferred:** Ambiguous per-unit prices risk inaccurate comparisons.
- **V1 behavior:** Normalize straightforward quantities and unambiguous discounts only; exclude uncertain promotional lines from automatic price matching.
- **Dependencies:** Structured promotion extraction, comparable-unit rules, discount allocation, merchant exclusions and test cases.

#### UC-065 — Advanced price-evidence assessment
- **Future capability:** Evaluate complex evidence restrictions, membership-only prices, one-time promotions, exclusions and proof quality.
- **Why deferred:** Policy-specific evidence interpretation greatly increases the rules and review surface.
- **V1 behavior:** Use basic documented, comparable peer observations. Label them as **historical transactions**, not verified live offers; avoid claim guarantees.
- **Dependencies:** Richer observation metadata, merchant policy extensions, evidence quality model and review tools.

#### UC-066 — Advanced price-observation validation and fraud detection
- **Future capability:** Detect coordinated fake receipts, anomalous pricing patterns, repeat offenders and other abuse.
- **Why deferred:** A comprehensive trust/fraud scoring system is outside the core initial discovery workflow.
- **V1 behavior:** **Keep** malware/file validation, duplicate detection, plausible field checks, verified product matching and basic admin invalidation (UC-044); do not publish unsupported or invalid observations.
- **Dependencies:** Abuse signals, moderation workflow, evaluation datasets, monitoring metrics and false-positive review.

#### UC-067 — Advanced online purchase document handling
- **Future capability:** Parse a wide variety of complex online order, shipment, fulfillment and invoice formats.
- **Why deferred:** Retailer-specific document formats multiply extraction and qualification logic.
- **V1 behavior:** **Still accept** a qualifying document proving a completed online purchase under UC-005; users can review and correct straightforward extraction. Cart screenshots and unconfirmed orders are not sufficient.
- **Dependencies:** Source-specific parsers, completed-purchase verification criteria, evidence lifecycle rules and regression fixtures.

### B. Advanced customer controls and administration (4)

#### UC-038 — Formal reporting and investigation of incorrect opportunities
- **Future capability:** Customer reports with categories, triage queues, resolutions and investigation history.
- **Why deferred:** Full case management is disproportionate to the first release.
- **V1 behavior:** Customers can dismiss or mark alerts not applicable; administrators can invalidate incorrect observations (UC-044).
- **Dependencies:** Report taxonomy, admin review workflow, feedback aggregation and traceable resolution actions.

#### UC-045 — Suspend or block user accounts
- **Future capability:** Administrator moderation actions with rationale and suspension periods.
- **Why deferred:** Extensive user-moderation tooling is not a required customer feature for first release.
- **V1 behavior:** No dedicated suspension/block UI or use case; **baseline authentication security, access controls and guest abuse protections remain required**.
- **Dependencies:** Account state transitions, enforcement policies, administrator authorization, notices and audit review.

#### UC-046 — Reinstate users
- **Future capability:** Administrator reinstatement of previously suspended accounts.
- **Why deferred:** Depends on UC-045 and related review/appeal policy.
- **V1 behavior:** No reinstatement workflow.
- **Dependencies:** UC-045, reinstatement authorization, audit history and session reactivation safeguards.

#### UC-049 — Advanced notification-template management
- **Future capability:** Administrator-editable templates, approval workflows, versioning and potentially multiple channels.
- **Why deferred:** V1 has few stable notification types and no need for a full template editor.
- **V1 behavior:** Fixed, tested English email/in-app templates; user has basic email preferences (UC-073).
- **Dependencies:** Template storage and preview, publishing/rollback, localization strategy and test coverage.

### C. Additional price sources, integrations and automation (9)

#### UC-052 — Connect a merchant account
- **Future capability:** Let customers authorize access to merchant accounts where a supported integration exists.
- **Why deferred:** Account linking, permissions and external-provider dependencies add risk.
- **V1 behavior:** No merchant account connection; users upload documented purchases.
- **Dependencies:** Authorized integrations, secure token handling, consent/revocation and mapping to purchases.

#### UC-053 — Automatically import merchant orders
- **Future capability:** Pull eligible orders through connected merchant accounts.
- **Why deferred:** Requires reliable upstream account access, order state interpretation and deduplication.
- **V1 behavior:** Manual documented receipt upload.
- **Dependencies:** UC-052 or equivalent authorized integration, import reconciliation, fulfillment/purchase dating, and consent.

#### UC-054 — Collect online prices
- **Future capability:** Source public online prices through permitted automated collection.
- **Why deferred:** V1 deliberately relies on actual peer transactions rather than advertised/live prices.
- **V1 behavior:** No scraping; historical peer receipts are the only observation source.
- **Dependencies:** Source permission/legal review, collection cadence, data provenance, validity rules and merchant location/channel mapping.

#### UC-055 — Upload store shelf-price photographs
- **Future capability:** Extract in-store advertised shelf prices from user photos.
- **Why deferred:** Shelf prices are not the same kind of evidence as completed transactions and may be short-lived or mislabeled.
- **V1 behavior:** No shelf-label submissions; documented purchases only.
- **Dependencies:** OCR/photo review, store/time validation, price provenance, anti-abuse and eligibility classification.

#### UC-056 — Upload merchant price lists
- **Future capability:** Import structured CSV/Excel merchant price lists.
- **Why deferred:** Price lists vary in format, freshness, store coverage and contractual access.
- **V1 behavior:** No price-list import.
- **Dependencies:** Schema/mapping contracts, merchant/store identifiers, effective-date handling and import quality controls.

#### UC-057 — Submit prices manually without a purchase
- **Future capability:** Community-submitted prices without purchase receipts.
- **Why deferred:** Lacks the documented transaction evidence fundamental to V1.
- **V1 behavior:** Customers can **correct extraction fields on an uploaded receipt**, but cannot create unsupported purchase/price observations.
- **Dependencies:** New observation provenance class, verification/moderation, expiry and anti-abuse rules.

#### UC-058 — Verify crowdsourced prices
- **Future capability:** Dedicated corroboration and verification process for non-transaction/community price claims.
- **Why deferred:** Associated with broader user-generated price sources outside V1.
- **V1 behavior:** Confirmed, consent-permitted receipt observations and baseline validation only.
- **Dependencies:** UC-055/057 or other added sources, verification evidence, confidence scores and review operations.

#### UC-059 — Import purchases from email
- **Future capability:** User-authorized ingestion of emailed receipts/order confirmations.
- **Why deferred:** Mailbox permissions, filtering, and sensitive-content processing expand scope.
- **V1 behavior:** Customer manually uploads a qualifying receipt or completed-order document.
- **Dependencies:** Narrow mailbox authorization, revocation, secure data minimization, attachment parsing and duplicate reconciliation.

#### UC-060 — Submit adjustment claims automatically
- **Future capability:** Initiate qualifying retailer claims on the customer's behalf.
- **Why deferred:** Merchants have varied processes and authorization/proof requirements; automation could imply an unavailable entitlement.
- **V1 behavior:** **Verified-policy** lower-price findings may generate an **editable draft** the customer submits manually. **Unverified-policy** findings send **informational alerts only, with no draft**.
- **Dependencies:** Merchant-specific channels, consent/authorization, proof handling, status reconciliation and failure recovery.

### D. Notification preferences and localization (2)

#### UC-068 — Advanced notification thresholds
- **Future capability:** Minimum-savings alerts, custom frequency, bundling and richer notification controls.
- **Why deferred:** Basic timely notification is sufficient to validate product value.
- **V1 behavior:** Price alerts by email and in-app; basic email preference on/off (UC-073), alert deduplication and suppression of non-improving observations.
- **Dependencies:** Preference model extensions, notification grouping/rate limiting and user research.

#### UC-069 — Additional language localization
- **Future capability:** Localized interfaces, templates, accessibility copy and potentially regional content variants beyond English.
- **Why deferred:** Keeps the initial content and QA surface manageable.
- **V1 behavior:** **English** UI/messages, but currency, transaction timestamps, time zone and region remain accurately modeled; do not convert currencies for eligibility.
- **Dependencies:** i18n framework, translations, locale QA, content review and jurisdiction-specific requirements.

## Deferred extensions to existing V1 use cases (no new IDs)

These are **future expansions of V1 use cases**, not extra entries in the 21 deferred-ID count.

### Cross-store and cross-channel comparisons — UC-026 / UC-028 extension
- **Future capability:** Compare different physical stores or online/in-store channel pairs when the merchant's verified rules allow it, including directionality and geographic boundaries.
- **Why deferred:** Requires complex merchant rules and can produce false-positive refund guidance.
- **V1 behavior:** Exact same physical store or regional online storefront **and** same purchase channel; no cross-location eligibility alerts.
- **Dependencies:** Versioned merchant channel-pair and location-scope policies, store equivalence rules, evidence comparability, product mapping and matching tests.

### Richer merchant promotion rules — UC-028 / UC-041 extension
- **Future capability:** Evaluate detailed promotion, membership, clearance and category exclusions.
- **Why deferred:** Merchant policy details are difficult to model and maintain consistently at launch.
- **V1 behavior:** Basic policy window and simple exclusions; uncertain promotion evidence is excluded rather than assumed eligible.
- **Dependencies:** Merchant-specific rule catalogue, policy-source tracking, versioned evaluator and acceptance fixtures.

## Proposed review order (not a release commitment)

1. **Strengthen data quality:** Product identity (UC-018), advanced validation (UC-066) and promotional pricing (UC-063).
2. **Expand matching coverage:** Cross-store/channel rules after enough merchant policy evidence exists.
3. **Add more trusted data sources:** Authorized imports (UC-052–053/059) and other price sources (UC-054–058) only after provenance/privacy controls are ready.
4. **Improve customer workflows:** Returns (UC-021), incorrect-alert reporting (UC-038), notification controls (UC-068), localization (UC-069) and optional claim automation (UC-060).
5. **Expand operations where justified:** Account moderation (UC-045–046), template editing (UC-049).

## Release decision guardrails

- Do not move an item into V1 solely because it appears in this roadmap; update the requirements baseline explicitly.
- New price-source types need explicit provenance, verification and eligibility distinctions from receipt-backed peer prices.
- A historical lower transaction price is **not** evidence of a current retailer offer or guaranteed refund.
- Any change to privacy/consent or data retention requires explicit review.
- Consider operational cost, false-alert rate, customer usefulness and onboarding impact before prioritizing V2 candidates.

## Traceability

- **21 deferred use-case IDs:** UC-018, UC-021, UC-038, UC-045, UC-046, UC-049, UC-052–060, UC-063, UC-065–069.
- **2 merged IDs, not independent features:** UC-071 → UC-064 (unknown policy, V1); UC-072 → UC-010 (stop monitoring, V1).
- **Additional future extensions:** UC-026/028 cross-location and cross-channel comparability; UC-028/041 detailed merchant restrictions.
- **Authority for V1 behavior:** [V1.3 Functional & Technical Specification](requirements/functional-technical-spec-v1.3.md).
