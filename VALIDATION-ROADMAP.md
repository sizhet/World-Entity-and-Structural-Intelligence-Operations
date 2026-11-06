# WE-SIO Validation Roadmap

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Release:** v0.1.0 — Research framework / proposed validation program  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed; no experimental results are asserted by this document  
**Last updated:** 2026-11-05

> **Conformance before performance. Evidence before promotion. Counterexamples remain first-class research assets.**

## 1. Purpose and scope

This roadmap converts the WE-SIO theoretical architecture into a staged, falsifiable research program. It establishes what must be specified, implemented, measured, independently checked, and documented before WE-SIO claims may be promoted from hypotheses to supported findings.

The research spans World Entity (WE) identity and perspective descriptors, WE Hybrid Differential Trees (WE-HDT), Perspective-Adaptive Variable Blocks (PAVB), Adaptive Variable-Intelligence Blocks (AVIB), Metric Leaf Intelligence Units (MLIU), Two-Ways CCC, residual-first discovery, metric/perspective generation, Constrained Delta Evolution (CDE), multi-agent collective learning, and self-modeling.

**Non-goals:** This release does not claim a new universal mathematical metric, proven search speedups, a validated scientific discovery, clinical efficacy, general intelligence, or subjective experience. Proposed architecture is not evidence of those outcomes.

## 2. Evidence and decision conventions

| Level | Meaning | Minimum record |
|---|---|---|
| E0 | Conceptual proposal | Definition, assumptions, counterexamples, test plan |
| E1 | Executable synthetic demonstration | Versioned code, deterministic fixtures, conformance report |
| E2 | Controlled benchmark | Baselines, workload specification, uncertainty estimates |
| E3 | External or realistic-domain validation | Data provenance, governance, out-of-distribution checks |
| E4 | Independent replication | Independent implementation or external reproduction |

A hypothesis can be **Proposed**, **In Test**, **Supported (qualified)**, **Refuted**, **Inconclusive**, or **Superseded**. Evidence levels are not quality scores: an E2 negative result can be more informative than an E1 positive demonstration.

All decisions require a traceable record: claim ID, versioned protocol, datasets or fixtures, software commit, seed, environment, baseline, measured outcomes, uncertainty, failures, reviewer, and decision rationale.

## 3. Stage gates at a glance

| Stage | Priority | Main deliverable | Exit gate |
|---|---|---|---|
| 0. Research contract freeze | P0 | Typed contracts, definitions, hypothesis map | No unresolved semantic contradiction in mandatory interfaces |
| 1. Minimal conformance harness | P0 | Deterministic reference implementation | Identity, perspective, search, delta, evidence tests pass |
| 2. Localization benchmark | P0–P1 | Reproducible WE-HDT / PAVB comparisons | Correctness parity, resource accounting, uncertainty reported |
| 3. Residual and discovery trials | P1 | Registered synthetic discovery suite | Leakage controls and independent hypothesis evaluation |
| 4. CDE and self-modeling stress tests | P1 | Chess / scheduling / calibration experiments | Cycle, rollback, prediction and policy constraints checked |
| 5. Multi-agent collective relay | P1–P2 | Relay interoperability and ablation suite | Evidence independence and overhead measured |
| 6. External validation and replication | P2 | External dataset and replication package | Claims scoped to reproduced evidence |

Stages may overlap only when their upstream correctness dependencies are satisfied. A failed gate produces an explicit leftover, not a silently weakened acceptance criterion.

## 4. Stage 0 — Definitions, contracts, and research trace

**Objective:** establish stable, testable semantics before choosing implementation shortcuts.

### Required activities

1. Specify **entity identity** separately from source record IDs, metric signatures, and candidate similarity.
2. Define typed **perspective descriptors**: domain, unit, metric/relation kind, time, uncertainty, evidence provenance, version, and authorization.
3. Distinguish mathematical metrics from measurements, similarity functions, directional relations, and arbitrary numeric attributes.
4. Define WE-HDT node, block, leaf, candidate, and resolution contracts; specify exactness versus approximation guarantees.
5. Separate **index partition granularity** from **intelligence allocation** in PAVB/AVIB.
6. Define the MLIU operations: Locate, Resolve, Relate, Infer, Question, Evolve; specify resource budgets and audit output.
7. Type the forward and reverse interfaces of Two-Ways CCC.
8. Distinguish world, observation, epistemic/knowledge, and structural/operational deltas.
9. Specify CDE's state-transition kernel separately from application-specific path-memory and no-reuse policies.
10. Define the Definition Evolution Loop (DEL), including backward compatibility and regression requirements.

