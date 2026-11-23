# OPEN QUESTIONS

**World Entity and Structural Intelligence Operations (WE-SIO)**  
**Research release:** v0.1.0  
**Status:** Open research agenda; questions and proposed experiments, not established results  
**Research contributors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-23

> Define the invariant, not the inventory. Preserve what remains unknown.

## 1. Purpose and scope

This document collects open questions whose answers could change the architecture, definitions, validation priorities, or claims of WE-SIO. It is intentionally distinct from `FUTURE-DIRECTIONS.md` (proposed workstreams), `TESTABLE-HYPOTHESES.md` (falsifiable predictions), and `research-trace/UNRESOLVED-RESIDUALS.md` (gaps against stated expectations). A question can motivate multiple hypotheses, and a residual can expose a question that has not yet been formulated.

**Current evidence posture:** The framework is a research proposal. Neither empirical superiority over established indexing methods nor automated scientific discovery, subjective experience, or generally beneficial self-improvement has been demonstrated by the repository's conceptual specifications.

## 2. How to read and answer a question

Each question has a stable identifier (`OQ-###`), a domain, a precise uncertainty, a proposed discriminating test, and a condition under which its answer should affect the framework. Priority indicates sequencing, not scientific importance. P0 = semantic/correctness blocker; P1 = empirical feasibility or integration; P2 = exploratory extension.

A useful answer should include: a claim with its scope, a minimal reproducible example, the baseline or counterexample, provenance and versions, negative results, and the proposed decision. Do not mark a question resolved merely because a plausible mechanism has been described.

## 3. World Entity and identity

### OQ-001 — What is the smallest useful World Entity contract? [P0]
Can entity references, identity scope, time, perspective descriptors, and provenance form a minimal kernel without forcing domain-specific ontology into every record? **Test:** Encode database records, events, abstract mathematical objects, and evolving agents using one contract; record exceptions and semantic loss. **Decision trigger:** Repeated domain-specific exceptions require a split between kernel and optional profiles.

### OQ-002 — When do two records refer to one entity? [P0]
How should identity be represented when source identifiers conflict, entities split or merge, and equivalence is uncertain? **Test:** Use synthetic longitudinal entity-resolution cases with ambiguous merges and reversible links. **Decision trigger:** Replace hard identity assertions with evidence-backed, scoped identity hypotheses where necessary.

### OQ-003 — Can entity boundaries be perspective-dependent without making identity arbitrary? [P1]
A vehicle may be a physical object, a fleet member, or a temporary composite service unit. Which boundaries belong to the entity and which to a perspective-specific view? **Test:** Cross-perspective queries with explicit identity and membership policies. **Decision trigger:** Introduce typed composite-entity contracts if boundary changes cannot be expressed as relations.

### OQ-004 — How should time and provenance participate in entity semantics? [P0]
Does an observation at time `t` describe the world, a source's claim, or the system's knowledge at `t`? **Test:** Delayed observations, corrections, and conflicting source updates. **Decision trigger:** Require bitemporal or provenance-aware records when single timestamps misrepresent history.

## 4. Perspectives, metrics, and typed relations

### OQ-005 — What is the minimum safe perspective type system? [P0]
Which types must be distinct: mathematical distance metric, similarity, measurement, asymmetric relation, directional score, and learned embedding? **Test:** Static and runtime conformance cases including non-symmetric distances and missing units. **Decision trigger:** Reject operations whose required properties are not declared and checked.

### OQ-006 — How can heterogeneous perspectives be compared without false equivalence? [P0]
When, if ever, may distance, trust, time, and semantic relevance enter a common score? **Test:** Explicit conversion contracts and sensitivity analyses; include incompatible units and scale shifts. **Decision trigger:** Require calibrated transforms and preserve component-level evidence.

### OQ-007 — What counts as a genuinely new metric or perspective? [P1]
Is a discovered feature merely a reparameterization of known variables, a useful predictor, a measurement, or a mathematical metric? **Test:** Redundancy, invariance, triangle-inequality, and out-of-distribution checks as applicable. **Decision trigger:** Assign typed promotion categories rather than calling every score a metric.

