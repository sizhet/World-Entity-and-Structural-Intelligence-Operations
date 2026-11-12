# WE-SIO-001 — From Variable-Size Blocks to World Entity

**World Entity and Structural Intelligence Operations (WE-SIO)**  
**Version:** v0.1.0 — Research hypothesis / architecture proposal  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Exploratory; not an established algorithmic performance claim

## Abstract

This paper records the technical origin of WE-SIO: a proposed transition from Variable-Size Blocks Index and Search to a general, perspective-aware computational representation of world entities. The central idea is to use efficient, task-valid Euclidean localization where available, then selectively resolve metric, relational, uncertain, and residual-bearing perspectives. We distinguish a real-world entity from its computational representation, propose a World Entity Hybrid Differential Tree (WE-HDT) as a logical architecture, and outline two-way discovery and evolution operations. The paper deliberately preserves unresolved questions, counterexamples, and testable claims so that it can serve as a reusable Collective Learning relay piece.

**Keywords:** World Entity; Structural Intelligence; Variable-Size Blocks; Hybrid Differential Tree; Perspective Index; Localization; Residual; Two-Ways CCC; Collective Learning.

## 1. Research Origin and Motivation

The starting point is an earlier research proposal named **Variable-Size Blocks Index and Search**, revisited in November 2026. Its original attraction was a potentially simple, adaptive method of organizing and searching multidimensional data. The present work asks a broader question: can a block-based localization mechanism become the entry point for *structural operations over world entities*, rather than remain solely a spatial search technique?

The historical implementation, complexity proofs, and benchmark results of the earlier algorithm are not reproduced here. Consequently, claims of superiority over k-d trees or other indexes are **not established** in this paper. Those claims are framed as benchmark hypotheses.

The research trajectory is:

1. Variable-size blocks for candidate localization.
2. Hybrid Euclidean and non-Euclidean perspective resolution.
3. Entity-specific structural intelligence operations.
4. Residual-driven questioning, metric construction, and representation evolution.
5. Possible self-modeling and cross-entity Collective Learning.

This is a proposal for a *research program*, not a claim that all five steps have already been implemented.

## 2. What Is a World Entity?

The initial shorthand is:

```text
WE := Object[metricIdx]
```

This is useful as an engineering entry point but should not be mistaken for an ontological identity. A world entity may exist without being observed or indexed. We therefore distinguish:

- **Entity** `e`: the referent under study, whether physical, social, conceptual, or computational.
- **Entity identity** `id(e)`: a reference and resolution policy; not merely a similarity signature.
- **Perspective** `p`: a context of observation, purpose, and interpretation.
- **Descriptor** `i`: an attribute, feature, metric, predicate, or relation made accessible through a contract.
- **Representation** `R_t(e,p)`: the system's time-indexed model of `e` from `p`.

A provisional representation is:

$$
R_t(e,p) = (id(e), p, I_t(e,p), V_t, E_t, U_t, H_t)
$$

where `I` denotes descriptors, `V` their values or expressions, `E` evidence and provenance, `U` uncertainty, and `H` versioned history. This is a **candidate schema**, not a universal ontology.

An entity's state and the system's knowledge about it must remain distinct. A new observation may change `R_t` without changing `e`; an unobserved event may change `e` without immediately changing `R_t`.

## 3. Perspective Indices: Three Useful Classes

A preliminary classification is:

| Class | Examples | Core caution |
|---|---|---|
| Euclidean-compatible | calibrated spatial coordinates, task-valid numerical features | numerical encoding alone does not validate Euclidean distance |
| Metric | distances on strings, graphs, or learned spaces when metric axioms hold | computational cost and domain assumptions vary |
| Relational / directional | causal links, trust, preferences, predicates, asymmetric scores | not every comparator is a mathematical metric |

The earlier term *Remaining Metric Perspective Indices* remains historically meaningful. For rigorous interfaces, we propose **Remaining Metric and Relational Perspectives (RMRP)**, encompassing representations that may not satisfy symmetry or triangle inequality.

