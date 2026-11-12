# WE-SIO-011 — Minimal Kernel, Contracts, and Definition Evolution

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Collective Learning Relay  
**Date:** 2026-11-05  
**Status:** Exploratory methodological proposal; not a validated universal theory  
**Authors / research dialogue:** Sizhe Tan and GPT-Obot  
**Companion record:** [`../research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md`](../research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md)

## Abstract

Research frameworks that aim for broad applicability face a recurrent difficulty: their precise definitions, admissible operations, and application boundaries cannot usually be enumerated at inception. New cases reveal previously unnoticed constraints, while counterexamples may invalidate assumptions mistaken for universal laws. WE-SIO proposes a disciplined response: specify a **minimal semantic kernel**, make domain-specific behavior explicit through **contracts and extensions**, and treat **definition evolution** as a versioned, evidence-driven research process. This paper develops the method, distinguishes formal precision from completeness, and illustrates its use in World Entity modeling, WE-HDT, and Constrained Delta Evolution (CDE). Chess supplies a boundary stress test: adversarial decisions, repeated positions, and legally repeated moves challenge a blanket prohibition on Delta reuse. The resulting approach preserves provenance, counterexamples, residuals, and unresolved questions as first-class Collective Learning relay assets. The framework is a research proposal; its practical benefits require comparison with established formal specification, type systems, scientific model revision, and software evolution methods.

## 1. The Problem: Generality Before Enumeration

A research project often begins with a small number of concrete examples and an ambitious generalization. In WE-SIO, an indexing idea—Variable-Size Blocks Index and Search—motivated a representation hypothesis:

```text
World Entity (WE) := Object[metricIdx]
```

In CDE, dynamic search and constrained state transformations motivated a general account of Delta evolution. Neither starting point determines all future entity types, index semantics, transition policies, or application domains. Attempting exhaustive enumeration at the outset creates two symmetric risks:

1. **Premature closure:** a narrow inventory excludes valid but not-yet-imagined cases.
2. **Vacuous universality:** an overbroad definition accepts virtually anything and ceases to discriminate or predict.

A third risk is **definition drift**: a familiar term quietly changes meaning across papers, specifications, and implementations. WE-SIO therefore needs a way to grow without losing traceability.

### 1.1 Central thesis

> **Define the invariant, not the inventory.**

Here *invariant* is used broadly for a stable semantic obligation or structural commitment across conforming instances; it need not denote a mathematically conserved numerical quantity. This principle does **not** eliminate examples. It changes their role: examples test the kernel and illustrate contracts, rather than defining the universe by enumeration.

### 1.2 Precision is not completeness

A definition may be **precise within its stated scope** and **incomplete with respect to future domains**. Precision requires explicit terms, preconditions, and falsifiable or checkable implications. Completeness would require anticipating every legitimate application. WE-SIO demands the former, not the latter.

## 2. Three Layers of Definition

The proposed separation is:

| Layer | Question answered | Stability expectation | Typical artifact |
|---|---|---|---|
| **Minimal Semantic Kernel** | What must every conforming instance mean or do? | Conservative, explicitly versioned | Kernel definition and invariants |
| **Operational Contracts** | Under which conditions is a particular operation valid? | Evolves with tested capabilities | Types, pre/postconditions, evidence obligations |
| **Open Extensions** | What specialized policies, models, or representations are added? | Expected to diversify | Domain profiles, plugins, experimental modules |

A **research claim** is separate from all three. Implementing an extension does not validate a scientific claim about it.

### 2.1 Admission by conformance, not resemblance

A new application belongs to a framework only if it satisfies the declared semantic and operational obligations. Similar vocabulary is insufficient. Calling a graph rewrite a “Delta,” for example, does not establish CDE conformance unless its state, applicability, constraints, transition semantics, and evolution policy can be specified.

### 2.2 The nontriviality requirement

