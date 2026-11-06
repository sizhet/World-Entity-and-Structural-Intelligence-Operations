# EXT-003 — Structural Scientific Discovery and Metric Generation

**Repository:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis / architecture proposal  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Open research; no empirical performance claims

## Abstract

Scientific discovery is not exhausted by fitting a better model to a fixed feature set. A discovery system must also ask whether its entities, observations, perspectives, relations, metrics, and explanatory assumptions are adequate. This extension proposes a **Structural Scientific Discovery (SSD)** workflow in which unexplained residuals become accountable research objects, autonomous questioning proposes alternative explanations, and candidate metrics or perspectives undergo typed validation before admission to a shared World Entity (WE) model. WE-HDT supports evidence-aware localization, Metric Leaf Intelligence Units (MLIUs) manage scoped reasoning, Two-Ways CCC connects forward evaluation with reverse questioning, and Constrained Delta Evolution (CDE) organizes bounded changes to hypotheses and research structures. The proposal emphasizes negative findings, independent tests, provenance, and explicit leftovers. Its added value relative to established scientific methods remains an empirical question.

## 1. Scope and research claim

The hypothesis is that an integrated, contract-governed pipeline can improve the **traceability, calibration, and eventual yield of useful research questions and candidate measurements**, relative to otherwise comparable workflows that use fixed representations or unstructured hypothesis logs. This is a testable systems claim, not a claim of automated scientific truth.

The extension covers:

- Structured residual capture and triage.
- Generation of candidate variables, measurements, relational descriptors, and mathematically valid metrics.
- Prospective tests, counterexamples, and controlled promotion of new perspectives.
- Multi-agent division of discovery, criticism, replication, and governance.
- Research artifacts that can be transferred through Collective Learning Relay.

It does **not** establish causal mechanisms from observational association, guarantee novelty, or authorize autonomous real-world experimentation without oversight.

## 2. Terminology and type discipline

A **World Entity** is a referent under a declared identity and scope contract. A **Perspective** is a typed way of describing or evaluating entities or their relationships. A **Measurement** is an observation produced under an instrument and protocol. A **Feature** is an input representation. A **Similarity** need not satisfy the metric axioms. A **Relation** may be directed and context-dependent. A mathematical **metric** `d` on domain `X` must satisfy nonnegativity, identity of indiscernibles, symmetry, and triangle inequality. A pseudometric may assign zero distance to distinct entities; a quasi-metric may be asymmetric. These types must not be silently interchanged.

A candidate perspective descriptor should declare:

```yaml
perspective_id: example:response-gradient:v0
kind: measurement                # metric | pseudometric | similarity | relation | measurement | feature
entity_domain: research-cohort-v2
value_type: real
unit: arbitrary-unit-per-day
protocol_ref: protocol-17
validity_window: [t0, t1]
uncertainty_model: calibrated-interval-v1
provenance_ref: evidence-bundle-82
privacy_class: restricted
status: proposed                 # proposed | testing | validated | rejected | deprecated
version: 0
```

“Validated” here means meeting **specified tests in a declared scope**, not universal scientific correctness.

## 3. Minimal scientific-discovery kernel

Define a research state:

`R = (E, P, O, H, V, G, B)`

where `E` is entity and identity registry; `P` perspective registry; `O` versioned observations; `H` hypothesis registry; `V` validation evidence; `G` governance constraints; and `B` computational, ethical, and experimental budgets.

A discovery step proposes a constrained delta:

`R' = Apply(R, Δ)` only if `Applicable(R, Δ, G)`.

Delta classes include observation correction, hypothesis addition, perspective proposal, metric promotion, index restructuring, and policy revision. **World Delta** (a change in the investigated world), **Observation Delta** (a new or corrected record), **Epistemic Delta** (a belief update), and **Structural Delta** (a research-system reconfiguration) remain separately logged. A corrected measurement is not a reversal of a physical event.

## 4. Forward and reverse discovery loops

### 4.1 Forward: accountable evaluation

1. Resolve entities, scope, and time windows.
2. Retrieve observations through appropriate WE-HDT indices.
3. Evaluate a registered model or explanatory hypothesis.
4. Produce predictions, uncertainty estimates, and diagnostic residuals.
5. Record evaluation protocol, baseline, data lineage, and limitations.

For an outcome `y` and registered prediction `ŷ`, a simple residual is `r = y − ŷ`. More complex residuals may be distributional, relational, ordinal, temporal, or constraint-violation objects. Their semantics must be specified; a numerical residual is not always appropriate.

### 4.2 Reverse: accountable questioning

1. Detect systematic or consequential residual patterns.
2. Exclude known data-quality failures and leakage.
3. Generate competing explanations, including null and mundane explanations.
4. Identify discriminating observations and feasible tests.
5. Propose new perspectives only when existing ones cannot adequately resolve the question.
6. Preserve unresolved findings even when no candidate is promoted.

