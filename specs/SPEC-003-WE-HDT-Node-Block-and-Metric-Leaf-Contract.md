# SPEC-003 — WE-HDT Node, Block, and Metric-Leaf Contract

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Status:** Candidate specification / research contract  
**Version:** 0.1.0  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Repository path:** `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`

> **Normative status.** MUST, MUST NOT, SHOULD, and MAY express proposed conformance requirements for implementations claiming this candidate contract. They do not imply that the underlying research hypotheses have been empirically validated.

## 1. Purpose and scope

This specification defines interoperable, testable contracts for three distinct but cooperating constructs in a World Entity Hybrid Differential Tree (WE-HDT): **index nodes**, **adaptive blocks**, and **metric-leaf intelligence units (MLIUs)**. It specifies identifiers, interfaces, invariants, versioning, evidence handling, resource budgets, failure semantics, and conformance tests. It does not prescribe a particular storage engine, machine-learning model, agent framework, or physical tree topology. The updated contract additionally specifies **Mask-First active computational views**, mature-structure preservation, and explicit separation of activation, knowledge, and structural changes.

WE-HDT combines candidate localization, perspective-aware resolution, and optional intelligence operations. An index node is a routing or retrieval construct; a block is a managed partition or grouping with independently adjustable granularity and capability; an MLIU is a logical intelligence interface scoped to an entity or entity set and a perspective. **An MLIU need not be a physical leaf, and a block need not host an agent.**

## 2. Dependencies and terminology

- **SPEC-001:** World Entity identity and perspective descriptor contract.
- **SPEC-002:** Euclidean, metric, and relational index conformance.
- **WE-SIO-003:** WE-HDT architecture.
- **WE-SIO-004:** Adaptive variable-intelligence blocks.
- **WE-SIO-005:** Metric-leaf intelligence and SI operations.
- **WE-SIO-011:** Minimal kernel, contracts, and definition evolution.

**EntityRef:** stable reference to an entity identity under a declared identity authority and version policy.  
**PerspectiveRef:** reference to a versioned measurement, metric, similarity, directional, or relational descriptor.  
**Node:** logical index/routing unit with explicit coverage and guarantee metadata.  
**Block:** partition or grouping managed by an adaptation policy.  
**MLIU:** logical interface for scoped SI operations, evidence, residuals, and relay.  
**Snapshot:** consistent view of entity data, perspective definitions, and index versions.  
**Residual:** recorded discrepancy between an expectation and observation, not automatically a discovery.  
**Conformance:** satisfaction of declared contracts under an explicit profile.

## 3. Design principles

1. **Entity ≠ representation ≠ index.** Identity survives permissible index reorganization.
2. **Index topology ≠ intelligence abstraction.** The two may be mapped but MUST NOT be conflated.
3. **Partition granularity ≠ capability level.** They MAY adapt independently.
4. **Euclidean-first is optional.** Non-Euclidean and relational entry points MUST remain representable.
5. **No silent guarantee upgrade.** Approximate candidates MUST NOT be advertised as exact global answers.
6. **Evidence precedes epistemic promotion.** Hypotheses and residuals remain distinct from validated claims.
7. **Conformance before runtime.** Operations have explicit preconditions, postconditions, and failure modes.
8. **Explicit leftovers.** Unresolved conflicts and unanswered questions remain addressable relay artifacts.
9. **Mask is not mutation.** Task-scoped activation changes MUST NOT silently modify persistent structure or epistemic records.
10. **Unknown is not residual.** Missing knowledge is not qualified discrepancy evidence without an explicit baseline and comparator.

## 4. Logical architecture and separation of concerns

```text
Query / Question / Observation
             |
       Query Planner
             |
   +---------+----------+
   |                    |
Index Node Graph    Perspective Registry
   |                    |
Adaptive Blocks -----+--+----> MLIU Registry
   |                             |
Candidate Sets              SI Operations
   +------------+----------------+
                |
       Evidence + Residual Registry
                |
       CDE / Adaptation Control
                |
       Versioned Research Relay
```

The diagram is a logical dependency map, not a mandatory physical execution sequence. A query MAY start from a relational index, a known MLIU, or an existing residual. A physical implementation MAY flatten, distribute, or virtualize the components if it preserves their observable contracts.

## 5. Common envelope

Every externally addressable node, block, and MLIU record MUST provide the following common fields, or an equivalent losslessly mapped representation:

| Field | Meaning | Requirement |
|---|---|---|
| `id` | Stable logical identifier within its namespace | MUST |
| `kind` | `index_node`, `adaptive_block`, or `mliu` | MUST |
| `schemaVersion` | Contract schema version | MUST |
| `revision` | Monotonic or causally ordered record revision | MUST |
| `createdAt`, `updatedAt` | Event timestamps with declared clock semantics | MUST |
| `snapshotRef` | Relevant data/registry snapshot or consistency token | MUST |
| `perspectiveRefs` | Versioned perspective descriptors used | MUST, possibly empty |
| `provenance` | Source and transformation lineage | MUST |
| `status` | Lifecycle state | MUST |
| `extensions` | Namespaced optional extension fields | MAY |

A record MUST NOT silently change the meaning of an existing `id`; migration or identity resolution MUST be explicit. An absent observation MUST NOT be represented as a measured zero.

## 6. Index node contract

### 6.1 Candidate schema

```json
{
  "id": "node:spatial:042",
  "kind": "index_node",
  "schemaVersion": "0.1.0",
  "revision": 7,
  "createdAt": "2026-11-05T00:00:00Z",
  "updatedAt": "2026-11-05T00:00:00Z",
  "snapshotRef": "snapshot:17",
  "nodeType": "euclidean_partition",
  "perspectiveRefs": ["perspective:position@3"],
  "coverage": {"type": "bounded_region", "regionRef": "region:42"},
  "children": ["node:spatial:043", "node:spatial:044"],
  "blockRefs": ["block:42"],
  "candidateGuarantee": "exact_under_declared_predicate",
  "pruningContractRef": "pruning:euclidean@2",
  "provenance": {"source": "index-build:17"},
  "status": "active"
}
```

### 6.2 Required semantics

- `nodeType` MUST distinguish Euclidean, general-metric, relational/directional, and hybrid routing semantics; implementations MAY define additional types.
- `coverage` MUST identify the population or search domain represented by the node, with explicit completeness or approximation qualifications.
- `candidateGuarantee` MUST be one of `exact_under_declared_predicate`, `approximate_with_characterized_recall`, or `unspecified`; stronger guarantees require supporting tests and assumptions.
- A pruning rule MUST state its mathematical assumptions, including metric axioms where applicable. Directional relations MUST NOT inherit triangle-inequality pruning without a separate proof.
- A node MAY link to blocks and MLIUs but MUST NOT treat an MLIU reference as evidence of physical leaf placement.
- Cycles in a logical routing graph MUST be detected or governed by an explicit termination policy; a tree-only profile MAY prohibit cycles.

### 6.3 Node operations

| Operation | Preconditions | Postconditions / failure |
|---|---|---|
| `route(query, snapshot)` | Compatible perspective and snapshot | Candidate child/block refs with guarantee; else `INCOMPATIBLE_PERSPECTIVE` |
| `enumerateCoverage(snapshot)` | Authorized scope | Coverage declaration; else `COVERAGE_UNKNOWN` |
| `validatePruning(predicate)` | Declared pruning contract | Proof/test evidence or `UNVERIFIED_PRUNING` |
| `rebuild(delta, policy)` | Authorized structural delta | New revision and lineage, or rollback |
| `retire(reason)` | Replacement or retention policy | Tombstone/redirect; no silent disappearance |

## 7. Adaptive block contract

### 7.1 Block semantics

An adaptive block groups references for localization, storage, execution, or intelligence orchestration. **Membership policy and capability policy are independent dimensions.** A block MAY cover a Euclidean region, metric neighborhood, relational community, temporal cohort, or explicit set. Overlap is allowed only when declared and when deduplication semantics are defined.

```json
{
  "id": "block:42",
  "kind": "adaptive_block",
  "schemaVersion": "0.1.0",
  "revision": 3,
  "createdAt": "2026-11-05T00:00:00Z",
  "updatedAt": "2026-11-05T00:00:00Z",
  "snapshotRef": "snapshot:17",
  "perspectiveRefs": ["perspective:position@3"],
  "membership": {"mode": "predicate", "predicateRef": "predicate:region42@1"},
  "overlapPolicy": "declared_overlap_with_deduplication",
  "capabilityProfileRef": "capability:resolve-and-question@1",
  "resourceBudget": {"computeUnits": 100, "maxDepth": 4},
  "adaptationPolicyRef": "policy:avib@1",
  "mliuRefs": ["mliu:42:a"],
  "provenance": {"source": "partition:17"},
  "status": "active"
}
```

