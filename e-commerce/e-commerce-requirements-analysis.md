# E-commerce Website — Initial Requirements Analysis

## 1. Requirement and status

**Raw requirement:** “Build an e-commerce website.”

**Business objective (proposal):** Enable customers to discover products, place and pay for orders online, and receive their purchases, while enabling the business to manage the activities needed to sell and fulfill those orders.

This is a broad solution request, not yet a complete or testable set of requirements. The business model, launch scope, policies, actors, integrations, and success measures are unknown. The capabilities and journeys below are **proposals for client validation**, not confirmed requirements.

### EPC source and limitation

No Event-driven Process Chain (EPC) diagram was provided. Therefore, this document cannot claim that the listed functions or features were derived from an EPC. They are a provisional process-based breakdown of a typical online purchase and order-fulfillment lifecycle.

When the client provides an EPC, map its events, functions, organizational roles, connectors/decisions, and hand-offs to the proposed system responsibilities. Confirm which business functions belong in the website and preserve relevant branches and exceptions. Do not assume every function shown in a business process is automated by the system.

## 2. Feature, user story, and use case

These artifacts describe related but different levels of requirement:

| Artifact | What it describes | Example |
|---|---|---|
| **Feature** | A cohesive solution capability that delivers stakeholder value and groups related requirements. A feature may be delivered through multiple stories. | **Product discovery:** shoppers can browse and search the product catalogue and inspect product details. |
| **User story** | A small, actor-centered backlog item that states a need and its value. It should be independently understandable and testable, with acceptance criteria added during refinement. | “As a shopper, I want to filter products by size so that I can find products that meet my needs.” |
| **Use case** | An actor-goal interaction with a trigger, preconditions as needed, a main success flow, alternative/exception flows, and outcomes. It describes behavior across a goal, not necessarily a single sprint-sized increment. | **Find products:** shopper searches or browses; the system displays matching products, supports refinement, and handles no results. |

In short: **features organize capabilities; user stories describe valuable increments; use cases describe interactions and their paths.** They are complementary and should not be used as interchangeable labels.

### Example use case: Place an order

- **Primary actor:** Shopper
- **Goal:** Submit an order for selected products.
- **Trigger:** Shopper chooses to proceed from the cart to checkout.
- **Preconditions:** The cart contains at least one item; item availability and applicable checkout rules can be checked.
- **Main success flow:**
  1. The shopper reviews the cart and proceeds to checkout.
  2. The system collects the required contact and delivery information.
  3. The shopper selects an available delivery option and payment method.
  4. The system presents the order total and obtains the shopper’s confirmation.
  5. The system processes the payment and creates the order.
  6. The system shows an order confirmation and sends the applicable notification.
- **Alternative/exception flows to clarify:**
  - An item becomes unavailable or its price changes before submission; the system explains the change and asks the shopper to review the cart.
  - Payment is declined, interrupted, or times out; the system reports the outcome and allows an appropriate retry or alternative.
  - The address is invalid or delivery is unavailable; the shopper corrects the details or chooses another available option.
  - The shopper abandons checkout; the system retains or expires the cart according to a policy to be agreed.
- **Postcondition on success:** An order exists with a recorded payment outcome and confirmation available to the shopper.
- **Postcondition on failure or cancellation:** No misleading success confirmation is shown; the final order and payment state follows the agreed payment and order rules.

Payment timing, inventory reservation, cart retention, and what constitutes a successful order are open business decisions—not assumptions established by this example.

## 3. Provisional function and feature catalogue

The functions below are candidate system responsibilities grouped into features. They are not EPC-derived until compared with an actual client EPC. Confirm whether each is in scope, who performs it, and which existing system—if any—is authoritative.

