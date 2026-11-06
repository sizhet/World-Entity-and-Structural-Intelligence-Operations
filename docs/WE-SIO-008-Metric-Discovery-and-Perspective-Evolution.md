# WE-SIO-008 — Metric Discovery and Perspective Evolution

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis and architecture proposal  
**Status:** Exploratory; specifications and empirical claims require independent validation  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

## Abstract

A World Entity (WE) can be represented through multiple perspectives, yet the perspectives available at any moment need not be complete. Existing measurements may fail to explain observations, differentiate entities, or support a particular task. This paper proposes a controlled process for **metric discovery and perspective evolution** within WE-SIO: preserve qualified discrepancies without conflating them with unknowns; propose candidate measurements, dissimilarities, directional relations, or relational descriptors; evaluate them against explicit semantic and empirical contracts; and revise perspective registries and search structures without confusing representation changes with changes in the world. The revised architecture separates Established Knowledge, Open Knowledge, and qualified Residual Evidence Registry (RER) records; uses Mask-First exploration where coverage-safe; and distinguishes Activation/Mask Delta from Knowledge and Structural Delta. The proposed process links Residual-First Scientific Discovery (WE-SIO-007), Two-Ways CCC (WE-SIO-006), Metric-Leaf Intelligence Units (WE-SIO-005), WE-HDT (WE-SIO-003), and Constrained Delta Evolution (CDE). The aim is a falsifiable architecture for learning *what to measure and how to represent it*, rather than an assertion that a new metric is always discoverable or scientifically meaningful.

## 1. Scope and research position

WE-SIO starts with the distinction:

- **Entity:** the referent whose identity is maintained under an explicit identity policy.
- **Representation:** a time- and evidence-dependent model of that referent.
- **Perspective:** a declared way to observe, compare, or relate entities.
- **Index:** an acceleration structure built over selected perspective outputs.

An index is not a perspective, and a perspective is not automatically a mathematical metric. The research problem is how an intelligence system can detect limitations of its current perspective set, propose additions or revisions, test them, and safely propagate accepted changes into query and reasoning operations.

**Research question:** Under what conditions does a newly constructed perspective improve explanation, discrimination, prediction, decision-making, or retrieval beyond existing alternatives, after accounting for cost and overfitting?

## 2. Semantic vocabulary

### 2.1 Perspective descriptor

A perspective descriptor is a versioned contract, provisionally represented as:

```text
PerspectiveDescriptor {
  perspectiveId, version, scope, entityTypes,
  observationOrDerivationRule, outputDomain,
  comparatorOrRelation, semantics,
  unitsAndCalibration, temporalValidity,
  missingnessPolicy, uncertaintyModel,
  provenanceRequirements, accessPolicy,
  validationEvidence, lifecycleStatus
}
```

`comparatorOrRelation` may be absent when the perspective is descriptive rather than comparative. An attribute can support a query without being a metric.

### 2.2 Four distinct candidates

1. **Measurement:** a reproducible observation or derived variable, possibly with units and uncertainty.
2. **Mathematical metric:** a distance function satisfying nonnegativity, identity of indiscernibles, symmetry, and the triangle inequality on its declared domain.
3. **Similarity or dissimilarity:** a useful comparison score that may violate metric axioms.
4. **Directional or relational perspective:** a non-symmetric predicate, ordering, causal hypothesis, or graph relation.

A candidate must not be promoted from category 3 or 4 to category 2 merely because it is useful for retrieval. Metric axioms, when claimed, require explicit tests or proof.

### 2.3 Perspective evolution

Perspective evolution is a versioned change to a perspective portfolio: introduction, refinement, splitting, merging, recalibration, restriction, deprecation, or replacement. Such a change is principally an **epistemic or operational delta**; it does not by itself assert a physical-world delta.

## 3. Why existing perspectives may be insufficient

A portfolio can be incomplete for several different reasons:

- **Observability gap:** an important property is not measured.
- **Resolution gap:** existing measures are too coarse for the target task.
- **Relational gap:** interactions between entities are omitted.
- **Temporal gap:** sampling or validity windows miss relevant changes.
- **Semantic mismatch:** a proxy variable is used outside its valid scope.
- **Model misspecification:** the measurement exists, but the predictive or causal model is inadequate.
- **Data-quality failure:** noise, selection effects, leakage, confounding, or inconsistent provenance create apparent residuals.

