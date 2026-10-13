# Traceability Matrix and Open Decisions

## Traceability

Source objective: enable online selling and customer purchase journeys (proposal in the initial requirements analysis).

Source journey: **Shopper purchases a product**—discover/browse; review product; select option/quantity and add to cart; provide checkout details; select delivery and payment; review and submit order; receive outcome.

| Journey stage | Epic | Feature | Stories | Acceptance criteria |
|---|---|---|---|---|
| Browse categories and find products | EP-01 | FEAT-01 Product discovery | US-01, US-02 | AC-01–AC-06 |
| Review product details and options | EP-01 | FEAT-02 Product details and option selection | US-03, US-04 | AC-07–AC-12 |
| Add, review, and update cart | EP-02 | FEAT-03 Cart management and validation | US-05, US-06, US-07 | AC-13–AC-21 |
| Enter contact/delivery details and select delivery | EP-02 | FEAT-04 Checkout and delivery details | US-08, US-09 | AC-22–AC-27 |
| Review items and total | EP-02 | FEAT-05 Order review | US-10 | AC-28–AC-31 |
| Select payment and submit | EP-03 | FEAT-06 Payment and order submission | US-11, US-12 | AC-32–AC-39 |
| Receive result and confirmation | EP-03 | FEAT-07 Purchase outcome | US-13 | AC-40–AC-43 |

Task-level traceability is listed in [delivery tasks](./delivery-tasks.md), with each task linked to its story.

## Open decisions and readiness

The following items need client confirmation before the related criteria can be treated as final business rules:

| Decision | Related items | Why it matters |
|---|---|---|
| Single seller or marketplace; first-release product, region, language, and customer scope | EP-01–EP-03 | Defines catalogue, actors, sales rules, and release boundary. |
| Catalogue and inventory system of record; product fields, variants, and availability freshness | FEAT-01, FEAT-02, FEAT-03 | Defines displayed data, product eligibility, and revalidation behavior. |
| Search matching, supported filters, sorting, and category behavior | FEAT-01 | Needed to make search and refinement criteria precise. |
| Whether identical cart items merge or appear as separate lines; cart persistence; quantity limits | FEAT-03 | Determines update, retry, and cart calculation behavior. |
| Guest checkout, account requirements, required contact/address fields, and validation rules | FEAT-04 | Determines checkout entry paths and required data. |
| Delivery eligibility, methods, charges, estimates, and no-service alternatives | FEAT-04, FEAT-05 | Determines available selections and totals. |
| Currency, price/tax/fee/discount rules, precision, rounding, and when totals become final | FEAT-03, FEAT-05 | Required for correct and testable monetary calculations. |
| Supported payment methods/providers, payment timing, and authoritative payment result | FEAT-06 | Defines payment selection and order/payment state behavior. |
| Order creation/status rules for failed, pending, unknown, and timed-out payment outcomes | FEAT-06, FEAT-07 | Prevents false order confirmation and defines recovery behavior. |
| Retry, duplicate-submission, inventory reservation, and idempotency rules | FEAT-03, FEAT-06 | Prevents inconsistent inventory, duplicate orders, or duplicate charges. |
| Confirmation channels, notification timing, and shopper identity/destination validation | FEAT-07 | Defines whether notifications are required and verifiable. |
| Relevant EPC diagrams, roles, decisions, and process ownership | All epics/features | Required to validate process coverage and establish which EPC activities the website supports. |

## Status

- Epics, features, stories, and tasks: **proposed**.
- Acceptance criteria: **candidate test conditions**, ready for refinement after the decisions above are confirmed.
- EPC mapping: **not performed** because no EPC was provided.
- Priority, estimates, owners, and release placement: **not assigned**.
