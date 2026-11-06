# WE-SIO Hypothesis Registry

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0  
**Date:** 2026-11-05  
**Status:** Research hypotheses; not experimentally validated  
**Research attribution:** Sizhe Tan & GPT-Obot  
**Location:** `research-trace/HYPOTHESIS-REGISTRY.md`

## 1. Purpose and evidentiary boundary

This registry is the cross-document index of falsifiable claims proposed by the WE-SIO research program. It is **not** a catalog of established scientific results. Its function is to preserve the distinction among a motivating conjecture, a specified test, observed evidence, and an independently reproduced finding. The registry records both supportive and adverse outcomes, including hypotheses that are rejected or remain unresolved.

The original research trajectory moves from variable-size spatial blocks and two-phase search toward World Entity representation, hybrid differential trees, perspective-aware intelligence operations, residual-first discovery, constrained delta evolution, collective learning, and self-modeling. That trajectory motivates hypotheses; it does not itself validate them.

**Core rule:** a proposed mechanism is not evidence of its own effectiveness. Performance, reliability, discovery quality, and safety claims require external measurements against explicit baselines.

## 2. Registry conventions

### 2.1 Identifier and status

- **ID:** `WEH-###`, stable across versions. Never reuse an identifier.
- **State:** `Proposed`, `Specified`, `Testing`, `Supported`, `Mixed`, `Refuted`, `Suspended`, or `Superseded`.
- **Initial state:** All entries below are `Proposed`. A drafted test protocol does not constitute a completed experiment.
- **Class:** Architecture, Algorithm, Discovery, Governance, Collective Learning, Self-Model, or Definition.
- **Evidence grade:** `E0` conjecture only; `E1` reproducible synthetic observation; `E2` independently controlled benchmark; `E3` independent external replication; `E4` multi-setting robust evidence. These are project-specific tracking labels, not universal scientific standards.
- **Comparison:** a matched baseline, workload, outcome metric, resource budget, and confidence interval or uncertainty estimate.

### 2.2 Promotion criteria

A hypothesis can move to `Supported` only when a preregistered protocol, accessible evaluation artifacts, independent checks, and meaningful effect estimates are available. `Supported` is scoped to the tested setting. It must not be interpreted as universal truth. `Refuted` requires a specified counterexample or sufficiently powered negative test under the claim's stated conditions. An inconclusive result is `Mixed` or `Suspended`, not automatically refutation.

### 2.3 Reproducibility package

Every executed test should produce a manifest with dataset provenance, licenses/consent where relevant, code and configuration hashes, hardware/software environment, seeds, splits, workload generator, budget, baselines, test statistics, failure traces, limitations, and a decision record. Negative results remain available for relay.

## 3. Master index

