# Origin and Research Questions

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Collective Learning Relay  
**Research record date:** 2026-11-05  
**Status:** Exploratory; hypotheses and architecture proposals, not validated results  
**Authors / research dialogue:** Sizhe Tan and GPT-Obot

## 1. Purpose of This Record

This document preserves the origin, motivating questions, conceptual decisions, objections, and unresolved work of WE-SIO. It is a **relay piece**, not a claim that a complete World Entity theory or executable implementation already exists. Subsequent research should be able to distinguish an initial conjecture from a later refinement, reproduce the reasoning behind a decision, and reopen unresolved questions without losing their provenance.

## 2. Initial Trigger: Revisiting Variable-Size Blocks

The initiating question was whether the earlier **Variable-Size Blocks Index and Search** idea could be extended beyond its original indexing and search role. Its proposed simplicity and potential advantages over k-d trees motivated reconsideration; **no universal performance superiority is established here**. Benchmarking must specify dimensionality, data distribution, query workload, updates, memory, and accuracy.

The first proposed abstraction was:

```text
World Entity (WE) := Object[metricIdx]
```

This notation is retained as the **initial computational representation hypothesis**, not an exhaustive ontological definition of a real-world entity. An entity may exist independently of our ability to identify, measure, or index it.

## 3. Initial WE-HDT Proposal

The initiating architecture proposed a **World Entity Hybrid Differential Tree (WE-HDT)**:

1. **Euclidean Differential Tree:** an efficient lower-level localization and search structure, potentially using Variable-Size Blocks and two-phase search.
2. **Metric Differential Tree:** richer perspective-specific interpretation and computation associated with Euclidean nodes or leaves.
3. **Remaining perspective indices:** information not sufficiently represented by the selected Euclidean coordinates, including relationships, partial observations, unexplained variation, and candidate unknown dimensions.

The original intuition was that Euclidean coordinates provide computationally tractable anchors, while richer structures capture what simple coordinates cannot. This remains a **candidate architecture**, not a universal hierarchy: some entities and questions have no meaningful Euclidean anchor, and shared relational structures may cross multiple leaves.

A further distinction is required between an **indexing hierarchy** (physical or logical access paths) and an **intelligence abstraction hierarchy** (levels of explanation, hypothesis, and reasoning). These need not be identical.

## 4. Key Conceptual Refinements from the Initial Discussion

### 4.1 Metric is not synonymous with unknown

A non-Euclidean relation can be fully known; an ordinary spatial coordinate can be unknown. Representation type and epistemic status must be modeled separately. Also, similarity, causality, trust, preference, and directional scores do not automatically satisfy the mathematical axioms of a metric. The broader working category is **Metric and Relational Perspectives**, with explicit conformance rules.

### 4.2 From variable-size blocks to variable-intelligence blocks

The proposed **Perspective-Adaptive Variable Blocks (PAVB)** idea allows block granularity and attached intelligence resources to respond to density, heterogeneity, uncertainty, task relevance, and computation cost. A block might contain only an index, a differential subtree, or richer multi-perspective intelligence. This is a hypothesis requiring comparison against conventional adaptive indexing and query optimization.

### 4.3 Metric Leaf Intelligence Unit (MLIU)

A proposed MLIU may retain entity and perspective references, observations, hypotheses, evidence, uncertainty, residuals, questions, provenance, versions, and relay interfaces. Candidate operations include **Locate, Resolve, Relate, Infer, Question, Evolve**. It need not be a standalone agent: shared services and lazy activation may be preferable.

### 4.4 SQL columns as an engineering entry point

A SQL row can map to an entity representation; columns can map to candidate attribute or perspective descriptors; keys and joins can help express identity and relationships. A SQL column is **not necessarily a mathematical metric**, and a database index is not the same as a WE perspective descriptor. WE-SIO should build on database technology rather than presume to replace it.

### 4.5 Two-Ways CCC across perspectives

