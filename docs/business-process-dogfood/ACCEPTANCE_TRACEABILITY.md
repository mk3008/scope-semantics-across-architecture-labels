# Acceptance traceability

This ledger is introduced by Protocol Amendment 001. `Current test location` is the post-review repair suite for Stage 1+2; it is not evidence that the original runs were cumulative.

| requirement / decision | rule | first stage | status | current test location | note |
| --- | --- | --- | --- | --- | --- |
| Quotation creation; nonblank identifiers; future expiry | HD-003, BR-004 | 1 | active | `work/business-process-dogfood/frozen-tests/cumulative-stage2-repair.test.js` | includes invalid customer/product and NaN cases |
| Quotation has one or more lines; duplicate products allowed | HD-002, BR-005 | 1 | active | `cumulative-stage2-repair.test.js` | duplicate is accepted |
| Read/search expired quotation; exact deterministic search | HD-001, HD-004 | 1 | active | `cumulative-stage2-repair.test.js` | expiry is based on statement time |
| Revise only eligible quotation before conversion | HD-007 | 2 | active | `cumulative-stage2-repair.test.js` | header and lines are coherent |
| Quotation-to-Order conversion; one canonical association; atomic ordered/read-only result | BR-001, BR-006 | 2 | active | `cumulative-stage2-repair.test.js` | second conversion rejected |
| Direct and sourced Orders have one or more lines | BR-008 | 2 | active | `cumulative-stage2-repair.test.js` | direct order is allowed |
| Sourced Order is conversion-time snapshot | BR-002, BR-009 | 2 | active | `cumulative-stage2-repair.test.js` | post-conversion source mutation is no longer a normal-operation property under HD-007 |

## Superseded/removed observation

| old condition | superseding decision | new condition | why old condition is no longer required | property removed |
| --- | --- | --- | --- | --- |
| Revise a source Quotation after conversion and prove its Order does not change | HD-007 | Test conversion-time copy and post-conversion Quotation immutability | sourced Quotations are read-only after conversion | normal-operation post-conversion source revision |
