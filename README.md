# World Entity and Structural Intelligence Operations (WE-SIO)

**From Variable-Size Block Indexing to Open-Ended World Modeling, Metric Discovery, and Self-Referential Intelligence**

**Research framework:** v0.1.0 (proposed; not empirically validated)  
**Authors / research collaboration:** Sizhe Tan & GPT-Obot  
**Research posture:** Specifications First · Conformance Before Runtime · Explicit Leftovers · Collective Learning

> **Define the invariant, not the inventory.**  
> **Definition incomplete does not mean definition imprecise.**

## 1. Overview

World Entity and Structural Intelligence Operations (WE-SIO) proposes an extensible structural-intelligence framework for representing entities, locating evidence across multiple perspectives, producing accountable inferences, generating questions from unresolved residuals, and evolving the definitions and structures used to model a changing world.

The investigation begins with **variable-size blocks and two-phase search** and asks a broader question: *What if the unit of indexing were not simply a data record or spatial cell, but a world entity with multiple, evolving perspectives and locally addressable intelligence?*

WE-SIO is a **research architecture and hypothesis collection**, not a demonstrated general-purpose intelligence system, production database, clinical decision system, or proven scientific discovery engine. Proposed advantages require conformance tests, comparative baselines, and independent replication.

## 2. Research trajectory

```text
Variable-Size Blocks (VSB)
    ↓ candidate localization and two-phase search
World Entity (WE) + typed Perspective Descriptors
    ↓ perspective-aware organization
WE Hybrid Differential Tree (WE-HDT)
    ↓ adaptive partition and local capability
PAVB / AVIB + Metric Leaf Intelligence Unit (MLIU)
    ↓ forward resolution ↔ backward questioning
Two-Ways CCC + Residual Registry
    ↓ hypothesis and perspective generation
Metric Discovery + Scientific Validation
    ↓ constrained structural adaptation
CDE + Definition Evolution Loop (DEL)
    ↓ multi-agent exchange and self-modeling
Collective Learning Relay + SME / SSI research interface
```

This sequence describes the **conceptual path of the proposal**, not an assertion that each arrow has been implemented or experimentally established.

## 3. Minimal semantic distinctions

| Concept | Working meaning | Essential boundary |
|---|---|---|
| **World Entity (WE)** | Referenced entity about which observations, perspectives and hypotheses are organized | Entity identity is not its metric signature, database key or representation |
| **Perspective** | Typed view defining what is measured, compared or related | Not every perspective is a mathematical metric |
| **Metric** | Distance satisfying declared mathematical axioms on its domain | Similarity, directional relation and arbitrary numeric feature need separate contracts |
| **Evidence** | Versioned observation or claim with source and uncertainty | Agreement among correlated agents is not independent corroboration |
| **WE-HDT** | Candidate architecture for perspective-aware localization and resolution | Index hierarchy need not equal conceptual hierarchy; Euclidean coordinates are optional |
| **PAVB** | Perspective-Adaptive Variable Blocks | Variable block size alone is not novel relative to all spatial trees |
| **AVIB** | Adaptive Variable-Intelligence Blocks | Partition granularity and intelligence capability are independent dimensions |
| **MLIU** | Metric Leaf Intelligence Unit exposing bounded structural operations | A logical leaf does not require a heavyweight autonomous agent |
| **Residual** | Accountable gap between expectation and observation or required condition | A residual is not automatically evidence of a new scientific mechanism |
| **Delta** | Typed change to world, observation, knowledge, or structure | Updating a model does not necessarily change the world |
| **CDE** | Constrained Delta Evolution over states and applicable transitions | No-Delta-Reuse is application-specific, not a universal CDE axiom |
| **SME** | Self-Modeling Entity maintaining testable models of its own capabilities and state | Self-modeling does not demonstrate subjective experience |
| **DEL** | Definition Evolution Loop for controlled conceptual revision | Revision must preserve traceability and pass regression tests |

The shorthand `Object[metricIdx]` is a useful entry point, but is **not** a complete entity-identity or perspective schema.

## 4. Proposed architecture

### 4.1 World entity and perspective layer

Each entity is referenced independently of its observations and representations. A perspective descriptor declares domain, value type, units (if any), comparison or relation contract, provenance, uncertainty, time, version and authorization context. Spatial, temporal, semantic and relational perspectives can coexist without being forced into one Euclidean metric space.

### 4.2 Localization and addressing: WE-HDT

WE-HDT is proposed as a hybrid organization for candidate generation, differential comparison, metric/relational resolution and traceable evidence retrieval. A two-phase operation separates **candidate localization** from **contract-governed verification**. Exactness, completeness and approximate-search error bounds must be stated per operation and benchmarked against appropriate baselines, including brute force and k-d trees.