A proposed extension moves from efficient explicit/Euclidean candidate localization to metric or relational comparison, residual detection, and reverse feedback that revises candidate metrics or search conditions. This **Cross-Metric Discovery Loop** is a research hypothesis, not a demonstrated discovery algorithm.

### 4.6 Residual as a first-class research object

Residuals, weak evidence, counterexamples, and unexplained observations should be preserved with provenance, uncertainty, and validation status. They may trigger questions, new perspectives, or alternative explanations. A residual is **not automatically evidence of a new mechanism**; noise, measurement error, confounding, and selection effects remain plausible.

### 4.7 World change versus knowledge change

**World Delta** denotes changes in the modeled entity or environment; **Epistemic Delta** denotes changes in the observer's representation or knowledge. These can occur independently and must not be conflated.

### 4.8 From WE to a model of “I”

A self-modeling entity can represent itself, act, observe consequences, and revise its self-model. This creates a research bridge to Subjective Structural Intelligence (SSI), identity continuity, and multi-perspective self-description. **Self-reference and feedback do not by themselves establish consciousness or subjective experience.**

## 5. Methodological Discovery: Define the Invariant, Not the Inventory

A major outcome of the discussion was recognizing the difficulty of defining universal frameworks before their application boundaries are known. The proposed approach is:

- **Minimal semantic kernel:** state only the essential common mechanism.
- **Conformance contracts:** specify conditions under which an instance belongs to the framework.
- **Open extensions:** place domain-specific rules outside the kernel.
- **Counterexample-driven refinement:** seek cases that challenge supposed universal conditions.
- **Versioned definition evolution:** preserve previous definitions and reasons for changes.
- **Nontriviality and operational tests:** ensure that generalization offers discriminating power and practical or explanatory gain.

This was summarized as **“Define the invariant, not the inventory.”**

### CDE boundary stress test: chess

Chess was proposed as a candidate application of **Constrained Delta Evolution (CDE)**. It immediately challenged assumptions carried over from Dynamic Bucket Tree of Permutation (D-BTP): adversarial turns, cycles, and legitimate repeated moves or states mean **No-Delta-Reuse cannot be a universal CDE axiom**. It is better treated as an optional path-policy constraint. The distinction between a minimal transition kernel, constraint policies, evolution/search policies, and application contracts should remain explicit.

This case is retained because it demonstrates how a counterexample can improve the *definition* of a framework, not merely add an implementation feature.

## 6. Research Questions

The questions below are deliberately open. IDs are stable handles for future discussion, hypotheses, experiments, and relay contributions.

### A. Representation and identity

- **RQ-001:** What is the minimal semantic definition of a World Entity, distinct from its computational representation?
- **RQ-002:** What must an `Object[metricIdx]` descriptor specify to distinguish attributes, mathematical metrics, directional scores, and relations?
- **RQ-003:** How should Entity Identity, Perspective Identity, observation time, and provenance be separated?
- **RQ-004:** When does a Euclidean-first search plan help, and when should relational or other backends be primary?
- **RQ-005:** How should the indexing hierarchy relate to, but remain independent from, the intelligence abstraction hierarchy?

### B. Indexing and structural computation

- **RQ-006:** Under which workloads do Variable-Size Blocks outperform, match, or underperform k-d trees and other index families?
- **RQ-007:** Which measurable signals justify splitting, merging, or enriching an adaptive block?
- **RQ-008:** What is the smallest interoperable contract for an MLIU, and which operations must be lazy or shared?
- **RQ-009:** How can cross-leaf references, shared relations, and updates be maintained without uncontrolled complexity?

### C. Discovery and evidence

- **RQ-010:** How can Two-Ways CCC perform bidirectional cross-metric candidate generation without conflating similarity with causality?
- **RQ-011:** What is the minimal record and lifecycle of a Residual, including alternative explanations and validation evidence?
- **RQ-012:** Can residual clusters justify proposing new metrics, relational predicates, or perspective dimensions, and how should candidates be tested?
- **RQ-013:** How can independent validation, uncertainty calibration, and safeguards against overfitting be integrated into the discovery loop?
- **RQ-014:** In biomedical use cases, what data governance, privacy, bias, and clinical validation requirements bound acceptable claims?

