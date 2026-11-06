# CASE-003 — Clinical Treatment-Response Residuals

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Case / Hypothesis  
**Status:** Proposed research protocol; no clinical or performance claims validated  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Related:** WE-SIO-002, WE-SIO-005–009, WE-SIO-011–012; SPEC-001, SPEC-004–006

> **Research-use-only boundary.** This case is a methodological thought experiment and prospective validation design, not a diagnostic tool, clinical decision rule, treatment recommendation, or evidence that WE-SIO improves patient outcomes. Any future use of patient data requires appropriate governance, privacy safeguards, expert oversight, and applicable approvals.

## 1. Purpose and Research Question

Patients receiving the same nominal intervention can exhibit different outcomes. A model may predict an expected response conditional on observed covariates, yet some observed responses diverge substantially. Such discrepancies—**residuals**—may reflect measurement error, model misspecification, selection effects, confounding, heterogeneous mechanisms, changes in care delivery, or genuine but currently unmodeled structure.

This case asks whether WE-SIO can **preserve, organize, compare, and investigate** these residuals across multiple perspectives without converting unexplained variation into unsupported causal or clinical claims.

**Primary research question:** Can a provenance-preserving Residual Registry combined with Two-Ways CCC and candidate Perspective Discovery produce more reproducible, testable hypotheses than an otherwise comparable conventional analysis workflow?

**Null hypothesis:** The WE-SIO workflow provides no measurable improvement in preregistered hypothesis quality, reproducibility, or discovery efficiency once equivalent analyst effort, data, and validation resources are controlled.

## 2. Scope and Non-Claims

In scope: retrospective or synthetic datasets, response prediction, residual quality checks, cross-perspective comparisons, hypothesis tracking, validation gates, and auditability.

Out of scope: assigning treatment to patients, claiming treatment efficacy, individual risk advice, automated diagnosis, and inferring biological mechanisms solely from correlations.

Clinical outcome definitions, treatment exposure, eligibility, follow-up windows, and missingness handling must be specified **before** looking for patterns. This case does not assume that residual-first science is new; residual diagnostics, subgroup analysis, causal inference, and anomaly detection are established methods. The proposed contribution is a structured, versioned, cross-perspective research relay.

## 3. World Entity and Perspective Model

A patient-related research record is a **representation** of a real-world entity, not the entity itself. Identifiers are study-scoped pseudonyms and must not be interpreted as proof of stable real-world identity across institutions.

Candidate entity types:

| Entity type | Example identity | Perspectives | Important boundary |
|---|---|---|---|
| Participant | Study pseudonym | Baseline characteristics, history, measurements | Consent and linkage constraints |
| Treatment episode | Episode ID | Exposure, dose, timing, adherence | Exposure may be misclassified |
| Observation | Measurement ID | Instrument, value, time, uncertainty | Measurement is not ground truth |
| Outcome episode | Outcome ID | Endpoint, time horizon, censoring | Outcome ascertainment bias |
| Care context | Site/time cohort | Workflow, clinician, access, policy | Context may confound comparisons |
| Research hypothesis | Hypothesis ID | Claim, assumptions, evidence, tests | Hypothesis is not an established fact |

### 3.1 Perspective categories

- **Euclidean/numeric:** meaningful normalized continuous measurements where a distance operation is explicitly justified; unit and scale must be recorded.
- **Mathematical metric:** distances with validated domain and required metric properties; no triangle-inequality pruning without a valid guarantee.
- **Similarity:** scores that may lack metric axioms; keep their semantics distinct.
- **Relational:** co-occurring conditions, exposure pathways, family or institutional relationships where authorized.
- **Directional/temporal:** treatment-before-outcome, event sequences, asymmetric associations, or proposed causal directions; temporal ordering alone does not establish causation.
- **Epistemic:** confidence, missingness, source reliability, disagreement, and model-version metadata.

## 4. Illustrative Synthetic Dataset

