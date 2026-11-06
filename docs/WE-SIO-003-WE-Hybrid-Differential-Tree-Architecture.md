# WE-SIO-003 — World Entity Hybrid Differential Tree Architecture

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Hypothesis  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed architecture; not a validated universal indexing method  
**Repository path:** `docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`

## Abstract

The World Entity Hybrid Differential Tree (WE-HDT) is a proposed structural-intelligence architecture for locating, comparing, interpreting, and evolving representations of world entities across heterogeneous perspectives. It combines a potentially efficient Euclidean indexing substrate with metric and relational interpretation structures, while preserving the distinction between a real-world entity, its knowledge representation, and its physical retrieval indexes. WE-HDT extends the motivating idea of variable-size block indexing into adaptive, perspective-aware retrieval and intelligence allocation. Its key research hypothesis is that selective localization followed by conditional semantic expansion can make cross-perspective operations tractable without discarding residuals, uncertainty, or counterexamples. This paper specifies the logical layers, node and edge contracts, query execution, update semantics, correctness obligations, alternatives, and falsifiable evaluation plan. The architecture is a candidate design, not a claim of superior performance to established spatial or database indexes.

**Keywords:** World Entity; Hybrid Differential Tree; Euclidean indexing; metric search; relational perspectives; variable-size blocks; two-phase search; residual; structural intelligence; localization.

## 1. Scope and research questions

WE-SIO begins with the shorthand `WE = Object[metricIdx]`. This shorthand describes a *computational access model*, not an exhaustive ontological definition. An entity may exist without being observed, indexed, or understood. The architectural problem is to maintain useful, revisable descriptions and query paths for such entities.

WE-HDT asks:

1. Which dimensions admit a valid Euclidean representation and efficient pruning?
2. How can the system attach non-Euclidean metrics and non-metric relationships without misclassifying them?
3. When should a query move from cheap candidate localization to expensive interpretation?
4. How should evidence, unknowns, and cross-perspective conflicts survive pruning and updating?
5. How can the index evolve without conflating world changes with changes in knowledge?
6. When does this architecture outperform simpler relational, graph, spatial, or vector retrieval baselines?

The immediate target is an executable specification and test plan, not a universal intelligence claim.

## 2. Foundational distinctions

### 2.1 Entity, representation, and index

Let `e` denote an entity, `R_t(e,p)` a time-indexed representation of `e` under perspective `p`, and `I_t` an index over some representations. In general:

`e != R_t(e,p) != I_t`.

A single entity may have many partially incompatible representations. A representation may be indexed by multiple retrieval mechanisms. Index entries are not evidence that the represented claims are true.

### 2.2 Perspective descriptor

A perspective descriptor `p` declares at least:

- `perspective_id`, scope, entity types, and applicable observation window;
- attribute domain, units, coordinate reference or relation vocabulary;
- comparison contract: equality, ordering, similarity, distance, predicate, or directed score;
- uncertainty, provenance, access policy, and version;
- validity tests and optional index-adapter capabilities.

The descriptor is the unit of semantic conformance. A numeric column is not automatically an admissible Euclidean distance dimension.

### 2.3 Three comparison families

**Euclidean-admissible:** coordinates in `R^d` with a task-appropriate, declared Euclidean geometry and scaling. Time and mixed-unit variables require explicit transformations or weighting.

**General metric:** a distance `d` satisfying non-negativity, identity of indiscernibles, symmetry, and the triangle inequality, but not necessarily arising from Euclidean coordinates.

**Relational/directional:** graph edges, causal hypotheses, preferences, asymmetric scores, and other predicates that need not satisfy metric axioms.

A non-metric relation must not be silently passed to a metric-tree pruning algorithm.

## 3. Architectural thesis: two hierarchies, not one

The initial research intuition is an Euclidean Differential Tree at the computational base with Metric Differential Tree structures attached above or at its leaves. WE-HDT retains this as a **candidate execution pattern**, not a mandatory universal physical tree.

Two independent hierarchies must be distinguished:

1. **Indexing hierarchy:** partitions, blocks, posting lists, node bounds, routing keys, and retrieval costs.
2. **Intelligence abstraction hierarchy:** perspectives, hypotheses, residuals, explanations, evidence, questions, and relay operations.

Mappings connect them, but neither hierarchy is required to be a tree in all cases. Shared perspective objects, many-to-many relations, and graph-like references are permitted.

### 3.1 Logical layers

```text
WE identity and perspective registry
              |
      Query/control plane
              |
  +-----------+------------+
  |                        |
Euclidean-admissible     Direct metric/
localization adapters    relational adapters
  |                        |
Variable-size blocks   Graph / metric / SQL /
2-phase candidates     vector / scan access
  +-----------+------------+
              |
    Candidate + evidence set
              |
 Conditional perspective resolution
              |
 Metric Leaf Intelligence Units (MLIU)
              |
 Residual / question / hypothesis registry
              |
 Validated updates and structural relay
```