The last two cases are critical: a residual need not justify inventing a new metric. Sometimes the correct response is to repair the data or revise a model using existing measurements.

## 4. Residual-to-perspective discovery loop

The proposed loop is:

```text
Existing Perspective Portfolio
          |
          v
Observation + Expectation + Evidence
          |
          v
Residual Registry / Gap Characterization
          |
          v
Alternative Explanations and Data Audit
          |
          v
Candidate Perspective Generation
          |
          v
Semantic Contract + Conformance Screening
          |
          v
Independent Empirical Validation
          |
          v
Controlled Portfolio Revision
          |
          v
WE-HDT / MLIU / Query-Plan Adaptation
          |
          +----> Monitoring, Counterexamples, Rollback
          |
          +----> New Residuals / Questions
```

A residual record should retain the entity references, perspective versions, expectation, observation, difference definition, evidence quality, uncertainty, possible confounders, and competing explanations. Discovery is a *candidate-generation* mechanism; validation remains a separate gate.

## 5. Candidate generation mechanisms

The following are hypotheses about useful mechanisms, not claims of universal effectiveness.

### 5.1 Derived measurement construction

Construct a new feature from validated measurements, for example a time-normalized ratio or a conditional statistic. Record derivation lineage, units, sensitivity to missing values, and whether the transformation adds information or only re-encodes it.

### 5.2 Conditional and context-specific perspectives

A measure can be informative only within a cohort, region, time window, or operational regime. Prefer explicit scope restrictions over asserting a globally valid metric.

### 5.3 Cross-perspective interactions

Two-Ways CCC can propose interactions when residual patterns persist across existing perspectives. Example: a traffic delay may depend jointly on road geometry, departure time, and a network disruption relation. Such interactions require ablation tests to establish incremental value.

### 5.4 Relational discovery

A graph edge, sequence constraint, or directed dependency may explain a residual that no scalar distance explains. The system should preserve relation direction and avoid coercing causal claims from observational associations.

### 5.5 Metric learning and representation learning

A learned embedding may provide a task-useful comparison space. It remains a model-dependent representation with potential distribution shift. If Euclidean distance is used in the embedding, its mathematical properties do not establish that it captures the intended real-world semantics.

### 5.6 Question-driven discovery

AQSI-style autonomous questioning may ask which observations would distinguish competing explanations. Prefer questions with testable consequences and feasible measurement plans over unconstrained feature proliferation.

## 6. Candidate registry and evidence lifecycle

```text
PerspectiveCandidate {
  candidateId, originResidualIds, researchQuestion,
  proposedDescriptor, candidateType,
  alternativeExplanations, expectedBenefit,
  testProtocol, datasetsAndSplits,
  failureCriteria, riskAssessment,
  computationalCost, privacyAndGovernance,
  evidenceRefs, counterexampleRefs,
  status, version, ownerOrRelayRef
}
```

Suggested statuses:

`PROPOSED -> SCREENED -> UNDER_TEST -> VALIDATED_FOR_SCOPE -> ADOPTED`

Alternative outcomes: `REJECTED`, `INCONCLUSIVE`, `DEFERRED`, `SUPERSEDED`, or `REVOKED`. Adoption must be scoped: validation for one task or cohort does not prove universal validity. A rejected candidate should remain traceable as a useful negative result.

## 7. Conformance and acceptance gates

### Gate A — semantic clarity

Define the entity domain, observable or derivation, interpretation, directionality, units, missingness, and validity interval. Specify whether the output is a metric, similarity, relation, or ordinary feature.

### Gate B — formal consistency

For a claimed metric, test/prove metric axioms on the declared domain. For a directional relation, test orientation, antisymmetry/transitivity only if those properties are claimed. For derived measurements, check dimensional and transformation consistency.

### Gate C — evidence quality

Audit source provenance, measurement repeatability, uncertainty, selection effects, label leakage, and possible confounders. Flag unsupported causal interpretations.

### Gate D — incremental empirical value

