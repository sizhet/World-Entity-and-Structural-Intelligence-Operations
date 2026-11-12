# EXT-001 — WE-HDT as an SIF Localization Pillar

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research extension / candidate architecture  
**Status:** Hypothesis and interface proposal; not an implemented or benchmark-validated system  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot

## Abstract

This extension proposes **World Entity Hybrid Differential Trees (WE-HDT)** as a candidate pillar of **Localization and Addressing** within the **Structural Intelligence Framework (SIF)**. The central claim is architectural rather than empirical: a localization service should address not only *where* an entity or candidate is stored, but also *under which perspective*, *with what retrieval guarantee*, *through which evidence*, and *at which version of the world model*. WE-HDT combines optional Euclidean or numeric candidate localization with metric and relational resolution, adaptive blocks, and logically addressable Metric-Leaf Intelligence Units (MLIUs). It is intended to complement—not replace—other SIF localization methods, including **Constrained Delta Evolution (CDE)** for constrained search and state-space evolution. We define responsibilities, interfaces, invariants, counterexamples, and falsifiable experiments, while preserving unresolved design questions for Collective Learning Relay.

## 1. Scope and motivation

SIF treats localization/addressing as a functional domain connecting problems, capabilities, structural representations, and control decisions. Conventional indexes can efficiently locate records in a known representation; they do not by themselves decide which perspective is appropriate, whether a relation is directional, how evidence should be interpreted, or when a new perspective should be investigated. WE-SIO asks whether these concerns can be connected through explicit contracts without sacrificing retrieval correctness or operational clarity.

This document is **not** a claim that WE-HDT is a universally superior index, a universal ontology, or a proven SIF component. It specifies a research candidate and a pathway for validation.

### 1.1 Research questions

- Can one localization interface route across Euclidean, general-metric, and relational perspectives while preserving their distinct semantics?
- Can an entity be located in one perspective and resolved in another without conflating identity, representation, and index position?
- Can a localized unresolved difference become a traceable research question rather than being silently discarded?
- How should WE-HDT cooperate with CDE, which explores and evolves constrained states rather than merely retrieving indexed entities?
- What is the smallest SIF-compatible contract that yields operational value beyond ordinary database and search-system composition?

## 2. Conceptual boundaries

A **World Entity (WE)** is a modeled referent with an identity policy and one or more versioned representations. A **Perspective Descriptor** specifies a view, measurement, mathematical metric, similarity, directional score, or relation, including its domain and evidence semantics. An **Index** accelerates access under a declared perspective; it is not the entity or the perspective itself.

A **WE-HDT** is a proposed hybrid arrangement of candidate generators, perspective-specific resolvers, cross-perspective mappings, and optional intelligence-bearing logical leaves. “Tree” describes a possible structural organization, **not** a requirement that every resolver or MLIU be a physical tree leaf.

An **MLIU** is a logical, addressable capability/evidence unit that may support Locate, Resolve, Relate, Infer, Question, and Evolve. It need not be an autonomous agent; a lightweight record and shared services may suffice.

**Localization** finds eligible candidates, regions, states, or capability endpoints under an explicit contract. **Resolution** interprets candidates against richer constraints. **Discovery** proposes and tests previously missing perspectives or explanations. These are related but distinct operations.

## 3. SIF functional placement

A simplified conceptual arrangement:

```text
Problem / Question / Task
          |
          v
SIF Control Plane ----> Scoring / Governance / Resource Budget
          |
          v
Localization & Addressing Domain
  |-- Perspective Registry + Entity Identity Resolver
  |-- WE-HDT: indexed candidate localization and cross-perspective resolution
  |-- CDE: constrained state-space exploration and structural delta evolution
  |-- Other locators: SQL, graph, vector, symbolic, external services
          |
          v
Node / MLIU / Capability Dispatch
          |
          v
Evidence, Residuals, Two-Ways CCC, Validation, Relay
          |
          +----> Feedback to Control Plane and registries
```

This is a **logical interface diagram**. It does not prescribe one runtime, one physical tree, or one universal dispatch order. SIF may select multiple locators and reconcile their results.

### 3.1 Distinct responsibilities

