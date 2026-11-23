# GLOSSARY — World Entity and Structural Intelligence Operations (WE-SIO)

**Release:** v0.1.0  
**Research status:** Proposed framework; definitions and hypotheses require conformance and validation  
**Research attribution:** Sizhe Tan & GPT-Obot  
**Repository location:** `GLOSSARY.md`  
**Date:** 2026-11-23

> **Terminology principle:** Define the invariant, not the inventory. Definition incomplete does not mean definition imprecise.

## 1. Purpose and reading rules

This glossary provides a readable entry point to WE-SIO terminology. The authoritative, versioned definition records and conformance probes live in [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md). If a short glossary description conflicts with a formal specification, consult the specification and log the discrepancy; do not silently reinterpret either.

**Notation rules:** `WE` denotes an entity, `P` a perspective, `d` a mathematical metric only when metric axioms hold, `Δ` a typed change, `r` a residual, and `H` a testable hypothesis. Terms such as *metric*, *measurement*, *similarity*, and *relation* are intentionally not synonyms.

## 2. Core terminology (linked to Definition Registry)

The entries below are concise operational summaries; the `DEF` IDs refer to versioned research definitions.

### 01. World Entity (`WE`)

**Meaning:** A referenceable subject of description, observation, relation, or operation under a declared modeling scope.

**Boundary:** Not necessarily a physical object, a database row, or a coordinate.

**Registry:** `DEF-001`.

### 02. Entity identity

**Meaning:** A scoped, evidence-supported rule for deciding whether references denote the same entity.

**Boundary:** Neither source primary-key equality nor high similarity proves identity.

**Registry:** `DEF-002`.

### 03. Entity reference (`entityRef`)

**Meaning:** A resolvable handle used to address a modeled entity under an identity policy.

**Boundary:** A handle is not itself the entity.

**Registry:** `DEF-003`.

### 04. Representation

**Meaning:** A particular encoding, view, record, or model of an entity.

**Boundary:** Several representations may refer to the same WE.

**Registry:** `DEF-004`.

### 05. Perspective (`P`)

**Meaning:** A typed view selecting attributes, relations, measurements, evidence, and operations relevant to a question.

**Boundary:** A perspective is not automatically a mathematical metric.

**Registry:** `DEF-005`.

### 06. Perspective descriptor

**Meaning:** A versioned contract stating a perspective’s domain, semantics, units, applicability, provenance, uncertainty, and allowed operations.

**Boundary:** Descriptions without type and scope are not interchangeable.

**Registry:** `DEF-006`.

### 07. Mathematical metric (`d`)

**Meaning:** A distance function on a domain satisfying nonnegativity, identity of indiscernibles, symmetry, and triangle inequality.

**Boundary:** A similarity score or directional cost is not necessarily a metric.

**Registry:** `DEF-007`.

### 08. Measurement

**Meaning:** An observation or estimation of a property using a declared method, scale, and unit.

**Boundary:** Measurement values need not define distances.

**Registry:** `DEF-008`.

### 09. Evidence (`e`)

**Meaning:** A traceable observation, experiment, record, or argument used to support or challenge a claim.

**Boundary:** Evidence quality and dependence must be assessed.

**Registry:** `DEF-009`.

### 10. Provenance

**Meaning:** A record of origin, method, transformation, timestamp, version, and custody of evidence or models.

**Boundary:** A citation alone may not provide reproducible provenance.

**Registry:** `DEF-009`.

### 11. WE Hybrid Differential Tree (`WE-HDT`)

**Meaning:** A proposed perspective-aware localization and resolution structure that combines candidate search with metric or relational differentiation.

**Boundary:** Euclidean-first routing is optional, not a universal requirement.

**Registry:** `DEF-010`.

### 12. Candidate localization

**Meaning:** A search stage producing a bounded or ranked set of potentially relevant entities or nodes.

**Boundary:** A candidate list is not a verified answer.

**Registry:** `DEF-010`.

### 13. Exact resolution

**Meaning:** A stage applying the declared query and perspective contracts to candidate results.

**Boundary:** Exactness depends on completeness of candidate generation and the resolver.

**Registry:** `DEF-010`.

### 14. Two-phase search (`TPS`)

