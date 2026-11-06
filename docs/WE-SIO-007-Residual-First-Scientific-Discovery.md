# WE-SIO-007 — Residual-First Scientific Discovery

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Hypothesis  
**Status:** Exploratory; not an experimentally validated discovery system  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

## Abstract

Scientific models simplify reality. Their residuals—differences between observations and expectations—may reflect measurement error, confounding, distribution shift, incomplete representation, or a genuine missing mechanism. This paper proposes **Residual-First Scientific Discovery (RFSD)** as a WE-SIO research architecture: preserve residuals as addressable, evidence-linked, perspective-aware objects; use them to drive questions and candidate explanations; and require independent validation before promoting hypotheses into models or operational decisions. This updated version explicitly separates established knowledge, open questions, and qualified residual evidence, and proposes a Residual Evidence Registry (RER) rather than an untyped residual bucket. The proposal integrates World Entity (WE) representations, WE Hybrid Differential Trees (WE-HDT), Metric-Leaf Intelligence Units (MLIU), Two-Ways CCC, Constrained Delta Evolution (CDE), and Collective Learning Relay. The claim is architectural, not that residual analysis or anomaly-driven science is new. The research question is whether interoperable residual records and governed bidirectional exploration improve discovery quality, reproducibility, or efficiency relative to established workflows.

## 1. Research Origin and Scope

WE-SIO began with variable-size block indexing and the possibility of representing entities through multiple perspective indices. In an ordinary retrieval system, a mismatch can be treated as an unsuccessful query. In a scientific system, a mismatch may be the beginning of a research question.

Consider a group of patients with similar measured profiles but different treatment outcomes. The difference may be attributable to an unmeasured biological factor, an interaction, nonadherence, selection bias, or noise. A responsible system should neither discard the mismatch nor proclaim a new causal mechanism. It should preserve what was expected, what was observed, why the comparison was considered meaningful, and which alternatives remain unresolved.

**Scope:** structured observation, hypothesis formation, controlled comparison, and provenance-preserving research relay. **Out of scope:** autonomous proof of scientific laws, replacement of domain expertise, unreviewed clinical decisions, and claims of guaranteed novelty.

## 2. Core Distinctions

### 2.1 Residual is not synonymous with discovery

For observation \(y\), expectation \(\hat y\), and a comparison rule \(d_p\) appropriate to perspective \(p\), a residual can be written:

\[
 r_p = d_p(y,\hat y).
\]

For numerical predictions, a signed difference \(r=y-\hat y\) may be useful. For categorical, relational, directional, or uncertain observations, a scalar subtraction may be invalid; the residual can instead be a structured discrepancy with a declared comparator and uncertainty model.

A residual is **evidence of a gap between observation and expectation**, not necessarily evidence of a new phenomenon.

### 2.2 Four different things that must not be collapsed

1. **World event:** what happened, whether or not observed.
2. **Observation:** what a measurement or source reported.
3. **Expectation:** what a model or hypothesis predicted under stated conditions.
4. **Residual:** the documented discrepancy under a specific comparison contract.

An epistemic revision may change the expectation without changing the world. A sensor correction may change the observation without any new world event. Therefore, residual histories must retain versions rather than silently overwrite prior records.

### 2.3 Epistemic separation: unknown is not residual

Three logically distinct views should be maintained for each entity, perspective, applicability scope, and version:

- **Established Knowledge:** evidence-supported statements with explicit scope, uncertainty, and revision rights; established does not mean infallible.
- **Open Knowledge:** unanswered questions, missing measurements, candidate explanations, and unvalidated metrics, whether or not a discrepancy has been observed.
- **Residual Evidence:** a documented discrepancy against an identified expectation, constraint, model, or explanation baseline, with evidence and comparison semantics.

A missing value, SQL `NULL`, unsupported claim, or unexamined hypothesis is **not** automatically a residual. An established statement may be revised after a qualifying residual is independently evaluated; an open question may be motivated by a residual without becoming a residual itself. These are *logical epistemic views*, not mandatory separate physical tables. Their statuses are context- and perspective-dependent.

### 2.4 Established foundations and proposed extension

Residual diagnostics, anomaly detection, model criticism, outlier analysis, active learning, causal inference, and scientific abduction already exist. WE-SIO's **hypothesized contribution** is their integration into an addressable structural intelligence workflow with explicit perspective contracts, cross-entity relay, and definition evolution. Comparative evaluation is required before asserting an advantage.

