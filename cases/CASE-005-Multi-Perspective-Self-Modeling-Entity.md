# CASE-005 — Multi-Perspective Self-Modeling Entity

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research case / hypothesis  
**Status:** Proposed specification and validation design; not an empirical demonstration  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot

## Abstract

This case examines how a World Entity (WE), represented through multiple perspective descriptors, may be extended into a **Self-Modeling Entity (SME)** that maintains an operational model of its own state, capabilities, boundaries, actions, and uncertainty. It explores the interfaces between WE-HDT, Metric-Leaf Intelligence Units (MLIUs), Two-Ways CCC, residual-first discovery, and Constrained Delta Evolution (CDE). The aim is to establish falsifiable functional contracts—not to claim that self-reference, self-modeling, autonomy, or feedback establishes consciousness or subjective experience.

The case centers on a bounded software agent performing tasks in a simulated environment. It compares a fixed self-description, a single-perspective adaptive self-model, and a multi-perspective self-model with evidence-aware revision. A fourth condition adds controlled collective relay. The design specifies state, observations, operational contracts, counterexamples, benchmarks, and unresolved questions.

## 1. Research question and scope

**Primary question:** Under what conditions does a multi-perspective self-model improve an entity's ability to predict its own task performance, recognize its limitations, and revise its operational decisions without confusing self-representation with objective identity or subjective experience?

Subquestions:

1. Can distinct perspectives provide complementary, testable information about the same entity?
2. Can residuals reveal gaps in the self-model rather than merely reflecting environmental noise?
3. Can Two-Ways CCC propose missing perspectives while preserving evidentiary boundaries?
4. Can CDE update self-model structure under identity, safety, and resource constraints?
5. Does relay of negative results and counterexamples improve transfer to new tasks?

**In scope:** Functional self-monitoring, predictive calibration, explicit evidence provenance, controlled revisions, task performance, and reproducible comparison.

**Out of scope:** Claims of phenomenal consciousness, personhood, moral status, subjective qualia, or proof of general intelligence. A system that says “I” does not thereby possess a subjective self.

## 2. Conceptual separation

| Concept | Operational interpretation | Must not be conflated with |
|---|---|---|
| World Entity (WE) | Referent about which claims are made | Its database row or model |
| Entity identity | Stable reference under a declared identity policy | A changing feature signature |
| Perspective | Typed way of observing, comparing, or relating the entity | Necessarily a mathematical metric |
| Self-model | Revisable representation of the entity's own properties and processes | The entity itself |
| Self-monitoring | Observation of internal or externally exposed indicators | Direct access to every internal cause |
| Self-regulation | Policy changes informed by self-model estimates | Unrestricted autonomy |
| Subjective Structural Entity (SSE) | A separate research hypothesis concerning richer subject-related structures | A demonstrated consequence of SME |

The working progression **WE → SME → candidate SSE** denotes increasing research commitments, not a proven developmental ladder. A WE can exist without any self-model; an SME can exist without any evidence of experience.

## 3. Scenario: bounded research agent

Consider an agent that processes document-analysis tasks in a sandbox. The environment varies input length, ambiguity, available tools, latency, and permitted computation. The agent must select an execution strategy, estimate success probability, execute, inspect outcomes, and update its self-model.

### 3.1 Perspectives

| Perspective ID | Kind | Example value | Evidence source |
|---|---|---|---|
| `P-capability` | Measurement / calibrated prediction | Estimated probability of correct extraction | Held-out scored tasks |
| `P-resource` | Euclidean-compatible numeric attributes where units permit | Token and time budgets | Instrumentation |
| `P-history` | Temporal / event sequence | Past failures on long tables | Versioned logs |
| `P-dependency` | Relational / directional | Tool A requires permission B | Declared tool graph |
| `P-uncertainty` | Statistical summary | Calibration interval | Evaluation records |
| `P-goal` | Normative / policy | Accuracy priority subject to cost cap | Authorized objective |
| `P-external-view` | Third-party assessment | Evaluator-detected omissions | Independent reviewer |
| `P-self-claim` | Self-reported estimate | “I expect to succeed” | Agent report |

A numeric attribute is not automatically a metric. Resource dimensions require unit normalization and a declared distance contract before metric indexing. `P-dependency` is directional; its relation is not presumed symmetric. `P-self-claim` is a claim requiring calibration, not privileged ground truth.

### 3.2 Example identity and representation