The direct metric/relational route prevents the Euclidean substrate from becoming an artificial bottleneck for entities without meaningful Euclidean coordinates.

## 4. Euclidean localization substrate

### 4.1 Variable-size blocks

A block is a bounded or otherwise indexed candidate region with an explicit membership rule, statistics, and version. Its size can adapt to data distribution and workload. Candidate criteria include density, heterogeneity, query frequency, update frequency, uncertainty, and maintenance cost.

A hypothetical refinement utility is:

`U(B) = w_d D(B) + w_h H(B) + w_q Q(B) + w_u Uc(B) - w_c C(B)`.

This is a **heuristic template**, not a theorem. All terms require normalization, and the system must estimate expected query benefit rather than splitting whenever a weighted score is high. Splits and merges must preserve coverage and retrieval correctness.

### 4.2 Differential structure

A differential node records what distinguishes a child region from its parent: coordinate bounds, partition predicates, summary changes, or optional comparison signatures. Differential encoding is an implementation option; a conventional tree or database index remains a valid baseline.

### 4.3 Search contracts

For exact range queries, a localization adapter must not discard any entity satisfying the declared predicate. For exact nearest-neighbor queries, pruning must use valid lower bounds under the declared distance. Approximate retrieval may relax recall only when the caller explicitly accepts that contract and the system reports the approximation.

The historical Variable-Size Blocks method is a motivating antecedent; its exact algorithm, complexity, and benchmark results are not reconstructed or assumed here.

## 5. Metric and relational perspective resolution

A localized candidate can link to zero, one, or multiple perspective-specific structures. A Metric Leaf is a **logical resolution unit**, not necessarily a physical leaf of the Euclidean tree. It may be shared across blocks, reference external stores, or be reached through a non-Euclidean route.

### 5.1 Metric Leaf Intelligence Unit (MLIU)

```text
MetricLeafIntelligenceUnit {
  leaf_id, entity_refs, perspective_id, descriptor_version
  observations, hypotheses, evidence_refs, provenance
  uncertainty, validity_window, residual_refs, question_refs
  supported_operations, resource_budget, access_policy
  structure_version, relay_interfaces
}
```

A leaf may expose `Locate`, `Resolve`, `Relate`, `Infer`, `Question`, and `Evolve`. These are **capability interfaces**; not every leaf needs to implement all six, and an implementation may share inference resources across many leaves. Observations and hypotheses must remain distinguishable.

### 5.2 Cross-leaf references

Many-to-many references represent cross-entity and cross-perspective relationships. Their contract records source and target, relation semantics, evidence, temporal validity, and uncertainty. A cross-reference is not a proof of identity or causality.

### 5.3 Unknown is not a distance

Unknown, missing, censored, contradictory, and not-applicable values require distinct statuses. None should be silently mapped to zero distance. Query planners must specify whether unknown values are retained for exploration, excluded from a strict predicate, or returned separately.

## 6. Two-phase and bidirectional search

A candidate execution plan consists of:

**Phase 1 — Localization:** apply valid cheap filters and indexes to produce candidate entity references, with explicit completeness or recall guarantees.

**Phase 2 — Resolution:** evaluate expensive metric/relational comparisons, evidence, hypotheses, and residuals on candidates, or invoke direct alternative adapters.

Two-Ways CCC can add feedback: metric or residual findings suggest new localization predicates, and localization differences prompt metric questions. Feedback may revise future query plans, but cannot retroactively justify dropping valid candidates from an exact query.

### 6.1 Pseudocode

```text
function WE_HDT_QUERY(query, policy):
    descriptors = resolve_perspective_contracts(query)
    plans = choose_valid_adapters(descriptors, policy)
    candidates = retrieve_candidates(plans, policy)
    results = []
    for entity_ref in candidates:
        observations = resolve_perspectives(entity_ref, query, policy)
        evaluation = evaluate_query(observations, descriptors)
        results.append(evaluation)
        record_unexplained_gaps(evaluation, policy)
    return rank_or_filter(results, policy), query_provenance(plans)
```

Planner choices must be visible in the trace. For exploratory queries, an additional discovery channel may retain low-confidence or unresolved candidates without presenting them as verified matches.

## 7. Structural updates and CDE connection

WE-HDT distinguishes two update classes:

- **World Delta:** a change in the represented entity's real-world state, supported by observations or other evidence.
- **Epistemic Delta:** a change in what the system knows or believes, including corrections, new measurements, revised hypotheses, or perspective definitions.

Both affect representations and indexes, but their meanings differ. A newly discovered skill does not imply that the skill appeared at discovery time.