| ID | Class | Hypothesis (testable shorthand) | Primary outcome | State | Grade |
|---|---|---|---|---|---|
| WEH-001 | Architecture | Typed perspectives reduce category errors | Contract violation rate | Proposed | E0 |
| WEH-002 | Architecture | Identity/representation separation improves entity continuity | Identity mismatch rate | Proposed | E0 |
| WEH-003 | Algorithm | WE-HDT preserves exact retrieval with certified pruning | Recall and correctness | Proposed | E0 |
| WEH-004 | Algorithm | Adaptive blocks improve selected skewed workloads | Cost at fixed recall | Proposed | E0 |
| WEH-005 | Algorithm | Two-phase localization reduces expensive resolutions | Resolution calls/query | Proposed | E0 |
| WEH-006 | Algorithm | Perspective routing improves mixed-query efficiency | p95 latency/cost | Proposed | E0 |
| WEH-007 | Architecture | AVIB capability allocation beats uniform agents under budgets | Utility per compute | Proposed | E0 |
| WEH-008 | Architecture | Lightweight MLIUs improve modularity without excess overhead | Integration effort/cost | Proposed | E0 |
| WEH-009 | Discovery | Residual registry improves anomaly traceability | Trace completeness | Proposed | E0 |
| WEH-010 | Discovery | Reverse CCC produces more useful testable questions | Valid question yield | Proposed | E0 |
| WEH-011 | Discovery | Cross-perspective residuals improve hypothesis generation | Held-out validation yield | Proposed | E0 |
| WEH-012 | Discovery | Typed metric gates reduce invalid metric promotions | False promotion rate | Proposed | E0 |
| WEH-013 | Discovery | Independent validation reduces spurious discoveries | Replication success | Proposed | E0 |
| WEH-014 | Governance | Delta-type separation prevents erroneous updates | Misclassified delta rate | Proposed | E0 |
| WEH-015 | Algorithm | CDE policy separation handles cyclic domains correctly | Legal coverage/termination | Proposed | E0 |
| WEH-016 | Algorithm | Adaptive branching improves constrained search efficiency | Quality per node/time | Proposed | E0 |
| WEH-017 | Architecture | WE-HDT and CDE compose with fewer interface failures | Cross-system failures | Proposed | E0 |
| WEH-018 | Collective Learning | Relay provenance reduces repeated invalid research | Duplicate failure rate | Proposed | E0 |
| WEH-019 | Collective Learning | Diverse adversarial roles improve error detection | Detection rate | Proposed | E0 |
| WEH-020 | Collective Learning | Independent evidence accounting improves calibration | Calibration error | Proposed | E0 |
| WEH-021 | Collective Learning | Repeated execution can create reusable learning assets | Transfer gain | Proposed | E0 |
| WEH-022 | Self-Model | Multi-perspective self-models improve self-prediction | Forecast calibration | Proposed | E0 |
| WEH-023 | Self-Model | Self-residual loops improve bounded adaptation | Utility under constraints | Proposed | E0 |
| WEH-024 | Self-Model | Explicit observer boundaries reduce self-reference confusion | Boundary violations | Proposed | E0 |
| WEH-025 | Definition | Counterexample-led revision improves definition utility | Conformance/coverage | Proposed | E0 |
| WEH-026 | Definition | Minimal-kernel contracts enable cross-domain reuse | Reuse with low exceptions | Proposed | E0 |
| WEH-027 | Governance | Explicit leftovers improve downstream research decisions | Resolved unknowns/time | Proposed | E0 |
| WEH-028 | Algorithm | WE-SIO adds value beyond SQL/index baselines in selected tasks | Quality-cost frontier | Proposed | E0 |
| WEH-029 | Discovery | Residual-driven clinical subgroup hypotheses survive external tests | External validity | Proposed | E0 |
| WEH-030 | Governance | Claim-scoped evidence gates reduce unsupported conclusions | Unsupported claim rate | Proposed | E0 |

## 4. Hypothesis cards: representation, indexing, and intelligence

### WEH-001 — Typed perspective descriptors reduce semantic category errors

**Claim:** Explicit descriptors distinguishing mathematical metric, measurement, similarity, and directional relation reduce invalid operator use relative to untyped numeric-column representations.  
**Test:** Blindly assign the same synthetic and real-schema tasks to typed and untyped implementations; compare violations under a shared audit rubric.  
**Falsifier:** No meaningful reduction, or increased errors after controlling for implementation complexity.  
**Confounders:** Developer training, schema quality, task familiarity.  
**Sources:** WE-SIO-002; SPEC-001; SPEC-002; CASE-001.

### WEH-002 — Identity is more stable when separated from metric signatures

**Claim:** Explicit identity, representation, and perspective versions lower accidental merges/splits during attribute change and source reconciliation.  
**Test:** Construct longitudinal entity datasets with aliases, changing attributes, duplicate records, and uncertain links; compare record-linkage errors.  
**Falsifier:** Equal or worse identity continuity with matched information and effort.  
**Sources:** WE-SIO-001; WE-SIO-002; SPEC-001; CASE-001.

### WEH-003 — Certified WE-HDT pruning can preserve exact query semantics