### OQ-008 — How should uncertainty propagate across perspective mappings? [P0]
What happens to confidence when a query crosses uncertain entity links and learned relation mappings? **Test:** Synthetic probabilistic and interval-valued examples with correlated evidence. **Decision trigger:** Introduce explicit dependence-aware uncertainty contracts.

## 5. WE-HDT, variable blocks, and localization

### OQ-009 — What is WE-HDT's formal search guarantee? [P0]
Can the candidate stage guarantee complete recall for an exact query, and under which metric assumptions? **Test:** Construct boundary and adversarial cases; prove safe pruning or label the method approximate. **Decision trigger:** No exactness claim without a correctness argument and conformance suite.

### OQ-010 — Does variable-size partitioning improve performance over established baselines? [P1]
What advantage, if any, remains against balanced and dynamically maintained k-d trees, ball trees, R-trees, approximate nearest-neighbor methods, and brute force? **Test:** Same datasets, query workloads, hardware, recall targets, and tuning budgets. **Decision trigger:** Limit performance claims to observed regimes and report failures.

### OQ-011 — When does Euclidean-first localization fail? [P0]
How should abstract or non-geometric entities be addressed without fabricated coordinates? **Test:** Relational-only, symbolic, and asymmetric-query workloads. **Decision trigger:** Keep Euclidean-first an optional strategy, never a universal prerequisite.

### OQ-012 — How should PAVB adapt without oscillation? [P1]
What split/merge/reindex policy balances latency, memory, maintenance cost, and workload drift? **Test:** Abruptly changing and cyclic query distributions; measure amortized costs and hysteresis. **Decision trigger:** Add stability budgets or rollback rules if adaptation costs dominate.

### OQ-013 — What is the relationship between index topology and intelligence topology? [P0]
Must an MLIU be attached to a physical leaf, a logical metric node, or an external service? **Test:** Move intelligence units across rebalanced indexes while preserving semantics. **Decision trigger:** Formalize logical addressing independent of physical layout.

## 6. MLIU, operations, and Two-Ways CCC

### OQ-014 — What is the minimum viable Metric Leaf Intelligence Unit? [P1]
Which of Locate, Resolve, Relate, Infer, Question, and Evolve can be lightweight operations rather than persistent agents? **Test:** Compare stateless services, cached operators, and agentic nodes under equal budgets. **Decision trigger:** Prefer simpler units when richer ones offer no validated benefit.

### OQ-015 — What makes reverse CCC more than ordinary error analysis? [P1]
Can residual-guided questioning produce better testable hypotheses than standard diagnostics and active learning? **Test:** Matched-budget comparisons on seeded hidden-factor tasks. **Decision trigger:** Narrow the novelty claim if equivalent baselines perform as well.

### OQ-016 — How can forward and reverse passes avoid circular evidence? [P0]
Can a model generate a hypothesis and then validate it using the same contaminated data? **Test:** Holdout discipline, independent evidence sources, and adversarial leakage cases. **Decision trigger:** Require evidence partition and validation provenance.

### OQ-017 — When should an unresolved query become an autonomous question? [P1]
What utility criterion distinguishes productive questions from unlimited question proliferation? **Test:** Compare information gain, downstream task benefit, cost, and false discovery rate. **Decision trigger:** Add question-budget and prioritization contracts.

## 7. Residual-first scientific discovery

### OQ-018 — Which residuals deserve preservation? [P0]
How can the system distinguish informative anomalies from instrumentation errors, noise, and known model mismatch? **Test:** Seeded data corruption and hidden-mechanism benchmarks. **Decision trigger:** Require residual typing and quality gates before hypothesis generation.

### OQ-019 — How do we prevent residual-driven overfitting? [P0]
Does repeated searching across perspectives inflate false discoveries? **Test:** Nested validation, preregistered synthetic truths, multiple-testing controls, and independent replication. **Decision trigger:** Introduce explicit discovery and confirmation stages.

### OQ-020 — Can a system propose causal mechanisms rather than correlations? [P1]
Which interventions or identification assumptions are necessary? **Test:** Confounded observational examples and randomized synthetic interventions. **Decision trigger:** Label non-interventional outputs as hypotheses, not causal findings.

