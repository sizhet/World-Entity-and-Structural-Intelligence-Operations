# Future Directions

**World Entity and Structural Intelligence Operations (WE-SIO)**  
**Research roadmap for v0.1.0 and beyond**  
**Status:** Proposed research directions; not validated system capabilities  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

> Define the invariant, not the inventory. Preserve the evidence, not just the conclusion.

## 1. Purpose and research posture

WE-SIO began with variable-size block indexing and two-phase candidate search. Its larger proposal is to connect entity identity, perspective-aware localization, evidence-based resolution, residual-driven questions, constrained structural evolution, and collective learning. The framework is intentionally open-ended, but openness is not a license to make untestable claims.

This document identifies research directions, the contracts each direction must respect, experimental milestones, credible baselines, failure criteria, and reusable research outputs. A direction is a *hypothesis about useful research*, not a statement that an implementation or result already exists.

The central research question is:

**Can a typed, evidence-preserving structural system improve the accuracy, adaptability, auditability, or discovery yield of entity-centered intelligence under realistic resource constraints?**

A second, independent question is whether the proposed architecture provides benefits beyond established indexing, database, knowledge-graph, probabilistic inference, workflow orchestration, and search methods. The answer may differ by workload.

## 2. Non-negotiable research invariants

1. **Identity is not similarity.** An entity identifier, record identifier, and perspective-specific signature have distinct semantics.
2. **Perspective is typed.** A mathematical metric, similarity, directional relation, measurement, and arbitrary attribute are not interchangeable.
3. **Candidate completeness is explicit.** An exact retrieval pipeline must not silently discard valid answers during candidate generation.
4. **Evidence has provenance.** Observations, hypotheses, model outputs, and independently validated findings remain distinguishable.
5. **Residuals are not automatically discoveries.** Data defects, leakage, confounding, misspecification, and noise must be examined first.
6. **Delta kinds are separated.** Changes in the world, observations, beliefs, indexes, and operating policies are different events.
7. **Conformance precedes performance claims.** A fast incorrect result is not a successful optimization.
8. **Definitions remain falsifiable.** Counterexamples can narrow, split, supersede, or retire a proposed definition.
9. **Self-modeling is not proof of experience.** Functional self-reference must not be equated with consciousness.
10. **Collective learning requires evidence discipline.** Agent agreement and repeated outputs are not automatically independent corroboration.

These invariants should appear in executable conformance suites, not only prose.

## 3. Direction A — A minimal executable World Entity kernel

### 3.1 Research question

What is the smallest interoperable contract that can represent a world entity without conflating its identity, representations, observations, and perspective-specific indexes?

### 3.2 Proposed components

- `EntityRef`: scoped identity and explicit identity-resolution status.
- `RepresentationRef`: source-specific descriptions or encodings.
- `PerspectiveDescriptor`: kind, domain, units, applicability, semantics, uncertainty, time, and version.
- `ObservationRecord`: evidence reference, provenance, validity interval, and collection conditions.
- `ResolutionClaim`: candidate identity or relationship with confidence and counterevidence.
- `ResidualRecord`: expected versus observed behavior, with unresolved explanation status.

### 3.3 Experiments and exit criteria

Start with a small synthetic collection containing duplicate records, conflicting source IDs, missing values, changing measurements, and asymmetric relationships. Test round-trip serialization, version migration, ambiguity preservation, and invalid cross-type operations.

**Exit criterion:** every supported operation passes contract tests; ambiguous identity remains ambiguous instead of being silently merged. Publish the schema, fixtures, and failure cases.

**Related:** `SPEC-001`, `CASE-001`, `DEFINITION-REGISTRY.md`.

## 4. Direction B — WE-HDT localization against established baselines

### 4.1 Research question

When, if ever, does WE-HDT provide a measurable advantage over well-engineered alternatives?

WE-HDT proposes a hybrid of candidate localization and perspective-aware evidence resolution. Its novelty and performance cannot be established merely by naming the architecture. A k-d tree already supports nonuniform partitions, and mature indexes offer many forms of adaptive search.

### 4.2 Required baselines

Compare against exhaustive scan, k-d tree, R-tree or suitable spatial index, approximate nearest-neighbor methods where approximation is allowed, database secondary indexes, and a graph-oriented retrieval baseline for relational workloads. Match implementation quality and resource budgets.

### 4.3 Workloads

- Low-dimensional, high-dimensional, clustered, uniform, and adversarially skewed data.
- Static collections versus sustained insert/update/delete streams.
- Exact range, nearest-neighbor, hybrid predicate, and cross-perspective queries.
- Sparse, absent, or misleading Euclidean coordinates.
- Time-dependent evidence and version-sensitive queries.