The reverse path is **hypothesis generation**, not validation. Two-Ways CCC should retain a traceable connection between the residual and every candidate explanation it motivates.

## 5. Residual registry as a first-class research object

A minimal record:

```yaml
residual_id: R-0042
entity_ref: E-137
perspective_id: outcome:response:v2
prediction_ref: model-M4-run-91
observation_ref: obs-782
residual_type: signed-error
value: 2.3
unit: outcome-unit
uncertainty_ref: interval-17
cohort_and_time_ref: cohort-A-2026Q4
quality_checks: [range-check, timestamp-check, missingness-audit]
possible_explanations: [measurement-error, omitted-variable, regime-change]
status: unexplained
provenance_ref: immutable-run-bundle-91
```

Residuals should be grouped without erasing individual counterexamples. Clustering is exploratory until tested on held-out or prospectively collected data. Avoid ranking purely by magnitude; account for measurement uncertainty, consequence, repeatability, and collection bias.

## 6. Candidate metric and perspective generation

Candidate sources include:

- **Derived measurements:** transformations with declared dimensional and measurement semantics.
- **Conditional perspectives:** relationships valid only within specified contexts or regimes.
- **Relational hypotheses:** directed links, graph structures, temporal precedence, and interactions.
- **Composite indices:** explicitly weighted and calibrated combinations of measurements.
- **Learned representations:** latent features whose stability and interpretation require separate tests.
- **AQSI-driven questions:** new discriminating questions proposed from residual patterns.
- **CDE search:** bounded generation and selection of candidate research deltas.

A novel numeric expression is not automatically a scientifically meaningful metric. If `d(x,y)=|f(x)-f(y)|`, this is generally a **pseudometric** on the original entity domain unless `f` is injective. If a learned distance is asymmetric, it cannot be advertised as an ordinary metric without qualification.

## 7. Metric validation gates

| Gate | Required evidence | Typical failure |
|---|---|---|
| G0 — Semantic | Domain, meaning, units, admissible values | Undefined construct |
| G1 — Formal | Type-specific axioms and interface tests | Similarity mislabeled metric |
| G2 — Measurement | Reliability, calibration, uncertainty | Instrument drift |
| G3 — Incremental | Benefit over preregistered baselines | Redundant feature |
| G4 — Robustness | Held-out, shift, subgroup, sensitivity tests | Overfit or leakage |
| G5 — Replication | Independent data, protocol, or team | One-off discovery |
| G6 — Governance | Privacy, consent, safety, resource limits | Unauthorized evidence use |

A failed gate yields `rejected`, `deferred`, or `scope-restricted`; it does not require deletion. Promotion must record the exact scope, version, evidence, and rollback condition.

## 8. WE-HDT, MLIU, and SIF interfaces

**WE-HDT** routes typed queries to candidate entities, observations, and relational neighborhoods. Its Euclidean branch is optional and appropriate only when coordinates are meaningful. It is not a proof that a proposed metric is valid. **MLIUs** hold local hypotheses, uncertainty, evidence, residuals, and supported operations: Locate, Resolve, Relate, Infer, Question, and Evolve. A leaf may be a lightweight service or logical record; the architecture does not require an autonomous agent for each leaf.

Within **SIF**, WE-HDT offers entity/perspective addressing, while **CDE** offers constrained exploration of hypothesis and research-structure deltas. The Control Plane allocates budgets and enforces validation gates. These are proposed complementary roles, not measured advantages.

## 9. AQSI and multi-agent scientific relay

Possible roles are Observation Auditor, Residual Analyst, Question Generator, Hypothesis Constructor, Adversarial Critic, Experiment Designer, Independent Validator, and Governance Reviewer. Roles can be performed by software, people, or mixed teams. Separation is functional; multiplying agents does not multiply independent evidence.

A relay packet must contain: question, target entity/perspective scope, source residuals, competing hypotheses, discriminating test, data lineage, validation outcome, known counterexamples, resource expenditure, and unresolved leftovers. Repeated execution is a valid relay when it accumulates **new, attributable evidence**, not merely duplicated claims.

## 10. Worked synthetic example: unexpected response gradient

Suppose a synthetic dataset contains a predicted response to an intervention and a subset with systematic negative residuals. The discovery loop first checks timestamps, missingness, measurement drift, and group imbalance. A candidate explanation proposes that **elapsed time since baseline** modifies the observed response. The new perspective is a measured time interval with units and uncertainty—not a new mathematical distance by default.

The research system then:

1. Registers the original residuals and competing null explanation.
2. Proposes an interaction model with preregistered covariates.
3. Defines a temporal measurement contract and collection protocol.
4. Compares held-out predictive calibration and subgroup stability.
5. Requests independent replication before promotion.
6. Preserves the hypothesis as unresolved if replication fails.

