# Delivery Tasks and Dependencies

Tasks are candidate delivery activities linked to user stories and acceptance criteria. They describe work to enable and verify the user-valued behavior; they do not prescribe a particular architecture or technology. Split or reassign them during team planning. No estimates or owners are assumed.

## EP-01 — Discover and select a product

| Task | Story | Task description | Depends on |
|---|---|---|---|
| T-001 | US-01 | Confirm category/product fields and catalogue source; implement category listing with configured product summary fields. | Catalogue contract confirmed |
| T-002 | US-01 | Add empty-category behavior and verify category membership, displayed fields, and unrelated-product exclusion. | T-001 |
| T-003 | US-02 | Confirm search matching behavior and supported filter facets; implement query and refinement behavior. | Catalogue/search behavior confirmed |
| T-004 | US-02 | Add no-results/change-or-clear-refinement behavior; test matching, filtered, and empty result sets. | T-003 |
| T-005 | US-03 | Define the product detail data contract and implement product details, options, price, and availability presentation. | Catalogue contract confirmed |
| T-006 | US-03 | Handle invalid or unavailable product identifiers; test that unavailable products cannot be added. | T-005 |
| T-007 | US-04 | Implement option/quantity validation and selected product-option state for add-to-cart. | Option model and quantity rules confirmed |
| T-008 | US-04 | Test missing, invalid, unavailable, and valid option selections against AC-10–AC-12. | T-007 |

## EP-02 — Prepare and review the cart and delivery

| Task | Story | Task description | Depends on |
|---|---|---|---|
| T-009 | US-05 | Implement add-to-cart for valid available product/option/quantity and expose the resulting cart line. | T-007; cart behavior confirmed |
| T-010 | US-05 | Implement and test unavailable-item rejection and the agreed duplicate-line/quantity-merge behavior. | T-009; duplicate-line policy confirmed |
| T-011 | US-06 | Implement cart quantity updates, removals, and recalculation using current configured prices. | T-009; price/quantity rules confirmed |
| T-012 | US-06 | Implement invalid/excess-quantity feedback and test cart update, removal, and total recalculation. | T-011; quantity limits confirmed |
| T-013 | US-07 | Implement cart display for current product, option, quantity, unit price, line total, and availability. | T-009; catalogue/stock source confirmed |
| T-014 | US-07 | Implement revalidation and shopper acknowledgement when price or availability changes; test subtotal and rounding. | T-013; revalidation and monetary rules confirmed |
| T-015 | US-08 | Confirm required contact/delivery fields and validation rules; implement checkout data entry and validation. | Checkout policy and field rules confirmed |
| T-016 | US-08 | Preserve valid entered values after correction and test valid, missing, and invalid submissions. | T-015 |
| T-017 | US-09 | Confirm delivery eligibility, available options, charges, estimates, and no-service behavior; implement option presentation. | Delivery rules/source confirmed |
| T-018 | US-09 | Persist selected option, update order total, and test available and unavailable destinations. | T-017; monetary rules confirmed |
| T-019 | US-10 | Implement order review showing cart, delivery, discounts, charges, and pending/unresolved amounts. | T-014; T-018; charge/tax rules confirmed |
| T-020 | US-10 | Implement change detection and explicit acknowledgement; test total calculation and no submission before confirmation. | T-019 |

## EP-03 — Pay for and confirm the order

| Task | Story | Task description | Depends on |
|---|---|---|---|
| T-021 | US-11 | Confirm supported payment methods and availability rules; implement payment-method listing and selection. | Payment provider/methods confirmed |
| T-022 | US-11 | Test available method selection and the no-method checkout-blocking behavior. | T-021 |
| T-023 | US-12 | Confirm order/payment state transitions and provider result contract; implement submission for a shopper-confirmed order. | T-020; T-021; payment/order rules confirmed |
| T-024 | US-12 | Implement distinct success, decline/failure, pending, unknown, and timeout outcome handling. | T-023 |
| T-025 | US-12 | Add the agreed duplicate-submission/payment protection; test retry and repeated submission scenarios. | T-023; retry/idempotency policy confirmed |
| T-026 | US-12 | Verify payment is not initiated without explicit order confirmation and test all result paths. | T-024; T-025 |
| T-027 | US-13 | Implement successful result page with matching order reference, status, and submitted-order summary. | T-023 |
| T-028 | US-13 | Implement configured confirmation notification and test one notification with matching order reference. | T-027; channel/delivery policy confirmed |
| T-029 | US-13 | Implement retrieval of the existing order result and test refresh/revisit status consistency. | T-027 |

## Sequencing notes

- Tasks within a story can be parallelized only when their stated prerequisites and shared interfaces are agreed.
- Catalogue, inventory, delivery, payment, and monetary rules are external dependencies until ownership and contracts are confirmed.
- Tasks that implement a policy-dependent behavior are blocked until that decision is recorded; do not replace the missing decision with an implementation assumption.
- End-to-end acceptance testing should cover at minimum: successful purchase; no results; unavailable product; cart price/availability change; invalid checkout details; no delivery option; payment failure; pending/unknown payment; and repeat submission.