### Exit criteria

- Every mandatory field has a definition, type, versioning rule, and invalid-input behavior.
- The definition registry and counterexample registry identify the principal boundary cases.
- Cross-perspective conversions require explicit contracts; no implicit unit or relation coercion is accepted.
- Open disagreements are logged as unresolved residuals with owners or proposed next experiments.

**Artifacts:** `DEFINITION-REGISTRY.md`, `COUNTEREXAMPLE-REGISTRY.md`, `HYPOTHESIS-REGISTRY.md`, `DECISION-LOG.md`, `specs/SPEC-001` through `SPEC-006`.

## 5. Stage 1 — Executable conformance reference

**Objective:** produce a deliberately small implementation whose behavior can be inspected and tested.

### Reference fixtures

- Duplicate source records representing one possible real-world entity, plus two distinct entities with near-identical metric values.
- Euclidean, abstract/non-Euclidean, asymmetric relational, and missing-perspective entities.
- Unit conversion failures, missing timestamps, stale versions, contradictory evidence, and unauthorized fields.
- Blocks that split, merge, and reindex while readers issue concurrent queries.
- MLIUs that exceed budget, decline unsupported operations, or return unresolved evidence.
- World events followed by delayed observations and later epistemic revisions.

### Required conformance assertions

| ID | Assertion |
|---|---|
| V-WE-001 | Entity identity is not inferred solely from distance or similarity |
| V-WE-002 | Source-record identity and canonical-entity identity remain distinguishable |
| V-PER-001 | Metric axioms are checked only when a mathematical metric is claimed |
| V-PER-002 | Asymmetric relations are never silently treated as distances |
| V-PER-003 | Unit, time, provenance, and version mismatches are detectable |
| V-HDT-001 | Exact candidate search has no false negatives under declared assumptions |
| V-HDT-002 | Approximate search reports its approximation contract |
| V-HDT-003 | Split/merge/reindex preserves reachable entities or signals a consistency failure |
| V-MLIU-001 | Unsupported operations fail explicitly, not by fabricated answers |
| V-MLIU-002 | Resource limits and audit trails are enforced |
| V-CCC-001 | Reverse discovery outputs questions/hypotheses, not automatically validated facts |
| V-RES-001 | Residuals preserve expectation, observation, uncertainty, and provenance |
| V-DELTA-001 | Observation correction is not labeled a reversal of a world event |
| V-CDE-001 | Repeated legal state transitions remain possible where domain rules allow |
| V-CDE-002 | Cycle and termination policies are explicit and testable |
| V-DEL-001 | Definition changes trigger affected conformance regression tests |

**Exit criteria:** all mandatory assertions pass in the reference harness; any exception has a recorded and justified scope limitation. Passing this stage does **not** establish performance superiority.

## 6. Stage 2 — WE-HDT and variable-block benchmark

**Objective:** determine whether proposed structures provide measurable benefits over credible indexing alternatives.

### Baselines

- Exhaustive scan (correctness oracle for small datasets).
- Standard k-d tree with documented splitting, balancing, and update policy.
- Fixed-size spatial or metric blocks.
- Variable-size blocks without perspective-aware adaptation.
- WE-HDT/PAVB with perspective-aware localization.
- AVIB variant with adaptive intelligence allocation, evaluated separately from indexing changes.

### Workloads and controlled factors

- Dimensions: low, moderate, and high; include non-Euclidean and relational queries where supported.
- Data distributions: uniform, clustered, skewed, adversarial, sparse, and changing over time.
- Queries: exact nearest neighbor, range, filtered relational resolution, mixed-perspective, and approximate search.
- Updates: insert, delete, revise, bulk rebuild, hot-spot shift, and versioned concurrent reads.
- Scale: multiple dataset sizes and memory budgets; record hardware and implementation language.

### Primary measures

- Recall/precision of candidate generation and final entity resolution; exactness violations are **gate failures**.
- Median, p95, and p99 latency; throughput; CPU time; memory; build time; update cost; reindex cost.
- Index size, block occupancy, split/merge churn, and cost per resolved query.
- Sensitivity to dimensions, skew, query selectivity, and workload drift.

