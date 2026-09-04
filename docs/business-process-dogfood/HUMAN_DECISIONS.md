# Human decisions

## HD-001 — Stage 1 quotation expiry

New Quotation `expires_at` must be strictly later than now. An open Quotation is business-expired when `now >= expires_at`; expiry is determined by `expires_at`, not stale persisted `status`. Expired Quotations remain searchable/readable but are unusable for an operation that requires an active Quotation. No other expiry effects are inferred. Materializing `status = expired` is implementation choice. A terminal/business state is not retroactively reinterpreted solely by clock passage.

## HD-002 — Stage 1 quotation lines

Quotation creation requires at least one line. Duplicate product IDs are permitted; line order has no current business significance.

## HD-003 — identifiers and performer scope

`customer_id` and `product_id` are opaque identifiers from an already-authorized surrounding system. Empty/whitespace-only values are invalid; no normalization or master-data validation is added. Sales is already authenticated and authorized. No audit matrix/trail is required absent later requirement.

## HD-004 — search and result contract

Search needs only the smallest deterministic contract required by current acceptance and cumulative activities: exact search by modeled identifiers and deterministic ordering. Pagination, fuzzy search, formatting, DTO/transport shape are implementation choices, not Business Rules.
