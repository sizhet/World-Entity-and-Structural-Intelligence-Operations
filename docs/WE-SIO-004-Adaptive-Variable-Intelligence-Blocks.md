# WE-SIO-004 — Adaptive Variable-Intelligence Blocks

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis and architecture proposal  
**Status:** Exploratory; no performance or scientific-discovery claims are validated  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

## Abstract

Variable-size indexing blocks adjust spatial or logical partition granularity to the distribution of stored entities. WE-SIO proposes a further, explicitly hypothetical generalization: **Perspective-Adaptive Variable Blocks (PAVB)** can vary not only their boundaries and population but also their *representation, evidence handling, and computational intelligence*. An **Adaptive Variable-Intelligence Block (AVIB)** is a bounded, versioned, perspective-dependent unit that selects from lightweight indexing, metric resolution, relational inference, residual analysis, and delegated intelligence services under explicit budgets and conformance contracts. This paper distinguishes the block's physical storage form from its logical intelligence responsibilities; defines candidate data structures, adaptation policies, correctness invariants, and evolution operators; and proposes falsifiable experiments against fixed-granularity and conventional adaptive-index baselines. The updated proposal adds **Mask-First computation**, preservation of mature structural pathways, and explicit separation of established knowledge, open knowledge, and residual evidence. It is a design for investigation, not a claim that AVIBs outperform established data structures.

## 1. Origin and research question

The starting point is **Variable-Size Blocks Index and Search**: a heterogeneous domain can be partitioned with locally different block sizes rather than one globally fixed cell size. Density, boundary complexity, query locality, and update frequency can all motivate different partition sizes. The subsequent World Entity (WE) hypothesis expands the domain beyond spatial coordinates to multiple *perspectives*: Euclidean, general metric, and relational/directional descriptions. This raises a new question:

> If different regions need different indexing resolution, might they also need different *levels and kinds of intelligence*?

A region with stable, uniform observations may need little beyond an index and a predicate evaluator. Another region with ambiguous identity, contradictory evidence, and emerging relations may justify residual tracking, hypothesis generation, and specialized reasoning. The proposed variable is therefore not only **block size** but **block capability**.

This extension must be kept distinct from established adaptive partitioning, learned indexes, query optimizers, and hierarchical inference. The research contribution sought here is a *contract-based integration* of adaptive partitioning with perspective-aware structural intelligence and traceable discovery, not a blanket claim of novelty for adaptive computation itself.

## 2. Definitions and boundaries

### 2.1 World Entity and perspective

A **World Entity** is a modeled referent whose identity is not reducible to any single observed feature or index key. A **Perspective Descriptor** specifies the scope, measurement/comparison semantics, provenance, uncertainty, and applicability of a representation of that entity. The notation `Object[metricIdx]` is an initial modeling shorthand, not a requirement that every descriptor satisfy mathematical metric axioms.

A *Euclidean* perspective admits meaningful coordinates and Euclidean distance; a *general metric* perspective must satisfy the metric contract claimed by its descriptor; a *relational or directional* perspective may represent asymmetric, causal, ordinal, or graph-based connections without pretending they form a metric.

### 2.2 Variable-Size Block (VSB)

A **VSB** is a query-addressable partition whose capacity, extent, or granularity may differ across regions. It is a physical or logical indexing choice; it is not inherently an intelligent agent.

### 2.3 Perspective-Adaptive Variable Block (PAVB)

A **PAVB** is a block with boundaries, grouping, and indexing policy conditioned on a declared perspective and workload. The same WE may appear in multiple PAVB views. Membership is therefore not entity identity; cross-view references must be explicit.

### 2.4 Adaptive Variable-Intelligence Block (AVIB)

An **AVIB** extends a PAVB with a **capability profile**, an **evidence/residual interface**, and a **resource-constrained adaptation policy**. Its intelligence may be local, shared, or invoked lazily. An AVIB is not required to run a dedicated LLM or autonomous agent.

The term *intelligence* here means task-oriented operations such as resolving ambiguous matches, identifying conflicts, maintaining uncertainty, or proposing testable questions. It does not imply consciousness or independent agency.

### 2.5 Two orthogonal axes