## 3. Residual as a First-Class Research Object

A candidate residual record is:

```yaml
ResidualRecord:
  residualId: immutable identifier
  entityRefs: [versioned entity references]
  perspectiveId: perspective descriptor and version
  context: task, cohort, environment, time window
  expectation:
    modelRef: model/version
    prediction: value or structured claim
    assumptions: []
  observation:
    value: value or structured claim
    sourceRefs: []
    measurementProtocol: protocol/version
  comparator:
    type: numeric | metric | relational | directional | other
    contractRef: identifier/version
  discrepancy:
    representation: signed value | interval | structured mismatch
    magnitudeOrPriority: optional calibrated score
  uncertainty:
    measurement: optional
    model: optional
    sampling: optional
  evidenceRefs: []
  alternativeExplanations: []
  confoundersAndBiases: []
  privacyAndAccessPolicy: policy reference
  status: observed | triaged | investigated | tested | resolved | unresolved
  hypothesisRefs: []
  provenance:
    creator: actor/system
    createdAt: timestamp
    lineage: []
  version: version identifier
```

This is a **candidate schema**, not a finalized universal ontology. Mandatory fields depend on the operation and data governance contract. The system should distinguish missing data from a measured zero, an absent relation from a disproved relation, and untested from falsified.

### 3.1 Residual identity and equivalence

Two residuals with similar numerical magnitudes need not represent the same phenomenon. Identity requires provenance and comparison context. Similarity or clustering is a separate, versioned hypothesis: `sameMechanism?` must not be inferred from `similarPattern?` without further evidence.

### 3.2 Lifecycle

`Observed → Triaged → Investigated → Hypothesis-linked → Tested → {Supported, Rejected, Inconclusive} → Archived / Reopened`

A residual may be resolved as measurement error yet remain valuable as a reproducibility or instrumentation case. A rejected hypothesis does not erase the residual. Reopening is allowed when new evidence or a changed perspective warrants it.

## 4. Residual Registry and Structural Addressing

A **Residual Registry** stores residual records and their relationships to entities, perspectives, models, evidence, hypotheses, and experiments. It should support:

- Lookup by entity, cohort, perspective, model version, time, discrepancy type, and status.
- Cross-perspective comparison while preserving comparator semantics.
- Links between residuals, candidate causes, counterexamples, and test outcomes.
- Reproducible query snapshots and audit trails.
- Access controls, redaction, retention policies, and source-specific licensing.

A **Residual Differential Tree** is a possible indexing and exploration layer, not a required physical tree. A graph, relational database, vector index, or hybrid system may implement the same logical contract. WE-HDT can localize candidate entities while the registry addresses residual evidence. The two hierarchies need not coincide.

### 4.1 Indexing without semantic overclaim

A fast approximate index may prioritize review, but a similarity score is not a probability of shared causation. Any approximate candidate generation must report recall and omission risks against a declared benchmark. If complete retrieval is required, the implementation must provide an appropriate exact or verified fallback.

## 5. Residual-First Discovery Loop

The proposed research loop is:

1. **Specify expectation:** identify model, population, perspective, comparator, and uncertainty.
2. **Observe:** capture measurements with provenance and quality indicators.
3. **Construct residual:** preserve discrepancy without forcing an explanation.
4. **Triage:** check instrumentation, missingness, data leakage, sampling bias, and confounding.
5. **Localize:** retrieve relevant entities and comparable residuals through WE-HDT and the registry.
6. **Question:** use MLIU / AQSI to propose competing, testable explanations.
7. **Cross perspectives:** apply Two-Ways CCC to identify missing or contradictory conditions.
8. **Design discriminating tests:** prefer experiments or analyses that separate alternatives.
9. **Validate independently:** preregister where appropriate; use held-out or external data.
10. **Update carefully:** revise model/perspective contracts through controlled epistemic deltas.
11. **Relay:** publish evidence, counterexamples, limitations, and unresolved residuals.

This is not a rigid linear pipeline. Failure in any stage can return the process to earlier assumptions. Budget limits, stop rules, and human review gates prevent unbounded recursive hypothesis generation.

## 6. Two-Ways CCC as a Discovery Interface

