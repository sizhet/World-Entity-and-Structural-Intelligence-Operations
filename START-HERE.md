# START HERE — World Entity and Structural Intelligence Operations (WE-SIO)

**Version:** v0.1.0 (research framework)  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Hypotheses and architectural contracts; not a validated production implementation  
**Repository:** `World-Entity-and-Structural-Intelligence-Operations`

> **Central idea:** A world entity can be addressed through multiple typed perspectives, investigated through accountable evidence, and refined through residual-driven structural intelligence—without confusing its identity with an index, a metric, or a model.

## 1. What problem does WE-SIO address?

Conventional indexes answer a bounded question: *Where can a matching record be found?* WE-SIO asks a wider set of questions:

- What is the entity to which a record, observation, or relation refers?
- Which perspectives are appropriate for locating, comparing, and explaining it?
- Which answers are supported by evidence, and what remains unresolved?
- Can an unexplained residual trigger a testable question or a candidate new perspective?
- Can the system revise its structures and definitions while preserving provenance and conformance?

WE-SIO is a **research architecture**, not a claim that a single universal index can answer every query. Its proposed value is the composition of explicit entity semantics, typed perspectives, adaptive localization, local intelligence operations, and verifiable research relay.

## 2. The path from variable-size blocks to world entities

The motivating path is:

```text
Variable-Size Blocks (VSB)
  → Two-Phase Search: candidate localization → resolution
  → Perspective-aware indexing and differential structures (WE-HDT)
  → World Entity (WE): identity + perspectives + evidence + relations
  → Adaptive Variable-Intelligence Blocks (AVIB) and MLIU
  → Two-Ways CCC: answer forward, question backward
  → Residual-driven hypothesis and perspective discovery
  → CDE / Definition Evolution / Collective Learning Relay
```

The initial shorthand `Object[metricIdx]` is useful as a research prompt, **not** a complete formal definition. A world entity is not reducible to its metric index. Nor must every entity have Euclidean coordinates or every perspective satisfy mathematical metric axioms.

## 3. Seven concepts to learn first

| Concept | Working meaning | Important boundary |
|---|---|---|
| **World Entity (WE)** | Referent with identity, typed perspectives, relations, and evidence | Entity identity is not a row key or similarity score |
| **Perspective** | Typed way to observe, measure, compare, or relate an entity | Not every numeric attribute is a metric |
| **WE-HDT** | Proposed hybrid differential organization for candidate localization and perspective-aware resolution | Euclidean-first is optional, not universal |
| **PAVB / AVIB** | Adaptive block partitioning / adaptive intelligence allocation | Block size and intelligence budget are independent axes |
| **MLIU** | Metric Leaf Intelligence Unit: a contract for leaf-level operations and evidence | A logical leaf need not host a heavyweight autonomous agent |
| **Two-Ways CCC** | Forward answering plus backward questioning from residuals | Candidate explanations require independent validation |
| **CDE** | Constrained Delta Evolution for evolving states and structures | No-Delta-Reuse is application-specific, not a universal axiom |

### The six MLIU operations

`Locate → Resolve → Relate → Infer → Question → Evolve` describes a possible operational repertoire, **not** a mandatory execution order. Every operation should declare input types, outputs, evidence, uncertainty, version, and resource budget.

## 4. Read the repository in four passes

### Pass A — The shortest conceptual route (about 30–60 minutes)

1. [`README.md`](README.md) — scope, architecture, and navigation.
2. [`docs/WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md`](docs/WE-SIO-001-From-Variable-Size-Blocks-to-World-Entity.md) — origin and generalization.
3. [`docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`](docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md) — localization proposal.
4. [`docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`](docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md) — forward/backward intelligence loop.
5. [`docs/WE-SIO-007-Residual-First-Scientific-Discovery.md`](docs/WE-SIO-007-Residual-First-Scientific-Discovery.md) — evidence-based discovery.

### Pass B — Check semantics and engineering contracts

Read [`docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`](docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md), then the six `specs/SPEC-001` through `SPEC-006` documents. Prioritize **identity vs. representation**, **metric vs. similarity**, **candidate recall**, **provenance**, **delta typing**, and **versioned conformance**.

### Pass C — Stress-test the ideas against cases

