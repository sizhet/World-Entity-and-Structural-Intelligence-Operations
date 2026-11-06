# Unresolved Residuals — WE-SIO v0.1.0

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Artifact:** Research Trace / Open Residual Registry  
**Version:** 0.1.0  
**Date:** 2026-11-05  
**Research attribution:** Sizhe Tan & GPT-Obot  
**Status:** Proposed research agenda; no empirical validation is implied.

## 1. Purpose

This registry preserves discrepancies between WE-SIO's intended capabilities and what has actually been specified, demonstrated, or validated. An unresolved residual is **not** a failed experiment by default, nor proof that a new scientific mechanism exists. It is an accountable gap with a defined next action.

The registry is intentionally distinct from `OPEN-QUESTIONS.md` (broad inquiries), `HYPOTHESIS-REGISTRY.md` (falsifiable claims), `COUNTEREXAMPLE-REGISTRY.md` (adversarial tests), and `DECISION-LOG.md` (choices and rationale). An entry here should be actionable even when its eventual resolution is negative.

> Unknown is not zero. Unexplained is not useless. A residual is evidence of a gap, not automatically evidence of a new law.

## 2. Operating contract

Every residual shall have an immutable ID, explicit observed or anticipated gap, expectation, scope, evidence status, severity, owner role, verification plan, acceptance/rejection criteria, related artifacts, and an audit trail. Entries may be linked or superseded but not silently erased.

### 2.1 Classification

| Class | Meaning | Example |
|---|---|---|
| SEM | Semantic / definition gap | Identity versus signature |
| COR | Correctness / conformance gap | Candidate completeness |
| PERF | Performance / resource gap | Adaptive partition overhead |
| SCI | Scientific inference gap | Residual versus confounding |
| EVO | Evolution / state semantics gap | Cycles and undo |
| GOV | Governance / provenance gap | Evidence independence |
| INT | Integration / interface gap | SIF routing contract |
| EPI | Epistemic boundary gap | Self-model versus experience |

### 2.2 Status and evidence

**Statuses:** `OPEN`, `SPECIFIED`, `TEST-DESIGNED`, `UNDER-TEST`, `PARTIALLY-RESOLVED`, `RESOLVED`, `REFUTED`, `SUPERSEDED`, `BLOCKED`. The default for this release is `OPEN` or `TEST-DESIGNED`, not `RESOLVED`.

**Evidence:** `E0` conceptual only; `E1` executable synthetic tests; `E2` controlled benchmarks or retrospective studies; `E3` independent replication; `E4` validated deployment under defined conditions. Evidence levels are local conventions, not clinical or scientific certification.

**Priority:** `P0` correctness, safety, or foundational definition; `P1` important architectural and empirical validation; `P2` exploratory or long-horizon research. A priority is not a claim of likelihood.

## 3. Registry overview

| ID | Class | Priority | Open gap | Proposed next evidence |
|---|---|---|---|---|
| UR-001 | SEM | P0 | Entity identity across sources | Identity conformance corpus |
| UR-002 | SEM | P0 | Perspective/metric typing | Typed descriptor test suite |
| UR-003 | COR | P0 | Two-phase candidate completeness | Exact-query oracle |
| UR-004 | PERF | P1 | WE-HDT versus strong baselines | Workload benchmark |
| UR-005 | PERF | P1 | Adaptive block stability | Split/merge stress test |
| UR-006 | PERF | P1 | MLIU overhead versus utility | Capability ablation |
| UR-007 | COR | P0 | Cross-perspective inference validity | Type-safe composition tests |
| UR-008 | SCI | P0 | Residual quality and confounding | Negative-control pipeline |
| UR-009 | SCI | P1 | Metric discovery beyond feature engineering | Held-out discovery benchmark |
| UR-010 | SCI | P1 | Autonomous question usefulness | AQSI ablation |
| UR-011 | EVO | P0 | CDE kernel versus ordinary transition systems | Comparative formalization |
| UR-012 | EVO | P0 | Cycle/termination semantics | Chess and graph tests |
| UR-013 | EVO | P0 | World versus epistemic delta | Event replay and correction |
| UR-014 | INT | P1 | WE-HDT/CDE localization routing | SIF integration prototype |
| UR-015 | GOV | P0 | Agent evidence dependence | Provenance-aware aggregation |
| UR-016 | GOV | P1 | Relay portability and negative results | Cross-team replay |
| UR-017 | EPI | P0 | Self-model calibration versus self-description | Behavioral evaluation |
| UR-018 | EPI | P0 | Subjectivity inference boundary | Claim audit |
| UR-019 | SEM | P1 | Definition evolution without vacuity | Regression counterexamples |
| UR-020 | GOV | P0 | Authorization and privacy across perspectives | Access-control conformance |
| UR-021 | PERF | P1 | High-dimensional and non-Euclidean search | Stress benchmarks |
| UR-022 | SCI | P0 | Clinical case evidence boundary | Protocol and ethics review |
| UR-023 | GOV | P1 | Research trace consistency | Cross-registry audit |
| UR-024 | INT | P2 | Open-ended plugin/perspective compatibility | Versioned interface tests |