### 7.2 Adaptation operations

- `split(block, partitionPlan)`: MUST preserve or explicitly characterize coverage and membership semantics; MUST return child mappings and provenance.
- `merge(blocks, mergePlan)`: MUST declare overlap, conflicts, deduplication, and any change in guarantees.
- `reindex(block, perspectiveVersion)`: MUST preserve snapshot compatibility or return a version conflict.
- `activateCapability(block, capability, budget)`: MUST check authorization, budget, and dependencies before activation.
- `deactivateCapability(block, capability)`: MUST preserve durable evidence and residual references required by retention policy.
- `delegate(block, task, target)`: MUST propagate scope, authorization, guarantee, and provenance.
- `rollback(adaptationId)`: MUST distinguish reversible structural changes from irreversible world actions.
- `mask(block, taskContext, policyRef)`: MUST create a task-scoped active computational view without silently modifying durable membership or identity.
- `unmask(view, scope)`: MUST expand eligible computation only within the caller’s authorization and declared guarantees.
- `remask(view, feedback)`: MUST produce a traceable revised selection with version checks and completeness handling.

The adaptation controller SHOULD evaluate density, heterogeneity, uncertainty, task relevance, observed benefit, and cost. Any scoring function is a configurable heuristic, not a universal optimality theorem.

### 7.3 Coverage conservation

For a disjoint partition, the union of child coverage SHOULD equal parent coverage under the same snapshot. If the representation allows overlap, the contract MUST state how duplicate candidates are handled. If coverage is intentionally lost by approximation or filtering, that loss MUST be explicitly reflected in the retrieval guarantee.

## 8. Metric-Leaf Intelligence Unit contract

### 8.1 Logical definition

An MLIU is an addressable, perspective-scoped intelligence interface that can attach observations, hypotheses, evidence, uncertainty, residuals, and questions to entities or entity groups. It MAY be implemented as a lightweight record, shared service, deferred computation, or specialized agent. It MUST NOT require one heavyweight agent per leaf.

```json
{
  "id": "mliu:42:a",
  "kind": "mliu",
  "schemaVersion": "0.1.0",
  "revision": 2,
  "createdAt": "2026-11-05T00:00:00Z",
  "updatedAt": "2026-11-05T00:00:00Z",
  "snapshotRef": "snapshot:17",
  "entityRefs": ["entity:example:9"],
  "perspectiveRefs": ["perspective:response@2"],
  "metricOrRelationContractRef": "contract:response@2",
  "observationRefs": ["observation:18"],
  "hypothesisRefs": ["hypothesis:4"],
  "evidenceRefs": ["evidence:18"],
  "uncertaintyRef": "uncertainty:18",
  "residualRefs": ["residual:11"],
  "openQuestionRefs": ["question:8"],
  "supportedOperations": ["locate", "resolve", "relate", "infer", "question", "evolve"],
  "resourceBudget": {"computeUnits": 40, "maxRelayHops": 3},
  "relayInterfaces": ["relay:research@1"],
  "provenance": {"source": "observation-pipeline:2"},
  "status": "active"
}
```

### 8.2 Six SI operations

| Operation | Input | Required output | Key guardrail |
|---|---|---|---|
| **Locate** | Entity/perspective/query scope | Addressable references and coverage metadata | No invented identity or completeness |
| **Resolve** | Candidate refs and evidence | Perspective-scoped interpretation with uncertainty | No silent hypothesis-to-fact promotion |
| **Relate** | Two or more refs and relation descriptor | Typed, directional relation with evidence | Preserve direction, time, and scope |
| **Infer** | Premises, rule/model, evidence | Qualified inference, assumptions, confidence semantics | Distinguish inference from observation |
| **Question** | Residuals, uncertainty, objectives | Candidate question and validation plan | No claim that question is validated |
| **Evolve** | Proposed representation/structure delta | Authorized plan, checks, resulting revision or rejection | CDE constraints, provenance, rollback policy |

Every operation MUST return an explicit status, provenance, snapshot reference, resource usage or estimate, and a guarantee/uncertainty declaration appropriate to its output. Operations MAY return `unsupported` rather than fabricate capability.

### 8.3 Operation result envelope