| Case | Question to ask |
|---|---|
| [`CASE-001`](cases/CASE-001-SQL-Columns-to-WE-Perspective-Indices.md) | When does a SQL column constitute a perspective, and when does it not? |
| [`CASE-002`](cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md) | Can VSB/PAVB beat a fair k-d tree baseline on defined workloads? |
| [`CASE-003`](cases/CASE-003-Clinical-Treatment-Response-Residuals.md) | How do we distinguish residual patterns from confounding and noise? |
| [`CASE-004`](cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md) | Which CDE constraints fail when legal state repetition is allowed? |
| [`CASE-005`](cases/CASE-005-Multi-Perspective-Self-Modeling-Entity.md) | Can a self-model improve calibration without implying consciousness? |

Clinical examples are research illustrations, **not** medical advice or clinically validated tools.

### Pass D — Connect to the wider SI ecosystem

- [`EXT-001`](extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md): WE-HDT and CDE as complementary candidate **SIF Localization / Addressing** methods.
- [`EXT-002`](extensions/EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md): multi-agent collaboration, adversarial checking, and relay.
- [`EXT-003`](extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md): residuals, AQSI, candidate metric generation, and validation gates.
- [`EXT-004`](extensions/EXT-004-Self-Referential-World-Entity-and-Subjective-SI.md): self-reference and interfaces with SSI, without consciousness claims.
- [`EXT-005`](extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md): Mask-First Structural Intelligence and Epistemic Separation.
- [`EXT-006`](extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md): SQL-Native Structural Intelligence and Knowledge Evolution.

## 5. The architecture at a glance

```text
                  Questions / tasks / observations
                               |
                     SIF Control Plane
                               |
                 Typed World Entity contracts
                               |
             +-----------------+-----------------+
             |                 |                 |
      WE-HDT localization   MLIU operations   Evidence / residual registry
             |                 |                 |
             +---------- Two-Ways CCC -----------+
                          /          \
                    Forward answer   Backward question
                          \          /
                  Validation and conformance
                               |
                   CDE / Definition Evolution
                               |
                 Collective Learning Relay
```

**Two different axes must not be collapsed:** WE-HDT principally addresses *which entities, perspectives, and evidence to inspect*; CDE principally addresses *which admissible state/structural deltas to explore*. Their coordination is proposed; empirical benefits remain unverified.

## 6. What is a residual here?

A **residual** is a documented mismatch between a declared expectation and an observation, with context and uncertainty. It can indicate measurement error, model misspecification, confounding, incomplete data, or a genuinely missing mechanism.

```text
Expectation + observation
        ↓
Typed residual record + data-quality checks
        ↓
Candidate question / explanation / perspective
        ↓
Independent tests + counterexamples
        ↓
Accept, reject, narrow, defer, or revise
        ↓
Versioned research trace and relay
```

**A residual is evidence of a gap, not automatically evidence of a new scientific law.** An unexplained result is neither a zero nor proof of novelty.

## 7. Research claims versus demonstrated results

At v0.1.0, the following are **proposals to test**, not established results:

- WE-HDT offers a useful general interface for multi-perspective localization.
- Adaptive block partitioning and intelligence allocation can improve workload-dependent efficiency.
- Two-Ways CCC improves question generation or error discovery over controlled baselines.
- Residual-first workflows improve valid discovery rather than merely producing more hypotheses.
- Multi-agent relay yields transferable, independently supported knowledge gains.
- Self-modeling improves calibration or bounded self-improvement.

The repository does **not** claim a proven universal index, demonstrated AGI, scientific discovery without external validation, or evidence of subjective experience.

## 8. First reproducible experiments

A practical implementation sequence is:

1. **Entity contract:** build synthetic entities with distinct source record IDs, canonical entity references, and versioned evidence.
2. **Typed perspectives:** implement Euclidean metric, categorical similarity, and directed relation as distinct contracts.
3. **Localization baselines:** compare brute-force exact search, k-d tree, fixed blocks, and candidate WE-HDT/VSB strategies under identical workloads.
4. **Correctness first:** test exact candidate recall, update consistency, false merges, and stale-version detection before performance claims.
5. **Residual tests:** inject known missing variables, noise, confounding, and corrupted observations; measure which explanations survive independent tests.
6. **Agent ablation:** compare single-agent, parallel, adversarial, and relay workflows with controlled budgets and evidence dependence.
7. **CDE boundary tests:** use chess-like cyclic state spaces to ensure policies are application-specific and do not erase legal paths.

Report datasets, splits, seeds, hardware, code revisions, baselines, failures, uncertainty intervals, and all prespecified evaluation metrics. **No benchmark result is implied by this roadmap.**

## 9. How to contribute a rigorous research relay

Use the following minimal packet:

```yaml
relay_id: RELAY-<unique-id>
source_claim: WEH-<hypothesis-id>
source_version: v0.1.0
artifact_type: hypothesis | counterexample | experiment | definition_revision
input_contracts: []
method_and_baselines: []
evidence_and_provenance: []
uncertainty_and_limitations: []
independent_validation: pending
result: proposed | supported | refuted | inconclusive
explicit_leftovers: []
next_relay_question: ""
```

The packet should link to the appropriate registries in `research-trace/`. Agreement among multiple agents is **not** independent corroboration when their evidence or failure modes are correlated. Repeated execution can become a valuable relay **only when its results and conditions are preserved**.

## 10. Where definitions, hypotheses, and decisions live

| File | Why it matters |
|---|---|
| [`research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md`](research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md) | Original problem framing and research questions |
| [`research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md`](research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md) | Synthesized evolution of the research ideas |
| [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md) | Falsifiable claims and proposed evidence gates |
| [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md) | Versioned terms, invariants, and boundaries |
| [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md) | Challenges, negative cases, and regression targets |
| [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md) | Rationale, alternatives, and revision triggers |
| [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md) | Unanswered gaps and next validation tasks |

For an overview of the full paper sequence, consult [`CONTENTS.md`](CONTENTS.md); for terminology, [`GLOSSARY.md`](GLOSSARY.md); for proposed empirical work, [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md) and [`VALIDATION-ROADMAP.md`](VALIDATION-ROADMAP.md).

## 11. Visual route

The `figures/` series is:

1. `Fig-001-WE-SIO-Grand-Architecture.png`
2. `Fig-002-From-Variable-Size-Blocks-to-World-Entity.png`
3. `Fig-003-WE-Hybrid-Differential-Tree.png`
4. `Fig-004-Adaptive-Variable-Intelligence-Blocks.png`
5. `Fig-005-Metric-Leaf-Intelligence-Unit.png`
6. `Fig-006-Two-Ways-CCC-Cross-Metric-Discovery.png`
7. `Fig-007-Residual-Driven-Scientific-Discovery-Loop.png`
8. `Fig-008-World-Delta-vs-Epistemic-Delta.png`
9. `Fig-009-Definition-Evolution-Loop.png`
10. `Fig-010-From-WE-to-Self-Modeling-Entity-and-Collective-Relay.png`

**Publication check:** confirm that each named PNG exists as an independent, legible image and that every figure reference resolves. A composite overview does not automatically satisfy ten separate file paths.

## 12. Frequent misunderstandings

**Is WE-SIO a replacement for SQL, k-d trees, or vector databases?**  
No. Those are important baselines and may remain underlying implementations. WE-SIO proposes additional semantic and research interfaces.

**Does every perspective have a numerical distance?**  
No. Relations, observations, similarities, and true metrics have different algebraic contracts.

**Is the World Entity's identity learned from similarity?**  
Not by default. Identity resolution requires its own evidence and conflict policy.

**Does every metric leaf need an LLM?**  
No. MLIU is an interface for bounded intelligence operations; lightweight deterministic methods may suffice.

**Is self-modeling equivalent to subjective consciousness?**  
No. The framework studies functional self-reference and explicitly leaves subjective experience unresolved.

**Does CDE forbid repeating a delta?**  
Not universally. Path-memory and cycle restrictions are chosen for a particular domain; chess supplies counterexamples to universal no-reuse.

## 13. Open problems worth taking first

- Define formal conditions for complete candidate localization across mixed perspectives.
- Separate index update cost from intelligence-update cost in adaptive blocks.
- Establish when a proposed perspective qualifies as a mathematical metric.
- Demonstrate discovery gains against data leakage and multiple-testing effects.
- Define measurable structural-intelligence gains beyond ordinary state transition search.
- Evaluate how collective learning handles correlated errors and negative evidence.
- Establish robust self-model calibration without unsupported claims of subjectivity.

See `OPEN-QUESTIONS.md` and `research-trace/UNRESOLVED-RESIDUALS.md` for the expanded backlog.

## 14. Research and publication conventions

- **Specifications and contracts before runtime.**
- **Conformance before performance.**
- **Counterexamples before broad claims.**
- **Independent validation before promotion.**
- **Explicit leftovers before declaring closure.**
- **Traceable collective learning rather than undocumented consensus.**

The intended repository license is **Apache-2.0**; verify that the actual `LICENSE`, `CITATION.cff`, `.zenodo.json`, release notes, and repository links are present and consistent before publication. A DOI should only be cited once assigned.

---

**Suggested next step:** read `WE-SIO-001`, then `WE-SIO-003` and `WE-SIO-006`; choose one counterexample, specify a baseline, and contribute a reproducible relay packet. The project grows through tested corrections as much as through new ideas.
