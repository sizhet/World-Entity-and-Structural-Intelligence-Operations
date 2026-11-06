# EXT-005 — Mask-First Structural Intelligence and Epistemic Separation

**WE-SIO v0.1.0 — Research Extension**  
**Title:** *Mature-Structure Preservation, Dynamic Computational Views, and Epistemic Separation*  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05  
**Status:** Hypothesis-driven architectural proposal; not empirically validated  
**License:** Apache-2.0

## Abstract

This extension proposes **Mask-First Structural Intelligence (MFSI)** as a computational mechanism for the World Entity and Structural Intelligence Operations (WE-SIO) framework. Instead of routinely splitting, merging, or rebuilding mature knowledge structures when tasks change, a control plane may generate task-, perspective-, context-, and budget-conditioned masks that select an *effective computational view* over a comparatively persistent substrate. We distinguish activation deltas from knowledge and structural deltas, define a minimal masking contract, and propose evidence-qualified separation of established knowledge, open knowledge, and residual evidence. These concepts connect adaptive variable-intelligence blocks (AVIB), metric-leaf intelligence units (MLIU), residual-first discovery, constrained delta evolution (CDE), and collective learning. Brain-inspired selective activation motivates the hypothesis but does not constitute neuroscientific proof or performance evidence. The proposal includes counterexamples, falsifiable hypotheses, conformance requirements, and an experimental roadmap.

## 1. Motivation and scope

WE-SIO treats World Entities, perspectives, metric/relational indices, adaptive blocks, and operations as potentially reusable structural assets. A naive implementation could respond to each new task by restructuring the index or redistributing blocks. That approach risks unnecessary migration costs, loss of mature paths, unstable identity, and difficult regression testing. A complementary approach is to **preserve the substrate and vary the active computational view**.

This extension makes three linked proposals:

1. **Mature-structure preservation:** reuse learned paths and local knowledge before modifying topology, subject to measurable quality and safety constraints.
2. **Mask-first computation:** dynamically select nodes, edges, perspectives, operations, depths, and resource budgets without requiring a physical reindex.
3. **Epistemic separation:** distinguish evidence-supported knowledge, unresolved questions or hypotheses, and qualified residual evidence. Unknown is not residual.

The extension does **not** claim that every structure should remain fixed, that all masks are cheap, that every column is a metric, or that biological brains implement one explicit software-style mask.

## 2. Definitions and invariants

### 2.1 Structural substrate and effective view

Let `S_v` be a versioned stored structure with entities, nodes, links, indices, evidence, and operational capabilities. Let `q` be the task, `p` the perspective set, `c` the context, `b` the resource budget, and `g` the governance constraints.

A mask generator produces:

`M_t = G(q, p, c, b, g, S_v, H_t)`

where `H_t` is relevant evaluation history. Execution is:

`(y_t, trace_t) = Execute(S_v, M_t, q, c)`

`M_t` may be binary, weighted, hierarchical, sparse, or a policy over permitted operations. The effective computational view `V_t = View(S_v, M_t)` is **not** necessarily a materialized subgraph. A masked-out path remains in storage unless an independently authorized structural operation changes it.

**Invariant M1 — Identity preservation:** applying or removing a mask must not silently change World Entity identity, evidence provenance, or the meaning of an established perspective.

**Invariant M2 — Governance preservation:** masking cannot expand access beyond the source's authorization boundary; a mask is never a substitute for access control.

**Invariant M3 — Traceability:** consequential mask decisions must be attributable to task, generator/policy version, selected scope, budget, and observed outcome.

**Invariant M4 — Recoverability:** deactivation is not deletion; stored structure must remain accessible to authorized future evaluations unless separately revised.

### 2.2 Three distinct delta families

- **Activation Delta (`ΔA`)** changes the active computational view: selected nodes, routes, metrics, operations, and budget.
- **Epistemic Delta (`ΔK`)** changes what is believed, hypothesized, evidenced, qualified, or retracted, with versioned provenance.
- **Structural Delta (`ΔS`)** changes durable representation or topology: new blocks, splits, merges, indices, contracts, or connections.

A fourth **World Delta (`ΔW`)** changes the modeled external world or an authorized source-of-truth state; it must not be inferred merely from `ΔK`. The system may attempt `ΔA` before `ΔS`, but this is a **cost-sensitive preference, not an obligatory ordering**. Safety, expressivity, latency, and fidelity may require immediate structural revision.

### 2.3 Epistemic categories

**Established Knowledge (`EK`)**: an assertion or model usable within a specified perspective, scope, time, and evidence contract. Established means *qualified for use*, not infallible or universally true.

**Open Knowledge (`OK`)**: unresolved questions, unverified hypotheses, candidate relations, missing measurements, or underdetermined explanations. Open items can exist without a prediction error.

