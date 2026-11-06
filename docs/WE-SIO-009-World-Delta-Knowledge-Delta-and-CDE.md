# WE-SIO-009 — World Delta, Knowledge Delta, and Constrained Delta Evolution

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Hypothesis / Collective Learning Relay  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Conceptual architecture; not an experimentally validated implementation

## Abstract

World Entity (WE) systems must reason about changes in the world, changes in observations, changes in what an intelligent system believes, and changes in its own indexing and operational structures. Treating all of these as one undifferentiated *delta* invites false causal conclusions, inconsistent state updates, and unsafe adaptation. This paper develops a typed delta model distinguishing **World Delta**, **Observation Delta**, **Knowledge (Epistemic) Delta**, and **Operational/Structural Delta**. It proposes an integration with **Constrained Delta Evolution (CDE)** in which transitions are explicit, evidence and provenance are preserved, constraints are testable, and reversibility is qualified rather than presumed. The model connects WE-HDT indexing, Metric-Leaf Intelligence Units (MLIUs), residual registries, Two-Ways CCC, perspective discovery, and Collective Learning Relay. All claims about generality and performance remain hypotheses pending conformance tests and comparative evaluation.

**Keywords:** World Entity, World Delta, Epistemic Delta, Knowledge Delta, Observation Delta, Constrained Delta Evolution, WE-HDT, residual, provenance, temporal modeling, structural intelligence.

## 1. Motivation: One Word, Several Different Changes

Consider four events:

1. A vehicle physically moves to a new location.
2. A delayed sensor packet reveals where the vehicle was ten minutes ago.
3. A model revises its estimate of the vehicle's route after comparing contradictory reports.
4. A retrieval system reorganizes its spatial blocks to improve query latency.

All four may appear as changes to a database or tree. Only the first is necessarily a change in the external world. The second changes the evidence available to the system; the third changes a belief or representation; the fourth changes an implementation structure. A WE-SIO system must not infer physical change merely because its representation changed.

**Foundational distinction:** *World change is not the same as knowledge change; knowledge change is not the same as index change.*

This distinction is especially important in a system that is designed to discover new perspectives. A newly recognized relation may have existed for years before the system could represent it.

## 2. Scope and Epistemic Commitments

WE-SIO does not assume direct, complete access to an objective world state. World Delta is therefore a **model-level category for a hypothesized or externally established change in the referent**, not a claim that every change can be observed without uncertainty.

The framework commits to:

- preserving entity identity independently of index keys;
- distinguishing event time, observation time, and model-update time;
- retaining the provenance and uncertainty of change assertions;
- allowing multiple, conflicting perspectives without forced premature reconciliation;
- recording residuals when predicted and observed outcomes disagree;
- separating semantic correctness from indexing and runtime optimization;
- retaining failed hypotheses and explicit unresolved leftovers.

It does **not** claim that CDE replaces established event sourcing, temporal databases, Bayesian filtering, graph databases, or planning algorithms. The research question is whether typed deltas and cross-layer conformance provide useful integration across those established techniques.

## 3. A Minimal Typed Delta Vocabulary

Let `e` denote a persistent entity reference, `p` a perspective descriptor, and `t` a time index. A conceptual WE representation is:

\[
R_t(e) = \{(p_i, v_i, q_i, \tau_i, \pi_i)\}_{i=1}^{n_t}
\]

where `v` is a value or relation, `q` captures uncertainty or quality, `τ` captures temporal semantics, and `π` is provenance. This is a representation, not the entity itself.

### 3.1 World Delta (ΔW)

A **World Delta** is a change in the external referent or its relationships, *as asserted under a stated observational or causal model*.

Examples: a bridge closes; a vehicle moves; a patient receives a treatment; a contractual relationship begins. A change assertion should identify the source and whether it is observed, inferred, or merely hypothesized.

### 3.2 Observation Delta (ΔO)

An **Observation Delta** is a change in the evidence stream available to the system, including newly received data, corrected measurements, late-arriving records, or retracted reports.

An observation can describe an old world event. Therefore `observed_at` and `valid_at` must not be conflated.

### 3.3 Knowledge / Epistemic Delta (ΔK)

A **Knowledge Delta** changes the system's representation, hypotheses, confidence, explanatory structure, or accepted perspectives.

Examples: revising a route hypothesis; discovering that two records refer to the same entity; learning a previously missing metric; downgrading confidence in a causal explanation. ΔK may occur with **ΔW = 0** over the period in question.

