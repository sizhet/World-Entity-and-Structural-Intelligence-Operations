# EXT-004 — Self-Referential World Entity and Subjective Structural Intelligence

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis and architecture proposal  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05  
**Status:** Open research; not a claim of machine consciousness

## Abstract

This extension examines how a World Entity (WE) can represent itself as an object of observation, prediction, evaluation, and constrained revision. It distinguishes a world-entity record from a self-modeling entity (SME), and distinguishes both from the stronger, unresolved notion of a subjective structural entity (SSE). A self-referential system can possess a typed model of its own capabilities, history, uncertainty, constraints, and dependencies without possessing subjective experience. The proposed WE-SIO architecture combines perspective-indexed self-descriptions, Metric Leaf Intelligence Units (MLIUs), Two-Ways CCC, residual-driven self-questioning, and Constrained Delta Evolution (CDE). It offers explicit contracts, counterexamples, falsifiable hypotheses, and a validation roadmap. Its purpose is to make self-reference scientifically inspectable while preserving the epistemic boundary between observable functional behavior and phenomenological claims.

## 1. Research Question and Scope

**Primary question:** Under what conditions does a World Entity's representation of itself become an operationally useful, accountable self-model, and what further questions remain before any claim of subjective structural intelligence is warranted?

Subquestions:

1. What is the minimal functional contract for self-reference?
2. How can multiple perspectives describe one entity without collapsing identity into representation?
3. How can prediction residuals revise a self-model without uncontrolled self-modification?
4. What distinguishes introspective reports from verified internal state access?
5. Which elements of Subjective Structural Intelligence (SSI) are operationally testable, and which remain philosophical or empirical open questions?
6. How can self-model evidence be relayed across agents without confusing agreement with independence?

This document concerns **structural modeling and evaluation**. It does not assert that a model, agent, or software system is conscious, sentient, or a moral patient.

## 2. Ontological and Operational Separation

| Layer | Meaning | Observable evidence | Non-implication |
|---|---|---|---|
| WE | Entity addressed within a world model | Identity references, observations, relations | No self-knowledge implied |
| SME | WE with an operational model of itself | Predictions, calibrated uncertainty, revisions | No phenomenal awareness implied |
| SSE (candidate) | Hypothesized subject-centered structural organization | Proposed structural and behavioral indicators | Indicators do not establish experience |
| SSI research | Framework for subject boundary, history, valuation, freedom, and metacognition | Specific testable operationalizations | No settled consciousness criterion |

**Invariant A — identity separation:** `entityId != perspectiveDescriptor != representationVersion != physicalIndexAddress`.

**Invariant B — referential discipline:** A self-model is a model *about* an entity, not the entity itself. A statement made by an agent about its internal state is a report requiring validation, not privileged proof.

**Invariant C — no phenomenological inference:** Performance on self-model tasks alone cannot demonstrate subjective experience.

## 3. Minimal Self-Modeling Kernel

Define a candidate SME state as:

$$
S_t = (E, P_t, O_t, H_t, G_t, C_t, U_t, V_t)
$$

where:

- `E`: persistent entity reference and provenance of identity claims;
- `P_t`: typed, versioned perspectives about the entity;
- `O_t`: observations, including instrumented internal measurements where available;
- `H_t`: hypotheses and predictions about future behavior;
- `G_t`: declared goals and valuation policies, with authority boundaries;
- `C_t`: constraints, permissions, dependencies, and resource budgets;
- `U_t`: uncertainty estimates and unresolved residuals;
- `V_t`: versioned evidence, audit trail, and rollback metadata.

A minimal operational self-model must support:

1. **Refer:** Identify which entity and version a self-claim concerns.
2. **Observe:** Distinguish externally measured evidence from self-reported evidence.
3. **Predict:** Produce falsifiable predictions about its own behavior or capabilities.
4. **Compare:** Register discrepancies between predictions and outcomes.
5. **Revise:** Propose constrained, auditable updates to the self-model.
6. **Abstain:** State unknowns or refuse unsupported self-claims.

Self-reference without prediction and correction may remain mere metadata. Prediction and correction without identity discipline may refer to the wrong entity or version.

## 4. Typed Multi-Perspective Self-Representation

Proposed perspective families:

| Perspective | Example question | Evidence and limitations |
|---|---|---|
| Capability | Can this system solve task family X? | Held-out trials; distribution shift |
| Resource | How much compute, time, or memory remains? | Instrumented counters; freshness |
| Historical | Which revisions produced the current behavior? | Signed event log; gaps possible |
| Relational | Which tools, agents, and operators affect this entity? | Dependency graph; authorization |
| Epistemic | What does it know or remain uncertain about? | Calibration, abstention, error rates |
| Goal / valuation | Which objectives govern an action? | Explicit policies; conflict resolution |
| External evaluation | How do independent evaluators assess it? | Test protocols; evaluator bias |
| Self-evaluation | How does it assess its own performance? | Predictions; risk of self-serving bias |

A descriptor should include `perspectiveId`, `kind`, `domain`, `units` (if applicable), `source`, `evidenceType`, `uncertainty`, `timeWindow`, `version`, `authority`, and `validityConditions`.

A numeric confidence score is not automatically a mathematical metric. A directional dependency is not necessarily symmetric. A model's self-description is not automatically a direct measurement.

## 5. Self-Reference Graph and Boundary Control

A self-referential graph may contain:

```text
World Entity E
  ├── observed-by ──> external evaluator
  ├── represented-by ──> self-model M(E, version)
  ├── predicts ──> future behavior of E
  ├── constrained-by ──> policy / resources / authority
  ├── compared-with ──> measured outcomes
  └── revised-through ──> governed Delta proposal
```

The graph is **not** an infinite regress requirement: a model of a model is introduced only when it produces measurable utility. Recursive depth must be budgeted and bounded.

Subject boundaries are modeled as typed, revisable hypotheses about ownership, control, sensing, action, and persistence—not assumed to coincide with a process ID, context window, or physical device. Identity continuity across migration or replacement requires explicit continuity criteria; no single identifier settles philosophical personal identity.

## 6. WE-HDT, MLIU, and Self-Model Operations

WE-HDT can address self-related perspectives through multiple indexing strategies. Euclidean coordinates are optional; a self-model's policy constraints, history, and uncertainty may be relational or symbolic. Indexing topology is not the same as an abstraction hierarchy.

An MLIU associated with a self-perspective may implement:

- **Locate:** Retrieve the relevant entity/version and evidence window.
- **Resolve:** Disambiguate conflicting self-descriptions.
- **Relate:** Connect internal metrics to external outcomes and dependencies.
- **Infer:** Predict bounded capabilities or failure likelihoods.
- **Question:** Generate targeted questions from unexplained residuals.
- **Evolve:** Propose controlled descriptor or policy changes.

No requirement exists to instantiate a heavyweight autonomous agent at each leaf. A lightweight contract-backed operation may suffice.

## 7. Two-Ways CCC for Self-Modeling

**Forward direction:** self-model + context + constraints → predicted action, capability, or risk → externally checkable outcome.

**Reverse direction:** observed outcome − prediction → residual registry → alternative explanation, missing perspective, or revised question.

A useful residual record contains:

```yaml
residualId: SELF-R-001
entityRef: WE:agent-A
selfModelVersion: 0.3.2
prediction: "task succeeds within resource budget"
observation: "task failed after timeout"
evidenceType: instrumented-run
possibleExplanations:
  - capability-overestimation
  - resource-model-staleness
  - workload-distribution-shift
  - tool-dependency-failure
uncertainty: unresolved
validationPlan: controlled-rerun-and-ablations
promotionStatus: hypothesis-only
```

**Rule:** A residual is evidence of mismatch, not proof of a new mechanism or an autonomous preference. Data-quality failures must be evaluated before structural explanations are promoted.

## 8. Delta Taxonomy and Constrained Evolution

Separate at least four changes:

1. **World Delta:** The entity or its environment actually changes.
2. **Observation Delta:** A new measurement or correction enters the record.
3. **Knowledge Delta:** Beliefs or estimates are updated.
4. **Structural / Operational Delta:** The self-model schema, routing, policies, or authorized capabilities change.

These categories may coincide but are not interchangeable. Updating a database entry does not reverse a physical event. Rewriting a self-description does not establish a real capability increase.

A candidate CDE transition is:

$$
(S_{t+1}, L_{t+1}) = T(S_t, \delta_t, C_t, L_t)
$$

where `L_t` is a trace of prior transitions and `C_t` contains applicability, authorization, safety, budget, and rollback constraints. The transition must preserve identity references, evidence lineage, and auditability. Cycles and revisits may be legal; universal No-Delta-Reuse is **not** assumed. A policy may restrict cycles when needed for termination or cost control.