- **Partition adaptation:** split, merge, rebalance, migrate, or revise membership.
- **Capability adaptation:** activate, deactivate, delegate, specialize, or revise reasoning/evidence services.
- **Activation-view adaptation:** mask, unmask, or remask nodes, edges, perspectives, operations, depth, and budgets without necessarily changing stored topology.

These axes should be measured separately. Increasing the number of blocks need not increase intelligence; adding an inference service need not change partition boundaries.

## 3. Architectural model

A candidate block schema is:

```text
AdaptiveVariableIntelligenceBlock {
  blockId
  version
  perspectiveId
  perspectiveContractVersion
  regionOrPredicate
  entityReferences
  membershipSemantics
  parentAndCrossViewLinks
  indexStrategy
  capabilityProfile
  maskPolicyRef
  activeViewContract
  epistemicViewRefs
  evidenceReferences
  uncertaintySummary
  residualReferences
  queryAndUpdateStatistics
  resourceBudget
  adaptationPolicy
  provenance
  conformanceStatus
}
```

`regionOrPredicate` can be a Euclidean bounding region, a metric ball, a relation predicate, or a composite filter. `entityReferences` are references to modeled entities, not necessarily copies. `membershipSemantics` specifies overlap, duplication, completeness, and whether a block is authoritative for a given query.

### 3.1 Capability tiers (illustrative, not mandatory)

| Tier | Capability | Typical trigger | Main risk |
|---|---|---|---|
| T0 | Membership and basic retrieval | Stable, low-complexity workload | Missed contextual ambiguity |
| T1 | Metric/relational resolution | Nontrivial similarity or relations | Misdeclared comparison semantics |
| T2 | Evidence and uncertainty reconciliation | Conflicting or incomplete observations | False certainty |
| T3 | Residual/question generation | Persistent unexplained deviations | Spurious hypotheses |
| T4 | Delegated multi-perspective reasoning | High-value, difficult cases | Cost, instability, ungrounded outputs |

Tiers describe service envelopes, not a mandatory ladder. A block may use T3 residual tracking without T2 inference, or outsource T4 operations to a shared service. Capability activation should be justified by measurable workload or evidence requirements.

### 3.2 Logical versus physical hierarchy

The WE-HDT **index hierarchy** is optimized for candidate localization and query execution. Its **intelligence abstraction hierarchy** organizes explanations, evidence, questions, and cross-perspective interpretation. The two hierarchies may map to each other, but need not be identical. A Metric Leaf Intelligence Unit (MLIU) is a logical service contract and may serve many blocks or exist outside a physical tree leaf.

```text
Query / Observation / Change
            |
    Perspective router
            |
  PAVB index candidates  <---->  cross-perspective references
            |
    AVIB capability policy
       /      |       \
   Resolve  Evidence   Residual / Question
       \      |       /
      Shared MLIU services
            |
   Validation + provenance
            |
    Adaptation proposals
```

## 4. Adaptive signals and objective functions

Candidate adaptation signals include:

1. **Density and skew:** uneven membership or access frequency.
2. **Heterogeneity:** variation of attributes or outcomes within a block.
3. **Uncertainty:** unresolved identity, missingness, or contradictory observations.
4. **Residual pressure:** persistent mismatch between expectations and observations.
5. **Task relevance:** query frequency, user-defined importance, or validated research value.
6. **Resource cost:** latency, memory, compute, energy, and governance overhead.
7. **Drift:** changes in data distribution, perspective semantics, or query workload.

An illustrative heuristic for deciding whether to *investigate* greater granularity or capability is:

\[
S(B)=w_DD(B)+w_HH(B)+w_UU(B)+w_RR(B)+w_TT(B)-w_CC(B).
\]

Here the features and weights must be defined and calibrated for the application; the formula is **not** a universal scoring law. Signals may be correlated, noisy, manipulable, or incomparable. A high score should propose an experiment, not directly authorize an expensive or irreversible transformation.

A more rigorous decision objective compares estimated marginal benefit against cost:

\[
\Delta V(a\mid B)=\widehat{Q}_{\text{after}}(a,B)-\widehat{Q}_{\text{before}}(B)
-\lambda\widehat{C}(a,B)-\mu\widehat{Risk}(a,B).
\]

`Q` is an application-defined, independently measured quality metric. An adaptation is eligible only if it passes correctness constraints and its expected gain is positive with adequate confidence. This explicitly separates **hard conformance gates** from **soft optimization preferences**.