**Meaning:** A coarse candidate-generation stage followed by a finer validation or resolution stage.

**Boundary:** A speedup cannot be presumed without workload and correctness evidence.

**Registry:** `DEF-010`.

### 15. Variable-Size Blocks (`VSB`)

**Meaning:** A proposed data partitioning strategy with blocks whose extents or populations can vary by workload or local structure.

**Boundary:** Variable-sized partitions also exist in established index structures.

**Registry:** `DEF-011`.

### 16. Perspective-Adaptive Variable Blocks (`PAVB`)

**Meaning:** Variable-sized partitions whose organization can respond to perspective and query characteristics.

**Boundary:** Partition adaptation does not imply intelligent reasoning.

**Registry:** `DEF-011`.

### 17. Adaptive Variable-Intelligence Blocks (`AVIB`)

**Meaning:** Blocks whose partitioning and assigned reasoning capabilities may evolve along separate axes.

**Boundary:** Larger blocks need not have more intelligence, or vice versa.

**Registry:** `DEF-012`.

### 18. Metric Leaf Intelligence Unit (`MLIU`)

**Meaning:** A scoped intelligence capability attached to a logical metric or perspective leaf, supporting evidence-aware operations.

**Boundary:** A leaf is logical; it need not be a physical tree leaf or an independent LLM agent.

**Registry:** `DEF-013`.

### 19. Locate

**Meaning:** Find candidate entities, perspectives, or structural addresses.

**Boundary:** Locating is not resolving identity.

**Registry:** `DEF-014`.

### 20. Resolve

**Meaning:** Evaluate candidates against explicit identity, metric, relation, or query contracts.

**Boundary:** A plausible candidate may still fail resolution.

**Registry:** `DEF-014`.

### 21. Relate

**Meaning:** Construct or evaluate typed relationships between entities or perspectives.

**Boundary:** Relationships may be asymmetric and uncertain.

**Registry:** `DEF-014`.

### 22. Infer

**Meaning:** Produce a qualified conclusion from premises, models, and evidence.

**Boundary:** Inference must retain uncertainty and provenance.

**Registry:** `DEF-014`.

### 23. Question

**Meaning:** Generate a testable question from uncertainty, residuals, or structural gaps.

**Boundary:** Question generation is not answer validation.

**Registry:** `DEF-014`.

### 24. Evolve

**Meaning:** Propose and evaluate changes to models, structures, or policies under contracts.

**Boundary:** Evolution is not automatically improvement.

**Registry:** `DEF-014`.

### 25. Two-Ways CCC

**Meaning:** A forward-and-reverse cycle coupling accountable answers with residual-driven questioning and structural exploration.

**Boundary:** The reverse path must not treat its own conjectures as independent evidence.

**Registry:** `DEF-015`.

### 26. Forward CCC

**Meaning:** Apply current models, constraints, and evidence to answer or evaluate a query.

**Boundary:** Outputs remain conditional on the active contracts.

**Registry:** `DEF-015`.

### 27. Backward CCC

**Meaning:** Use unexplained outcomes to generate questions, hypotheses, and candidate perspectives.

**Boundary:** Backward generation does not establish causality.

**Registry:** `DEF-015`.

### 28. Cross-metric discovery

**Meaning:** Identify candidate relations or explanations spanning two or more typed perspectives.

**Boundary:** Requires explicit transformations and compatibility checks.

**Registry:** `DEF-016`.

### 29. Residual (`r`)

**Meaning:** A traceable discrepancy between an expectation and an observation under a declared model and comparison rule.

**Boundary:** Not every residual is noise, and not every residual indicates a new mechanism.

**Registry:** `DEF-017`.

### 30. Residual registry

**Meaning:** A versioned collection of residual records, linked evidence, candidate explanations, and resolution status.

**Boundary:** Unresolved records must not silently disappear.

**Registry:** `DEF-017`.

### 31. Residual-first discovery

**Meaning:** A research workflow that preserves unexplained discrepancies as inputs to questions and validation.

**Boundary:** Residuals initiate investigation, not proof.

**Registry:** `DEF-018`.

### 32. Scientific hypothesis (`H`)

**Meaning:** A claim framed so that observations or tests could challenge it within a declared scope.

**Boundary:** A suggestive pattern is not a validated hypothesis.