| SIF concern | WE-HDT candidate contribution | Required boundary |
|---|---|---|
| Problem-to-capability mapping | Locate compatible entity/perspective/capability references | Do not equate nearest index entry with best capability |
| Localization/addressing | Generate candidates with explicit guarantees | Preserve completeness/approximation declarations |
| Node intelligence | Route to MLIU or shared inference service | No mandatory agent per leaf |
| Scoring/control | Supply evidence, uncertainty, cost, residuals | Control plane owns policy and authorization |
| Structural growth | Suggest reindexing, splits, new perspectives | Validate and authorize changes before promotion |
| Collective learning | Emit replayable trace and open questions | Separate observations from hypotheses |

## 4. A federated localization model

Let a query be represented as:

$$
Q=(\mathcal{E},P,C,G,B,V)
$$

where $\mathcal{E}$ is the entity scope, $P$ the perspective set, $C$ the conditions, $G$ the requested guarantee, $B$ the resource budget, and $V$ the version/snapshot policy. This notation is a **candidate specification**, not a proven minimal kernel.

A dispatcher selects locators $L_1,\ldots,L_n$, each returning candidates, guarantee metadata, evidence, and provenance:

$$
L_i(Q)\rightarrow(C_i,\gamma_i,E_i,T_i).
$$

A resolver combines or rechecks the results according to the declared semantics. Set union, intersection, ranking, and join are **not interchangeable**: they must be chosen from query semantics and locator guarantees.

### 4.1 Retrieval guarantee contract

A result must distinguish:

- **Exact and complete** for a declared query domain and snapshot.
- **Exact within candidates** but not globally complete.
- **Approximate**, with documented approximation assumptions or measured recall.
- **Exploratory**, suitable for hypothesis generation but not definitive exclusion.

For an exact query with true answer set $A(Q)$, a two-phase architecture using candidate set $C(Q)$ must establish $A(Q)\subseteq C(Q)$ before exact resolution can claim complete retrieval. A precise second stage cannot recover a valid entity omitted in the first stage.

### 4.2 Euclidean is optional

Euclidean-first can be efficient for suitable spatial/numeric workloads, but is neither a universal ontology nor an obligatory physical hierarchy. Non-Euclidean entities and relations may enter through graph, symbolic, general-metric, or other locators. Even numerical columns are not automatically Euclidean coordinates; units, scale, missingness, and distance semantics must be declared.

### 4.3 Mathematical metric versus relation

If a locator relies on metric pruning, the distance function must satisfy the relevant metric properties or explicitly justify weaker bounds. Similarity scores, asymmetric directional evidence, and causal relations must not silently inherit triangle-inequality-based pruning guarantees.

## 5. WE-HDT localization pipeline

A candidate operational pipeline is:

1. **Normalize and bind:** identify entity scope, identity policy, perspective descriptors, query time, and required guarantees.
2. **Select routes:** choose one or more eligible Euclidean, metric, relational, SQL, graph, or other index paths.
3. **Generate candidates:** record candidate sets and whether completeness is proven, estimated, or unknown.
4. **Resolve:** apply perspective-specific comparison and relational conditions, preserving directionality and provenance.
5. **Dispatch capabilities:** invoke MLIUs or shared services for inference, explanation, questioning, or further validation as authorized.
6. **Record residuals:** retain unexplained discrepancies with their observations, expectations, evidence, and model versions.
7. **Feedback:** let Two-Ways CCC propose new questions or perspectives; let the SIF control plane decide whether to schedule validation or CDE evolution.
8. **Relay:** publish traceable outputs, limitations, counterexamples, and explicit leftovers.

The pipeline may short-circuit when the query is simple; advanced discovery is not a prerequisite for ordinary retrieval.

## 6. WE-HDT and CDE: complementary SIF localization pillars

WE-HDT and CDE should be **cooperating methods**, not synonyms.

| Dimension | WE-HDT | CDE |
|---|---|---|
| Primary object | Indexed entities, perspectives, candidate sets, logical intelligence endpoints | States, admissible deltas, transition/evolution policies |
| Primary question | Where and under which perspective can relevant candidates be found/resolved? | Which constrained changes or paths lead to useful states? |
| Typical operation | Locate, filter, join, resolve, route | Generate, apply, evaluate, branch, prune, revise |
| Typical guarantee | Candidate coverage, index correctness, version consistency | Constraint preservation, transition validity, policy-specific completeness/termination |
| Natural outputs | Entity references, evidence, residuals, candidate capability endpoints | New states, search paths, structural changes, policies |
| Risk | False exclusions from inappropriate pruning | Search explosion, cycles, invalid transitions, premature pruning |

### 6.1 Cooperation patterns

**WE-HDT → CDE:** localization identifies a relevant entity cohort or state neighborhood; CDE explores admissible modifications, hypotheses, or candidate solutions within that scoped region.