## 4. Detailed unresolved residuals

### UR-001 — Cross-source entity identity is not solved by metric similarity
- **Expectation:** Stable entity references remain meaningful across datasets, time, and representations.
- **Gap:** A high similarity score, a database key, and a real-world identity assertion have different semantics; merging them can introduce irreversible errors.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Identity-contract maintainer.
- **Test:** Construct synthetic duplicates, aliases, collisions, merged records, and entity splits; compare conservative linking against ground-truth identity relationships.
- **Exit:** Identity assertions require provenance, uncertainty, scope, reversible merge decisions, and audited counterexamples. No automatic global identity guarantee is claimed.
- **Links:** `SPEC-001`, `CASE-001`, `DEF-001–009` (verify exact registry references).

### UR-002 — Not every perspective is a mathematical metric
- **Expectation:** Search and inference operators use a perspective only when its mathematical and semantic contract permits it.
- **Gap:** Measurements, similarities, directed relations, and distances are easily conflated.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P0. **Owner role:** Perspective-schema maintainer.
- **Test:** Property-based tests for non-negativity, symmetry, identity, and triangle inequality where a true metric is declared; asymmetric counterexamples for directional relations.
- **Exit:** Invalid operator/perspective combinations fail closed; units, domain, uncertainty, and version are checked.
- **Links:** `SPEC-001`, `SPEC-002`, `WE-SIO-002`.

### UR-003 — Two-phase retrieval may drop valid candidates
- **Expectation:** Exact retrieval never loses a qualifying answer during candidate generation.
- **Gap:** Bounding assumptions, stale indexes, or heuristic pruning may introduce false negatives.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Search-correctness maintainer.
- **Test:** Compare candidate+resolve against exhaustive oracle on adversarial boundaries, skew, ties, dynamic updates, and non-Euclidean perspectives.
- **Exit:** Exact mode has a stated completeness guarantee under explicit assumptions; approximate mode reports its different contract.
- **Links:** `CASE-002`, `SPEC-003`, `WE-SIO-003`.

### UR-004 — WE-HDT performance advantage remains unmeasured
- **Expectation:** A workload-adaptive WE-HDT may improve selected search and update workloads.
- **Gap:** No reproducible measurements yet show superiority over tuned k-d trees, ball trees, R-trees, ANN indexes, or simple scan.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P1. **Owner role:** Benchmark lead.
- **Test:** Compare latency distribution, recall, memory, build time, update cost, energy where available, and total lifecycle cost with equal tuning budgets.
- **Exit:** Publish full workload and confidence intervals, including losses and break-even regions; avoid universal superiority claims.
- **Links:** `CASE-002`, `WE-SIO-003`, `EXT-001`.

### UR-005 — Adaptive partitioning may oscillate
- **Expectation:** Split/merge/reindex decisions converge or remain cost-bounded under realistic workloads.
- **Gap:** Workload drift and noisy signals can cause repeated restructuring.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Adaptive-index lead.
- **Test:** Alternating hot spots, abrupt distribution shifts, and adversarial query schedules; measure churn and regret against fixed partitions.
- **Exit:** Define hysteresis, budgets, rollback, and measurable upper bounds or documented failure conditions.
- **Links:** `WE-SIO-004`, `SPEC-003`.