**Claim:** Under formally stated distance bounds and complete candidate routing, WE-HDT can return the same exact results as exhaustive search.  
**Test:** Property-based and adversarial tests across boundaries, ties, duplicates, missing coordinates, and updates; compare every result to brute force.  
**Falsifier:** Any unexplained false negative under the claimed exact contract.  
**Important limitation:** This is a correctness hypothesis, not a speed claim.  
**Sources:** WE-SIO-003; SPEC-002; SPEC-003; CASE-002.

### WEH-004 — Perspective-adaptive blocks can improve selected skewed workloads

**Claim:** Adaptive block partitioning can lower end-to-end cost on specified nonuniform distributions versus tuned fixed blocks and tuned k-d trees.  
**Test:** Preregister low/medium/high-dimensional, static/dynamic, uniform/skewed workload families; measure build, memory, p50/p95 latency, update, and recall.  
**Falsifier:** No improvement on prespecified target families, or improvement disappears after tuning and maintenance costs.  
**Caveat:** k-d trees already create nonuniform partitions; variable size alone is not novel.  
**Sources:** WE-SIO-003; WE-SIO-004; CASE-002.

### WEH-005 — Two-phase candidate localization reduces expensive resolutions

**Claim:** A sound candidate stage reduces downstream exact evaluations without sacrificing the required recall.  
**Test:** Compare exhaustive resolution, single-stage indexing, and two-stage pipelines with equal quality guarantees.  
**Falsifier:** Candidate filtering overhead exceeds saved resolution cost, or required recall is violated.  
**Sources:** WE-SIO-001; WE-SIO-003; CASE-002.

### WEH-006 — Perspective-aware routing improves mixed-query workloads

**Claim:** Query-specific routing across Euclidean, metric, and relational indexes can improve the latency-cost frontier over a single universal index.  
**Test:** Mixed workload with known ground truth; compare routing against best single index and oracle routing upper bound.  
**Falsifier:** Routing overhead or mistakes eliminate benefits.  
**Sources:** WE-SIO-002; WE-SIO-003; EXT-001.

### WEH-007 — AVIB capability allocation improves utility per compute

**Claim:** Selectively activating richer intelligence operations at blocks yields higher task utility at a fixed resource budget than uniform rich agents or uniform minimal nodes.  
**Test:** Equal-budget ablation of adaptive and uniform allocations; include activation, coordination, and migration costs.  
**Falsifier:** No quality gain at matched total cost or unstable split/merge oscillation.  
**Sources:** WE-SIO-004; SPEC-003; EXT-002.

### WEH-008 — MLIU contracts improve interoperability

**Claim:** Small typed intelligence units with six operations (Locate, Resolve, Relate, Infer, Question, Evolve) reduce integration defects versus ad hoc per-node interfaces.  
**Test:** Independent teams implement equivalent workflows with and without contract templates; compare conformance, effort, and runtime overhead.  
**Falsifier:** Added complexity dominates or contract coverage is inadequate.  
**Sources:** WE-SIO-005; SPEC-003; SPEC-004.

## 5. Hypothesis cards: residuals and scientific discovery

### WEH-009 — Residual registries improve traceability

**Claim:** First-class residual records with provenance, uncertainty, versioning, and unresolved status improve later explanation and auditability.  
**Test:** Controlled retrospective investigation with registry versus ordinary logging; blind assessors score reconstruction completeness and time.  
**Falsifier:** No measurable benefit after accounting for extra documentation effort.  
**Sources:** WE-SIO-007; SPEC-005; CASE-003.

### WEH-010 — Reverse CCC improves useful question yield

**Claim:** Residual-driven reverse questioning produces more independently testable, nonredundant questions per unit effort than prompt-only or random question generation.  
**Test:** Blind evaluation against AQSI-only, expert-only, and randomized baselines; track novelty, testability, cost, and eventual empirical yield.  
**Falsifier:** Equal or lower validated yield.  
**Sources:** WE-SIO-006; WE-SIO-007; EXT-003.