## 5. Adaptation operations

### 5.1 Partition operators

- `Split(B, policy)`: subdivide a block while preserving coverage and reference semantics.
- `Merge(B1, B2, policy)`: combine compatible blocks without losing evidence or identity links.
- `Rebalance(B, policy)`: change boundaries or routing while maintaining query correctness.
- `Reindex(B, perspectiveVersion)`: rebuild access paths when comparison semantics change.
- `Migrate(B, target)`: move physical storage or compute placement without changing logical identity.

### 5.2 Capability operators

- `Activate(B, capability)`: provision an operation with an explicit budget and contract.
- `Deactivate(B, capability)`: retire it while retaining required evidence and audit records.
- `Delegate(B, service)`: invoke a shared MLIU, evaluator, or agent through a bounded interface.
- `Specialize(B, policy)`: choose a different inference or matching strategy.
- `EscalateResidual(B, residualRef)`: submit an unexplained discrepancy for cross-block or cross-perspective review.
- `Mask(B, context, policy)`: produce a task-scoped active computation view without changing persistent membership.
- `Unmask(B, scope)`: restore eligible routes or operators subject to authorization and query contracts.
- `Remask(B, feedback)`: revise a prior active view using observed cost, coverage, uncertainty, or failure evidence.

### 5.3 Example adaptation policy

```text
observe block metrics and query outcomes
verify freshness and provenance of signals
propose a task-scoped mask or local learning update first where appropriate
compare against full-view or verified reference execution
propose partition and/or capability changes only when warranted
estimate quality gain, cost, and risk
reject candidates violating hard contracts
run shadow evaluation or bounded sandbox trial
compare against unchanged baseline
commit versioned change only if acceptance criteria pass
retain rollback pointer and explicit leftover
```

Hysteresis, cooldown windows, and minimum evidence thresholds help avoid split/merge oscillation and repeated capability thrashing. A policy must also allow **no change** as a valid decision.

## 6. Query execution and Two-Ways CCC

A candidate query pathway is:

1. Parse the query into perspective-specific predicates and requested evidence standards.
2. Use available Euclidean, metric, or relational indexes to obtain **candidate** WEs; Euclidean-first is optional.
3. Resolve ambiguous candidates through block-local or delegated capability services.
4. Evaluate conditions, uncertainty, and contradictory evidence under the declared contracts.
5. Return matches, provenance, confidence/uncertainty, and explicit unresolved items.
6. Route unexplained results backward as candidate query refinements, perspective revisions, or metric-discovery questions.

This last step is the proposed **Two-Ways CCC** extension: forward localization and resolution are paired with backward feedback from contradictions, residuals, and unanswered questions. Feedback must not silently mutate the semantics of a live query. Any new metric or perspective requires a separately versioned descriptor and validation.

### 6.1 Query correctness

Adaptive execution must not silently sacrifice recall or completeness when the API promises exact results. Approximate search is allowed only under an explicit contract specifying error/recall targets and evaluation procedures. Changing a capability tier must not change the meaning of entity identity or the truth conditions of an exact predicate.

## 7. Residual-first block intelligence

**Epistemic boundary:** an unanswered question is *open knowledge*, not automatically a residual. A residual requires a declared expectation, constraint, model, or explanatory baseline and traceable evidence of a discrepancy. A Residual Evidence Registry (RER) is therefore distinct from an Open Knowledge Registry; neither is an untyped miscellaneous bucket.

A residual is not automatically a discovery. It is a traceable discrepancy requiring interpretation:

```text
ResidualRecord {
  residualId
  entityRefs
  perspectiveId
  expectationRef
  observationRef
  discrepancyDefinition
  evidenceRefs
  uncertaintyAndConfounders
  competingExplanations
  status
  provenance
  version
}
```

Residual pressure can motivate finer partitions or stronger reasoning, but it can also indicate sensor error, distribution shift, selection bias, confounding, or a flawed expectation model. The AVIB should preserve these alternatives and route candidate hypotheses to a separate validation process.

**Example:** A clinical treatment-response cohort may show unexplained heterogeneity. An AVIB could propose subdividing the cohort by an already validated descriptor or testing a new candidate perspective. It must not infer a biological mechanism or recommend treatment from an unvalidated residual. Clinical deployment requires independent scientific, ethical, and regulatory review.

