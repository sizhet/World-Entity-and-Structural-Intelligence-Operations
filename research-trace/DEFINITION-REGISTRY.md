# DEFINITION REGISTRY

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Release:** v0.1.0 · Research framework / hypothesis  
**Registry revision:** DR-0.1.1 · 2026-11-05 (additive definition alignment)  
**Research attribution:** Sizhe Tan & GPT-Obot  
**Status:** Proposed definitions; no implementation or empirical validation implied  
**Repository location:** `research-trace/DEFINITION-REGISTRY.md`

> **Design rule:** Define the invariant, not the inventory. Definition incomplete does not mean definition imprecise.

## 1. Purpose and epistemic status

This registry provides stable, testable meanings for terms used across WE-SIO's papers, specifications, cases, and extensions. It is a research coordination artifact, not an ontology claiming to exhaust the world. Definitions can be proposed, constrained, split, superseded, or rejected as evidence and counterexamples accumulate. The record must preserve *why* a definition changed.

The registry distinguishes **semantic claims** (what a concept means), **formal contracts** (what an implementation must preserve), **operational conventions** (how a system represents it), and **hypotheses** (what remains to be tested). A term may be semantically useful without being mathematically universal or computationally efficient.

### 1.1 Registry status vocabulary

| Status | Meaning | Allowed next steps |
|---|---|---|
| Proposed | Precise working definition awaiting challenge | Review, test, narrow, split |
| Contracted | Formal conformance requirements documented | Implement, test, revise |
| Provisionally accepted | Survives named tests, within stated scope | Extend or challenge |
| Contested | Substantive ambiguity or counterexample unresolved | Refine or branch |
| Superseded | Replaced by a versioned successor | Retain for provenance |
| Rejected | Contradicted or operationally incoherent in declared scope | Preserve rationale |

All entries below are **Proposed**, except where a linked specification may define an additional contract. No entry is marked validated solely because it is written here.

### 1.2 Entry schema

Each record has: `ID`, `Term`, `Definition`, `Invariants`, `Non-equivalences`, `Boundary / counterexample`, `Conformance probe`, `Dependencies`, `Status`, and `Version`. An entry may also include an `Open question` and `Related files`. Registry IDs are immutable; definitions can evolve through explicit versions.

---

## 2. Foundational entity and perspective definitions

### DEF-001 — World Entity (WE)

**Definition.** A referenceable subject of description, observation, relation, or operation within an explicitly declared modeling scope. A WE may be physical, abstract, institutional, computational, or event-like; its *kind* and identity policy must be declared.

- **Invariants:** Entity reference and entity-kind are explicit; representations may vary without silently changing identity.
- **Non-equivalences:** WE ≠ database row; WE ≠ coordinate; WE ≠ all its current attributes.
- **Boundary / counterexample:** Two hospital rows may refer to one person; one event row may represent an event rather than a person.
- **Conformance probe:** Change a nonidentity perspective and verify entity identity remains stable under the declared identity policy.
- **Dependencies:** DEF-002, DEF-003. **Status:** Proposed. **Version:** 0.1.

### DEF-002 — Entity identity

**Definition.** A scoped rule or evidence-backed resolution process determining whether references denote the same WE across observations, times, and sources.

- **Invariants:** Identity assertions include scope, evidence/provenance, and uncertainty where resolution is probabilistic.
- **Non-equivalences:** Identity ≠ similarity; identity ≠ source-local primary key; identity ≠ identical metric signature.
- **Boundary / counterexample:** Namesakes may have identical names and demographics without being the same entity.
- **Conformance probe:** Two equal attribute vectors must not be automatically merged absent an identity rule.
- **Dependencies:** DEF-001, DEF-009. **Status:** Proposed. **Version:** 0.1.

### DEF-003 — Representation

**Definition.** A versioned encoding or view of a WE or its evidence, chosen for a task, observer, and medium.

- **Invariants:** Encoding format and interpretation are distinguishable from the represented entity.
- **Non-equivalences:** Representation ≠ reality; serialization ≠ identity.
- **Boundary / counterexample:** A map and a graph can represent the same city with different omissions.
- **Conformance probe:** Two formats should refer to the same WE without claiming field-for-field equivalence.
- **Dependencies:** DEF-001, DEF-004. **Status:** Proposed. **Version:** 0.1.

### DEF-004 — Perspective

**Definition.** A typed, scoped way of observing, measuring, comparing, relating, or reasoning about WEs, accompanied by semantics and evidence requirements.

- **Invariants:** Descriptor identifies domain, value/relation type, units if applicable, applicability, provenance, uncertainty, time, and version.
- **Non-equivalences:** Perspective ≠ numeric column; Perspective ≠ mathematical metric.
- **Boundary / counterexample:** “Works with” is a directed or symmetric relation depending on its declared semantics, not automatically a distance.
- **Conformance probe:** Reject a perspective lacking a domain or incompatible value semantics.
- **Dependencies:** DEF-001, DEF-005–008. **Status:** Proposed. **Version:** 0.1.

### DEF-005 — Mathematical metric

**Definition.** A function `d: X × X → [0,∞)` satisfying nonnegativity, identity of indiscernibles, symmetry, and triangle inequality over its declared domain `X`.

