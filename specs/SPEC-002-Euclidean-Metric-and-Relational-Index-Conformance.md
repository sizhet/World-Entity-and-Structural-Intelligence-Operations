# SPEC-002 — Euclidean, Metric, and Relational Index Conformance

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** 0.1.0 (research draft)  
**Status:** Proposed specification; not an implementation or demonstrated performance claim  
**Authors:** Sizhe Tan & GPT-Obot  
**Companion:** `SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md`

## Abstract

This specification defines testable contracts for three families of World Entity (WE) perspective indexes: Euclidean, general metric, and relational/directional. Its purpose is to prevent a convenient search heuristic from being mistaken for a mathematical guarantee, and to separate index-level candidate retrieval from evidence-backed entity resolution and Structural Intelligence (SI) interpretation. It specifies descriptor typing, query semantics, completeness and soundness claims, admissible pruning, versioning, provenance, cross-perspective joins, failure modes, and conformance tests. The specification is deliberately extensible: not every entity has Euclidean coordinates, not every comparison is a metric, and a logical WE-HDT hierarchy need not match its physical storage layout.

## 1. Scope and normative language

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative within an implementation that declares conformance to this *proposed* WE-SIO specification. They do not imply adoption by any standards organization.

In scope: perspective descriptors, index eligibility, retrieval semantics, filtering, cross-index routing, updates, correctness claims, and validation. Out of scope: mandatory storage engine, distributed consensus, learned metric validity, and proof that any index improves accuracy or speed in all workloads.

## 2. Semantic foundation

A World Entity is not its index. An entity reference identifies the modeled subject within a declared identity scope; a perspective descriptor specifies how some aspect of it is observed or compared; an index accelerates retrieval under that descriptor. All results MUST preserve the separation:

`Entity ≠ Identity ≠ Representation ≠ Perspective ≠ Index`.

A perspective descriptor MUST declare at least:

- `perspective_id`, `version`, `kind`, `domain`, `value_schema`;
- `comparison_contract` (including units, missing-value rules, and directionality);
- `valid_time_policy` and `observation_time_policy`;
- `provenance_policy`, `uncertainty_policy`, and `identity_scope`;
- `index_capabilities` and their declared guarantee level.

Kinds are `euclidean`, `metric`, `similarity`, `directional`, `relational`, or an explicitly registered extension. A descriptor MUST NOT be promoted to `metric` merely because its values are numeric or its comparison returns a score.

## 3. Euclidean index contract

A Euclidean perspective declares a coordinate map `x: E -> R^d` for a fixed dimension `d` and a distance contract, ordinarily

\[d_2(x,y)=\sqrt{\sum_{i=1}^{d}(x_i-y_i)^2}.\]

An implementation MUST specify the coordinate reference system, scaling, units, dimension, null handling, and numerical tolerance. If a different norm or weighted distance is used, it MUST be named and its properties documented. Physical location is only one possible Euclidean perspective; numeric attributes qualify only if the coordinate/distance interpretation is defensible.

### E-1 Eligibility

- Every indexed value MUST satisfy the declared dimensionality and finite-value policy.
- Mixed units MUST be normalized by an explicit transform, not silently combined.
- Coordinate transformations MUST be versioned and reproducible.
- An entity lacking the Euclidean perspective MUST remain reachable through another supported query path where the query semantics require it.

### E-2 Query behavior

Supported query types MAY include exact lookup, range, radius, and `k` nearest neighbors. The response MUST label its guarantee as `exact`, `bounded_approximate`, or `best_effort`, and disclose filters and the effective snapshot. Exact radius queries MUST not omit any eligible point within the declared radius (subject to documented numeric tolerance). An approximate search MUST NOT present its result as complete.

### E-3 Variable-size blocks and pruning