### UR-006 — Intelligence at metric leaves may cost more than it helps
- **Expectation:** Selective MLIU activation improves task utility relative to its cost.
- **Gap:** Per-leaf reasoning and provenance storage may dominate query costs.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** MLIU evaluation lead.
- **Test:** Compare plain index, index+shared reasoning, and budgeted MLIU on identical tasks and budgets.
- **Exit:** Report utility/cost frontier and explicit cases where MLIU should be disabled.
- **Links:** `WE-SIO-005`, `SPEC-003`, `CASE-005`.

### UR-007 — Cross-perspective inference can be semantically invalid
- **Expectation:** Two-Ways CCC can combine perspectives without illicit unit conversion or relation inversion.
- **Gap:** A relation inferred in one perspective may not transfer to another; correlation can be mistaken for identity or causality.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P0. **Owner role:** CCC interface lead.
- **Test:** Typed composition examples with unit mismatch, missing provenance, nontransitive similarity, and directed-edge reversal.
- **Exit:** Every cross-perspective step is typed, evidence-linked, and rejectable; no silent conversion.
- **Links:** `WE-SIO-006`, `SPEC-004`.

### UR-008 — Residuals may be noise, leakage, or confounding
- **Expectation:** Residual-First Discovery distinguishes informative gaps from artifacts.
- **Gap:** A systematic-looking residual can be generated by measurement bias, selection effects, or multiple testing.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Scientific-validation lead.
- **Test:** Synthetic confounding, negative controls, blinded holdouts, pre-registered hypotheses, and correction for multiple comparisons.
- **Exit:** Promotion gates reject spurious discoveries and retain negative findings.
- **Links:** `WE-SIO-007`, `CASE-003`, `SPEC-005`.

### UR-009 — Metric discovery may merely rename feature engineering
- **Expectation:** Generated perspectives add measurable predictive or explanatory value beyond conventional feature construction.
- **Gap:** Novel terminology alone does not demonstrate methodological novelty.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Metric-discovery lead.
- **Test:** Strong feature engineering and automated feature discovery baselines, held-out transfer, calibration, and complexity penalties.
- **Exit:** Identify specific incremental capability, with falsification cases and ablations.
- **Links:** `WE-SIO-008`, `EXT-003`.

### UR-010 — Autonomous questions may be plentiful but unhelpful
- **Expectation:** AQSI-style reverse questioning improves subsequent validated discovery.
- **Gap:** Question quantity and novelty do not guarantee information gain or experimental feasibility.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Question-evaluation lead.
- **Test:** Compare human-designed, random, heuristic, and autonomous question portfolios at fixed experimental budget.
- **Exit:** Demonstrate improvements in validated yield or information gain, not question count alone.
- **Links:** `WE-SIO-006`, `EXT-003`.

### UR-011 — CDE needs an identifiable contribution beyond state transitions
- **Expectation:** CDE adds useful contracts for constrained delta generation, selection, memory, and structural evolution.
- **Gap:** Without distinctive testable operators, it may reduce to a generic transition-system description.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** CDE formalization lead.
- **Test:** Specify minimal kernel, compare against search/DP/branch-and-bound/MDPs, and isolate added capabilities in executable tasks.
- **Exit:** Publish a non-vacuous kernel and counterexamples where its optional policies do not apply.
- **Links:** `WE-SIO-009`, `CASE-004`, `EXT-001`.

### UR-012 — Cycles and termination are application-dependent
- **Expectation:** CDE supports legitimate repeated states while controlling unproductive loops.
- **Gap:** D-BTP's No-Delta-Reuse policy is not universal; chess and reversible workflows contradict a blanket ban.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P0. **Owner role:** CDE conformance lead.
- **Test:** Chess repetition, transpositions, reversible actions, finite and infinite graphs, bounded and unbounded search.
- **Exit:** Explicit policy for path memory, transposition, budget, and termination; no universal termination promise.
- **Links:** `CASE-004`, `WE-SIO-009`, `DECISION-LOG.md`.