### WEH-011 — Cross-perspective residual analysis improves hypothesis yield

**Claim:** Typed cross-perspective evidence can uncover hypotheses missed by single-perspective analysis.  
**Test:** Synthetic ground-truth mechanisms and held-out real-world tasks; compare hypothesis precision and independent validation.  
**Falsifier:** Gains vanish after multiple-testing correction or data-leakage controls.  
**Sources:** WE-SIO-006; WE-SIO-008; EXT-003.

### WEH-012 — Metric validation gates prevent invalid promotion

**Claim:** Explicit semantic, mathematical, measurement, robustness, and governance gates reduce the rate of falsely labeling a relation as a mathematical metric.  
**Test:** Seed candidate formulas violating nonnegativity, identity, symmetry, or triangle inequality; compare detection with ungated generation.  
**Falsifier:** Gates fail to catch seeded violations or reject nearly all valid candidates.  
**Sources:** WE-SIO-008; SPEC-002; SPEC-005; EXT-003.

### WEH-013 — Independent checks reduce spurious discovery

**Claim:** Separate hypothesis-generation and validation datasets, plus adversarial review, reduce unsupported promotions.  
**Test:** Compare workflows with and without independent evaluation, measuring replication and false discovery at equal candidate budget.  
**Falsifier:** No reduction after controlling for selection effects and statistical power.  
**Sources:** WE-SIO-007; WE-SIO-008; EXT-003.

## 6. Hypothesis cards: delta evolution and SIF localization

### WEH-014 — Typed deltas reduce category confusion

**Claim:** Distinguishing world, observation, epistemic, and structural/operational deltas prevents incorrect claims that a database update changed the world.  
**Test:** Annotated event streams including corrections, delayed observations, true events, and model revisions; compare classification and downstream action errors.  
**Falsifier:** No improvement over a well-designed conventional event-sourcing baseline.  
**Sources:** WE-SIO-009; CASE-001; CASE-004.

### WEH-015 — CDE policy separation accommodates cycles without unsound pruning

**Claim:** Separating state-transition legality from optional path-memory/no-reuse policy preserves legal solutions in cyclic domains such as chess.  
**Test:** Enumerate legal state transitions and repetitions; compare generalized CDE against variants enforcing unconditional delta nonreuse.  
**Falsifier:** Policy-separated implementation loses legal transitions or fails its specified termination bound.  
**Sources:** WE-SIO-009; CASE-004.

### WEH-016 — Adaptive M→N branching improves bounded search

**Claim:** Budget-aware adaptive branching can improve solution quality per node expansion or time versus fixed branching in selected constrained problems.  
**Test:** Chess puzzles, routing, scheduling, and synthetic constrained state spaces; use fixed budgets and equal evaluation functions.  
**Falsifier:** No prespecified advantage or poorer worst-case behavior.  
**Sources:** WE-SIO-009; CASE-004; EXT-001.

### WEH-017 — WE-HDT/CDE interoperability reduces localization failures

**Claim:** Typed candidate/entity outputs from WE-HDT and typed state/delta interfaces in CDE reduce semantic integration defects in composite workflows.  
**Test:** Compare contract-mediated and ad hoc integration in routing, entity resolution, and scheduling pipelines.  
**Falsifier:** Comparable failures with lower cost for simpler integration.  
**Sources:** WE-SIO-003; WE-SIO-009; EXT-001.

## 7. Hypothesis cards: multi-agent and collective learning

### WEH-018 — Research relay provenance reduces repeated failures

**Claim:** Sharing counterexamples, negative results, and exact experiment manifests reduces redundant invalid attempts across teams/agents.  
**Test:** Randomized teams with and without prior relay packages; measure repeated failed hypotheses, time, and novel validated outputs.  
**Falsifier:** No net benefit after documentation and retrieval overhead.  
**Sources:** WE-SIO-012; SPEC-006; EXT-002.

### WEH-019 — Diverse adversarial agents improve defect detection