**Residual Evidence (`RE`)**: a traceable discrepancy, conflict, or explanatory gap **relative to a declared expectation, constraint, model, or comparison baseline**. Residuals may be numeric or structural. A residual is not automatically noise, novelty, a new law, or a failed hypothesis.

`EK`, `OK`, and `RE` are **logical views/statuses**, not necessarily disjoint physical buckets. A single entity may have established attributes under one perspective and open attributes under another; a residual may reference both an established model and an open hypothesis.

## 3. Mask taxonomy and operations

| Mask class | Selected scope | Example | Key risk |
|---|---|---|---|
| Node mask | Entity/block/MLIU activation | Relevant AVIBs for a question | Omitted evidence |
| Edge/path mask | Traversal and relational routes | Restrict joins to justified paths | Broken multi-hop inference |
| Metric/perspective mask | Measurement or relational lenses | Use temporal and spatial views | Semantic type confusion |
| Operation mask | Locate, Resolve, Relate, Infer, Question, Evolve | Read-only inference | Unauthorized action |
| Depth/scale mask | Search depth and granularity | Coarse-to-fine candidate search | Premature stopping |
| Budget mask | Time, tokens, memory, compute | Limit expensive exploration | Quality degradation |
| Epistemic mask | Established/open/residual views | Retrieval vs hypothesis generation | Treating tentative claims as facts |

**Core operations:** `GenerateMask`, `ValidateMask`, `ApplyMask`, `EvaluateMaskedExecution`, `ReviseMask`, `ReleaseMask`, `PromoteMaskPolicy`, and `RollbackMaskPolicy`.

A mask can be **soft** (weight or priority) or **hard** (strict exclusion). Hard exclusion requires stronger completeness checks when the task demands exhaustive results. Mask composition must specify precedence, conflicts, and the behavior of an empty or contradictory selection.

## 4. Mask-first execution loop

1. **Resolve task and permissions.** Determine required result type, relevant World Entities, permitted perspectives, risk, and acceptable error.
2. **Generate candidate masks.** Use precedent masks, schema constraints, control-plane policies, and possibly learned generators.
3. **Check contracts.** Validate type compatibility, permissions, provenance coverage, mandatory paths, and budget feasibility.
4. **Execute selectively.** Run the selected operations over the persistent substrate; retain an execution trace.
5. **Compare against baselines.** Evaluate correctness, coverage, latency, cost, uncertainty, and omissions.
6. **Diagnose residuals.** Register qualified discrepancies; place untested questions in Open Knowledge rather than in a generic residual bucket.
7. **Choose the next delta.** Revise `ΔA`, update qualified `ΔK`, or propose `ΔS` only when justified by evidence and cost.
8. **Relay and regress.** Store transferable masks with compatibility contracts and test them on held-out tasks.

A practical fallback is an **unmasked or broader-mask reference execution** on selected benchmark cases. Where full execution is too expensive, use independently sampled coverage audits or domain-specific completeness certificates. Mask generation overhead must be included in total cost.

## 5. Established/Open Knowledge and the Residual Evidence Registry

### 5.1 Why two knowledge views are not enough

A simple Known/Unknown split misses the distinction between *not yet known* and *observed to disagree with a particular explanation*. For example:

- The conductivity of an untested material is **Open Knowledge**.
- A measured conductivity inconsistent with a versioned prediction is **Residual Evidence**.
- A validated relationship within stated experimental conditions may be **Established Knowledge**.

Unknown values, missing data, database `NULL`, conflicting sources, and model residuals must not be automatically equated.

### 5.2 Proposed logical records

**Knowledge Assertion**

```text
assertionId, entityRef, perspectiveId, statementOrValue,
status(EK|OK), scope, conditions, validTime, recordedTime,
evidenceRefs, confidenceOrUncertainty, provenance,
modelVersion, reviewStatus
```

**Residual Evidence Registry (RER) entry**

```text
residualId, entityRef, perspectiveId, baselineRef,
expectedOrConstraint, observedOrConflict, discrepancyType,
evidenceRefs, uncertainty, severity, alternativeExplanations,
openQuestionRefs, diagnosticStatus, ownerOrAgent,
createdAt, resolvedAt, provenance, version
```

The RER is a **qualified evidence registry**, not a catch-all storage bucket. Entries without a meaningful comparison baseline belong elsewhere until their residual qualification can be established.

### 5.3 State transitions and safeguards

- `OK → EK`: evidence evaluation passes the applicable validation contract.
- `EK → revised EK`: new evidence narrows or changes scope, with historical versions retained.
- `EK → OK/retracted`: contradictory evidence invalidates current qualification; downstream dependents are flagged.
- `RE → diagnosed`: discrepancy attributed to noise, measurement error, confounding, drift, model limitation, or a candidate new mechanism.
- `RE → resolved`: disposition is documented; do not erase the historical evidence trace.