### UR-013 — Undoing knowledge is not undoing the world
- **Expectation:** World, observation, epistemic, and structural deltas retain separate semantics.
- **Gap:** Replaying a corrected record can be mistaken for reversing a real-world event.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Delta semantics lead.
- **Test:** Event sourcing, delayed observation, corrected measurement, irreversible event, and index rollback scenarios.
- **Exit:** Typed delta log and replay tests preserve chronology, provenance, and irreversible-event distinctions.
- **Links:** `WE-SIO-009`, `SPEC-006`.

### UR-014 — SIF localization orchestration lacks a tested contract
- **Expectation:** WE-HDT and CDE are complementary localization/addressing methods.
- **Gap:** Their interface and routing policy are proposals, not validated SIF integration.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** SIF integration lead.
- **Test:** Mixed workloads requiring entity lookup and constrained state-space search; measure routing accuracy and end-to-end overhead.
- **Exit:** Versioned interfaces, fallback behavior, and comparison against monolithic alternatives.
- **Links:** `EXT-001`, `WE-SIO-003`, `WE-SIO-009`.

### UR-015 — Multi-agent consensus can duplicate one source
- **Expectation:** Collective Learning aggregates genuinely informative evidence.
- **Gap:** Correlated agents may repeat the same flawed source and create false confidence.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P0. **Owner role:** Relay governance lead.
- **Test:** Shared-source, independent-source, adversarial, and collusive agent configurations with provenance graphs.
- **Exit:** Evidence dependence is represented and aggregation does not treat copies as independent observations.
- **Links:** `EXT-002`, `SPEC-006`.

### UR-016 — Research relay may fail to reproduce negative results
- **Expectation:** Another team can replay both successes and failures from a relay package.
- **Gap:** Missing seeds, environments, versions, or unsuccessful trials undermine cumulative learning.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Reproducibility steward.
- **Test:** Independent handoff with code/data access restrictions documented and blinded replication instructions.
- **Exit:** Replay manifests include negative results, deviations, artifacts, and unresolved exceptions.
- **Links:** `WE-SIO-012`, `EXT-002`.

### UR-017 — Self-description is not calibrated self-modeling
- **Expectation:** A self-model predicts capabilities, limitations, and uncertainty under interventions.
- **Gap:** Fluent self-description can be inaccurate or ungrounded.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Self-model evaluation lead.
- **Test:** Hidden capability changes, resource limits, distribution shift, and intervention-based prediction scoring against non-self-model baselines.
- **Exit:** Measurable calibration and decision utility; document failures and drift.
- **Links:** `CASE-005`, `WE-SIO-010`, `EXT-004`.

### UR-018 — Self-reference does not establish subjective experience
- **Expectation:** Claims about self-model function are separated from claims about phenomenology.
- **Gap:** Structural and behavioral evidence alone does not settle consciousness or subjective experience.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Epistemic boundary reviewer.
- **Test:** Audit all documents and experiments for unjustified inference from feedback, agency, or self-reference to subjective experience.
- **Exit:** Claims remain appropriately scoped; philosophical uncertainty is documented rather than falsely resolved.
- **Links:** `EXT-004`, `WE-SIO-010`, `CASE-005`.

### UR-019 — Definition evolution may become unfalsifiable
- **Expectation:** Definition Evolution Loop revises contracts while preserving explanatory precision.
- **Gap:** Repeatedly broadening definitions can absorb every counterexample and remove discriminating power.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Definition steward.
- **Test:** Require negative examples, invariants, version diffs, and regression tests for every proposed definition change.
- **Exit:** Revisions improve conformance without vacuous universalization; rejected revisions remain visible.
- **Links:** `WE-SIO-011`, `DEFINITION-REGISTRY.md`, `COUNTEREXAMPLE-REGISTRY.md`.