A WE-HDT Euclidean block MAY use adaptive partitions. Pruning a block for an exact query is permitted only when a proven lower bound exceeds the admissible query threshold. Adaptive splitting, merging, and two-phase candidate generation MUST preserve the declared exactness guarantee or downgrade the query's guarantee explicitly.

## 4. General metric index contract

A mathematical metric `d` over domain `X` satisfies:

1. `d(x,y) >= 0`;
2. `d(x,y) = 0` if and only if `x = y` under the descriptor's equality semantics;
3. `d(x,y) = d(y,x)`;
4. `d(x,z) <= d(x,y) + d(y,z)`.

A metric descriptor MUST either provide a proof/known construction supporting these properties or declare the properties as empirically checked but **unproven**. Empirical sampling alone is insufficient to assert universal metric validity. A pseudometric (distinct objects can have zero distance) MUST be labeled separately. If triangle inequality is unavailable, triangle-based pruning MUST NOT be used as a correctness-preserving optimization.

### M-1 Metric query guarantees

Metric radius and nearest-neighbor queries MUST state the same exactness categories as Euclidean queries. Exact metric pruning requires a justified bound, such as a triangle-inequality-derived bound. A learned embedding MAY be indexed in Euclidean space while the *semantic* comparison remains non-Euclidean; the system MUST distinguish retrieval-space distance from target-space distance and validate any claimed recall.

### M-2 Version changes

Changing metric parameters, calibration, embedding model, or equality semantics creates a new perspective version. An index built against an older version MUST NOT be silently reused as though equivalent. Compatibility may be established by an explicit migration or proof-backed transformation.

## 5. Relational, similarity, and directional contracts

These perspective types do not inherit metric axioms.

- **Relational:** typed edges or predicates, potentially temporal, uncertain, many-to-many, and provenance-bearing.
- **Directional:** ordered score `s(a,b)` that may differ from `s(b,a)`; examples include influence, preference, causal hypotheses, or directional evidence.
- **Similarity:** a comparison score whose range and interpretation are specified, without assuming metric conversion.

A relational index MUST declare edge direction, cardinality, identity references, predicate semantics, temporal validity, and evidence source. A directional query MUST retain argument order. A missing relation MUST NOT be treated as a negative fact unless the perspective explicitly declares a closed-world assumption. Causal claims MUST NOT be inferred from association or edge direction alone.

Graph traversal, predicate lookup, and score-based candidate ranking MAY serve as indexes, but any pruning or threshold guarantees MUST be justified under the corresponding relation contract, not borrowed from metric geometry.

## 6. Cross-perspective query and WE-HDT routing

WE-HDT is a *logical* hybrid structure. A physical implementation MAY use multiple indexes, a shared tree, a graph store, a database, or external services. A metric leaf is a logical intelligence address, not necessarily a physical tree leaf.

A conforming cross-perspective query MUST specify:

1. **Intent:** exact selection, approximate discovery, exploratory ranking, or hypothesis generation.
2. **Perspective plan:** descriptors and versions used, with any Euclidean-first optimization marked optional.
3. **Candidate policy:** whether the initial stage can exclude eligible entities.
4. **Resolution policy:** how candidate evidence, identity, and conflicting perspectives are reconciled.
5. **Output guarantee:** completeness/soundness where defined, otherwise an explicit uncertainty and coverage statement.

**Critical rule:** If phase one is incomplete, phase two cannot restore global recall without a compensating search path. An implementation MUST NOT claim exact global retrieval when an approximate or restricted first-stage candidate generator can exclude valid answers.

### 6.1 Two-phase search

`Phase A: candidate localization -> Phase B: metric/relational resolution -> evidence-bearing result`.

Euclidean-first is a strategy, not a universal requirement. A purely relational entity MAY enter through relational lookup. A query planner MAY use multiple candidate generators and union their results. A planner MUST report when its strategy is heuristic and may omit candidates.

### 6.2 Two-Ways CCC feedback