### 3.4 Operational / Structural Delta (ΔS)

A **Structural Delta** changes internal execution or representation machinery: a WE-HDT split or merge, index rebuild, MLIU activation, cache invalidation, relay routing, or capability allocation. Some structural changes also carry semantic changes, so each delta must declare which state components it affects.

### 3.5 The four-way distinction

| Delta | Primary referent | Example | Common validation question |
|---|---|---|---|
| ΔW | External entity or relationship | Vehicle moves | What evidence establishes the event? |
| ΔO | Available observations | Delayed sensor packet | Is the report authentic and temporally aligned? |
| ΔK | Model, beliefs, perspectives | Route estimate revised | Is the revision justified and calibrated? |
| ΔS | Index, capability, execution | WE-HDT block split | Are semantics and query results preserved? |

These types can interact; they are not mutually exclusive descriptions of an entire workflow. One event may produce a chain of typed deltas.

## 4. A Causal and Temporal Chain

A typical update path is:

```text
World event (possibly unobserved)
          │
          ▼
Observation / evidence ingestion ──► ΔO
          │
          ▼
Entity resolution and perspective interpretation
          │
          ▼
Knowledge revision ────────────────► ΔK
          │
          ├──► Residual registry / hypothesis questions
          │
          ▼
Index and capability maintenance ──► ΔS
          │
          ▼
WE-HDT / MLIU query and reasoning services
```

A change in ΔO does not guarantee a change in ΔK; an untrusted report may be rejected. A ΔK need not require a ΔS if the existing index remains valid. A ΔS may be triggered solely by workload pressure, with no new evidence. Conversely, a real-world change may remain unknown until evidence arrives.

### 4.1 Time axes

At minimum, track:

- `valid_time`: when an assertion applies to the modeled world;
- `observation_time`: when an observation was made;
- `ingestion_time`: when the system received it;
- `decision_time`: when a knowledge revision was accepted;
- `index_version_time`: when an operational view was published.

Bitemporal database conventions can support part of this, but the WE-SIO research contract also records *why* a revision occurred and which perspectives were affected.

## 5. Minimal CDE Kernel and Optional Policies

CDE is treated as a **candidate constrained state-evolution framework**, not as a universal algorithm proven to outperform existing search methods. A useful minimal formulation is:

\[
\mathcal{E} = (S, \mathcal{D}, A, T, P)
\]

where `S` is the state space, `D` the family of delta descriptions, `A(s,δ)` an applicability predicate, `T(s,δ)` a partial or nondeterministic transition relation, and `P` the evolution and selection policy. Constraints and evidence obligations are specified through contracts associated with each application.

A deterministic instance may use:

\[
T : (S,\delta) \rightharpoonup S'
\]

A nondeterministic or adversarial instance may instead use a relation `T ⊆ S × D × S`. Neither transition form alone guarantees convergence, termination, optimality, or scientific validity.

### 5.1 Typed delta envelope

```yaml
delta_id: unique-event-or-transition-id
delta_type: WORLD | OBSERVATION | KNOWLEDGE | STRUCTURAL
entity_refs: [entity-id]
perspective_refs: [perspective-id]
base_state_version: version-or-snapshot-ref
valid_time: time-or-interval
recorded_at: timestamp
preconditions: explicit-applicability-contract
operation: typed-change-description
evidence_refs: [source-or-observation-id]
uncertainty: confidence-or-uncertainty-model
provenance: origin-and-transformation-chain
postconditions: expected-invariants
rollback_policy: reversible | compensating | nonreversible
status: proposed | accepted | rejected | superseded
```

This envelope is illustrative, not a frozen serialization standard. Distinct delta types may require additional fields.

### 5.2 Reversibility is not universal

An index split can often be undone; a belief revision may be rolled back to an earlier model version; a treatment administered to a patient cannot simply be reversed. **Undoing a record is not undoing the world.** For nonreversible operations, use compensating actions or explicit irreversibility declarations.

### 5.3 Path memory and cycles

Earlier D-BTP-style *No-Delta-Reuse* rules are valid in some permutation/search settings but are **not universal CDE invariants**. Chess and recurrent physical processes permit repeated moves or revisited states. CDE should expose configurable `CyclePolicy`, `PathMemoryPolicy`, `TerminationPolicy`, and, where applicable, `AdversarialPolicy`.