This example is entirely synthetic and supports no clinical or causal conclusion.

## 11. Worked synthetic example: directional relations

An ecological monitoring model exhibits unexplained movement asymmetry between sites A and B. A candidate **directional transport relation** may depend on prevailing flow. The relation `A → B` can differ from `B → A`; therefore a symmetric distance representation could erase the effect. WE-SIO should preserve a typed directed relation and test its explanatory value against symmetric baselines. This illustrates why metric discovery sometimes results in a **non-metric perspective**.

## 12. Experimental design and baselines

Evaluate on synthetic environments with known hidden mechanisms and on public, permissioned research datasets where feasible. Use matched budgets and the same underlying data access.

- **B0:** Fixed-feature model and standard error analysis.
- **B1:** B0 plus a structured residual registry.
- **B2:** B1 plus automated candidate perspective generation.
- **B3:** B2 plus typed validation and independent criticism.
- **B4:** Full WE-SIO pipeline with WE-HDT, CDE, AQSI, and relay governance.

Primary outcomes: valid discovery precision, discovery recall against known synthetic mechanisms, time/cost to validated hypothesis, calibration, replication rate, and proportion of unsupported claims promoted. Secondary outcomes: evidence trace completeness, recovery from false leads, search latency, computational cost, and human reviewer burden. Include ablations for each architectural component. Predefine split strategy and prohibit test-set reuse for candidate selection.

## 13. Falsifiable hypotheses

**H-SSD-001 — Traceability:** B1 improves provenance completeness over B0 at comparable analyst effort.

**H-SSD-002 — Question yield:** B2 increases the number of *testable and nonredundant* questions per fixed budget over B1.

**H-SSD-003 — False-promotion control:** B3 reduces invalid candidate promotions relative to B2, accounting for reviewer time.

**H-SSD-004 — Cross-perspective value:** Typed relational perspectives outperform forced symmetric metrics on synthetic asymmetric mechanisms.

**H-SSD-005 — Structural advantage:** B4 improves validated discovery yield over B3 under matched resources; failure falsifies the incremental systems-value claim.

**H-SSD-006 — Relay value:** Independent teams using complete relay packets reproduce findings more reliably than teams receiving conclusions alone.

**H-SSD-007 — Definition resilience:** Versioned definition changes with regression tests cause fewer downstream semantic failures than untracked schema edits.

## 14. Conformance tests

| ID | Requirement |
|---|---|
| SSD-T001 | Entity identity is distinct from perspective signature. |
| SSD-T002 | Each perspective declares a type and domain. |
| SSD-T003 | Mathematical metric claims are axiom-tested. |
| SSD-T004 | Directed relations are not silently symmetrized. |
| SSD-T005 | Units and temporal scope are retained. |
| SSD-T006 | Predictions and observations have distinct provenance. |
| SSD-T007 | Residual uncertainty is recorded or explicitly unknown. |
| SSD-T008 | Missing data are not converted into zero residuals. |
| SSD-T009 | Reverse questions link to originating evidence. |
| SSD-T010 | Candidate generation does not imply promotion. |
| SSD-T011 | Held-out data remain isolated from search. |
| SSD-T012 | Confounding and leakage checks are logged. |
| SSD-T013 | Negative and null findings remain retrievable. |
| SSD-T014 | Independent evidence is not double-counted. |
| SSD-T015 | Delta categories are separately versioned. |
| SSD-T016 | Promotion includes scope and rollback criteria. |
| SSD-T017 | Resource and authorization constraints are enforced. |
| SSD-T018 | Rejected perspectives cannot be silently reused as validated. |
| SSD-T019 | Model and data versions are reproducible. |
| SSD-T020 | Definition revisions trigger regression tests. |
| SSD-T021 | A relay consumer can recover source claims and caveats. |
| SSD-T022 | Unsupported causal claims are flagged. |
| SSD-T023 | Drift detection distinguishes observation from world change. |
| SSD-T024 | Benchmark comparisons use matched data and budgets. |

## 15. Counterexamples and boundary cases

- **CE-SSD-001:** Large residual caused by a swapped unit; no new mechanism exists.
- **CE-SSD-002:** Apparent discovery vanishes after correcting timestamp alignment.
- **CE-SSD-003:** Learned embedding improves prediction but fails metric axioms.
- **CE-SSD-004:** Directional dependence is destroyed by symmetric-distance conversion.
- **CE-SSD-005:** A subgroup effect is induced by selection bias.
- **CE-SSD-006:** Multiple agents agree because they share the same flawed source.
- **CE-SSD-007:** A candidate passes internal tests but fails external replication.
- **CE-SSD-008:** An overgeneral definition becomes vacuous and predicts nothing.
- **CE-SSD-009:** An expensive new perspective offers no gain over a simple baseline.
- **CE-SSD-010:** A privacy restriction makes a proposed test inadmissible.
- **CE-SSD-011:** Dynamic reindexing improves query latency but changes no discovery quality.
- **CE-SSD-012:** A world event changes while the recorded data remain stale.
- **CE-SSD-013:** A measurement correction is falsely treated as physical reversal.
- **CE-SSD-014:** Hypothesis search repeatedly reuses its own test set.

