# TESTABLE HYPOTHESES

**World Entity and Structural Intelligence Operations (WE-SIO)**  
**Version:** v0.1.0  
**Date:** 2026-11-05  
**Contributors:** Sizhe Tan & GPT-Obot  
**Research status:** Proposed protocols, not executed experiments  
**Location:** `TESTABLE-HYPOTHESES.md`

> Conformance before performance. Evidence before promotion. Negative results are relay assets.

## 1. Purpose and scope

This document turns the 40 research hypotheses proposed as `WEH-001` through `WEH-040` into auditable, falsifiable study plans. It is an experimental specification, not a report of observed outcomes. The authoritative identifier, status and provenance ledger is `research-trace/HYPOTHESIS-REGISTRY.md`; any status change must be synchronized there.

A proposed architecture, attractive example, or internal agent consensus is not experimental evidence. A claim must be scoped to a population, workload, task, resource budget, baseline and measurable endpoint. The proposed tests below must be preregistered before examining confirmatory results.

## 2. Hypothesis lifecycle and evidence

| Stage | Required artifact | Allowed claim |
|---|---|---|
| Proposed / E0 | Defined hypothesis, falsifier, protocol draft | Conjecture only |
| Specified / E0 | Frozen protocol, data/metric/baseline plan | Ready for experiment |
| Testing | Reproducible execution logs | Preliminary observation only |
| Supported / E1–E4 | Results, uncertainty, negative controls, scope | Evidence-supported in tested setting |
| Mixed | Conflicting or heterogeneous evidence | Qualified and unresolved |
| Refuted | Reproducible counterexample or decisive negative test | Claim fails under specified conditions |
| Superseded | New definition and linked successor | Historical provenance preserved |

E1 means reproducible synthetic observations; E2 controlled benchmarks; E3 independent replication; E4 robust evidence across distinct settings. These grades are local bookkeeping, not external scientific certifications. All entries begin **Proposed / E0**. New `WEH-031`–`WEH-040` entries are candidate additions; their identifiers and status must be reconciled with the authoritative registry before release.

## 3. Common experimental contract

For every study, freeze the following before accessing held-out outcomes:

1. **Question and estimand:** what effect is being estimated and for which task population?
2. **Unit of analysis:** query, entity, residual, agent run, research decision, or independently sampled dataset.
3. **Intervention and baseline:** precise implementation and matched information access; include a simple conventional baseline.
4. **Outcome and constraints:** primary metric, acceptable error, latency, memory, compute, human effort and safety boundaries.
5. **Sampling:** workload strata, randomization unit, independence assumptions, sample-size or precision justification.
6. **Data hygiene:** immutable train/validation/test splits; leakage checks; consent, licenses, and privacy review where applicable.
7. **Statistics:** effect sizes, confidence intervals, multiple-comparison control, heterogeneity and sensitivity analyses.
8. **Reproducibility:** dataset and code hashes, environment, seeds, hardware, timestamps, failure traces and raw metrics.
9. **Falsification:** explicit failure threshold or counterexample, plus handling of null and inconclusive results.
10. **Relay:** register result, adverse evidence, definition implications, decision and unresolved residuals.

Use paired workload comparisons when possible; report distributions (including p95 latency) rather than averages alone. For noninferiority of exact search, require zero observed correctness violations in a comprehensive conformance suite and a documented proof of pruning safety where applicable; a finite test alone cannot prove universal correctness.

## 4. Hypothesis index

