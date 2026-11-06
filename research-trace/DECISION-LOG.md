# WE-SIO — Decision Log

**Repository:** World-Entity-and-Structural-Intelligence-Operations  
**Release:** v0.1.0 (research proposal)  
**Document class:** Research Trace / Architecture Decision Records (ADRs)  
**Prepared:** 2026-11-05  
**Research contributors:** Sizhe Tan & GPT-Obot  
**Evidence status:** Design rationale and proposed decisions; not an empirical validation report.

> **Purpose.** Record why a design choice was made, what alternatives remain viable, what evidence would change the choice, and what must be carried forward as an explicit leftover. A decision log is not a claim of priority, proof, or a verbatim transcript.

## 1. Scope, provenance, and decision semantics

This register reconstructs the design rationale reflected in the WE-SIO research corpus. The entries are **editorial syntheses** of research choices, not authenticated quotations or timestamped meeting minutes. The preparation date is not asserted to be the exact moment every idea first arose. Each decision should be checked against the relevant source document before a DOI release; any discrepancy is resolved by an appended amendment rather than silent rewriting.

**Decision states:** `Proposed`, `Adopted-for-v0.1.0`, `Conditional`, `Deferred`, `Superseded`, `Rejected-as-universal`. “Adopted” means selected as a specification or research design, **not** empirically proven. “Rejected-as-universal” means the rule may still be appropriate under an explicit application contract.

**Evidence levels:** `E0` conceptual proposal; `E1` formal or synthetic conformance evidence; `E2` controlled comparative experiment; `E3` external-domain replication; `E4` independent replication. Entries start at E0 unless separately evidenced.

**Amendment protocol:** Preserve stable IDs; append date, author, prior/new state, rationale, affected definitions and tests, and a link to reproducible evidence. Never overwrite an adverse result. Decisions about terminology do not automatically alter runtime contracts.

## 2. Decision index

| ID | Decision | State | Key trade-off |
|---|---|---|---|
| ADR-001 | Keep World Entity separate from its representation | Adopted-for-v0.1.0 | Semantic identity versus storage convenience |
| ADR-002 | Use typed Perspective descriptors rather than untyped columns | Adopted-for-v0.1.0 | Expressivity versus schema complexity |
| ADR-003 | Make Euclidean-first localization optional | Adopted-for-v0.1.0 | Spatial speed versus abstract-domain coverage |
| ADR-004 | Separate candidate localization from evidence-based resolution | Adopted-for-v0.1.0 | Efficiency versus soundness |
| ADR-005 | Do not equate adaptive block sizes with algorithmic novelty | Conditional | Engineering optimization versus research novelty |
| ADR-006 | Keep partition granularity and intelligence capacity orthogonal | Adopted-for-v0.1.0 | Modularity versus coupling benefits |
| ADR-007 | Specify six SI operations at the metric leaf interface | Adopted-for-v0.1.0 | Interoperability versus overspecification |
| ADR-008 | Use Two-Ways CCC for accountable answers and questions | Adopted-for-v0.1.0 | Discovery potential versus circularity |
| ADR-009 | Make residuals first-class research objects | Adopted-for-v0.1.0 | Traceability versus storage burden |
| ADR-010 | Gate Metric/Perspective promotion through independent validation | Adopted-for-v0.1.0 | Open-ended generation versus rigor |
| ADR-011 | Distinguish world, observation, knowledge and structural deltas | Adopted-for-v0.1.0 | Ontological precision versus bookkeeping cost |
| ADR-012 | Treat CDE as a constrained state/delta evolution framework | Conditional | Generalization versus vacuity |
| ADR-013 | Reject universal No-Delta-Reuse | Rejected-as-universal | Path pruning versus legal recurrence |
| ADR-014 | Propose WE-HDT and CDE as complementary SIF localization pillars | Conditional | Architectural integration versus overlap |
| ADR-015 | Separate self-modeling competence from subjective experience | Adopted-for-v0.1.0 | Research reach versus unwarranted metaphysics |
| ADR-016 | Make definition evolution versioned and counterexample-driven | Adopted-for-v0.1.0 | Adaptability versus semantic instability |
| ADR-017 | Treat multi-agent agreement as potentially correlated evidence | Adopted-for-v0.1.0 | Collective throughput versus epistemic independence |
| ADR-018 | Preserve repeated execution as a relay of observations | Conditional | Learning opportunities versus redundant computation |
| ADR-019 | Keep research trace separate from experimental validation | Adopted-for-v0.1.0 | Transparency versus apparent certainty |
| ADR-020 | Publish explicit leftovers and failed alternatives | Adopted-for-v0.1.0 | Reproducibility versus editorial neatness |