## 8. CDE as an optional evolution controller

Constrained Delta Evolution (CDE) provides a candidate way to model versioned block transformations:

\[
(B_t, C_t) \xrightarrow{\delta_t} B_{t+1},
\]

where `C_t` encodes correctness, cost, provenance, and application constraints. A delta may alter partitioning, capability, evidence links, or index descriptors. Some deltas may be reversible; others require compensating migrations. A block evolution controller should support bounded branching, rollback, and explicit termination conditions.

**Important boundary:** A prohibition on reusing a delta along a path is **not** a universal CDE invariant. Applications such as chess legitimately revisit positions or repeat move types. Path memory and cycle policy are configurable contracts, not universally fixed laws.

The relationship to SIF is similarly precise: WE-HDT and adaptive blocks are **candidate Localization mechanisms**, not replacements for all SIF functional domains. CDE can help govern their constrained evolution, while the scoring/control plane evaluates changes.

## 9. Contracts and invariants

The following are proposed conformance obligations; each needs an executable test in a concrete implementation.

**Identity invariant.** Block split, merge, or migration must not silently create or destroy WE identity.

**Coverage invariant.** Every entity required by an exact query must remain reachable through the declared index paths after adaptation.

**Perspective invariant.** Every comparison identifies its perspective descriptor and version; asymmetric relations cannot be treated as metrics without justification.

**Evidence invariant.** Reasoning outputs distinguish observation, inference, hypothesis, and unknown; provenance is retained.

**Budget invariant.** Activation and delegation respect resource and authorization limits, including timeout and failure handling.

**Version invariant.** Readers have a documented consistency model across reindexing and capability changes; mixed versions are detected or managed.

**Rollback invariant.** Reversible changes support rollback; irreversible changes have a documented recovery/compensation policy.

**Nontriviality invariant.** Added capability must be shown to improve an independently defined outcome, not merely increase structural complexity.

These invariants should be expressed as testable contracts in `SPEC-003`, `SPEC-004`, and `SPEC-006` rather than treated as achieved implementation properties.

## 10. Worked conceptual cases

### 10.1 Uniform spatial catalog

A spatially uniform catalog with simple exact filters may remain at T0. Variable-size partitioning may still reduce query work, but a sophisticated inference service would add overhead without demonstrated benefit. This is a **negative case** for capability escalation.

### 10.2 Dense multi-perspective entity neighborhood

A dense neighborhood may contain entities with similar coordinates but different roles, temporal histories, and relations. Spatial candidate retrieval can be followed by relational resolution. If conflicts persist, a shared evidence service is activated. The block may remain physically unchanged while its logical capability profile changes.

### 10.3 Scientific anomaly cluster

A recurring unexplained residual across multiple blocks may be routed to a cross-perspective registry. The system proposes candidate explanatory descriptors, tests them on held-out data, and either promotes a validated descriptor or records a failed hypothesis. Discovery is not established by improved fit on the same observations that generated the hypothesis.

### 10.4 Abstract graph-only entity

An entity with no meaningful Euclidean embedding must be searchable through graph or relation predicates. This is a counterexample to any mandatory Euclidean-first AVIB architecture.

## 11. Experimental design and baselines

The first validation suite should use both synthetic controlled workloads and real, appropriately licensed datasets. Compare:

| Baseline / variant | Purpose |
|---|---|
| Fixed-size partition + fixed resolver | Measure value of adaptive partitioning |
| Variable-size partition without adaptive capability | Isolate value of intelligence adaptation |
| Adaptive capability with fixed partition | Isolate value of partition adaptation |
| Conventional k-d tree / R-tree / database index, where applicable | Compare with established retrieval systems |
| Graph or metric index baseline for non-Euclidean workloads | Avoid inappropriate spatial comparisons |
| Full AVIB prototype | Test interaction effects and overhead |

**Primary metrics:** exact-query correctness or recall at declared approximation level; p50/p95 latency; throughput; memory and compute cost; update overhead; versioning failures; recovery time.

**Secondary metrics:** evidence completeness, calibrated uncertainty, residual retrieval quality, hypothesis precision on held-out cases, human evaluation cost, and number of validated versus rejected candidate descriptors.