| ID | Domain | Prediction | Primary endpoint |
|---|---|---|---|
| WEH-001 | Architecture | Typed perspectives reduce category errors | Contract violation rate |
| WEH-002 | Architecture | Identity/representation separation improves entity continuity | Identity mismatch rate |
| WEH-003 | Algorithm | WE-HDT preserves exact retrieval with certified pruning | Recall and correctness |
| WEH-004 | Algorithm | Adaptive blocks improve selected skewed workloads | Cost at fixed recall |
| WEH-005 | Algorithm | Two-phase localization reduces expensive resolutions | Resolution calls/query |
| WEH-006 | Algorithm | Perspective routing improves mixed-query efficiency | p95 latency/cost |
| WEH-007 | Architecture | AVIB capability allocation beats uniform agents under budgets | Utility per compute |
| WEH-008 | Architecture | Lightweight MLIUs improve modularity without excess overhead | Integration effort/cost |
| WEH-009 | Discovery | Residual registry improves anomaly traceability | Trace completeness |
| WEH-010 | Discovery | Reverse CCC produces more useful testable questions | Valid question yield |
| WEH-011 | Discovery | Cross-perspective residuals improve hypothesis generation | Held-out validation yield |
| WEH-012 | Discovery | Typed metric gates reduce invalid metric promotions | False promotion rate |
| WEH-013 | Discovery | Independent validation reduces spurious discoveries | Replication success |
| WEH-014 | Governance | Delta-type separation prevents erroneous updates | Misclassified delta rate |
| WEH-015 | Algorithm | CDE policy separation handles cyclic domains correctly | Legal coverage/termination |
| WEH-016 | Algorithm | Adaptive branching improves constrained search efficiency | Quality per node/time |
| WEH-017 | Architecture | WE-HDT and CDE compose with fewer interface failures | Cross-system failures |
| WEH-018 | Collective Learning | Relay provenance reduces repeated invalid research | Duplicate failure rate |
| WEH-019 | Collective Learning | Diverse adversarial roles improve error detection | Detection rate |
| WEH-020 | Collective Learning | Independent evidence accounting improves calibration | Calibration error |
| WEH-021 | Collective Learning | Repeated execution can create reusable learning assets | Transfer gain |
| WEH-022 | Self-Model | Multi-perspective self-models improve self-prediction | Forecast calibration |
| WEH-023 | Self-Model | Self-residual loops improve bounded adaptation | Utility under constraints |
| WEH-024 | Self-Model | Explicit observer boundaries reduce self-reference confusion | Boundary violations |
| WEH-025 | Definition | Counterexample-led revision improves definition utility | Conformance/coverage |
| WEH-026 | Definition | Minimal-kernel contracts enable cross-domain reuse | Reuse with low exceptions |
| WEH-027 | Governance | Explicit leftovers improve downstream research decisions | Resolved unknowns/time |
| WEH-028 | Algorithm | WE-SIO adds value beyond SQL/index baselines in selected tasks | Quality-cost frontier |
| WEH-029 | Discovery | Residual-driven clinical subgroup hypotheses survive external tests | External validity |
| WEH-030 | Governance | Claim-scoped evidence gates reduce unsupported conclusions | Unsupported claim rate |
| WEH-031 | Mask-first cost | Task-conditioned masking reduces net compute on suitable workloads | Total cost at matched correctness |
| WEH-032 | Mature structures | Selective reuse reduces unnecessary rebuilds without excess forgetting | Rebuild cost and regression rate |
| WEH-033 | Epistemic separation | Distinct EK/OK/RER views reduce category errors | False epistemic classification rate |
| WEH-034 | Mask policy relay | Versioned mask policies transfer with net benefit | Transfer gain after overhead |
| WEH-035 | SQL mapping | Typed SQL-to-WE mapping reduces semantic mapping errors | Critical mapping error rate |
| WEH-036 | SQL localization | Mask-first schema selection improves cost at noninferior correctness | Cost at matched answer correctness |
| WEH-037 | SQL epistemic states | EK/OK/RER separation reduces false knowledge promotions | False promotion rate |
| WEH-038 | Residual diagnosis | Qualified RER improves attribution and reproducibility | Attribution accuracy/reproduction |
| WEH-039 | SQL mask relay | Reusable mask policies transfer across compatible schemas | Net cross-schema benefit |
| WEH-040 | Knowledge governance | Promotion/withdrawal contracts reduce unsupported claims | Unsupported derived claim rate |

## 5. Falsifiable hypothesis protocols

The following are **protocol drafts**. No numerical results or effect sizes are asserted. In each test, compare against matched baselines and document uncertainty, costs and adverse cases.

### WEH-001 — Typed perspective descriptors reduce semantic category errors

**Prediction:** Explicit descriptors distinguishing mathematical metric, measurement, similarity, and directional relation reduce invalid operator use relative to untyped numeric-column representations.  

**Discriminating experiment:** Blindly assign the same synthetic and real-schema tasks to typed and untyped implementations; compare violations under a shared audit rubric.  

**Primary endpoint:** Contract violation rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No meaningful reduction, or increased errors after controlling for implementation complexity.  

**Threats to validity:** Developer training, schema quality, task familiarity.  

**Source cross-references:** WE-SIO-002; SPEC-001; SPEC-002; CASE-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-002 — Identity is more stable when separated from metric signatures

**Prediction:** Explicit identity, representation, and perspective versions lower accidental merges/splits during attribute change and source reconciliation.  

**Discriminating experiment:** Construct longitudinal entity datasets with aliases, changing attributes, duplicate records, and uncertain links; compare record-linkage errors.  

**Primary endpoint:** Identity mismatch rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Equal or worse identity continuity with matched information and effort.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-001; WE-SIO-002; SPEC-001; CASE-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-003 — Certified WE-HDT pruning can preserve exact query semantics

**Prediction:** Under formally stated distance bounds and complete candidate routing, WE-HDT can return the same exact results as exhaustive search.  

**Discriminating experiment:** Property-based and adversarial tests across boundaries, ties, duplicates, missing coordinates, and updates; compare every result to brute force.  

**Primary endpoint:** Recall and correctness. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Any unexplained false negative under the claimed exact contract.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-003; SPEC-002; SPEC-003; CASE-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-004 — Perspective-adaptive blocks can improve selected skewed workloads

**Prediction:** Adaptive block partitioning can lower end-to-end cost on specified nonuniform distributions versus tuned fixed blocks and tuned k-d trees.  