## 3. Detailed architecture decision records

The sections below state **the selected research position** and the most important alternative, not a claim that a production implementation exists.

### ADR-001 — Keep World Entity separate from its representation

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance semantic identity versus storage convenience?
- **Context and rationale:** An entity can have multiple observations and representations; conflation breaks cross-source identity.
- **Alternative considered:** Use database row or metric vector as entity identity. **Why not as the default:** Source-scoped identifiers are convenient and often sufficient in closed datasets.
- **Chosen contract or research direction:** Require explicit entityRef, source record IDs, identity evidence and uncertainty; avoid asserting global identity from matching signatures.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Cross-source identity can remain unresolved; ambiguous merges must be reversible.
- **Related research:** CASE-001; SPEC-001; DEF-001–009.
- **Validation / challenge hooks:** CE-WE-001–040; SQL identity tests.

### ADR-002 — Use typed Perspective descriptors rather than untyped columns

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance expressivity versus schema complexity?
- **Context and rationale:** A numeric field need not be a metric; relational evidence may be asymmetric or directional.
- **Alternative considered:** Treat each SQL column or feature as a metric index. **Why not as the default:** Simple schema translation is cheap but loses mathematical and evidentiary semantics.
- **Chosen contract or research direction:** Specify domain, units, directionality, temporal validity, provenance, uncertainty and version; distinguish metric, measurement, similarity and relation.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Formal conformance for newly proposed Perspective types is incomplete.
- **Related research:** WE-SIO-002; SPEC-001/002; CASE-001.
- **Validation / challenge hooks:** Type-error and asymmetric-relation counterexamples.

### ADR-003 — Make Euclidean-first localization optional

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance spatial speed versus abstract-domain coverage?
- **Context and rationale:** Many entities lack meaningful Euclidean coordinates.
- **Alternative considered:** Require Euclidean candidate pruning for every WE query. **Why not as the default:** Efficient in geometric workloads but excludes symbolic and abstract entities.
- **Chosen contract or research direction:** Select localization route by declared Perspective and guarantee contract.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Benchmark routing overhead and mixed-domain retrieval.
- **Related research:** WE-SIO-003; SPEC-002/003; EXT-001.
- **Validation / challenge hooks:** Non-spatial entities and candidate-recall tests.

### ADR-004 — Separate candidate localization from evidence-based resolution

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance efficiency versus soundness?
- **Context and rationale:** Two-phase search permits broad cheap filtering followed by exact or calibrated resolution.
- **Alternative considered:** Declare the candidate stage itself an identity decision. **Why not as the default:** Fast but can create false merges and untraceable misses.
- **Chosen contract or research direction:** Expose candidate completeness/recall guarantees and resolver evidence; do not claim exactness without a proof or full fallback.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** High-dimensional, adversarial and skewed workload tests.
- **Related research:** WE-SIO-001/003; CASE-002; SPEC-003.
- **Validation / challenge hooks:** Candidate omission and adversarial index tests.

### ADR-005 — Do not equate adaptive block sizes with algorithmic novelty

- **Status / evidence:** `Conditional` / `E0`.
- **Decision question:** How should WE-SIO balance engineering optimization versus research novelty?
- **Context and rationale:** k-d trees already yield variable-size partitions; differentiation needs explicit workload, objective and measurements.
- **Alternative considered:** Claim VSB categorically outperforms k-d trees. **Why not as the default:** Unsupported and easily falsified by baseline choices.
- **Chosen contract or research direction:** Compare against tuned k-d tree, brute force, fixed blocks and other relevant indexes under matched budgets.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Formalize the specific VSB algorithm and independent benchmarks.
- **Related research:** CASE-002.
- **Validation / challenge hooks:** Skew, dimensionality and update-heavy counterexamples.