Forward CCC applies explicit conditions to candidates; backward CCC uses unresolved mismatches, weak evidence, or residuals to propose additional perspectives or queries. Feedback MUST distinguish `observation`, `inference`, and `hypothesis`. New perspectives MUST pass SPEC-001 registration and relevant validation before being used as correctness-critical filters.

## 7. Minimal interface contracts

The following pseudotypes are illustrative and not a required wire protocol.

```yaml
PerspectiveIndexDescriptor:
  perspective_id: string
  perspective_version: string
  kind: euclidean | metric | similarity | directional | relational
  value_schema: object
  comparison_contract: object
  equality_semantics: object
  temporal_policy: object
  provenance_policy: object
  index_capabilities: [string]
  guarantee_policy: exact | bounded_approximate | best_effort
  validation_evidence_refs: [string]

IndexQuery:
  query_id: string
  perspective_refs: [id@version]
  query_kind: lookup | range | radius | knn | traversal | rank | hybrid
  parameters: object
  snapshot_ref: string
  requested_guarantee: exact | bounded_approximate | best_effort
  resource_budget: object

IndexResult:
  query_id: string
  entity_refs: [string]
  perspective_versions: [string]
  snapshot_ref: string
  achieved_guarantee: exact | bounded_approximate | best_effort
  candidate_coverage: object
  provenance_refs: [string]
  uncertainty: object
  residual_refs: [string]
  warnings: [string]
```

`registerPerspective`, `buildIndex`, `queryIndex`, `resolveAcrossPerspectives`, `applyIndexDelta`, `validateIndex`, and `deprecateIndex` MUST either return a typed success with evidence or a typed failure. Unsupported query types MUST fail explicitly, not degrade silently.

## 8. Identity, time, and evidence invariants

**I-01 Identity preservation.** Index insertion/removal MUST NOT itself change entity identity.

**I-02 Descriptor consistency.** A result MUST identify the descriptor version that governed retrieval.

**I-03 Temporal consistency.** A query MUST identify its snapshot or temporal interpretation; observations from incompatible times MUST not be merged without an explicit policy.

**I-04 Provenance preservation.** A derived relation or comparison MUST retain traceable evidence references.

**I-05 Missing-data honesty.** Unknown, absent, false, and not-applicable MUST remain distinguishable.

**I-06 Guarantee honesty.** Approximate or heuristic candidates MUST not be reported as exhaustive.

**I-07 Directionality preservation.** Reversing operands MUST not be assumed safe for directional comparisons.

**I-08 Metric eligibility.** Metric-specific pruning MUST not be applied to unvalidated nonmetric scores.

**I-09 Cross-perspective conflict.** Contradictory observations MUST be surfaced or resolved by a documented policy, never overwritten silently.

**I-10 Change auditability.** Index mutations MUST be traceable to input observations or authorized structural changes.

**I-11 Separation of claims.** Retrieval relevance, identity equivalence, and scientific validity MUST be separately represented.

**I-12 Termination/resource control.** Exploratory backward search MUST obey budget and stop policies.

## 9. Index deltas and CDE integration

Index maintenance is a **Structural Delta**, not automatically a World Delta. A new observation may induce an **Observation Delta**, followed by a **Knowledge Delta** and a reindexing Structural Delta. An entity may also change in the world without immediate observation. These changes MUST remain distinguishable.

Proposed CDE-compatible operations:

| Delta | Preconditions | Required postcondition |
|---|---|---|
| `ADD_INDEX_ENTRY` | Valid entity and descriptor | Entry retrievable under declared semantics |
| `REMOVE_INDEX_ENTRY` | Authorized removal and temporal policy | No unintended deletion of entity history |
| `SPLIT_BLOCK` | Partition invariant holds | Coverage preserved; no duplicate identity side effects |
| `MERGE_BLOCKS` | Compatible descriptor/snapshot | Coverage and query guarantees preserved |
| `REBUILD_INDEX` | New descriptor version or index policy | Old/new versions auditable; migration explicit |
| `ADD_PERSPECTIVE` | Registered descriptor and validation | No unapproved upgrade to exact filtering |
| `ROLLBACK_STRUCTURE` | Reversible structural change | Index state restored; world facts unchanged |