**Discriminating experiment:** Preregister low/medium/high-dimensional, static/dynamic, uniform/skewed workload families; measure build, memory, p50/p95 latency, update, and recall.  

**Primary endpoint:** Cost at fixed recall. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No improvement on prespecified target families, or improvement disappears after tuning and maintenance costs.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-003; WE-SIO-004; CASE-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-005 — Two-phase candidate localization reduces expensive resolutions

**Prediction:** A sound candidate stage reduces downstream exact evaluations without sacrificing the required recall.  

**Discriminating experiment:** Compare exhaustive resolution, single-stage indexing, and two-stage pipelines with equal quality guarantees.  

**Primary endpoint:** Resolution calls/query. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Candidate filtering overhead exceeds saved resolution cost, or required recall is violated.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-001; WE-SIO-003; CASE-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-006 — Perspective-aware routing improves mixed-query workloads

**Prediction:** Query-specific routing across Euclidean, metric, and relational indexes can improve the latency-cost frontier over a single universal index.  

**Discriminating experiment:** Mixed workload with known ground truth; compare routing against best single index and oracle routing upper bound.  

**Primary endpoint:** p95 latency/cost. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Routing overhead or mistakes eliminate benefits.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-002; WE-SIO-003; EXT-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-007 — AVIB capability allocation improves utility per compute

**Prediction:** Selectively activating richer intelligence operations at blocks yields higher task utility at a fixed resource budget than uniform rich agents or uniform minimal nodes.  

**Discriminating experiment:** Equal-budget ablation of adaptive and uniform allocations; include activation, coordination, and migration costs.  

**Primary endpoint:** Utility per compute. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No quality gain at matched total cost or unstable split/merge oscillation.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-004; SPEC-003; EXT-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-008 — MLIU contracts improve interoperability

**Prediction:** Small typed intelligence units with six operations (Locate, Resolve, Relate, Infer, Question, Evolve) reduce integration defects versus ad hoc per-node interfaces.  

**Discriminating experiment:** Independent teams implement equivalent workflows with and without contract templates; compare conformance, effort, and runtime overhead.  

**Primary endpoint:** Integration effort/cost. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Added complexity dominates or contract coverage is inadequate.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-005; SPEC-003; SPEC-004.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-009 — Residual registries improve traceability

**Prediction:** First-class residual records with provenance, uncertainty, versioning, and unresolved status improve later explanation and auditability.  

**Discriminating experiment:** Controlled retrospective investigation with registry versus ordinary logging; blind assessors score reconstruction completeness and time.  

**Primary endpoint:** Trace completeness. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No measurable benefit after accounting for extra documentation effort.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-007; SPEC-005; CASE-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-010 — Reverse CCC improves useful question yield

**Prediction:** Residual-driven reverse questioning produces more independently testable, nonredundant questions per unit effort than prompt-only or random question generation.  

**Discriminating experiment:** Blind evaluation against AQSI-only, expert-only, and randomized baselines; track novelty, testability, cost, and eventual empirical yield.  

**Primary endpoint:** Valid question yield. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Equal or lower validated yield.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-006; WE-SIO-007; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-011 — Cross-perspective residual analysis improves hypothesis yield

**Prediction:** Typed cross-perspective evidence can uncover hypotheses missed by single-perspective analysis.  

**Discriminating experiment:** Synthetic ground-truth mechanisms and held-out real-world tasks; compare hypothesis precision and independent validation.  

**Primary endpoint:** Held-out validation yield. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Gains vanish after multiple-testing correction or data-leakage controls.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-006; WE-SIO-008; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-012 — Metric validation gates prevent invalid promotion

**Prediction:** Explicit semantic, mathematical, measurement, robustness, and governance gates reduce the rate of falsely labeling a relation as a mathematical metric.  

**Discriminating experiment:** Seed candidate formulas violating nonnegativity, identity, symmetry, or triangle inequality; compare detection with ungated generation.  

**Primary endpoint:** False promotion rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Gates fail to catch seeded violations or reject nearly all valid candidates.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-008; SPEC-002; SPEC-005; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-013 — Independent checks reduce spurious discovery

**Prediction:** Separate hypothesis-generation and validation datasets, plus adversarial review, reduce unsupported promotions.  

**Discriminating experiment:** Compare workflows with and without independent evaluation, measuring replication and false discovery at equal candidate budget.  

**Primary endpoint:** Replication success. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No reduction after controlling for selection effects and statistical power.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-007; WE-SIO-008; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-014 — Typed deltas reduce category confusion

**Prediction:** Distinguishing world, observation, epistemic, and structural/operational deltas prevents incorrect claims that a database update changed the world.  

**Discriminating experiment:** Annotated event streams including corrections, delayed observations, true events, and model revisions; compare classification and downstream action errors.  

**Primary endpoint:** Misclassified delta rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No improvement over a well-designed conventional event-sourcing baseline.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-009; CASE-001; CASE-004.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-015 — CDE policy separation accommodates cycles without unsound pruning

**Prediction:** Separating state-transition legality from optional path-memory/no-reuse policy preserves legal solutions in cyclic domains such as chess.  