### ADR-006 — Keep partition granularity and intelligence capacity orthogonal

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance modularity versus coupling benefits?
- **Context and rationale:** PAVB controls partitions; AVIB controls which operations and budgets are activated.
- **Alternative considered:** Assign a heavyweight agent to every leaf. **Why not as the default:** Potentially prohibitive resource cost.
- **Chosen contract or research direction:** Permit light-weight MLIUs, delegated inference, split/merge and independent intelligence activation.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Quantify coordination and overhead thresholds.
- **Related research:** WE-SIO-004/005; SPEC-003.
- **Validation / challenge hooks:** Resource-budget and oscillation tests.

### ADR-007 — Specify six SI operations at the metric leaf interface

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance interoperability versus overspecification?
- **Context and rationale:** Locate, Resolve, Relate, Infer, Question, Evolve offer an operational vocabulary.
- **Alternative considered:** Mandate all six as continuously running local agents. **Why not as the default:** Expensive and not required for all data types.
- **Chosen contract or research direction:** Expose capabilities as optional contract-governed operations with resource budgets.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Prove interface sufficiency or revise with counterexamples.
- **Related research:** WE-SIO-005; SPEC-004.
- **Validation / challenge hooks:** Capability declaration and budget tests.

### ADR-008 — Use Two-Ways CCC for accountable answers and questions

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance discovery potential versus circularity?
- **Context and rationale:** Forward inference produces inspectable claims; reverse residual analysis proposes testable questions.
- **Alternative considered:** Treat reverse-generated hypotheses as validated answers. **Why not as the default:** Confuses candidate generation with evidence.
- **Chosen contract or research direction:** Separate generation, evidence gathering, independent validation and promotion.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Measure net discovery yield after leakage controls.
- **Related research:** WE-SIO-006/007; EXT-003; SPEC-004.
- **Validation / challenge hooks:** Circular reasoning and data leakage tests.

### ADR-009 — Make residuals first-class research objects

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance traceability versus storage burden?
- **Context and rationale:** Residuals can reveal mismatch but also noise, confounding or measurement failure.
- **Alternative considered:** Discard all residuals as noise or treat all as discoveries. **Why not as the default:** Either loses information or promotes false findings.
- **Chosen contract or research direction:** Index residual with expectation, observation, uncertainty, source, version, quality checks and status.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Estimate false discovery rates and retention costs.
- **Related research:** WE-SIO-007; SPEC-005; CASE-003.
- **Validation / challenge hooks:** Noise, confounding and missingness counterexamples.

### ADR-010 — Gate Metric/Perspective promotion through independent validation

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance open-ended generation versus rigor?
- **Context and rationale:** Novel candidate measures require semantic, formal and empirical checks.
- **Alternative considered:** Promote a learned numerical expression directly to mathematical metric. **Why not as the default:** Can violate symmetry, triangle inequality or domain validity.
- **Chosen contract or research direction:** Apply type-specific gates, holdout tests, robustness checks, governance review and rollback.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Validate on external datasets and new tasks.
- **Related research:** WE-SIO-008; EXT-003; SPEC-005.
- **Validation / challenge hooks:** Metric axiom and overfitting tests.

### ADR-011 — Distinguish world, observation, knowledge and structural deltas

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance ontological precision versus bookkeeping cost?
- **Context and rationale:** Editing a record or belief does not undo the underlying event.
- **Alternative considered:** Represent all updates as a single untyped delta. **Why not as the default:** Simple but obscures causality and auditability.
- **Chosen contract or research direction:** Type deltas and separate reversible representation updates from irreversible world events.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Operational reconciliation of concurrent and late data.
- **Related research:** WE-SIO-009; CASE-003; SPEC-006.
- **Validation / challenge hooks:** Out-of-order observation and rollback tests.

### ADR-012 — Treat CDE as a constrained state/delta evolution framework