No automatic promotion solely because multiple agents agree. Independence, provenance, leakage checks, uncertainty calibration, and domain-specific review remain necessary.

## 6. Integration with WE-SIO components

### 6.1 WE-HDT and PAVB

WE-HDT may support coarse candidate localization followed by typed metric or relational resolution. Masks choose active subtrees, candidate routes, or perspectives while leaving physical indexing and identity stable. PAVB boundaries need not be altered on every query. The index is an access structure, not a proof of semantic equivalence.

### 6.2 AVIB and MLIU

AVIB gains explicit `Mask/Unmask/Remask` operations alongside `Split/Merge/Resize/Reindex/Activate/Delegate`. MLIU exposes capabilities and epistemic status under a resource budget. A lightweight leaf may be masked into a workflow without becoming a full autonomous agent.

### 6.3 Two-Ways CCC and residual-first discovery

Forward evaluation uses masks to localize candidates and apply constraints. Reverse evaluation uses qualified residuals to generate diagnostic questions, new perspectives, and revised masks. Unknown questions remain in Open Knowledge until there is an identifiable discrepancy.

### 6.4 CDE and SIF

CDE evaluates competing `ΔA`, `ΔK`, and `ΔS` proposals under constraints and resource budgets; path-memory or no-reuse restrictions apply only where specified by a particular search contract. Within SIF, WE-HDT and CDE remain complementary **candidate** localization/addressing mechanisms; the mask layer is an execution/control interface, not a replacement for either.

### 6.5 Collective learning and relay

A reusable mask is a potential **relay piece** containing: task family, structural compatibility, perspective types, policy version, selected routes, measured outcomes, failure cases, and provenance. A mask discovered by one agent should be revalidated before reuse in another environment. Repeated execution can accumulate useful evaluation evidence, but repeated agreement is not independent confirmation.

## 7. Brain-inspired motivation and its limits

Selective neural activation, inhibition, attention, and gain modulation motivate the idea of dynamically engaging subsets of a persistent substrate. However, biological neural systems also undergo synaptic pruning, connection formation, and other structural plasticity. This extension does **not** claim that brains never restructure, that a unified explicit mask exists in neural tissue, or that biomimicry guarantees superior performance. The proposed abstraction must stand on engineering tests rather than analogy.

## 8. Contracts and conformance requirements

**C-MASK-01 — Typed selection:** each mask declares target structure version, perspective/operation types, and selection semantics.

**C-MASK-02 — No silent mutation:** applying a computational mask cannot mutate durable structure or established knowledge without an independently authorized delta.

**C-MASK-03 — Permission monotonicity:** selected data and operations are a subset of authorized capabilities.

**C-MASK-04 — Evidence coverage:** masked results carry coverage or omission indicators; exhaustive tasks require a completeness strategy.

**C-MASK-05 — Reproducibility:** record generator version, mask definition, task context, substrate version, and execution trace.

**C-MASK-06 — Budget accounting:** count mask construction, validation, execution, audit, and rollback costs.

**C-EPI-01 — Perspective-relative qualification:** EK/OK status includes scope, evidence, and version.

**C-EPI-02 — Residual qualification:** RER entries require a stated comparison baseline and discrepancy or explanatory conflict.

**C-EPI-03 — Promotion/retraction:** status transitions require explicit validation, dependency handling, and rollback history.

**C-EPI-04 — No conflation:** absence, uncertainty, unknown, NULL, conflict, and residual must remain distinguishable.

These are proposed requirements for integration into `SPEC-003` and `SPEC-005`, not assertions that existing implementations already conform.

## 9. Testable hypotheses

**WEH-031 — Mask-first efficiency.** On specified multi-perspective retrieval/inference workloads, MFSI reduces end-to-end compute or latency compared with repeated split/merge/reindex strategies **at matched answer quality and coverage**. Null result: no savings after mask overhead or unacceptable omissions.

**WEH-032 — Mature-structure retention.** In continual-task benchmarks, in-situ masked adaptation reduces structural churn and catastrophic forgetting relative to restructuring baselines **without degrading adaptation to distribution shifts**. Null result: retention provides no benefit or blocks necessary adaptation.

**WEH-033 — Epistemic separation.** Explicit EK/OK/RER contracts reduce false residual classification, unsupported knowledge promotion, and provenance loss compared with a single generic unknown/residual bucket. Null result: no statistically meaningful improvement or excessive management overhead.

**WEH-034 — Relay portability (exploratory).** Versioned mask policies transfer across compatible task families more efficiently than rediscovering routes from scratch, without increased error. Null result: compatibility checks erase the gain or transfer produces negative performance.