```json
{
  "entityRef": "agent-sandbox-01",
  "identityPolicy": "stable-sandbox-instance-id",
  "representationVersion": "3",
  "perspectives": [
    {"id": "P-capability", "estimate": 0.74, "taskClass": "long-table-extraction", "evidenceRef": "eval-142"},
    {"id": "P-resource", "timeBudgetMs": 3000, "tokenBudget": 6000},
    {"id": "P-dependency", "relation": "requires", "target": "tool-permission-B"},
    {"id": "P-uncertainty", "interval": [0.61, 0.84], "method": "declared-calibration-method"}
  ],
  "worldTime": "2026-11-05T00:00:00Z",
  "recordedAt": "2026-11-05T00:00:01Z"
}
```

All values above are illustrative synthetic data, not measured results.

## 4. Self-model minimal kernel

An SME candidate requires at least:

1. **Referent binding:** The self-model identifies which entity it models, under an explicit identity contract.
2. **Perspective declarations:** Claims are typed and scoped, with provenance and uncertainty where applicable.
3. **Action/observation coupling:** The entity can relate at least some actions to subsequent observations.
4. **Prediction or expectation:** At least one self-relevant prediction is testable.
5. **Residual accounting:** Discrepancies are recorded, including ambiguous and negative evidence.
6. **Controlled revision:** The model can be revised with versioned decisions and rollback or supersession semantics.

These are **candidate functional requirements** for this case, not a universal definition of selfhood. They may be narrowed or revised under the Definition Evolution Loop (DEL).

A conceptual state can be written as

\[
S_t=(I, M_t, G_t, C_t, H_t),
\]

where \(I\) is the identity reference, \(M_t\) the multi-perspective self-model, \(G_t\) authorized goals, \(C_t\) operational constraints, and \(H_t\) a provenance-bearing history. With action \(a_t\) and observation \(o_{t+1}\):

\[
a_t=\pi(M_t,G_t,C_t), \qquad
r_{t+1}=\operatorname{Compare}(\widehat{o}_{t+1},o_{t+1}),
\]

\[
M_{t+1}=\operatorname{Revise}(M_t,r_{t+1},E_{t+1},C_t).
\]

`Compare` must declare its semantics; it need not return a scalar distance. `Revise` may choose **no change** when evidence is insufficient.

## 5. WE-HDT and MLIU roles

**WE-HDT** provides perspective-aware addressing of observations, task contexts, capability estimates, dependency relations, and residuals. It does not require every self-model component to be physically embedded in one tree. The indexing hierarchy and intelligence abstraction hierarchy remain separate.

**MLIU** is a logical intelligence unit with a bounded capability contract:

```text
SelfModelMLIU {
  entityRef
  perspectiveId
  perspectiveContract
  modelVersion
  observations[]
  predictions[]
  evidenceRefs[]
  uncertainty
  residualRefs[]
  openQuestions[]
  supportedOperations[]
  resourceBudget
  provenance
  relayInterfaces[]
}
```

Six candidate operations:

- **Locate:** Retrieve the relevant self-model perspective or evidence record.
- **Resolve:** Interpret claims within declared semantic and temporal scopes.
- **Relate:** Connect self-assessments to task contexts, actions, and external evaluations.
- **Infer:** Produce explicitly qualified predictions about capability or resource needs.
- **Question:** Generate testable questions from residuals and contradictions.
- **Evolve:** Propose a versioned, constrained model or index change.

MLIUs need not be autonomous agents. Shared services, lazy activation, and bounded execution are valid implementations.

## 6. Two-Ways CCC in a self-modeling loop

### 6.1 Forward direction

Given task context \(q\), select relevant perspectives, estimate expected outcome, choose an authorized action, and record the prediction and its provenance.

```text
Task -> Locate perspectives -> Evaluate conditions
     -> Predict outcome -> Execute authorized action
     -> Observe -> Compare -> Residual record
```

### 6.2 Reverse direction

A discrepancy triggers structured questions rather than an immediate rewrite:

```text
Residual -> Check measurement / logging / task shift
         -> Search missing conditions and relations
         -> Propose candidate perspective
         -> Validate independently
         -> Accept, reject, defer, or rollback
```

Example: The agent predicts high accuracy on a document task but fails when the document contains nested tables. A candidate `P-layout-complexity` perspective may explain the discrepancy. This is a **hypothesis**, not an established causal explanation. Validation requires controlled task variation and independent evaluation.

### 6.3 Safety and epistemic gates

A reverse trigger must not silently change goals, permissions, or identity policy. Candidate discoveries carry uncertainty and are tested against simpler explanations (sampling error, instrumentation defects, data leakage, evaluator mismatch).