**CDE → WE-HDT:** CDE proposes a validated split, merge, reindex, perspective activation, or routing change; WE-HDT updates its structural representation under a versioned transaction.

**Joint feedback:** a residual uncovered during WE-HDT resolution becomes a CDE search objective; CDE's resulting hypothesis returns for evidence validation and possible registry promotion.

**Control-plane arbitration:** SIF decides when to search, evolve, stop, defer, or escalate. No proposed locator may silently change the objective, identity semantics, or evidence standard.

### 6.2 The chess boundary test

Chess demonstrates why CDE's **No-Delta-Reuse** cannot be universal: legal moves and positions may recur, while castling rights, en passant, clocks, and repetition history can distinguish states. A **Path Memory Contract** and **Cycle Policy** must be configurable by domain. WE-HDT may index position features, but cannot infer full legal equivalence from a lossy board-only signature. This counterexample should remain in the definition regression suite.

## 7. Candidate interface contracts

The following are illustrative schema sketches; fields are provisional and not executable API commitments.

```yaml
LocalizationRequest:
  request_id: string
  entity_scope: string
  perspective_ids: [string]
  conditions: object
  guarantee_required: exact_complete | exact_within_candidates | approximate | exploratory
  snapshot_ref: string
  budget: {time_ms: integer, compute_units: number}
  evidence_policy: string
  authorization_ref: string

LocalizationResult:
  request_id: string
  entity_refs: [string]
  perspective_versions: [string]
  guarantee_delivered: string
  candidate_coverage_basis: string
  provenance_refs: [string]
  uncertainty: object
  residual_refs: [string]
  continuation_ref: string | null
```

```yaml
EvolutionProposal:
  proposal_id: string
  target_structure_ref: string
  delta_kind: split | merge | reindex | activate | retire | remap
  preconditions: [string]
  expected_benefit: object
  risk_and_cost: object
  evidence_refs: [string]
  validation_plan_ref: string
  rollback_plan_ref: string
  approval_state: proposed | approved | rejected | applied | reverted
```

### 7.1 Contract invariants

1. **Identity preservation:** an index key or learned embedding must not silently redefine entity identity.
2. **Perspective validity:** each comparison uses a declared descriptor, domain, and version.
3. **Guarantee honesty:** approximate or exploratory output must not be labeled globally complete.
4. **Evidence separation:** observation, inference, hypothesis, and validation decision remain distinguishable.
5. **Snapshot consistency:** cross-index joins identify time/version mismatch rather than hide it.
6. **Directional correctness:** asymmetric relations preserve source/target orientation.
7. **Authorized evolution:** a proposal is not an applied structural change.
8. **Rollback semantics:** reverting a model/index revision does not imply reversing a real-world event.
9. **Budget accounting:** delegated searches and discovery loops obey the control plane's limits.
10. **Traceability:** a published research claim links to its supporting and conflicting evidence, tests, and definition version.

## 8. Two-Ways CCC as a localization feedback bridge

**Forward direction:** a query and its conditions choose perspectives and locators, produce candidates, and resolve them against known constraints.

**Reverse direction:** a residual or unresolved candidate triggers questions such as “Was the relevant perspective omitted?”, “Is the metric inappropriate?”, “Was the snapshot stale?”, or “Does a relation need directional interpretation?”

The reverse direction generates **candidate questions and hypotheses**, not validated facts. Its outputs must be routed through evidence-quality checks, counterexample search, and independent validation before any perspective is promoted.

This feedback channel connects SIF Localization to AQSI-style autonomous questioning and CDE-style structural evolution without collapsing those functions into one opaque search procedure.

## 9. Worked examples

### 9.1 Spatial logistics and scheduling

A WE-HDT spatial locator returns vehicles and stops near a region, with a declared distance bound and snapshot. A relational resolver checks service eligibility, route restrictions, and temporal constraints. CDE explores feasible schedule deltas and vehicle assignments. The SIF control plane scores objectives such as fleet size, journey time, and fairness. A new schedule is a proposed plan, not evidence that the physical fleet has already changed.

### 9.2 Clinical research cohort exploration

A registry identifies records under explicit cohort and consent/governance constraints. Perspective-aware retrieval joins measurements, treatment events, and outcome observations. Residuals between expected and observed outcomes may trigger questions about confounding, measurement quality, subgroup heterogeneity, or omitted variables. These are **research hypotheses**, not clinical diagnoses or treatment recommendations; causal interpretation requires appropriate study design and independent validation.