**Claim:** Role-diverse generator/critic/verifier teams detect more seeded flaws than equal-budget homogeneous ensembles.  
**Test:** Blind seeded defect corpus; matched model budgets, prompts, and tools; track detection, false alarms, and correlated failures.  
**Falsifier:** No incremental detection at matched budget.  
**Sources:** EXT-002; EXT-003.

### WEH-020 — Evidence independence accounting improves confidence calibration

**Claim:** Explicitly recording shared sources and correlated agent judgments prevents overconfident consensus.  
**Test:** Inject common-source misinformation and compare calibration metrics such as Brier score and expected calibration error.  
**Falsifier:** Calibration does not improve or useful evidence is excessively discounted.  
**Sources:** EXT-002; SPEC-005.

### WEH-021 — Repeated execution can create transferable relay assets

**Claim:** Repeated runs with preserved observations and failures can produce improvements transferable to new workloads, beyond merely replaying the same task.  
**Test:** Hold out new task distributions; compare persistent structured relay against stateless repeated execution and raw-log memory.  
**Falsifier:** No out-of-distribution gain or unmanageable memory overhead.  
**Sources:** WE-SIO-012; EXT-002.

## 8. Hypothesis cards: self-modeling and definition evolution

### WEH-022 — Multi-perspective self-models improve self-prediction

**Claim:** Capability, resource, uncertainty, history, dependency, and external-evaluation perspectives improve calibrated forecasts of the entity's own task performance.  
**Test:** Compare static, single-perspective, and multi-perspective self-models on held-out tasks; measure calibration, discrimination, and compute cost.  
**Falsifier:** No significant improvement or model leakage masquerading as self-knowledge.  
**Boundary:** No inference about consciousness or subjective experience.  
**Sources:** WE-SIO-010; CASE-005; EXT-004.

### WEH-023 — Self-residual loops improve constrained adaptation

**Claim:** Comparing predicted and observed self-performance, then applying validated updates, improves bounded task utility without violating safety/resource contracts.  
**Test:** Matched adaptive agents with and without residual-driven revisions; audit constraint violations and rollback.  
**Falsifier:** Utility fails to improve or safety regressions outweigh benefits.  
**Sources:** CASE-005; EXT-004; WE-SIO-009.

### WEH-024 — Observer/subject boundary contracts reduce self-reference errors

**Claim:** Explicit boundaries among entity, self-model, external observer, and evidence reduce invalid self-referential claims.  
**Test:** Adversarial tasks involving nested self-reports, stale identity, contradictory external evidence, and authorization changes.  
**Falsifier:** No reduction in provenance or boundary violations.  
**Sources:** WE-SIO-010; EXT-004; SPEC-001.

### WEH-025 — Counterexample-driven definition revision improves operational coverage

**Claim:** A definition-evolution loop using counterexamples, regression tests, and explicit exceptions produces more reusable definitions than unconstrained rewriting.  
**Test:** Compare definitions over successive novel domains; score ambiguity, coverage, vacuity, and regressions using blinded judges and executable contracts.  
**Falsifier:** Increased vagueness or no improvement in transfer.  
**Sources:** WE-SIO-011; SPEC-006.

### WEH-026 — Minimal-kernel contracts enable cross-domain reuse

**Claim:** A small shared entity/perspective/delta kernel plus domain-specific extensions supports multiple domains with fewer semantic exceptions than monolithic universal schemas.  
**Test:** Implement SQL, spatial, clinical research, chess, and self-modeling adapters; count exceptions, conformance failures, and engineering effort.  
**Falsifier:** Core is too weak to constrain behavior or too rigid to accommodate valid domains.  
**Sources:** WE-SIO-001; WE-SIO-011; CASE-001 through CASE-005.

### WEH-027 — Explicit leftovers improve research prioritization

