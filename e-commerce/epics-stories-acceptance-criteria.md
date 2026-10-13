# Epics, Features, User Stories, and Acceptance Criteria

All items below are candidate backlog content derived from the shopper-purchase journey. Each feature groups related user-valued behavior; stories are delivery-sized actor needs; acceptance criteria define verifiable outcomes. Confirm business rules and scope with the client before implementation.

## EP-01 — Discover and select a product

**Outcome:** A shopper can find a relevant product, understand its available choices, and select an item to purchase.

### FEAT-01 — Product discovery

**Description:** Let shoppers browse and find products using the catalogue information and discovery options supported by the store.

#### US-01 — Browse the catalogue

As a shopper, I want to browse product categories so that I can discover products available in the store.

**Acceptance criteria**

- **AC-01:** Given the catalogue contains products assigned to a category, when the shopper opens that category, then the system displays only products assigned to it.
- **AC-02:** Given a displayed product has catalogue details available, when it appears in a category listing, then the listing shows its configured name, price, and availability indicator.
- **AC-03:** Given a category has no products available to display, when the shopper opens it, then the system displays an empty-category message and does not show unrelated products.

#### US-02 — Search and refine products

As a shopper, I want to search and refine the product list so that I can find products matching my needs.

**Acceptance criteria**

- **AC-04:** Given products match the submitted search query, when the shopper searches, then every returned product matches the configured search behavior for that query.
- **AC-05:** Given one or more supported filters are available, when the shopper applies a filter, then every displayed product matches the applied filter values.
- **AC-06:** Given no products match the query and selected filters, when results are displayed, then the system shows a no-results state and provides a way to change or clear the search/refinement.

### FEAT-02 — Review product details and select an option

**Description:** Let shoppers inspect a product and choose an available variant or option before adding it to the cart.

#### US-03 — Review product details

As a shopper, I want to view a product’s details so that I can decide whether it meets my needs.

**Acceptance criteria**

- **AC-07:** Given a product exists in the catalogue, when the shopper opens it, then the system displays its configured name, description, price, images (if supplied), available options, and availability.
- **AC-08:** Given a product has selectable options, when the detail page is displayed, then each option’s current availability is distinguishable from unavailable options.
- **AC-09:** Given the product identifier is invalid or the product is no longer available, when the shopper opens its detail page, then the system communicates that it cannot be purchased and does not offer an add-to-cart action for it.

#### US-04 — Select product options

As a shopper, I want to select an available product option and quantity so that the cart reflects the item I intend to buy.

**Acceptance criteria**

- **AC-10:** Given a product requires an option choice, when the shopper attempts to add it without selecting a valid available option, then the system identifies the missing or invalid choice and does not add the item.
- **AC-11:** Given the shopper selects a valid available option and a quantity accepted by configured rules, when the shopper adds it to the cart, then the cart line records that product, option, and quantity.
- **AC-12:** Given an option is unavailable, when the shopper attempts to select or add it, then the system indicates it is unavailable and does not add that option to the cart.

## EP-02 — Prepare and review the cart and delivery

**Outcome:** A shopper can manage the intended purchase, provide checkout details, select an available delivery option, and review the order before submission.

### FEAT-03 — Manage and validate the cart

**Description:** Let shoppers review items, change quantities, remove items, and see relevant availability or price changes.

#### US-05 — Add a product to the cart

As a shopper, I want to add a selected product to my cart so that I can purchase it.

**Acceptance criteria**

- **AC-13:** Given a product and any required option are available, when the shopper adds a valid quantity, then the cart contains a line for the selected product/option and quantity.
- **AC-14:** Given a product or option is unavailable at the time the add request is validated, when the shopper adds it, then the system does not add it and explains that it is unavailable.
- **AC-15:** Given the shopper adds an item already in the cart with the same product and option, when the configured cart behavior is applied, then the cart reflects that behavior consistently and displays the resulting quantity. **Client decision:** merge matching lines or keep separate lines.

#### US-06 — Change or remove cart items

As a shopper, I want to change quantities or remove items so that my cart contains the products I intend to order.

**Acceptance criteria**

- **AC-16:** Given a cart line exists, when the shopper changes its quantity to a valid value, then the displayed cart quantity and line total reflect the updated quantity and current configured price.
- **AC-17:** Given a cart line exists, when the shopper removes it, then it no longer appears in the cart and the cart total is recalculated.
- **AC-18:** Given a requested quantity is invalid or exceeds a configured limit, when the shopper applies it, then the system does not silently accept it and identifies the quantity issue.

#### US-07 — Review current cart prices and availability

As a shopper, I want to see current prices and item availability in my cart so that I can review changes before checkout.

**Acceptance criteria**

- **AC-19:** Given the cart contains items, when the shopper views it, then each line displays the product/option, quantity, current configured unit price, line total, and availability status.
- **AC-20:** Given an item’s price or availability has changed since it was added, when the cart is revalidated, then the system shows the changed value/status and requires the shopper to review the affected item before order submission.
- **AC-21:** Given displayed prices and quantities are valid, when the cart total is calculated, then the subtotal equals the sum of displayed line totals using the configured currency and rounding rules.

### FEAT-04 — Provide checkout and delivery details

**Description:** Collect the contact and delivery information required by the agreed checkout process, then present delivery options available for those details.

#### US-08 — Provide contact and delivery information