The following records are **fictional** and exist only to demonstrate schema and workflow; numbers are not clinical estimates.

| Participant | Episode | Predicted standardized response | Observed standardized response | Residual | Context |
|---|---|---:|---:|---:|---|
| P-101 | T-01 | 0.60 | 0.58 | -0.02 | Site A |
| P-102 | T-02 | 0.55 | 0.10 | -0.45 | Site A |
| P-103 | T-03 | 0.40 | 0.76 | +0.36 | Site B |
| P-104 | T-04 | 0.65 | 0.61 | -0.04 | Site B |
| P-105 | T-05 | 0.50 | 0.08 | -0.42 | Site A |

Define a residual for a preregistered response scale and horizon:

\[
r_i = y_i^{\mathrm{observed}} - \widehat{y}_i^{\mathrm{predicted}}.
\]

A large \(|r_i|\) is a **screening signal**, not evidence of a treatment effect, causal subgroup, data fraud, or novel mechanism. Residual comparability requires consistent outcome definition, time horizon, calibration, and model version. If predictive uncertainty is available, a standardized or predictive-distribution-aware residual may be more appropriate than raw magnitude.

## 5. Baseline Analysis Before WE-SIO

A credible evaluation must begin with ordinary best practices:

1. Define a clinically meaningful, ethically permissible research endpoint and estimand.
2. Separate development, validation, and held-out test cohorts at the patient and, where relevant, site/time levels.
3. Fit transparent baseline prediction models; check calibration, discrimination or error, subgroup performance, and data leakage.
4. Assess measurement quality, censoring, missing data mechanisms, distribution shift, and selection bias.
5. Use established residual diagnostics and preplanned exploratory analysis.
6. Preserve a conventional analysis trail as the **matched comparator**.

WE-SIO must demonstrate added value against this baseline, not against an intentionally weak straw man.

## 6. WE-SIO Research Architecture

```text
Governed data sources
        |
        v
WE Entity / Perspective Registry
        |
        v
Validated baseline model and outcome definition
        |
        v
Observation vs expectation comparison
        |
        v
Residual Registry ----> quality / confounding / bias checks
        |                               |
        |                     artifact or uncertainty?
        |                               |
        v                               v
Two-Ways CCC reverse inquiry       document and retain
        |
        v
Candidate relational / metric / temporal perspectives
        |
        v
Hypothesis Registry + negative controls + counterexamples
        |
        v
Independent validation / replication
        |
        v
Promotion, revision, rejection, or unresolved residual
        |
        v
Collective Learning Relay (provenance + next questions)
```

### 6.1 Forward CCC

Given a study question, inclusion criteria, exposure and outcome definitions, and authorized perspectives, identify candidate records and produce an **accountable prediction or comparison**. Record retrieval coverage and whether the result is exact or approximate.

### 6.2 Reverse CCC

Given an unexplained, quality-checked residual pattern, propose which missing conditioning variables, measurement processes, relational links, or temporal distinctions could explain it. This process produces **questions and candidate hypotheses**, not accepted explanations.

### 6.3 Metric Leaf Intelligence Unit (MLIU)

An MLIU may attach to a cohort, observation group, or hypothesis perspective. It offers six bounded operations:

| Operation | Research role | Required guardrail |
|---|---|---|
| Locate | Find eligible observations | Cohort and index-coverage guarantees |
| Resolve | Interpret measurement/endpoint | Units, timing, provenance |
| Relate | Link exposures, contexts, outcomes | Authorized linkage and directionality |
| Infer | Generate model-based estimates | Assumptions and uncertainty |
| Question | Propose residual explanations | Explicit hypothesis status |
| Evolve | Propose schema/perspective revisions | Validation, versioning, rollback |

A leaf is a logical unit; it need not be a dedicated autonomous agent.

## 7. Residual Registry Contract

A candidate record (illustrative YAML):