**Claim:** Explicit unresolved questions, blocked assumptions, and failed tests improve subsequent team's decisions relative to success-only summaries.  
**Test:** Randomized handoff study; compare follow-up experiment relevance, duplicated work, and time to resolve a key unknown.  
**Falsifier:** No net improvement.  
**Sources:** WE-SIO-012; SPEC-006; research-trace/UNRESOLVED-RESIDUALS.md (planned).

## 9. Hypothesis cards: external baselines and governance

### WEH-028 — WE-SIO adds task-specific value beyond established SQL/index tools

**Claim:** In selected multi-perspective entity workflows, a WE-SIO layer improves evidence completeness or total quality-cost tradeoff over tuned SQL, spatial index, and graph baselines.  
**Test:** Use identical data, identity semantics, permissions, and workload; include schema design, maintenance, and audit overhead.  
**Falsifier:** No gain beyond conventional indexes, graph databases, or well-designed event sourcing.  
**Sources:** CASE-001; CASE-002; EXT-001.

### WEH-029 — Clinical residual hypotheses generalize under independent validation

**Claim:** Residual-first, confounder-aware research workflows can generate treatment-response heterogeneity hypotheses that survive genuinely independent validation more often than specified conventional alternatives.  
**Test:** Retrospective deidentified or synthetic data first; prespecified external cohort validation; proper adjustment for selection, missingness, multiplicity, and confounding.  
**Falsifier:** No reproducible gain, leakage, or clinically implausible unstable findings.  
**Safety boundary:** Research only; not a diagnostic, prescribing, or treatment recommendation system.  
**Sources:** CASE-003; EXT-003; SPEC-005.

### WEH-030 — Claim-scoped evidence gates reduce unsupported conclusions

**Claim:** Requiring each promoted claim to cite scope, provenance, counterevidence, and validation status reduces unsupported statements in multi-agent research reports.  
**Test:** Blind audits of matched reports with and without evidence gates; assess unsupported claim rates and review cost.  
**Falsifier:** No reduction or prohibitive review overhead.  
**Sources:** SPEC-005; SPEC-006; EXT-002; EXT-003.

## 10. Cross-hypothesis dependencies

The hypotheses should not be tested as if they were independent:

| Upstream requirement | Downstream hypotheses | Risk if omitted |
|---|---|---|
| Identity and perspective contracts (WEH-001/002) | WEH-003/006/017/022 | False matches and invalid cross-perspective claims |
| Retrieval soundness (WEH-003) | WEH-004/005/028 | Apparent speed from missed results |
| Provenance and residual integrity (WEH-009) | WEH-010/011/013/029 | Hypothesis leakage and unverifiable discoveries |
| Typed delta semantics (WEH-014/015) | WEH-016/017/023 | Invalid state transitions or false world-change assertions |
| Independent evidence accounting (WEH-020) | WEH-019/021/030 | Correlated consensus mistaken for replication |
| Counterexample-led revision (WEH-025) | WEH-026 | Vacuous or contradictory universalization |

## 11. Priority experiment portfolio

### P0 — Correctness and semantics (must precede performance claims)

1. **P0-A:** Descriptor type-checking and identity continuity: WEH-001/002.
2. **P0-B:** Exact retrieval and adversarial boundary tests: WEH-003.
3. **P0-C:** Mathematical metric validation: WEH-012.
4. **P0-D:** Chess legal transitions, reversibility, repetition, and optional no-reuse policies: WEH-014/015.
5. **P0-E:** Evidence provenance and correlated-source accounting: WEH-009/020.

### P1 — Measured utility

1. **P1-A:** VSB vs tuned k-d tree and fixed blocks: WEH-004/005/006.
2. **P1-B:** AVIB/MLIU equal-budget ablations: WEH-007/008.
3. **P1-C:** Multi-agent role diversity and relay handoff: WEH-018/019/021.
4. **P1-D:** Self-model forecasting and safe adaptation: WEH-022/023.
5. **P1-E:** Definition evolution transfer study: WEH-025/026.

### P2 — Higher-risk discovery claims