**Forward direction:** known perspectives and conditions select entities and generate expected observations. A WE-HDT query may localize a cohort; MLIU operations resolve metric or relational constraints; the comparator produces residuals.

**Backward direction:** a residual prompts a search for alternative conditions, unmodeled relations, changed cohort definitions, candidate perspectives, or errors in existing assumptions. The reverse direction is **hypothesis generation**, not logical inversion of a causal relationship.

Illustrative trace:

```text
Known cohort + known predictors
  → forward CCC → expected response
  → observed response → residual R-17
  → quality/confounding triage
  → reverse CCC → candidate factor F / interaction I
  → competing hypotheses H1, H2, H3
  → independent validation
  → supported revision OR explicit unresolved leftover
```

A reverse search must avoid target leakage: the data used to discover a candidate cannot by itself establish that candidate's predictive generalization.

## 7. Metric and Perspective Discovery

Some residual clusters may suggest that the current feature space is inadequate. Candidate outcomes include:

- A new measurable attribute with an explicit acquisition protocol.
- A composite feature or interaction among existing attributes.
- A revised similarity function with declared mathematical properties.
- A directional or relational descriptor that is **not** a mathematical metric.
- A revised population boundary or context condition.
- No new perspective at all: a corrected model or measurement process may suffice.

A candidate descriptor should carry domain, codomain, units (where applicable), admissible comparisons, uncertainty, provenance, scope, validation evidence, and known failure cases. The label *metric* is reserved for functions satisfying the relevant metric axioms; other comparisons should be called scores, divergences, or relations.

**Promotion rule:** no candidate becomes a stable perspective index solely because it reduces residuals on the discovery dataset. Require baseline comparisons, held-out testing, robustness checks, and regression tests against known counterexamples.

## 8. MLIU Operations and Research Responsibilities

| Operation | Residual-first role | Required guardrail |
|---|---|---|
| Locate | Find comparable entities/residuals | Coverage and recall accounting |
| Resolve | Apply perspective-specific comparison | Valid comparator contract |
| Relate | Link evidence, entities, hypotheses | Directionality and provenance |
| Infer | Generate candidate explanations | Uncertainty and alternatives |
| Question | Form discriminating research questions | Testability and budget |
| Evolve | Propose model/index/definition updates | Validation and rollback |

MLIU is a **logical capability unit**. Implementations may share services or activate reasoning lazily; no independent heavyweight agent is required per residual or leaf.

## 9. Worked Research Scenarios

### 9.1 Clinical treatment-response heterogeneity

**Question:** why do apparently similar patients respond differently to a treatment?

**Inputs:** consented or appropriately governed records, baseline covariates, treatment protocol, outcome definition, time window, and model predictions.

**Residual:** observed outcomes depart from expectations under a specified cohort/perspective.

**Competing explanations:** measurement timing, adherence, disease severity, interactions, selection bias, missing biomarkers, model misspecification, or random variation.

**WE-SIO process:** preserve residual provenance; compare matched or otherwise carefully adjusted cohorts; generate candidate interactions; test with independent datasets and domain review. Observational association must not be promoted to causal treatment advice without an appropriate study design.

**Possible outcome:** a reproducible stratification hypothesis, an improved measurement protocol, or an unresolved discrepancy. All three are legitimate research outputs.

### 9.2 Transportation and routing

A route model predicts travel time, but a subset of trips repeatedly deviates. Reverse exploration considers time-of-day, road closures, vehicle types, weather, and network relationships. WE-HDT may retrieve comparable routes; a new perspective might encode transfer constraints rather than geographic distance. Validate on future trips and compare with established traffic models.

### 9.3 Chess and strategic models

A strategy model predicts an evaluation trajectory but encounters a surprising move. The discrepancy may reflect search-depth limitations, opponent modeling, or evaluation-function defects. This is an **epistemic residual**, not a claim that the rules of chess changed. Chess also stress-tests CDE policies: legal repeated states and adversarial choices show why universal no-delta-reuse is untenable.

## 10. World Delta, Epistemic Delta, and CDE

Define separate change classes:

- **World Delta:** change in the modeled external system, if established by observation/evidence.
- **Observation Delta:** correction, arrival, or retraction of measurements.
- **Epistemic Delta:** change in model, perspective, hypothesis, or confidence.
- **Operational Delta:** change in indexing, computation allocation, or workflow policy.