### 4.3 Adaptive structure: PAVB and AVIB

Block size may adapt to workload, perspective and density; intelligence capability may independently adapt to expected utility, residual pressure and resource budgets. Splitting, merging, activating or delegating must be auditable and should avoid oscillation, uncontrolled overhead and silent invalidation of indices.

### 4.4 Metric Leaf Intelligence Units

An MLIU may expose six bounded operations: **Locate, Resolve, Relate, Infer, Question, Evolve**. Its contract includes entity reference, perspective identifier, observations, hypotheses, uncertainty, residuals, resource budget, provenance, version and relay interfaces. Local outputs must remain distinguishable from verified global conclusions.

### 4.5 Two-Ways CCC and scientific discovery

The forward path localizes candidates, evaluates constraints, and produces answers with evidence and uncertainty. The backward path inspects unexplained residuals and generates questions, candidate relationships or new perspectives. Proposed discoveries pass data-quality, semantic, mathematical, experimental, robustness and governance checks before promotion. Independent validation is essential; noise, confounding, selection bias and leakage are alternative explanations.

### 4.6 Delta, CDE and definition evolution

WE-SIO separates **world delta**, **observation delta**, **epistemic/knowledge delta**, and **structural/operational delta**. CDE is a candidate mechanism for bounded transitions and structural search, while DEL governs revisions of definitions and their invariants. The chess case demonstrates why repeated moves or positions can be legal and why a universal No-Delta-Reuse rule would be unsound.

### 4.7 Collective learning and self-reference

Multiple agents may specialize in localization, inference, questioning, critique, verification and governance. Relay artifacts preserve evidence provenance, negative results, dependency information and unresolved questions. WE → SME → candidate SSE is a **research progression**, not a proof of consciousness; links to Subjective Structural Intelligence (SSI) are exploratory.

## 5. Relationship to the broader SI research program

| Framework | Proposed relationship to WE-SIO |
|---|---|
| **SIF — Structural Intelligence Framework** | WE-HDT is a candidate Localization / Addressing pillar; CDE offers complementary state/delta-space exploration |
| **CDE — Constrained Delta Evolution** | Constrained structural transitions, candidate search and evolution policies |
| **UCPSF** | Perspective-aware scoring and control-plane decisions |
| **AQSI** | Autonomous questioning and hypothesis proposal driven by residuals |
| **UIERU** | Multi-unit relay, learning accumulation and structural evolution |
| **SSI** | Subject boundaries, self-modeling, valuation and the limits of subjective inference |
| **BM-ODWEI** | Directional weak evidence, perspective distance and cautious cross-perspective interpretation |
| **D-BTP** | A motivating constrained-search specialization; its path rules are not generalized without qualification |

These are proposed research interfaces, not claims of completed software interoperability.

## 6. Repository map

```text
World-Entity-and-Structural-Intelligence-Operations/
├── README.md
├── START-HERE.md
├── CONTENTS.md
├── GLOSSARY.md
├── FIGURE-INDEX.md
├── FUTURE-DIRECTIONS.md
├── OPEN-QUESTIONS.md
├── TESTABLE-HYPOTHESES.md
├── VALIDATION-ROADMAP.md
├── CHANGELOG.md
├── CITATION.cff
├── .zenodo.json
├── LICENSE
├── docs/                  # WE-SIO-001 … WE-SIO-012
├── specs/                 # SPEC-001 … SPEC-006
├── cases/                 # CASE-001 … CASE-005
├── extensions/            # EXT-001 … EXT-004
├── research-trace/        # origin, synthesis and five registries/logs
├── figures/               # Fig-001 … Fig-010 (planned individual PNGs)
└── release/               # GitHub release notes and ResearchGate assets
```

The tree is the **target release layout**. Check the actual repository before publishing: listing a file here does not guarantee that it has been committed. The ten figure concepts have been visualized as a composite overview; the ten separately named PNGs must be exported and checked individually before linking them as repository assets.

### 6.1 Core papers (`docs/`)