A useful kernel must reject some candidates. A definition that accepts every imaginable process without further obligations is merely a renaming of “process.” Each kernel revision should document both **positive witnesses** (accepted cases) and **negative witnesses** (excluded cases).

## 3. A Candidate WE-SIO Minimal Kernel

WE-SIO must distinguish an entity in the world from the system's representation of that entity.

Let:

- $e$ denote a referent or hypothesized world entity;
- $p$ denote a perspective, observer, or interpretive context;
- $t$ denote a time or version context;
- $R(e,p,t)$ denote a **representation** of $e$, not the entity itself;
- $I$ denote a collection of typed perspective descriptors;
- $E$ denote evidence and provenance;
- $U$ denote uncertainty or unresolved status.

A working representation schema is:

$$
R(e,p,t)=(id_e,p,t,I,E,U,links).
$$

The earlier `Object[metricIdx]` remains a compact notation for an indexed view of this representation. The following are **candidate kernel obligations**, subject to refinement:

**WE-K1 — Referent/representation separation.** A change in knowledge must not be silently equated with a change in the referent.

**WE-K2 — Explicit identity semantics.** Entity identity, descriptor equality, and similarity are distinct; unresolved identity is representable.

**WE-K3 — Typed perspective descriptors.** Every descriptor declares its domain and supported operations. Numeric data alone do not establish Euclidean or metric validity.

**WE-K4 — Traceable assertions.** Claims may carry source, time, perspective, confidence/uncertainty, and validation status; unsupported claims must not be promoted silently to facts.

**WE-K5 — Extensible representation.** The descriptor set may evolve through explicit, versioned changes without presuming that all future dimensions are enumerable.

**WE-K6 — Residual preservation.** An unresolved discrepancy may be recorded and revisited; it is not automatically noise, nor automatically evidence of a new mechanism.

These obligations describe an initial **representation-and-research kernel**, not a proof that every real-world entity is indexable. A WE-HDT is one possible backend; it is not a required property of all entities.

## 4. Contracts for Indexing, Reasoning, and Evolution

A contract should specify at least:

```text
Contract {
  id, version, purpose
  accepted_input_types
  preconditions
  operation_semantics
  postconditions
  invariants
  failure_and_unknown_states
  evidence_and_provenance_requirements
  resource_or_termination_policy
  conformance_tests
  known_limitations
}
```

### 4.1 Perspective descriptor contract

A descriptor may expose `equality`, `ordering`, `distance`, `similarity`, `directional_score`, or `relation_query`, but **none is inferred merely from column type**. A mathematical metric requires non-negativity, identity of indiscernibles, symmetry, and the triangle inequality. Other comparisons must declare their actual properties. The category *Remaining Metric and Relational Perspectives (RMRP)* avoids forcing every relationship into a metric space.

### 4.2 WE-HDT indexing contract

An indexing backend must specify its domain, supported queries, correctness criterion (exact or approximate), update semantics, and cost model. Euclidean-first localization is an **optional optimization strategy**; some domains have no valid Euclidean anchor. The indexing hierarchy and intelligence abstraction hierarchy must remain distinguishable.

### 4.3 Metric Leaf Intelligence Unit (MLIU) contract

An MLIU may expose `Locate`, `Resolve`, `Relate`, `Infer`, `Question`, and `Evolve`, but each operation must define inputs, outputs, evidence status, and failure modes. An MLIU need not instantiate a dedicated agent; shared services and lazy evaluation are permitted implementation profiles.

### 4.4 Residual contract

A residual record should distinguish expectation, observation, discrepancy, model/perspective, source, and validation state. It should also permit non-numeric structural disagreements. The system must distinguish **hypothesis generation** from **independent confirmation** to limit overfitting and false discovery.

## 5. CDE as a Boundary Stress Test

A minimal deterministic transition can be expressed as a partial function:

$$
\delta_C:S\rightharpoonup S',
$$