### 4.4 Measures and failure criteria

Measure recall/completeness, precision, p50/p95/p99 latency, build time, update cost, memory, energy or CPU time, index maintenance, and provenance reconstruction. Distinguish exact from approximate guarantees.

**Failure criterion:** if WE-HDT adds complexity without improving a specified workload or auditability objective, retain the simpler baseline and record the result.

**Related:** `WE-SIO-003`, `CASE-002`, `SPEC-002`, `SPEC-003`, `EXT-001`.

## 5. Direction C — Perspective-adaptive variable blocks and intelligence allocation

### 5.1 Research question

Can partition size and local intelligence capacity be adapted independently, and does their coordinated adaptation outperform simpler policies?

PAVB concerns representation and indexing granularity. AVIB concerns which capabilities and resource budgets are attached to a block or unit. These are different control variables, even when they co-evolve.

### 5.2 Candidate policies

Evaluate fixed-size blocks, density-based splitting, workload-sensitive splitting, budget-constrained capability activation, and a joint policy with explicit switching costs. Include hysteresis to prevent repeated split/merge oscillation.

### 5.3 Key ablations

1. Fixed blocks + fixed intelligence.
2. Adaptive blocks + fixed intelligence.
3. Fixed blocks + adaptive intelligence.
4. Adaptive blocks + adaptive intelligence.
5. Same four conditions without reverse residual feedback.

**Exit criterion:** statistically credible improvement in a declared objective after accounting for adaptation overhead and regression risk. If the joint policy fails, preserve the independent axes rather than forcing a universal coupling.

**Related:** `WE-SIO-004`, `WE-SIO-005`, `SPEC-003`.

## 6. Direction D — Lightweight Metric Leaf Intelligence Units

### 6.1 Research question

Can MLIUs support useful local reasoning without becoming an impractically expensive agent per leaf?

The proposed operations are **Locate, Resolve, Relate, Infer, Question, and Evolve**. A leaf is a logical capability boundary, not necessarily a physical tree leaf or a continuously running model.

### 6.2 Design alternatives

- Declarative rule and scoring unit.
- Shared inference service invoked on demand.
- Cached local statistics with provenance.
- Event-triggered question generator.
- Delegated specialized agent for high-value residuals only.

Measure resource consumption per query and per retained residual. Compare with a centralized service of equivalent capability.

**Failure criterion:** a per-leaf design that increases cost or inconsistency without meaningful improvement should be replaced with shared or event-triggered execution.

## 7. Direction E — Two-Ways CCC as an accountable discovery loop

### 7.1 Research question

Does reverse residual-driven questioning improve discovery yield beyond forward retrieval and ordinary active learning?

**Forward:** locate candidates, evaluate typed constraints, resolve evidence, and report uncertainty.  
**Reverse:** inspect unexplained residuals, propose missing conditions or perspectives, and formulate testable questions.

### 7.2 Safeguards

- Enforce typed cross-perspective mappings.
- Separate candidate generation from independent validation.
- Preserve negative and inconclusive results.
- Prevent answers generated from a hypothesis from serving as its independent evidence.
- Track the incremental cost of each question and experiment.

### 7.3 Validation

Compare a forward-only baseline, a conventional active-learning baseline, and a Two-Ways CCC variant on synthetic ground-truth tasks. Measure validated discoveries per resource unit, false-discovery rate, and time to correct rejection of spurious hypotheses.

**Related:** `WE-SIO-006`, `SPEC-004`, `EXT-003`.

## 8. Direction F — Residual-first scientific discovery

### 8.1 Research question

Can a versioned residual registry produce more reproducible and informative research programs than ad hoc anomaly triage?

Residuals should include model version, expectation, observation, uncertainty, data lineage, context, known alternative explanations, and unresolved status. They should not be promoted directly into laws, mechanisms, or new dimensions.

### 8.2 Discovery pipeline

1. Detect a reproducible mismatch.
2. Audit measurement quality and data processing.
3. Test confounding, leakage, and distribution shift.
4. Generate competing explanations.
5. Define discriminating experiments and holdouts.
6. Validate or reject each explanation independently.
7. Promote, quarantine, or retire candidate perspectives.
8. Relay both successful and failed investigations.

### 8.3 Demonstration domains

Begin with synthetic systems where the hidden mechanism is known. Follow with observational datasets only under suitable domain governance. Clinical examples remain methodological illustrations and must not be used for patient-level treatment recommendations.

**Exit criterion:** demonstrate lower false-discovery rates or improved recovery of hidden structure against a prespecified baseline, with full experimental provenance.