### UR-020 — Perspective federation creates privacy and authorization risks
- **Expectation:** Cross-perspective joins and relays respect access boundaries and purpose restrictions.
- **Gap:** A permissible local observation can become sensitive when combined with other perspectives.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Security/privacy reviewer.
- **Test:** Unauthorized joins, inference attacks, revoked permissions, tenant boundaries, audit logging, and data minimization.
- **Exit:** Deny-by-default controls, tested policy enforcement, and incident response procedures.
- **Links:** `SPEC-001`, `SPEC-004`, `EXT-002`.

### UR-021 — High-dimensional and non-Euclidean retrieval may defeat WE-HDT
- **Expectation:** WE-HDT degrades gracefully or delegates to a suitable index when its assumptions fail.
- **Gap:** Euclidean locality is unreliable in some high-dimensional and abstract domains.
- **Status / evidence:** OPEN / E0. **Priority:** P1. **Owner role:** Search-benchmark lead.
- **Test:** Dimension sweeps, sparse embeddings, graph relations, asymmetric distances, and adversarial distributions.
- **Exit:** Explicit applicability map and fallback routing; no Euclidean-first universal axiom.
- **Links:** `CASE-002`, `EXT-001`.

### UR-022 — Clinical residuals require more than algorithmic validation
- **Expectation:** Clinical case studies can illustrate residual discovery without implying medical efficacy.
- **Gap:** Confounding, bias, privacy, data governance, and prospective validity remain untested.
- **Status / evidence:** OPEN / E0. **Priority:** P0. **Owner role:** Clinical-domain and ethics reviewers.
- **Test:** Begin with synthetic data; any real-world study requires appropriate approvals, expert oversight, preregistration where applicable, and secure data handling.
- **Exit:** Research claims are limited to demonstrated results; no treatment recommendations or clinical deployment claims.
- **Links:** `CASE-003`, `EXT-003`.

### UR-023 — Cross-registry references may drift
- **Expectation:** Hypotheses, definitions, counterexamples, decisions, and residuals remain navigable and version-consistent.
- **Gap:** Document edits can break IDs, filenames, or implied dependencies.
- **Status / evidence:** TEST-DESIGNED / E0. **Priority:** P1. **Owner role:** Repository release steward.
- **Test:** Automated link and ID checks, duplicate detection, referenced-file existence, version matching, and publication artifact linting.
- **Exit:** Reproducible release audit with zero unexplained broken references; missing source artifacts are reported, not fabricated.
- **Links:** All `research-trace/` files, `CONTENTS.md`, `VALIDATION-ROADMAP.md`.

### UR-024 — Open-ended perspective plugins need compatibility boundaries
- **Expectation:** New perspectives and agents can be installed without silently changing established contracts.
- **Gap:** Schema evolution, stale clients, untrusted plugins, and incompatible versions can corrupt inference.
- **Status / evidence:** OPEN / E0. **Priority:** P2. **Owner role:** Interoperability lead.
- **Test:** Backward/forward compatibility matrices, sandboxed execution, contract negotiation, version pinning, and rollback.
- **Exit:** Explicit extension points and compatibility tests, with fail-safe behavior.
- **Links:** `WE-SIO-012`, `EXT-002`, `SPEC-006`.

## 5. Prioritized research program

### Phase A — Establish semantic and correctness gates (P0)

1. Formalize identity and perspective contracts (`UR-001`, `UR-002`).
2. Establish exhaustive oracle for exact retrieval (`UR-003`).
3. Define cross-perspective proof obligations (`UR-007`).
4. Separate delta types and cycle policies (`UR-011`–`UR-013`).
5. Add evidence dependence and authorization checks (`UR-015`, `UR-020`).

**Gate A:** No claim of general search correctness, scientific discovery, or autonomous evolution without the applicable typed contracts and reproducible conformance tests.

### Phase B — Establish comparative evidence (P1)

1. Benchmark WE-HDT, adaptive blocks, and MLIU against tuned baselines (`UR-004`–`UR-006`, `UR-021`).
2. Evaluate metric generation and question portfolios using holdouts (`UR-008`–`UR-010`).
3. Prototype SIF routing and research relay (`UR-014`, `UR-016`).
4. Test definition revisions and repository integrity (`UR-019`, `UR-023`).