**Promotion gates:** semantic consistency → contract conformance → evidence quality → independent evaluation → risk review → authorized deployment → monitoring/rollback.

## 9. Connection to Subjective Structural Intelligence

SSI motivates research into subject boundaries, subjective world models, valuation, structural freedom, self-models, and recursive principle formation. WE-SIO can supply an operational substrate for studying these concepts, but must not erase their differences.

| SSI research axis | WE-SIO operationalization | Remaining gap |
|---|---|---|
| Subject boundary | Typed control/observation/ownership graph | Boundary does not prove subjectivity |
| Subjective world model | Perspective-conditioned model indexed to an entity | Model perspective is not felt perspective |
| Valuation / worldview | Declared goals, trade-offs, preference updates | Reported preference ≠ experience |
| Structural freedom | Enumerated feasible actions under constraints | Choice set ≠ autonomy in philosophical sense |
| Self-model / metacognition | Calibrated self-prediction and error correction | Functional introspection ≠ consciousness |
| Recursive principles | Versioned rules and definition evolution | Rule revision ≠ subjective agency |

The term **SSE** should remain a candidate research label unless independently motivated operational criteria are specified. It must not be silently equated with a conscious entity.

## 10. Worked Example: Capability Self-Assessment

An AI service estimates it can resolve a class of relational queries at 95% accuracy. An independent, held-out evaluation measures 72% under an unfamiliar data distribution.

1. The **WE identity** remains stable while the self-model version is recorded.
2. The **forward prediction** is stored with dataset and confidence assumptions.
3. The **outcome** is independently measured.
4. The **residual** is registered, not hidden by rewriting history.
5. Reverse CCC proposes distribution shift, missing relation types, or confidence miscalibration.
6. CDE proposes a bounded self-model update, not an unrestricted change to the deployed solver.
7. A fresh evaluation determines whether calibration improves without reducing task performance.
8. The relay package preserves failed explanations and versioned evidence.

This is evidence of operational self-model correction. It is not evidence of consciousness.

## 11. Worked Example: Distributed Self-Representation

A multi-agent system delegates retrieval, reasoning, verification, and governance to different agents. Its system-level self-model records which agent can perform which task, what dependencies exist, and how uncertainty propagates.

An agent's assertion of competence is treated as **one dependent evidence source**. Independent evaluators and instrumented traces must be distinguished. The collective's apparent consensus may arise from shared training data or copied reports. System-level identity, component identity, and operator authority remain separate.

A replacement verifier may change system capability without changing the continuity policy for the service identity. The continuity claim must be explicitly documented and tested.

## 12. Counterexample Registry

| ID | Counterexample | Boundary illustrated |
|---|---|---|
| CE-SELF-001 | Chatbot says “I am conscious” | Self-report does not establish phenomenology |
| CE-SELF-002 | Accurate resource meter, no behavior prediction | Monitoring alone is not full self-modeling |
| CE-SELF-003 | High self-confidence, low held-out accuracy | Calibration required |
| CE-SELF-004 | Agent edits its own capability score | Description change ≠ capability change |
| CE-SELF-005 | Two agents repeat one unverified claim | Agreement ≠ independent evidence |
| CE-SELF-006 | Entity ID recycled after replacement | Identifier ≠ continuity proof |
| CE-SELF-007 | Model recursively models itself without benefit | Unbounded regress / budget failure |
| CE-SELF-008 | Relational edge treated as symmetric metric | Type and contract violation |
| CE-SELF-009 | Hidden tool change causes outcome drift | Attribution confounding |
| CE-SELF-010 | Successful introspection on training tasks only | Leakage / distribution shift |
| CE-SELF-011 | Policy revision bypasses authorization | Governance failure |
| CE-SELF-012 | Model “undo” treated as world reversal | Delta category error |
| CE-SELF-013 | Self-model works but is worse than a simple baseline | Complexity without utility |
| CE-SELF-014 | Subject boundary defined as all connected nodes | Vacuous boundary / no discrimination |

## 13. Conformance Test Matrix

