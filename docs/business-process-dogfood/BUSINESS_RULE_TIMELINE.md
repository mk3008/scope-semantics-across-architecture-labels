# Business Rule timeline

| id | rule text | source | first observed | activities | tables | status | implementation locations |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BR-001 | A Quotation has at most one source Order and an Order has zero or one source Quotation; `customer_order.quotation_id` is canonical. | human decision + amended DDL | Stage 1 resolution | quotation/order creation | quotation, customer_order | active | amended DDL |
| BR-004 | New Quotation expires_at is strictly future; an open quotation is business-expired at now >= expires_at. | human decision | Stage 1 resolution | quotation creation/search | quotation | active | Stage 1 consistency-resolution `src/app.js` |
| BR-005 | Quotation creation requires at least one line. | human decision | Stage 1 resolution | quotation creation | quotation_line | active | Stage 1 consistency-resolution `src/app.js` |
| BR-006 | Conversion eligibility and atomic `ordered`/canonical-association invariant. | human decision | Stage 2 resolution | quotation revision, order creation | quotation, customer_order | active | pending Stage 2 resolution |
| BR-007 | Quotation revision is limited to open, unexpired, unassociated Quotation. | human decision | Stage 2 resolution | quotation revision | quotation, customer_order | active | pending Stage 2 resolution |
| BR-008 | Every Order has at least one line. | human decision | Stage 2 resolution | direct/sourced order creation | customer_order, order_line | active | pending Stage 2 resolution |
| BR-009 | Sourced Order snapshot projection has only HD-009 Order semantics. | human decision | Stage 2 resolution | quotation-to-order conversion | quotation, quotation_line, customer_order, order_line | active | pending Stage 2 resolution |
| BR-002 | Quotation-originated Order lines are a snapshot and later Quotation changes do not change that Order. | explicit requirement | Stage 2 | quotation revision, order creation | quotation_line, order_line | pending | pending implementation |
| BR-003 | An Order at or above 1000.00 needs manager approval before confirmation. | explicit requirement | Stage 3 | approval, confirmation | customer_order, order_approval | pending | pending implementation |
| BR-010 | A manager may not approve/reject an approval-required Order that the same individual created; creator identity is stored on the Order. | HD-010 | Stage 3 resolution | direct/sourced order creation, approval | customer_order, order_approval | active | pending Stage 3 resolution |
| BR-011 | Confirmation is a Sales activity; an Order at or above 1000.00 confirms only after valid manager approval, while lower-value Orders may confirm without approval. | Stage 3 packet + HD-010 | Stage 3 resolution | approval, confirmation | customer_order, order_approval | active | pending Stage 3 resolution |