```json
{
  "operationId": "operation:77",
  "operation": "question",
  "status": "completed_with_open_residuals",
  "snapshotRef": "snapshot:17",
  "outputRefs": ["question:8"],
  "evidenceRefs": ["evidence:18"],
  "residualRefs": ["residual:11"],
  "guarantee": "candidate_hypothesis_only",
  "resourceUsage": {"computeUnits": 5},
  "provenance": {"operator": "mliu:42:a", "contractVersion": "0.1.0"}
}
```

## 9. Cross-component mapping contracts

1. **Node → Block:** routing MUST specify candidate scope and retrieval guarantee.
2. **Block → MLIU:** activation MUST pass authorized entity scope, perspective versions, and resource budget.
3. **MLIU → Node/Block:** an intelligence finding MAY request reindexing but MUST NOT mutate an index without an authorized structural delta.
4. **Perspective registry → all components:** incompatible descriptor revisions MUST be detected; reinterpretation requires explicit migration.
5. **Residual registry → MLIU/CDE:** residuals MAY trigger questions and adaptation proposals, but MUST NOT automatically validate new metrics.
6. **Relay → external systems:** transmitted records MUST retain source identity, evidence references, status, and unresolved limitations.

A cross-perspective mapping MUST declare whether it is exact, lossy, heuristic, learned, or unknown. Composition of mappings MUST NOT claim a stronger guarantee than justified by the components and their assumptions.

## 10. Two-phase retrieval and Two-Ways CCC

**Forward path:** query → eligible index routing → candidate set → metric/relational resolution → qualified result → residual capture.  
**Reverse path:** residual or failed condition → candidate question → alternative perspective or index proposal → validation → optional authorized revision.

For an exact retrieval profile, the candidate stage MUST be a superset of all true matches under the declared query predicate and snapshot. If candidate generation is approximate, the result MUST expose that qualification even if the second-stage resolver is exact on the candidates it receives. A reverse-discovery path MUST have explicit budgets, termination criteria, and human or automated governance gates appropriate to the action.

## 11. Consistency, versioning, and concurrency

- A query MUST identify its consistency model: snapshot, bounded staleness, eventual, or another declared profile.
- Results spanning multiple perspective versions MUST expose the mixed-version condition or fail safely.
- Node/block/MLIU updates MUST preserve causal lineage; a revision MAY be represented by a vector clock or event sequence where a single integer is inadequate.
- Concurrent split/merge or capability changes MUST resolve conflicts explicitly, not silently overwrite divergent changes.
- Deletion MUST distinguish logical tombstoning, retention, and legally required erasure; provenance retention is subject to applicable privacy and security constraints.
- Index changes MUST NOT be misrepresented as physical-world changes. Rollback of a representation does not reverse an external event.

## 12. Failure and uncertainty semantics

| Code | Meaning |
|---|---|
| `INCOMPATIBLE_PERSPECTIVE` | Requested perspective is unavailable or incompatible |
| `SNAPSHOT_CONFLICT` | Components refer to incompatible versions |
| `COVERAGE_UNKNOWN` | Completeness cannot be established |
| `UNVERIFIED_PRUNING` | Pruning assumptions lack proof or tests |
| `RESOURCE_BUDGET_EXCEEDED` | Computation or relay budget exhausted |
| `AUTHORIZATION_DENIED` | Operation exceeds delegated scope |
| `AMBIGUOUS_ENTITY` | Identity resolution remains unresolved |
| `EVIDENCE_INSUFFICIENT` | Inference or evolution cannot be promoted |
| `ADAPTATION_CONFLICT` | Structural change violates a constraint |
| `CYCLE_LIMIT_REACHED` | Exploration encountered a declared termination bound |

Failure results MUST preserve enough context to diagnose and, where appropriate, relay the unresolved issue. Unknown, missing, disputed, and zero-valued data MUST remain distinguishable.

## 13. Security, governance, and resource control

MLIU operations MAY be computationally expensive or involve sensitive data. Implementations MUST enforce scoped authorization for observation access, inference, relay, and structural evolution. They SHOULD support privacy-preserving evidence references, audit trails, budget ceilings, loop detection, and human review for high-impact changes. Evidence references MUST NOT bypass source access controls. Multi-agent relay MUST propagate permissions and MUST NOT silently escalate capability.

## 14. Conformance profiles

