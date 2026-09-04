# Business Rule timeline

| id | rule text | source | first observed | activities | tables | status | implementation locations |
| --- | --- | --- | --- | --- | --- | --- | --- |
| BR-001 | A Quotation has at most one Order and an Order has at most one Quotation. | DDL constraint | frozen | quotation/order creation | quotation, customer_order | active | pending implementation |
| BR-002 | Quotation-originated Order lines are a snapshot and later Quotation changes do not change that Order. | explicit requirement | Stage 2 | quotation revision, order creation | quotation_line, order_line | pending | pending implementation |
| BR-003 | An Order at or above 1000.00 needs manager approval before confirmation. | explicit requirement | Stage 3 | approval, confirmation | customer_order, order_approval | pending | pending implementation |