All hypotheses require predeclared datasets, baselines, metrics, and failure thresholds. Hypothesis IDs should be reconciled with the repository's authoritative registry before release.

## 10. Minimal experimental program

| Phase | Experiment | Baseline | Primary metrics |
|---|---|---|---|
| P0 | Synthetic WE-HDT/AVIB task switching | Full traversal; eager reindex | Accuracy, recall, p95 latency, total compute, mask overhead |
| P0 | EK/OK/RER classification | Generic residual bucket | False residual rate, provenance completeness, review cost |
| P1 | Continual multi-task adaptation | Periodic split/merge/rebuild | Forgetting, structural churn, recovery time, accuracy |
| P1 | Mask completeness audit | Unmasked reference on sampled cases | Missed evidence, calibration, audit overhead |
| P2 | Multi-agent mask relay | Independent mask discovery | Transfer gain, compatibility failures, negative transfer |
| P2 | SQL schema-to-WE prototype | Schema linking without MFSI | Correct joins, column selection, access compliance, end-to-end cost |

Use paired tasks and held-out distributions; report failure cases and negative results. SQL-specific work should distinguish table/row/column semantics, source-scoped identity, NULL, relational constraints, and physical indices. A SQL column is not automatically a mathematical metric.

## 11. Counterexamples and failure modes

1. **Mask misses a critical path:** a low-cost result is wrong because evidence was excluded. Remedy: coverage audits, uncertainty signaling, fallback expansion.
2. **Mask generation costs more than execution:** dynamic gating increases latency. Remedy: cache or reuse masks only when validated; bypass masks for small tasks.
3. **New relation cannot be represented:** preserving structure prevents necessary modeling. Remedy: authorize `ΔS` rather than enforcing mask-first dogmatically.
4. **Stale mask after schema drift:** reused paths silently become invalid. Remedy: structural compatibility checks and invalidation.
5. **Open question misfiled as residual:** unknown data is mistaken for model failure. Remedy: baseline-required RER admission.
6. **Conflicting evidence promoted by consensus:** agents repeat the same source. Remedy: source-independence checks and validation gates.
7. **Masked security boundary:** a generated mask appears to grant inaccessible data. Remedy: authorization checked outside and below the mask layer.
8. **Biological analogy overreach:** claims about brain mechanisms are treated as proven implementation facts. Remedy: explicitly separate inspiration from evidence.

## 12. Open questions

- Can a compact mask policy remain interpretable as WE-SIO scales to heterogeneous perspectives?
- When is mask reuse superior to regeneration, and what invalidates compatibility?
- How should hard and soft masks compose under conflicting governance and completeness constraints?
- What is the smallest useful MLIU mask interface for non-agentic leaves?
- Can residual-driven mask revision discover missing perspectives without amplifying spurious correlations?
- What formal criterion justifies moving from `ΔA` to `ΔS`?
- How should epistemic states propagate across JOIN-like relational compositions and derived views?
- Can negative mask-transfer results be stored as reusable relay evidence?

## 13. Recommended repository integration

**Primary companion files:**

- `docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md` — Mask/Unmask/Remask; mature-structure preservation; activation versus structural deltas.
- `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md` — epistemic views and metric/operation masks.
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md` — replace ambiguous residual-bucket language with qualified Residual Evidence Registry semantics.
- `docs/WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md` — promotion, retraction, and versioned evidence.
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md` — activation delta as distinct from structural and epistemic delta.
- `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md` — mask interface and no-silent-mutation contract.
- `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md` — epistemic separation and RER qualification.
- `TESTABLE-HYPOTHESES.md`, `VALIDATION-ROADMAP.md`, `CONTENTS.md`, `README.md`, `CHANGELOG.md` — add registry links and version-consistent navigation.

**Next application extension (proposed):** `EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`, using SQL as a concrete validation environment rather than claiming a completed SQL AI system.

## 14. Conclusion

MFSI proposes a division of labor: **persistent structural knowledge, dynamic masked computation, evidence-qualified epistemic evolution, and selective structural change**. The practical rule is *Mask before Rebuild; Reuse before Regenerate; Validate before Promote*—a defeasible engineering preference rather than a universal law. Its value depends on measurable improvements in correctness, coverage, cost, adaptability, and governance. Until those tests are completed, this extension remains a structured research hypothesis and a candidate collective-learning relay piece.

---

**Suggested citation:** Sizhe Tan and GPT-Obot (2026). *EXT-005: Mask-First Structural Intelligence and Epistemic Separation*. WE-SIO v0.1.0 research extension. GitHub repository: https://github.com/sizhet/World-Entity-and-Structural-Intelligence-Operations. DOI pending.