CDE may coordinate admissible transformations of WE-SIO representations and processes. A candidate transition record is:

```text
Transition = (StateVersion, DeltaType, Preconditions,
              ProposedChange, EvidenceRefs, Constraints,
              ValidationResults, RollbackPlan, NextVersion)
```

This is not an assertion that all world changes are generated by the algorithm. State changes are versioned descriptions; their relationship to physical events must be established separately. Path memory, cycle policy, and admissible reuse are configurable contracts rather than universal prohibitions.

## 11. Scientific Quality, Governance, and Failure Modes

### 11.1 Principal threats

- **Noise mining:** discovering patterns that vanish under replication.
- **Multiple testing:** apparent significance from repeated searches.
- **Confounding:** plausible explanations mistaken for causal effects.
- **Distribution shift:** residuals caused by changed sampling or environment.
- **Selection bias:** only unusual cases retained or surfaced.
- **Measurement drift:** instruments or annotation conventions change.
- **Semantic mismatch:** comparing scores under incompatible perspectives.
- **Privacy leakage:** linking residuals reveals sensitive entity information.
- **Automation bias:** plausible generated hypotheses treated as validated results.
- **Registry accumulation:** growing storage and review costs with little discovery value.

### 11.2 Required controls

Record uncertainty and missingness; use negative controls and null models where appropriate; adjust for multiplicity; separate exploration from confirmation; require domain review for consequential conclusions; enforce access policies; preserve retractions; and allow explicit `inconclusive` and `unresolved` states.

A high-priority residual is a **review priority**, not a high-confidence discovery.

## 12. Candidate Conformance Contracts

**RFSD-C01 — Expectation provenance:** every residual links to a versioned expectation or declares the comparison unavailable.

**RFSD-C02 — Observation provenance:** observation source, time, and measurement protocol are retained.

**RFSD-C03 — Comparator validity:** comparison is defined for the perspective and data types.

**RFSD-C04 — Uncertainty separation:** measured discrepancy is not presented as significance without calibration.

**RFSD-C05 — Identity stability:** residual, entity, and hypothesis identifiers remain distinguishable.

**RFSD-C06 — Version immutability:** updates preserve historical states and lineage.

**RFSD-C07 — Alternative explanations:** triage can record noise, bias, confounding, and model error.

**RFSD-C08 — Discovery/confirmation split:** candidate selection data are distinguished from validation data.

**RFSD-C09 — Explicit inconclusiveness:** untested, rejected, and unresolved are different statuses.

**RFSD-C10 — Perspective compatibility:** cross-metric comparison requires a mapping contract or reports incompatibility.

**RFSD-C11 — Access governance:** sensitive records obey source permissions and minimization policies.

**RFSD-C12 — Controlled evolution:** promoted perspectives/models have validation and rollback records.

**RFSD-C13 — Termination:** recursive search has resource budgets and stop criteria.

**RFSD-C14 — Relay reproducibility:** a downstream researcher can reconstruct the question, inputs, methods, and limitations to the extent permitted by governance.

These are proposed requirements for future `SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`, not claims of existing implementation conformance.

## 13. Testable Hypotheses

**H-RFSD-01 — Traceability:** structured residual records improve the proportion of research findings with reconstructible provenance versus unstructured anomaly logs.

**H-RFSD-02 — Question quality:** residual-linked, cross-perspective hypothesis generation yields more independently testable questions per review-hour than a baseline question-generation workflow.

**H-RFSD-03 — Replication:** explicit counterexample and uncertainty records reduce false promotion of hypotheses on held-out datasets.

**H-RFSD-04 — Cross-domain transfer:** a common residual contract improves reuse of analysis procedures across at least two domains without erasing domain-specific semantics.

**H-RFSD-05 — Search efficiency:** WE-HDT-assisted localization reduces candidate retrieval cost at matched recall relative to suitable database, graph, or vector baselines on selected tasks.

**H-RFSD-06 — Definition evolution:** versioned perspective revisions reduce regression failures compared with unversioned feature/schema changes.

**H-RFSD-07 — Resource allocation:** prioritizing high-information residuals improves validated discovery yield per unit compute or expert time relative to uniform review.