| Profile | Minimum scope |
|---|---|
| **P0 — Representation** | Common envelope, identity/perspective refs, provenance, status |
| **P1 — Index** | P0 + node routing, coverage, pruning, retrieval guarantee |
| **P2 — Adaptive Block** | P1 + membership, split/merge, capability/budget separation |
| **P3 — MLIU Operations** | P0 + declared SI operation contracts and evidence handling |
| **P4 — Integrated WE-HDT** | P1 + P2 + P3 + cross-component versioning and relay |
| **P5 — Research Evolution** | P4 + residual-driven proposals, CDE governance, definition trace |

A system MUST declare the profiles it claims. Support for a higher profile does not excuse nonconformance with the lower-level dependencies listed for that profile.

## 15. Candidate conformance tests

| ID | Test | Expected result |
|---|---|---|
| CT-001 | Reorganize an index without changing entity identity | Identity refs remain stable |
| CT-002 | Use an MLIU that is not a physical tree leaf | Valid logical attachment |
| CT-003 | Query a non-Euclidean-only entity | No mandatory Euclidean path |
| CT-004 | Apply triangle-inequality pruning to directional relation | Rejected unless independently justified |
| CT-005 | Approximate candidate set with exact resolver | Overall guarantee remains approximate |
| CT-006 | Split a block with complete disjoint coverage | Child union equals parent coverage |
| CT-007 | Merge overlapping blocks | Deduplication and conflict policy enforced |
| CT-008 | Change block capability without changing membership | Membership preserved |
| CT-009 | Change membership without changing capability | Capability contract preserved or explicitly migrated |
| CT-010 | Activate capability beyond budget | Explicit resource failure |
| CT-011 | Resolve under mismatched perspective versions | Conflict or declared migration |
| CT-012 | Infer with missing evidence | Qualified uncertainty or failure |
| CT-013 | Promote residual to validated metric without tests | Rejected |
| CT-014 | Run Question with a cycle-prone relay | Bounded termination or cycle policy |
| CT-015 | Evolve index without authorization | Rejected; no mutation |
| CT-016 | Roll back index revision after external world action | Index restored; world action not claimed undone |
| CT-017 | Delegate task to another MLIU | Scope, budget, provenance preserved |
| CT-018 | Delete/retire node with active references | Tombstone/redirect or explicit failure |
| CT-019 | Represent missing observation and measured zero | Distinct states |
| CT-020 | Concurrent split and merge on same snapshot | Deterministic conflict resolution or rejection |
| CT-021 | Query mixed-version distributed partitions | Declared consistency and guarantee |
| CT-022 | Export a research relay with unresolved questions | Questions and limits retained |

These are **candidate** tests. A runtime suite must specify fixtures, predicates, expected datasets, and measurable pass/fail criteria before claiming verified conformance.

## 16. Reference validation scenarios

### 16.1 Spatial localization with relational resolution

Use a spatial partition to produce candidate transit stops, then resolve reachability over a directed network. The spatial index cannot substitute for directed travel-time semantics. Record unreachable candidates and mismatched expectations as qualified residuals.

### 16.2 Clinical treatment-response heterogeneity

Group de-identified observations into a cohort block; attach an MLIU to a versioned response perspective; record model residuals and candidate explanatory questions. No hypothesis is a clinical conclusion without suitable study design, confounding controls, independent validation, and governance.

### 16.3 Chess as a structural evolution boundary test

Represent positions, legal transitions, and evaluators as perspective-scoped records. Repeated moves or states may be legal; universal No-Delta-Reuse is therefore not a WE-HDT or CDE axiom. The applicable cycle and path-memory policies must be explicit.

### 16.4 SQL-backed World Entities

Use primary keys for identity and SQL indexes for physical acceleration, while WE perspective descriptors supply additional semantics. A column is not automatically a mathematical metric; schema migration must preserve identity and version lineage.

## 17. Research hypotheses and evaluation metrics

**H1 — Adaptive allocation:** Joint block and capability adaptation can reduce resource use at comparable retrieval/inference quality relative to fixed partitions and fixed capability assignment.  
**H2 — Logical MLIUs:** Shared or lazily activated MLIUs can provide comparable task quality to per-leaf agents at lower cost.  
**H3 — Explicit guarantees:** Typed retrieval guarantees reduce false claims of completeness in hybrid search.  
**H4 — Residual relay:** Preserving unresolved residuals improves reproducibility and useful follow-up question generation.  
**H5 — Contract-based evolution:** Versioned CDE adaptation reduces invalid structural changes compared with unconstrained mutation.