## 6. WE-HDT Integration

A WE-HDT may maintain several coordinated structures:

1. **Identity layer** — stable entity references and resolution history.
2. **Perspective descriptors** — metric, similarity, directional, or relational semantics.
3. **Candidate localization layer** — Euclidean or other index-appropriate search structures.
4. **Metric/relational resolution layer** — richer comparisons, constraints, and interpretation.
5. **MLIU layer** — logical intelligence operations and evidence handling.
6. **Residual and relay layer** — unexplained discrepancies, hypotheses, and traceable updates.

The layers need not correspond to physical tree levels. Euclidean-first is an optional optimization, not a universal entry requirement.

### 6.1 ΔW → affected representations

An accepted world-event assertion may invalidate cached perspective values or relationship edges. The system should record an *impact set* of affected entity/perspective pairs, without assuming every index must be rebuilt.

### 6.2 ΔK → perspective evolution

Knowledge changes may add, split, merge, recalibrate, or deprecate a perspective. Query plans should be version-aware: results computed under a previous perspective definition must not silently masquerade as results under a new definition.

### 6.3 ΔS → semantics-preserving maintenance

Splitting an adaptive block should preserve candidate completeness for supported exact queries. Approximate retrieval may relax completeness only under an explicit approximation contract. Performance claims require measurement against baselines.

## 7. Metric-Leaf Intelligence Units as Delta Consumers and Producers

The six proposed SI operations connect to typed deltas:

| Operation | Delta interaction | Required guardrail |
|---|---|---|
| Locate | Reads ΔS-maintained indices | Completeness/approximation contract |
| Resolve | Reads ΔO and ΔK | Entity identity and ambiguity trace |
| Relate | Produces candidate ΔK | Relation semantics and evidence |
| Infer | Proposes ΔK | Uncertainty, provenance, counterexamples |
| Question | Opens residual-driven proposals | Distinguish hypothesis from fact |
| Evolve | Requests ΔK or ΔS | Authorization, conformance, rollback policy |

MLIUs are logical units and need not each host an autonomous agent. Shared services and lazy capability activation can reduce operational cost.

## 8. Two-Ways CCC and Residual-Driven Evolution

A forward pathway evaluates known perspectives and predicts or retrieves candidate outcomes. A backward pathway begins with a discrepancy and asks which missing condition, relation, or perspective could explain it.

```text
Known perspectives + evidence
           │ forward CCC
           ▼
Expected outcome / candidate resolution
           │ compare
           ▼
Residual (observation - expectation)
           │ reverse CCC
           ▼
Candidate condition / metric / relation
           │ independent validation
           ▼
Accepted ΔK (or rejected hypothesis)
           │ constrained maintenance
           ▼
Optional ΔS, updated WE-HDT and relay trace
```

A residual is evidence of a *model-observation gap*, not automatically evidence of a new physical law. Noise, selection bias, sensor failure, temporal misalignment, confounding, and model misspecification are alternative explanations that must be tested.

## 9. Three Worked Scenarios

### 9.1 Moving vehicle with late-arriving evidence

At 10:00, a vehicle moves from A to B (candidate ΔW). A sensor observation made at 10:01 arrives at 10:12 (ΔO). At 10:13, entity resolution accepts the observation and revises the vehicle's trajectory model (ΔK). At 10:14, an affected spatial index is updated (ΔS). The query *“Where was it at 10:05?”* must use valid time and evidence status rather than simply returning the newest database value.

**Failure mode:** confusing ingestion time with world-event time creates a false movement sequence.

### 9.2 Clinical treatment-response residuals

Treatment administration may be a world event. New laboratory results are observations. A model may revise a patient's predicted response (ΔK), and the research system may generate a candidate stratification perspective. The hypothesis must undergo data-quality checks, confounder analysis, leakage prevention, appropriate statistical testing, and external validation before clinical use.

**Failure mode:** treating an observational association or model residual as a validated causal treatment rule. WE-SIO is a research architecture, not a medical decision system.

### 9.3 Chess as a definition stress test

A chess move changes the formal game state (a world-state transition *within the modeled game*). A player's evaluation function may change independently (ΔK). A search tree may be rebuilt (ΔS). Repetition of moves or positions can be legal and strategically important. Thus any universal prohibition on delta reuse would reject valid trajectories. This case motivates application-specific cycle policies and adversarial evaluation contracts.