### OQ-021 — What is the promotion threshold for a new perspective? [P1]
Which semantic, formal, predictive, robustness, and governance gates are necessary and sufficient? **Test:** Candidate registry with acceptance/rejection outcomes under dataset shift. **Decision trigger:** Version promotion rules and permit rollback.

### OQ-022 — How should failed discoveries become reusable knowledge? [P1]
Can a negative result constrain future search without forbidding valid discoveries in changed contexts? **Test:** Replay rejected hypotheses with altered assumptions and versioned evidence. **Decision trigger:** Store scoped rejection rationales, not universal prohibitions.

## 8. Delta, CDE, and structural evolution

### OQ-023 — What distinguishes CDE from a generic transition system? [P0]
Which additional contracts—candidate generation, constrained evaluation, path memory, residual feedback, or structural policy evolution—are essential rather than optional packaging? **Test:** Formal reduction and ablation against search, dynamic programming, and branch-and-bound. **Decision trigger:** Revise the minimal kernel if its distinctive content cannot be specified.

### OQ-024 — How should different Delta types interact? [P0]
How are World, Observation, Epistemic, and Structural Deltas composed, ordered, and rolled back? **Test:** Delayed correction and index rebuild examples where the world does not reverse. **Decision trigger:** Separate event semantics from belief and infrastructure updates.

### OQ-025 — Which cycle and path-memory policies are domain-specific? [P0]
Chess permits legal repeated moves and states; D-BTP may prohibit repeated Delta usage along a path. **Test:** Chess repetition, reversible moves, and constrained permutation examples. **Decision trigger:** Keep No-Delta-Reuse a configurable policy, not a CDE axiom.

### OQ-026 — Can adaptive M-to-N branching be controlled under fixed budgets? [P1]
How should a generator allocate branch count among promising, uncertain, and adversarial directions? **Test:** Equal-budget search benchmarks with solution-quality and coverage metrics. **Decision trigger:** Add resource and termination contracts if branching is unstable.

### OQ-027 — How can CDE and WE-HDT interoperate without conflating their purposes? [P1]
WE-HDT locates entities and perspectives; CDE explores feasible state transitions. **Test:** A scheduling workflow with typed candidate and state-transition interfaces. **Decision trigger:** Define separate localization and evolution guarantees in SIF.

## 9. Multi-agent relay and collective learning

### OQ-028 — What constitutes a real collective-learning gain? [P1]
Is the benefit greater than the sum of extra computation and repeated evaluations? **Test:** Single-agent and multi-agent matched-budget baselines; measure transfer and persistent improvement. **Decision trigger:** Claim collective learning only with reproducible gains.

### OQ-029 — How should correlated agent evidence be handled? [P0]
Agents sharing training data or prompts may agree without independent support. **Test:** Controlled correlation and common-mode error scenarios. **Decision trigger:** Track evidence lineage and independence rather than vote counts alone.

### OQ-030 — When is competitive or adversarial relay useful? [P1]
Does critique improve hypothesis quality or simply increase cost and convergence to shared biases? **Test:** Compare cooperative, competitive, and adversarial portfolios. **Decision trigger:** Route tasks based on demonstrated marginal benefit.

### OQ-031 — How can relay preserve rejected paths and explicit leftovers? [P1]
What minimal artifact permits a different researcher to continue a failed attempt? **Test:** Independent handoff using only recorded inputs, contracts, results, and uncertainty. **Decision trigger:** Make missing provenance a conformance failure.

## 10. Self-modeling and subjective structural intelligence

### OQ-032 — What makes a self-model operationally meaningful? [P0]
Can the system forecast its own capabilities, limitations, and resource use more accurately than a static profile? **Test:** Calibration and intervention benchmarks across changing tasks. **Decision trigger:** Require measurable self-prediction, not self-description alone.

### OQ-033 — How do self-models avoid self-confirming feedback? [P0]
Can a model revise itself based on independent outcomes rather than its own narrative? **Test:** External evaluations, blinded outcome checks, and deliberate self-report contradictions. **Decision trigger:** Separate first-person reports from verified operational evidence.