**Registry:** `DEF-019`.

### 33. Metric discovery

**Meaning:** Generate and test candidate measurement, distance, similarity, or relation structures.

**Boundary:** Only candidates satisfying metric axioms should be called mathematical metrics.

**Registry:** `DEF-020`.

### 34. Perspective evolution

**Meaning:** Versioned revision, extension, split, or retirement of perspectives after evaluation.

**Boundary:** Avoid silent semantic drift.

**Registry:** `DEF-020`.

### 35. Definition Evolution Loop (`DEL`)

**Meaning:** A governed cycle from counterexample or residual through analysis, definition revision, conformance, and relay.

**Boundary:** A patch that handles one example may break the general contract.

**Registry:** `DEF-021`.

### 36. State (`S`)

**Meaning:** A typed snapshot of relevant world, knowledge, operational, or structural variables for a transition system.

**Boundary:** A state representation is not necessarily the entire world.

**Registry:** `DEF-022`.

### 37. State container

**Meaning:** A structured holder for state, constraints, history, evidence, and applicable transitions.

**Boundary:** Its contents and equivalence criteria are application-specific.

**Registry:** `DEF-022`.

### 38. Delta (`Δ`)

**Meaning:** A typed change proposal or difference between declared states or representations.

**Boundary:** Different delta kinds have different semantics and rollback limits.

**Registry:** `DEF-023`.

### 39. World Delta (`ΔW`)

**Meaning:** A change in the modeled world or entity itself.

**Boundary:** Updating a database record does not necessarily change the world.

**Registry:** `DEF-023`.

### 40. Observation Delta (`ΔO`)

**Meaning:** A change in recorded observations, including new data or corrections.

**Boundary:** May occur without world change.

**Registry:** `DEF-023`.

### 41. Knowledge / Epistemic Delta (`ΔK`)

**Meaning:** A revision in beliefs, estimates, hypotheses, or explanations.

**Boundary:** A revised model does not imply that the external world changed.

**Registry:** `DEF-023`.

### 42. Structural / Operational Delta (`ΔS`)

**Meaning:** A persistent change to index topology, block membership, durable service organization, or a versioned operational policy.

**Boundary:** Task-scoped activation, masking, and computation-path selection are not automatically Structural Deltas; a reindex is not an entity mutation.

**Registry:** `DEF-023`.

### 42A. Activation / Mask Delta (`ΔA`)

**Meaning:** A task-scoped change in the *effective computational view*—which eligible nodes, edges, perspectives, operations, depths, or budgets are activated—without necessarily changing persistent topology or epistemic claims.

**Boundary:** `ΔA ≠ ΔS ≠ ΔK`. A persisted change to a durable mask policy may also require a separately typed `ΔS`.

**Contract:** `docs/WE-SIO-009`, `specs/SPEC-003`. **Registry status:** Candidate addition; assign a stable DEF ID in the Definition Registry rather than reusing `DEF-023` without review.

### 43. Constrained Delta Evolution (`CDE`)

**Meaning:** A proposed framework for generating, selecting, and validating state transitions under explicit constraints and evolution policies.

**Boundary:** The minimal kernel and distinct value beyond generic state-transition systems remain research questions.

**Registry:** `DEF-024`.

### 44. Applicability contract

**Meaning:** A predicate and supporting evidence specifying when a delta may legally apply.

**Boundary:** Legal application does not guarantee a good outcome.

**Registry:** `DEF-024`.

### 45. Path memory

**Meaning:** History retained to enforce constraints, avoid cycles, or explain decisions.

**Boundary:** Its scope and retention must be declared.

**Registry:** `DEF-025`.

### 46. No-Delta-Reuse

**Meaning:** An optional policy prohibiting repeated deltas along a defined path.

**Boundary:** Not a universal CDE axiom; chess allows legally repeated moves or positions.

**Registry:** `DEF-025`.

### 47. Loop-back control

**Meaning:** A policy for detecting, permitting, limiting, or terminating cyclic transitions.

**Boundary:** Some domains require cycles rather than forbidding them.

**Registry:** `DEF-026`.

### 48. Self-Modeling Entity (`SME`)

**Meaning:** A WE that maintains, evaluates, and revises a model of its own capabilities, history, or state.