**Related:** `WE-SIO-007`, `CASE-003`, `SPEC-005`.

## 9. Direction G — Metric and perspective generation with formal gates

### 9.1 Research question

Can WE-SIO discover useful new perspectives without mislabeling arbitrary numerical functions as mathematical metrics?

A metric candidate must be checked for nonnegativity, identity of indiscernibles, symmetry, and triangle inequality on its declared domain. Similarities, directed relations, measurements, and learned scores use different contracts.

### 9.2 Validation gates

- **Semantic:** What is being measured, for whom, and in which domain?
- **Formal:** Which algebraic properties are claimed and tested?
- **Measurement:** Are units, calibration, uncertainty, and sampling explicit?
- **Predictive:** Does the perspective improve held-out performance?
- **Robustness:** Does it survive shifts, perturbations, and negative controls?
- **Incremental:** Does it add value beyond existing perspectives?
- **Governance:** Can the perspective be versioned, challenged, and rolled back?

**Failure criterion:** candidates failing formal or evidence gates must not be advertised as validated metrics, even if their scores look promising.

**Related:** `WE-SIO-008`, `EXT-003`, `SPEC-002`, `SPEC-005`.

## 10. Direction H — CDE and explicit delta semantics

### 10.1 Research question

What minimal kernel makes Constrained Delta Evolution useful beyond an ordinary labeled state-transition system?

A candidate kernel includes a state container, typed delta, applicability predicate, transition semantics, constraint evaluation, history or provenance policy, and bounded evolution controller. Additional mechanisms must be justified by observable value.

### 10.2 Separate delta categories

| Delta | Meaning | Example |
|---|---|---|
| World | Change in the modeled external world | A vehicle physically changes location |
| Observation | Change in the recorded evidence | A sensor reading is corrected |
| Epistemic | Change in an agent's belief or model | An identity hypothesis is downgraded |
| Structural | Change in representation or index | A block is split |
| Operational | Change in a control policy or deployment | A query strategy is switched |

Undoing an observation record does not undo the world. Rollback capabilities depend on delta type and domain.

### 10.3 Boundary tests

Chess provides legal repeated states and reversible moves; therefore **No-Delta-Reuse** is not a universal CDE axiom. Test transpositions, castling rights, en passant, draw rules, and path-dependent constraints. Evaluate loop prevention as a configurable policy with explicit consequences for completeness.

**Exit criterion:** show a useful property or improvement not already supplied by a simpler state-transition or search baseline; otherwise narrow the CDE claim.

**Related:** `WE-SIO-009`, `CASE-004`, `EXT-001`.

## 11. Direction I — SIF localization and addressing federation

### 11.1 Research question

Can WE-HDT and CDE serve as complementary SIF Localization / Addressing mechanisms under one typed control interface?

WE-HDT primarily locates and resolves entity- and perspective-centered candidates. CDE primarily generates and evaluates constrained state transitions and paths. Both may expose localization services, but their semantics and guarantees differ.

### 11.2 Proposed federation contract

Requests declare target kind, perspective, constraints, required completeness, evidence policy, budget, and authorization. Responses include candidates or trajectories, guarantee type, provenance, uncertainty, resource use, and unresolved residuals.

Compare the federation against independently invoked tools and a conventional orchestrator. Test whether shared routing improves quality or merely adds indirection.

**Related:** `EXT-001`, `WE-SIO-003`, `WE-SIO-009`.

## 12. Direction J — Multi-agent relay and collective learning

### 12.1 Research question

When does a multi-agent WE-SI system produce verified improvements rather than duplicated work, correlated errors, or inflated consensus?

Study sequential relay, parallel specialization, competitive proposals, adversarial critique, independent validation, and repeated execution as evidence accumulation. Repetition is valuable only when it changes information, calibration, or a reproducible capability estimate.

### 12.2 Controls

- Track common sources and model ancestry.
- Distinguish independent evidence from repeated summaries.
- Use blinded validation where feasible.
- Preserve dissenting and rejected hypotheses.
- Limit agent cost and prevent feedback loops that reward agreement alone.
- Record versioned inputs, tools, outputs, and decisions.

### 12.3 Experiments

Compare a single strong agent, multiple identical agents, specialized agents, and specialized agents with independent verification under matched budgets. Measure task quality, calibration, verified novel findings, error propagation, and marginal return per agent.

**Related:** `EXT-002`, `WE-SIO-012`, `HYPOTHESIS-REGISTRY.md`.

## 13. Direction K — Self-modeling without unsupported consciousness claims

### 13.1 Research question

Does a typed, multi-perspective self-model improve an entity's predictions about its own capabilities, resource use, failure modes, and policy changes?