Suggested metrics: exact recall against an exhaustive oracle, approximate recall@k, latency distributions, memory/compute cost, capability activation rate, version-conflict rate, provenance completeness, residual triage precision, and conformance pass rate. All comparisons SHOULD include matched workloads, ablations, confidence intervals where applicable, and failure cases.

## 18. Definition evolution and research relay

A proposed contract revision SHOULD record:

```text
Change ID | prior definition | triggering case/counterexample
new definition | affected invariants | migration impact
new conformance tests | evidence | unresolved residuals
```

The definition evolution loop is:

```text
Minimal kernel → Application → Counterexample / Residual
       → Contract revision → Regression tests → Relay
```

Revision MAY narrow, split, or reject a proposed abstraction; evolution is not synonymous with expansion. Maintain links to `research-trace/DEFINITION-REGISTRY.md`, `COUNTEREXAMPLE-REGISTRY.md`, `DECISION-LOG.md`, and `UNRESOLVED-RESIDUALS.md` when those artifacts are available.

## 19. Open questions and explicit leftovers

1. What is the minimal observable MLIU contract that remains useful without collapsing into an ordinary function wrapper?
2. Which workloads justify an adaptive intelligence block rather than a conventional index plus external service?
3. How should overlapping and fuzzy membership be represented without overstating completeness?
4. Can a general query planner compare Euclidean, metric, and relational plans with calibrated uncertainty?
5. Which parts of residual triage should be local to an MLIU versus centralized?
6. How should cross-perspective learned mappings expose drift, fairness, and out-of-distribution behavior?
7. What is the least costly consistency model adequate for multi-agent relay?
8. How can conformance evidence itself be shared across independent implementations?
9. When does a structural adaptation warrant a new perspective descriptor version rather than a node revision?
10. What falsifying results would justify simplifying or abandoning WE-HDT integration?

## 20. Recommended next work

1. Define machine-readable schemas and fixtures for P0–P3.
2. Build an exhaustive small-dataset oracle for hybrid retrieval guarantees.
3. Compare fixed blocks, adaptive blocks, and adaptive capabilities in controlled ablations.
4. Implement a lightweight MLIU adapter over an existing SQL or graph store.
5. Connect residual and adaptation events to a versioned research-trace registry.
6. Use SPEC-004 to formalize the Six SI Operations and Two-Ways CCC interoperability contract.

## 21. Related documents

- `docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`
- `docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`
- `docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md`
- `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md`
- `docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`
- `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`
- `specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md`
- `specs/SPEC-002-Euclidean-Metric-and-Relational-Index-Conformance.md`
- `specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md`

---

**Research principle:** Define the invariant, not the inventory. Preserve not only successful results, but also their assumptions, provenance, counterexamples, and unresolved questions.