**Boundary:** A self-model is not the self, nor evidence of consciousness.

**Registry:** `DEF-027`.

### 49. Subjective Structural Entity (`SSE`)

**Meaning:** A candidate research category concerning subject-relative structural modeling and evaluation.

**Boundary:** Subjective experience is not established by functional self-report.

**Registry:** `DEF-028`.

### 50. Self-reference

**Meaning:** A model or operation that explicitly refers to the entity or system producing it.

**Boundary:** Can be syntactic or functional without implying phenomenal awareness.

**Registry:** `DEF-027`.

### 51. Agent

**Meaning:** A bounded component or actor with declared capabilities, state, goals, permissions, and outputs.

**Boundary:** Multiple agents need not be independent sources of evidence.

**Registry:** `DEF-029`.

### 52. Relay

**Meaning:** A traceable handoff of work, evidence, questions, or capability between stages or agents.

**Boundary:** Repetition can be a relay when it accumulates useful observations.

**Registry:** `DEF-030`.

### 53. Collective Learning

**Meaning:** Improvement across participants through validated and reusable evidence, models, methods, or structures.

**Boundary:** Consensus or agent count alone is not learning.

**Registry:** `DEF-031`.

### 54. SIF Localization / Addressing

**Meaning:** The Structural Intelligence Framework function that locates problems, capabilities, entities, states, and actionable structures.

**Boundary:** WE-HDT and CDE are candidate complementary methods, not proven universal pillars.

**Registry:** `DEF-032`.

## 2A. Newly refined epistemic, masking, and SQL-facing terminology

These definitions extend the initial v0.1.0 vocabulary. They are **proposed contract terms**, not claims of experimentally established capabilities. New stable `DEF` identifiers should be assigned during the `DEFINITION-REGISTRY.md` update; existing identifiers remain unchanged.

### E01. Epistemic Separation

**Meaning:** A logical separation between evidence-supported established claims, open or unverified knowledge, and qualified residual evidence, including their scope, versions, and provenance.

**Boundary:** Logical separation does not require physically separate databases. Physical co-location must not erase semantic distinctions.

**Contracts:** `specs/SPEC-005` (ESC); `extensions/EXT-005`.

### E02. Established Knowledge (`EK`)

**Meaning:** A claim supported under declared evidence, perspective, context, time, validation criteria, and version.

**Boundary:** “Established” is scope-relative and revisable, not absolute truth or permanent certainty.

### E03. Open Knowledge (`OK`)

**Meaning:** Unanswered questions, unknown variables, untested hypotheses, contested claims, and unresolved possibilities tracked without pretending they have been verified.

**Boundary:** An unknown is not automatically a residual; absence of information is not a demonstrated model failure.

### E04. Residual Evidence Registry (`RER`)

**Meaning:** An addressable collection of *qualified* discrepancies between observations and explicit baselines, expectations, constraints, or explanatory commitments under typed comparison contracts.

**Boundary:** RER is not a miscellaneous “unknowns bucket.” A SQL `NULL`, unmeasured attribute, or missing prediction alone is not admissible residual evidence.

**Minimum fields:** Entity and perspective scope; baseline/reference/version; observation and source lineage; comparator and discrepancy; uncertainty; qualification status; reviewer/policy; and revision history.

### E05. Residual Qualification / RER Admission

**Meaning:** A governed decision that a candidate discrepancy has a meaningful baseline, comparable observation, adequate provenance, uncertainty characterization, and explicit status.

**Boundary:** Qualified residual evidence does not prove a new mechanism, causal relation, or law.

**Status examples:** Provisional, qualified, rejected, superseded. These are evidence-processing states, not levels of scientific truth.

### E06. Residual Diagnosis

**Meaning:** Investigation of competing explanations for a discrepancy, including sensor error, miscalibration, confounding, selection bias, data leakage, distribution shift, model misspecification, or a potentially missing phenomenon.

**Boundary:** Diagnosing a data artifact is a legitimate scientific outcome; not every residual warrants metric discovery.

### E07. Knowledge Promotion

**Meaning:** A versioned, evidence-reviewed transition of a claim or perspective from candidate/open status to *established for a declared scope*.