Study the transition **WE → Self-Modeling Entity (SME)** as a functional design. A proposed Subjective Structural Entity (SSE) is a separate research construct, not an empirically established category of conscious systems.

### 13.2 Candidate tests

- Forecast own task success and latency under changing workloads.
- Detect when internal confidence is miscalibrated.
- Distinguish external evaluator feedback from self-evaluation.
- Revise self-models without rewriting historical evidence.
- Test identity continuity across model upgrades and role changes.
- Detect self-referential feedback that produces circular justification.

Use calibration error, selective prediction risk, intervention outcomes, and provenance consistency as observable metrics.

**Failure criterion:** self-description without improved prediction or control does not establish useful self-modeling.

**Related:** `CASE-005`, `EXT-004`, `WE-SIO-010`.

## 14. Direction L — Definition Evolution as an experimental discipline

### 14.1 Research question

Can definitions evolve through explicit counterexamples and regression tests without becoming either rigid or vacuously universal?

A definition revision should specify its old scope, triggering counterexample, proposed change, new invariants, backward compatibility, and tests. Revisions may narrow, split, broaden, supersede, or retire a concept.

### 14.2 Required records

- `DEFINITION-REGISTRY.md` for normative semantic claims.
- `COUNTEREXAMPLE-REGISTRY.md` for challenges and boundary cases.
- `DECISION-LOG.md` for alternatives and reasons.
- `HYPOTHESIS-REGISTRY.md` for empirical claims and tests.
- `UNRESOLVED-RESIDUALS.md` for gaps not yet resolved.

A successful Definition Evolution Loop (DEL) should reduce ambiguity and improve conformance coverage; producing more terminology is not itself success.

**Related:** `WE-SIO-011`, `SPEC-006`.

## 15. Cross-cutting evaluation strategy

### 15.1 Experimental ladder

| Stage | Goal | Required artifact |
|---|---|---|
| E0 | Define proposal and counterexamples | Contracts, assumptions, falsifiers |
| E1 | Establish synthetic conformance | Executable fixtures and reports |
| E2 | Compare controlled baselines | Reproducible benchmarks and ablations |
| E3 | Validate realistic workloads | Domain-grounded data and limitations |
| E4 | Independent reproduction | External replication and discrepancy log |

The labels describe an evidence progression, not automatic endorsement. A single experiment may support one claim and leave others at E0.

### 15.2 Universal reporting requirements

For every result, publish: exact claim, baseline, dataset and provenance, train/test separation, code and configuration versions, hardware, resource budget, statistical uncertainty, negative results, known threats to validity, and explicit leftover questions.

### 15.3 Safety and governance

For clinical, financial, security, or identity-related data, use appropriate privacy protections, access control, consent or authorization, and domain-specific review. Research prototypes must not be represented as validated decision systems.

## 16. Suggested priority roadmap

### Phase P0 — Semantic foundations

**Priority:** highest.  
Deliver typed entity/perspective schemas, formal distinctions, conformance fixtures, and cross-file definition consistency. Reject malformed or ambiguous requests explicitly.

**Gate:** no known violation of the core semantic invariants in the declared test scope.

### Phase P1 — Localization and baseline validation

Implement minimal WE-HDT and variable-block variants. Benchmark against established methods on matched workloads. Publish counterexamples where the proposed method loses.

**Gate:** an independently reproducible advantage on at least one prespecified metric or a documented reason to retain a simpler method.

### Phase P2 — Residual and question loops

Introduce residual registry, forward/reverse CCC interfaces, and independent hypothesis evaluation. Run synthetic discovery tasks with known hidden structure.

**Gate:** validated improvement in discovery quality or auditability without unacceptable false-discovery cost.

### Phase P3 — Controlled structural evolution

Add CDE policies for partitioning, perspective activation, and query strategy adaptation. Include cycle policy, resource ceilings, and rollback where semantically valid.

**Gate:** conformance preservation and measurable benefit after adaptation overhead.

### Phase P4 — Multi-agent and self-modeling research

Test specialized relay and calibrated self-modeling independently before combining them. Include strong single-agent and static-model controls.

**Gate:** repeatable improvements under equalized resources; no claims about subjective experience.

### Phase P5 — Open external relay

Invite independent replications, counterexamples, and alternative architectures. Publish versioned research packages and revise definitions when warranted.

**Gate:** traceable external evidence, not merely additional citations or collaborators.

## 17. High-priority falsification questions