where the constraints $C$ determine admissibility. This notation is a useful starting point, not a complete CDE definition. For nondeterministic or multi-result systems, a transition relation is more appropriate:

$$
T_C\subseteq S\times A\times S.
$$

Here $A$ is a set of candidate actions or Deltas. A distinctive CDE profile must add meaningful obligations for constrained Delta generation, admissibility, path/history management, branch control, and evolution; otherwise it collapses into an ordinary state-transition system.

### 5.1 Why chess matters

Chess challenges assumptions that may have been convenient in D-BTP-style search:

- **Adversarial agency:** the next action may be chosen by an opponent with an opposing objective.
- **Cycles:** positions and move patterns may recur; a search policy must decide how to handle repetition.
- **Repeated Deltas:** an action type or move can recur legally; a blanket `No-Delta-Reuse` prohibition is not universal.
- **History-dependent legality/outcomes:** the same piece arrangement need not encode every relevant game-state rule; turn, rights, counters, and history may matter.

Thus:

```text
No-Delta-Reuse: optional PathPolicy, not universal CDE axiom.
```

Possible application profiles include `AcyclicSearch`, `HistoryAwareSearch`, `AdversarialAlternatingTurn`, and `BoundedRepetition`. These names are proposals, not implemented modules. For chess, actual rule compliance requires a game-specific legal-move and terminal-state contract; search truncation is separate from a game's terminal rules.

### 5.2 Core revision or extension?

When a counterexample appears, ask:

1. Does it contradict a genuinely universal kernel obligation?
2. Was the disputed rule actually domain-specific?
3. Can a new contract profile express the case without changing existing meanings?
4. Does the extension preserve nontriviality and testability?
5. What previously accepted cases must be rechecked?

Moving No-Delta-Reuse into an optional path policy is a **boundary correction**, not an admission that every rule is arbitrary.

## 6. Definition Evolution Loop (DEL)

A research definition is represented as a versioned object:

$$
D_t=(K_t,C_t,X_t,W_t,N_t),
$$

where $K$ is the kernel, $C$ contracts, $X$ extensions, $W$ positive/negative witnesses and evidence, and $N$ unresolved questions and residuals. A proposed change $\Delta D_t$ is evaluated before adoption:

$$
D_{t+1}=\mathrm{AcceptRevision}(D_t,\Delta D_t,Tests,Review).
$$

This notation is procedural, not an assertion that theory evolution is automatically computable or guaranteed to converge.

### 6.1 Proposed workflow

1. **Propose:** state a minimal definition and scope explicitly.
2. **Instantiate:** collect diverse positive examples and boundary cases.
3. **Attack:** actively seek counterexamples and alternative explanations.
4. **Classify:** distinguish kernel failure, contract omission, extension need, and implementation bug.
5. **Revise:** change only the necessary layer, with migration notes.
6. **Regress:** rerun positive and negative conformance cases.
7. **Relay:** publish the decision, evidence, residuals, and open questions.

A revision may **broaden, narrow, split, or retire** a definition. Growth is not synonymous with monotonic expansion.

### 6.2 Definition change categories

| Category | Meaning | Typical handling |
|---|---|---|
| Clarification | Same semantics, clearer wording | Patch-level documentation |
| Extension | New optional capability | New contract/profile |
| Restriction | Prior accepted cases excluded | Breaking-change review |
| Correction | Previous universal claim falsified | Counterexample-linked revision |
| Split | One concept shown to cover distinct mechanisms | New terms and migration map |
| Deprecation | Concept no longer supported | Preserve historical record |

Semantic versioning is a useful analogy, not a substitute for scientific change records. WE-SIO's repository version `v0.1.0` identifies an exploratory release, not verified implementation stability.

## 7. Evidence, Counterexamples, and Research Trace

A Collective Learning relay must preserve *how* a conclusion was reached. Suggested persistent artifacts:

- [`HYPOTHESIS-REGISTRY.md`](../research-trace/HYPOTHESIS-REGISTRY.md): hypothesis ID, claim, scope, predicted observations, status.
- [`DEFINITION-REGISTRY.md`](../research-trace/DEFINITION-REGISTRY.md): term, version, semantic obligations, changes.
- [`COUNTEREXAMPLE-REGISTRY.md`](../research-trace/COUNTEREXAMPLE-REGISTRY.md): violated claim, minimal witness, reproduction, disposition.
- [`DECISION-LOG.md`](../research-trace/DECISION-LOG.md): alternatives, rationale, reviewers, impact.
- [`UNRESOLVED-RESIDUALS.md`](../research-trace/UNRESOLVED-RESIDUALS.md): unexplained observations, uncertainty, next tests.

A record should identify **claim status**: `Proposed`, `Under Test`, `Supported Within Scope`, `Revised`, `Rejected`, or `Unresolved`. “Supported” must name the tested scope and evidence; it does not mean universally true.

### 7.1 Example decision record

```yaml
id: DEC-WE-SIO-001
question: Is No-Delta-Reuse a universal CDE invariant?
initial_position: Candidate universal path constraint
counterexample: Legal repeated moves and positions in chess
resolution: Reclassify as optional PathPolicy
status: Proposed methodological correction
follow_up: Formalize game-state equivalence and regression cases
```

This is an illustrative record; the corresponding registry and tests remain to be authored.

## 8. Two-Ways CCC and Metric Discovery Under Contract

WE-HDT may support a two-direction research loop:

$$
\text{Known descriptors}\rightarrow\text{candidate matches}\rightarrow\text{residuals}
$$
$$
\text{residuals}\rightarrow\text{candidate new descriptors}\rightarrow\text{new tests}.
$$

A generated “metric” is not automatically a mathematical metric; it may instead be a similarity function, directional score, predicate, or learned representation. Each must declare its properties, domain, training/evaluation separation, and provenance. In medical or scientific applications, candidate associations require independent validation, confounding analysis, and appropriate study design before causal or clinical claims.

**World Delta** (change in referent) and **Epistemic Delta** (change in representation or belief) must remain distinct. New evidence may change a model without changing the world; real-world change may go unobserved. This distinction is essential for auditability and self-modeling.

## 9. Avoiding False Generality: Three Evaluation Gates

**Gate A — Nontriviality.** Does the definition exclude identifiable negative cases? Are its obligations more specific than generic state transition or generic object storage?

**Gate B — Explanatory gain.** Does it make relationships, failure modes, or previously disconnected mechanisms clearer than existing approaches?

**Gate C — Operational gain.** Does it yield measurable improvements in correctness, reproducibility, query quality, resource use, hypothesis generation, or interoperability?

No single gate proves novelty. A fair comparison should include relevant baselines: database indexing and query planning, formal methods, knowledge graphs, Bayesian and active learning methods, anomaly detection, and established search/planning algorithms. Avoid claiming that classical mathematics or physics ignores residuals; the research hypothesis concerns **cross-domain preservation and operational reuse of unresolved evidence**.

## 10. A Minimal Conformance and Validation Plan

| Test | Target | Expected discriminating result |
|---|---|---|
| WE-T01 | Entity vs representation | Knowledge-only update does not imply world-state change |
| WE-T02 | Descriptor semantics | Non-metric similarity is not mislabeled a metric |
| WE-T03 | Index portability | A non-Euclidean domain can bypass Euclidean-first indexing |
| WE-T04 | Identity resolution | Similar attributes do not force entity identity |
| WE-T05 | Residual lifecycle | Unresolved evidence survives model revision with provenance |
| CDE-T01 | Repetition | A legal chess repetition is not rejected by universal No-Reuse |
| CDE-T02 | Adversarial policy | Opponent choice is represented explicitly, not as a single-agent optimization |
| DEL-T01 | Regression | Revised definitions are checked against earlier positive and negative witnesses |
| DEL-T02 | Negative control | At least one plausible but nonconforming candidate is rejected |