**Boundary:** Agent consensus, repeated model execution, or retrieval utility alone do not satisfy independent validation. Promotion is `ΔK`, not necessarily `ΔS`.

### E08. Knowledge Demotion / Withdrawal

**Meaning:** An evidence-governed narrowing, suspension, or retraction of previously accepted knowledge, with dependency review and preserved audit history subject to lawful retention constraints.

**Boundary:** Epistemic rollback cannot reverse an irreversible physical event.

### E09. Mask-First Structural Intelligence (`MFSI`)

**Meaning:** A candidate computational strategy that first selects a task-appropriate view over mature structures, reusing existing pathways before costly regeneration or reconstruction when correctness and net benefit permit.

**Boundary:** A heuristic, not a universal optimality principle. Stale or corrupt structures and incompatible guarantees may require immediate rebuild.

**Heuristic:** *Mask before Rebuild; Reuse before Regenerate; Validate before Promote.*

### E10. Mask

**Meaning:** A versioned, authorized selection rule over eligible nodes, edges, metrics, operations, depth, or resource budgets for a task.

**Boundary:** A mask is not deletion, a proof of irrelevance, a substitute for source authorization, or automatically a persistent structural mutation.

### E11. Unmask / Remask

**Meaning:** `Unmask` broadens or restores the active eligible view within authorization; `Remask` recomputes selection after context, feedback, evidence, or policy changes.

**Boundary:** Unmasking must not bypass access controls. Remasking cannot silently remove candidates when exactness is promised.

### E12. Active Computational View (`ACV`)

**Meaning:** The effective, task-scoped computation graph or selection over a versioned underlying substrate, perspective definitions, and authorized resources.

**Boundary:** `ACV ≠ persistent WE-HDT topology`. An active view can change while the substrate remains unchanged.

**Contract attributes:** Task/context, principal and authorization, substrate/perspective versions, selection policy, completeness guarantee, budget, and provenance.

### E13. Mature-Structure Preservation

**Meaning:** A design preference to retain validated knowledge pathways and durable indexing structures where selective reuse, local adaptation, or masking is sufficient.

**Boundary:** Preservation does not outrank correctness, privacy, security, or demonstrated need to rebuild.

### E14. Coverage-Safe Mask

**Meaning:** A mask that preserves the candidate superset or recall guarantee required by its declared retrieval or discovery contract.

**Boundary:** A high-scoring or apparently relevant mask is not necessarily coverage-safe. Exact retrieval needs a proof, conservative coverage, or safe full-view fallback.

### E15. Mask Policy Invalidation

**Meaning:** Revalidation or replacement of a cached mask when relevant source data, schema, perspective definition, authorization, policy, or structural versions change.

**Boundary:** Reusing a stale mask may create silent omissions or security failures.

### E16. Five-Way Delta Taxonomy

**Meaning:** A research-level classification separating `ΔW` (world), `ΔO` (observation), `ΔK` (knowledge), `ΔS` (persistent structure), and `ΔA` (activation/mask).

**Boundary:** These are semantic types, not proof that all real workflows have exactly one delta. A composite event can contain several separately auditable types.

### E17. SQL-Native Structural Intelligence

**Meaning:** A proposed WE-SIO integration in which established SQL engines provide source data, schema, transactions, indexes, queries, and security controls, while SI layers provide typed entity/perspective mapping, residual investigation, and governed knowledge evolution.

**Boundary:** SQL tables are not necessarily entity types; rows are not necessarily world entities; columns are not automatically mathematical metrics; JOINs do not prove identity.

### E18. SQL Epistemic Missingness

**Meaning:** Interpretation of absent, unknown, withheld, inapplicable, or not-yet-observed values under an explicit missingness contract.

**Boundary:** SQL `NULL` alone cannot determine whether something is an unknown, negative observation, contradiction, or residual.

### E19. Source-State Delta

**Meaning:** A change in recorded source-system state, such as an SQL `UPDATE`, that must be distinguished from a claim about an external-world event.

**Boundary:** A source update may accompany `ΔO`, `ΔK`, or `ΔW`, but does not by itself prove any physical change.

### E20. Evidence Independence

**Meaning:** The degree to which supporting observations or analyses originate from genuinely distinct sources and error processes.

**Boundary:** Multiple agents citing the same dataset, derived measurements, or copied reports are not independent replications.