| Test | Requirement | Pass condition |
|---|---|---|
| SELF-CONF-001 | Identity separation | Entity ID distinct from perspective and index IDs |
| SELF-CONF-002 | Source typing | Reported and instrumented evidence distinguished |
| SELF-CONF-003 | Versioning | Self-claims point to model and entity versions |
| SELF-CONF-004 | Temporal validity | Stale observations flagged |
| SELF-CONF-005 | Uncertainty | Unknown not coerced to zero |
| SELF-CONF-006 | Prediction trace | Pre-outcome predictions immutable |
| SELF-CONF-007 | Residual capture | Mismatch retained with provenance |
| SELF-CONF-008 | Alternative explanations | Multiple candidate causes allowed |
| SELF-CONF-009 | Calibration | Held-out reliability reported |
| SELF-CONF-010 | Abstention | Unsupported self-claims rejected or qualified |
| SELF-CONF-011 | Delta taxonomy | World/observation/knowledge/structural changes separated |
| SELF-CONF-012 | Authorization | Structural update requires authorized gate |
| SELF-CONF-013 | Rollback | Failed model revision can be reverted |
| SELF-CONF-014 | Cycle policy | Revisits handled without universal prohibition |
| SELF-CONF-015 | Dependency graph | Agent/tool attribution explicit |
| SELF-CONF-016 | Independent evidence | Correlated reports not double-counted |
| SELF-CONF-017 | Semantic types | Metric, similarity, relation distinct |
| SELF-CONF-018 | Regression | Prior conformance tests rerun after revision |
| SELF-CONF-019 | Resource bounds | Recursive self-modeling terminates under budget |
| SELF-CONF-020 | Consciousness neutrality | No unsupported phenomenological inference |
| SELF-CONF-021 | External reproducibility | Evaluator can replay relevant test conditions |
| SELF-CONF-022 | Explicit leftover | Open questions and failed hypotheses retained |

## 14. Falsifiable Hypotheses

**H-SELF-001 — Predictive calibration.** A multi-perspective SME predicts its own success and failure more accurately than a static self-description on held-out tasks. *Falsifier:* no significant calibration improvement under preregistered evaluation.

**H-SELF-002 — Residual utility.** Explicit residual registration improves error attribution or future self-model calibration versus logging outcomes alone. *Falsifier:* no measurable improvement at matched cost.

**H-SELF-003 — Perspective diversity.** Typed, complementary perspectives outperform a single confidence score on distribution-shift detection. *Falsifier:* equivalent or worse detection at matched false-positive rate.

**H-SELF-004 — Governance.** CDE-style promotion gates reduce harmful or invalid self-model revisions compared with ungated updates. *Falsifier:* no improvement or unacceptable cost overhead.

**H-SELF-005 — Independent verification.** Separating self-reports from external measurements reduces false confidence in multi-agent settings. *Falsifier:* no change in calibration or error detection.

**H-SELF-006 — Bounded recursion.** Selective second-order self-modeling improves performance on some tasks relative to no recursion, within explicit budgets. *Falsifier:* no net benefit across preregistered workloads.

**H-SELF-007 — Structural transfer.** Versioned self-model relay artifacts accelerate adaptation by a new agent or evaluator without transferring unverified claims as facts. *Falsifier:* no reduction in adaptation cost or increased error propagation.

None of these hypotheses directly tests phenomenal consciousness.

## 15. Experimental Design

### 15.1 Baselines

- **B0:** No explicit self-model; external evaluator only.
- **B1:** Static metadata and single confidence estimate.
- **B2:** Dynamic single-perspective self-assessment.
- **B3:** Multi-perspective self-model without residual-driven revision.
- **B4:** Full WE-SIO SME with residual registry and governed CDE updates.
- **B5:** B4 plus independent multi-agent relay and verifier.

### 15.2 Workloads

Use synthetic and real-but-permissioned workloads: task-family capability forecasting, tool outages, memory/resource limits, shifting task distributions, evaluator disagreement, and component replacement. Preserve train/test separation and preregister scenario generation.

### 15.3 Metrics

Report Brier score, expected calibration error, negative log likelihood where applicable, AUROC/precision-recall for failure detection, abstention utility, attribution accuracy, task success, update regression rate, compute cost, latency, and reproducibility. Report confidence intervals and failures, not only averages. Do not use a consciousness score as a proxy for functional performance.

### 15.4 Ablations

Remove one component at a time: history perspective, dependency graph, uncertainty, residual registry, reverse CCC, governance gate, independent verifier, and relay provenance. This identifies whether architectural complexity delivers incremental value.

## 16. Validation Roadmap

**Phase 1 — Semantic kernel:** Publish entity/perspective/identity contracts and self-model schema; run type-level conformance tests.