### OQ-034 — Where is the boundary between an entity model and a subject? [P2]
Which features of self-reference, valuation, continuity, and autonomy are computationally testable, and which remain philosophical? **Test:** Explicitly scoped operational criteria; do not infer experience from behavior alone. **Decision trigger:** Keep subjective-experience claims separate from engineering conformance.

### OQ-035 — Can self-modeling improve constrained self-modification safely? [P1]
Can proposed policy changes be evaluated and reverted under resource and authorization constraints? **Test:** Sandboxed modifications with external rollback and independent evaluation. **Decision trigger:** Reject uncontrolled self-update as a default design.

## 11. Definition evolution and governance

### OQ-036 — When should a definition be revised, split, or rejected? [P0]
How can counterexamples guide revisions without creating ad hoc exceptions? **Test:** Run a regression suite on each proposed definition change. **Decision trigger:** Require explicit invariant preservation or versioned breaking changes.

### OQ-037 — Can an open semantic kernel remain precise? [P0]
Does extensibility inevitably produce ambiguous, vacuous concepts? **Test:** Independent implementers classify borderline examples from written contracts. **Decision trigger:** Add typed extensions where disagreement persists.

### OQ-038 — What must be proven before calling a component an SIF pillar? [P1]
Which correctness, interoperability, and empirical criteria justify elevating WE-HDT or CDE from candidate methods to validated infrastructure? **Test:** Cross-domain integration, baseline comparisons, and independent conformance. **Decision trigger:** Maintain 'candidate pillar' status until evidence is sufficient.

### OQ-039 — How should sensitive domains constrain experimentation? [P0]
What privacy, access, consent, bias, and safety controls are required for clinical or identity-resolution examples? **Test:** Synthetic data first, governance review for real data, and audit of prohibited inferences. **Decision trigger:** Block deployment claims without domain-specific safeguards.

### OQ-040 — How can research claims survive independent reproduction? [P1]
What constitutes a complete reproducibility package for a framework with changing definitions and metrics? **Test:** Independent implementation from versioned specifications and frozen datasets. **Decision trigger:** Preserve immutable experiment manifests, failures, and evaluation scripts.

## 12. Cross-question dependencies

| Dependency | Why it matters |
|---|---|
| OQ-001, 002, 004 → OQ-009, 013 | Localization correctness requires stable entity and temporal semantics. |
| OQ-005, 006, 008 → OQ-015, 016 | Cross-perspective inference requires type and uncertainty discipline. |
| OQ-018, 019 → OQ-020, 021 | Discovery claims require error control before promotion. |
| OQ-023, 024, 025 → OQ-027 | SIF integration depends on a defensible CDE kernel and Delta semantics. |
| OQ-029 → OQ-028, 030 | Correlated evidence can invalidate apparent multi-agent benefits. |
| OQ-032, 033 → OQ-035 | Self-modification should not rely on uncalibrated self-models. |
| OQ-036, 037 → OQ-038 | Architectural promotion requires precise, stable contracts. |

## 13. Suggested first experiments

1. **Identity and temporal conformance:** Synthetic record merge/split, correction, and delayed-observation tests (OQ-001–004).
2. **Perspective type checker:** Reject invalid metric assumptions, dimensional mismatches, and unsupported cross-perspective compositions (OQ-005–008).
3. **Exact search proof and benchmark:** Verify candidate recall and compare VSB/WE-HDT with tuned k-d tree and brute force under matched budgets (OQ-009–012).
4. **Residual discovery benchmark:** Seed hidden factors and noise; measure independent validation yield and false discoveries (OQ-015–022).
5. **CDE boundary suite:** Chess cycles, reversible state transitions, and D-BTP path constraints (OQ-023–027).
6. **Collective relay audit:** Compare single versus multi-agent workflows with controlled evidence correlation (OQ-028–031).
7. **Self-model calibration:** Compare static capability metadata with dynamically revised, externally evaluated self-models (OQ-032–035).

## 14. Question status and evidence rules

All OQ entries in this release are **Open / E0 (conceptual)** unless accompanied by a separate versioned experiment report. An implemented test is not itself positive evidence; its result, baseline, uncertainty, and limitations must be recorded. Recommended lifecycle:

`Open → Operationalized → Testing → Supported Answer / Refuted Answer / Split / Superseded → Archived with provenance`

Do not delete superseded questions. Link them to the successor definition, hypothesis, counterexample, and decision record.

## 15. Research relay submission template

```yaml
question_id: OQ-000
claim_or_answer: ""
claim_scope: ""
related_hypotheses: []
related_definitions: []
related_counterexamples: []
related_residuals: []
method: ""
baseline: ""
dataset_and_license: ""
code_commit: ""
metric_and_uncertainty: ""
positive_findings: []
negative_findings: []
limitations: []
reproduction_steps: []
proposed_decision: ""
review_status: proposed
```

## 15A. New open questions: Mask-First, epistemic separation, SQL-native SI, and five-way Delta (2026-11-05 update)

The following questions **extend OQ-001–040 without renumbering them**. They reflect candidate research directions in `EXT-005`, `EXT-006`, updated `WE-SIO-004/005/007/008/009`, and updated `SPEC-003/005`. All remain **open**; the tests below are proposals, not completed experiments. An *unknown* is not automatically a *residual*: a residual requires an explicit baseline, observation, comparator, and evidence lineage.

### 15A.1 Mask-First computation and mature-structure preservation

### OQ-041 — When does Mask-First actually outperform rebuilding or full-view computation? [P1]
How do mask construction, selection, invalidation, cache maintenance, and fallback costs compare with full-view execution, fixed masks, local adaptation, and eager structural rebuild? **Test:** Match hardware, workloads, retrieval guarantees, tuning budgets, and end-to-end cost; include frequent context shifts. **Decision trigger:** Restrict Mask-First to regimes with reproducible net benefit and no unreported correctness loss. **Hypothesis link:** WEH-031.

### OQ-042 — Can a dynamic mask preserve exact candidate coverage? [P0]
Which node, metric, edge, and operation masks admit formal safe-pruning proofs or conservative candidate supersets? **Test:** Adversarial boundary fixtures and differential comparison against exhaustive full-view queries; measure false omissions. **Decision trigger:** Require a full-view fallback or explicit approximate-mode declaration when completeness cannot be certified. **Contracts:** SPEC-003 MIC, WE-SIO-004.

### OQ-043 — How should stale masks be invalidated across changing versions? [P0]
Which schema, evidence, perspective, permission, and topology changes invalidate cached Active Computational Views? **Test:** Interleave reads with schema migration, revocation, reindexing, and late observations under snapshot/version checks. **Decision trigger:** Specify mandatory invalidation triggers and fail-closed semantics.

### OQ-044 — What makes a mature structure worth preserving? [P1]
Can reuse prevent unnecessary reconstruction without entrenching outdated partitions or obsolete knowledge? **Test:** Compare retained mature pathways with adaptive rebuild under drift, fragmentation, and corrupted-index cases. **Decision trigger:** Define quantitative preserve-versus-rebuild thresholds and exceptions. **Hypothesis link:** WEH-032.

### OQ-045 — Can Mask Policy Relay generalize without transferring unsafe assumptions? [P1]
Which mask policies transfer across tasks, domains, and schemas, and what must be revalidated at the destination? **Test:** Cross-workload transfer with schema mismatches, adversarial changes, and provenance-aware baselines. **Decision trigger:** Require policy compatibility descriptors and destination-specific conformance checks. **Hypotheses:** WEH-034, WEH-039.

### 15A.2 Epistemic separation and qualified residual evidence

### OQ-046 — What is the minimum interoperable separation of Established, Open, and Residual states? [P0]
Can a single logical interface support scope-relative Established Knowledge, Open Knowledge, and qualified RER evidence without collapsing unknowns into mismatches? **Test:** Classify mixed numeric, relational, missing, and contested records across independent evaluators. **Decision trigger:** Refine state transitions or introduce subtypes when systematic disagreement remains. **Hypothesis:** WEH-033.