### E21. Metric Candidate versus Perspective Candidate

**Meaning:** A metric candidate proposes a distance function with axioms on a declared domain; a perspective candidate may instead be a measurement, similarity, directional score, or typed relation.

**Boundary:** A useful comparator is not automatically a mathematical metric; metric pruning requires verified mathematical guarantees.

### E22. Epistemic and Structural Governance Boundary

**Meaning:** The separation of evidence/claim-status decisions (`SPEC-005`) from node, block, mask, and active-view computation contracts (`SPEC-003`).

**Boundary:** Changing a computation view cannot automatically validate a scientific claim; accepting a new claim does not necessarily require a new physical index.

## 3. Supporting terms and methodological vocabulary

### S01. Similarity

**Meaning:** A score or relation indicating resemblance under declared features and calibration.

**Boundary:** May not satisfy symmetry, metric axioms, or identity semantics.

### S02. Directional relation

**Meaning:** A typed relation whose value or meaning may depend on orientation or ordered endpoints.

**Boundary:** Do not force symmetry without a justified contract.

### S03. Euclidean distance (`L2`)

**Meaning:** The square root of the sum of squared coordinate differences in a compatible Euclidean coordinate system.

**Boundary:** Not defined for arbitrary abstract entities without an embedding.

### S04. Identity of indiscernibles

**Meaning:** For a mathematical metric, d(x,y)=0 if and only if x=y on the declared domain.

**Boundary:** Zero feature distance need not imply real-world entity identity.

### S05. Triangle inequality

**Meaning:** For a metric, d(x,z) ≤ d(x,y)+d(y,z).

**Boundary:** May fail for arbitrary learned dissimilarities.

### S06. Typed contract

**Meaning:** An explicit declaration of permitted values, operations, assumptions, and failure conditions.

**Boundary:** Type matching is necessary but not sufficient for empirical validity.

### S07. Conformance test

**Meaning:** A repeatable test checking an implementation or artifact against a declared contract.

**Boundary:** Passing tests is not a proof of every intended property.

### S08. Counterexample (`CE`)

**Meaning:** A constructed or observed case challenging a stated definition, invariant, or hypothesis.

**Boundary:** Must specify exactly which claim it challenges.

### S09. Explicit leftover

**Meaning:** A preserved unanswered question, untested assumption, failed attempt, or unresolved residual.

**Boundary:** Should not be disguised as a completed result.

### S10. Research trace

**Meaning:** A linked record of questions, hypotheses, definitions, decisions, evidence, counterexamples, and revisions.

**Boundary:** A synthesis is not a verbatim transcript.

### S11. Research relay package

**Meaning:** A transferable bundle of contracts, methods, evidence, negative results, versions, and next questions.

**Boundary:** Must preserve source provenance and limitations.

### S12. Evidence dependence

**Meaning:** Correlation or shared provenance among apparently separate observations or agents.

**Boundary:** Multiple agreeing outputs may count as one underlying evidence source.

### S13. Independent replication

**Meaning:** Repetition of a test with meaningfully independent data, process, or investigators.

**Boundary:** Re-running the same pipeline is not independent replication.

### S14. Calibration

**Meaning:** Agreement between predicted probabilities or uncertainty claims and observed frequencies under a stated evaluation protocol.

**Boundary:** Confidence statements alone do not establish calibration.

### S15. Confounding

**Meaning:** A factor associated with both an explanatory variable and an outcome that can distort inferred relations.

**Boundary:** Residual correlations alone cannot remove confounding.

### S16. Data leakage

**Meaning:** Use of information in evaluation or training that would not legitimately be available at the decision point.

**Boundary:** Can produce illusory discovery or predictive gains.

### S17. Ablation study

**Meaning:** A controlled comparison removing a proposed component to estimate its contribution.

**Boundary:** Requires matched budgets and workloads.

### S18. Candidate recall

**Meaning:** Fraction of truly relevant entities retained after candidate generation.

**Boundary:** Low recall cannot be repaired by an exact downstream resolver.

### S19. k-d tree

**Meaning:** A spatial search tree recursively partitioning a coordinate space, commonly by axis-aligned splits.

**Boundary:** Can already create unequal partitions; comparative novelty must be demonstrated.