As a shopper, I want to enter my contact and delivery details so that the store can process and deliver my order.

**Acceptance criteria**

- **AC-22:** Given checkout requires specified contact and delivery fields, when the shopper submits the form with all required fields valid, then the system accepts the details for the checkout.
- **AC-23:** Given a required field is missing or a value fails its configured validation, when the shopper submits the form, then the system identifies the field(s) requiring correction and does not proceed to order review.
- **AC-24:** Given the shopper corrects invalid fields, when the shopper resubmits valid details, then the system retains the corrected values and proceeds without requiring unrelated fields to be re-entered.

#### US-09 — Choose an available delivery option

As a shopper, I want to choose a delivery option available for my address so that I know how my order will be delivered.

**Acceptance criteria**

- **AC-25:** Given delivery options are available for the entered delivery details, when the options are displayed, then each option shows its configured name, charge, and delivery estimate when supplied.
- **AC-26:** Given the shopper selects an available delivery option, when the selection is saved, then checkout records that option and includes its configured charge in the order total.
- **AC-27:** Given no delivery option is available for the entered details, when the system checks delivery availability, then it explains that delivery is unavailable and prevents submission until the shopper changes the details or an agreed alternative is selected.

### FEAT-05 — Review the order before submission

**Description:** Present the selected items, delivery choice, and known charges so the shopper can confirm the order they are about to submit.

#### US-10 — Review the order total

As a shopper, I want to review my items and total before submitting my order so that I can confirm the purchase details.

**Acceptance criteria**

- **AC-28:** Given checkout has valid cart and delivery details, when the shopper opens order review, then the system displays each product/option and quantity, item subtotal, selected delivery option and charge, and all other configured charges or discounts.
- **AC-29:** Given the review displays component amounts, when the total is calculated, then it equals those displayed amounts using configured currency and rounding rules; the system labels any amount not yet determined as pending rather than presenting an incomplete amount as final.
- **AC-30:** Given a required review item changes before submission, when the system detects the change, then it updates the review and requires the shopper to acknowledge the changed details before proceeding.
- **AC-31:** Given the shopper has not confirmed the displayed order, when the order review is shown, then no order is submitted.

## EP-03 — Pay for and confirm the order

**Outcome:** A shopper can use an agreed payment method to submit an order and receive an accurate outcome.

### FEAT-06 — Select payment and submit an order

**Description:** Let the shopper select a supported payment method and submit the reviewed order, handling successful, failed, or unresolved payment outcomes accurately.

#### US-11 — Select a supported payment method

As a shopper, I want to choose an available payment method so that I can pay for my order using an accepted option.

**Acceptance criteria**

- **AC-32:** Given one or more payment methods are configured and available for the order, when the shopper reaches payment selection, then the system lists only those available methods.
- **AC-33:** Given the shopper selects a listed method, when the selection is saved, then the selected method is associated with the current checkout.
- **AC-34:** Given no payment method is available, when the shopper reaches payment selection, then the system explains that checkout cannot proceed and does not show an order as paid or confirmed.

#### US-12 — Submit an order and handle payment outcome

As a shopper, I want to submit my reviewed order for payment so that the store can process my purchase.

**Acceptance criteria**

- **AC-35:** Given the cart, required checkout details, delivery option, payment method, and shopper confirmation are valid, when the payment provider reports success, then the system records the agreed successful order/payment state and provides the order reference.
- **AC-36:** Given payment is declined or the provider reports failure, when the result is received, then the system does not show a successful payment or confirmed order and explains the failure with an allowed next step.
- **AC-37:** Given the payment result is pending, unknown, or times out, when the system cannot confirm success, then it communicates the unresolved status and does not tell the shopper that payment succeeded.
- **AC-38:** Given the shopper retries after an uncertain response, when the same checkout submission is retried, then the system follows the agreed duplicate-submission/payment protection rule and does not create duplicate successful orders for the same submission.
- **AC-39:** Given the shopper has not confirmed the reviewed order, when a payment submission is attempted, then the system rejects the submission and does not initiate payment.

### FEAT-07 — Confirm the purchase outcome

**Description:** Give the shopper an accurate, usable result after order submission.

#### US-13 — Receive an order result

As a shopper, I want to see the result of my order submission so that I know whether it was placed and what to do next.

**Acceptance criteria**

- **AC-40:** Given the system has confirmed successful order placement, when the result is displayed, then it includes the order reference, confirmed status, and a summary matching the submitted order.
- **AC-41:** Given the order is not confirmed, when the result is displayed, then it does not use success wording or provide a false confirmation reference.
- **AC-42:** Given an order confirmation channel is configured and required, when successful placement is confirmed, then the system sends one confirmation for that order to the shopper’s validated destination and the message’s order reference matches the displayed reference.
- **AC-43:** Given the shopper refreshes or revisits the result for an existing order, when the system retrieves its current state, then the displayed order reference and status match the stored order state.

## Cross-cutting acceptance checks

- Criteria involving a configurable business rule are testable only after that rule is agreed and recorded.
- Monetary calculations must use the agreed currency, precision, and rounding policy; do not infer tax or fee rules from this backlog.
- Each negative or pending outcome must be distinguishable from successful order placement.
- Validate all main and alternate journey paths in [the traceability matrix](./traceability.md); out-of-scope exceptions must be explicitly recorded rather than silently omitted.