CDE's path-memory and cycle policies are configurable. In particular, D-BTP's no-delta-reuse rule MUST NOT be imposed as a universal WE-SIO invariant; adversarial and cyclic domains (e.g., chess) require different policies.

## 10. Failure taxonomy

Implementations SHOULD expose structured failures including:

- `INVALID_DESCRIPTOR`, `INVALID_COORDINATE`, `UNIT_MISMATCH`;
- `METRIC_AXIOM_UNVERIFIED`, `UNSAFE_PRUNING_RULE`;
- `STALE_INDEX_VERSION`, `SNAPSHOT_MISMATCH`;
- `UNKNOWN_RELATION_NOT_FALSE`, `DIRECTION_REVERSED`;
- `INCOMPLETE_CANDIDATE_SET`, `UNSUPPORTED_EXACT_GUARANTEE`;
- `IDENTITY_AMBIGUOUS`, `EVIDENCE_MISSING`;
- `BUDGET_EXCEEDED`, `CROSS_PERSPECTIVE_CONFLICT`.

Failure results SHOULD include the triggering query, descriptor version, evidence references, and recovery suggestion. Sensitive provenance MAY be access-controlled while remaining auditable by authorized evaluators.

## 11. Conformance test matrix

Each test requires a fixture, an expected oracle, observed output, and an archived result. A test passing on one fixture does not prove universal correctness.

| ID | Test | Expected result |
|---|---|---|
| CT-001 | Same entity, multiple perspective indexes | Stable entity identity across results |
| CT-002 | Euclidean coordinates with mixed units | Reject or explicitly normalize |
| CT-003 | Euclidean exact radius vs brute-force oracle | Equal eligible result set within tolerance |
| CT-004 | Variable-size block split/merge | Coverage and exact result preservation |
| CT-005 | Nonmetric score violating triangle inequality | No metric-specific exact pruning |
| CT-006 | Symmetric metric vs asymmetric directional score | Correct classification and operand order |
| CT-007 | Pseudometric with distinct zero-distance entities | No forced identity merge |
| CT-008 | Missing relational edge under open-world semantics | Return unknown, not false |
| CT-009 | Relation traversal with time validity | Correct snapshot-sensitive edges |
| CT-010 | Approximate phase-one candidate omission | No false exact-global claim |
| CT-011 | Non-Euclidean-only entity | Reachable by appropriate relational/metric path |
| CT-012 | Cross-perspective conflicting evidence | Conflict exposed with provenance |
| CT-013 | Perspective descriptor upgrade | Explicit version migration/rebuild |
| CT-014 | Concurrent observation and structural changes | Declared snapshot/consistency policy respected |
| CT-015 | Learned embedding vs target metric | Retrieval-space and target-space scores distinguished |
| CT-016 | Unauthorized index delta | Rejected without entity mutation |
| CT-017 | Backward CCC creates candidate perspective | Marked hypothesis pending validation |
| CT-018 | Budget exhaustion during exploratory search | Typed partial result and termination |
| CT-019 | Duplicate entity across indexes | Deduplication by identity policy, not score equality |
| CT-020 | Index rollback | Restores index state without asserting world reversal |

### 11.1 Required baselines

For small deterministic fixtures, compare exact queries against brute-force enumeration. For larger experiments, compare with appropriate established baselines (e.g., k-d tree, R-tree, metric tree, graph index, SQL indexes, vector ANN), matched by query type and guarantee. Measure build time, update cost, memory, latency, recall, precision, and provenance completeness. Performance comparisons MUST report hardware, data distribution, query mix, tuning budget, and statistical uncertainty.

## 12. Research hypotheses (unvalidated)