### S20. Adaptive branching (`M→N`)

**Meaning:** A transition mechanism allowing a state to generate and select a variable number of successors.

**Boundary:** Branching policies require resource and correctness controls.

### S21. NoSubtree

**Meaning:** A policy or structural record that rules out exploration of a specified branch under stated assumptions.

**Boundary:** Pruning must be justified and versioned.

### S22. Governance gate

**Meaning:** A required check before promoting a hypothesis, metric, definition, or system change.

**Boundary:** A gate is a process control, not an empirical guarantee.

### S23. Open-ended evolution

**Meaning:** A process allowing new perspectives, operations, or structural hypotheses to be proposed over time.

**Boundary:** Open-ended does not mean unconstrained or unbounded resource use.

### S24. Structural intelligence (`SI`)

**Meaning:** A research orientation treating intelligence as organized, typed, governed, and evolvable structures and operations.

**Boundary:** No single proposed implementation defines all intelligence.

### S25. Autonomous Questioning Structural Intelligence (`AQSI`)

**Meaning:** A related research approach to generating and evaluating questions as part of intelligence evolution.

**Boundary:** Generated questions need validation and priority control.

### S26. Universal Intelligence Evolution and Relay Unit (`UIERU`)

**Meaning:** A related architecture for structural intelligence composition, relay, and evolution.

**Boundary:** Its proposed mechanisms require domain-specific conformance.

### S27. Subjective Structural Intelligence (`SSI`)

**Meaning:** A related research program studying subject boundaries, self-models, values, and subjective structural perspectives.

**Boundary:** Functional models do not resolve the philosophical problem of experience.

### S28. Structural Intelligence Framework (`SIF`)

**Meaning:** A broader framework organizing problem/capability mapping, localization, node intelligence, and control.

**Boundary:** The integration of WE-SIO remains an architectural proposal.

## 4. Critical non-equivalences

| Distinction | Why it matters |
|---|---|
| Entity identity ≠ similarity | Similar records may represent different entities; different records may represent one entity. |
| Perspective ≠ mathematical metric | A perspective can be relational, temporal, categorical, or directional. |
| Measurement ≠ metric distance | A measured number does not establish metric axioms. |
| Candidate localization ≠ resolution | An index proposes candidates; a contract-qualified resolver determines matches. |
| Index hierarchy ≠ intelligence hierarchy | Physical partitioning and reasoning scope can evolve separately. |
| Unknown ≠ qualified residual | Unknown variables, SQL NULLs, and untested ideas lack a required observation–baseline comparison. |\n| Established Knowledge ≠ immutable truth | Acceptance is scoped, versioned, and revisable. |\n| RER ≠ Open Knowledge bucket | RER requires qualified evidence of a discrepancy; open questions need not have a baseline. |\n| Mask ≠ deletion or authorization | Masks select eligible computation but cannot grant access or erase evidence. |\n| Activation Delta ≠ Structural Delta | A task-scoped active view may change without modifying persistent topology. |\n| Source-state update ≠ World Delta | An SQL UPDATE is not evidence by itself of a physical event. |\n| Residual ≠ novel mechanism | Residuals may reflect error, confounding, noise, or model inadequacy. |
| World Delta ≠ Epistemic Delta | Reality can change without a belief update, and beliefs can change without reality changing. |
| No-Delta-Reuse ≠ universal CDE invariant | Repetition may be legal or necessary in chess and many dynamic systems. |
| Self-model ≠ subjective experience | Functional self-monitoring cannot by itself establish consciousness. |
| Agent agreement ≠ independent evidence | Shared data and model ancestry may correlate outputs. |
| Conformance ≠ empirical effectiveness | Correctly implementing a contract does not demonstrate improved performance. |
| Proposed architecture ≠ validated system | WE-HDT, AVIB, and SIF integrations remain research proposals. |

## 5. Compact notation and type discipline