1. [WE-SIO-001 — From Variable-Size Blocks to World Entity](docs/WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md)
2. [WE-SIO-002 — World Entity Representation and Perspective Indices](docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md)
3. [WE-SIO-003 — WE Hybrid Differential Tree Architecture](docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md)
4. [WE-SIO-004 — Adaptive Variable-Intelligence Blocks](docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md)
5. [WE-SIO-005 — Metric Leaf Intelligence and SI Operations](docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md)
6. [WE-SIO-006 — Two-Ways CCC and Cross-Metric Discovery](docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md)
7. [WE-SIO-007 — Residual-First Scientific Discovery](docs/WE-SIO-007-Residual-First-Scientific-Discovery.md)
8. [WE-SIO-008 — Metric Discovery and Perspective Evolution](docs/WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md)
9. [WE-SIO-009 — World Delta, Knowledge Delta, and CDE](docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md)
10. [WE-SIO-010 — From World Entity to Self-Modeling Entity](docs/WE-SIO-010-From-World-Entity-to-Self-Modeling-Entity.md)
11. [WE-SIO-011 — Minimal Kernel, Contracts, and Definition Evolution](docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md)
12. [WE-SIO-012 — WE-SIO as a Collective Learning Relay Piece](docs/WE-SIO-012-WE-SIO-as-a-Collective-Learning-Relay-Piece.md)

### 6.2 Specifications (`specs/`)

- [SPEC-001 — World Entity Identity and Perspective Descriptor Contract](specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md)
- [SPEC-002 — Euclidean, Metric, and Relational Index Conformance](specs/SPEC-002-Euclidean-Metric-and-Relational-Index-Conformance.md)
- [SPEC-003 — WE-HDT Node, Block, and Metric Leaf Contract](specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md)
- [SPEC-004 — SI Operations and Two-Ways CCC Interface](specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md)
- [SPEC-005 — Residual, Evidence, and Metric Discovery Contract](specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md)
- [SPEC-006 — Definition Evolution and Research Relay Contract](specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md)

### 6.3 Cases (`cases/`)

- [CASE-001 — SQL Columns to WE Perspective Indices](cases/CASE-001-SQL-Columns-to-WE-Perspective-Indices.md): database-record versus entity semantics.
- [CASE-002 — Variable-Size Blocks vs k-d Tree](cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md): fair indexing baselines and unproven performance claims.
- [CASE-003 — Clinical Treatment-Response Residuals](cases/CASE-003-Clinical-Treatment-Response-Residuals.md): hypothetical research workflow, **not clinical advice**.
- [CASE-004 — Chess as a CDE Boundary Stress Test](cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md): cycles, state history and domain-specific constraints.
- [CASE-005 — Multi-Perspective Self-Modeling Entity](cases/CASE-005-Multi-Perspective-Self-Modeling-Entity.md): calibration and self-modeling boundaries.

### 6.4 Extensions (`extensions/`)

- [EXT-001 — WE-HDT as an SIF Localization Pillar](extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md)
- [EXT-002 — Multi-Agent WE-SI and Collective Learning](extensions/EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md)
- [EXT-003 — Structural Scientific Discovery and Metric Generation](extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md)
- [EXT-004 — Self-Referential World Entity and Subjective SI](extensions/EXT-004-Self-Referential-World-Entity-and-Subjective-SI.md)

### 6.5 Research trace (`research-trace/`)

- [Origin and Research Questions](research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md)
- [Discussion Synthesis — 2026-11-05](research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md)
- [Hypothesis Registry](research-trace/HYPOTHESIS-REGISTRY.md) — falsifiable propositions and evidence levels.
- [Definition Registry](research-trace/DEFINITION-REGISTRY.md) — minimal kernels, scope and evolution.
- [Counterexample Registry](research-trace/COUNTEREXAMPLE-REGISTRY.md) — stress tests and failure conditions.
- [Decision Log](research-trace/DECISION-LOG.md) — architectural choices and alternatives.
- [Unresolved Residuals](research-trace/UNRESOLVED-RESIDUALS.md) — explicitly outstanding gaps.

Registry entries are **research proposals or candidate tests** unless an entry explicitly links to a completed, reproducible result.

## 7. Ten planned figures

| Figure | Title | Primary purpose |
|---|---|---|
| Fig-001 | WE-SIO Grand Architecture | Overall research stack and feedback |
| Fig-002 | From Variable-Size Blocks to World Entity | Origin and conceptual transition |
| Fig-003 | WE Hybrid Differential Tree | Multi-perspective localization |
| Fig-004 | Adaptive Variable-Intelligence Blocks | Decoupled partition and capability adaptation |
| Fig-005 | Metric Leaf Intelligence Unit | Local operations and evidence contracts |
| Fig-006 | Two-Ways CCC Cross-Metric Discovery | Forward answers and backward questions |
| Fig-007 | Residual-Driven Scientific Discovery Loop | Discovery and validation workflow |
| Fig-008 | World Delta vs Epistemic Delta | Change-type distinctions |
| Fig-009 | Definition Evolution Loop | Counterexample-driven definition revision |
| Fig-010 | From WE to Self-Modeling Entity and Collective Relay | Self-modeling and multi-agent relay |