**Failure mode:** importing a D-BTP path uniqueness constraint into all CDE applications.

## 10. Delta Composition and Conflict

Typed deltas may be composed only when their preconditions, target versions, and semantic effects are compatible. A candidate composition is:

\[
\delta_b \circ \delta_a : S \to S''
\]

when `δa` is applicable at `S`, `δb` is applicable after `δa`, and the combined transition preserves required invariants. Commutativity must not be assumed: a perspective redefinition followed by an index rebuild is not necessarily equivalent to the reverse order.

Conflict examples include:

- two observations disagree about the same event time;
- two knowledge revisions rely on incompatible entity-resolution assumptions;
- an index rebuild targets a stale perspective version;
- a proposed metric change invalidates previously accepted comparisons.

A conflict registry should retain both claims, provenance, adjudication status, and the reasons for any resolution. Some conflicts should remain open rather than be silently overwritten.

## 11. Candidate Conformance Contracts

**C-01 — Delta typing:** every accepted change declares its semantic type(s).  
**C-02 — Identity preservation:** entity identity is not replaced by a mutable index key.  
**C-03 — Temporal separation:** event/valid, observation, and recording times remain distinguishable.  
**C-04 — Evidence trace:** world and knowledge assertions identify supporting evidence or explicit assumptions.  
**C-05 — Version consistency:** updates declare the base version they modify.  
**C-06 — Transition applicability:** invalid preconditions fail explicitly.  
**C-07 — Rollback semantics:** reversible, compensating, and irreversible changes are differentiated.  
**C-08 — Index semantics:** structural optimization preserves declared retrieval semantics.  
**C-09 — Perspective versioning:** comparisons specify the descriptor version used.  
**C-10 — Residual preservation:** unexplained discrepancies are not silently deleted by model updates.  
**C-11 — Conflict visibility:** contradictory evidence remains traceable.  
**C-12 — Cycle policy:** path-memory and termination rules are application-scoped.  
**C-13 — Budget and authorization:** autonomous evolution respects resource and governance limits.  
**C-14 — Relay trace:** decisions, rejected proposals, and explicit leftovers are exportable.

These are proposed contracts. Formal verification, implementation details, and empirical conformance suites remain future work.

## 12. Testable Research Hypotheses

| ID | Hypothesis | Proposed evaluation | Potential falsifier |
|---|---|---|---|
| H-009-01 | Typed deltas reduce false causal interpretations of updates | Annotated temporal-event benchmark | No reduction versus well-designed temporal baselines |
| H-009-02 | ΔK/ΔS separation improves reproducibility | Replay identical evidence across index versions | Results remain inconsistent without explanation |
| H-009-03 | Explicit provenance improves conflict resolution | Multi-source entity resolution tasks | No measurable improvement in adjudication quality |
| H-009-04 | Residual-triggered ΔK proposals improve discovery recall | Controlled hidden-relation datasets | No gain after controlling for false discoveries |
| H-009-05 | Constrained structural deltas improve maintenance efficiency | Compare full rebuild vs incremental updates | Overhead exceeds benefits at target workloads |
| H-009-06 | Configurable cycle policies broaden CDE applicability | Chess and recurrent-process tests | Valid trajectories still incorrectly rejected |
| H-009-07 | Delta replay supports Collective Learning Relay | Cross-agent reproducibility tasks | Trace cannot reconstruct decisions or assumptions |

All comparisons require matched resources, clearly specified metrics, multiple seeds where relevant, and disclosure of negative results.

## 13. Validation Roadmap

**Phase A — Semantic fixtures.** Build small deterministic examples covering late evidence, no-world-change knowledge revisions, index-only updates, and conflicting observations.

**Phase B — Contract tests.** Test identity, versioning, temporal ordering, rollback, cycle policies, and index invariants. Include intentionally malformed delta records.

**Phase C — Comparative baselines.** Compare against event-sourced systems, temporal SQL, standard incremental indexing, and appropriate probabilistic or graph models. Do not claim novelty for already established primitives.

**Phase D — Discovery experiments.** Evaluate whether residual-to-perspective evolution adds explanatory or operational value beyond ordinary feature engineering and model selection.

**Phase E — Relay and reproducibility.** Export the full evidence-to-decision trace, replay it with independent agents, and record disagreements and unresolved residuals.

## 14. Definition Evolution and Research Trace