- **Status / evidence:** `Conditional` / `E0`.
- **Decision question:** How should WE-SIO balance generalization versus vacuity?
- **Context and rationale:** State, applicable delta, constraints and transitions provide a kernel, but added value beyond generic state-transition systems needs evidence.
- **Alternative considered:** Declare CDE universally novel or merely rename all transitions. **Why not as the default:** Neither yields testable differentiation.
- **Chosen contract or research direction:** Require explicit contracts, adaptive branch policies, residual guidance and benchmarks against established search/optimization baselines.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Identify minimal nontrivial CDE contribution and falsification cases.
- **Related research:** WE-SIO-009; CASE-004; EXT-001.
- **Validation / challenge hooks:** State-machine equivalence and baseline comparisons.

### ADR-013 — Reject universal No-Delta-Reuse

- **Status / evidence:** `Rejected-as-universal` / `E0`.
- **Decision question:** How should WE-SIO balance path pruning versus legal recurrence?
- **Context and rationale:** Chess permits recurring moves and states; no-reuse can be a D-BTP path policy but not a general CDE axiom.
- **Alternative considered:** Ban any repeated delta in all CDE paths. **Why not as the default:** Incorrect for recurrent domains and can remove legal solutions.
- **Chosen contract or research direction:** Make cycle, path-memory, repetition and termination policies explicit per application.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Formalize sufficient termination guarantees for each policy.
- **Related research:** CASE-004; DEF-022–026.
- **Validation / challenge hooks:** Chess repetition and transposition tests.

### ADR-014 — Propose WE-HDT and CDE as complementary SIF localization pillars

- **Status / evidence:** `Conditional` / `E0`.
- **Decision question:** How should WE-SIO balance architectural integration versus overlap?
- **Context and rationale:** WE-HDT localizes entities/evidence; CDE explores constrained state transitions and paths.
- **Alternative considered:** Make one subsystem replace the other. **Why not as the default:** Would obscure their different guarantees and use cases.
- **Chosen contract or research direction:** Integrate through typed SIF control-plane interfaces while keeping independent correctness contracts.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Demonstrate incremental benefit against simpler integration.
- **Related research:** EXT-001; WE-SIO-003/009.
- **Validation / challenge hooks:** Localization/search ablation tests.

### ADR-015 — Separate self-modeling competence from subjective experience

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance research reach versus unwarranted metaphysics?
- **Context and rationale:** A system can predict and revise its own capabilities without establishing phenomenal consciousness.
- **Alternative considered:** Treat self-reference as proof of subjective experience. **Why not as the default:** No accepted inference follows from self-description alone.
- **Chosen contract or research direction:** Use WE → SME → candidate SSE as distinct research categories with explicit evidentiary limits.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Operationalize self-model calibration and avoid consciousness claims.
- **Related research:** WE-SIO-010; CASE-005; EXT-004.
- **Validation / challenge hooks:** Self-report mimicry and calibration counterexamples.

### ADR-016 — Make definition evolution versioned and counterexample-driven

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance adaptability versus semantic instability?
- **Context and rationale:** Minimal invariants permit extension without silently redefining core terms.
- **Alternative considered:** Fix a closed inventory or redefine terms opportunistically. **Why not as the default:** Either blocks growth or makes claims unfalsifiable.
- **Chosen contract or research direction:** Record counterexample, proposed revision, regression impact, acceptance criteria and rollback.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Test cross-version compatibility and ontology drift.
- **Related research:** WE-SIO-011; SPEC-006; DEFINITION-REGISTRY.
- **Validation / challenge hooks:** Definition overfitting and vacuity tests.

### ADR-017 — Treat multi-agent agreement as potentially correlated evidence

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance collective throughput versus epistemic independence?
- **Context and rationale:** Shared training, sources and prompts can yield correlated errors.
- **Alternative considered:** Count every agreeing agent as independent confirmation. **Why not as the default:** Inflates confidence and suppresses counterevidence.
- **Chosen contract or research direction:** Track source lineage, agent dependencies, adversarial review and independent replication.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Quantify gain relative to single-agent and non-agent baselines.
- **Related research:** WE-SIO-012; EXT-002.
- **Validation / challenge hooks:** Correlated hallucination and consensus tests.

### ADR-018 — Preserve repeated execution as a relay of observations