### 9.3 Knowledge-system entity resolution

SQL keys, document mentions, and graph nodes may refer to the same real-world entity—or to distinct entities with similar attributes. WE-HDT returns candidate identity matches with provenance and uncertainty; a resolver applies identity policy. CDE may explore candidate merges/splits as **proposals**. A merge must not be committed solely because embeddings are close.

## 10. Baselines and falsifiable hypotheses

The appropriate comparison is not WE-HDT versus a straw-man “static index.” Use mature alternatives and ablations:

- SQL indexes and joins, spatial indexes such as R-trees, k-d trees, metric indexes, graph traversals, and vector retrieval, each on suitable workloads.
- A federated search baseline without MLIU or residual feedback.
- WE-HDT without adaptive blocks.
- WE-HDT without reverse CCC.
- WE-HDT without CDE-driven structural changes.

**H-EXT001-01 — Routing value.** On mixed-perspective queries, contract-aware dispatch improves at least one predeclared quality/cost measure over a strong federated baseline without violating correctness constraints.

**H-EXT001-02 — Residual value.** Traceable residual feedback increases independently validated useful follow-up hypotheses per unit of review effort relative to a matched baseline.

**H-EXT001-03 — Adaptive value.** Perspective-adaptive blocks reduce measured cost under heterogeneous workloads after including maintenance and adaptation overhead.

**H-EXT001-04 — CDE complementarity.** WE-HDT localization plus CDE exploration yields better constrained-search efficiency or solution quality on preselected tasks than either component alone, under equal budgets.

**H-EXT001-05 — Trace value.** Structured relay records reduce reproduction time and unsupported-claim rate in blinded handoff exercises.

All five are **untested hypotheses**. Negative results must be retained.

## 11. Conformance and validation plan

| ID | Test | Expected property |
|---|---|---|
| EXT001-T01 | Identity collision across sources | Distinct referents are not silently merged |
| EXT001-T02 | Euclidean exact range query | No false negatives under declared exact contract |
| EXT001-T03 | Nonmetric directional score | Metric pruning is rejected or explicitly disabled |
| EXT001-T04 | Non-Euclidean-only entity | Query can route without mandatory Euclidean stage |
| EXT001-T05 | Candidate omission injection | Global completeness claim fails visibly |
| EXT001-T06 | Snapshot skew | Version mismatch is detected and surfaced |
| EXT001-T07 | Perspective descriptor revision | Old and new results remain distinguishable |
| EXT001-T08 | MLIU service unavailable | Failure/partial result is explicit; no fabricated inference |
| EXT001-T09 | Reverse CCC suggestion | Output remains hypothesis until validation |
| EXT001-T10 | Unauthorized structural delta | CDE proposal cannot mutate live index |
| EXT001-T11 | Rollback after reindex | Previous index version recoverable without rewriting world history |
| EXT001-T12 | Chess repeated position | Path-memory policy handles legitimate cycles |
| EXT001-T13 | Resource exhaustion | Control plane enforces time/compute limits |
| EXT001-T14 | Counterexample relay | Reproduction steps and definition version are present |
| EXT001-T15 | Strong baseline comparison | Quality/cost measured under equal conditions |
| EXT001-T16 | Adverse results | Failed hypotheses and residuals are preserved |

### 11.1 Phased roadmap

**Phase A — Semantic contracts:** validate entity identity, perspective types, retrieval guarantees, and versioning with small synthetic datasets.

**Phase B — Locator interoperability:** compose SQL/spatial/graph or other existing locators without new intelligence; test exactness and failure behavior.

**Phase C — MLIU and reverse CCC:** introduce bounded questioning, residual registry, and provenance; assess hypothesis quality against independent review.

**Phase D — CDE integration:** propose and validate structural deltas; test rollback, oscillation control, and equal-budget benchmarks.

**Phase E — SIF relay evaluation:** test control-plane arbitration, reproducibility, collective handoff, and real-world workload generalization.

Progression is gated by conformance, not by a predetermined release calendar.

## 12. Counterexamples and failure modes

**CE-01: A purely symbolic entity.** A WE without meaningful Euclidean coordinates invalidates mandatory Euclidean-first routing. **Revision:** Euclidean localization is optional.

**CE-02: An asymmetric trust relation.** Treating directed trust as a symmetric metric can produce invalid pruning. **Revision:** typed relational descriptors and restricted pruning.