Consistent with WE-SIO-011, the delta taxonomy is a **minimal working semantic kernel**, not a closed inventory of all possible changes. New applications may expose additional types (e.g., policy delta, normative delta, agent-goal delta) or require splitting an existing type. Such changes must pass a Definition Evolution Loop:

```text
Definition version → Application → Counterexample
        ↑                               │
        └── Regression + conformance ← Revision proposal
```

The following repository artifacts should capture the research history:

- `research-trace/HYPOTHESIS-REGISTRY.md` — IDs, claims, status, evidence.
- `research-trace/DEFINITION-REGISTRY.md` — delta terminology and revisions.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md` — failure cases and boundary tests.
- `research-trace/DECISION-LOG.md` — accepted/rejected changes and rationale.
- `research-trace/UNRESOLVED-RESIDUALS.md` — open discrepancies and next tests.

**Research principle:** *Define the invariant, not the inventory.* The purpose of traceability is not to conceal uncertainty, but to make it useful for subsequent researchers and agents.

## 15. Interfaces to the Broader SI Research Program

- **SIF:** WE-HDT and CDE are candidate complementary Localization/Addressing pillars; SIF can govern routing, control, and structural growth.
- **CDE / D-BTP:** CDE supplies a candidate language for constrained transitions; D-BTP provides a more specialized path-search origin whose constraints must not be generalized uncritically.
- **UCPSF:** scoring and control-plane mechanisms can evaluate competing delta proposals under multiple perspectives.
- **AQSI:** autonomous questioning can turn residuals into structured research questions.
- **UIERU:** relay mechanisms can exchange evidence, proposed changes, and reproducibility traces across agents.
- **SSI:** self-modeling agents may track changes in their own beliefs and capabilities; this does not establish subjective experience.
- **WE-SIO-002/003/005/006/007/008:** the representation, WE-HDT, MLIU, CCC, residual, and perspective-evolution layers are the immediate technical dependencies.

## 16. Open Questions and Explicit Leftovers

1. What is the smallest delta kernel that adds operational value beyond ordinary state-transition notation?
2. When can a World Delta be asserted, rather than merely hypothesized, from incomplete evidence?
3. How should the system represent simultaneous, conflicting, or partially ordered observations?
4. What consistency model is appropriate for distributed WE-HDT replicas?
5. Which delta compositions are safe under concurrent perspective revisions?
6. How should evidence retractions propagate through previously accepted inferences?
7. What guarantees can be offered for approximate or probabilistic index maintenance?
8. When does adding a new perspective improve explanation rather than overfit residuals?
9. How should costs of replay, provenance, and rollback be budgeted?
10. Which parts of CDE can be formally verified, and which require empirical validation?
11. How should a self-modeling entity distinguish its own action effects from observation and belief changes?
12. How should Collective Learning reconcile contradictory traces from independent agents?

These are research questions, not implicit claims of solved functionality.

## 17. Proposed Figure Placement

**Fig-008 — World Delta vs Epistemic Delta** should appear after Section 4, with four parallel delta tracks and time axes.  
**Fig-003 — WE Hybrid Differential Tree** can support Section 6.  
**Fig-007 — Residual-Driven Scientific Discovery Loop** can support Section 8.  
**Fig-009 — Definition Evolution Loop** can support Section 14.

Figures are planned assets; this document does not assume that they already exist.

## 18. Conclusion

WE-SIO requires a disciplined distinction between the world, observations of the world, knowledge about the world, and the structures used to operate on that knowledge. Typed deltas provide a candidate way to maintain that distinction across WE-HDT, MLIU, Two-Ways CCC, residual-driven discovery, and perspective evolution. CDE may offer a unifying transition and governance vocabulary, provided its kernel remains minimal, its constraints remain application-specific, and its claimed advantages are tested against existing methods.

The central proposition is not that all change is the same. It is that **different kinds of change can be coordinated without erasing their differences**. Preserving those distinctions is a prerequisite for trustworthy structural learning and traceable Collective Learning Relay.

---

### Related WE-SIO documents

- `WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md`
- `WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`
- `WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`
- `WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md`
- `WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`
- `WE-SIO-007-Residual-First-Scientific-Discovery.md`
- `WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md`
- `WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`

**License intent:** Apache-2.0 (repository-level LICENSE governs).  
**Citation status:** Candidate research manuscript, v0.1.0; no DOI is asserted here.