**Discriminating experiment:** Enumerate legal state transitions and repetitions; compare generalized CDE against variants enforcing unconditional delta nonreuse.  

**Primary endpoint:** Legal coverage/termination. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Policy-separated implementation loses legal transitions or fails its specified termination bound.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-009; CASE-004.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-016 — Adaptive M→N branching improves bounded search

**Prediction:** Budget-aware adaptive branching can improve solution quality per node expansion or time versus fixed branching in selected constrained problems.  

**Discriminating experiment:** Chess puzzles, routing, scheduling, and synthetic constrained state spaces; use fixed budgets and equal evaluation functions.  

**Primary endpoint:** Quality per node/time. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No prespecified advantage or poorer worst-case behavior.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-009; CASE-004; EXT-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-017 — WE-HDT/CDE interoperability reduces localization failures

**Prediction:** Typed candidate/entity outputs from WE-HDT and typed state/delta interfaces in CDE reduce semantic integration defects in composite workflows.  

**Discriminating experiment:** Compare contract-mediated and ad hoc integration in routing, entity resolution, and scheduling pipelines.  

**Primary endpoint:** Cross-system failures. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Comparable failures with lower cost for simpler integration.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-003; WE-SIO-009; EXT-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-018 — Research relay provenance reduces repeated failures

**Prediction:** Sharing counterexamples, negative results, and exact experiment manifests reduces redundant invalid attempts across teams/agents.  

**Discriminating experiment:** Randomized teams with and without prior relay packages; measure repeated failed hypotheses, time, and novel validated outputs.  

**Primary endpoint:** Duplicate failure rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No net benefit after documentation and retrieval overhead.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-012; SPEC-006; EXT-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-019 — Diverse adversarial agents improve defect detection

**Prediction:** Role-diverse generator/critic/verifier teams detect more seeded flaws than equal-budget homogeneous ensembles.  

**Discriminating experiment:** Blind seeded defect corpus; matched model budgets, prompts, and tools; track detection, false alarms, and correlated failures.  

**Primary endpoint:** Detection rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No incremental detection at matched budget.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** EXT-002; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-020 — Evidence independence accounting improves confidence calibration

**Prediction:** Explicitly recording shared sources and correlated agent judgments prevents overconfident consensus.  

**Discriminating experiment:** Inject common-source misinformation and compare calibration metrics such as Brier score and expected calibration error.  

**Primary endpoint:** Calibration error. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Calibration does not improve or useful evidence is excessively discounted.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** EXT-002; SPEC-005.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-021 — Repeated execution can create transferable relay assets

**Prediction:** Repeated runs with preserved observations and failures can produce improvements transferable to new workloads, beyond merely replaying the same task.  

**Discriminating experiment:** Hold out new task distributions; compare persistent structured relay against stateless repeated execution and raw-log memory.  

**Primary endpoint:** Transfer gain. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No out-of-distribution gain or unmanageable memory overhead.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-012; EXT-002.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-022 — Multi-perspective self-models improve self-prediction

**Prediction:** Capability, resource, uncertainty, history, dependency, and external-evaluation perspectives improve calibrated forecasts of the entity's own task performance.  

**Discriminating experiment:** Compare static, single-perspective, and multi-perspective self-models on held-out tasks; measure calibration, discrimination, and compute cost.  

**Primary endpoint:** Forecast calibration. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No significant improvement or model leakage masquerading as self-knowledge.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-010; CASE-005; EXT-004.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-023 — Self-residual loops improve constrained adaptation

**Prediction:** Comparing predicted and observed self-performance, then applying validated updates, improves bounded task utility without violating safety/resource contracts.  

**Discriminating experiment:** Matched adaptive agents with and without residual-driven revisions; audit constraint violations and rollback.  

**Primary endpoint:** Utility under constraints. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Utility fails to improve or safety regressions outweigh benefits.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** CASE-005; EXT-004; WE-SIO-009.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-024 — Observer/subject boundary contracts reduce self-reference errors

**Prediction:** Explicit boundaries among entity, self-model, external observer, and evidence reduce invalid self-referential claims.  

**Discriminating experiment:** Adversarial tasks involving nested self-reports, stale identity, contradictory external evidence, and authorization changes.  

**Primary endpoint:** Boundary violations. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No reduction in provenance or boundary violations.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-010; EXT-004; SPEC-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-025 — Counterexample-driven definition revision improves operational coverage

**Prediction:** A definition-evolution loop using counterexamples, regression tests, and explicit exceptions produces more reusable definitions than unconstrained rewriting.  

**Discriminating experiment:** Compare definitions over successive novel domains; score ambiguity, coverage, vacuity, and regressions using blinded judges and executable contracts.  

**Primary endpoint:** Conformance/coverage. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Increased vagueness or no improvement in transfer.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-011; SPEC-006.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-026 — Minimal-kernel contracts enable cross-domain reuse

**Prediction:** A small shared entity/perspective/delta kernel plus domain-specific extensions supports multiple domains with fewer semantic exceptions than monolithic universal schemas.  