**Gate B:** Report negative results, uncertainty, costs, and workload-specific conditions alongside any improvements.

### Phase C — Study bounded self-model and open extension (P1/P2)

1. Measure self-model calibration and intervention robustness (`UR-017`).
2. Maintain an explicit subjective-experience claim boundary (`UR-018`).
3. Validate plugin and perspective compatibility (`UR-024`).
4. Reassess residual priorities based on evidence, not enthusiasm.

**Gate C:** Demonstrate concrete functional improvements without overstating subjective or scientific conclusions.

## 6. Residual-to-hypothesis conversion protocol

A residual can generate a new hypothesis only when:

1. Its expected behavior and observed discrepancy are separately recorded.
2. Measurement error, implementation bugs, and provenance gaps have been investigated.
3. At least one falsifiable explanation and a competing explanation are stated.
4. The experiment includes negative controls or appropriate counterexamples.
5. A held-out or independent validation route is available, or the limitation is explicitly recorded.
6. The new hypothesis receives an ID in `HYPOTHESIS-REGISTRY.md` and links back to the residual.

A rejected hypothesis does not erase the originating residual; it updates the search space and evidence trail.

## 7. Change and resolution workflow

```text
OPEN residual
  -> triage (type, priority, evidence, owner)
  -> contract or hypothesis proposal
  -> conformance / adversarial test design
  -> execution and provenance capture
  -> independent review where material
  -> RESOLVED | PARTIALLY-RESOLVED | REFUTED | BLOCKED
  -> definition/decision updates + regression tests
  -> collective-learning relay package
```

**Resolution requires:** exact scope, observed evidence, versioned artifacts, test outcomes, negative results, remaining limitations, and reviewer/date. An architectural decision alone cannot resolve an empirical residual.

## 8. Example update record (template, not an executed test)

```yaml
residual_id: UR-003
revision: 1
status: TEST-DESIGNED
claim_scope: exact radius queries under a declared metric
expected: all qualifying entities reach resolution phase
observed: not_yet_measured
evidence_level: E0
experiment_id: proposed-search-oracle-001
baseline: exhaustive_scan
counterexamples: [boundary_ties, stale_index, skew]
result: pending
next_action: implement oracle and randomized tests
reviewer: unassigned
```

## 9. Research governance and publication rules

- Do not describe E0 conceptual work as measured performance, established causality, or verified intelligence.
- Keep source data, algorithm outputs, and interpretations distinct.
- Record failures, null results, and irreducible uncertainty as first-class artifacts.
- Treat security, privacy, and clinical concerns as gates, not optional benchmark dimensions.
- Preserve superseded definitions and rejected hypotheses for historical traceability.
- Do not infer subjective experience from self-referential computation alone.
- Where this registry cites shorthand such as `SPEC-001` or `DEF-001–009`, confirm exact filenames and IDs against the published repository before release.

## 10. Explicit leftovers for the next relay

1. Populate owners and dates once contributors accept responsibility.
2. Add runnable test suites, datasets, seeds, and environment manifests.
3. Link each residual to exact hypothesis and counterexample IDs after cross-registry audit.
4. Distinguish experimentally observed residuals from design-time anticipated gaps in machine-readable metadata.
5. Define quantitative severity thresholds per domain and workload.
6. Build an automated dashboard showing state transitions and evidence levels.
7. Invite independent replication, including null and negative findings.
8. Review the registry at every versioned release and after any major definition change.

## 11. Related WE-SIO artifacts

- `research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md`
- `research-trace/HYPOTHESIS-REGISTRY.md`
- `research-trace/DEFINITION-REGISTRY.md`
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`
- `research-trace/DECISION-LOG.md`
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md`
- `docs/WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md`
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`
- `extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md`
- `VALIDATION-ROADMAP.md`

---

**Closing principle:** A research framework becomes more useful when it can explain what it has *not* yet established, why the gap matters, and exactly how another researcher can challenge or resolve it.