Each counterexample should become a regression fixture or an explicitly unresolved test, not a rhetorical footnote.

## 16. Validation roadmap

**Phase 0 — Contract audit:** finalize types, identifiers, evidence semantics, and threat model.  
**Phase 1 — Synthetic mechanism recovery:** generate controlled worlds with hidden variables, asymmetric relations, noise, and confounding.  
**Phase 2 — Residual registry:** test reproducibility, auditability, and false-pattern suppression.  
**Phase 3 — Candidate generation:** compare manual, AQSI-assisted, and CDE-guided strategies under fixed budgets.  
**Phase 4 — Independent validation:** held-out tests, external replication, adversarial counterexamples.  
**Phase 5 — Systems ablation:** assess WE-HDT, MLIU, control plane, and relay components separately.  
**Phase 6 — Definition evolution:** revise the minimal kernel only after observed failures, with backward-compatibility and regression checks.

Exit criteria are predeclared improvements with uncertainty intervals and no unacceptable rise in false promotion. A negative result is a publishable relay outcome.

## 17. Definition Evolution Loop

A definition revision must specify the observed counterexample, old and new wording, affected contracts, newly admitted/excluded cases, migration requirements, and regression tests. Prefer narrowing or splitting a perspective over broadening “metric” until it means any numeric relation. The minimal kernel should remain precise while its inventory of admissible perspective types stays open.

## 18. Safety, ethics, and governance

Research involving humans, sensitive records, clinical settings, or consequential interventions requires appropriate legal, institutional, and professional oversight. The system should not autonomously prescribe treatment, manipulate participants, or conduct unapproved experiments. Privacy constraints, consent, data minimization, and model-risk review are part of the applicable-delta contract. Scientific claims must be calibrated to evidence quality.

## 19. Research relay package

Recommended files for each candidate:

```text
candidate-<id>/
  QUESTION.md
  PERSPECTIVE-CONTRACT.yaml
  HYPOTHESES.md
  RESIDUAL-EVIDENCE.json
  TEST-PLAN.md
  RESULTS.md
  COUNTEREXAMPLES.md
  DECISION.md
  PROVENANCE.json
  LEFTOVERS.md
```

The packet must distinguish observed evidence, interpretations, assumptions, and proposed next actions. Failures, null results, and explicit leftovers remain part of the scientific record.

## 20. Open questions and explicit leftovers

1. How can nonnumeric residuals be compared without fabricating a common scalar?
2. What evidence justifies creating a new perspective rather than revising a model?
3. How should correlated observations and agent outputs be discounted?
4. Can automated metric-axiom testing scale to learned or implicit distances?
5. When does a discovery-oriented index improve science rather than only retrieval?
6. How should CDE balance exploration, exploitation, and the cost of validation?
7. Which definition changes are safe across existing relay consumers?
8. Can scientific novelty be evaluated without rewarding mere unfamiliarity?
9. How should ethical and experimental feasibility constrain question generation?
10. What constitutes a meaningful systems-level improvement over established scientific workflows?

## 21. Connections to the WE-SIO research corpus

- `WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md` — typed localization and candidate retrieval.
- `WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md` — local reasoning operations.
- `WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md` — forward/reverse coupling.
- `WE-SIO-007-Residual-First-Scientific-Discovery.md` — residual-first epistemic discipline.
- `WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md` — perspective promotion.
- `WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md` — constrained research evolution.
- `SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md` — validation interfaces.
- `SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md` — definition and relay governance.
- `CASE-003-Clinical-Treatment-Response-Residuals.md` — bounded synthetic application.
- `EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md` — SIF integration.
- `EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md` — coordinated research relay.

## Conclusion

The distinctive proposal of Structural Scientific Discovery is not that unexplained observations automatically disclose new laws. It is that residuals, questions, candidate perspectives, tests, counterexamples, and definition changes can be managed as **typed, evidence-bearing, versioned structural objects**. WE-SIO provides a possible integration architecture; its scientific and engineering benefit must be demonstrated through rigorous baselines, ablations, independent replication, and transparent preservation of failures.

---

**Research status:** Hypothesis and validation plan; not a demonstrated scientific discovery engine.  
**License intent:** Apache-2.0, subject to repository license.  
**Relay principle:** Preserve the path of inquiry, not only the surviving answer.