**Figure integrity note:** A combined overview image does not by itself create ten individual figure files. Before release, ensure the filenames, diagrams, captions and `FIGURE-INDEX.md` agree.

## 8. Research claims and validation boundaries

WE-SIO proposes that perspective-aware indexing, accountable residuals and bounded structural intelligence **may** improve some workloads and research workflows. It does **not** currently establish that:

- WE-HDT outperforms k-d trees, spatial indexes or database engines on general workloads;
- variable-size blocks guarantee better complexity or recall;
- generated metrics correspond to genuine scientific mechanisms;
- multi-agent consensus creates independent evidence;
- CDE is universally superior to established search or optimization methods;
- self-modeling entails consciousness, subjective experience or autonomous agency.

### 8.1 Validation priorities

**P0 — Semantic correctness:** typed perspective descriptors, identity separation, exactness guarantees, delta consistency, cycle policies and provenance.

**P1 — Controlled baselines:** k-d tree and brute-force comparisons, index update workloads, multi-perspective ablations, resource cost and reproducibility.

**P2 — Discovery and learning:** residual-driven hypothesis quality, independent holdout validation, false discovery control, agent diversity, calibrated self-modeling and relay transfer.

Negative results, failed hypotheses and contradictory cases must be retained as first-class research assets.

## 9. How to participate in Collective Learning

Contributions are welcome in the form of precise counterexamples, alternative definitions, specification clarifications, test cases, baseline implementations, benchmark protocols, replications, or well-supported criticism. A useful relay contribution should include:

1. **Claim or gap:** the exact definition, hypothesis, contract or residual being addressed.
2. **Reproducible setup:** data and code versions, assumptions, constraints and environment.
3. **Evidence:** positive and negative results, uncertainty, provenance and independent checks.
4. **Decision:** support, refute, narrow, split, defer or supersede the claim.
5. **Leftover:** what remains unexplained, untested or disputed.

This process is designed to make research **cumulative without treating every prior hypothesis as settled fact**.

## 10. Suggested reading paths

**New readers:** this README → `START-HERE.md` → WE-SIO-001 → WE-SIO-002 → WE-SIO-003 → WE-SIO-006 → WE-SIO-007.

**Engineers:** SPEC-001 → SPEC-002 → SPEC-003 → CASE-001 → CASE-002 → `VALIDATION-ROADMAP.md`.

**Scientific discovery researchers:** WE-SIO-007 → WE-SIO-008 → EXT-003 → CASE-003 → hypothesis and counterexample registries.

**SIF / CDE researchers:** WE-SIO-009 → CASE-004 → EXT-001 → decision and definition registries.

**Self-modeling / SSI researchers:** WE-SIO-010 → CASE-005 → EXT-004 → unresolved residuals.

## 11. Release and citation

**Target release:** v0.1.0, research-framework publication. DOI should be added **only after** a real archival release has received one. Do not insert a placeholder DOI as though it were registered.

Suggested citation until an archival record is available:

> Tan, S., & GPT-Obot. (2026). *World Entity and Structural Intelligence Operations: From Variable-Size Block Indexing to Open-Ended World Modeling, Metric Discovery, and Self-Referential Intelligence* (v0.1.0). Research framework. GitHub repository: `sizhet/World-Entity-and-Structural-Intelligence-Operations` (repository URL and release to be verified before publication).

**License:** Apache-2.0 is the intended repository license; confirm that a complete `LICENSE` file is included before publishing. Citation and Zenodo metadata must match the actual release and author attribution.

## 12. Explicit leftovers

1. A formal, implementation-independent WE-HDT definition and exactness theorem remain open.
2. Comparative indexing benefits have not been established by controlled benchmarks.
3. Adaptive partitioning and intelligence allocation need cost-aware stability criteria.
4. Cross-perspective composition requires more precise type and evidence semantics.
5. Residual-to-hypothesis generation needs independent empirical evaluation.
6. The minimal distinguishing contribution of CDE beyond generic state-transition search needs clarification.
7. Collective Learning needs provenance-aware evidence independence and transfer metrics.
8. Self-modeling needs calibrated behavioral evaluation; subjective experience remains unresolved.
9. Definition Evolution needs regression and governance procedures demonstrated in practice.
10. Release assets, including ten individual figure PNGs, need final repository-level integrity checks.

For detailed items and tracking, consult [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md).

---

**WE-SIO research principle:** *Answers should remain accountable, questions should remain generative, and unresolved evidence should remain visible.*