**Discriminating experiment:** Implement SQL, spatial, clinical research, chess, and self-modeling adapters; count exceptions, conformance failures, and engineering effort.  

**Primary endpoint:** Reuse with low exceptions. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** Core is too weak to constrain behavior or too rigid to accommodate valid domains.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-001; WE-SIO-011; CASE-001 through CASE-005.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-027 — Explicit leftovers improve research prioritization

**Prediction:** Explicit unresolved questions, blocked assumptions, and failed tests improve subsequent team's decisions relative to success-only summaries.  

**Discriminating experiment:** Randomized handoff study; compare follow-up experiment relevance, duplicated work, and time to resolve a key unknown.  

**Primary endpoint:** Resolved unknowns/time. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No net improvement.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** WE-SIO-012; SPEC-006; research-trace/UNRESOLVED-RESIDUALS.md.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-028 — WE-SIO adds task-specific value beyond established SQL/index tools

**Prediction:** In selected multi-perspective entity workflows, a WE-SIO layer improves evidence completeness or total quality-cost tradeoff over tuned SQL, spatial index, and graph baselines.  

**Discriminating experiment:** Use identical data, identity semantics, permissions, and workload; include schema design, maintenance, and audit overhead.  

**Primary endpoint:** Quality-cost frontier. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No gain beyond conventional indexes, graph databases, or well-designed event sourcing.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** CASE-001; CASE-002; EXT-001.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-029 — Clinical residual hypotheses generalize under independent validation

**Prediction:** Residual-first, confounder-aware research workflows can generate treatment-response heterogeneity hypotheses that survive genuinely independent validation more often than specified conventional alternatives.  

**Discriminating experiment:** Retrospective deidentified or synthetic data first; prespecified external cohort validation; proper adjustment for selection, missingness, multiplicity, and confounding.  

**Primary endpoint:** External validity. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No reproducible gain, leakage, or clinically implausible unstable findings.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** CASE-003; EXT-003; SPEC-005.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.

### WEH-030 — Claim-scoped evidence gates reduce unsupported conclusions

**Prediction:** Requiring each promoted claim to cite scope, provenance, counterevidence, and validation status reduces unsupported statements in multi-agent research reports.  

**Discriminating experiment:** Blind audits of matched reports with and without evidence gates; assess unsupported claim rates and review cost.  

**Primary endpoint:** Unsupported claim rate. Define the direction, measurement unit, aggregation level, acceptable threshold and confidence interval in the preregistration.

**Potential refutation:** No reduction or prohibitive review overhead.  

**Threats to validity:** Workload selection, implementation quality, correlated evidence and evaluation leakage.

**Source cross-references:** SPEC-005; SPEC-006; EXT-002; EXT-003.

**Required evidence:** paired baseline results, negative-control or adversarial cases, raw trace manifest, uncertainty estimate and an explicit `Supported / Mixed / Refuted / Suspended` recommendation.


### 5A. Extension protocols — WEH-031 through WEH-040

These additions operationalize EXT-005 and EXT-006. Each protocol is **Proposed / E0**; preregister thresholds, sample sizes and equivalence/noninferiority margins before confirmatory experiments. Tests must report negative results, evidence dependence and any authorization or completeness violation.

#### WEH-031 — Mask-first efficiency under matched correctness

**Prediction:** Task-conditioned masking reduces net compute on suitable workloads.

**Discriminating experiment:** Compare adaptive task-conditioned node/edge/metric/operation masks against full-view execution, fixed masks, and eager structural rebuild across stratified tasks. Include mask construction, invalidation, fallback and selection overhead.

**Primary endpoint:** End-to-end compute/time at exact correctness or preregistered recall noninferiority.

**Potential refutation:** No net savings or unsafe omissions after overhead is counted.

**Threats to validity:** Mask training leakage; workload cherry-picking; stale policies.

**Source cross-references:** EXT-005; WE-SIO-004/005/009; SPEC-003; MCT; D5.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-032 — Mature-structure retention versus premature reconstruction

**Prediction:** Selective reuse reduces unnecessary rebuilds without excess forgetting.

**Discriminating experiment:** Run workload and evidence drift sequences with reuse-first, eager-rebuild, and static baselines; inject corrupt indexes and incompatible schema updates as counterexamples.

**Primary endpoint:** Total lifecycle cost, reconstruction frequency, correctness regression and stale-knowledge rate.

**Potential refutation:** Reuse causes unacceptable stale results or costs more than appropriate rebuilding.

**Threats to validity:** Nonstationarity, caching confounds, unmeasured maintenance.

**Source cross-references:** EXT-005; WE-SIO-004/009; SPEC-003.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-033 — Epistemic separation prevents unknown/residual confusion

**Prediction:** Distinct EK/OK/RER views reduce category errors.

**Discriminating experiment:** Blind annotators or implementations classify synthetic and domain-grounded unknowns, missing values, qualified contradictions, and rejected residuals with typed EK/OK/RER versus untyped buckets.