```yaml
residual_id: R-CLIN-0007
status: quality_review_pending
entity_refs: [P-102, T-02]
endpoint_id: endpoint-response-v1
observation_time: 2026-01-15T00:00:00Z
prediction_model_version: baseline-v1
observed_value: 0.10
predicted_value: 0.55
residual_value: -0.45
scale: synthetic-standardized-response
uncertainty:
  method: pending
  interval: null
provenance:
  observation_source: synthetic-example
  source_hash: null
quality_flags: [needs-measurement-review]
confounding_checks: pending
candidate_explanations: []
validation_status: untested
privacy_class: synthetic
next_question: Could outcome timing or measurement process explain this discrepancy?
```

**Required invariants:** immutable original observation references; explicit model/version and time window; separation of observed from inferred; missingness visible; status transitions audited; corrections append rather than silently overwrite; no automatic promotion of hypotheses.

### 7.1 Residual triage

- **Data/measurement:** transcription, instrument drift, incompatible units, timing mismatch.
- **Statistical/model:** miscalibration, nonlinearity, covariate shift, sparse subgroup, overfitting.
- **Study design:** selection bias, confounding, informative censoring, competing events.
- **Unexplained:** remains open after specified checks; may motivate further study.

A residual may belong to several categories simultaneously. A registry should not force premature exclusive classification.

## 8. Candidate Discovery and Perspective Evolution

Consider a synthetic cluster of negative residuals at one site. Candidate explanations might include outcome assessment timing, baseline severity not captured by the model, missing adherence measurements, or site-specific recording practices. These are alternatives to test, **not findings**.

A candidate perspective descriptor should include:

```yaml
perspective_id: candidate-assessment-lag-v1
kind: temporal_measurement
semantic_definition: elapsed time between intervention and outcome assessment
units: days
applicability: episodes with reliable timestamps
missingness_policy: explicit_missing
comparison_operator: numeric_difference
metric_claim: false
hypothesis_ids: [H-CLIN-001]
evidence_status: exploratory
version: 1
promotion_status: candidate
```

Candidate evolution actions: `ADD`, `REFINE`, `SPLIT`, `MERGE`, `RECALIBRATE`, `DEPRECATE`, `ROLLBACK`. Each is a **Knowledge or Structural Delta**, not proof that the physical world changed.

## 9. Hypothesis and Counterexample Registry

| ID | Candidate hypothesis | Disconfirming evidence to seek |
|---|---|---|
| H-CLIN-001 | Outcome timing explains a residual cluster | Pattern persists after timing harmonization |
| H-CLIN-002 | A measurement artifact contributes | Independent remeasurement agrees with original |
| H-CLIN-003 | An omitted baseline factor improves prediction | No improvement in held-out cohorts |
| H-CLIN-004 | Site-specific process matters | Effect vanishes in prospective site-balanced replication |
| H-CLIN-005 | A relational interaction improves fit | Interaction unstable across cohorts or sensitive to confounding |

For each hypothesis retain origin residuals, dataset/model versions, assumptions, alternative explanations, tests, negative controls, outcomes, and explicit unresolved issues. Hypotheses may be split or narrowed following counterexamples; no requirement that every residual eventually receive a satisfying narrative.

## 10. Validation Gates

**Gate 0 — Governance:** permitted data use, ethics review where required, de-identification, access control, and appropriate clinical/statistical oversight.

**Gate 1 — Semantics:** stable endpoint and exposure definitions, temporal ordering, units, cohort eligibility, and missingness.

**Gate 2 — Residual integrity:** calibration, measurement review, uncertainty, and baseline comparison.

**Gate 3 — Hypothesis validity:** prespecified testing where possible, multiplicity handling, sensitivity analyses, negative controls, and plausible alternatives.

**Gate 4 — Independent evidence:** held-out site/time cohorts, external replication, or prospective validation when feasible.

**Gate 5 — Operational and epistemic promotion:** promote a perspective only with documented scope, evidence level, failure conditions, owner, and rollback plan. Scientific/causal conclusions require stronger evidence than predictive improvement alone.