Membership in a Euclidean layer must be justified by task-specific semantics and a declared distance contract. Time may be encoded numerically, but combining time with spatial coordinates requires explicit units, scaling, and interpretation.

## 4. WE-HDT: A Logical Hybrid Differential Architecture

The proposed **World Entity Hybrid Differential Tree (WE-HDT)** uses two complementary roles:

**Localization layer.** Euclidean-compatible coordinates, adaptive blocks, and inexpensive candidate filtering narrow the search space when suitable.

**Interpretation layer.** Metric and relational descriptors resolve meanings, relationships, evidence, uncertainty, and unmodeled variation, often on demand.

A schematic query is:

```text
Query + Perspective Contract
          |
          v
Candidate Localization (optional Euclidean / block index)
          |
          v
Metric and Relational Resolution
          |
          v
Evidence-Aware Result + Explicit Residuals
          |
          v
Question / Validation / Representation Update
```

**Important:** “lower” and “upper” denote logical functions, not a mandatory physical tree topology. A nonspatial entity may bypass Euclidean localization entirely. One metric or relational component may be shared across many Euclidean blocks. The index hierarchy and intelligence abstraction hierarchy must be specified separately.

### 4.1 Two-phase search

A practical implementation may first select candidate entities using inexpensive predicates, then apply expensive perspective-specific resolution. Correctness requires either a lossless candidate stage or a declared approximation/recall guarantee. A fast filter that silently drops valid candidates is not an acceptable general solution.

### 4.2 Relation to k-d trees

A k-d tree is one possible baseline, alongside R-trees, ball trees, metric indexes, graph indexes, and database query planners. Which backend is best depends on dimensionality, distributions, updates, queries, distance semantics, and memory budgets. WE-HDT should allow multiple backends rather than hard-code one.

## 5. From Variable-Size to Variable-Intelligence Blocks

The first substantive extension is to allow blocks to vary not only in geometric size but also in *resolution effort and attached structure*. We call this candidate mechanism **Perspective-Adaptive Variable Blocks (PAVB)**, or more generally **Variable-Intelligence Blocks**.

A block may carry metadata such as:

```text
BlockDescriptor {
  regionOrPredicate
  coveredEntityRefs
  perspectiveRefs
  densityEstimate
  heterogeneityEstimate
  uncertaintySummary
  residualRefs
  computeBudget
  indexBackend
  refinementPolicy
  provenanceAndVersion
}
```

A tentative refinement utility is:

$$
J(B) = \mathrm{ExpectedQueryGain}(B)
     + \mathrm{ExpectedLearningGain}(B)
     - \lambda\mathrm{ComputeCost}(B)
     - \mu\mathrm{MaintenanceCost}(B).
$$

This expression is a design placeholder. Its terms require operational definitions, calibrated estimators, and out-of-sample tests. Splitting, merging, and attaching new intelligence components should be governed by explicit contracts and reversible or auditable structural changes where feasible.

## 6. Metric Leaf Intelligence Units

A **Metric Leaf Intelligence Unit (MLIU)** is a proposed on-demand computational interface for a perspective-specific component. It need not be a persistent autonomous agent.

```text
MLIU {
  entityRef
  perspectiveRef
  metricOrRelationContract
  observationsAndEvidence
  hypothesesAndUncertainty
  residualRefs
  supportedOperations
  resourceBudget
  provenanceAndVersion
  relayInterfaces
}
```

Candidate operations include:

| Operation | Intended behavior |
|---|---|
| Locate | find relevant entities or perspective regions |
| Resolve | interpret descriptor values and structural context |
| Relate | evaluate entity-to-entity relationships |
| Infer | generate evidence-bounded hypotheses |
| Question | propose discriminating observations or tests |
| Evolve | propose and validate representation updates |

Operations should return provenance, confidence or uncertainty where meaningful, and explicit unresolved outputs. Shared services can execute operations lazily; full agents at every leaf would usually be wasteful.

## 7. Two-Ways CCC and Cross-Metric Discovery

WE-HDT could extend **Two-Ways CCC** from explicit candidate matching to feedback between localization and interpretation:

$$
\text{Localization} \rightarrow \text{Metric/Relational Analysis}
\rightarrow \text{Residual Detection}
$$