A constrained update can be modeled as a partial transition:

`ApplyDelta : (RepresentationState, Delta, Contracts) -> Result<NewState, Rejection>`.

A successful update preserves identity constraints, evidence provenance, required query invariants, and version traceability. CDE offers a candidate language for state transitions and path policies; `No-Delta-Reuse` is an optional application policy, not a universal WE-HDT invariant.

### 7.1 Update workflow

1. Validate the proposed Delta against its perspective and identity contracts.
2. Append evidence and retain the prior representation version.
3. Update affected leaf or relation structures.
4. Refresh, split, merge, or re-route affected index blocks.
5. Recheck exact-query invariants and version consistency.
6. Record any residual, conflict, or rejected Delta for later review.

## 8. Residual-first discovery and metric generation

A residual is an unresolved discrepancy between observation, expectation, comparison, or perspective claims. Residuals should be first-class records with identity, evidence, uncertainty, and lifecycle status. They may trigger questions or candidate new metrics.

```text
Residual -> Question -> Candidate Perspective/Metric
         -> Conformance Check -> Independent Validation
         -> Accepted / Revised / Rejected / Unresolved
```

A candidate metric must pass its declared mathematical or operational contract. A useful directional score need not be called a metric. Independent evaluation is required to distinguish discovery from overfitting, selection bias, or measurement error.

In clinical or pharmaceutical research, this mechanism may help organize treatment-response discrepancies and candidate explanations. It is not evidence of clinical validity, causal identification, or patient benefit without appropriate study design and validation.

## 9. Identity, history, and self-modeling boundary

`EntityID` is not equivalent to a feature signature. Identity resolution is a separately governed process with temporal, evidential, and privacy implications. Two similar records may refer to different entities; one entity may change features over time.

A self-modeling entity is an entity whose operational system maintains a representation of its own state, actions, predictions, and feedback. WE-HDT may supply the representational and retrieval substrate for such a model. This does not establish consciousness, subjective experience, or personhood.

## 10. Example execution: relational database to WE-HDT

Consider a `Person` table with `person_id`, `age`, `latitude`, `longitude`, and `occupation`.

- `person_id` maps to a candidate entity identifier, subject to identity rules.
- `latitude` and `longitude` may participate in a declared spatial adapter.
- `age` is numeric but must not be combined with geographic distance without a task-specific metric contract.
- `occupation` is a categorical descriptor, not a Euclidean distance by default.
- Related skills, evidence, and professional relationships may be resolved through joins, graph edges, or MLIUs.

A query for people near a region with a particular expertise may use spatial localization first, then resolve evidence of expertise. If the expertise criterion is highly selective and indexed, a relational-first plan may be cheaper. The planner should compare both rather than hard-code Euclidean-first.

## 11. Complexity and performance hypotheses

No asymptotic superiority is claimed without specifying the index implementation, dimension, data distribution, update model, and query family. A rough cost decomposition is:

`T_query = T_plan + T_localize + |Candidates| * T_resolve + T_rank + T_trace`.

This expression identifies cost drivers but is not a complexity bound. Important risks include high-dimensional distance concentration, costly cross-leaf joins, frequent schema evolution, update amplification, skewed blocks, and excessive residual accumulation.

**Hypothesis H1:** On spatially selective workloads with expensive relational resolution, valid two-phase pruning can reduce total query cost compared with full resolution.

**Hypothesis H2:** Adaptive block sizes can improve selected skewed workloads over fixed partitioning, after accounting for update and rebuild costs.

**Hypothesis H3:** A shared residual registry can improve traceability and hypothesis reuse, but may impose significant storage and governance overhead.

**Hypothesis H4:** Adaptive query planning will outperform forced Euclidean-first execution on heterogeneous workloads.

All four hypotheses are falsifiable; none is yet established.

## 12. Conformance and validation plan

### 12.1 Correctness tests

- **CT-01:** Identity remains distinct from representation and index keys.
- **CT-02:** Every Euclidean adapter declares units, dimensions, and distance semantics.
- **CT-03:** Non-metric relations are rejected by metric-only pruning routines.
- **CT-04:** Exact range retrieval retains all qualifying entities.
- **CT-05:** Approximate retrieval discloses its recall/quality policy.
- **CT-06:** Missing, unknown, and not-applicable are not conflated.
- **CT-07:** Perspective provenance and version are preserved through joins.
- **CT-08:** World Delta and Epistemic Delta are recorded separately.
- **CT-09:** Block split/merge operations preserve index coverage.
- **CT-10:** Residuals remain traceable after perspective revisions.
- **CT-11:** Direct non-Euclidean access is available where Euclidean routing is invalid.
- **CT-12:** Policy enforcement prevents unauthorized cross-entity joins.

### 12.2 Benchmark families