1. **P2-A:** Reverse questioning and metric discovery: WEH-010/011/013.
2. **P2-B:** Independent clinical research validation: WEH-029.
3. **P2-C:** Integrated WE-HDT/CDE and end-to-end WE-SIO comparison: WEH-017/028.

No P2 claim should be promoted without satisfying its applicable P0 contracts.

## 12. Standard test record template

Copy this template for every experiment. Preserve failed runs.

```yaml
hypothesis_id: WEH-000
experiment_id: EXP-YYYY-NNN
protocol_version: 0.1.0
preregistered_at: null
owner: null
state: planned
claim_scope: null
baseline: null
dataset:
  provenance: null
  version: null
  split_policy: null
  access_and_privacy: null
implementation:
  commit: null
  environment: null
  seeds: []
  budget: null
metrics:
  primary: null
  secondary: []
  uncertainty_method: null
acceptance_rule: null
negative_controls: []
confounder_checks: []
results:
  effect_estimate: null
  uncertainty: null
  adverse_findings: []
  artifacts: []
replication:
  independent_reviewer: null
  independent_run: null
decision:
  state: Proposed
  evidence_grade: E0
  rationale: Not yet tested
  linked_decision_log: null
leftovers: []
```

## 13. Decision rules and safeguards

1. **Never promote by rhetorical strength.** Architectural elegance is not an empirical result.
2. **Do not compare against weak strawman baselines.** Tune classical alternatives fairly.
3. **Treat exactness separately from efficiency.** An approximate result cannot be silently scored as exact.
4. **Report total cost.** Include indexing, updates, orchestration, validation, and provenance overhead.
5. **Correct for search and selection.** Hypothesis generation across many candidates increases false discovery risk.
6. **Preserve negative evidence.** Failed or contradictory trials remain searchable.
7. **Prevent circular verification.** An agent's agreement with itself is not independent validation.
8. **Protect sensitive data.** Clinical research requires appropriate privacy, access, and governance controls.
9. **Avoid consciousness overclaims.** Self-modeling performance is not evidence of subjective experience.
10. **Version definitions.** A changed meaning requires new conformance tests and an explicit migration decision.

## 14. Links to repository research trace

- `research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md` — original motivation and research questions.
- `research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md` — synthesis of the research trajectory.
- `research-trace/DEFINITION-REGISTRY.md` — evolving definitions and semantic contracts.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md` — known counterexamples and falsification triggers.
- `research-trace/DECISION-LOG.md` — acceptance, rejection, and scope decisions.
- `research-trace/UNRESOLVED-RESIDUALS.md` — unexplained outcomes and research leftovers.
- `TESTABLE-HYPOTHESES.md` — release-facing concise hypothesis overview.
- `VALIDATION-ROADMAP.md` — implementation and experimental sequencing.

Some linked files are planned components of the repository and may not yet exist at this stage of preparation. This registry does not assert their completion.

## 15. Explicit leftovers

- The exact formal algorithm and bounds for Variable-Size Blocks need a canonical specification before speed claims can be meaningful.
- WE-HDT's correctness conditions for relational and nonmetric perspectives require further formalization.
- The minimum viable MLIU implementation and scheduling policy are unspecified.
- The independent contribution of CDE beyond ordinary state-transition/search frameworks remains an open comparison.
- A shared benchmark suite spanning SQL, spatial, scientific, chess, and self-modeling tasks has not been built.
- No WE-SIO benchmark results, external replications, or clinical findings are reported in this version.
- The threshold for promoting a candidate perspective to a trusted operational metric remains domain-dependent.
- Governance of autonomous definition evolution requires authorization, rollback, and conflict-resolution policies.

## 16. Release note

**v0.1.0:** Initial registry of 30 cross-document research hypotheses. Every entry is `Proposed / E0`; tests and evaluation criteria are designs for future work, not claims of completed experiments. Updates should be additive, versioned, and traceable to a decision log.

---

*WE-SIO research principle: define the invariant, not the inventory; preserve the counterexample, not only the success.*