- **H-INDEX-01:** Hybrid routing improves workload-weighted efficiency over single-index baselines for sufficiently heterogeneous perspectives, without reducing declared correctness.
- **H-INDEX-02:** Perspective-adaptive variable-size blocks reduce unnecessary refinement under nonuniform data density.
- **H-INDEX-03:** Explicit separation of candidate generation and evidence-based resolution improves auditability of cross-perspective results.
- **H-INDEX-04:** Residual-triggered backward CCC increases discovery of useful overlooked perspectives compared with fixed-query baselines, after controlling for false discoveries.
- **H-INDEX-05:** Typed delta/version contracts reduce silent index inconsistency under evolving perspectives.

These are hypotheses, not established outcomes. Negative results MUST be retained.

## 13. Validation roadmap

**Phase 0 — Contract review:** agree on equality semantics, descriptor schemas, temporal policies, and failure taxonomy.  
**Phase 1 — Deterministic fixtures:** execute CT-001–CT-020 with oracle-backed small datasets.  
**Phase 2 — Comparative indexing:** evaluate exact and approximate modes separately against established index families.  
**Phase 3 — Cross-perspective workflows:** exercise Two-Ways CCC, MLIU and residual registries on heterogeneous synthetic or public datasets.  
**Phase 4 — Evolution stress tests:** test descriptor revisions, CDE block deltas, rollbacks, adversarial/cyclic workloads, and reproducibility.  
**Phase 5 — Collective relay:** publish conformance results, counterexamples, unresolved residuals, and versioned decisions.

No phase may substitute an illustrative example for evidence of general effectiveness.

## 14. Collective Learning research trace

Every substantial change to an index contract SHOULD create or update a trace entry:

```yaml
trace_id: string
artifact: SPEC-002
claim_or_change: string
perspective_ids: [string]
status: proposed | tested | rejected | revised | accepted_with_scope
supporting_evidence_refs: [string]
counterexample_refs: [string]
conformance_test_refs: [string]
decision_ref: string
unresolved_residual_refs: [string]
next_research_question: string
```

Trace destinations:

- `research-trace/HYPOTHESIS-REGISTRY.md`
- `research-trace/DEFINITION-REGISTRY.md`
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`
- `research-trace/DECISION-LOG.md`
- `research-trace/UNRESOLVED-RESIDUALS.md`

## 15. Open questions and explicit leftovers

1. Which formal equivalence criteria permit safe reuse of indexes across descriptor versions?
2. How should uncertainty propagate through approximate candidate generation and exact second-stage resolution?
3. Can cross-perspective routing be optimized without conflating ranking with completeness?
4. What are minimal provenance requirements for privacy-preserving, distributed relay?
5. How should learned, nonstationary similarities be indexed while retaining honest guarantees?
6. When does a candidate relation warrant a new perspective descriptor rather than a local hypothesis?
7. How should multi-agent WE-HDT reconcile incompatible snapshots and identity scopes?
8. What operational tests best distinguish explanatory gain from merely adding dimensions?
9. Can variable-intelligence blocks improve end-to-end resource use once validation overhead is counted?
10. What failures of this specification should trigger a revision of the minimal semantic kernel itself?

## 16. Related WE-SIO artifacts

- `docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`
- `docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`
- `docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md`
- `docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`
- `docs/WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md`
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`
- `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`
- `specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md`
- `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`

## 17. Closing principle

**Index what can be justified, distinguish what cannot yet be compared, and preserve what remains unexplained.**

WE-SIO's proposed hybrid indexing framework should be judged not by its breadth of vocabulary, but by the clarity of its contracts, the validity of its retrieval guarantees, its handling of counterexamples, and its ability to relay reproducible evidence to future researchers.

---

*Research draft v0.1.0. This document specifies proposed interfaces and test obligations; it does not claim implementation, experimental validation, clinical utility, or universal optimality.*