### D. Evolution, self-modeling, and collective learning

- **RQ-015:** What operations distinguish World Delta from Epistemic Delta, and what provenance is needed to reconcile them?
- **RQ-016:** How can CDE govern structural changes to indices, metrics, schemas, and research definitions while preserving conformance?
- **RQ-017:** What minimum self-reference, action-feedback, and history structures are needed for a functional self-model?
- **RQ-018:** How should competing perspectives about one entity be compared without erasing disagreement or weak evidence?
- **RQ-019:** What can be relayed across SI units or research groups without falsely promoting unverified hypotheses to facts?
- **RQ-020:** Which counterexamples would force WE-SIO's kernel to shrink, split, or be abandoned?

## 7. Proposed Evaluation and Falsification Directions

1. **Index benchmark:** compare Variable-Size Blocks with k-d trees and suitable alternatives on synthetic and representative workloads; report latency, memory, updates, accuracy, and failure cases.
2. **Representation conformance:** test known Euclidean, non-Euclidean metric, non-metric relational, and missing-data cases against descriptor contracts.
3. **Cross-metric discovery:** compare fixed-metric baselines with candidate-generation and feedback variants on held-out data; track false discoveries and compute cost.
4. **Residual lifecycle:** test whether provenance-preserving residual records improve reproducibility and useful follow-up question generation.
5. **Definition stress tests:** use chess/CDE and other boundary cases to expose overbroad axioms and document the revision process.
6. **Self-model limits:** test functional prediction and feedback behavior while explicitly avoiding claims about consciousness.

## 8. Explicit Non-Claims and Scope Limits

- WE-SIO is not yet a complete ontology of reality.
- `Object[metricIdx]` is a proposed access/representation abstraction, not the entity itself.
- WE-HDT is not demonstrated to be optimal for all domains.
- Variable-Size Blocks are not established as universally superior to k-d trees.
- Non-Euclidean and relational data are not inherently unknown.
- Residuals are not automatically discoveries, and weak evidence is not established truth.
- Medical examples motivate research and do not support clinical recommendations or efficacy claims.
- A self-model is not proof of subjective consciousness.
- CDE applicability to chess does not validate every CDE generalization.

## 9. Relay Interfaces and Follow-On Artifacts

This origin record should be cross-linked to:

- `research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md` — detailed synthesis of the initiating discussion.
- `research-trace/DEFINITION-REGISTRY.md` — versioned terms and semantic commitments.
- `research-trace/HYPOTHESIS-REGISTRY.md` — testable conjectures and status.
- `research-trace/COUNTEREXAMPLE-REGISTRY.md` — stress tests and invalidated assumptions.
- `research-trace/DECISION-LOG.md` — why a choice was made or revised.
- `research-trace/UNRESOLVED-RESIDUALS.md` — explicit unanswered questions and leftovers.
- `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md` — methodological development.
- `specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md` — proposed conformance interface.

The linked files are **planned artifacts**; listing them here does not imply that they have already been authored or validated.

## 10. Next Research Sequence

1. Fix terminology and definition status without prematurely closing boundaries.
2. Develop the minimal-kernel and definition-evolution methodology.
3. Specify WE identity, perspective descriptors, and WE-HDT contracts.
4. Build concrete cases and counterexamples before claiming generality.
5. Evaluate indexing, cross-metric discovery, and residual handling with explicit baselines.
6. Record supported findings, failures, and remaining unknowns as reusable relay pieces.

## 11. Closing Principle

> Preserve not only what we know, but also how we arrived there, what challenged it, and what remains unknown.

**Unknown is not zero. Unexplained is not useless. Residual is not necessarily noise.** Equally, **a residual is evidence of an explanatory gap, not automatically evidence of a new law.**

This document is the starting point of an open research program. Its purpose is to enable critical continuation, not to freeze a provisional theory.