## 7. Delta taxonomy and CDE

| Delta type | Example | Interpretation |
|---|---|---|
| World Delta | Tool becomes unavailable | Environment or actual entity state changed |
| Observation Delta | Previous measurement corrected | Recorded evidence changed |
| Knowledge Delta | Capability estimate recalibrated | Belief/model changed |
| Structural Delta | New perspective index introduced | Representation or indexing architecture changed |
| Operational Delta | Authorized execution strategy switched | System policy/execution changed |

A **CDE proposal** is a typed transition with preconditions, constraints, provenance, validation criteria, and rollback/supersession handling. Not every delta is reversible in the world; reverting a knowledge record does not reverse a past action.

Candidate operations: `ADD_PERSPECTIVE`, `RECALIBRATE`, `SPLIT_CONTEXT`, `MERGE_PERSPECTIVES`, `REINDEX`, `DEPRECATE`, `ROLLBACK_MODEL`.

For example, a `RECALIBRATE(P-capability)` proposal must specify the evaluation sample, model version, calibration method, and impact on dependent policies. A `SPLIT_CONTEXT` proposal must establish that separate task contexts improve held-out prediction without unjustified complexity.

## 8. Multi-perspective conflicts

A self-report may conflict with an external evaluator, and both may conflict with recent operational logs. The system should preserve all three observations, rather than overwrite one with another.

A conflict record should include:

```json
{
  "conflictId": "conflict-017",
  "entityRef": "agent-sandbox-01",
  "claims": ["self-estimate-52", "external-eval-142", "run-log-203"],
  "perspectives": ["P-self-claim", "P-external-view", "P-history"],
  "possibleExplanations": ["task-distribution-shift", "miscalibration", "evaluator-error"],
  "status": "unresolved",
  "nextTest": "held-out-task-stratification"
}
```

No source is declared authoritative without a justified evidence policy. Disagreement is a research residual, not proof that a new latent property exists.

## 9. Experimental conditions and baselines

Four matched conditions use the same task corpus, tools, execution budget, and evaluation protocol:

| Condition | Description | Purpose |
|---|---|---|
| B0 — Static | Fixed self-description, no model revision | Baseline |
| B1 — Single perspective | One adaptive capability estimate | Isolate adaptation benefit |
| B2 — Multi-perspective | Typed perspectives, residuals, controlled revisions | Test representation benefit |
| B3 — Multi-perspective + relay | B2 plus versioned transfer of findings and failures | Test collective-learning contribution |

Additional ablations: B2 without residual registry; B2 without reverse CCC; B2 without uncertainty; B2 without revision gates. Where feasible, include a strong conventional contextual predictor and a task-specific calibration model to avoid comparing only against weak baselines.

### 9.1 Workload

Use synthetic and appropriately licensed benchmark tasks with variations in ambiguity, document structure, tool dependencies, and computational limits. Partition by task family and time to reduce leakage. Include distribution shift and adversarially misleading self-reports.

### 9.2 Metrics

- **Predictive calibration:** Brier score, expected calibration error, coverage of declared intervals.
- **Decision quality:** Task success and utility under equal resource budgets.
- **Residual utility:** Fraction of flagged discrepancies yielding independently reproducible explanatory gain.
- **Discovery precision:** Validated candidate perspectives / all proposed perspectives.
- **Robustness:** Performance under shift, noise, missing observations, and evaluator disagreement.
- **Governance:** Unauthorized changes, contract violations, and rollback correctness.
- **Overhead:** Runtime, memory, indexing cost, and human review effort.
- **Relay transfer:** Out-of-sample improvement for receiving agents, with negative transfer reported.

Report confidence intervals and per-context breakdowns; do not infer causality from correlation alone. No empirical performance claims are made in this case document.

## 10. Conformance tests