**License intent:** Apache-2.0 (subject to the repository's `LICENSE`).

---


## 22. Mask-First active computational view contract (2026-11-05 update)

This extension formalizes the proposed Mask-First Structural Intelligence (MFSI) layer from `EXT-005` and its WE-HDT/AVIB/MLIU implementation boundary. A mature, versioned substrate can serve many transient task-specific execution views. A Mask is a **selection policy over eligible computation**, not an entity identity, a scientific conclusion, a persistent index mutation, or an authorization grant.

### 22.1 Typed mask and active view

```yaml
MaskPolicy:
  maskId: stable-id
  policyVersion: version
  substrateSnapshotRef: snapshot-id
  taskRef: task-id
  perspectiveRefs: []
  selection:
    nodeRefs: []
    blockRefs: []
    metricOrRelationRefs: []
    edgeOrPredicateRefs: []
    allowedOperations: []
    depthLimit: optional
  budget: {compute: declared, memory: declared, externalCalls: declared}
  authorizationContextRef: access-policy-and-principal
  guaranteeMode: exact | conservative | approximate
  fallbackPolicy: full-view | expand | fail-closed | declared-approximation
  provenance: {generatorRef: versioned, inputs: [], evidenceRefs: []}
  expirationOrInvalidation: declared

ActiveComputationalView:
  viewId: stable-id
  maskPolicyRef: versioned-reference
  substrateSnapshotRef: snapshot-id
  effectiveSelectionRef: versioned-reference
  declaredGuarantees: []
  resourceUsage: {maskBuild: measured, execution: measured, fallback: measured}
  validationStatus: untested | checked | invalidated
```

The schema is illustrative. Implementations MAY use sparse bitmaps, predicate programs, learned gates, hierarchical masks, or delegated services, provided observable semantics remain equivalent under the declared profile.

### 22.2 Normative requirements

- **MASK-001 — Nonmutation:** `mask`, `unmask`, and `remask` MUST NOT silently change entity identity, node/block membership, persistent topology, stored observations, or knowledge status.
- **MASK-002 — Authorization:** effective selection MUST be intersected with existing access-control constraints. `unmask` MUST NOT expand permissions; SQL row/column security and source restrictions remain authoritative.
- **MASK-003 — Exact coverage:** a view claiming exact retrieval MUST be provably coverage-safe for its query contract or invoke an equivalent verified fallback. Unknown recall MUST NOT be represented as exactness.
- **MASK-004 — Guarantee preservation:** pruning and metric assumptions MUST derive from declared perspective contracts; a relational or directional score MUST NOT inherit Euclidean/metric pruning without proof.
- **MASK-005 — Snapshot coherence:** all view references MUST identify compatible versions of source data, topology, perspective descriptors, and relevant access policy, or return a version conflict.
- **MASK-006 — Invalidation:** cached masks MUST be revalidated or invalidated when relevant evidence, schema, permissions, topology, or perspective semantics change.
- **MASK-007 — Evidence visibility:** a view advertised as evidence-complete MUST preserve required negative, contradictory, and provenance evidence; omitted evidence MUST be disclosed for approximate exploration.
- **MASK-008 — Resource accounting:** comparative performance MUST include mask generation, compilation, caching, invalidation, fallback, and adaptation overhead.
- **MASK-009 — Traceable remasking:** a remask MUST record its predecessor, feedback trigger, revised policy, decision rationale, and validation outcome.
- **MASK-010 — Safe degradation:** if a selected service is unavailable or exceeds budget, the implementation MUST preserve durable evidence and MUST either use a declared fallback or return an explicit incomplete/error result.

### 22.3 Operation contracts

```text
mask(substrateRef, task, perspectiveRefs, policy, auth) -> ActiveView | Error
unmask(activeViewRef, requestedScope, auth)       -> ActiveView | Denied
remask(activeViewRef, feedback, policyVersion)    -> ActiveView | Conflict
execute(activeViewRef, query, guaranteeMode)      -> Result + Audit | Error
validateMask(activeViewRef, referenceOracle)      -> CoverageReport
```

Each operation MUST specify preconditions, resource budget, output guarantees, and failure semantics. A mask policy MAY be learned, but learned selection alone is not proof of coverage or safety.

## 23. Mature-structure preservation and Delta typing

A candidate adaptation preference is **Mask before Rebuild; Reuse before Regenerate; Validate before Promote**. This is a testable heuristic, not a universal invariant: stale, corrupt, unsafe, or structurally incompatible substrates MAY require immediate rebuilding.

| Change type | Affects | Does not by itself imply |
|---|---|---|
| `ActivationDelta` | Task-scoped selected nodes, relations, operations, budgets | New knowledge or persistent topology mutation |
| `KnowledgeDelta` | Evidence, hypothesis status, validated claims | Physical world change or block split |
| `StructuralDelta` | Persistent partition, index topology, service organization | Improved inference quality or changed entity identity |
| `WorldOrSourceStateDelta` | External event or source-data mutation | Automatically validated epistemic explanation |

- **DELTA-001:** the change log MUST type every material delta and record its target and version.
- **DELTA-002:** an activation-only operation MUST NOT increment a persistent structural revision solely because a transient mask changed; policy versions MAY advance independently.
- **DELTA-003:** structural changes MUST preserve declared coverage, identity, authorization, and evidence-reference invariants or explicitly downgrade guarantees.
- **DELTA-004:** knowledge promotion/withdrawal MUST follow `SPEC-005`; it MUST NOT be implemented as an unreviewed side effect of `remask` or `split`.
- **DELTA-005:** CDE MAY coordinate proposed transitions and rollback, but application-specific cycle/path constraints MUST be declared. A reversible record operation does not reverse an irreversible world event.

## 24. MLIU epistemic interfaces and RER boundary

An MLIU MAY expose three logically distinct interfaces without requiring separate physical stores:

```yaml
MLIUEpistemicInterfaces:
  establishedKnowledgeViewRef: versioned-and-scoped
  openKnowledgeViewRef: versioned-and-scoped
  residualEvidenceRegistryRef: versioned-and-scoped
  maskPolicyRefs: []
  activeViewRefs: []
  promotionAuthorityRef: declared
```

- **EPI-001:** established knowledge MUST retain perspective, applicability scope, supporting evidence, and version; it is revisable, not absolute.
- **EPI-002:** open knowledge MUST distinguish missingness, provisional hypotheses, contested claims, and untested questions where relevant.
- **EPI-003:** RER admission MUST satisfy the explicit baseline, observation, comparator, and provenance conditions of `SPEC-005`. **Unknown ≠ Residual.**
- **EPI-004:** `Locate`, `Resolve`, `Relate`, `Infer`, `Question`, and `Evolve` MUST declare which knowledge view(s) they read or write and whether they operate under an exact or approximate mask.
- **EPI-005:** a mask MUST NOT silently promote an open hypothesis to established knowledge or manufacture a qualified residual from missing data.
- **EPI-006:** shared MLIUs and relayed mask policies MUST preserve data-access restrictions and source dependence; agreement between agents is not independent evidence.

## 25. Additive conformance fixtures

The tests below supplement, rather than renumber, existing tests in this specification. The `MCT` prefix avoids collision with `SPEC-005`'s `CT-029`–`CT-042`.

| ID | Fixture | Expected result |
|---|---|---|
| MCT-001 | Mask a subset, inspect persistent node/block revision | No silent structural mutation |
| MCT-002 | Exact query with excluded valid candidate | Coverage proof fails; safe fallback or explicit failure |
| MCT-003 | Approximate query with intentionally pruned candidates | Recall/completeness status disclosed |
| MCT-004 | Unmask a restricted SQL column | Access denied; no leakage |
| MCT-005 | Change perspective definition after mask caching | Mask invalidated/revalidated |
| MCT-006 | Use asymmetric relation with metric pruning | Rejected unless guarantee proved |
| MCT-007 | Remask under compute budget exhaustion | Explicit degraded/fallback outcome |
| MCT-008 | Unknown fact without comparison baseline | Open knowledge, not RER |
| MCT-009 | Validated residual with expectation and observation | RER qualification and lineage retained |
| MCT-010 | Change only active view | ActivationDelta, not StructuralDelta |
| MCT-011 | Split block under overlapping membership | Coverage and deduplication verified |
| MCT-012 | Relay learned mask across incompatible schema | Reject or revalidate before use |
| MCT-013 | Mask hides contradictory evidence in evidence-complete mode | Conformance failure |
| MCT-014 | Compare masked/full-view cost | Include generation, fallback, and cache overhead |

**Suggested profiles:** `Mask-Core` (MASK-001,002,005,006,009; MCT-001,004,005), `Mask-Exact` (Mask-Core plus MASK-003,004,007; MCT-002,006,013), `Mask-Operational` (Mask-Exact plus MASK-008,010; MCT-003,007,014), and `MLIU-Epistemic` (EPI-001–006; MCT-008,009,012). Profile adoption is optional; claims MUST identify the exact profile and tests passed.

## 26. Evaluation program and research limitations

**P0 — Contract correctness:** synthetic trees, overlapping blocks, relational-only entities, adversarial missingness, authorization tests, and exhaustive small-dataset retrieval oracles.

**P1 — Mask efficiency:** compare full-view execution, static expert masks, adaptive/learned masks, and structural reindexing at matched correctness. Measure end-to-end latency, memory, mask-generation overhead, recall, cache invalidation, and fallback rate.

**P2 — Mature-structure retention:** controlled changing-workload experiments measuring reconstruction frequency, structural churn, transfer performance, stale-path failures, and any operational forgetting.

**P3 — Epistemic governance and relay:** independent residual qualification, knowledge promotion audits, shared mask transfer across schema changes, and negative controls for correlated evidence.

Proposed falsifiable hypotheses include `WEH-031` (net mask efficiency), `WEH-032` (mature-pathway retention), `WEH-033` (epistemic classification), and `WEH-034` (validated mask-policy transfer). These are research hypotheses, not results.

**Explicit leftovers:** efficient proof of coverage for learned masks; policy compilation cost; nonstationary workload drift; mask-driven selection bias; uncertainty preservation across perspective translations; source-level authorization changes; and the conditions where immediate reconstruction is better than reuse.

**Integration references:** `EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`, `EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`, `WE-SIO-004`, `WE-SIO-005`, `WE-SIO-007`, and `SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`.

**Research status:** candidate interface specification only; no certified implementation or empirically demonstrated performance advantage is asserted.