These are **test specifications**, not claims that tests have been implemented or passed. Future work should add fixtures, expected outputs, automated checks, and comparative baselines.

## 11. Integration With the SI Research Ecosystem

- **SIF:** separates localization and addressing mechanisms from higher-level intelligence functions; WE-HDT and CDE may offer complementary, still-unverified approaches.
- **CDE:** offers a candidate language for constrained evolution of representations, descriptors, and research definitions, subject to its own kernel boundary work.
- **AQSI:** can propose questions designed to expose gaps and counterexamples.
- **UCPSF:** may score alternative revisions, while retaining explicit perspectives and evaluator governance.
- **BM-ODWEI / REN:** may help preserve weak, directional, or conflicting evidence without falsely converting it into established fact.
- **UIERU / Collective Learning:** can relay definitions, tests, failures, and unresolved questions between research units.
- **SSI:** motivates later self-modeling questions, without claiming that self-reference alone establishes consciousness.

These are architectural hypotheses and interface opportunities, not validated integrations.

## 12. Open Questions

1. Which WE obligations are truly kernel-level rather than conventions of a particular representation backend?
2. Can a precise WE descriptor contract accommodate genuinely non-comparable or not-yet-expressible properties?
3. How should conflicting perspectives be retained without imposing unjustified consensus?
4. Which properties distinguish CDE from generic transition systems while still admitting adversarial and cyclic cases?
5. What is the right granularity for versioning a definition, a contract, and a deployed implementation?
6. Can DEL's revisions be partly automated without delegating scientific judgment to a black-box scorer?
7. How should failed hypotheses be relayed so that future researchers can reproduce rather than merely inherit them?
8. What empirical benchmark would demonstrate that a residual registry improves discovery beyond conventional anomaly tracking?
9. Under what conditions does adaptive WE-HDT indexing outperform established baselines, and when does it not?
10. Can a self-modeling entity retain a stable identity across changing, contradictory, and incomplete self-representations?

## 13. Proposed Research Deliverables

1. Publish versioned kernel and descriptor schemas in `SPEC-001` and `SPEC-002`.
2. Specify WE-HDT/MLIU and SI Operations in `SPEC-003` and `SPEC-004`.
3. Define residual and metric-construction evidence contracts in `SPEC-005`.
4. Turn this paper's DEL procedure into a testable research-relay contract in `SPEC-006`.
5. Implement the chess boundary stress test (`CASE-004`) with explicit game-state and history rules.
6. Populate definition, counterexample, decision, and unresolved-residual registries with linked IDs.
7. Benchmark a concrete WE-HDT implementation against task-matched indexing and reasoning baselines.

## 14. Scope and Non-Claims

This paper **does not** establish that WE-SIO is a complete ontology of the world, that WE-HDT outperforms k-d trees or relational databases, that every relation admits a mathematical metric, that residuals prove new laws, that CDE applies to every constrained system, or that self-modeling demonstrates consciousness. The paper offers a traceable method for developing and testing such claims without prematurely closing the research boundary.

## 15. Conclusion

The challenge of a general research framework is not to enumerate every future application. It is to identify a meaningful core, state operational obligations precisely, expose the boundary to counterexamples, and preserve the evidence trail when definitions change. **Minimal Kernel + Contracts + Open Extensions + Definition Evolution** is proposed as the methodological backbone of WE-SIO. Its most important output is not a permanently fixed definition, but a disciplined process in which definitions can be challenged, corrected, compared, and relayed.

> **Preserve not only what we know, but also how we arrived there, what challenged it, and what remains unknown.**

---

**Research note:** This manuscript is an original exploratory synthesis for the WE-SIO research repository. Formal proofs, implementations, benchmarks, and external scholarly comparisons are future work. References to related SI projects identify conceptual relationships rather than independently verified empirical results.
