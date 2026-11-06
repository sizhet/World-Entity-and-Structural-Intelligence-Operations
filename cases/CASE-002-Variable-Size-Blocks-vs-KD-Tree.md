# CASE-002 — Variable-Size Blocks vs. k-d Tree

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Case / Benchmark Protocol  
**Status:** Proposed architecture and falsifiable evaluation; no performance results claimed  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

## Abstract

This case examines the original Variable-Size Blocks Index and Search idea against the established k-dimensional tree (k-d tree), then asks which properties survive its generalization into WE-SIO's Perspective-Adaptive Variable Blocks (PAVB) and Adaptive Variable-Intelligence Blocks (AVIB). It separates correctness from efficiency, geometric partitioning from semantic interpretation, and a research proposal from demonstrated superiority. A reproducible benchmark plan, counterexamples, conformance requirements, and explicit research leftovers are provided.

## 1. Research origin and question

The starting proposal is to partition an indexed space into **variable-size blocks** rather than commit to one uniform granularity. Dense, heterogeneous, frequently queried, or high-uncertainty regions may warrant different partitions from sparse or stable regions. The proposed WE-SIO extension adds two further dimensions: (a) perspective-specific partitions and (b) independently adjustable intelligence capabilities associated with blocks.

The central question is not whether variable-size blocks *can* beat a k-d tree on a selected workload; it is **under which data distributions, query families, update regimes, and cost constraints** each approach is preferable.

### Scope

- Baseline: exact Euclidean point lookup, orthogonal range queries, and nearest-neighbor search in fixed-dimensional spaces.
- Extensions: updates, skew, heterogeneous densities, nonstationary workloads, and perspective-aware routing.
- Outside initial scope: claims of universally superior asymptotic complexity, automatic scientific discovery, or validated clinical benefit.

## 2. Terms and comparison boundaries

**k-d tree:** A spatial partitioning data structure that recursively splits points using axis-aligned hyperplanes. Construction, balance, pruning, and update policies vary by implementation. It is a family of designs, not one universal performance curve.

**Variable-Size Blocks (VSB):** A proposed indexing family that partitions a domain into blocks of adaptively selected extent and occupancy. Its exact partition rules, block directory, and search guarantees must be specified before benchmarking.

**PAVB:** Perspective-Adaptive Variable Blocks, in which different perspectives may use distinct partition geometries or representations.

**AVIB:** Adaptive Variable-Intelligence Blocks, which can change both partition structure and attached computational capabilities. **Block granularity and intelligence capability are independent axes.**

**WE-HDT:** A proposed hybrid architecture connecting geometric candidate localization with metric/relational resolution and optional intelligence operations. Logical metric leaves need not coincide with physical index leaves.

A k-d tree itself has nonuniform cell extents after recursive splitting. Therefore **variable block size alone is not a novel differentiator**. The proposed differentiators must be expressed as specific adaptation policies, operational interfaces, and measurable advantages.

## 3. Candidate architecture

### 3.1 Minimal block record

```yaml
Block:
  block_id: stable-reference
  perspective_id: registered-perspective
  geometry_or_predicate: domain-coverage-description
  member_reference: point-ids-or-secondary-index
  occupancy: nonnegative-integer
  version: monotonic-version
  routing_contract: exact-or-approximate
  split_merge_policy: policy-reference
  evidence_and_provenance: optional-records
  capability_profile: optional-MLIU-reference
```

Block extents may be geometric boxes, cells defined by a metric cover, or predicates for relational candidates. A geometric bound cannot be silently reused as a valid pruning rule for arbitrary directional relations.

### 3.2 Two-phase search

1. **Candidate localization:** Select blocks and candidate entity references using a perspective-specific index.
2. **Resolution:** Evaluate the query predicate or distance exactly (or under an explicitly declared approximation contract) on candidates.

For an exact query, the first phase must not exclude any qualifying entity. If candidate generation is approximate, the end-to-end guarantee must be reported as approximate even when the second phase uses exact scoring.

### 3.3 Adaptation controls

Potential operations include `SPLIT`, `MERGE`, `REBALANCE`, `REINDEX`, `ACTIVATE_CAPABILITY`, `DEACTIVATE_CAPABILITY`, and `ROLLBACK`. Each is governed by constraints on coverage, identity preservation, consistency, compute budget, and version transitions. CDE may organize these changes but does not establish their optimality by itself.

## 4. Reference query contracts

Let dataset \(X \subset \mathbb{R}^d\), query \(q\), and distance \(d_2(x,q)\) be Euclidean distance.

