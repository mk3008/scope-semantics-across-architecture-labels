# Business Rule timeline

| id | rule text | source | first observed | activities | tables | status | implementation locations |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BR-001 | A Quotation has at most one source Order and an Order has zero or one source Quotation; `customer_order.quotation_id` is canonical. | human decision + amended DDL | Stage 1 resolution | quotation/order creation | quotation, customer_order | active | pending implementation |
| BR-004 | New Quotation expires_at is strictly future; an open quotation is business-expired at now >= expires_at. | human decision | Stage 1 resolution | quotation creation/search | quotation | active | pending implementation |
| BR-005 | Quotation creation requires at least one line. | human decision | Stage 1 resolution | quotation creation | quotation_line | active | pending implementation |
| BR-002 | Quotation-originated Order lines are a snapshot and later Quotation changes do not change that Order. | explicit requirement | Stage 2 | quotation revision, order creation | quotation_line, order_line | pending | pending implementation |
| BR-003 | An Order at or above 1000.00 needs manager approval before confirmation. | explicit requirement | Stage 3 | approval, confirmation | customer_order, order_approval | pending | pending implementation |