**Primary endpoint:** False residual admission and false established-claim classification.

**Potential refutation:** No reduction, or added categories increase misclassification at matched effort.

**Threats to validity:** Annotation disagreement, ambiguous baselines, class imbalance.

**Source cross-references:** EXT-005; WE-SIO-007; SPEC-005; ESC/RQC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-034 — Mask policy relay yields transferable benefit

**Prediction:** Versioned mask policies transfer with net benefit.

**Discriminating experiment:** Transfer versioned mask policies between held-out compatible tasks; compare fresh policy training, static masks and no masks, charging transfer validation and adaptation.

**Primary endpoint:** Net cost-quality gain and transfer failure rate.

**Potential refutation:** No positive net gain or policy reuse violates coverage/security.

**Threats to validity:** Task overlap, schema similarity, hidden transfer leakage.

**Source cross-references:** EXT-005; SPEC-003; WE-SIO-004.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-035 — SQL-to-WE mapping fidelity

**Prediction:** Typed SQL-to-WE mapping reduces semantic mapping errors.

**Discriminating experiment:** Evaluate typed mappings across normalized schemas, event tables, many-to-many JOINs, NULL semantics and key collisions against naive row=entity/column=metric mapping and expert-designed rules.

**Primary endpoint:** Critical semantic mapping errors per schema/task.

**Potential refutation:** No lower error rate or excessive false identity claims.

**Threats to validity:** Schema selection, annotation bias, baseline weakness.

**Source cross-references:** EXT-006; SPEC-001/002/005.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-036 — Mask-first SQL schema localization

**Prediction:** Mask-first schema selection improves cost at noninferior correctness.

**Discriminating experiment:** Compare full-schema retrieval, strong schema-linking methods and authorized task-conditioned masks on broad SQL workloads, including schema drift and security tests.

**Primary endpoint:** End-to-end cost at preregistered noninferior answer correctness.

**Potential refutation:** Correctness loss, access leakage, or no net savings after mask overhead.

**Threats to validity:** Database optimizer effects, workload difficulty, schema caching.

**Source cross-references:** EXT-006; SPEC-003; MIC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-037 — SQL epistemic-state reliability

**Prediction:** EK/OK/RER separation reduces false knowledge promotions.

**Discriminating experiment:** Inject unknown variables, NULLs, data defects, conflicting rows and legitimate model residuals into SQL workflows; compare EK/OK/RER contracts against undifferentiated analysis.

**Primary endpoint:** False promotion and epistemic misclassification rate.

**Potential refutation:** No improvement after matched reviewer effort.

**Threats to validity:** Fixture realism, error-label reliability, implementation skill.

**Source cross-references:** EXT-006; SPEC-005; ESC/KPC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-038 — Qualified residual diagnosis

**Prediction:** Qualified RER improves attribution and reproducibility.

**Discriminating experiment:** Use controlled sensor error, JOIN fanout, confounding, drift, model misspecification and true synthetic effects; compare RER baseline-qualified records with generic anomaly logs.

**Primary endpoint:** Correct root-cause attribution and independent reproducibility.

**Potential refutation:** No gain, or false novelty attribution increases.

**Threats to validity:** Known ground-truth design, selection bias, synthetic realism.

**Source cross-references:** EXT-006; WE-SIO-007; SPEC-005; RQC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-039 — Cross-schema mask policy relay

**Prediction:** Reusable mask policies transfer across compatible schemas.

**Discriminating experiment:** Transfer versioned mask strategies across compatible but nonidentical SQL schemas; explicitly charge adaptation, invalidation and permission revalidation costs.

**Primary endpoint:** Net transfer benefit and safety/correctness failure rate.

**Potential refutation:** Transfer cost exceeds benefit or unsafe mask reuse occurs.

**Threats to validity:** Schema family leakage, small schema diversity.

**Source cross-references:** EXT-006; SPEC-003; MIC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

#### WEH-040 — Governed SQL-derived knowledge evolution

**Prediction:** Promotion/withdrawal contracts reduce unsupported claims.

**Discriminating experiment:** Compare contract-gated evidence review, promotion, retraction and dependency tracking with unconstrained agent-generated SQL claims under adversarial and held-out evidence.

**Primary endpoint:** Unsupported derived claims, successful withdrawals and audit completeness.

**Potential refutation:** No reduction in unsupported claims or excessive governance failure.

**Threats to validity:** Reviewer bias, dependence among evidence sources, prompt sensitivity.

**Source cross-references:** EXT-006; SPEC-005; KPC.

**Required evidence:** frozen protocol, matched baseline, independent evaluation where feasible, complete cost accounting, counterexamples, uncertainty and linked registry decision.

## 6. Preregistered study families and baselines

### 6.1 Semantic and identity conformance (WEH-001, 002, 014, 024, 026, 030)