**Exact range query:** Return precisely \(\{x \in X : x \in R\}\) for a specified region \(R\).

**Exact nearest neighbor:** Return an \(x^* \in X\) such that \(d_2(x^*,q)=\min_{x\in X} d_2(x,q)\), with deterministic or documented tie handling.

**Approximate nearest neighbor:** Define the error contract, e.g. \(d_2(\hat{x},q)\le(1+\epsilon)d_2(x^*,q)\), or a recall-at-k metric if that is the actual guarantee. Do not conflate approximation ratios with observed recall.

**Dynamic correctness:** Queries must identify whether they observe a consistent snapshot, an eventual state, or a versioned state. Updates cannot be ignored in reported performance.

## 5. Comparative analysis

| Dimension | k-d tree baseline | Proposed VSB / PAVB | What must be tested |
|---|---|---|---|
| Partitioning | Recursive axis-aligned splits | Adaptive block size and policy | Whether policies add value beyond standard adaptive splitting |
| Exact range search | Established pruning rules | Requires proven block coverage and routing | Completeness and latency |
| Nearest neighbor | Established branch-and-bound approaches | Requires valid lower bounds or exhaustive fallback | Correctness, distance evaluations |
| Density skew | Behavior depends on split policy | Density-aware occupancy control proposed | Tail latency, memory, rebuild cost |
| Updates | Depends on implementation | Local split/merge proposed | Amortized update and query costs |
| High dimension | Pruning often degrades | No automatic escape from dimensionality | Scaling versus dimension |
| Multiple perspectives | Typically separate indexes or transformations | Explicit perspective registry and routing | Cost of extra indexes and query planning |
| Intelligence operations | Not a native requirement | Optional MLIU / residual relay | Incremental utility and overhead |

No row above implies an established VSB advantage. Balanced k-d trees can already adapt split positions to data distribution; comparisons must use strong, tuned baselines.

## 6. Complexity and correctness cautions

A balanced k-d tree for \(n\) points commonly has \(O(n)\) storage and logarithmic tree height, but actual query work depends on dimension, geometry, data distribution, and query type. Exact nearest-neighbor queries can approach linear scans in unfavorable cases. A VSB index also requires a directory or routing structure; claiming constant-time block selection without accounting for that structure is unjustified.

For VSB, total cost can be decomposed as:

\[
T_{query}=T_{route}+T_{candidate}+T_{resolve}+T_{coordination}.
\]

Memory and maintenance costs can be decomposed as:

\[
M_{total}=M_{directory}+M_{members}+M_{metadata}+M_{capabilities},
\]

\[
T_{update}=T_{locate}+T_{mutate}+T_{rebalance}+T_{version}.
\]

These are accounting identities, not complexity theorems. Report each term empirically where feasible.

## 7. Benchmark protocol

### 7.1 Implementations

- **B0:** Brute-force scan, serving as a correctness oracle for manageable datasets.
- **B1:** Well-implemented, tuned k-d tree, with disclosed split/balance and leaf-size settings.
- **B2:** Fixed-size grid or fixed-block index, when applicable.
- **B3:** Variable-size block index with predeclared adaptation policy.
- **B4:** PAVB, with perspective-specific partitioning and explicit routing.
- **B5:** AVIB, evaluated separately for indexing-only and intelligence-enabled configurations.

Use the same language/runtime, hardware, data representation, precision, and query workloads when possible. If implementations differ, disclose the limitations of direct comparison.

### 7.2 Datasets

1. Uniform synthetic points in 2, 3, 8, 16, and 32 dimensions.
2. Clustered and strongly skewed point clouds.
3. Anisotropic distributions and correlated dimensions.
4. Mixed dense/sparse regions and heavy-tailed occupancy.
5. Nonstationary streams with moving clusters.
6. Real-world datasets with documented provenance, licensing, and preprocessing.
7. Duplicate points, boundary points, missing values, and degenerate distributions.

Vary \(n\) over several orders of magnitude where resources permit. Hold out workloads used for final evaluation from policy tuning.

### 7.3 Workloads

- Exact point and range queries with varied selectivity.
- Exact k-nearest neighbor queries at different k.
- Mixed read/write streams with disclosed update ratios.
- Hotspot queries and shifting query distributions.
- Batch and concurrent queries, where supported.
- Perspective switching, including non-Euclidean queries where geometric pruning must be disabled or separately justified.

### 7.4 Metrics

Measure build time, memory footprint, query latency (median, p95, p99), throughput, candidate count, distance evaluations, block visits, update latency, rebalancing cost, and energy or CPU time when practical. For approximate modes also measure recall@k or the declared approximation guarantee. For AVIB measure **incremental capability cost** separately from index cost.