- **Status / evidence:** `Conditional` / `E0`.
- **Decision question:** How should WE-SIO balance learning opportunities versus redundant computation?
- **Context and rationale:** Repeated work may accumulate longitudinal evidence when provenance and novelty are measured.
- **Alternative considered:** Treat every rerun as new independent evidence. **Why not as the default:** Duplicates can falsely strengthen conclusions.
- **Chosen contract or research direction:** Deduplicate evidence, version execution context and measure information gain.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Find when repeated execution pays its resource cost.
- **Related research:** EXT-002; WE-SIO-012.
- **Validation / challenge hooks:** Duplicate-evidence and no-gain tests.

### ADR-019 — Keep research trace separate from experimental validation

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance transparency versus apparent certainty?
- **Context and rationale:** A well-documented design is not a proven system.
- **Alternative considered:** Treat prose, registry counts or diagrams as benchmark results. **Why not as the default:** Misstates research maturity.
- **Chosen contract or research direction:** Tag all proposed hypotheses E0 and attach real artifacts before promotion.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Produce independent conformance and performance reports.
- **Related research:** HYPOTHESIS-REGISTRY; VALIDATION-ROADMAP.
- **Validation / challenge hooks:** Evidence provenance audits.

### ADR-020 — Publish explicit leftovers and failed alternatives

- **Status / evidence:** `Adopted-for-v0.1.0` / `E0`.
- **Decision question:** How should WE-SIO balance reproducibility versus editorial neatness?
- **Context and rationale:** Negative results and unresolved questions make future relay more useful.
- **Alternative considered:** Remove failed attempts from the release narrative. **Why not as the default:** Encourages repeated dead ends and hindsight bias.
- **Chosen contract or research direction:** Maintain immutable IDs, status changes and links to residuals/counterexamples.
- **Consequences:** The design must make its scope and failure modes observable. Any additional computational or governance overhead must be measured against simpler alternatives rather than assumed worthwhile.
- **Reversal / revision trigger:** A reproducible counterexample, violated invariant, unacceptable resource cost, or stronger baseline may require narrowing, replacing, or superseding this decision.
- **Explicit leftover:** Establish practical curation and retention thresholds.
- **Related research:** COUNTEREXAMPLE-REGISTRY; UNRESOLVED-RESIDUALS.
- **Validation / challenge hooks:** Traceability audit.

## 4. Cross-decision dependencies and conflict checks

| Dependency | Required consistency check | Failure response |
|---|---|---|
| ADR-001 → ADR-002/003 | Perspective descriptors do not become identity keys by accident | Separate identity resolution from index lookup |
| ADR-003/004 → ADR-005 | Candidate-stage recall guarantee is not inferred from partition adaptivity | Add exact fallback or declare approximate semantics |
| ADR-006/007 → ADR-017 | MLIU operation contracts remain usable by remote agents | Version interface and budget declarations |
| ADR-008/009 → ADR-010 | Residual-based hypothesis generation does not self-validate | Require independent data and adversarial review |
| ADR-011/012 → ADR-013 | Delta and cycle policies respect domain-specific state semantics | Narrow policy; rerun Chess conformance suite |
| ADR-012/014 → ADR-016 | CDE/SIF localization claims have non-vacuous testable interfaces | Defer pillar claim pending ablation |
| ADR-015 → ADR-016 | Self-model definitions do not imply subjective experience | Revise terminology and evidence boundary |
| ADR-017/018 → ADR-019/020 | Repeated or correlated outputs are not double-counted as independent evidence | Deduplicate, disclose lineage and preserve negative results |

## 5. Deferred alternatives and rejected universal claims

The following remain **available as context-specific choices**, not prohibited technologies:

1. **Relational databases and classical indexes:** useful as primary storage and reference baselines; WE-SIO must not claim to replace SQL.
2. **Euclidean and k-d-tree routing:** appropriate for geometric workloads, not mandatory for all entities.
3. **Fixed-size partitions:** potentially preferable for uniform workloads and predictable memory layouts.
4. **Single-agent pipelines:** often cheaper and easier to validate; multi-agent coordination must earn its cost.
5. **Purely statistical residual analysis:** a strong baseline against which structured discovery should be compared.
6. **No-Delta-Reuse:** may be sound in constrained permutation paths, but is not a universal state-evolution rule.
7. **Static ontologies:** can be appropriate for stable regulated interfaces; definition evolution requires change control.
8. **Self-report-based self-model evaluation:** insufficient alone; use externally observable calibration and behavior.