### OQ-047 — What qualifies a nonnumeric discrepancy for the Residual Evidence Registry? [P0]
Can logical contradictions, temporal inconsistencies, and relational violations share a minimal residual admission contract without a meaningless generic “difference” field? **Test:** Explicit baseline/comparator fixtures, including absent baselines, SQL NULL, incompatible perspectives, and contradictory constraints. **Decision trigger:** Split comparator profiles if a common admission contract obscures essential semantics. **Contracts:** SPEC-005 RQC.

### OQ-048 — How do we distinguish real residuals from data and model artifacts? [P0]
What checks reliably detect duplicate JOIN rows, measurement error, selection bias, miscalibration, leakage, and distribution shift before scientific interpretation? **Test:** Inject known artifacts and compare RER triage against anomaly logging and manual review. **Decision trigger:** Tighten admission or introduce a provisional-only queue when false qualification is high. **Hypothesis:** WEH-038.

### OQ-049 — When is a knowledge claim established, and who may withdraw it? [P0]
What evidence, scope, independence, negative controls, and review authority are necessary for `Open → Established`, and how should later contradictory evidence propagate? **Test:** Blinded promotion/demotion fixtures with dependency graphs and post-promotion counterexamples. **Decision trigger:** Revise governance gates if unsupported promotions or silent downstream inconsistencies occur. **Hypotheses:** WEH-033, WEH-040.

### OQ-050 — Can masks create systematic epistemic blind spots? [P0]
Could selection of seemingly relevant metrics conceal contradictory evidence, amplify confirmation bias, or falsely raise discovery confidence? **Test:** Compare masked and unmasked investigations with deliberately hidden counterexamples, matched budgets, and blinded reviewers. **Decision trigger:** Mandate contradiction sweeps, conservative expansion, or full-view review before promotion.

### 15A.3 SQL-native Structural Intelligence

### OQ-051 — What is the safe mapping between SQL constructs and World Entity semantics? [P0]
When is a table a relation rather than an entity collection, a row an event rather than an entity, or a column an attribute rather than a metric? **Test:** Map normalized, denormalized, event-sourced, many-to-many, and temporal schemas with identity/provenance fixtures. **Decision trigger:** Add explicit mapping profiles and prohibit unsupported identity inference. **Hypothesis:** WEH-035.

### OQ-052 — Can SQL Mask-First localization improve total cost without bypassing SQL security? [P0]
How do table/column/relation masks interact with row-level security, column permissions, query planning, and transaction snapshots? **Test:** Differential authorized-query comparisons, privilege revocations, joins, and schema changes. **Decision trigger:** Reject mask optimizations that leak data, change promised result semantics, or silently omit valid candidates. **Hypothesis:** WEH-036.

### OQ-053 — How should SQL missingness and source-state updates affect knowledge status? [P0]
How can `NULL`, absent rows, late transactions, `UPDATE`, and contradictory joins be interpreted without assuming unknown means residual or database change means world change? **Test:** Typed missingness and bitemporal fixtures with independent world-event evidence. **Decision trigger:** Require explicit source-state and epistemic transition contracts. **Hypothesis:** WEH-037.

### OQ-054 — What constitutes successful cross-schema SI transfer? [P1]
Which parts of a perspective descriptor, mask policy, or residual diagnostic survive schema renaming, normalization changes, and different access policies? **Test:** Cross-database transfer with held-out schemas, matching semantics, and cost accounting. **Decision trigger:** Define compatibility, adaptation, and rejection conditions. **Hypothesis:** WEH-039.

### 15A.4 Five-way Delta and CDE integration

### OQ-055 — Is five-way Delta typing necessary and sufficient? [P0]
Does separating `ΔA` (Activation/Mask) from `ΔS` (persistent structure) prevent real errors, and what mixed events remain ambiguous among `ΔW`, `ΔO`, `ΔK`, `ΔS`, and `ΔA`? **Test:** Independently label composite events and compare error rates with the original four-way taxonomy. **Decision trigger:** Revise types or allow explicitly composite events when a forced single label is misleading. **Reference:** WE-SIO-009.

### OQ-056 — What are safe CDE rollback semantics for each Delta type? [P0]
When can an activation, epistemic, structural, observation, or external-world change be reversed, compensated, or only historically annotated? **Test:** Inject failed transitions, stale snapshots, irreversible world actions, and dependent downstream decisions. **Decision trigger:** Require typed reversibility, compensation, and audit contracts; never imply that epistemic rollback undoes external events.