- **Invariants:** `d(x,y) ≥ 0`; `d(x,y)=0 iff x=y` (under the domain's equality); `d(x,y)=d(y,x)`; `d(x,z)≤d(x,y)+d(y,z)`.
- **Non-equivalences:** Metric ≠ similarity score; metric ≠ arbitrary measured value; metric ≠ directional evidence.
- **Boundary / counterexample:** Asymmetric travel time is generally not a metric; a pseudometric may assign zero distance to distinct items.
- **Conformance probe:** Property-based checks with numerical tolerances and explicit floating-point policy.
- **Dependencies:** DEF-004. **Status:** Proposed. **Version:** 0.1.

### DEF-006 — Measurement

**Definition.** An observation procedure yielding a value or distribution with units, calibration, context, and uncertainty, without implying a pairwise metric.

- **Invariants:** Measurement procedure, units, time, and evidence source remain traceable.
- **Non-equivalences:** Measurement ≠ metric distance; measurement ≠ ground truth.
- **Boundary / counterexample:** Body temperature is a scalar measurement; it is not itself a distance function between patients.
- **Conformance probe:** Verify unit conversion, provenance, missingness, and calibration metadata.
- **Dependencies:** DEF-004, DEF-009. **Status:** Proposed. **Version:** 0.1.

### DEF-007 — Similarity

**Definition.** A declared function or rule quantifying resemblance or affinity, possibly asymmetric, contextual, or nontransitive.

- **Invariants:** Range, direction, normalization, and interpretation are explicit.
- **Non-equivalences:** Similarity ≠ identity; similarity ≠ metric without a proven transformation.
- **Boundary / counterexample:** High text similarity does not establish authorship or entity equivalence.
- **Conformance probe:** A system must not use a similarity threshold as an identity proof without a separate policy.
- **Dependencies:** DEF-002, DEF-004. **Status:** Proposed. **Version:** 0.1.

### DEF-008 — Relational / directional perspective

**Definition.** A typed relation, possibly weighted and directed, connecting WEs or their states with explicit role and temporal semantics.

- **Invariants:** Subject/object roles, directionality, validity period, and evidence are recorded.
- **Non-equivalences:** Relation ≠ symmetric similarity; relation ≠ causation by default.
- **Boundary / counterexample:** “Prescribes treatment to” is directional and does not imply treatment efficacy.
- **Conformance probe:** Reverse the relation and check whether the declared type permits inversion.
- **Dependencies:** DEF-001, DEF-004. **Status:** Proposed. **Version:** 0.1.

### DEF-009 — Evidence record

**Definition.** A versioned claim-support object containing observation/source, collection method, context, uncertainty, provenance, and applicable access controls.

- **Invariants:** Evidence can be inspected, challenged, and traced; multiple dependent reports are not automatically independent confirmations.
- **Non-equivalences:** Evidence ≠ truth; consensus ≠ independent evidence.
- **Boundary / counterexample:** Ten agents quoting the same source are one provenance chain, not ten independent observations.
- **Conformance probe:** Trace duplicate or correlated source lineage across relays.
- **Dependencies:** DEF-003. **Status:** Proposed. **Version:** 0.1.

---

## 3. Localization, indexing, and intelligence definitions

### DEF-010 — Localization / Addressing

**Definition.** The task of identifying or routing to candidate entities, states, perspectives, capabilities, or evidence satisfying an explicitly specified query and correctness contract.

- **Invariants:** Query scope, completeness/approximation guarantees, authorization, and version are declared.
- **Non-equivalences:** Localization ≠ proof of relevance; address ≠ entity identity.
- **Boundary / counterexample:** An approximate nearest-neighbor index can omit the true nearest neighbor.
- **Conformance probe:** Compare candidate recall with a defined exhaustive baseline.
- **Dependencies:** DEF-001, DEF-004, DEF-011. **Status:** Proposed. **Version:** 0.1.

### DEF-011 — WE Hybrid Differential Tree (WE-HDT)

**Definition.** A proposed federated localization and resolution architecture combining task-appropriate candidate indexing with typed metric, relational, and differential reasoning over WEs.

- **Invariants:** Candidate generation is separable from resolution; Euclidean-first is optional; perspective and version semantics are preserved.
- **Non-equivalences:** WE-HDT ≠ necessarily one physical tree; WE-HDT ≠ proven faster than a k-d tree.
- **Boundary / counterexample:** An abstract legal obligation has no required Euclidean coordinates.
- **Conformance probe:** Resolve the same query under a non-Euclidean perspective without inventing spatial coordinates.
- **Dependencies:** DEF-004, DEF-010, DEF-012. **Status:** Proposed. **Version:** 0.1.

### DEF-012 — Two-phase search

**Definition.** A process that first generates a candidate set and then resolves or ranks candidates under a declared exact or approximate contract.

- **Invariants:** The second phase cannot recover candidates excluded by the first unless a fallback is specified.
- **Non-equivalences:** Candidate filtering ≠ guaranteed exact answer.
- **Boundary / counterexample:** A coarse block filter that drops a boundary-straddling nearest neighbor breaks exactness.
- **Conformance probe:** Test boundary cases against exhaustive search and report recall and latency separately.
- **Dependencies:** DEF-010. **Status:** Proposed. **Version:** 0.1.

### DEF-013 — Perspective-Adaptive Variable Block (PAVB)

**Definition.** A variable-granularity partition whose boundaries and maintenance policy depend on declared perspectives and workload signals.

- **Invariants:** Split/merge/reindex events preserve query correctness guarantees or explicitly downgrade them.
- **Non-equivalences:** PAVB ≠ inherently novel partitioning; k-d trees can already create unequal partitions.
- **Boundary / counterexample:** Highly dynamic skew may cause costly oscillating repartitioning.
- **Conformance probe:** Test split/merge hysteresis, update costs, and boundary recall.
- **Dependencies:** DEF-004, DEF-012. **Status:** Proposed. **Version:** 0.1.

### DEF-014 — Adaptive Variable-Intelligence Block (AVIB)

**Definition.** A block or addressable region with independently configurable computational intelligence capabilities and resource budgets.

- **Invariants:** Partition granularity and intelligence capability are separate control dimensions.
- **Non-equivalences:** AVIB ≠ one agent per block; more intelligence ≠ better outcomes automatically.
- **Boundary / counterexample:** A dense region may need a small index block but no heavyweight inference unit.
- **Conformance probe:** Vary block size while holding capability fixed, then vary capability while holding size fixed.
- **Dependencies:** DEF-013, DEF-015. **Status:** Proposed. **Version:** 0.1.

### DEF-015 — Metric Leaf Intelligence Unit (MLIU)

**Definition.** A logical, perspective-scoped intelligence interface attached to an addressable entity/region/evidence context, supporting Locate, Resolve, Relate, Infer, Question, and Evolve operations.

- **Invariants:** Interface includes reference, perspective contract, evidence, uncertainty, residuals, supported operations, budget, provenance, and version.
- **Non-equivalences:** Logical leaf ≠ physical leaf; MLIU ≠ autonomous consciousness; MLIU ≠ mandatory LLM agent.
- **Boundary / counterexample:** A shared lightweight evaluator can serve many logical leaves.
- **Conformance probe:** Invoke an unsupported operation and verify explicit rejection or delegation.
- **Dependencies:** DEF-004, DEF-009, DEF-011. **Status:** Proposed. **Version:** 0.1.

### DEF-016 — Two-Ways CCC

**Definition.** A bidirectional structural workflow: forward localization/constraint evaluation and reverse residual-driven questioning, hypothesis generation, or perspective discovery.

- **Invariants:** Forward answers and reverse questions have separate evidence and validation statuses.
- **Non-equivalences:** Generated question ≠ verified discovery; backward search ≠ inverse of every forward operator.
- **Boundary / counterexample:** A model's unexplained error may be a data-entry mistake rather than a new mechanism.
- **Conformance probe:** Verify that reverse-generated hypotheses cannot silently modify production definitions.
- **Dependencies:** DEF-017, DEF-018. **Status:** Proposed. **Version:** 0.1.

---

## 4. Discovery and epistemic evolution definitions

### DEF-017 — Residual

**Definition.** A typed, contextual discrepancy between an expectation/model and an observation or constraint result, with explicit comparison semantics.

- **Invariants:** Baseline model/version, observation, error definition, uncertainty, and provenance are retained.
- **Non-equivalences:** Residual ≠ noise by definition; residual ≠ new scientific law.
- **Boundary / counterexample:** Sensor drift creates residuals without a changed underlying phenomenon.
- **Conformance probe:** Recompute residuals after baseline revision without overwriting prior records.
- **Dependencies:** DEF-006, DEF-009. **Status:** Proposed. **Version:** 0.1.

### DEF-018 — Residual Registry

**Definition.** A versioned, queryable record of residual observations, explanations, unresolved alternatives, challenges, and validation outcomes.

- **Invariants:** Negative results and unresolved items remain visible; no silent promotion to established fact.
- **Non-equivalences:** Registry count ≠ number of independent anomalies.
- **Boundary / counterexample:** Repeated measurements from one faulty sensor are correlated.
- **Conformance probe:** Deduplicate by provenance while preserving each original observation.
- **Dependencies:** DEF-009, DEF-017. **Status:** Proposed. **Version:** 0.1.

### DEF-019 — Candidate metric / perspective discovery

**Definition.** The generation and staged assessment of new measurement, comparison, relation, or formal metric descriptors intended to explain or improve previously unresolved tasks.

- **Invariants:** Candidate is typed correctly; mathematical metric claims require metric axioms; predictive claims require out-of-sample validation.
- **Non-equivalences:** Derived feature ≠ metric; correlation ≠ causal mechanism.
- **Boundary / counterexample:** A powerful learned score may be asymmetric and violate triangle inequality.
- **Conformance probe:** Apply semantic, mathematical, evidence, robustness, and governance gates before promotion.
- **Dependencies:** DEF-004–009, DEF-017. **Status:** Proposed. **Version:** 0.1.

### DEF-020 — Scientific discovery claim

**Definition.** A versioned, falsifiable explanation or prediction supported by a specified chain of observations, methods, tests, and alternatives.

- **Invariants:** Hypothesis, supporting evidence, disconfirming evidence, and generalization scope are distinct.
- **Non-equivalences:** Hypothesis generation ≠ scientific validation; predictive accuracy ≠ causal identification.
- **Boundary / counterexample:** A clinical subgroup pattern may disappear after adjusting for confounding.
- **Conformance probe:** Require held-out or independent tests where appropriate and explicit failure criteria.
- **Dependencies:** DEF-009, DEF-018, DEF-019. **Status:** Proposed. **Version:** 0.1.

### DEF-021 — Definition Evolution Loop (DEL)

**Definition.** A controlled process for proposing, testing, narrowing, splitting, generalizing, or reverting definitions in response to counterexamples and research needs.

- **Invariants:** Minimal kernel, scope, version history, counterexamples, compatibility analysis, and regression tests are preserved.
- **Non-equivalences:** More general wording ≠ better definition; revision ≠ retroactive rewriting of evidence.
- **Boundary / counterexample:** Generalizing a chess-specific no-repeat policy to all CDE systems would wrongly exclude legal repeated moves.
- **Conformance probe:** A change must cite a trigger and pass declared regression tests or document exceptions.
- **Dependencies:** DEF-022, DEF-023, DEF-027. **Status:** Proposed. **Version:** 0.1.

---

## 5. State, Delta, and CDE definitions

### DEF-022 — State container

**Definition.** A typed, versioned description of the relevant variables and constraints used to evaluate a transition or a decision in a declared domain.

- **Invariants:** State equality and completeness are defined relative to the task.
- **Non-equivalences:** State ≠ entire world; snapshot ≠ full event history.
- **Boundary / counterexample:** Identical chess piece placement can differ in castling or en-passant rights.
- **Conformance probe:** Compare positions with identical boards but different legal rights.
- **Dependencies:** DEF-001, DEF-003. **Status:** Proposed. **Version:** 0.1.

### DEF-023 — Delta

**Definition.** A typed change proposal or recorded difference between scoped states or descriptions, subject to explicit applicability, composition, reversal, and provenance rules.

- **Invariants:** Delta type, source/target semantics, preconditions, and outcome are explicit.
- **Non-equivalences:** Delta ≠ necessarily reversible; Delta ≠ necessarily unique; Delta ≠ always a real-world event.
- **Boundary / counterexample:** Undoing a mistaken database entry does not undo the real-world event it described.
- **Conformance probe:** Apply an invalid delta and require failure without partial silent mutation.
- **Dependencies:** DEF-022. **Status:** Proposed. **Version:** 0.1.

### DEF-024 — Delta type taxonomy

**Definition.** A disjoint-by-intent classification of changes: **World Delta** (modeled real-world change), **Observation Delta** (new/corrected observation), **Knowledge/Epistemic Delta** (belief/model revision), **Structural Delta** (index/architecture revision), and **Operational Delta** (policy/resource/agent configuration revision).

- **Invariants:** One event may produce linked deltas of different types, each with independent semantics and evidence.
- **Non-equivalences:** Database UPDATE ≠ automatically World Delta; model revision ≠ physical change.
- **Boundary / counterexample:** A newly discovered old diagnosis changes knowledge now but need not change the patient's past.
- **Conformance probe:** Classify synthetic event logs and preserve cross-type links.
- **Dependencies:** DEF-009, DEF-023. **Status:** Proposed. **Version:** 0.1.

### DEF-025 — Constrained Delta Evolution (CDE)

**Definition.** A proposed search/evolution framework over typed state containers and admissible deltas, with explicit constraints, evaluation, branching, memory/cycle policy, and termination or resource bounds.

- **Invariants:** Transition validity is checked; branch policy and resource bounds are declared; domain-specific restrictions are not silently universalized.
- **Non-equivalences:** CDE ≠ proof of algorithmic superiority over search, dynamic programming, or branch-and-bound; CDE ≠ inherently acyclic.
- **Boundary / counterexample:** Chess permits repeated states; the same move type can occur again along a legal line.
- **Conformance probe:** Support both cycle-permitting and cycle-restricting policies without altering the minimal transition contract.
- **Dependencies:** DEF-021–024, DEF-026. **Status:** Proposed. **Version:** 0.1.

### DEF-026 — Path memory / cycle policy

**Definition.** An application-specified constraint on revisiting states, transitions, delta identities, or histories during exploration.

- **Invariants:** Equality key, memory scope, exception policy, and termination implications are explicit.
- **Non-equivalences:** No-Delta-Reuse ≠ universal CDE axiom; state repetition ≠ always infinite loop.
- **Boundary / counterexample:** Chess repetition is sometimes legal and strategically meaningful.
- **Conformance probe:** Run identical transition systems with different cycle policies and compare legal paths.
- **Dependencies:** DEF-022, DEF-025. **Status:** Proposed. **Version:** 0.1.

---

## 6. Self-reference and collective intelligence definitions

### DEF-027 — Self-Modeling Entity (SME)

**Definition.** A WE equipped with a versioned model of its own relevant capacities, constraints, histories, uncertainties, and actions, able to compare self-predictions with outcomes and revise that model under governance.

- **Invariants:** Self-model reference, observation source, prediction, residual, revision rationale, and model version are distinguishable.
- **Non-equivalences:** Self-model ≠ self; self-report ≠ reliable introspection; self-modeling ≠ consciousness.
- **Boundary / counterexample:** A system can confidently misestimate its own capabilities.
- **Conformance probe:** Compare predicted versus observed task success and audit corrections.
- **Dependencies:** DEF-001, DEF-017, DEF-021. **Status:** Proposed. **Version:** 0.1.

### DEF-028 — Subjective Structural Entity (SSE), candidate concept

**Definition.** A research placeholder for a system whose structural modeling incorporates subject-relative valuation, boundaries, perspective, and recursive self-reference; no phenomenological or consciousness criterion is established by this label.

- **Invariants:** Operational claims must be distinguished from philosophical claims about experience.
- **Non-equivalences:** SSE ≠ demonstrated sentience; SSE ≠ moral status determination.
- **Boundary / counterexample:** Recursive self-description can be generated without evidence of subjective experience.
- **Conformance probe:** Check that experiments measure operational self-modeling rather than claiming to detect consciousness.
- **Dependencies:** DEF-027. **Status:** Proposed / contested scope. **Version:** 0.1.

### DEF-029 — Agent

**Definition.** An accountable execution role with an objective or delegated task, accessible operations, resource limits, and evidence/reporting obligations.

- **Invariants:** Role, authority, scope, budget, and output provenance are explicit.
- **Non-equivalences:** Agent ≠ WE; agent ≠ necessarily separate model process.
- **Boundary / counterexample:** One model instance may enact several logical agent roles.
- **Conformance probe:** Reject unauthorized cross-role operations.
- **Dependencies:** DEF-009, DEF-015. **Status:** Proposed. **Version:** 0.1.

### DEF-030 — Relay

**Definition.** A traceable transfer of tasks, evidence, questions, policies, or learned structures between execution contexts, agents, runs, or research participants.

- **Invariants:** Sender/context, payload, transformation, recipient/context, and provenance are recorded.
- **Non-equivalences:** Relay ≠ necessarily handoff between different agents; repeated execution can form a data-accumulation relay.
- **Boundary / counterexample:** Copying an unsupported claim across agents does not increase evidentiary strength.
- **Conformance probe:** Reconstruct the provenance chain of a multi-hop conclusion.
- **Dependencies:** DEF-009, DEF-029. **Status:** Proposed. **Version:** 0.1.

### DEF-031 — Collective Learning

**Definition.** A measurable, persistent improvement in shared evidence, capabilities, policies, representations, or structures attributable to coordinated and traceable contributions.

- **Invariants:** Improvement metric, baseline, transfer mechanism, evidence independence, and retention conditions are specified.
- **Non-equivalences:** More agents ≠ collective learning; consensus ≠ validation; aggregation ≠ transferable improvement.
- **Boundary / counterexample:** Five agents repeating one incorrect inference can amplify error.
- **Conformance probe:** Test whether learned artifacts improve held-out tasks after contributor removal.
- **Dependencies:** DEF-009, DEF-030. **Status:** Proposed. **Version:** 0.1.

### DEF-032 — Structural Intelligence Framework (SIF) localization pillar

**Definition.** A candidate reusable family of addressing/localization methods integrated through explicit SIF contracts; WE-HDT and CDE are proposed complementary contributors, not proven exclusive pillars.

- **Invariants:** Routing, correctness, policy, interoperability, and ownership of evaluation decisions are declared.
- **Non-equivalences:** Architecture diagram ≠ demonstrated integration; WE-HDT ≠ CDE.
- **Boundary / counterexample:** A WE-HDT index can identify candidates without finding a feasible state-transition path; CDE can explore paths without providing a global entity index.
- **Conformance probe:** Exchange typed candidate sets and state-transition requests with reproducible versions.
- **Dependencies:** DEF-010, DEF-011, DEF-025. **Status:** Proposed. **Version:** 0.1.

---

## 6A. Extended definition registry: EXT-005, EXT-006, and updated core contracts

**Addition policy:** `DEF-033`–`DEF-054` correspond one-to-one with `GLOSSARY.md` candidate terms `E01`–`E22`. Original `DEF-001`–`DEF-032` are retained; this extension does not silently change their meanings. Each new record is **Proposed / version 0.1**, not empirically validated. A linked specification can impose a testable contract without making the associated research hypothesis true.

### DEF-033 — Epistemic Separation (Glossary E01)

**Definition.** A logical separation between evidence-supported established claims, open or unverified knowledge, and qualified residual evidence, including their scope, versions, and provenance.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Logical separation does not require physically separate databases. Physical co-location must not erase semantic distinctions.
- **Conformance probe:** Represent an unknown, an accepted scoped claim, and a qualified contradiction; reject implicit cross-state promotion.
- **Dependencies:** DEF-009, DEF-017–021. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-034 — Established Knowledge (`EK`) (Glossary E02)

**Definition.** A claim supported under declared evidence, perspective, context, time, validation criteria, and version.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** “Established” is scope-relative and revisable, not absolute truth or permanent certainty.
- **Conformance probe:** Revise the declared scope or evidence version; require an auditable status transition.
- **Dependencies:** DEF-009, DEF-020. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-035 — Open Knowledge (`OK`) (Glossary E03)

**Definition.** Unanswered questions, unknown variables, untested hypotheses, contested claims, and unresolved possibilities tracked without pretending they have been verified.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** An unknown is not automatically a residual; absence of information is not a demonstrated model failure.
- **Conformance probe:** Create an unanswered question without baseline; ensure it cannot be auto-admitted to RER.
- **Dependencies:** DEF-017, DEF-019. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-036 — Residual Evidence Registry (`RER`) (Glossary E04)

**Definition.** An addressable collection of *qualified* discrepancies between observations and explicit baselines, expectations, constraints, or explanatory commitments under typed comparison contracts.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** RER is not a miscellaneous “unknowns bucket.” A SQL `NULL`, unmeasured attribute, or missing prediction alone is not admissible residual evidence.
- **Conformance probe:** Attempt to admit a SQL NULL or ungrounded anomaly; require rejection or provisional status.
- **Dependencies:** DEF-017–018. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-037 — Residual Qualification / RER Admission (Glossary E05)

**Definition.** A governed decision that a candidate discrepancy has a meaningful baseline, comparable observation, adequate provenance, uncertainty characterization, and explicit status.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Qualified residual evidence does not prove a new mechanism, causal relation, or law.
- **Conformance probe:** Compare mismatched baseline versions; reject qualification until comparable.
- **Dependencies:** DEF-017–018. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-038 — Residual Diagnosis (Glossary E06)

**Definition.** Investigation of competing explanations for a discrepancy, including sensor error, miscalibration, confounding, selection bias, data leakage, distribution shift, model misspecification, or a potentially missing phenomenon.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Diagnosing a data artifact is a legitimate scientific outcome; not every residual warrants metric discovery.
- **Conformance probe:** Inject sensor drift and confounding; retain non-novel diagnoses.
- **Dependencies:** DEF-017–020. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-039 — Knowledge Promotion (Glossary E07)

**Definition.** A versioned, evidence-reviewed transition of a claim or perspective from candidate/open status to *established for a declared scope*.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Agent consensus, repeated model execution, or retrieval utility alone do not satisfy independent validation. Promotion is `ΔK`, not necessarily `ΔS`.
- **Conformance probe:** Attempt promotion using multiple agents citing one shared source; reject unsupported independence.
- **Dependencies:** DEF-020–021. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-040 — Knowledge Demotion / Withdrawal (Glossary E08)

**Definition.** An evidence-governed narrowing, suspension, or retraction of previously accepted knowledge, with dependency review and preserved audit history subject to lawful retention constraints.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Epistemic rollback cannot reverse an irreversible physical event.
- **Conformance probe:** Withdraw a claim and verify dependent claims are flagged without deleting history.
- **Dependencies:** DEF-020–021. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-041 — Mask-First Structural Intelligence (`MFSI`) (Glossary E09)

**Definition.** A candidate computational strategy that first selects a task-appropriate view over mature structures, reusing existing pathways before costly regeneration or reconstruction when correctness and net benefit permit.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** A heuristic, not a universal optimality principle. Stale or corrupt structures and incompatible guarantees may require immediate rebuild.
- **Conformance probe:** Compare masked, full-view and eager-rebuild executions including mask overhead.
- **Dependencies:** DEF-011–016. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-042 — Mask (Glossary E10)

**Definition.** A versioned, authorized selection rule over eligible nodes, edges, metrics, operations, depth, or resource budgets for a task.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** A mask is not deletion, a proof of irrelevance, a substitute for source authorization, or automatically a persistent structural mutation.
- **Conformance probe:** Revoke authorization; ensure no mask expands permitted access.
- **Dependencies:** DEF-011–016. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-043 — Unmask / Remask (Glossary E11)

**Definition.** `Unmask` broadens or restores the active eligible view within authorization; `Remask` recomputes selection after context, feedback, evidence, or policy changes.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Unmasking must not bypass access controls. Remasking cannot silently remove candidates when exactness is promised.
- **Conformance probe:** Remask after context drift and test candidate coverage and authorization.
- **Dependencies:** DEF-042, DEF-043. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-044 — Active Computational View (`ACV`) (Glossary E12)

**Definition.** The effective, task-scoped computation graph or selection over a versioned underlying substrate, perspective definitions, and authorized resources.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** `ACV ≠ persistent WE-HDT topology`. An active view can change while the substrate remains unchanged.
- **Conformance probe:** Change a task mask while holding persistent topology fixed; verify separate versions.
- **Dependencies:** DEF-011, DEF-014. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-045 — Mature-Structure Preservation (Glossary E13)

**Definition.** A design preference to retain validated knowledge pathways and durable indexing structures where selective reuse, local adaptation, or masking is sufficient.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Preservation does not outrank correctness, privacy, security, or demonstrated need to rebuild.
- **Conformance probe:** Inject a corrupted mature index; allow justified rebuild instead of forced preservation.
- **Dependencies:** DEF-011, DEF-013–014. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-046 — Coverage-Safe Mask (Glossary E14)

**Definition.** A mask that preserves the candidate superset or recall guarantee required by its declared retrieval or discovery contract.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** A high-scoring or apparently relevant mask is not necessarily coverage-safe. Exact retrieval needs a proof, conservative coverage, or safe full-view fallback.
- **Conformance probe:** Compare exact masked retrieval against exhaustive baseline; detect any omitted valid candidate.
- **Dependencies:** DEF-010–012. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-047 — Mask Policy Invalidation (Glossary E15)

**Definition.** Revalidation or replacement of a cached mask when relevant source data, schema, perspective definition, authorization, policy, or structural versions change.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Reusing a stale mask may create silent omissions or security failures.
- **Conformance probe:** Change permissions, schema, evidence, and topology versions; ensure stale masks are invalidated.
- **Dependencies:** DEF-042–044. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-048 — Five-Way Delta Taxonomy (Glossary E16)

**Definition.** A research-level classification separating `ΔW` (world), `ΔO` (observation), `ΔK` (knowledge), `ΔS` (persistent structure), and `ΔA` (activation/mask).

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** These are semantic types, not proof that all real workflows have exactly one delta. A composite event can contain several separately auditable types.
- **Conformance probe:** Classify composite event logs without forcing a single delta; test activation-versus-structure distinction.
- **Dependencies:** DEF-023–024. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-049 — SQL-Native Structural Intelligence (Glossary E17)

**Definition.** A proposed WE-SIO integration in which established SQL engines provide source data, schema, transactions, indexes, queries, and security controls, while SI layers provide typed entity/perspective mapping, residual investigation, and governed knowledge evolution.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** SQL tables are not necessarily entity types; rows are not necessarily world entities; columns are not automatically mathematical metrics; JOINs do not prove identity.
- **Conformance probe:** Test row/event/entity ambiguity, JOIN duplication, source-local keys and column/metric confusion.
- **Dependencies:** DEF-001–009. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-050 — SQL Epistemic Missingness (Glossary E18)

**Definition.** Interpretation of absent, unknown, withheld, inapplicable, or not-yet-observed values under an explicit missingness contract.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** SQL `NULL` alone cannot determine whether something is an unknown, negative observation, contradiction, or residual.
- **Conformance probe:** Distinguish unknown, inapplicable, withheld and absent values without automatic residual classification.
- **Dependencies:** DEF-006, DEF-009. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-051 — Source-State Delta (Glossary E19)

**Definition.** A change in recorded source-system state, such as an SQL `UPDATE`, that must be distinguished from a claim about an external-world event.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** A source update may accompany `ΔO`, `ΔK`, or `ΔW`, but does not by itself prove any physical change.
- **Conformance probe:** Issue SQL UPDATE with no evidence of external change; disallow automatic ΔW.
- **Dependencies:** DEF-009, DEF-024. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-052 — Evidence Independence (Glossary E20)

**Definition.** The degree to which supporting observations or analyses originate from genuinely distinct sources and error processes.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Multiple agents citing the same dataset, derived measurements, or copied reports are not independent replications.
- **Conformance probe:** Use three agents drawing on one source; prevent triple-counting independent support.
- **Dependencies:** DEF-009, DEF-030–031. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-053 — Metric Candidate versus Perspective Candidate (Glossary E21)

**Definition.** A metric candidate proposes a distance function with axioms on a declared domain; a perspective candidate may instead be a measurement, similarity, directional score, or typed relation.

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** A useful comparator is not automatically a mathematical metric; metric pruning requires verified mathematical guarantees.
- **Conformance probe:** Pass asymmetric similarity as a metric; require axiom check or nonmetric label.
- **Dependencies:** DEF-004–008, DEF-019. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### DEF-054 — Epistemic and Structural Governance Boundary (Glossary E22)

**Definition.** The separation of evidence/claim-status decisions (`SPEC-005`) from node, block, mask, and active-view computation contracts (`SPEC-003`).

- **Invariants:** Declare semantic scope, source/version, responsible policy, and applicable evidence or authorization constraints; preserve type and provenance through transitions.
- **Non-equivalences / boundary:** Changing a computation view cannot automatically validate a scientific claim; accepting a new claim does not necessarily require a new physical index.
- **Conformance probe:** Change mask policy without changing claim status; separately promote a claim without reindexing.
- **Dependencies:** DEF-017–021, DEF-042–044. **Status:** Proposed. **Version:** 0.1.
- **Related research:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`; updated `SPEC-003` / `SPEC-005` as applicable.

### 6A.1 Delta taxonomy compatibility note

`DEF-024` originally distinguished World, Observation, Knowledge, Structural, and *Operational* changes. The updated WE-SIO-009 introduces `ΔA` as a distinct **Activation/Mask Delta**; `DEF-048` is the versioned five-way refinement, not a silent retroactive rewrite of `DEF-024`. Operational changes require typing by their actual persistence and semantics: a task-scoped mask is `ΔA`, a durable policy/topology mutation may be `ΔS`, and a source record mutation must not be assumed to be `ΔW`. Composite events may contain multiple linked deltas. **Open issue:** whether resource/agent configuration changes warrant a separate operational subtype beyond the five-way research taxonomy.

### 6A.2 Mapping from provisional glossary labels

| Glossary term | Stable registry ID | Glossary term | Stable registry ID |
|---|---|---|---|
| E01 Epistemic Separation | DEF-033 | E02 Established Knowledge (`EK`) | DEF-034 |
| E03 Open Knowledge (`OK`) | DEF-035 | E04 Residual Evidence Registry (`RER`) | DEF-036 |
| E05 Residual Qualification / RER Admission | DEF-037 | E06 Residual Diagnosis | DEF-038 |
| E07 Knowledge Promotion | DEF-039 | E08 Knowledge Demotion / Withdrawal | DEF-040 |
| E09 Mask-First Structural Intelligence (`MFSI`) | DEF-041 | E10 Mask | DEF-042 |
| E11 Unmask / Remask | DEF-043 | E12 Active Computational View (`ACV`) | DEF-044 |
| E13 Mature-Structure Preservation | DEF-045 | E14 Coverage-Safe Mask | DEF-046 |
| E15 Mask Policy Invalidation | DEF-047 | E16 Five-Way Delta Taxonomy | DEF-048 |
| E17 SQL-Native Structural Intelligence | DEF-049 | E18 SQL Epistemic Missingness | DEF-050 |
| E19 Source-State Delta | DEF-051 | E20 Evidence Independence | DEF-052 |
| E21 Metric Candidate versus Perspective Candidate | DEF-053 | E22 Epistemic and Structural Governance Boundary | DEF-054 |

## 7. Cross-definition invariants and prohibited conflations

| Rule ID | Required distinction | Failure if conflated |
|---|---|---|
| INV-001 | Entity identity vs representation | False merges and unstable references |
| INV-002 | Perspective vs mathematical metric | Invalid distance assumptions |
| INV-003 | Measurement vs evidence-backed truth | Hidden measurement error |
| INV-004 | Similarity vs identity | Incorrect entity resolution |
| INV-005 | Candidate localization vs validated resolution | Unreported false negatives |
| INV-006 | Logical MLIU vs physical tree leaf | Unnecessary architectural coupling |
| INV-007 | Residual vs mechanism | Spurious scientific claims |
| INV-008 | World vs observation vs knowledge vs structural delta | False causal and temporal statements |
| INV-009 | Domain-specific path memory vs universal CDE semantics | Overconstrained search |
| INV-010 | Self-modeling vs subjective experience | Unsupported consciousness inference |
| INV-011 | Agent agreement vs independent evidence | Evidence double counting |
| INV-012 | Definition generality vs explanatory value | Vacuous universal framework |
| INV-013 | Unknown vs qualified residual | SQL NULL or an open question misrepresented as evidence |
| INV-014 | Established knowledge vs immutable truth | Unsupported certainty and silent promotion |
| INV-015 | Activation view vs persistent structure | Task selection falsely recorded as reindex |
| INV-016 | Mask selection vs access authorization | Security bypass or false coverage |
| INV-017 | Source-state mutation vs external-world event | SQL UPDATE falsely inferred as physical change |
| INV-018 | Agent consensus vs independent evidence | Correlated evidence double-counted |

## 8. Definition dependency and change-impact map

- **Identity foundation:** DEF-001–003 supports all later entity, self-model, and relay records.
- **Perspective semantics:** DEF-004–009 supports WE-HDT, MLIU, residual discovery, and metric promotion.
- **Localization interfaces:** DEF-010–016 supports SIF addressing and two-way discovery.
- **Discovery contracts:** DEF-017–021 supports scientific hypothesis validation and definition revision.
- **State evolution:** DEF-022–026 supports CDE, including chess and dynamic operational applications.
- **Self / collective:** DEF-027–032 builds on earlier contracts and requires stronger empirical evidence.
- **Epistemic and masking extensions:** DEF-033–047 govern knowledge state, RER, masks, active views, and mature-structure reuse.
- **Delta and SQL extensions:** DEF-048–054 govern five-way Delta, SQL semantics, evidence independence, and governance boundaries.

A change to DEF-005 must trigger review of metric conformance and all algorithms using metric axioms. A change to DEF-023 or DEF-025 must trigger chess cycle-policy tests. A change to DEF-027 or DEF-028 must trigger review of claims concerning consciousness and subjective status. A change to DEF-002 must trigger SQL identity and entity-resolution tests.

## 9. Definition Evolution Loop: change-control procedure

1. **Register trigger:** Cite counterexample, unresolved residual, experiment, interoperability failure, or conceptual ambiguity.
2. **Freeze baseline:** Preserve existing definition ID, version, scope, and dependent tests.
3. **Propose revision:** Mark whether narrowing, broadening, splitting, merging, or renaming.
4. **Check invariant preservation:** Explicitly list preserved and intentionally changed guarantees.
5. **Run adversarial counterexamples:** Include cases that defeated earlier versions.
6. **Run conformance and regression tests:** Compare before/after behavior and compatibility.
7. **Decide:** Accept provisionally, contest, reject, or supersede; record decision owner and evidence.
8. **Relay:** Update registry, decision log, hypothesis registry, linked specifications, and open leftovers.

### 9.1 Change request template

```yaml
change_id: DCR-YYYY-NNN
term_id: DEF-025
from_version: "0.1"
to_version: "0.2-proposed"
trigger: "COUNTEREXAMPLE-REGISTRY: CE-..."
change_kind: narrow | broaden | split | merge | clarify | reject
old_definition: "..."
proposed_definition: "..."
invariants_preserved: []
invariants_changed: []
affected_specs: []
affected_cases: []
new_tests: []
regression_results: pending
evidence_level: E0
review_status: proposed
decision_log_id: pending
explicit_leftovers: []
```

### 9.2 Worked definition revision: No-Delta-Reuse

**Trigger:** A D-BTP path may prohibit reusing a delta identity; chess permits revisiting certain board configurations and repeated move patterns under the rules.

**Rejected overgeneralization:** “All CDE paths prohibit reuse of any delta.”

**Proposed correction:** CDE requires a typed, explicit *cycle/path-memory policy*, which may prohibit, permit, penalize, bound, or specially handle revisits. A particular application can adopt No-Delta-Reuse when justified by its semantics.

**Regression obligation:** Preserve D-BTP's intended path constraint while allowing chess-legal repetition and correct treatment of castling, en-passant, halfmove clock, and repetition history.

**Status:** Conceptual clarification; runtime tests not yet executed.

## 10. Conformance checklist for registry consumers

| Test | Requirement | Expected outcome |
|---|---|---|
| DR-T01 | Same entity, different representation | Identity remains scoped and stable |
| DR-T02 | Same values, different entity | No automatic identity merge |
| DR-T03 | Asymmetric score labeled metric | Metric conformance rejects it |
| DR-T04 | Measurement lacks units | Explicit rejection or documented dimensionless contract |
| DR-T05 | Directional relation reversed | Type-aware inversion or rejection |
| DR-T06 | Index candidate omission | Recall failure exposed |
| DR-T07 | Abstract entity without coordinates | Non-Euclidean path remains available |
| DR-T08 | AVIB intelligence budget changed | Partition identity need not change |
| DR-T09 | Unsupported MLIU operation | Reject/delegate with trace |
| DR-T10 | Residual caused by sensor drift | Not auto-promoted to discovery |
| DR-T11 | New feature called metric | Metric axioms verified or label changed |
| DR-T12 | Observation corrected | No fictitious World Delta |
| DR-T13 | Chess board equal, rights differ | States not falsely collapsed |
| DR-T14 | Chess legal repetition | Cycle policy permits where specified |
| DR-T15 | Self-model prediction wrong | Revision provenance retained |
| DR-T16 | Agent outputs share one source | No evidence independence inflation |
| DR-T17 | Definition broadened | Counterexamples and regression checked |
| DR-T18 | Definition superseded | Historical version remains addressable |

| DR-T19 | Unknown without baseline submitted as RER | Reject or keep in Open Knowledge |
| DR-T20 | Qualified residual with mismatched baseline version | Reject qualification until reconciled |
| DR-T21 | Mask removes exact-query candidate | Coverage violation or safe full-view fallback |
| DR-T22 | Mask changes while substrate remains unchanged | Record ΔA without fabricating ΔS |
| DR-T23 | Schema or permission revocation with cached mask | Invalidate mask; preserve authorization |
| DR-T24 | SQL NULL interpreted as contradiction | Reject unsupported inference |
| DR-T25 | SQL UPDATE without physical-world evidence | Do not infer ΔW |
| DR-T26 | Agent consensus from common source | Do not promote as independent replication |
| DR-T27 | Knowledge withdrawal with dependent claims | Propagate review; preserve provenance |
| DR-T28 | Asymmetric comparator used as metric | Reject metric designation or validate axioms |
| DR-T29 | Corrupted mature index under preserve-first heuristic | Permit justified rebuild |
| DR-T30 | Cross-schema policy transfer | Require destination revalidation |

These are **test specifications**, not executed test results.

## 11. Open ambiguities and explicit leftovers

| ID | Open question | Proposed next action |
|---|---|---|
| DL-001 | How much identity policy belongs in the WE minimal kernel? | Compare cross-source entity resolution cases |
| DL-002 | Can perspective descriptors be both extensible and statically type-safe? | Prototype descriptor schema and migration |
| DL-003 | Which WE-HDT guarantees require exhaustive fallback? | Formalize recall and exactness contracts |
| DL-004 | How should AVIB intelligence activation be budgeted? | Cost-sensitive benchmark against static baselines |
| DL-005 | What constitutes a meaningful cross-perspective hypothesis? | Negative controls and independent validation |
| DL-006 | When is a residual epistemic rather than measurement-related? | Causal audit protocol and uncertainty model |
| DL-007 | What nontrivial invariants distinguish CDE from generic state-transition search? | Comparative formalization and ablation |
| DL-008 | What is the correct equality key for path memory? | Chess and logistics counterexamples |
| DL-009 | What measurable capabilities distinguish SME from ordinary monitoring? | Self-calibration experiments |
| DL-010 | Can SSE have a precise operational definition without claims of experience? | Separate SSI philosophical and operational tracks |
| DL-011 | How should evidence dependency propagate across relays? | Provenance DAG and correlated-evidence tests |
| DL-012 | How do definitions evolve without breaking historical reproducibility? | Schema versioning and compatibility tests |

### 11.1 New explicit leftovers

| ID | Open question | Proposed next action |
|---|---|---|
| DL-013 | Which baseline and comparator types qualify relational residuals? | RER admission fixtures and adversarial negative controls |
| DL-014 | Can exact retrieval survive task-specific masking? | Coverage proofs, differential testing, safe fallback |
| DL-015 | When does preserving mature structures become harmful? | Drift and corrupted-index benchmarks |
| DL-016 | How to govern knowledge promotion and withdrawal across dependent claims? | Provenance DAG and independent evidence review |
| DL-017 | How should operational policy changes map onto five-way Delta? | Composite event typing and versioned definition review |
| DL-018 | Which SQL row/entity and JOIN assumptions fail? | Multi-schema conformance fixtures |
| DL-019 | What prevents Mask Policy Relay from transferring access or scope errors? | Destination validation and permission revocation tests |

## 12. Cross-references

**Core papers:** `docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`; `docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md`; `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md`; `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md`; `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`; `docs/WE-SIO-010-From-World-Entity-to-Self-Modeling-Entity.md`; `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`.

**Specifications:** `specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md` through `specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md`.

**Boundary cases:** `cases/CASE-001-SQL-Columns-to-WE-Perspective-Indices.md`; `cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md`; `cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md`; `cases/CASE-005-Multi-Perspective-Self-Modeling-Entity.md`.

**Extensions:** `extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md`; `extensions/EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md`; `extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md`; `extensions/EXT-004-Self-Referential-World-Entity-and-Subjective-SI.md`.

**Recent extensions:** `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`; `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`. **Updated contracts:** `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`; `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`.

**Research trace:** `research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md`; `research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md`; `research-trace/HYPOTHESIS-REGISTRY.md`; `research-trace/COUNTEREXAMPLE-REGISTRY.md`; `research-trace/DECISION-LOG.md`; `research-trace/UNRESOLVED-RESIDUALS.md`.

## 13. Release and governance note

The definitions in this file are an **initial working vocabulary** for a research repository. They do not establish a completed world ontology, an implemented indexing engine, clinical validity, scientific discovery performance, or subjective experience. Publication should preserve the versioned definitions and identify which claims remain theoretical. Changes should be handled by explicit pull requests or equivalent review records and reflected in `CHANGELOG.md`.

**Research stance:** Open-ended conceptual growth is welcome; silent semantic drift is not. Preserve precise contracts, counterexamples, failed experiments, and unanswered questions as reusable Collective Learning assets.

---

*End of DEFINITION-REGISTRY.md · WE-SIO v0.1.0 · registry DR-0.1.1 · 2026-11-05*