### Fairness and analysis

Match correctness targets, hardware, resource limits, query mixes, preprocessing accounting, and implementation maturity. Report confidence intervals across independent runs, not only best-case speedups. Include ablations that disable perspective adaptation and intelligence allocation separately.

**Exit criteria:** complete baseline parity and reproducible measurements; no universal speedup claim without cross-workload support. If the advantage disappears after accounting for reindexing or agent overhead, retain that negative result.

**Linked case:** `cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md`.

## 7. Stage 3 — Residual-first discovery and metric generation

**Objective:** test whether structured residual preservation and reverse questioning improve discovery quality beyond ordinary analysis.

### Study arms

A. Standard predictive or rule-based analysis without a residual registry.  
B. Same model with residual recording and provenance.  
C. Residual registry plus Two-Ways CCC question generation.  
D. C plus candidate perspective/metric generation and independent validation.

Use synthetic data with known hidden factors first; introduce controlled confounding, noise, measurement error, distribution shift, and null scenarios with no discoverable new mechanism.

### Evaluation measures

- Recovery rate of known hidden factors; false discovery rate; hypothesis novelty and validity.
- Calibration and uncertainty quality; time/compute to a validated candidate.
- Cross-dataset replication and robustness to leakage, confounding, and multiple comparisons.
- Number of rejected hypotheses and proportion with preserved rejection rationale.

### Mandatory validation gates

1. Semantic plausibility and typed perspective compatibility.
2. Mathematical property tests if the candidate claims to be a metric.
3. Measurement reliability and evidence provenance.
4. Holdout evaluation with predeclared selection protocol.
5. Independent replication or a genuinely independent test set.
6. Governance review before promotion to operational use.

A residual is a signal that a model and observation differ; it is **not** by itself proof of a missing law. Clinical examples are research simulations, not medical guidance or evidence of treatment benefit.

**Exit criteria:** validated findings are distinguishable from generated candidates, and null experiments quantify false discovery behavior.

**Linked documents:** `docs/WE-SIO-007`, `docs/WE-SIO-008`, `cases/CASE-003-Clinical-Treatment-Response-Residuals.md`, `extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md`.

## 8. Stage 4 — CDE, delta semantics, and self-modeling

**Objective:** stress the generalized evolution kernel and evaluate self-model accuracy without conflating function with subjective experience.

### CDE tracks

**Chess boundary track:** represent full game state including side to move, castling rights, en-passant state, and relevant counters; test legal repetition, transposition, cycle control, undo, and termination. Compare CDE search policies with conventional search under matched compute. **No-Delta-Reuse** must be configurable rather than a universal axiom.

**Scheduling track:** use school-bus or logistics tasks with explicit capacity, timing, routing, and fairness constraints. Compare standard heuristics, optimization baselines, and CDE-guided generation under identical objective functions.

**Delta provenance track:** inject out-of-order observations, corrections, world events, and structural reindexing; verify that each delta category has distinct semantics and rollback scope.

### Self-modeling tracks

- Static self-description versus single-perspective versus multi-perspective self-model.
- Self-prediction of task capability, resource usage, uncertainty, and failure probability.
- Feedback-driven model revision with held-out future tasks.
- Adversarial and distribution-shift calibration tests.

**Measures:** calibration error, proper scoring rules, decision utility under constraints, adaptation overhead, regression frequency, and audit completeness. Self-modeling success is evidence of functional metacognitive performance only, not evidence of subjective consciousness.

**Exit criteria:** CDE policies satisfy domain constraints; any incremental benefit over standard search is measured; self-model revisions improve held-out calibration or are reported as inconclusive.

**Linked cases:** `cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md`, `cases/CASE-005-Multi-Perspective-Self-Modeling-Entity.md`.

## 9. Stage 5 — Multi-agent WE-SI and collective relay

**Objective:** determine whether multiple specialized agents provide transferable learning rather than merely additional compute or correlated agreement.

### Comparison arms

1. Single agent, fixed budget.
2. Single agent, matched total compute of the multi-agent configuration.
3. Multi-agent without shared residual registry.
4. Multi-agent with relay, provenance, counterexample exchange, and independent validation.
5. Competitive/adversarial relay with independent evidence checks.

### Measurements