| ID | Requirement | Expected result |
|---|---|---|
| CT-001 | Stable identity under capability revision | Entity reference unchanged |
| CT-002 | Identity split/merge is explicit | No silent rebinding |
| CT-003 | Perspective type declared | Invalid/missing type rejected |
| CT-004 | Directional relation not treated as metric | Metric-only pruning disallowed |
| CT-005 | Observation provenance | Source and version traceable |
| CT-006 | World and knowledge time separated | No conflation of timestamps |
| CT-007 | Predictions recorded before outcomes | No retrospective leakage |
| CT-008 | Residual includes comparison semantics | Undefined differences rejected |
| CT-009 | Conflicting self/external claims preserved | No silent overwrite |
| CT-010 | Reverse CCC creates candidates, not facts | Validation state retained |
| CT-011 | Candidate perspective has independent test | Promotion blocked otherwise |
| CT-012 | Insufficient evidence | Valid no-change decision |
| CT-013 | CDE change respects resource budget | Violations rejected |
| CT-014 | Goal/permission changes require authorization | No unauthorized evolution |
| CT-015 | Versioned rollback | Previous model reconstructable |
| CT-016 | External tool failure | World Delta not mislabeled as model error |
| CT-017 | Repeated contradictory evidence | Residual reopened, not erased |
| CT-018 | Self-model is not treated as consciousness evidence | Scope claim enforced |
| CT-019 | Relay carries counterexamples and limitations | Incomplete payload rejected |
| CT-020 | No negative-transfer concealment | Regression results preserved |
| CT-021 | Indexing hierarchy separated from abstraction | Physical tree location not assumed |
| CT-022 | Missing perspective | Graceful fallback with uncertainty |

Passing these tests would establish specified functional conformance, **not** prove general intelligence or subjective experience.

## 11. Counterexamples and definition stress tests

**CE-001 — Mere self-reference.** A static program prints its own name. It references itself but lacks prediction, evidence, or revision. It should not satisfy this case's SME contract.

**CE-002 — Accurate self-description without self-action.** An external monitoring dashboard predicts agent performance accurately. It is a model *of* an entity, but not necessarily a model maintained *by* that entity. Clarify the locus of model maintenance and policy coupling.

**CE-003 — Incorrect self-confidence.** An agent persistently overestimates competence. Self-reports must not override external evidence.

**CE-004 — Distribution shift.** A capability estimate deteriorates after task changes. The failure may be a context mismatch, not a defect in the self-model kernel.

**CE-005 — Unobservable internals.** The agent lacks access to some internal causes. Functional self-modeling must allow partial observability and uncertainty.

**CE-006 — Contradictory perspectives.** Internal and external views disagree. Preserve evidence and test the disagreement.

**CE-007 — Non-Euclidean self-properties.** Identity commitments, dependencies, and goals do not admit Euclidean distance by default.

**CE-008 — Self-modification without authorization.** An agent changes safety constraints to improve its reported score. Such a change violates governance even if task accuracy rises.

**CE-009 — Reversible representation, irreversible action.** Restoring a model snapshot cannot undo a previously sent message or external action.

**CE-010 — Consciousness inference.** A system with recursive self-modeling says it is conscious. The claim does not follow from the observed algorithmic structure.

**CE-011 — Overfitted perspective creation.** A new feature explains training residuals but harms held-out performance. Reject or defer promotion.

**CE-012 — Relay contamination.** Shared self-assessments create correlated errors across agents. Require independent evaluation and provenance.

These counterexamples are inputs to DEL and should be preserved even when a later revision resolves them.

## 12. Testable hypotheses

- **H-001 (Calibration):** B2 yields lower held-out prediction error than B1 under matched resources on heterogeneous tasks.
- **H-002 (Decision quality):** B2 improves resource-constrained task selection relative to B0 and B1.
- **H-003 (Residual discovery):** Reverse CCC increases the number of independently validated missing-context hypotheses compared with a non-reverse ablation.
- **H-004 (Uncertainty):** Explicit uncertainty handling reduces harmful overconfident decisions under distribution shift.
- **H-005 (Governance):** Contract-gated CDE reduces unauthorized or invalid model revisions compared with unconstrained adaptation.
- **H-006 (Relay):** B3 improves transfer on held-out task families compared with B2, after accounting for relay overhead.
- **H-007 (Complexity):** Gains from additional perspectives plateau or reverse under some workloads, yielding measurable complexity tradeoffs.

Each hypothesis requires a preregistered primary metric, matched baseline, failure threshold, and replication plan before empirical claims are made.

## 13. Validation roadmap

**Phase 0 — Contract review.** Align identity, perspective, residual, and delta terminology with SPEC-001 through SPEC-006; register unresolved ambiguities.

**Phase 1 — Synthetic fixtures.** Create reproducible action–observation traces, contradictory perspectives, and controlled capability shifts.

**Phase 2 — Conformance.** Execute CT-001 through CT-022; preserve failures and revised contract versions.

**Phase 3 — Baselines and ablations.** Compare B0–B3 and targeted ablations under matched budgets and independent held-out data.