| Candidate feature | Candidate business/system functions | Likely actors | Status / questions to resolve |
|---|---|---|---|
| **Product catalogue and discovery** | Maintain product information; organize categories; browse and search; filter and sort results; display product details, options/variants, price, and availability. | Shopper; catalogue manager | Proposal. Confirm product types, catalogue owner, variants, search needs, and source of prices/stock. |
| **Cart and checkout** | Add, update, and remove cart items; validate availability and price; collect contact and delivery details; calculate totals; apply eligible promotions; review and submit an order. | Shopper | Proposal. Confirm guest checkout, cart persistence, promotion rules, and order-submission rules. |
| **Payment and refunds** | Present supported payment methods; initiate and record payment outcomes; handle payment failure; support refunds where in scope. | Shopper; finance/customer-service staff | Proposal. Confirm providers, methods, currencies, payment timing, refund policy, and ownership of payment records. |
| **Order management** | Create and update orders; review order details; progress orders through agreed statuses; support cancellation or correction where policy permits. | Shopper; order-management staff | Proposal. Confirm lifecycle, cancellation window, roles, and source of truth. |
| **Fulfillment and delivery** | Allocate or prepare items; hand orders to a fulfillment party; select delivery service; provide tracking/status updates; handle delivery exceptions. | Fulfillment staff/partner; shopper | Proposal. Confirm who fulfills, service areas, delivery options, tracking, and exception handling. |
| **Customer account and service** | Register/sign in where required; manage profile and addresses; view order history; request help, cancellation, return, or exchange if supported. | Shopper; customer-service staff | Proposal. Confirm account requirements, support channels, identity/security needs, and service policies. |
| **Returns and after-sales** | Receive a return or exchange request; determine eligibility; communicate next steps; record receipt and refund/replacement outcome. | Shopper; customer-service/returns staff | Proposal. Confirm eligible items, deadlines, conditions, workflow, and refund handling. |
| **Store administration** | Manage catalogue content, prices, availability, promotions, orders, and staff access as authorized. | Store administrator; catalogue/order staff | Proposal. Confirm administrative roles, approval controls, audit needs, and which functions belong in this product. |
| **Notifications** | Send relevant order, payment, fulfillment, and service updates through agreed channels. | Shopper; staff | Proposal. Confirm events, channels, content ownership, preferences, and delivery expectations. |

### EPC traceability to complete with the client

For each process path in the supplied EPC, capture the source element and decide whether the website supports it:

| EPC event/function/decision and role | Candidate website function/feature | System responsibility or external hand-off | Requirement/question | Status |
|---|---|---|---|---|
| To be populated from client EPC | To be mapped and validated | To be agreed | To be captured | Question |

## 4. High-level user journeys

These are provisional target-state journeys. Alternate paths are included to guide clarification; they do not define policy or guarantee that a particular capability is in scope.

### A. Shopper purchases a product

1. Shopper opens the store and browses categories or searches.
2. Shopper refines results and opens a product to review its details, options, price, and availability.
3. Shopper selects an option/quantity and adds the item to the cart.
4. Shopper reviews the cart and proceeds as a guest or signed-in customer, depending on the agreed approach.
5. Shopper provides contact and delivery information and selects an available delivery option.
6. Shopper reviews the total, selects a payment method, and submits the order.
7. The system reports the outcome and, on success, provides confirmation and the agreed next steps.
8. Shopper follows order/ delivery status and contacts support or starts a return if applicable.

**Decision and alternate paths:** no search results; product unavailable; selected option changes availability; cart price/stock changes; promotion is invalid; delivery is unavailable; address validation fails; payment fails or is pending; shopper leaves checkout; order is delayed or delivery fails.

### B. Shopper tracks or gets help with an order

1. Shopper identifies an order through the agreed account or order-reference process.
2. Shopper reviews the current status and available next actions.
3. Shopper checks tracking or contacts support.
4. If policy and order state allow, shopper requests cancellation, return, or exchange.
5. System/staff confirms the request, communicates the outcome, and updates the order/service record.