Use repeated trials, confidence intervals or uncertainty estimates, and publish raw results. Report negative findings and workloads on which k-d trees win.

### 7.5 Ablations

- Fixed vs adaptive block sizes.
- Density-only vs density-plus-query-frequency adaptation.
- With and without split/merge hysteresis.
- Single-perspective vs multiple-perspective routing.
- MLIU disabled vs enabled.
- Static vs dynamic datasets.
- Exact vs approximate candidate localization.

These ablations are necessary to attribute improvements to a specific mechanism.

## 8. Conformance requirements

| ID | Requirement | Test oracle |
|---|---|---|
| C-001 | Entity references remain stable across block split/merge | Identity registry |
| C-002 | Exact range queries are complete and sound | Brute-force oracle |
| C-003 | Exact NN agrees with oracle within numerical tolerance | Brute-force oracle |
| C-004 | Every indexed entity is covered by valid routing | Coverage audit |
| C-005 | Overlapping blocks do not cause duplicate output identities | Deduplication check |
| C-006 | Boundary predicates have specified inclusivity | Edge-case suite |
| C-007 | Nonmetric relations are not used with unproven metric pruning | Contract inspection |
| C-008 | Approximate results declare their guarantee | Query response schema |
| C-009 | Update visibility follows declared consistency semantics | Concurrent/snapshot tests |
| C-010 | Rebalancing preserves query correctness | Before/after oracle |
| C-011 | Perspective version changes invalidate dependent caches | Version audit |
| C-012 | Capability activation does not silently alter retrieval semantics | A/B conformance |
| C-013 | Resource limits and cancellation are enforced | Budget exhaustion tests |
| C-014 | Split/merge failures are recoverable or explicitly flagged | Fault injection |
| C-015 | Data provenance survives index migration | Provenance audit |
| C-016 | Performance claims are tied to published workload/configuration | Reproducibility checklist |
| C-017 | Empty, duplicate, and degenerate datasets are handled | Edge-case suite |
| C-018 | Residual and discovery outputs remain labeled hypotheses | Output schema |

Conformance establishes whether an implementation obeys its stated contract; it does **not** establish superiority to baselines.

## 9. Counterexamples and failure modes

**CE-001 — k-d tree already adapts cell size.** If the claimed contribution is merely nonuniform cell extents, it is not distinguishable from established k-d tree behavior.

**CE-002 — High-dimensional collapse.** A VSB partition may lose pruning power as dimension increases, just as k-d trees often do.

**CE-003 — Boundary-heavy queries.** Queries crossing many blocks can trigger high routing and candidate costs.

**CE-004 — Hotspot oscillation.** A rapidly changing workload can cause repeated split/merge churn; hysteresis and adaptation budgets may be needed.

**CE-005 — Sparse-region overhead.** Block metadata and directory lookup can outweigh a direct scan.

**CE-006 — Correlated axes.** Axis-aligned partitions may be poorly matched to diagonal manifolds; learned transformations or other indexes may be better.

**CE-007 — Metric misuse.** A directional relation without valid lower bounds cannot safely inherit Euclidean pruning guarantees.

**CE-008 — Candidate loss.** A two-phase pipeline can return a plausible but incomplete answer if stage one omits true matches.

**CE-009 — Capability inflation.** Per-block intelligence overhead can erase any indexing savings.

**CE-010 — Update inconsistency.** Concurrent migration can temporarily omit or double-count entities without a snapshot/transaction contract.

**CE-011 — Query-distribution overfitting.** Adaptation trained on one workload can underperform on a shifted distribution.

**CE-012 — No explanatory gain.** Adding MLIU/relay may increase system complexity without measurable decision quality improvement.

Every counterexample should be entered into `research-trace/COUNTEREXAMPLE-REGISTRY.md` with status, evidence, and any resulting definition revision.

## 10. Falsifiable hypotheses

**H-001 — Skew-sensitive latency:** For predefined skewed workloads, a tuned VSB policy reduces p95 query latency relative to a tuned k-d tree at comparable memory usage. *Falsified* if the confidence interval does not support the predefined improvement threshold.

**H-002 — Dynamic maintenance:** Under predefined update regimes, local split/merge reduces total maintenance cost without violating exact retrieval. *Falsified* if rebuild, churn, or synchronization costs dominate.

**H-003 — Multi-perspective efficiency:** PAVB reduces end-to-end cost for mixed-perspective workloads compared with separate strong per-perspective indexes. *Falsified* if added coordination and storage outweigh benefits.