**Phase 4 — Stress testing.** Evaluate missing data, adversarial reports, distribution shift, tool failures, irreversible actions, and unsafe revision attempts.

**Phase 5 — Collective relay.** Transfer validated and invalidated discoveries to independent agents; quantify transfer and negative transfer.

**Phase 6 — Definition evolution.** Use counterexamples to revise the SME minimal kernel or extension contracts, then rerun regression tests.

## 14. Collective Learning Relay record

A proposed research relay package contains:

```yaml
relay_id: WE-SIO-CASE-005-RELAY-001
source_case: CASE-005
status: hypothesis-and-validation-plan
entity_scope: bounded-software-agent
claims:
  - multi-perspective-self-modeling-is-operationally-testable
  - self-modeling-does-not-establish-subjective-experience
hypotheses: [H-001, H-002, H-003, H-004, H-005, H-006, H-007]
conformance: [CT-001, CT-022]
negative_evidence: [] # populate with actual results; never imply none exists
counterexamples: [CE-001, CE-012]
known_limits:
  - partial_observability
  - benchmark_dependency
  - unverified_transfer_gain
next_actions:
  - implement_synthetic_fixtures
  - preregister_baselines
  - run_independent_validation
```

The `conformance` range above denotes endpoints for compact illustration, **not** a claim that only two tests exist or that tests have passed. Full test coverage is CT-001–CT-022. A production relay must enumerate its actual results and status explicitly.

## 15. Connections to the SI research ecosystem

- **WE-SIO-002:** Entity identity and typed perspective indices.
- **WE-SIO-003:** Hybrid indexing and perspective-aware resolution.
- **WE-SIO-005:** MLIU and six SI operations.
- **WE-SIO-006:** Two-Ways CCC and cross-perspective questions.
- **WE-SIO-007 / 008:** Residual-first discovery and perspective evolution.
- **WE-SIO-009:** World/knowledge/structural deltas and CDE.
- **WE-SIO-010:** Self-modeling concepts and boundaries.
- **WE-SIO-011:** Minimal kernel, contracts, and definition evolution.
- **WE-SIO-012:** Collective Learning Relay Piece and research trace.
- **SSI:** Subjective Structural Intelligence provides a distinct research context for subject boundaries, identity history, and valuation; this case does not establish consciousness.
- **SIF:** Localization and addressing may use WE-HDT as a candidate pillar, subject to validation.
- **AQSI / UIERU:** Candidate autonomous questioning and multi-agent relay interfaces.

## 16. Explicit leftovers and open questions

1. Which minimal functional requirements distinguish a self-modeling entity from a passive self-description?
2. How should an agent identify its own causal contribution when observations are confounded?
3. What self-model properties are accessible only through external evaluation?
4. How should contradictory self/other perspectives be weighted without circular authority?
5. Can model revision be proven safe under incomplete world models?
6. When does a new perspective yield genuine explanatory gain rather than overfitting?
7. What is the smallest useful MLIU implementation for self-modeling?
8. How can collective relay avoid propagating shared miscalibration?
9. Which capabilities require identity continuity, and which tolerate entity splitting or replacement?
10. How should the SME/SSE boundary be studied without equating behavioral sophistication with experience?
11. What distinguishes CDE-driven self-model evolution from conventional adaptive state estimation?
12. How should irreversible external actions be governed when the model itself is revisable?

These questions are deliberately unresolved and should be tracked in `research-trace/UNRESOLVED-RESIDUALS.md` and the hypothesis/counterexample registries.

## 17. Figure integration

Recommended insertion: **Fig-010 — From WE to Self-Modeling Entity and Collective Relay**, following Section 2 or Section 6. Optionally cross-reference **Fig-008 — World Delta vs Epistemic Delta** in Section 7 and **Fig-009 — Definition Evolution Loop** in Section 13. Figures are planned research illustrations, not experimental evidence.

## 18. Conclusion

This case proposes a bounded, testable transition from multi-perspective World Entity representation to functional self-modeling. Its central contribution is not the assertion that recursive self-modeling creates consciousness. Rather, it is an explicit experimental and contractual framework for relating self-description, observation, prediction, residuals, perspective discovery, constrained model revision, and collective research relay.

**A self-model is an accountable hypothesis about an entity, not the entity itself.** Its value must be measured through calibration, decision quality, robustness, governance, and independently validated transfer. Failures, counterexamples, and unresolved questions are first-class outputs of the research.

---

*WE-SIO v0.1.0 — Research case. All numerical examples are synthetic; no experiments or clinical claims are reported.*
