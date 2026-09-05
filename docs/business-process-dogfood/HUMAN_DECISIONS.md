# Human decisions

## HD-001 — Stage 1 quotation expiry

New Quotation `expires_at` must be strictly later than now. An open Quotation is business-expired when `now >= expires_at`; expiry is determined by `expires_at`, not stale persisted `status`. Expired Quotations remain searchable/readable but are unusable for an operation that requires an active Quotation. No other expiry effects are inferred. Materializing `status = expired` is implementation choice. A terminal/business state is not retroactively reinterpreted solely by clock passage.

## HD-002 — Stage 1 quotation lines

Quotation creation requires at least one line. Duplicate product IDs are permitted; line order has no current business significance.

## HD-003 — identifiers and performer scope

`customer_id` and `product_id` are opaque identifiers from an already-authorized surrounding system. Empty/whitespace-only values are invalid; no normalization or master-data validation is added. Sales is already authenticated and authorized. No audit matrix/trail is required absent later requirement.

## HD-004 — search and result contract

Search needs only the smallest deterministic contract required by current acceptance and cumulative activities: exact search by modeled identifiers and deterministic ordering. Pagination, fuzzy search, formatting, DTO/transport shape are implementation choices, not Business Rules.

## HD-005 — Quotation eligibility for Order creation

Quotation-to-Order conversion requires `status = open`, `now < expires_at`, and no existing `customer_order` reference. Conversion neither revives nor extends expiry.

## HD-006 — Post-conversion Quotation state and association invariant

Conversion atomically creates one canonical `customer_order.quotation_id` reference, copies HD-009 data, and sets Quotation status to `ordered`. `quotation.status = ordered` iff an Order references it; open/expired Quotations have no associated Order. The operation must not be partly visible. No DDL amendment is authorized merely because this cross-table invariant is not a simple FK constraint.

## HD-007 — Quotation revision policy

Revision requires open status, future expiry, and no associated Order. Expired/ordered Quotations are read-only. Sales may change customer_id, expires_at, and lines but not quotation_id/status. Existing line, expiry, identifier, duplicate, and order decisions continue to apply.

## HD-008 — Order line cardinality

Every direct or sourced Order has at least one Order Line. Duplicate product IDs are allowed; Order Line order has no business significance.

## HD-009 — sourced Order snapshot projection

Copy Quotation customer_id to Order customer_id; set canonical source association; create draft Order; compute total from copied lines; copy product_id, quantity, unit_price. Do not copy Quotation expires_at/status. Later Quotation changes never change the Order/lines. No DDL amendment is required.

## HD-010 — Order approval separation of duties

`confirmOrder` is a Sales activity. An authorized Sales performer confirms an Order after all applicable approval requirements are satisfied. An authorized Sales performer may confirm an Order below the approval threshold without manager approval. The confirmer need not be the Sales individual who created the Order.

Approval/rejection is a manager activity. Manager identity and manager-role authorization are supplied by a trusted, already-authenticated surrounding boundary. `manager_id` must not be accepted as an arbitrary impersonatable value from an untrusted caller.

For an Order requiring manager approval, the manager who approves or rejects it must not be the same individual who created it. Role names alone are insufficient: a person with both Sales and manager roles may not decide an Order that person created; another authorized manager may.

Order creator identity is required Business Data. `customer_order.created_by` records the opaque external identifier supplied by trusted authenticated Sales actor context for direct Order creation and Quotation-to-Order creation. No identity/user master data is created.

`order_approval.manager_id` records the trusted manager who decided. Approval/rejection is rejected when it equals `customer_order.created_by`. Current requirements do not require persisted confirmer identity, a creator/confirmer relation, general audit history, or `confirmed_by`.