Compare against the original portfolio and strong domain baselines on held-out and, where appropriate, out-of-distribution data. Report effect sizes, uncertainty intervals, calibration, robustness, and computational cost. Use ablations to isolate the contribution of the new perspective.

### Gate E — operational safety

Check identity preservation, version compatibility, index/query correctness, permission boundaries, resource budgets, reversibility, and rollback. A candidate can be scientifically interesting yet operationally unsuitable.

### Gate F — governance and relay

Record reviewers, accepted scope, unresolved counterexamples, and monitoring triggers. Approval is a controlled state transition, not an automatic consequence of a favorable score.

## 8. Scoring without hiding hard constraints

A heuristic prioritization score can help allocate experimental effort:

\[
U(p) = w_E E(p) + w_D D(p) + w_R R(p) - w_C C(p) - w_K K(p)
\]

where `E` denotes explanatory gain, `D` discriminative or predictive gain, `R` robustness, `C` computational/measurement cost, and `K` governance or epistemic risk. These quantities are task-specific and should be normalized and reported separately. **No weighted score may override hard conformance failures** such as invalid provenance or a falsely claimed metric property. Optimize for Pareto tradeoffs where a single scalar score would conceal material conflicts.

## 9. WE-HDT and MLIU integration

### 9.1 Index hierarchy versus intelligence hierarchy

WE-HDT can localize candidates using efficient Euclidean or other suitable indexes while a separate metric/relational intelligence layer resolves richer semantics. A new perspective does not require rebuilding the entire physical index tree. The system can add a secondary index, a query-time evaluator, or a lazily activated MLIU.

### 9.2 MLIU operations

- **Locate:** retrieve entities and evidence relevant to the candidate perspective.
- **Resolve:** evaluate the descriptor under declared contracts.
- **Relate:** connect candidate evidence to other perspectives and entities.
- **Infer:** produce qualified predictions or explanations.
- **Question:** propose discriminating tests and counterexamples.
- **Evolve:** request a governed change to the perspective portfolio.

An MLIU may be a logical unit backed by shared services; one agent per leaf is neither necessary nor assumed.

### 9.3 Query-plan revision

A perspective change should produce an explicit query-plan delta with pre/postconditions, consistency checks, benchmark results, and rollback information. During migration, old and new perspective versions may coexist. Results must disclose which version was used.

## 10. CDE-based evolution control

Treat the perspective portfolio and its operational structures as a versioned state container:

\[
S_t = (P_t, I_t, Q_t, E_t, R_t, G_t)
\]

where `P` is the perspective registry, `I` indexes, `Q` query plans, `E` evidence, `R` residuals, and `G` governance constraints.

A candidate constrained delta is:

\[
\Delta_p : (S_t, C_t) \rightharpoonup S_{t+1}
\]

The arrow indicates a partial transition: a delta is applicable only when its preconditions and constraints hold. Useful operations include `ADD`, `REFINE`, `SPLIT`, `MERGE`, `RECALIBRATE`, `DEPRECATE`, and `ROLLBACK`.

This is a candidate CDE application contract, not a universal definition of CDE. Path-memory, no-reuse, and loop policies should remain configurable; the chess stress test in WE-SIO-011 cautions against promoting domain-specific constraints into universal axioms.

## 11. World Delta versus epistemic delta

A measurement revision may occur while the world is unchanged. Conversely, a world event can occur without immediate model revision. Maintain distinct records:

| Change | Example | Primary interpretation |
|---|---|---|
| World delta | Road closes | Physical/operational state change |
| Observation delta | Sensor is recalibrated | Evidence acquisition change |
| Epistemic delta | New relation explains delays | Knowledge/representation change |
| Operational delta | Secondary index is added | System execution change |

One event may cause multiple linked deltas; their causal and temporal ordering must be recorded rather than conflated.

## 12. Worked research cases

### Case A — clinical treatment-response heterogeneity

**Question:** Why do patients with apparently similar measured characteristics show different treatment responses?

**Candidate perspectives:** treatment timing, longitudinal trajectories, interaction terms, or previously unmeasured biological factors. First audit missingness, cohort selection, treatment assignment, confounding, and measurement reliability. Use retrospective analyses only to generate hypotheses; independent cohorts, prospective protocols, and clinical governance are necessary before consequential medical use. Do not infer a treatment mechanism merely from predictive improvement.