$$
\text{Residual} \rightarrow \text{Candidate Perspective or Metric}
\rightarrow \text{Revised Localization / Validation}
$$

The backward direction must not convert a weak pattern into a fact. Proposed new descriptors, metrics, or relations require conformance checks and independent evidence. This is a research hypothesis about discoverability and operational efficiency, not an established improvement in accuracy.

## 8. Residuals as First-Class Research Objects

A residual can be an unexplained numerical deviation, contradictory relation, unclassified case, missing perspective, or prediction failure. A provisional residual record is:

```text
ResidualRecord {
  residualId
  entityAndPerspectiveRefs
  expectationOrModelRef
  observationAndEvidenceRefs
  discrepancyDescription
  alternativeExplanations
  uncertainty
  proposedTests
  statusAndHistory
}
```

Residuals should be retained, compared, questioned, and independently tested. Their presence signals a gap between model and observation; it does **not** by itself establish a novel mechanism. Existing scientific practices already exploit anomalies and residuals. The WE-SIO hypothesis is that cross-domain structural indexing, provenance, and relay may make such work more reusable.

## 9. World Delta, Epistemic Delta, and CDE

WE-SIO distinguishes two kinds of change:

- **World Delta:** a change in the referent or environment.
- **Epistemic Delta:** a change in the system's representation or evidence state.

They may coincide, diverge, or be temporally separated. A representation update can be modeled as:

$$
R_{t+1} = \mathrm{Apply}(R_t, \Delta_K; C)
$$

where `C` includes integrity, provenance, identity, and validation constraints. This connects naturally to **Constrained Delta Evolution (CDE)** as a candidate structural evolution mechanism, without requiring every application to share the same delta format or path policy.

The chess counterexample is instructive: a global *No-Delta-Reuse* rule is not valid across all state-transition problems. Such restrictions belong in application-specific contracts unless proven essential to a narrower kernel.

## 10. From World Modeling to Self-Modeling

An entity representation can describe a subject that observes, acts, and updates a model of itself. A candidate self-modeling loop is:

$$
M_t \rightarrow a_t \rightarrow o_{t+1} \rightarrow M_{t+1}.
$$

This suggests a bridge from WE-SIO to **Subjective Structural Intelligence (SSI)**: self-reference, history, boundaries, perspectives, and feedback. However, an operational self-model does **not** demonstrate consciousness, subjective experience, or philosophical personhood. Those questions remain open and must not be conflated with software functionality.

## 11. Definition Evolution as Research Method

General frameworks cannot enumerate every future application at inception. WE-SIO therefore adopts:

> **Define the invariant, not the inventory.**

Its research process separates:

1. **Minimal semantic kernel:** the smallest clear commitments.
2. **Conformance contracts:** tests that admit or reject proposed instances.
3. **Optional extensions:** specialized algorithms and policies.
4. **Counterexample registry:** cases that stress or falsify assumptions.
5. **Versioned refinement:** explicit changes, compatibility notes, and regression tests.

Definitions may broaden, narrow, split, or be rejected. A universal-sounding definition that admits everything without discriminating mechanisms is not a scientific achievement.

## 12. Preliminary Research Questions

**Representation and identity**

- RQ-01: What is the smallest useful entity representation independent of any particular database schema?
- RQ-02: How can entity identity remain stable across changing and conflicting perspectives?
- RQ-03: When is a perspective legitimately Euclidean, metric, or only relational?

**Indexing and computation**

- RQ-04: Under which workloads do variable-size blocks outperform established index structures?
- RQ-05: Can a hybrid candidate stage provide explicit recall and cost guarantees?
- RQ-06: When should the system refine a block versus attach a richer perspective component?
- RQ-07: Can shared metric components avoid duplicative per-block computation?

**Discovery and evolution**

- RQ-08: Does cross-metric feedback improve hypothesis discovery under controlled evaluation?
- RQ-09: How should residuals be ranked without suppressing rare but meaningful exceptions?
- RQ-10: Can new metrics or relational predicates be proposed and validated automatically?
- RQ-11: How can World Delta be distinguished from Epistemic Delta in partially observed systems?