- Construct typed/untyped schemas, ambiguous identity merges, delayed corrections, observer-boundary violations and false metric declarations.
- Compare a minimal typed WE contract against a conventional schema plus explicit hand-coded validation. Match available metadata.
- Endpoints: invalid operation rate, identity-continuity errors, delta misclassification, unsupported conclusion rate, integration overhead.
- Negative controls: trivially typed tasks where added structure should confer no advantage.

### 6.2 Retrieval and adaptive structures (WEH-003–008, 017, 028)

- Baselines: brute-force exact scan, conventional k-d tree where applicable, fixed spatial blocks, standard relational/SQL indexes, and a WE-HDT implementation with disabled adaptive components.
- Workloads: uniform and clustered distributions, skew, mixed perspectives, missing Euclidean coordinates, high dimensionality, updates, concurrent readers, adversarial boundary cases.
- Endpoints: exact recall/correctness, candidate count, p50/p95 latency, memory, build/update cost, resolution calls, cost-quality Pareto frontier.
- Exact pruning is permitted only with a sound bound for the relevant perspective and query; otherwise fall back to exhaustive or explicitly approximate retrieval.
- Report failures in which k-d trees or SQL indexes outperform the proposed approach; adaptive partitioning is not novel solely because blocks vary in size.

### 6.3 Questioning and scientific discovery (WEH-009–013, 029)

- Baselines: standard residual logs, conventional feature engineering, random/heuristic question generation, and independent expert hypothesis generation when feasible.
- Use synthetic ground-truth mechanisms and strictly held-out observational datasets; lock hypotheses before independent validation.
- Endpoints: residual trace completeness, useful question yield, false promotion rate, externally validated discovery rate and replication success.
- Controls: permuted labels, sham residuals, null effects, measurement noise, confounding, data leakage and multiple-hypothesis search.
- For clinical examples, use synthetic/deidentified appropriately governed research data; no diagnosis, treatment recommendation or causal claim follows from exploratory residual patterns.

### 6.4 CDE, cyclic domains and constrained search (WEH-015–017)

- Compare generic state-transition search, dynamic programming, branch-and-bound, minimax/alpha-beta in chess, and CDE with policy-controlled memory and branching.
- Record full state including history-dependent legal rights where relevant; repeated states or moves may be legitimate.
- Endpoints: legal-state coverage, incorrect pruning, termination, best-found solution quality per node/time, interface conformance.
- Counterexample: enforcing a global No-Delta-Reuse rule in a domain that permits repeated legal transitions.

### 6.5 Multi-agent and self-modeling (WEH-018–024, 027)

- Compare independent agents, homogeneous ensembles, diverse adversarial roles, and relay systems with or without provenance and evidence-dependence accounting.
- Separate independent observations from copied claims; repeated agreement is not independent corroboration.
- Self-model baselines: static model, single-perspective model, multi-perspective model without residual feedback, and full bounded-feedback model.
- Endpoints: error detection, calibration, prediction quality, transfer gains, resource use, governance violations and unresolved-question resolution.
- No self-modeling benchmark is evidence of subjective experience or consciousness.

### 6.6 Definition evolution (WEH-025–027)

- Freeze a set of novel counterexamples; compare fixed definitions, ad hoc patches, and versioned Definition Evolution Loop with regression tests.
- Endpoints: conformance coverage on unseen cases, semantic exception count, backwards compatibility, human audit time and unresolved residual closure.
- Reject vacuous definitions that achieve coverage only by removing useful constraints.

### 6.7 Mask-first, epistemic separation, and SQL-native extension (WEH-031–040)

- **Mask baselines:** full-view execution, fixed masks, task-conditioned masks, and eager rebuild; match authorization, correctness guarantees and information access.
- **Epistemic baselines:** untyped anomaly/unknown buckets versus Established Knowledge, Open Knowledge, and qualified Residual Evidence Registry (RER) with explicit baseline, comparator, uncertainty and provenance.
- **SQL baselines:** conventional SQL optimization, strong schema linking, expert-defined entity mapping and controlled agent-generated analysis. SQL NULL is not automatically a residual; a row or JOIN is not automatically a world entity or identity proof.
- **Governance controls:** independently reviewed promotion and withdrawal, correlated-source tests, versioned mask invalidation, schema drift, exact-query fallback and adversarial authorization fixtures.
- **Primary reporting:** false residual admission, false promotion, critical SQL mapping errors, net lifecycle cost, recall/answer correctness, investigation attribution, transfer benefit, and safety violations.

## 7. Minimum conformance gates before performance claims