**Decision and alternate paths:** order cannot be found; identity cannot be verified; cancellation/return is outside policy or too late; package has not yet shipped; support requires staff review.

### C. Store staff manages and fulfills an order

1. Authorized staff review new orders and their payment/validation state.
2. Staff or an integrated system confirms that items can be fulfilled.
3. Staff prepare the order and arrange dispatch or hand-off to the fulfillment partner.
4. The order status and tracking information are updated.
5. Staff handle an exception such as unavailable stock, failed hand-off, or delivery issue and communicate the agreed resolution.

**Decision and alternate paths:** payment requires review; stock is insufficient; order needs cancellation; fulfillment is split; delivery or integration fails. Confirm which steps are performed by staff, the website, or external systems.

## 5. Client clarification questions

Prioritize these in discovery. Answers should be recorded as confirmed requirements, constraints, assumptions, or remaining questions.

### Business objective and launch scope

1. What business outcome should the website achieve, and how will success be measured?
2. Is the business single-seller, multi-vendor marketplace, or another model? Who is the seller of record?
3. Which products, customer segments, sales regions, and languages are in the first release?
4. Which capabilities are essential for launch, and what is explicitly out of scope?

### Actors and access

5. Which customer types and internal/partner roles will use the solution?
6. Is guest checkout required, or must shoppers create an account?
7. What roles and permissions are needed for catalogue, order, fulfillment, finance, and support staff?

### Catalogue, price, and inventory

8. Who creates and maintains product information, images, categories, variants, prices, and availability?
9. Which system is authoritative for catalogue, pricing, and stock? How frequently must updates appear?
10. How should the system handle out-of-stock items, low stock, price changes, substitutions, or backorders?
11. Are promotions, coupons, bundles, memberships, or customer-specific prices required? What rules govern them?

### Checkout, payment, tax, and fraud

12. Which payment methods, providers, currencies, and payment timing are required?
13. What should happen after a declined, pending, duplicate, or interrupted payment?
14. Which party calculates tax, duties, fees, and the final order total? Which jurisdictions apply?
15. Are refunds, partial refunds, chargebacks, fraud screening, or manual payment review in scope? Who owns those processes?

### Fulfillment, delivery, and after-sales

16. Who stores, picks, packs, and ships orders? Are multiple warehouses, vendors, or fulfillment partners involved?
17. Which delivery regions, options, fees, time estimates, and tracking capabilities are required?
18. How should split shipments, delayed/lost deliveries, failed delivery attempts, and unavailable items be handled?
19. What are the cancellation, return, exchange, warranty, and refund policies, including eligibility and time limits?
20. Which customer-support channels and service expectations should be supported?

### Integrations, constraints, and operations

21. Which systems must integrate (for example, inventory/ERP, payment, tax, shipping, CRM, analytics, or identity), and which system owns each data item?
22. What security, privacy, accessibility, regulatory, data-retention, or audit requirements apply in the target regions?
23. What availability, performance, traffic-volume, recovery, and support expectations apply?
24. Who owns content, operational configuration, customer communications, and ongoing support?
25. Can the client provide current/target EPC diagrams, process policies, example exceptions, and responsible roles so the provisional catalogue and journeys can be traced and validated?

## 6. Recommended next steps

1. Confirm the business model, launch scope, target users, and success measures.
2. Obtain and review the relevant current-state and/or target-state EPC diagrams with business owners; fill the traceability table and validate system boundaries.
3. Agree policies and ownership for catalogue/stock, payment, order lifecycle, fulfillment, cancellations, returns, and support.
4. Convert confirmed capabilities into prioritized epics/features, actor-centered user stories, and use cases for complex or exception-heavy interactions.
5. Add measurable acceptance criteria and validate the journeys with business, operations, and customer stakeholders.

**Classification:** Candidate capabilities and journeys in this document are `proposal`; open client decisions are `question`. No business policy, integration, or EPC-derived requirement is treated as confirmed.