### OQ-057 — How should CDE choose Mask, local update, reindex, or no-op? [P1]
Can a budgeted transition controller compare candidate `ΔA`, `ΔK`, and `ΔS` paths under uncertainty without destabilizing mature structures? **Test:** Controlled workloads with drift and competing objectives; compare fixed policy, greedy, and adaptive decision rules. **Decision trigger:** Narrow the controller's claimed domain if decision overhead, instability, or missed candidates dominate.

### OQ-058 — Which parts of WE-HDT and CDE qualify as complementary SIF Localization pillars? [P1]
What independent addressing/localization capabilities does each contribute, and which are already covered by established search, planning, or index techniques? **Test:** Contract-level decomposition, counterexamples, and comparable benchmark tasks. **Decision trigger:** Narrow or revise the proposed pillar positioning when boundaries or gains cannot be demonstrated.

### 15A.5 Evidence, dependencies, and research relay

- **P0 semantic gates:** OQ-042–043, OQ-046–053, OQ-055–056 should be addressed at the contract/fixture level before performance or scientific discovery claims.
- **P1 comparative experiments:** OQ-041, OQ-044–045, OQ-054, OQ-057–058 require matched baselines, costs, negative results, and documented uncertainty.
- **Cross-question dependency:** OQ-047 and OQ-048 constrain OQ-049; OQ-042 and OQ-043 constrain OQ-041; OQ-051–053 constrain OQ-054; OQ-055–056 constrain OQ-057.
- **Registry linkage:** Record formal answers and rejected definitions in `research-trace/DEFINITION-REGISTRY.md`, falsifiable predictions in `research-trace/HYPOTHESIS-REGISTRY.md`, adversarial failures in `research-trace/COUNTEREXAMPLE-REGISTRY.md`, and **only qualified observation–baseline discrepancies** in `research-trace/UNRESOLVED-RESIDUALS.md`. Unanswered questions alone belong here, not automatically in RER.
- **Primary sources:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`, `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`, `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`, and `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`.

## 16. Related repository assets

- `README.md` — research framing and repository overview.
- `START-HERE.md` — newcomer pathways.
- `FUTURE-DIRECTIONS.md` — proposed workstreams and milestones.
- `TESTABLE-HYPOTHESES.md` — falsifiable research predictions.
- `VALIDATION-ROADMAP.md` — evidence-building sequence.
- `research-trace/HYPOTHESIS-REGISTRY.md` — hypothesis tracking.
- `research-trace/DEFINITION-REGISTRY.md` — formal concept boundaries.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md` — adversarial and boundary cases.
- `research-trace/DECISION-LOG.md` — architecture choices and revision triggers.
- `research-trace/UNRESOLVED-RESIDUALS.md` — gaps against explicit expectations.
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md` — residual discovery theory.
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md` — Delta taxonomy.
- `cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md` — indexing baselines.
- `cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md` — CDE boundary test.
- `extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md` — SIF integration proposal.
- `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md` — Mask-First and epistemic separation proposal.
- `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md` — SQL-native integration proposal.
- `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md` — Mask-safe structural contracts.
- `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md` — Residual qualification and knowledge promotion.

## 17. Explicit leftovers for v0.1.0

- No generally accepted formal WE-SIO semantics or independently reviewed proof of WE-HDT completeness is supplied here.
- No published benchmark establishes superiority over mature indexing systems.
- No validated automatic discovery of scientific laws is claimed.
- No empirical result demonstrates that multi-agent relay improves learning under equal budgets.
- No operational self-model establishes subjective experience.
- No deployment-ready clinical, identity-resolution, or autonomous self-modification system is provided.
- Cross-repository terminology and reference identifiers should be audited before DOI release.

**Closing principle:** An unanswered question is a research asset only when its assumptions, tests, possible refutations, and provenance remain visible.

---

*WE-SIO v0.1.0 — Open Research Questions. Licensed under the repository's Apache-2.0 license where applicable.*
