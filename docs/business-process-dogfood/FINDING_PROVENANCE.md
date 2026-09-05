# Finding discovery provenance (observer-only)

Historical records are preserved. This retrospective classification does not change their outcomes.

| finding | stage | classification | provenance | basis |
| --- | --- | --- | --- | --- |
| transaction-start expiry comparison | 1 | implementation defect | uncertain | review found implementation timing behavior; packet did not explicitly request transaction-start semantics |
| numeric NaN acceptance | 1 | implementation defect | uncertain | numeric validity was required, but provenance cannot be established from the preserved prompt alone |
| conversion eligibility, post-conversion association, revision, order cardinality, snapshot projection | 2 | HUMAN_BLOCKER — under-specification | latent_cross_activity | required by interactions between quotation revision and order creation, rather than a single implementation detail |
| torn quotation read | 2 | implementation defect | uncertain | implementation coherence issue |
| revised quotation header omission | 2 | implementation defect | uncertain | HD-007 supplied header mutability but implementation omitted it |
| performer authority and creator/manager separation | 3 | HUMAN_BLOCKER — under-specification / data-model insufficiency | latent_cross_activity | approval and confirmation activities require individual identity relation not represented by then-current order data |

Stage 4's published approval-validity-after-revision ambiguity, if it becomes a blocker, is `explicitly_cued`; it must not be counted as discovery of a hidden inconsistency.