| Gate | Pass criterion | Failure response |
|---|---|---|
| Identity | Stable identity contract under representation changes | Repair identity semantics |
| Perspective typing | No unlicensed metric assumptions or unit mismatch | Reject operation or convert with evidence |
| Exact retrieval | Every returned/pruned decision obeys query contract | Disable unsafe pruning |
| Delta semantics | World, observation, knowledge, structural and activation/mask deltas distinguished | Block update and log discrepancy |
| CDE path policy | Domain-legal repetitions not prohibited by universal rule | Revise cycle policy |
| Residual provenance | Qualified RER records link baseline, observation, comparator, uncertainty, version and evidence | Route unqualified cases to Open Knowledge |
| Epistemic states | Established, Open and Residual evidence remain logically distinguishable | Reject false promotion or residual admission |
| Mask safety | Exactness, authorization, version compatibility and fallback requirements satisfied | Invalidate, broaden or fail closed |
| SQL mapping | Source keys, NULL, JOIN and row semantics not falsely equated with WE identity or metrics | Reject unsafe mapping |
| Discovery validation | Independent held-out evidence required for promotion | Keep hypothesis provisional |
| Agent evidence | Correlated sources not counted as independent | Reweight or flag evidence |
| Self-model boundaries | Observer, model and entity are not conflated | Correct representation |
| Research trace | Negative results and superseded definitions retained | Block evidence promotion |

## 8. Priority and sequencing

**P0 — correctness and semantic validity:** WEH-001, 002, 003, 012, 014, 015, 024, 026, 030, 033, 035, 037, 038, 040. These are prerequisites for stronger claims.

**P1 — comparative feasibility:** WEH-004–008, 009, 010, 017, 018, 020, 025, 028, 031, 032, 036. Benchmark after P0 conformance.

**P2 — exploratory extension:** WEH-011, 013, 016, 019, 021–023, 027, 029, 034, 039. Stage-gate any costly or high-stakes study and avoid promoting unreplicated discoveries.

Priority is a proposed planning aid, not an evidence rank. Dependency links must be checked against `research-trace/HYPOTHESIS-REGISTRY.md`.

## 9. Experiment record template

```yaml
experiment_id: WE-EXP-0001
hypothesis_id: WEH-001
protocol_version: 0.1.0
status: planned  # planned | running | completed | suspended
claim_scope: ""
dataset_manifest_sha256: ""
code_commit: ""
baseline_commit: ""
environment: ""
random_seeds: []
primary_endpoint: ""
effect_direction: ""
success_threshold_preregistered: ""
sample_size_rationale: ""
uncertainty_method: ""
negative_controls: []
safety_privacy_review: ""
results_uri: ""
failure_traces_uri: ""
evidence_grade: E0
decision: pending
decision_log_ref: ""
residual_refs: []
epistemic_state: open  # established | open | residual-evidence (context-specific)
mask_policy_ref: ""
active_view_ref: ""
substrate_and_perspective_versions: []
delta_types_evaluated: []  # world | observation | knowledge | structural | activation
independence_assessment_ref: ""
```

## 10. Cross-document traceability

| Artifact | Responsibility |
|---|---|
| `OPEN-QUESTIONS.md` | Questions motivating hypotheses |
| `research-trace/HYPOTHESIS-REGISTRY.md` | Stable WEH identifiers and evidence status |
| `research-trace/DEFINITION-REGISTRY.md` | Formal terms and definition versions |
| `research-trace/COUNTEREXAMPLE-REGISTRY.md` | Boundary and falsification cases |
| `research-trace/DECISION-LOG.md` | Decisions made after reviewing evidence |
| `research-trace/UNRESOLVED-RESIDUALS.md` | Gaps and remaining research tasks |
| `VALIDATION-ROADMAP.md` | Implementation schedule and acceptance gates |
| `specs/` | Normative interface and conformance contracts |
| `cases/` and `extensions/` | Domain tests and exploratory extensions |

## 11. Explicit leftovers

1. Exact effect sizes, sample sizes and success margins remain to be preregistered for each implementation.
2. The variable-size block algorithm requires an executable reference specification before claims of superiority.
3. WE-HDT exactness requires perspective-specific pruning proofs or exhaustive fallbacks.
4. AVIB/MLIU cost models require measured scheduling and integration overhead.
5. Residual-driven scientific discovery requires independent tests against null and confounded data.
6. CDE must demonstrate operational value beyond generic state-transition notation.
7. Cross-agent evidence dependence needs an auditable statistical accounting rule.
8. Self-model improvement must not be conflated with evidence of subjective experience.
9. Definition Evolution needs blinded counterexamples to avoid post hoc patching.
10. External replication and publication-grade statistical review remain future work.
11. Mask coverage proofs and net lifecycle cost accounting remain unverified.
12. SQL-to-WE mappings require counterexamples for JOIN fanout, NULL semantics and non-entity rows.
13. RER qualification and epistemic promotion need blinded adjudication and independent evidence accounting.
14. The proposed five-way Delta taxonomy must be compared against simpler classifications; added complexity is not presumed beneficial.

## 12. Release discipline

This file specifies research questions and tests; it reports **no completed experiments**. The additions WEH-031–040 must be synchronized with `research-trace/HYPOTHESIS-REGISTRY.md` before release; the authoritative ledger is not automatically modified by this document. Future evidence must be dated, versioned, linked to raw artifacts and recorded in the authoritative registry. Failed and inconclusive studies must remain accessible as Collective Learning relay assets.

**Research contributors:** Sizhe Tan & GPT-Obot  
**License intent:** Apache-2.0 (subject to repository LICENSE).