**Self-modeling and collective relay**

- RQ-12: What operational capabilities distinguish self-modeling from ordinary entity indexing?
- RQ-13: Which research artifacts enable independent teams or agents to resume unresolved investigations?
- RQ-14: What conformance tests distinguish WE-SIO from a generic schema-plus-query system?

## 13. Validation Roadmap

### Stage A — Definitions and conformance

Specify entity identity, perspective descriptors, admissible metrics/relations, residual records, and operation contracts. Produce positive, negative, and boundary cases.

### Stage B — Localization baselines

Benchmark variable-size blocks against k-d trees and other appropriate baselines across low/high dimensions, skewed/uniform distributions, mixed query types, dynamic updates, and memory constraints. Report latency distributions, recall, build time, and maintenance cost.

### Stage C — Structural operations

Implement a minimal MLIU interface with explicit evidence and provenance. Compare query plans with and without metric/relational resolution and residual capture.

### Stage D — Discovery tests

Use synthetic datasets with known hidden mechanisms, then carefully selected public research datasets. Measure hypothesis precision, discovery recall, false discoveries, validation cost, and robustness to confounding. Medical examples must not be interpreted as clinical efficacy claims.

### Stage E — Relay and self-modeling

Test whether independent investigators can reconstruct prior decisions, reuse contracts, challenge hypotheses, and continue from explicit unresolved residuals. Treat self-modeling as a functional research target, not a consciousness test.

## 14. Explicit Non-Claims and Risks

This paper does **not** establish that:

- Variable-Size Blocks generally outperform k-d trees.
- Euclidean-first organization is appropriate for every entity or query.
- All attributes or relationships are mathematical metrics.
- Residuals necessarily indicate hidden scientific laws.
- Cross-metric CCC has already demonstrated superior discovery performance.
- A self-referential representation constitutes consciousness.

Key risks include overgeneralization, ambiguous identity, invalid distance semantics, spurious correlations, expensive metric resolution, uncontrolled structural growth, privacy leakage, and benchmark selection bias.

## 15. Interfaces to the Wider SI Research Program

- **SIF:** localization, addressing, and structural intelligence orchestration.
- **CDE:** constrained structural and epistemic representation updates.
- **AQSI:** autonomous question generation from unresolved gaps.
- **UCPSF:** perspective-aware scoring and resource governance.
- **BM-ODWEI / REN:** weak evidence, directional and relational analysis.
- **UIERU:** cross-unit relay and collective structural learning.
- **SSI:** self-models, subject boundaries, and perspective-sensitive identity.

These are proposed conceptual interfaces; their exact compatibility requires future specifications.

## 16. Collective Learning Relay Contract

To make this paper a durable relay piece, future contributions should record:

```text
ContributionRecord {
  questionOrHypothesisId
  originatingAssumption
  proposedDefinitionOrMechanism
  supportingEvidence
  counterexamples
  evaluationProtocol
  observedResults
  unresolvedResiduals
  versionAndProvenance
  nextRecommendedTest
}
```

Relevant repository companions include `research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md`, `research-trace/HYPOTHESIS-REGISTRY.md`, `research-trace/COUNTEREXAMPLE-REGISTRY.md`, and `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`.

## 17. Conclusion

Variable-size block indexing offers a concrete starting point for exploring a larger question: how can a computational system locate, interpret, question, and revise its representations of world entities? WE-HDT, PAVB, MLIU, cross-metric Two-Ways CCC, and residual-centered evolution are **candidate answers**, not completed proofs. The immediate goal is to turn them into discriminating contracts, comparative benchmarks, and reproducible research traces.

> **Preserve not only what we know, but also how we arrived there, what challenged it, and what remains unknown.**

---

**Suggested citation:** Tan, S., & GPT-Obot. (2026). *WE-SIO-001: From Variable-Size Blocks to World Entity*. World Entity and Structural Intelligence Operations, v0.1.0 (research manuscript). DOI pending.

**License:** Intended repository license Apache-2.0; see root `LICENSE` when published.