Each hypothesis requires operational metrics, sample sizes, appropriate statistical analysis, and a preregistered or clearly declared exploratory evaluation protocol. Negative results should remain in the relay record.

## 14. Validation Roadmap

### Phase A — Schema and synthetic cases

Implement minimal residual and perspective contracts. Construct synthetic datasets with known noise, confounding, missing variables, and injected anomalies. Test whether the registry preserves distinctions and whether the system avoids labeling known artifacts as discoveries.

### Phase B — Baseline comparisons

Compare against conventional residual diagnostics, SQL/graph retrieval, anomaly detectors, and standard feature engineering. Measure recall, precision of flagged cases, review burden, runtime, and provenance completeness. Do not treat a different interface as evidence of scientific superiority.

### Phase C — Cross-perspective experiments

Use datasets with multiple legitimate representations. Test whether bidirectional CCC generates useful hypotheses without violating comparison contracts. Evaluate held-out generalization and ablate individual components (registry, reverse CCC, MLIU, adaptive blocks).

### Phase D — Domain-reviewed pilots

Conduct controlled pilots in low-risk settings first, such as transport simulation or benchmark games. For biomedical settings, use appropriately governed retrospective research and independent expert oversight before considering any prospective application.

### Phase E — Collective Learning Relay

Publish versioned questions, candidate definitions, conformance outcomes, counterexamples, unresolved residuals, and reproducible evaluation protocols. Refine the kernel only when evidence warrants a change.

## 15. Research Trace and Relay Interfaces

Suggested cross-references:

- `research-trace/HYPOTHESIS-REGISTRY.md`: register H-RFSD-01 through H-RFSD-07 with owners, evidence, and status.
- `research-trace/DEFINITION-REGISTRY.md`: version residual, expectation, comparator, and perspective definitions.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`: preserve false positives and semantic failures.
- `research-trace/DECISION-LOG.md`: document why a perspective or hypothesis was promoted, deferred, or rejected.
- `research-trace/UNRESOLVED-RESIDUALS.md`: retain open anomalies and unanswered methodological questions.
- `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`: formalize schemas and conformance requirements.
- `cases/CASE-003-Clinical-Treatment-Response-Residuals.md`: develop a domain-specific research example with safeguards.
- `extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md`: explore cross-domain metric generation.

**Relay package (candidate):** `Question + Context + Expectation + Observation + Residual + Alternatives + Evidence + Tests + Outcomes + DefinitionVersion + OpenLeftovers`.

A relay recipient must be able to challenge assumptions, reproduce permissible analyses, add counterexamples, and return a revised artifact without overwriting the original record.

## 16. Open Questions and Explicit Leftovers

1. What is the smallest useful residual schema across numeric and relational domains?
2. Which residual similarities are meaningful without implying shared causes?
3. When does reverse CCC outperform ordinary feature search or active learning?
4. How should a residual priority score account for uncertainty, impact, and verification cost?
5. What minimum evidence supports promotion of a new perspective descriptor?
6. How should the registry represent incompatible models and contested observations?
7. Can WE-HDT improve scientific retrieval without sacrificing exactness or recall?
8. Which parts of MLIU should be local, shared, or activated on demand?
9. How should contradictory findings from independent groups be merged or preserved?
10. When is a residual merely a model artifact, and how can this be detected efficiently?
11. How can the system avoid self-reinforcing feedback between hypothesis generation and selection?
12. What privacy-preserving relay mechanisms retain enough information for validation?
13. How should CDE handle epistemic rollback, cycles, and branching revisions?
14. What evidence would falsify the claim that first-class residual records add value?
15. How should the WE-SIO minimal kernel change if relational residuals cannot share the proposed comparator abstraction?

## 17. Position within the SI Research Program

WE-SIO provides a proposed world-entity and perspective substrate. **WE-HDT** supplies candidate localization and structural access. **MLIU** supplies logical operations over perspectives and evidence. **Two-Ways CCC** enables forward condition evaluation and backward hypothesis search. **AQSI** offers a research direction for autonomous question generation. **CDE** provides a candidate framework for controlled epistemic and operational revisions. **SIF** is the broader architectural context, especially Localization and structural intelligence control. **UIERU/Collective Learning Relay** motivate transfer of evidence, counterexamples, and reusable research pieces. **SSI** raises additional questions about self-models but is not necessary for RFSD.

These connections are architectural proposals, not evidence that the integrated system has been built or empirically validated.

## Addendum A — Residual Evidence Registry (RER): qualification and lifecycle (v0.1.0 update)

This section incorporates the epistemic separation and Mask-First principles developed in `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`. The term **Residual Evidence Registry (RER)** is preferred over *Residual Bucket* to avoid implying that all unclassified, unknown, or low-confidence knowledge belongs in one container. Existing uses of *residual registry* remain valid when they satisfy the qualification contract below.

### 19.1 Admission criteria

A candidate record qualifies for RER only if it includes, or explicitly references:

1. **Target and scope:** entity or population, perspective, context, temporal window, and versions.
2. **Comparison basis:** a prediction, model, constraint, expected relation, or explanation baseline that can be evaluated.
3. **Observation or counterevidence:** a traceable measurement, event report, or other evidence bearing on that basis.
4. **Discrepancy semantics:** a typed comparator and result (numeric, categorical, relational, directional, or structured), with uncertainty and missing-data rules.
5. **Provenance:** source identifiers, transformation lineage, evaluator, and timestamps.
6. **Qualification status:** provisional, qualified, rejected, resolved, or reopened, with explicit reasons.

A record that lacks a valid comparison basis remains in the **Open Knowledge Registry** or evidence intake queue, not in RER. A contradiction between two well-specified claims can qualify as a structured residual even without scalar subtraction. The system must not invent a numerical baseline merely to admit a record.

### 19.2 Candidate schema

```yaml
ResidualEvidenceRecord:
  residualId: stable-identifier
  entityOrCohortRef: versioned-reference
  perspectiveRef: typed-descriptor-and-version
  applicabilityScope: {conditions: [], timeWindow: null}
  expectationRef: model-or-constraint-and-version
  observationRefs: []
  comparisonContract: {kind: typed, units: optional, tolerance: declared}
  discrepancy: {valueOrStructure: null, uncertainty: declared}
  qualityChecks: {measurement: pending, leakage: pending, confounding: pending}
  alternativeExplanations: []
  hypothesisRefs: []
  status: provisional
  provenance: {sources: [], evaluator: null, timestamps: []}
  transitions: []
  permissionsAndRetention: declared