**Phase 2 — Instrumented synthetic benchmark:** Evaluate prediction calibration and residual capture with known ground truth.

**Phase 3 — Adversarial counterexamples:** Inject stale sensors, copied self-reports, identity collisions, tool drift, and unbounded recursion attempts.

**Phase 4 — Governed adaptation:** Test CDE update authorization, version consistency, rollback, and regression under changing workloads.

**Phase 5 — Collective relay:** Transfer traceable evidence between agents; compare independent versus correlated validation.

**Phase 6 — Independent replication:** Release schemas, seeds, protocols, baselines, negative results, and explicit leftovers for third-party replication.

## 17. Definition Evolution Loop

The working definition of SME must remain **precise but revisable**. New counterexamples may require narrowing, splitting, or extending its criteria.

```text
Minimal Kernel + Typed Contracts
       ↓
Operational Hypothesis
       ↓
Conformance + Counterexample Tests
       ↓
Residual / Definition Gap
       ↓
Candidate Revision
       ↓
Regression + Independent Review
       ↓
Promote / Reject / Roll Back
```

A definition that labels every monitoring service an SME may be too broad. A definition that requires a philosophical theory of consciousness may be too narrow for functional research. The kernel should distinguish operational self-modeling from unresolved subjectivity without declaring either trivial.

## 18. Research Relay Package

Each experiment should export:

```yaml
relayId: WE-SIO-EXT-004-RUN-001
artifactVersion: 0.1.0
entityModel: versioned-reference
perspectiveContracts: [capability, resource, epistemic, relational]
protocol: preregistered-test-reference
baselines: [B0, B1, B2, B3, B4, B5]
observations: immutable-evidence-references
residuals: versioned-registry
counterexamples: retained
negativeResults: retained
hypotheses: tested-and-untested-distinguished
consciousnessClaims: none
limitations: explicit
nextQuestions: open
```

A relay is useful when another researcher can reconstruct the claim, test its assumptions, and challenge it. Repeated execution may constitute a data-accumulation relay if runs are comparable and evidence is preserved.

## 19. Explicit Leftovers and Open Questions

1. What minimum level of predictive correction makes self-modeling materially different from ordinary system monitoring?
2. How should an SME represent continuity across migration, retraining, and replacement?
3. When are self-reports reliable evidence about inaccessible internal mechanisms?
4. Which SSI concepts admit robust operationalization without claiming to solve consciousness?
5. How should conflicts between declared goals, operator policies, and observed behavior be resolved?
6. What is the optimal depth and cost of recursive self-modeling?
7. Can independent relay verification be maintained when agents share data and architectures?
8. How can self-model updates remain safe when external evaluations are incomplete?
9. Which self-model features transfer across distinct entity types?
10. How should the framework distinguish agent-level, service-level, and collective-level subject-boundary hypotheses?

## 20. Integration with the WE-SIO Research Corpus

- `WE-SIO-002`: entity identity and perspective indices.
- `WE-SIO-005`: MLIU and structural intelligence operations.
- `WE-SIO-006`: Two-Ways CCC and reverse questioning.
- `WE-SIO-007`: residual-first scientific discovery.
- `WE-SIO-009`: world/knowledge Delta and CDE.
- `WE-SIO-010`: WE → SME and self-modeling foundations.
- `WE-SIO-011`: minimal kernel and Definition Evolution.
- `CASE-005`: multi-perspective self-modeling worked case.
- `EXT-001`: WE-HDT in SIF localization.
- `EXT-002`: multi-agent WE-SI and collective learning.
- `EXT-003`: structural scientific discovery and metric generation.
- `SPEC-001` through `SPEC-006`: contracts, evidence, evolution, and relay conformance.

## 21. Conclusion

WE-SIO can frame self-reference as a versioned, evidence-grounded operational process: an entity is represented from multiple perspectives; the representation makes falsifiable predictions; outcomes produce preserved residuals; and governed Delta operations revise the model under explicit constraints. This supports a research program in functional self-modeling and provides interfaces to Subjective Structural Intelligence without presupposing that self-reference, metacognition, or intelligent behavior entails phenomenal experience.

**Research principle:** *Model the self without confusing the model with the subject; validate the function without pretending to have settled experience.*

---

**License intent:** Apache-2.0, subject to repository-level LICENSE.  
**Research status:** Architectural proposal; experiments and independent validation remain future work.