| Symbol | Intended meaning | Contract note |
|---|---|---|
| `WE` | World Entity | Identity scoped to domain and evidence |
| `P_i` | Perspective i | Type, units, version, and provenance required |
| `d_P(x,y)` | Distance in perspective P | Call a *metric* only if axioms hold |
| `s_P(x,y)` | Similarity under P | Not automatically symmetric |
| `R_P(x,y)` | Typed relation under P | Direction and scope explicit |
| `r = y_obs − y_pred` | Example scalar residual | Comparison and measurement semantics required |
| `ΔW` | World Delta | Actual modeled-world change |
| `ΔO` | Observation Delta | Data acquisition/correction |
| `ΔK` | Knowledge/Epistemic Delta | Belief or model revision |
| `ΔS` | Structural Delta | Persistent index, topology, or durable policy change |\n| `ΔA` | Activation/Mask Delta | Task-scoped active computational view selection |
| `H_i` | Testable hypothesis | Falsification and evidence status explicit |
| `CE_i` | Counterexample | Target claim and reproduction steps explicit |

## 6. Abbreviation index

| Abbreviation | Expansion |
|---|---|
| **WE-SIO** | World Entity and Structural Intelligence Operations |
| **WE** | World Entity |
| **WE-HDT** | World Entity Hybrid Differential Tree |
| **VSB** | Variable-Size Blocks |
| **TPS** | Two-Phase Search |
| **PAVB** | Perspective-Adaptive Variable Blocks |
| **AVIB** | Adaptive Variable-Intelligence Blocks |
| **MLIU** | Metric Leaf Intelligence Unit |
| **CCC** | Continuous–Correctable–Constructive (project usage; see formal paper for precise semantics) |
| **ACV** | Active Computational View |\n| **MFSI** | Mask-First Structural Intelligence |\n| **EK** | Established Knowledge |\n| **OK** | Open Knowledge |\n| **RER** | Residual Evidence Registry |\n| **ESC** | Epistemic Separation Contract |\n| **RQC** | Residual Qualification Contract |\n| **KPC** | Knowledge Promotion Contract |\n| **MIC** | Mask-First Investigation Contract |\n| **CDE** | Constrained Delta Evolution |
| **D-BTP** | Dynamic Bucket Tree of Permutation |
| **DEL** | Definition Evolution Loop |
| **SME** | Self-Modeling Entity |
| **SSE** | Subjective Structural Entity (candidate) |
| **SI** | Structural Intelligence |
| **SIF** | Structural Intelligence Framework |
| **SSI** | Subjective Structural Intelligence |
| **AQSI** | Autonomous Questioning Structural Intelligence |
| **UIERU** | Universal Intelligence Evolution and Relay Unit |
| **ADR** | Architecture Decision Record |
| **DOI** | Digital Object Identifier |

## 7. Where to find formal details

- **Definitions and evolution:** [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md), [`docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`](docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md).
- **Identity and perspectives:** [`specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md`](specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md).
- **Metric/relational correctness:** [`specs/SPEC-002-Euclidean-Metric-and-Relational-Index-Conformance.md`](specs/SPEC-002-Euclidean-Metric-and-Relational-Index-Conformance.md).
- **WE-HDT and MLIU:** [`specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`](specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md).
- **Operations and CCC:** [`specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md`](specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md).
- **Residuals and metric discovery:** [`specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md`](specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md).
- **Mask-first and epistemic separation:** [`extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`](extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md).\n- **SQL-native integration:** [`extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`](extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md).\n- **Five-way deltas:** [`docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`](docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md).\n- **Research governance:** [`specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md`](specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md).
- **Challenges and evidence:** [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md), [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md), [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md).

## 8. Terminology maintenance protocol

1. **Propose:** record a candidate term and the precise question it answers.
2. **Type:** identify whether it names an entity, relation, mathematical object, operation, or hypothesis.
3. **Bound:** state at least one non-equivalence and one counterexample.
4. **Contract:** link to a `DEF` entry or propose a new immutable ID.
5. **Test:** provide conformance probes and empirical validation separately.
6. **Revise:** log version, rationale, dependencies, and regression effects.
7. **Relay:** preserve dissent, failures, and explicit leftovers.

**Open terminology questions:** The exact operational expansion and contract of CCC should remain tied to its original specification; the minimal nontrivial kernel of CDE remains to be demonstrated; the SSE category is a research proposal rather than an empirical classification.

---

*WE-SIO v0.1.0 — Glossary. Research artifact, not an assertion of completed empirical validation.*