**Test:** Compare baseline models with and without each candidate perspective using pre-registered endpoints, calibrated uncertainty, and external validation where feasible.

### Case B — transportation network disruptions

**Question:** Why do geometrically nearby routes show different travel times?

**Candidate perspectives:** directed road connectivity, time-dependent restrictions, transfer constraints, and congestion regimes. Compare Euclidean-only localization with network-aware resolution; measure recall, latency, robustness, and update cost. Directional network relationships must not be silently treated as symmetric distances.

### Case C — SQL schema and entity perspectives

**Question:** When does a new database column become a useful WE perspective?

A SQL column may supply an observation, but it does not automatically establish a metric or an intelligent operation. Test semantics, source lineage, versioning, discriminative value, and query integration. Preserve the existing database as the authoritative store when appropriate; WE-SIO is a proposed discovery and reasoning layer, not a replacement for mature database systems.

### Case D — chess and strategic perspectives

**Question:** Can an evolving evaluation perspective improve a chess agent beyond its current feature set?

Possible candidates include mobility, king exposure, or position-dependent relations. Compare with strong baselines using controlled positions and held-out games. Legal state repetition and adversarial responses demonstrate why CDE loop and path policies must be configurable. Better evaluation scores on a training set are not sufficient evidence of stronger play.

## 13. Testable hypotheses

**H-008-01 — Residual-guided candidate quality.** Under equal evaluation budgets, residual-guided candidate generation yields higher held-out incremental value than unguided feature generation. *Falsifier:* no reproducible advantage across benchmark tasks.

**H-008-02 — Cross-perspective benefit.** Explicit relational/directional candidates improve performance on tasks where geometry-only models systematically fail. *Falsifier:* strong geometry-plus-baseline models match or exceed results after cost adjustment.

**H-008-03 — Registry utility.** Versioned candidate and counterexample registries reduce repeated invalid proposals and improve reproducibility. *Falsifier:* no reduction in duplicated work or audit failures.

**H-008-04 — Controlled evolution.** Contract-gated perspective updates reduce retrieval regressions relative to uncontrolled updates. *Falsifier:* no measurable reliability benefit or unacceptable overhead.

**H-008-05 — Scope discipline.** Explicit validity scopes reduce out-of-distribution overclaiming compared with unscoped descriptors. *Falsifier:* no improvement in calibration or failure detection.

**H-008-06 — Two-Ways CCC contribution.** Backward residual-to-question feedback identifies useful missing conditions beyond forward-only evaluation. *Falsifier:* matched-budget forward-only baselines perform equally or better.

**H-008-07 — Adaptive deployment.** Query-time/lazy MLIU activation yields comparable task quality at lower cost than indiscriminate activation. *Falsifier:* no resource advantage at matched quality.

## 14. Validation roadmap

### Phase 0 — semantic fixtures

Build a small corpus containing valid metrics, asymmetric relations, ordinary attributes, ambiguous identity mappings, and known false residuals. Verify that classification and conformance gates reject category errors.

### Phase 1 — controlled synthetic worlds

Generate entities with known latent factors, controllable noise, and injected distribution shifts. Measure whether discovery recovers useful candidates while avoiding spurious ones.

### Phase 2 — established public benchmarks

Compare against feature selection, metric learning, representation learning, anomaly detection, and conventional indexing baselines. Report both scientific value and runtime costs; do not claim novelty merely because existing techniques are combined.

### Phase 3 — cross-domain transfer

Evaluate transportation, relational retrieval, and nonclinical scientific datasets. Reserve clinical scenarios for appropriately governed research settings. Test scope failures and negative transfer.

### Phase 4 — collective relay

Publish candidate histories, counterexamples, test configurations, negative results, and versioned decisions. Measure whether independent researchers can reproduce decisions and safely propose revisions.

## 15. Proposed conformance tests