## 6. Release and audit gate

A decision may be cited as a **design commitment** when its status and specification are consistent. It may be cited as a **validated result** only when an evidence package includes: test definition; dataset/license and consent constraints; baseline configuration; code/version hashes; seed and compute budget; outcome metrics and uncertainty; negative results; independent review; and the associated hypothesis, definition, counterexample and ADR IDs.

### Audit checklist

- [ ] All ADR IDs unique, stable and linked from `CONTENTS.md` or `START-HERE.md`.
- [ ] No `Adopted-for-v0.1.0` entry is presented as experimentally proven.
- [ ] Every mathematical metric claim is checked against the relevant axioms.
- [ ] Every identity claim distinguishes record keys, signatures and entity identity.
- [ ] Candidate localization states its completeness or approximation guarantees.
- [ ] CDE policy examples preserve legal recurrence and application-specific termination.
- [ ] Residual-based claims have noise, confounding and leakage controls.
- [ ] Multi-agent evidence lineage identifies dependence and duplication.
- [ ] Self-modeling claims do not imply verified consciousness.
- [ ] Contradictions between registries are recorded and resolved by amendment.
- [ ] All external evidence is cited; absent experiments remain E0.

## 7. Amendment record template

```yaml
amendment_id: AMD-YYYYMMDD-NNN
decision_id: ADR-NNN
recorded_at: YYYY-MM-DD
recorded_by: contributor-or-team
previous_status: Proposed
new_status: Conditional
reason: "What changed and why"
evidence_level: E0
evidence_artifacts: []
challenging_counterexamples: []
affected_definitions: []
affected_hypotheses: []
conformance_tests_added: []
compatibility_impact: "none | minor | breaking"
rollback_or_migration: "Plan if required"
review_status: pending
```

## 8. Explicit leftovers for the next relay

| ID | Open issue | Next falsifiable action |
|---|---|---|
| DL-L01 | Formal, implementation-level VSB specification absent | Publish pseudocode and prove candidate coverage conditions |
| DL-L02 | Incremental benefit of WE-HDT over tuned indexes unknown | Matched-resource retrieval benchmark |
| DL-L03 | Cost/benefit of adaptive intelligence activation unknown | AVIB/MLIU ablation under latency and budget limits |
| DL-L04 | Reverse CCC may generate circular or low-value questions | Blind held-out discovery experiment |
| DL-L05 | Residual-driven metric discovery risks false discoveries | Preregistered controls and replication |
| DL-L06 | Minimal nontrivial CDE kernel not established | Compare with state-transition, DP, B&B and search baselines |
| DL-L07 | General cycle-policy guarantees incomplete | Formal Chess and non-Chess recurrence cases |
| DL-L08 | WE-HDT/CDE SIF integration untested | Interface conformance and integration ablation |
| DL-L09 | Multi-agent epistemic independence uncertain | Shared-source versus independent-source study |
| DL-L10 | Self-model utility and calibration unproven | External ground-truth capability prediction benchmark |
| DL-L11 | Definition evolution may destabilize compatibility | Version migration and regression suite |
| DL-L12 | Research trace requires source-level reconciliation | Review original source passages and annotate provenance |

## 9. Related documents

- `research-trace/ORIGIN-AND-RESEARCH-QUESTIONS.md`
- `research-trace/DISCUSSION-SYNTHESIS-2026-11-05.md`
- `research-trace/HYPOTHESIS-REGISTRY.md`
- `research-trace/DEFINITION-REGISTRY.md`
- `research-trace/COUNTEREXAMPLE-REGISTRY.md`
- `research-trace/UNRESOLVED-RESIDUALS.md` (planned)
- `VALIDATION-ROADMAP.md` (planned)
- `docs/WE-SIO-001` through `docs/WE-SIO-012`
- `specs/SPEC-001` through `specs/SPEC-006`
- `cases/CASE-001` through `cases/CASE-005`
- `extensions/EXT-001` through `extensions/EXT-004`

---

**Research position:** WE-SIO v0.1.0 is a structured proposal and a collective-learning relay artifact. The decisions above should make the work *more falsifiable*, not less. The next useful output is an evidence-backed experiment or a precisely documented counterexample, not another unsupported assertion of generality.