Failed gates retain the candidate as rejected, deferred, or unresolved with provenance.

## 11. Conformance Test Suite (Proposed)

| Test ID | Requirement | Pass criterion |
|---|---|---|
| CT-001 | Entity vs representation | Pseudonym and source identity remain distinct |
| CT-002 | Endpoint semantics | All compared residuals share compatible endpoint definitions |
| CT-003 | Time consistency | No post-outcome variable leaks into prediction |
| CT-004 | Prediction provenance | Every residual points to immutable model/version |
| CT-005 | Observation provenance | Every observed value has authorized source lineage |
| CT-006 | Missingness | Missing values are never silently encoded as zero |
| CT-007 | Uncertainty | Reported precision matches available uncertainty method |
| CT-008 | Quality triage | Measurement anomalies can be flagged without causal claims |
| CT-009 | Directionality | Temporal relation is not mislabeled causal |
| CT-010 | Candidate status | Exploratory perspectives are not treated as validated |
| CT-011 | Counterexamples | Disconfirming evidence is retained and linked |
| CT-012 | Leakage prevention | Held-out data cannot drive candidate selection and final scoring simultaneously |
| CT-013 | Multiple testing | Search multiplicity is recorded and addressed |
| CT-014 | Retrieval coverage | Approximate retrieval is not represented as exhaustive |
| CT-015 | Delta classification | World, observation, knowledge, structural changes are distinguished |
| CT-016 | Version rollback | Prior registry state can be reconstructed |
| CT-017 | Privacy | Unauthorized cross-site linkage is rejected |
| CT-018 | Relay reproducibility | Another authorized team can reconstruct the hypothesis trail |
| CT-019 | Failure reporting | Negative results and unresolved residuals remain discoverable |
| CT-020 | Clinical boundary | No automatic treatment recommendation or deployment claim |

These are **candidate tests**, not evidence of an implemented or passing system.

## 12. Benchmark Design

### 12.1 Matched comparison arms

- **B0:** conventional predictive modeling and standard residual diagnostics.
- **B1:** B0 plus structured, versioned residual tracking without automated reverse CCC.
- **B2:** B1 plus WE-SIO Two-Ways CCC and candidate perspective generation.
- **B3:** B2 plus Collective Learning Relay across independent research teams.

All arms receive equivalent underlying data, privacy constraints, compute/accounting, analyst time, and access to domain experts. The experiment should distinguish the benefit of **better recordkeeping** from the benefit of **new discovery operations**.

### 12.2 Outcomes

Primary: preregistered externally validated hypothesis yield per fixed research budget; independent reproducibility of research trail.

Secondary: false-discovery proportion, calibration and held-out prediction change, time to rule out artifacts, cross-site transportability, compute and human review costs, and fraction of unresolved residuals accurately retained.

Report uncertainty intervals, null findings, and stratified results. A higher number of generated hypotheses is not automatically better.

### 12.3 Data strategy

Start with synthetic data containing known planted measurement artifacts and heterogeneous response-generating mechanisms. Then consider suitably governed retrospective de-identified research datasets. Any prospective clinical study requires separate approvals and protocol design. Synthetic success cannot establish clinical utility.

## 13. Falsifiable Research Hypotheses

- **RH-001 — Auditability:** B1 improves reconstruction of the research trail relative to B0.
- **RH-002 — Discovery yield:** B2 increases independently validated hypothesis yield relative to B1 at matched effort.
- **RH-003 — False-discovery control:** B2 does not increase false discoveries beyond a preregistered tolerance.
- **RH-004 — Cross-perspective value:** Relational/temporal candidates add out-of-sample value beyond existing measured covariates.
- **RH-005 — Relay value:** B3 improves cross-team replication relative to B2.
- **RH-006 — Residual retention:** Explicit unresolved-state handling reduces premature explanatory closure without unbounded review cost.
- **RH-007 — Resource discipline:** Candidate pruning and governance keep computation and human review within fixed budgets.