**CE-03: A stale candidate index.** An exact resolver operating on incomplete candidates misses valid entities. **Revision:** explicit candidate coverage proof or downgraded guarantee.

**CE-04: A spurious clinical residual.** Measurement error produces an apparent novel subgroup. **Revision:** independent validation and confounding checks before promotion.

**CE-05: Adaptation thrashing.** Frequent split/merge cycles consume more resources than they save. **Revision:** hysteresis, budgets, minimum dwell times, and reversible proposals.

**CE-06: CDE as ordinary graph search.** A weak CDE definition offers no distinctive benefit over a state-transition baseline. **Revision:** require measurable additional value, clear contracts, or narrower claims.

**CE-07: Self-model mistaken for subjective experience.** A self-referential WE model is incorrectly described as conscious. **Revision:** preserve functional/phenomenological distinction and defer unsupported claims.

**CE-08: Index-centric governance.** An index silently updates identity or evaluation policy. **Revision:** control-plane authority and auditable approvals.

## 13. Research-trace and Collective Learning Relay

Each substantial experiment or definition change should produce a relay record with:

```yaml
relay_id: string
research_question_ref: string
claim_or_hypothesis_ref: string
definition_version: string
implementation_or_dataset_ref: string
baseline_and_protocol_ref: string
observations_and_metrics: object
supporting_evidence_refs: [string]
conflicting_evidence_refs: [string]
counterexample_refs: [string]
limitations: [string]
decision: retain | revise | reject | unresolved
next_questions: [string]
reproduction_instructions_ref: string
```

Suggested repository destinations:

- `research-trace/HYPOTHESIS-REGISTRY.md`
- `research-trace/DEFINITION-REGISTRY.md`
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`
- `research-trace/DECISION-LOG.md`
- `research-trace/UNRESOLVED-RESIDUALS.md`

Preserve rejected proposals and failed benchmarks when they illuminate a boundary. An execution repeated with new evidence may itself be a useful relay, provided the provenance and changed observations are explicit.

## 14. Relationship to the WE-SIO corpus

- **WE-SIO-001–003:** origin, entity representation, and WE-HDT architecture.
- **WE-SIO-004–005:** adaptive blocks and MLIU operations.
- **WE-SIO-006–008:** Two-Ways CCC, residual-first discovery, and perspective evolution.
- **WE-SIO-009:** typed world/knowledge/structural deltas and CDE.
- **WE-SIO-010:** self-modeling boundary, without consciousness claims.
- **WE-SIO-011–012:** minimal kernels, definition evolution, and Collective Learning Relay.
- **SPEC-001–006:** identity, index, structural, operation, evidence, and research-trace contracts.
- **CASE-002:** strong k-d-tree comparison and variable-block baselines.
- **CASE-004:** chess as a CDE definition stress test.

A proposed figure is `figures/Fig-001-WE-SIO-Grand-Architecture.png`, supplemented by `Fig-003-WE-Hybrid-Differential-Tree.png` and `Fig-009-Definition-Evolution-Loop.png`. 

## 15. Explicit leftovers

1. What formal property distinguishes a useful WE-HDT from a well-engineered federation of conventional indexes?
2. What minimum perspective descriptor supports cross-system interoperability without excessive ontology requirements?
3. How can completeness guarantees compose across mixed exact, approximate, and relational stages?
4. When is an MLIU a genuine operational abstraction rather than a renamed service endpoint?
5. Which CDE evolution policies measurably outperform conventional adaptive indexing or search planning?
6. How should conflicting entity identities and contradictory perspectives be represented over time?
7. Can reverse CCC improve scientific discovery without increasing false-positive hypotheses or review burden?
8. What conformance profile is sufficient for a useful first implementation?
9. How should SIF allocate budgets between retrieval, exploration, and validation?
10. Which failure cases require narrowing WE-HDT's proposed SIF role?

## 16. Conclusion

WE-HDT is proposed as an **SIF Localization and Addressing pillar candidate** for perspective-aware entity retrieval, resolution, and intelligence dispatch. **CDE is a complementary localization/evolution pillar** for constrained state exploration and structural change. Their relationship is strongest when each keeps a distinct contract and both are governed by SIF's control plane, evidence standards, and research trace. The research contribution remains a hypothesis until interoperability, correctness, cost, and reproducibility are tested against strong baselines.

**Define the invariant, not the inventory. Preserve the counterexample, not merely the successful demonstration.**

---

*Research status: proposed architecture and test plan. No empirical performance or scientific-discovery claims are asserted as validated results.*