- Verified task success and generalization to new datasets/tasks.
- Cost per validated finding; latency and communication overhead.
- Evidence independence and duplicate-source detection.
- Error propagation, correction time, and recovery from adversarial or low-quality contributions.
- Reusability of a relay package by a separate team or implementation.

### Governance gates

Agents must identify evidence sources, distinguish claims from suggestions, respect permissions, and retain failed or contradictory results. Majority agreement is not treated as independent corroboration.

**Exit criteria:** collective improvements persist under compute-matched ablation and provenance-aware evaluation; otherwise characterize the costs and failure modes.

**Linked extension:** `extensions/EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md`.

## 10. Stage 6 — External validation and independent replication

**Objective:** test portability and limit claims to evidence that survives external evaluation.

Candidate domains include relational databases, logistics, scientific datasets with known ground truth, and non-sensitive self-modeling benchmarks. Sensitive or clinical datasets require appropriate approvals, privacy protections, domain expertise, and access controls; synthetic results must never be presented as clinical validation.

A replication package should contain:

- Protocol and preregistered primary outcomes where feasible.
- Source or reproducible pseudocode, exact commits, dependency lockfiles, and license information.
- Dataset access instructions or shareable synthetic generators.
- Environment and resource accounting, seeds, baseline configurations, and scripts.
- Raw results, uncertainty estimates, failures, and counterexamples.
- A concise claim-to-evidence table and reviewer notes.

**Exit criteria:** at least one independently reproducible result for each claim intended for promotion beyond exploratory status; unreproduced claims retain explicit qualifiers.

## 11. Claim-to-evidence promotion matrix

| Claim family | Minimum evidence before qualified public claim | Blocking failure |
|---|---|---|
| Entity/perspective semantic correctness | Stage 1 conformance, negative fixtures | Identity conflation or invalid implicit coercion |
| WE-HDT retrieval correctness | Stage 1 + Stage 2 oracle comparison | Undeclared false negatives |
| WE-HDT efficiency advantage | Stage 2 controlled multi-workload results | Unfair baseline or unaccounted overhead |
| Residual discovery advantage | Stage 3 held-out/null controls | Leakage or elevated unreported false discoveries |
| New metric validity | Formal property checks + Stage 3 independent tests | Metric axioms fail under declared domain |
| CDE structural advantage | Stage 4 matched-search comparison | Policy violations or baseline mismatch |
| Multi-agent collective improvement | Stage 5 compute-matched ablation | Correlated evidence treated as independent |
| Self-modeling improvement | Stage 4 held-out calibration | In-sample-only improvement |
| General cross-domain portability | Stage 6 external replication | Non-reproducibility or undocumented domain assumptions |

No stage grants an unrestricted “universal” claim.

## 12. Priority queue and dependency order

**P0 — semantic and correctness blockers**

- Entity identity versus source IDs and similarity.
- Perspective typing, units, temporal validity, and evidence provenance.
- Exact/approximate retrieval contracts and update consistency.
- World versus epistemic delta semantics.
- CDE path memory as a domain policy, not a universal invariant.

**P1 — performance and scientific utility**

- Index benchmarks and adaptive overhead ablations.
- Residual discovery against null and confounded datasets.
- Metric candidate validation and rejection.
- CDE versus conventional search; self-model calibration.

**P2 — transfer and ecosystem**

- SIF Localization integration with WE-HDT and CDE.
- Multi-agent relay and evidence independence.
- Cross-domain replication and definition evolution governance.

Dependencies should be represented explicitly in `HYPOTHESIS-REGISTRY.md`; a dependent hypothesis cannot be promoted when a prerequisite contract is unresolved.

## 13. Risks, counterexamples, and stop rules

| Risk | Required response |
|---|---|
| Candidate omission in exact retrieval | Stop performance claim; repair search contract |
| High-dimensional or skew-induced degradation | Report workload boundary; do not extrapolate |
| Split/merge oscillation | Add stability controls and account for maintenance cost |
| False metric classification | Reclassify as measurement/similarity/relation |
| Residuals caused by noise or confounding | Reject causal interpretation pending independent evidence |
| Hypothesis leakage into evaluation | Rebuild holdout protocol; invalidate contaminated results |
| CDE nontermination or invalid loop suppression | Revise domain cycle policy; preserve counterexample |
| Agent consensus from shared sources | Deduplicate provenance; seek independent checks |
| Self-model overconfidence | Report calibration failure; restrict autonomy |
| Definition revised only to escape a counterexample | Require independent regression and scope review |