**H-004 — Independent adaptation:** Joint tuning of partition size and capability allocation yields greater task utility per resource than tuning either alone. *Falsified* if ablations show no incremental benefit.

**H-005 — Residual-aware allocation:** Residual-guided adaptation improves a predeclared downstream validation metric without inflating false discoveries. *Falsified* if gains vanish on held-out evaluation.

All thresholds, datasets, and statistical criteria should be registered before confirmatory testing.

## 11. WE-SIO architectural implications

The research progression is:

```text
Variable-Size Blocks
    -> Perspective-Adaptive Variable Blocks (PAVB)
    -> Adaptive Variable-Intelligence Blocks (AVIB)
    -> WE-HDT integration
       [index localization] <-> [metric/relational resolution]
                         <-> [MLIU operations]
                         <-> [residual / research relay]
```

The progression is a **design hypothesis**, not a proof that every application needs each layer. In a simple Euclidean query workload, a tuned k-d tree may be the best choice. WE-SIO's stronger potential claim is **composability with explicit semantics, evidence, and evolution contracts**, whose value must be independently measured.

### Related project interfaces

- **WE-SIO-001–004:** Origin, entity representations, WE-HDT, and adaptive blocks.
- **WE-SIO-005–008:** MLIU, Two-Ways CCC, residuals, and perspective discovery.
- **WE-SIO-009:** Typed knowledge and structural delta updates.
- **WE-SIO-011:** Minimal Kernel and Definition Evolution Loop.
- **SPEC-001–003:** Identity, index conformance, and node/block/leaf contracts.
- **CDE:** Constrained evolution of partition and capability states.
- **SIF:** Localization/addressing as a possible integration point.

## 12. Research trace and relay record

Each experiment should publish a record with:

```yaml
experiment_id: CASE-002-EXP-001
hypothesis_id: H-001
code_revision: pending
baseline_revision: pending
dataset_manifest: pending
query_manifest: pending
hardware_and_runtime: pending
index_configuration: pending
correctness_oracle: brute-force
measurement_protocol: pending
results_and_uncertainty: pending
counterexamples: []
negative_findings: []
limitations: []
next_questions: []
```

Do not populate unknown fields with fabricated benchmark numbers. Research contributors should be able to rerun the comparison and understand which decisions produced the outcome.

## 13. Validation roadmap

**Stage 0 — Contract stabilization:** Specify block coverage, split/merge rules, exact/approximate semantics, and workload assumptions.

**Stage 1 — Correctness prototype:** Implement a reference VSB with brute-force oracle, boundary tests, and deterministic datasets.

**Stage 2 — Strong baselines:** Tune k-d tree and fixed-block baselines; publish configuration sweeps.

**Stage 3 — Adaptation experiments:** Evaluate skew, dynamics, query hotspots, memory, and update cost.

**Stage 4 — Perspective extension:** Test PAVB against independent indexes, clearly separating Euclidean from relational queries.

**Stage 5 — Intelligence extension:** Enable MLIU/relay and measure task utility, false-discovery control, and overhead independently.

Progression to each stage requires passing the preceding stage's relevant correctness tests.

## 14. Explicit leftovers and open questions

1. Which block directory best supports both exact coverage and cheap updates?
2. What objective should adaptation optimize: latency, memory, update cost, downstream utility, or a constrained combination?
3. Can a block's split/merge decision be made locally without harming global performance?
4. What formal guarantee is possible for mixed Euclidean and relational candidate generation?
5. How should adaptation respond to distribution drift without oscillation?
6. Where is the crossover between VSB routing overhead and a brute-force scan?
7. What is the minimal MLIU capability that produces measurable utility?
8. Which advantages, if any, remain after comparison with tuned R-trees, ball trees, cover trees, and approximate-neighbor systems?
9. How can index migration remain correct under concurrent updates?
10. Can residual-driven block adaptation improve scientific hypothesis generation without selection bias?

## 15. Conclusion

Variable-size partitioning is a promising **design degree of freedom**, not a demonstrated replacement for k-d trees. The WE-SIO contribution to investigate is the controlled combination of adaptive partitioning, perspective-aware indexing, independently allocated intelligence capabilities, and traceable research feedback. Exactness, efficiency, novelty, and scientific utility are separate claims and require separate evidence.

> **Define the invariant, not the inventory. Compare against the strongest relevant baseline, not a convenient one. Preserve the counterexample as well as the result.**

---

**Repository path:** `cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md`  
**Release status:** v0.1.0 research case; benchmark results pending.  
**License:** Apache-2.0 (repository policy, subject to final release metadata).