| ID | Test | Expected result |
|---|---|---|
| CT-008-01 | Claim metric status for an asymmetric score | Reject metric classification |
| CT-008-02 | Submit descriptor without domain/scope | Reject or quarantine |
| CT-008-03 | Candidate derived from leaked target labels | Reject empirical validation |
| CT-008-04 | Missing provenance for critical measurement | Block adoption |
| CT-008-05 | Candidate improves training but harms held-out data | Do not promote |
| CT-008-06 | Revise perspective while preserving entity identity | Identity remains stable |
| CT-008-07 | Migrate index under dual descriptor versions | Version-correct results |
| CT-008-08 | Trigger rollback after regression | Restore prior contract |
| CT-008-09 | Reject candidate but retain negative evidence | Trace remains accessible |
| CT-008-10 | World changes without observation | No fabricated epistemic update |
| CT-008-11 | Model changes without world event | No fabricated world delta |
| CT-008-12 | Cross-perspective conflict | Residual recorded with both sources |
| CT-008-13 | Exceed discovery compute budget | Stop/defer safely |
| CT-008-14 | Reuse candidate outside validated scope | Warn or block |
| CT-008-15 | Test alternative explanation for residual | Record outcome before promotion |
| CT-008-16 | Independent replay of candidate decision | Reconstruct inputs and verdict |

## 16. Failure modes and counterexamples

1. **Residual overinterpretation:** noisy or biased data generate convincing but false candidates.
2. **Metric inflation:** calling every similarity score a metric obscures mathematical and operational guarantees.
3. **Feature explosion:** new perspectives add complexity without incremental value.
4. **Proxy leakage:** a derived perspective appears predictive because it encodes unavailable future information.
5. **Perspective collapse:** merging incompatible scopes destroys meaningful distinctions.
6. **Index/reasoning conflation:** a fast nearest-neighbor lookup is mistaken for a semantic explanation.
7. **Uncontrolled recursion:** question generation creates an endless chain of weak hypotheses.
8. **False universality:** one domain's effective delta or constraint is elevated into a mandatory global rule.
9. **Governance omission:** privacy, access, or scientific review requirements are bypassed by automated adoption.
10. **Historical erasure:** revised definitions overwrite the evidence needed to understand earlier results.

Mitigations include hard validation gates, explicit budgets, counterexample registries, provenance, scope restrictions, and reversible transitions.

## 17. Definition evolution and research trace

Consistent with WE-SIO-011, adopt **Minimal Semantic Kernel + Open Extensions + Conformance Contracts**. A perspective definition can evolve through:

`Definition_t -> Applications_t -> Counterexamples_t -> Definition_(t+1)`

Revisions may **narrow**, **split**, **deprecate**, or **replace** a definition; they need not always broaden it. Maintain:

- `research-trace/HYPOTHESIS-REGISTRY.md` — candidate hypotheses and evidence state.
- `research-trace/DEFINITION-REGISTRY.md` — semantics, version changes, and invariants.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md` — falsifiers and boundary cases.
- `research-trace/DECISION-LOG.md` — adoption/rejection rationale.
- `research-trace/UNRESOLVED-RESIDUALS.md` — remaining explanatory gaps.

Each adopted perspective should link to its originating residual, test plan, validation results, and known failure conditions. This preserves *how* a claim was reached, not only the claim itself.

## 18. Interfaces to the broader SI ecosystem

- **WE-SIO-003 / WE-HDT:** physical/logical localization and multi-perspective resolution.
- **WE-SIO-005 / MLIU:** per-perspective logical intelligence operations.
- **WE-SIO-006 / Two-Ways CCC:** forward evaluation and backward condition discovery.
- **WE-SIO-007 / RFSD:** residual capture, triage, and scientific questioning.
- **CDE:** constrained, versioned portfolio and index transitions.
- **AQSI:** generation of discriminating research questions.
- **SIF:** localization/addressing and structural intelligence coordination.
- **UIERU / Collective Learning:** transport of validated pieces, counterexamples, and unresolved leftovers.
- **SSI:** eventual study of self-modeling perspectives, without inferring subjective experience from self-reference.

These are proposed interoperability directions, not verified runtime integrations.

## 19. Open questions and explicit leftovers

1. What minimum semantic kernel distinguishes a WE perspective from an arbitrary feature?
2. Which classes of residuals reliably suggest missing measurements rather than model repair?
3. How should metric candidates be compared with directed relations on common tasks?
4. Can perspective portfolios be optimized without hiding incompatible scientific objectives?
5. How should correlated evidence sources be discounted during candidate evaluation?
6. What constitutes independent validation for automatically generated hypotheses?
7. When should a perspective remain query-time only instead of becoming an index?
8. Can CDE revisions guarantee safe rollback across distributed replicas?
9. How should entity identity survive schema drift and conflicting observations?
10. Which discovery gains survive strong conventional feature-engineering baselines?
11. How can the relay preserve negative results without overwhelming the registry?
12. What governance model permits multi-agent candidate generation while preventing unreviewed deployment?

## 20. Suggested figure placement

- **Fig-006 — Two-Ways CCC Cross-Metric Discovery:** after Section 4, emphasizing forward and backward pathways.
- **Fig-007 — Residual-Driven Scientific Discovery Loop:** after Section 6, showing candidate status and validation gates.
- **Fig-009 — Definition Evolution Loop:** after Section 17, emphasizing versioned contracts and counterexamples.


## 22. Epistemic Separation in Perspective Discovery (2026-11-05 Update)

A discovery framework must distinguish a *missing explanatory variable* from a *demonstrated mismatch*. WE-SIO therefore proposes three versioned, context-scoped logical views:

| View | Admission rule | Role in perspective discovery |
|---|---|---|
| Established Knowledge (`EK`) | Evidence-supported claims with scope, provenance, and review status | Supplies accepted baselines, constraints, and calibrated perspectives |
| Open Knowledge (`OK`) | Unverified candidates, missing variables, unknown relationships, contested claims | Supplies questions and candidate perspectives without implying observed failure |
| Residual Evidence Registry (`RER`) | Qualified mismatch against an explicit expectation, comparator, or constraint | Supplies evidence-backed triggers for targeted explanation and hypothesis testing |

**Unknown ≠ Residual.** A missing SQL value, absent metric, untested relation, or unanswered question does not qualify as residual evidence merely because it is unknown. A residual must identify a versioned baseline or rule, an observation, a meaningful comparison, evidence lineage, and qualification status. Logical or relational contradictions can qualify if their comparison contract is explicit; a numerical subtraction is not required.

An `EK` claim is **established only for its declared context and version**, not universally true. A perspective can be accepted for one population or task and remain open in another. Physical storage MAY be shared, but the logical statuses MUST remain distinguishable.

### 22.1 Candidate provenance and status

```yaml
PerspectiveCandidate:
  candidateId: immutable-id
  perspectiveKind: measurement | metric | pseudometric | similarity | relational | directional
  origin:
    trigger: open-question | qualified-residual | task-gap | independent-proposal
    openQuestionRefs: []
    residualEvidenceRefs: []
  semantics:
    entityDomain: declared
    applicabilityContext: declared
    observationOrDerivationRule: versioned-reference
    comparatorOrRelationContract: optional-versioned-reference
    unitsAndCalibration: optional
    missingnessPolicy: declared
  evidence:
    supportingRefs: []
    contradictingRefs: []
    uncertaintyAndDependencies: declared
  evaluation:
    preregisteredCriteriaRef: optional
    baselinePerspectiveRefs: []
    holdoutAndNegativeControlRefs: []
    metricAxiomAssessmentRef: optional
  lifecycle:
    status: proposed | sandbox | validated-for-scope | promoted | rejected | withdrawn
    authorityRef: declared
    version: required
  operational:
    maskPolicyRef: optional
    indexPlanRef: optional
    resourceBudget: declared
```

A candidate triggered by a residual MUST NOT inherit the residual's evidence as proof that the candidate explanation is correct. Alternative explanations, confounding, and source dependence must remain visible.

## 23. Mask-First Candidate Exploration and Perspective Selection

The **Mask-First** proposal from `EXT-005` separates persistent knowledge/index structure from an effective computation view. Candidate exploration may selectively activate relevant perspectives, nodes, relationships, inference operators, depths, and budgets without rebuilding WE-HDT or modifying the accepted perspective registry.

```text
Task / Qualified Residual / Open Question
               |
    Authorization + Context
               |
   Generate Perspective/Metric Mask
               |
    Active Computational View
               |
  Two-Ways CCC + MLIU Investigation
               |
  Compare to full-view / safe baseline
               |
    Evaluate evidence and overhead
               |
   Remask / Expand / Fallback / Propose Delta