Compare against appropriate implementations of k-d trees, R-trees, metric trees, SQL B-tree/GiST indexes, graph traversal, vector indexes, and simple scans. Do not assume all baselines apply to every workload. Vary dimensionality, skew, query selectivity, update rate, evidence density, relation fan-out, and approximation budget.

Report recall, precision where applicable, p50/p95 latency, throughput, index size, update cost, query-plan overhead, provenance completeness, and residual retention. Use held-out workloads and repeatable datasets.

### 12.3 Negative controls and stress tests

Include tasks with no meaningful Euclidean embedding, misleading numeric attributes, conflicting perspectives, identity collisions, missing values, cyclic relations, adversarial updates, and data where a standard database index clearly wins. These tests define the architecture's actual boundary.

## 13. Interfaces to the SI research ecosystem

- **SIF:** localization/addressing and structural-intelligence functional-domain integration.
- **Variable-Size Blocks / Two-Phase Search:** candidate physical indexing and retrieval techniques.
- **Two-Ways CCC:** bidirectional candidate-condition triggering and cross-perspective feedback.
- **UCPSF:** scoring and policy selection under explicit perspectives and budgets.
- **AQSI:** question generation from residuals and unresolved distinctions.
- **BM-ODWEI / REN:** weak-evidence, directional and relational interpretation.
- **CDE:** constrained structural updates and evolution policies.
- **UIERU:** relay, collective learning, and exchange of validated structural pieces.
- **SSI:** possible self-modeling extension, with explicit epistemic boundaries.

These are proposed interoperability directions, not proven equivalences.

## 14. Open questions and explicit leftovers

1. What is the minimal WE-HDT kernel that adds value beyond a generic state-and-index framework?
2. Which differential-node representation is best suited to heterogeneous perspectives?
3. Under what distributions do variable-size blocks beat established spatial indexes?
4. Can the planner estimate metric-resolution cost without costly profiling?
5. When should a Metric Leaf be shared, split, merged, or externalized?
6. How should non-metric directional relations be composed without false metric assumptions?
7. What evidence threshold justifies creating a new perspective descriptor?
8. Can residual-driven metric generation improve held-out discovery rather than fit noise?
9. What is the appropriate version-consistency model for concurrent World and Epistemic Deltas?
10. How should privacy, consent, and access constraints propagate through cross-entity relay?
11. Which parts of WE-HDT belong to indexing, and which to intelligence abstraction?
12. What observations would falsify the claim that WE-HDT is useful as an integrated architecture?

These leftovers are intended to remain visible and transferable to future researchers or agents.

## 15. Proposed research milestones

**M0 — Formal contracts:** complete perspective descriptors, node invariants, identity and evidence contracts.

**M1 — Minimal prototype:** one Euclidean adapter, one relational adapter, explicit two-phase planner, and versioned provenance.

**M2 — Comparative benchmark:** baseline comparisons, adversarial data distributions, update workloads, and negative controls.

**M3 — Discovery loop:** residual registry, candidate metric proposals, independent validation, and query-plan feedback.

**M4 — Collective relay:** portable research records, conformance results, and reproducible extension contracts.

Advancement between milestones requires explicit evidence, not simply completion of a narrative document.

## 16. Research positioning and non-claims

WE-HDT is a proposed architecture and research relay piece. It does **not** claim that variable-size blocks universally outperform k-d trees, that all knowledge admits Euclidean representation, that all relations are mathematical metrics, that unexplained residuals imply novel laws, that an entity representation equals the entity, or that a self-model proves consciousness. The design favors a small semantic kernel, explicit contracts, optional extensions, falsifiable hypotheses, and preservation of unresolved evidence.

> Define the invariant, not the inventory.

> Unknown is not zero. Unexplained is not useless. Residual is not necessarily noise.

> Residual is evidence of an explanatory gap, not automatically evidence of a new law.

## 17. Repository links and suggested reading order

1. `research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md` — origin and research provenance.
2. `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md` — methodological foundation.
3. `docs/WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md` — technical motivation.
4. `docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md` — semantic and descriptor foundations.
5. `docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md` — proposed adaptive block mechanisms.
6. `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md` — leaf-level intelligence interfaces.
7. `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md` — future normative contract.
8. `cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md` — future empirical stress test.

## 18. Collective Learning Relay handoff

A future contributor should be able to reconstruct (a) the declared representation and perspective semantics, (b) the adapter and query-plan choices, (c) the evidence and residual records, (d) the update history, and (e) the benchmark or counterexample supporting each architectural claim. New claims should be registered with their scope, supporting evidence, counterexamples, and unresolved questions. Implementations should preserve this trace even when a hypothesis is rejected.

---

**Document status:** Research proposal, v0.1.0. Subject to revision through conformance tests, benchmark evidence, and collective learning.