1. Can a standard database and graph stack reproduce WE-SIO's claimed benefits at lower cost?
2. Does WE-HDT lose its advantage in high-dimensional or highly dynamic workloads?
3. Does candidate pruning violate exact completeness under any supported perspective?
4. Does adaptive intelligence allocation cost more than it saves?
5. Do reverse-generated questions outperform a conventional active-learning baseline?
6. Are apparent discoveries explained by leakage, confounding, or multiple testing?
7. Does CDE add an operational invariant beyond ordinary transition-system semantics?
8. Does multi-agent relay amplify shared errors or redundant evidence?
9. Does a self-model improve measurable calibration, or only verbal self-description?
10. Do definition revisions increase predictive precision or merely expand vocabulary?

A negative answer to a proposed advantage is a valid research outcome. Each such outcome should update the corresponding hypothesis, definition, and decision records.

## 18. Proposed research deliverables

- A minimal WE schema and conformance reference suite.
- A reproducible WE-HDT benchmark package with baselines.
- A PAVB/AVIB adaptation ablation report.
- A typed MLIU operation interface and cost profile.
- A residual registry and synthetic discovery benchmark.
- A metric-candidate validation suite with negative controls.
- A CDE state/delta/cycle-policy conformance suite.
- An SIF localization federation interface proposal.
- A multi-agent evidence-independence evaluation.
- A self-model calibration benchmark.
- A versioned Definition Evolution change log.
- An external Research Relay package template.

Deliverables should be independently usable; no implementation should be assumed to exist merely because it is listed here.

## 19. Dependencies and cross-references

The roadmap should be read alongside:

- `README.md` and `START-HERE.md` — overall positioning and reading path.
- `CONTENTS.md` and `GLOSSARY.md` — navigation and terminology.
- `TESTABLE-HYPOTHESES.md` and `VALIDATION-ROADMAP.md` — testable claims and execution plan.
- `HYPOTHESIS-REGISTRY.md` — hypothesis IDs, evidence states, and dependencies.
- `DEFINITION-REGISTRY.md` — normative concepts and revisions.
- `COUNTEREXAMPLE-REGISTRY.md` — boundary tests and falsifiers.
- `DECISION-LOG.md` — architectural choices and rejected alternatives.
- `UNRESOLVED-RESIDUALS.md` — unresolved research gaps.
- `docs/WE-SIO-001` through `docs/WE-SIO-012` — core theory.
- `specs/SPEC-001` through `specs/SPEC-006` — contracts.
- `cases/CASE-001` through `cases/CASE-005` — application and stress-test cases.
- `extensions/EXT-001` through `extensions/EXT-004` — ecosystem integration.

The shorthand references above identify planned or corresponding documents; repository maintainers should verify exact links and filenames before release.

## 20. Explicit leftovers

**L-001 — Novelty:** Which WE-SIO elements are genuinely distinct from existing indexing and knowledge-system designs?

**L-002 — Identity:** What cross-source identity claims are justified without assuming global identifiers?

**L-003 — Formal retrieval:** Which hybrid searches guarantee completeness, and under what assumptions?

**L-004 — Adaptation:** When should partitions or intelligence budgets change, and who authorizes those changes?

**L-005 — Metric validity:** How can newly generated perspectives be rejected before they contaminate downstream decisions?

**L-006 — Scientific evidence:** How are residual hypotheses protected against confounding and multiple-comparison bias?

**L-007 — CDE kernel:** What is the minimal nontrivial contribution beyond conventional state transitions and search?

**L-008 — Federation:** What should SIF guarantee when localization methods disagree?

**L-009 — Collective evidence:** How should correlated agents and reused sources be discounted?

**L-010 — Self-reference:** Which functional self-modeling properties are measurable without overclaiming subjectivity?

**L-011 — Resource governance:** What are safe budgets, stopping criteria, and rollback policies for open-ended evolution?

**L-012 — Reproducibility:** What is the smallest independent package needed to reproduce each claimed improvement?

These leftovers are first-class research assets. They should be assigned identifiers, owners or open ownership, validation routes, and review dates when the project moves from conceptual documentation to experiments.

## 21. Closing perspective

WE-SIO's most promising direction is not the claim that every object, metric, question, or intelligence can fit one tree. It is the possibility of **typed interoperability** between entity localization, evidence resolution, residual analysis, constrained evolution, and collaborative validation.

The project should grow by demonstrating which interfaces preserve correctness and which mechanisms create measurable value. Where experiments favor established alternatives, the framework should learn from them. Where definitions fail, counterexamples should drive revisions. Where evidence is missing, uncertainty should remain visible.

**The future of WE-SIO is an open research program—not a finished universal engine.**

---

*WE-SIO v0.1.0 · Future Directions · Sizhe Tan & GPT-Obot · 2026-11-05*