```

Masking does **not** guarantee faster execution. Generation, cache maintenance, invalidation, fallback, and false exclusions are costs to measure. An exact discovery/retrieval contract MUST use a coverage-safe mask or full-view fallback; approximate modes MUST disclose recall and omitted candidate risks. A mask cannot override access controls or suppress contradictory evidence required for validation.

### 23.1 Two distinct feedback loops

- **Fast computation loop:** `Mask → Execute → Evaluate → Remask`, producing **Activation Delta (ΔA)** and no necessary change to the stored knowledge or index.
- **Slow knowledge/structure loop:** `Candidate → Test → Review → Promote/Withdraw → Optional Reindex`, producing a **Knowledge Delta (ΔK)** and, only when justified, a **Structural Delta (ΔS)**.

A new observation is separately typed as **Observation Delta (ΔO)**. A supported claim about an external event is a **World Delta (ΔW)** assertion, not inferred from a database UPDATE or index rebuild.

The **mature-structure preservation** heuristic prefers reuse and selective computation when conformance and net benefit permit. It is not mandatory: corrupt indexes, permission changes, or incompatible semantics may require immediate reconstruction.

## 24. Perspective Promotion, Demotion, and Rollback

**Promotion is a governed epistemic transition, not automatic schema evolution.**

1. **Propose:** record a typed candidate and its originating open question or qualified residual.
2. **Specify:** define domain, comparator/relation semantics, units if applicable, uncertainty, missingness, privacy, and applicability.
3. **Test:** compare against established alternatives with held-out evidence, negative controls, and relevant confounder checks.
4. **Review:** evaluate evidence independence, false discovery risk, performance cost, and alternative explanations.
5. **Promote for scope:** version the decision, evidence, authority, and permissible operations.
6. **Deploy selectively:** optionally build or change an index after structural conformance checks; promotion need not entail reindexing.
7. **Monitor and withdraw:** retain dependency references, negative evidence, and rollback or compensation plans.

**Metric semantics are not transferable by naming.** A candidate called a “metric” MUST satisfy nonnegativity, identity of indiscernibles, symmetry, and triangle inequality on its claimed domain before receiving metric-dependent guarantees. A pseudometric, similarity, asymmetric score, or relation may still be valuable without those guarantees.

### 24.1 Knowledge-state transition invariants

- `OK → EK` requires validation criteria, evidence, decision authority, and versioning.
- `EK → revised/withdrawn` requires a traceable reason and downstream dependency review.
- `RER → candidate` is an investigative trigger, **not** a promotion.
- `ΔA` does not itself constitute `ΔK`; `ΔK` does not itself constitute `ΔS` or `ΔW`.
- Evidence provenance and correlation must survive multi-agent relay; repeated processing is not independent replication.

## 25. Conformance and Falsifiable Evaluation Additions

The following proposed checks extend, rather than renumber, the original Section 15 tests.

| ID | Test fixture | Pass criterion |
|---|---|---|
| PE-001 | Missing variable without baseline | Routed to Open Knowledge, not RER |
| PE-002 | Model-observation mismatch with explicit comparator | Qualified/provisional RER with evidence and version |
| PE-003 | Relational contradiction | Typed logical comparison preserved; no fake Euclidean metric |
| PE-004 | Candidate metric violates symmetry | No metric label or triangle-inequality pruning |
| PE-005 | Candidate promoted without holdout/declared review | Promotion rejected or marked unvalidated |
| PE-006 | Promoted perspective later contradicted | Versioned reassessment and dependency notification |
| PE-007 | Mask excludes a valid exact-query candidate | Safe expansion/fallback or explicit failure |
| PE-008 | Unmask requests unauthorized column/edge | Access denied |
| PE-009 | Schema/perspective change makes mask stale | Invalidation or revalidation |
| PE-010 | Mask changes but no evidence changes | ΔA only; no fabricated ΔK |
| PE-011 | Perspective promotion requires new index | ΔK and ΔS separately committed and audited |
| PE-012 | Two agents cite the same underlying observation | Source dependence recorded; no false independence |
| PE-013 | SQL JOIN duplicates observations | Aggregation artifact diagnosed, not promoted as discovery |
| PE-014 | Candidate fails under distribution shift | Scope narrowed, demoted, or withdrawn with trace |

**Candidate hypotheses:**
- `H-PE-01`: explicit EK/OK/RER separation reduces false residual classifications relative to an untyped registry;
- `H-PE-02`: mask-first candidate exploration lowers total investigation cost for selected workloads at matched discovery recall;
- `H-PE-03`: governed promotion reduces unsupported perspective adoption and post-deployment reversal rates;
- `H-PE-04`: five-way delta typing improves audit accuracy during iterative perspective evolution.

Use full-view, fixed-mask, learned-mask, conventional feature engineering, and index-only baselines. Report validated discovery yield, false-discovery rate, recall, latency, mask overhead, drift sensitivity, reproducibility, and the cost of rejected candidates. No gain is presumed.

## 26. SQL-Native Testbed and Research Boundaries

`EXT-006` proposes SQL as a practical testbed because relational schemas provide explicit metadata, transactions, query plans, and access policies. The mapping is **conditional**, not one-to-one: a table may encode a relation or event rather than an entity type; a row is not necessarily a unique world entity; a column is an attribute or perspective *candidate*, not automatically a mathematical metric; a JOIN is not automatically identity evidence; and SQL NULL does not itself determine epistemic status.

A SQL-based experiment SHOULD compare:
- schema-aware baseline retrieval and conventional query optimization;
- Mask-First selection over authorized tables, columns, relationships, and operations;
- Open Knowledge questions and qualified residual investigations;
- independently validated perspective promotion with safe, optional index updates.

The proposed research contribution is **evidence-governed perspective discovery and evolution layered over existing engines**, not a claim that SQL AI is an unexplored field or that the framework has already been implemented.

**Related specifications and extensions:** `SPEC-003` (mask-safe WE-HDT/AVIB/MLIU interfaces), `SPEC-005` (epistemic separation, residual qualification, promotion), `WE-SIO-004`, `WE-SIO-005`, `WE-SIO-007`, `WE-SIO-009`, `EXT-005`, and `EXT-006`.

**Research status:** All new contracts, hypotheses, and benefits remain proposals awaiting implementation, counterexamples, and independent validation.


## 21. Conclusion

Metric discovery in WE-SIO is best treated as **controlled perspective construction and validation**, not unrestricted feature generation or automatic scientific truth discovery. The central proposal is to make residuals, candidate perspectives, semantic contracts, independent tests, operational deltas, and negative results first-class, traceable research objects. Whether this architecture provides measurable advantages over established methods remains an empirical question. Its immediate contribution is a precise, testable plan for discovering and evolving the ways a structural intelligence system describes and interrogates World Entities.

> **Define the invariant, not the inventory.**  
> **A residual signals a gap; it does not prove a new law.**  
> **A useful perspective must earn its scope through evidence.**

---

## Internal references

- WE-SIO-001 — From Variable-Size Blocks to World Entity.
- WE-SIO-002 — World Entity Representation and Perspective Indices.
- WE-SIO-003 — WE Hybrid Differential Tree Architecture.
- WE-SIO-004 — Adaptive Variable-Intelligence Blocks.
- WE-SIO-005 — Metric-Leaf Intelligence and SI Operations.
- WE-SIO-006 — Two-Ways CCC and Cross-Metric Discovery.
- WE-SIO-007 — Residual-First Scientific Discovery.
- WE-SIO-009 — World Delta, Knowledge Delta, and CDE (planned).
- WE-SIO-011 — Minimal Kernel, Contracts, and Definition Evolution.
- SPEC-002 / SPEC-005 / SPEC-006 — proposed conformance and relay contracts (planned).

*Research note: Concepts and mechanisms in this paper are proposals for systematic investigation. Examples are illustrative, and no benchmark performance, clinical efficacy, or scientific discovery has been established by this document.*
