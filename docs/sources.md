# Sources and Evidence Boundary

Accessed 2026-09-04. Sources are used for conceptual comparison, not as evidence that the candidate intervention works for coding agents.

## Primary or authoritative sources

1. David L. Parnas, [On the Criteria To Be Used in Decomposing Systems into Modules](https://dl.acm.org/doi/10.1145/361598.361623), *Communications of the ACM*, 1972. The foundational information-hiding framing.
2. Robert C. Martin, [Screaming Architecture](https://blog.cleancoder.com/uncle-bob/2011/09/30/Screaming-Architecture.html), 2011. Business/use-case legibility of architecture.
3. Robert C. Martin, [The Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html), 2012. Dependency-rule framing.
4. Jimmy Bogard, [Vertical Slice Architecture](https://www.jimmybogard.com/vertical-slice-architecture/), 2018. Coupling on an axis of change, minimal cross-slice sharing, and per-slice choices.
5. Philipp Hauer, [Package by Feature](https://phauer.com/2020/package-by-feature/), 2020/2022. Feature packaging contrast with technical-layer packaging.
6. Microsoft Learn, [Use domain analysis to model microservices](https://learn.microsoft.com/en-nz/azure/architecture/microservices/model/domain-analysis), accessed 2026-09-04. Bounded contexts, iterative boundaries, and model scope.
7. Microsoft Learn, [Use tactical DDD to design microservices](https://learn.microsoft.com/en-ca/azure/architecture/microservices/model/tactical-ddd), accessed 2026-09-04. Tactical patterns are applied within bounded contexts rather than mandated as one global package layout.
8. Eric Evans, *Domain-Driven Design: Tackling Complexity in the Heart of Software*, Addison-Wesley, 2003. Canonical book reference for bounded context/modules/domain modeling; not quoted here because no authoritative freely accessible full text was used.

## Methodological boundary

The requested “Raw SQL Rules” Contracts / Default Requirements / evidence-driven subtraction material was not present locally, and searches did not yield a clearly authoritative public source. This repository therefore does not claim to have reviewed or derived any specific rule from it. Its only methodological stance is explicit in the documents: do not publish a rule before evidence; remove unsupported structure; and separate an evaluable candidate from a normative contract.

## What these sources cannot prove

They cannot establish a causal effect of this exact candidate wording on modern coding agents, nor demonstrate the claimed outcomes for lower-cost models. Those are the deliberately unresolved claims in the evaluation plan.