```

The schema is illustrative, not a mandatory serialization format. Privacy-sensitive evidence may remain behind access-controlled references. Registry membership must not override source authorization or imply independent validation.

### 19.3 Lifecycle and governance

```text
Observation / Claim / Question
          |
   Epistemic classification
       /        |        \
Established    Open     Candidate discrepancy
knowledge      question         |
   |             |       Compare against typed baseline
   |             |              |
   |             |       RER provisional / rejected
   |             |              |
   |             +<--- Question / hypothesis generation
   |                            |
   +<--- Independent testing and evidence review
                 |
       Promote / revise / withdraw
```

- **Provisional → qualified:** comparator, provenance, uncertainty, and initial error checks meet a declared policy.
- **Provisional → rejected:** no meaningful baseline, invalid comparison, duplicate, or identified artifact; preserve a reasoned audit record.
- **Qualified → resolved:** discrepancy is explained, corrected, or superseded; retain original evidence and versions.
- **Resolved → reopened:** new independent evidence or changed assumptions justify renewed investigation.

No status transition automatically establishes a new scientific mechanism. Promotion of a hypothesis into Established Knowledge requires a separate **Knowledge Promotion Contract**, including independent tests, appropriate controls, reproducibility criteria, domain review where necessary, and reversible versioning. Established claims can be downgraded or withdrawn.

## Addendum B — Mask-First residual investigation and separation of deltas

**Mask-First discovery** can select relevant entities, perspectives, relations, operators, and computation budgets without splitting or rebuilding mature WE-HDT/AVIB structures. A mask is a *task-scoped active computation view*, not a change in the underlying scientific evidence or the physical world.

A candidate investigation sequence is:

1. Generate a permission-constrained, versioned Mask for the question and comparison contract.
2. Retrieve expectations and observations while preserving full evidence lineage.
3. Evaluate discrepancies with declared uncertainty and error checks.
4. Expand or remask when evidence coverage, alternative explanations, or recall is insufficient.
5. Record the investigation as an **Activation Delta** (selection), **Knowledge Delta** (belief/evidence revision), or **Structural Delta** (persistent index/representation change), without conflating them.
6. Compare against a full-view or independently verified reference for exact tasks; report approximation and false-exclusion risk for exploratory tasks.

**Mask safety:** an exact-query mask must not exclude eligible evidence; when completeness cannot be guaranteed, use safe expansion, fallback, or an explicitly approximate contract. Mask generation and validation costs count toward the claimed computational savings. A mask cannot bypass SQL row/column security or other access restrictions. Stable structures are preferred when beneficial, not preserved unconditionally.

This framework also supports **Collective Learning Relay**: a reusable mask policy or residual diagnosis must carry its source conditions, evidence, validation outcomes, failure cases, and transfer limits. Consensus among agents is not independent confirmation.

## Addendum C — Updated conformance and falsifiable experiments

| ID | Required behavior | Failure case |
|---|---|---|
| EPI-SEP-01 | Open unknowns remain distinct from qualified residuals | Missing observation automatically labeled anomaly |
| RER-QUAL-01 | Every qualified residual has a typed comparison basis and evidence | Unattributed difference or incompatible units |
| RER-QUAL-02 | Provisional/rejected/resolved records preserve provenance | Silent deletion of negative or corrected evidence |
| RER-QUAL-03 | Non-numeric contradictions can be represented without fabricated distance | Directional relation forced into Euclidean metric |
| EPI-PROM-01 | Knowledge promotion, demotion, and withdrawal require reviewable evidence | One anomalous result becomes established law |
| MASK-RER-01 | Masked exact investigation preserves required evidence coverage | Critical cohort excluded by selection mask |
| MASK-RER-02 | Remasking changes activation state without silently changing world/knowledge state | Query filter interpreted as data update |
| RELAY-RER-01 | Cross-agent reuse retains provenance and independent validation criteria | Repeated agreement mistaken for replication |

**Research hypotheses:** `WEH-033` proposes that epistemic separation improves classification and traceability; `WEH-034` proposes that validated mask-policy relay transfers useful selection behavior across compatible tasks. These hypotheses are shared with EXT-005 and must not be double-counted as independent evidence. Additional domain-specific tests should compare (a) a single undifferentiated anomaly bucket, (b) separate Open Knowledge and RER views, and (c) the same views with mask-first execution. Report false-residual rate, missed discrepancies, evidence coverage, investigator time, validation cost, and downstream hypothesis quality. Include adversarial tests for noise, distribution shift, confounding, selection bias, model misspecification, missing-not-at-random data, and incompatible perspectives.

**Integration points:** `WE-SIO-005` (MLIU views and operations), `WE-SIO-008` (metric promotion), `WE-SIO-009` (Delta typing), `SPEC-005` (formal qualification and evidence contracts), `EXT-005` (Mask-First and epistemic separation), and `EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md` (SQL-facing conformance cases).

---

## 18. Conclusion

Residual-first scientific discovery does not elevate every mismatch into a breakthrough. It asks that unexplained differences be **preserved with context, made addressable, compared under valid perspective contracts, and transformed into testable questions**. A successful WE-SIO implementation would improve the discipline of learning from what current models fail to explain while retaining the right to conclude that an anomaly was noise, bias, or error.

> **Unknown is not zero. Unexplained is not useless. Residual is not necessarily noise.**
>
> **A residual is evidence of a gap, not automatically evidence of a new law.**

The next research step is to convert this architecture into explicit contracts and falsifiable comparisons with existing scientific workflows.

---

## Suggested Figure Placement

- **Fig-007-Residual-Driven-Scientific-Discovery-Loop.png** — after Section 5.
- **Fig-006-Two-Ways-CCC-Cross-Metric-Discovery.png** — after Section 6.
- **Fig-008-World-Delta-vs-Epistemic-Delta.png** — after Section 10.

## Related WE-SIO Documents

- `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`
- `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`

- `WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md`
- `WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`
- `WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`
- `WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md`
- `WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`
- `WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md`
- `WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`
- `WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`

## Citation and Status Note

This document is a versioned research hypothesis and architecture proposal. It does not report new experimental results or establish clinical efficacy, causal discoveries, or superiority to existing scientific methods. Future releases should link empirical results, code, datasets where permissible, and a versioned citation record.