Stop rules apply to the affected claim or stage, not necessarily to the entire research program. A failed experiment should become a documented relay artifact.

## 14. Reporting cadence and reproducibility

For every experiment, publish a compact **Experiment Record**:

```yaml
experiment_id: WE-SIO-EXP-YYYY-NNN
hypothesis_ids: [WEH-XXX]
protocol_version: "0.1"
status: proposed # proposed | running | completed | invalidated
implementation_commit: null
dataset_or_generator_version: null
seed_set: []
baselines: []
primary_metrics: []
acceptance_criteria: []
conformance_results: null
observed_results: null
uncertainty_method: null
counterexample_ids: []
residual_ids: []
review_decision: pending
limitations: []
next_relay_action: null
```

Records must distinguish **planned thresholds** from **observed outcomes**. Failed runs, excluded observations, and changes to the protocol should remain visible in the research trace.

## 15. Definition Evolution Loop integration

1. Detect a contradiction, failed conformance check, or unexplained residual.
2. Create a counterexample and link it to definitions and hypotheses.
3. Identify whether the failure concerns implementation, assumptions, measurement, or the definition itself.
4. Propose a narrow, versioned revision with explicit alternatives.
5. Run the original and newly added regression fixtures.
6. Accept, reject, or defer the revision with a recorded rationale.
7. Relay the outcome, including negative evidence, to dependent research tracks.

Definition evolution should increase explanatory precision, not merely enlarge a concept until it cannot be falsified.

## 16. Research interfaces and related files

| File | Role |
|---|---|
| `TESTABLE-HYPOTHESES.md` | Detailed falsifiable protocols and metrics |
| `HYPOTHESIS-REGISTRY.md` | Claim IDs, dependencies, evidence status |
| `DEFINITION-REGISTRY.md` | Canonical terms, invariants, versioned definitions |
| `COUNTEREXAMPLE-REGISTRY.md` | Boundary failures and regression fixtures |
| `DECISION-LOG.md` | Architecture tradeoffs and revision rationale |
| `UNRESOLVED-RESIDUALS.md` | Unresolved gaps and next actions |
| `OPEN-QUESTIONS.md` | Research questions and exploration entry points |
| `FUTURE-DIRECTIONS.md` | Longer-term research directions |
| `specs/` | Formal and operational conformance contracts |
| `cases/` | Domain-specific boundary and benchmark studies |
| `extensions/` | SIF, scientific discovery, relay, self-modeling interfaces |

## 17. Release readiness checklist

- [ ] All mandatory semantic contracts reviewed and cross-linked.
- [ ] Every promoted claim has a hypothesis ID and evidence record.
- [ ] No proposed experiment is described as completed.
- [ ] Benchmark baselines and hardware/software environments documented.
- [ ] Negative and null results preserved, not selectively omitted.
- [ ] Clinical or sensitive examples explicitly scoped and governed.
- [ ] Figures and links verified against actual repository files.
- [ ] DOI metadata, citation, release notes, and license reviewed.
- [ ] Open residuals and limitations remain discoverable.
- [ ] Independent reviewers can identify how to reproduce or challenge claims.

## 18. Explicit leftovers

1. The smallest interoperable WE identity contract across unrelated sources remains open.
2. A rigorous WE-HDT exactness proof depends on the final indexing and pruning rules.
3. The comparative value of PAVB and AVIB over mature indexing baselines is unmeasured.
4. The resource-optimal MLIU granularity remains unknown.
5. Cross-perspective discovery may require stronger causal and type-theoretic controls.
6. A practical boundary between mathematical metrics and learned relations needs enforcement tests.
7. CDE's distinguishing contribution beyond general state-transition/search frameworks requires empirical and formal scrutiny.
8. Reliable collective learning under correlated agent evidence remains an open problem.
9. Functional self-modeling gains do not resolve subjective-experience questions.
10. External replication infrastructure and governance procedures remain to be built.

## 19. Closing research contract

WE-SIO v0.1.0 is a **research proposal with testable interfaces**, not a report of completed experiments. Its intended contribution is to make structural intelligence claims easier to locate, challenge, reproduce, revise, and relay. The roadmap is successful when it can produce both well-supported advances **and** clear, reusable explanations of where an idea fails.

**Research maxim:** *Preserve the invariant, test the boundary, retain the residual, and relay the evidence.*