**Ablations:** remove residual feedback, remove capability adaptation, remove partition adaptation, disable cross-perspective routing, and disable CDE-based governance. Evaluate on distribution shift and adversarial/noisy inputs. Report confidence intervals and failure cases, not only mean scores.

**Falsification criterion:** If adaptive capability fails to improve task quality or cost-adjusted utility relative to the strongest relevant baseline, the hypothesis of its general benefit is not supported for that workload. A negative result should remain in the research trace.

## 12. Threats, limitations, and failure modes

- **Overengineering:** a conventional index and resolver may be sufficient.
- **Metric confusion:** similarity scores and directional relations may violate metric axioms.
- **Adaptation instability:** noisy signals can induce oscillations and thrashing.
- **Feedback contamination:** residual-driven hypotheses can overfit or leak test data.
- **Identity fragmentation:** duplicated cross-view references can be mistaken for distinct entities.
- **Hidden cost:** orchestration, provenance, and LLM delegation may dominate retrieval cost.
- **Model drift:** a changed perspective contract can invalidate prior indexes or scores.
- **Governance and privacy:** provenance and cross-entity linkage can expose sensitive data.
- **Non-universality:** some domains have no useful partition structure or no measurable gain from intelligence escalation.

Mitigations include conformance gates, budgeted sandbox experiments, versioned perspective descriptors, access controls, rollback plans, and explicit non-adoption criteria.

## 13. Research hypotheses

**H-AVIB-01 (conditional efficiency).** On heterogeneous workloads, perspective-adaptive partitioning can improve cost-adjusted retrieval performance over a fixed-granularity baseline while preserving the declared correctness contract.

**H-AVIB-02 (capability allocation).** Selective capability activation can achieve comparable resolution quality at lower cost than uniformly activating the same capabilities across all blocks.

**H-AVIB-03 (residual utility).** Traceable residual routing can improve the yield of *independently validated* candidate descriptors relative to a workflow that discards unexplained discrepancies.

**H-AVIB-04 (two-axis independence).** Partition and capability adaptation have separable effects that can be identified through factorial ablation.

**H-AVIB-05 (governed evolution).** Versioned, contract-gated adaptation can reduce correctness regressions compared with ungoverned heuristic adaptation, at a measurable overhead cost.

All hypotheses are unverified and must be registered with datasets, metrics, baselines, acceptance thresholds, and failure conditions before testing.

## 14. Open questions and explicit leftovers

1. What is the smallest AVIB contract that retains explanatory and operational value?
2. Which signals predict *actual* benefit from reasoning, rather than merely difficult-looking data?
3. When should adaptation change block boundaries, and when should it change only service routing?
4. Can residual pressure be calibrated across incompatible perspectives?
5. How should overlapping blocks and multi-perspective entity memberships be reconciled?
6. Which correctness guarantees remain feasible under online reindexing and concurrent updates?
7. Can a shared MLIU be amortized across many blocks without introducing a new bottleneck?
8. What prevents recursive capability escalation from consuming unbounded resources?
9. How should adaptation policies incorporate privacy, consent, and governance constraints?
10. Which applications provide strong negative cases that help narrow the definition?
11. How should WE-HDT and AVIB interfaces coexist with mature SQL, graph, and vector systems?
12. Can evidence-preserving capability downgrades be made lossless, or must some changes be irreversible?

## 15. Definition evolution and collective-learning relay

This paper follows the WE-SIO definition-evolution discipline: **define the invariant, not the inventory**. Its proposed contracts are a minimal candidate kernel, not an exhaustive classification of possible intelligence services. Future applications and counterexamples may require narrowing, splitting, or replacing definitions.

Recommended trace entries:

- `research-trace/HYPOTHESIS-REGISTRY.md`: H-AVIB-01 through H-AVIB-05.
- `research-trace/DEFINITION-REGISTRY.md`: VSB, PAVB, AVIB, capability tier, adaptation policy.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`: graph-only entities, uniform catalogs, costly inference, adaptation oscillation.
- `research-trace/DECISION-LOG.md`: why physical and intelligence hierarchies are separated.
- `research-trace/UNRESOLVED-RESIDUALS.md`: failures to explain workload-specific gains or losses.

A research relay should preserve: **claim → contract → evidence → counterexample → decision → remaining uncertainty**. Repeated experiments, including failed ones, contribute to collective learning when their provenance and conditions are retained.

## 16. Connections and next steps

- **WE-SIO-001:** origin in variable-size indexing and WE modeling.
- **WE-SIO-002:** entity identity and perspective descriptors.
- **WE-SIO-003:** WE-HDT indexing and intelligence architecture.
- **WE-SIO-005:** MLIU operation contracts and service allocation.
- **WE-SIO-006:** Two-Ways CCC and cross-metric discovery.
- **WE-SIO-007/008:** residual registries and candidate metric discovery.
- **WE-SIO-009:** World Delta, Epistemic Delta, and CDE.
- **WE-SIO-011:** Minimal Kernel, Contracts, and Definition Evolution.
- **SPEC-003/004/006:** formalization and conformance work.

**Next research milestone:** implement a small benchmark with fixed versus variable-size partitions, fixed versus adaptive capabilities, explicit identity/coverage checks, and a recorded residual registry. Only after this should AVIB complexity be justified or reduced.

---

## 17. Mask-First computation and mature-structure preservation (v0.1.0 update)

This update incorporates the hypotheses developed in `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`. It treats established structural pathways as accumulated computational assets, while allowing task-specific activation to change frequently. The biological analogy is limited: selective neural activation and gating motivate the design, but do not demonstrate that the brain uses a single explicit mask data structure or that this architecture is faster.

### 17.1 Stored substrate versus active computational view

Let `S_v` be a versioned, authorized structural substrate and `q, p, c, b` a task, perspective, context, and budget. A mask generator produces:

```text
M = GenerateMask(S_v, task=q, perspective=p, context=c, budget=b)
V = ApplyMask(S_v, M)            # transient effective computational view
result = Execute(V, q)
audit = Evaluate(result, reference, evidence, budget)
```

`M` may gate nodes, edges, metric descriptors, operation classes, depth, or budget allocations. Boolean masks, sparse selections, weighted gates, and hierarchical policies are all admissible representations. A mask does **not** change entity identity, source data, index ownership, or authorization. Masking is a *logical selection mechanism*, not necessarily a physical speedup: implementations must verify that excluded computation is actually skipped and that mask-generation overhead does not exceed the savings.

A mask should carry `maskId`, `policyVersion`, `substrateVersion`, `taskScope`, `perspectiveRefs`, `selectedNodesOrPredicates`, `selectedOperations`, `budget`, `authorizationScope`, `completenessMode`, `evidenceRefs`, and `provenance`. A cached mask is invalidated when its relevant structural, schema, authorization, or perspective assumptions change.

### 17.2 Mask/Unmask/Remask semantics

- **Mask:** construct an eligible, task-scoped active view; no persistent structural mutation is implied.
- **Unmask:** broaden or restore eligibility only within the caller's permissions and declared query contract.
- **Remask:** revise the active view after feedback; record policy changes and reasons.

For exact retrieval, the mask must be **coverage-safe**: it cannot exclude any record that may satisfy the declared predicate. If coverage cannot be certified, use full-view fallback, safe expansion, or an explicitly approximate API with measured recall. Evidence or audit paths required by a contract must remain accessible even when expensive inference paths are inactive. A mask must never circumvent row-level or column-level SQL security policies.

### 17.3 Adaptation preference, not universal hierarchy

A candidate preference is: **reuse mature pathways → update locally → remask execution → extend or reconstruct persistent structure when justified**. This is not a mandatory sequence: a corrupt index, changed legal constraint, or incompatible schema may require immediate reconstruction. The governing rule is to choose the lowest-risk, contract-conformant option with demonstrable net benefit, rather than always favoring a mask.

## 18. Activation Delta, Knowledge Delta, and Structural Delta

Three changes must be tracked separately:

| Delta | What changes | Typical persistence | Conformance concern |
|---|---|---|---|
| Activation / Mask Delta | Task-specific eligible routes, nodes, operators, budgets | Transient or cached policy | Completeness, authorization, cost |
| Knowledge / Epistemic Delta | Evidence, beliefs, uncertainty, hypothesis status | Versioned knowledge record | Provenance, validation, rollback |
| Structural Delta | Block boundaries, index topology, service organization | Persistent substrate | Identity, coverage, consistency |

These deltas can interact but are not interchangeable. A revised mask does not by itself establish new knowledge; an epistemic update does not imply that the world changed; a block split does not prove that inference improved. World/source-state changes remain separately typed under `WE-SIO-009`. CDE may govern candidate transitions with application-specific constraints and reversibility policies; the D-BTP path no-reuse rule is not a universal CDE axiom.

A proposed policy score may combine measured task quality, execution cost, mask-generation overhead, stability of mature pathways, evidence loss, and structural-change cost. The weights and baselines must be declared before evaluation; they are not claims of a universal objective function.

## 19. Epistemic views and Residual Evidence Registry

For each `(entityRef, perspectiveId, applicabilityContext, version)` the AVIB/MLIU may expose:

- **Established Knowledge View:** evidence-supported assertions valid within a declared scope; *established* never means infallible.
- **Open Knowledge View:** unresolved questions, untested candidate metrics, provisional explanations, and unknown values.
- **Residual Evidence Registry (RER):** discrepancies against explicit expectations, predictions, constraints, or explanatory baselines.

These are logical views, not necessarily separate physical stores. A hypothesis may be open under one perspective and established under another. A SQL `NULL` is not inherently a residual or a well-defined epistemic status. Residual records must identify the comparison basis, observation, uncertainty, provenance, and competing explanations; a pure unknown without such a basis belongs in the open view.

**Knowledge promotion contract:** transitions `open → established`, `established → revised`, or `established → withdrawn` require evidence criteria, an evaluator or governance policy, version history, and rollback/appeal where feasible. A residual may motivate a candidate hypothesis but never automatically promote it.

## 20. Updated conformance tests and research hypotheses

**Candidate conformance checks:**

1. `MASK-001`: an exact masked query returns the same complete set as a verified full-view reference, or fails closed.
2. `MASK-002`: no mask or remask bypasses entity-, row-, column-, or operation-level authorization.
3. `MASK-003`: changing only an activation mask does not alter persistent block identity, topology, or evidence history.
4. `MASK-004`: stale masks are invalidated after relevant substrate, perspective, or permission changes.
5. `MASK-005`: cost accounting includes mask generation, materialization, cache invalidation, and fallback.
6. `EPI-001`: unknown/open records cannot enter RER without a documented discrepancy basis.
7. `EPI-002`: promotion, demotion, and withdrawal of knowledge are versioned and evidence-traceable.
8. `RELAY-001`: shared mask policies declare transfer assumptions and are independently evaluated on target tasks.

**Proposed falsifiable hypotheses** (to be synchronized with `TESTABLE-HYPOTHESES.md` and the research registry):

- `WEH-031`: Mask-first AVIB execution reduces end-to-end resource cost for some workload classes relative to eager full-view execution at matched correctness.
- `WEH-032`: mature-pathway preservation plus local adaptation reduces measured reconfiguration cost or forgetting in selected continual workloads.
- `WEH-033`: explicit established/open/residual separation reduces epistemic misclassification and improves evidence traceability.
- `WEH-034`: validated mask-policy relay transfers useful computational selection strategies across compatible tasks without unacceptable recall loss.

**Evaluation design:** compare full-view, static hand-designed masks, learned masks, partition-only adaptation, and combined mask-plus-CDE adaptation. Report accuracy/recall, false exclusions, runtime, memory, energy where measurable, mask overhead, rebuild frequency, drift sensitivity, rollback events, and transfer degradation. Include adversarial negative cases: high mask-generation cost, rapidly shifting workloads, weak cross-perspective mappings, and unknown unknowns. Treat all benefits as hypotheses until independently reproduced.

**Cross-references:** `EXT-005` supplies the general mechanism; `EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md` provides a proposed SQL-facing testbed. Formal contracts should be synchronized into `SPEC-003` and `SPEC-005` before claiming conformance.

---

## Research status and attribution

This document is a **research proposal and conceptual specification**, not a peer-reviewed empirical result or deployed system. Names, schemas, tiers, scores, and hypotheses are provisional. Comparisons with established indexing and adaptive-computation methods require literature review and reproducible evaluation. The project is intended as a traceable Collective Learning Relay Piece within the broader Structural Intelligence research program.

**Suggested citation:** Tan, Sizhe, and GPT-Obot. (2026). *WE-SIO-004: Adaptive Variable-Intelligence Blocks*. World Entity and Structural Intelligence Operations, v0.1.0 (research draft).