All are hypotheses awaiting evaluation; negative results should revise the architecture rather than be discarded.

## 14. CDE and Definition Evolution

A CDE transition may change a hypothesis status, add a perspective, reindex a cohort, or revise a definition under specified contracts. Such changes should not be conflated with a patient's real-world state.

```text
ResearchState_t
  + proposed Knowledge/Structural Delta
  + applicability, evidence, governance, resource contracts
  -> validated transition or explicit rejection
  -> ResearchState_(t+1) with provenance
```

Definition Evolution Loop: minimal definition → application → counterexample → semantic gap → clarify/narrow/split/refine → regression checks. Example: an initial descriptor incorrectly calls an asymmetric treatment-outcome association a mathematical metric; a counterexample forces reclassification as a directional relation.

## 15. Research Trace and Collective Learning Relay

Recommended records under `research-trace/`:

- `HYPOTHESIS-REGISTRY.md`: RH-001–RH-007, evidence, tests, dispositions.
- `DEFINITION-REGISTRY.md`: endpoint, residual, metric, perspective, and entity semantics with version history.
- `COUNTEREXAMPLE-REGISTRY.md`: failures, leakage, confounding, nonreplication, and misclassification.
- `DECISION-LOG.md`: promotion/rejection decisions and rationale.
- `UNRESOLVED-RESIDUALS.md`: remaining uncertainty and the next discriminating tests.

A relay packet should include a claim, exact cohort/data and code version references (subject to data-use restrictions), provenance, assumptions, supporting and opposing evidence, negative controls, validation status, limitations, and a next action. Never expose participant-level protected information in a public repository.

## 16. Explicit Leftovers and Open Questions

1. Which residual representation is most robust under censoring and non-Gaussian outcomes?
2. How should residuals be compared across heterogeneous endpoints without false equivalence?
3. Can candidate perspective search be controlled against multiple-comparison inflation?
4. What portion of value arises from provenance infrastructure rather than novel inference?
5. How can domain experts reject misleading candidates early without suppressing useful surprises?
6. What formal guarantees can be given for cross-site linkage and retrieval coverage?
7. When does a candidate relational structure warrant a causal study rather than further predictive modeling?
8. How should privacy-preserving relays represent evidence that cannot be shared publicly?
9. What triggers a definition revision instead of a model recalibration?
10. Under what empirical conditions should the WE-SIO clinical use case be abandoned?

## 17. Proposed Milestones

| Phase | Deliverable | Exit criterion |
|---|---|---|
| P0 | Endpoint, estimand, governance and baseline protocol | Reviewed and preregistered |
| P1 | Synthetic data + residual registry | CT-001–CT-010 evaluated |
| P2 | Two-Ways CCC candidate generation | Held-out evaluation with multiplicity control |
| P3 | Matched B0–B3 benchmark | Reproducible comparison with uncertainty |
| P4 | Independent replication | External team can reproduce findings and failures |
| P5 | Definition/architecture revision | Updated contracts and explicit leftovers |

## 18. Conclusion

Clinical treatment-response heterogeneity offers a demanding **stress test** for WE-SIO: observations are noisy, outcomes are temporally structured, confounding is pervasive, and erroneous claims can cause harm. A credible residual-first framework must therefore make uncertainty and negative evidence more visible—not simply produce more patterns.

The proposed contribution is a **traceable workflow** linking World Entity perspectives, residuals, Two-Ways CCC, candidate metric/relational discovery, validation, and Collective Learning Relay. Whether this yields more reliable discoveries than strong conventional baselines is an empirical question that this case is designed to test.

---

**Suggested figure:** `figures/Fig-007-Residual-Driven-Scientific-Discovery-Loop.png` (after Section 6).  
**License:** Apache-2.0 (repository-level, subject to author confirmation).  
**Citation status:** Research hypothesis; not peer-reviewed or clinically validated.
