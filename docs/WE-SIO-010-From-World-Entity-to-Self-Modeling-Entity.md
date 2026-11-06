# WE-SIO-010 — From World Entity to Self-Modeling Entity

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Hypothesis  
**Status:** Candidate architecture; not an empirical demonstration  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05

## Abstract

World Entity (WE) representation provides a means to describe identifiable entities through multiple perspective descriptors, including Euclidean, metric, directional, and relational views. This paper asks what changes when an entity is also capable of representing, monitoring, and revising a model of itself. We propose a **Self-Modeling Entity (SME)** as an operational extension of WE, not as a synonym for subjectivity or consciousness. We distinguish an external description of an entity from a self-maintained model, a feedback controller from a reflective self-model, and a self-model from a subjective structural entity. We develop candidate contracts for self-reference, action–observation loops, provenance, perspective disagreement, identity continuity, governance, and constrained self-model revision. The design integrates WE-HDT, Metric-Leaf Intelligence Units (MLIU), Two-Ways CCC, residual-first discovery, and Constrained Delta Evolution (CDE). It concludes with counterexamples, falsifiable hypotheses, conformance tests, and an explicit research relay.

**Keywords:** World Entity; Self-Modeling Entity; self-reference; self-model; Structural Intelligence; perspective; residual; CDE; SSI; Collective Learning.

## 1. Motivation and Scope

A world model may contain descriptions of vehicles, organizations, organisms, software services, or artificial agents. Such a description does not imply that the described entity has access to it. Conversely, an agent may maintain operational estimates of its own resources or actions without having a rich, explicit model of itself. These distinctions matter when extending WE-SIO from *modeling entities* to *entities that model themselves*.

The central research question is:

> Under what operational conditions can a World Entity be treated as a Self-Modeling Entity, and what additional intelligence operations become possible or necessary?

This is a systems and representation question. No claim about phenomenal consciousness, personhood, moral status, or biological equivalence follows from the proposed architecture.

### 1.1 Contributions proposed for investigation

1. A layered distinction between **WE**, **SME**, and a candidate **Subjective Structural Entity (SSE)**.
2. A minimal operational contract for an SME, with explicit uncertainty and failure states.
3. A separation of **world change**, **observation change**, **self-knowledge change**, and **structural adaptation**.
4. A two-way loop connecting self-predictions, observed outcomes, residuals, and revised self-perspectives.
5. An integration pathway with WE-HDT, MLIU, CDE, and the earlier Subjective Structural Intelligence (SSI) research.
6. A conformance-first, counterexample-driven validation agenda.

## 2. Three Levels of Entity Modeling

### 2.1 Level W — World Entity (WE)

A **World Entity** is an entity referent for which a system maintains one or more representations under explicit perspectives. An initial shorthand is:

`WE = Object[metricIdx]`

This shorthand is useful as a starting intuition but is not a sufficient universal definition: some perspectives are relational, directional, categorical, or not mathematical metrics. A fuller representation separates:

- **Entity reference / identity policy:** how the referent is distinguished and tracked;
- **Perspective descriptors:** what is measured or related and under what semantics;
- **Observations and hypotheses:** claims with provenance, time, and uncertainty;
- **Indexes and access paths:** retrieval mechanisms, which are not the entity itself.

An external observer can maintain a WE representation even when the entity has no modeling capability.

### 2.2 Level S — Self-Modeling Entity (SME)

An **SME** is a candidate operational system that maintains a representation whose referent includes the system itself, uses that representation in at least one consequential operation, observes relevant outcomes, and can revise the representation under an explicit update policy.

Proposed minimum conditions:

- **Self-reference:** an explicit, resolvable relation between the model and the modeled system;
- **Operational use:** the self-model affects prediction, planning, control, diagnosis, or question selection;
- **Feedback:** observations can be compared with self-model expectations;
- **Revision:** an authorized process can update self-model claims while preserving provenance;
- **Boundary awareness:** the model declares what belongs to the system, what is external, and what remains uncertain.

This is a **candidate research contract**, not a settled scientific definition of selfhood. A thermostat with a simple internal state may satisfy fragments of the contract without satisfying a richer operational-use or reflective-model criterion; the boundary should be tested rather than decided by terminology.

### 2.3 Level SS — Subjective Structural Entity (SSE), a research extension

An SSE is a possible higher-level functional research construct involving persistent identity history, subject-relative perspectives, valuation, goal selection, and autonomy constraints. These dimensions connect to SSI, but no single dimension proves subjective experience. The proposed progression is conceptual, not an inevitable developmental ladder:

```text
World Entity (WE)
  |  self-reference + operational self-model + feedback + revision
  v
Self-Modeling Entity (SME)
  |  candidate subject-relative valuation, identity continuity,
  |  autonomy / boundary contracts, and richer reflective processes
  v
Subjective Structural Entity (SSE) [research hypothesis]
```

An SME may remain entirely instrumental and externally governed. A system may have sophisticated internal monitoring without self-directed goals.

## 3. Minimal Semantic Kernel and Open Extensions

Following WE-SIO-011, the definition should capture invariant operational requirements rather than enumerate all possible implementations.

### 3.1 Candidate SME kernel

Let an SME candidate be represented as:

\[
\mathrm{SME}=(E, I_s, M_s, O, A, U, B)
\]

where:

- \(E\): entity referent and environment interface;
- \(I_s\): self-reference and identity-resolution policy;
- \(M_s\): versioned self-model;
- \(O\): observation and evidence interface;
- \(A\): actions or consequential operations influenced by the model;
- \(U\): authorized update and validation policy;
- \(B\): declared system boundaries, constraints, and permissions.

This tuple is a *working contract*. It is not a claim that these fields are necessary or sufficient for all possible self-modeling systems.

### 3.2 Optional extensions

Extensions may include episodic memory, counterfactual self-simulation, resource introspection, uncertainty calibration, social models of how others perceive the entity, goal revision, and multi-agent coordination. These should remain modular; requiring all of them would collapse a broad research category into one preferred implementation.

### 3.3 Avoiding trivial universality

If any controller with a state variable is called an SME, the concept risks adding little beyond existing feedback control. A useful operational threshold must demonstrate **incremental explanatory or engineering value**: explicit self-referential representation, consequential use, update traceability, and testable distinctions from a matched non-self-modeling baseline.

## 4. Self-Reference, Identity, and Boundary Contracts

Self-reference is not simply a field named `self`. The system must specify how the referent is resolved, which subsystems are included, and what changes preserve continuity.

**Candidate identity contract:**

```yaml
self_reference:
  entity_ref: <stable-reference>
  resolver_version: <version>
  boundary_policy: <declared-scope>
  identity_evidence: <provenance>
  unresolved_identity_conflicts: []
```

The example is illustrative, not a normative serialization format.

### 4.1 Boundary questions

A cloud service may migrate across machines; a robot may replace sensors; a collective agent may gain or lose members. Physical location, hardware identity, process identifier, and organizational role can disagree. Identity continuity must therefore be declared as a **policy with evidence and counterexamples**, not inferred from a single index.

### 4.2 Recursive self-reference

A model may represent its own model, producing a hierarchy such as \(M_s^{(0)}, M_s^{(1)}, \ldots\). Unrestricted recursion can be computationally unbounded or semantically circular. Candidate safeguards include bounded reflection depth, lazy materialization, versioned snapshots, and explicit stopping criteria. No infinite hierarchy is required for the minimal SME contract.

## 5. The Self-Model Action–Observation Loop

A simple operational formulation is:

\[
 a_t = \pi(M_s(t), W_s(t), G_s(t), C_t),
\]

\[
 o_{t+1} \sim \mathcal{O}(E_{t+1}, A_t),
\]

\[
 M_s(t+1)=U(M_s(t),a_t,o_{t+1},C_t),
\]

where \(W_s\) is the system's accessible world representation, \(G_s\) is a goal or task specification (possibly externally assigned), and \(C_t\) denotes constraints and evidence conditions. The stochastic observation notation permits noise and incomplete observability; it does not require a particular probabilistic implementation.

The key feature is **closed-loop self-model revision**. A predicted capability, resource level, failure mode, or behavioral tendency can be checked against observed outcomes. The resulting mismatch becomes a typed residual, not automatically a reason to rewrite the model.

### 5.1 Example: a delivery robot

A robot's self-model predicts battery endurance and turning radius. A route outcome differs from expectation. Candidate explanations include sensor drift, environmental conditions, battery degradation, model misspecification, or an external disturbance. A valid update pipeline first records the discrepancy, tests competing explanations, and only then revises an appropriate self-perspective.

### 5.2 Example: a software agent

A software agent predicts that it can complete a task within a tool budget. A tool fails or a permission is denied. The agent should update its operational capability estimate without confusing a temporary authorization failure with a permanent loss of skill. The distinction between *capability*, *access*, and *observation* is itself a perspective-design problem.

## 6. Multi-Perspective Self-Models

An SME can be represented under several simultaneous perspectives:

| Perspective | Example self-claim | Main failure mode |
|---|---|---|
| Physical / resource | battery, memory, latency | sensor error or stale telemetry |
| Functional | supported operations, task success | benchmark mismatch |
| Relational | membership, dependencies, permissions | changed external relationships |
| Historical | past states, decisions, commitments | corrupted or selective history |
| Predictive | expected behavior under conditions | distribution shift |
| Evaluative | goals, priorities, risk thresholds | inconsistent or unauthorized valuation |
| Social / external-view | how other agents estimate the entity | perspective conflation |

These views need not agree. A system may report high task competence while external evaluation shows failure. The disagreement should be recorded as an **evidence-bearing cross-perspective residual**, with provenance and uncertainty, rather than forcibly averaged away.

### 6.1 Self-view versus other-view

A system's self-description is evidence about what it reports, not necessarily ground truth about its capacities or intentions. WE-SIO should support both `selfPerspective` and `externalPerspective` descriptors, plus explicit source reliability and conflict handling. This connects to prior work on perspective-aware scoring and directional weak evidence.

## 7. WE-HDT and MLIU Integration

WE-HDT can supply a multi-perspective address space for the self-model. Euclidean indexing may accelerate spatial or resource-related queries; general metric and relational views can represent capability similarity, dependencies, or role constraints. **Euclidean-first remains optional**, and the physical index hierarchy need not mirror the intelligence abstraction hierarchy.

A Metric-Leaf Intelligence Unit (MLIU) may host or reference a self-model perspective through a lightweight contract:

```text
SelfModelPerspectiveUnit {
  entityRef
  selfReferencePolicy
  perspectiveDescriptor
  claimsAndPredictions
  observationsAndEvidence
  uncertaintyAndResiduals
  updatePolicy
  provenanceAndVersion
  permissionBoundary
  relayInterfaces
}
```

The MLIU need not be a separate agent or a physical tree leaf. Shared services and lazy activation can provide the necessary operations without agent-per-leaf overhead.

### 7.1 Six SI operations in self-modeling

1. **Locate:** find the relevant self-perspective, evidence, or historical state.
2. **Resolve:** interpret the claim using its descriptor, context, and version.
3. **Relate:** connect self-perspectives to one another and to external entities.
4. **Infer:** generate bounded, uncertainty-aware predictions about the system.
5. **Question:** formulate tests for missing, contradictory, or weakly supported self-claims.
6. **Evolve:** propose authorized updates to the self-model, descriptors, or structure.

Each operation must expose unsupported conditions and explicit leftovers instead of silently treating unknowns as zero or false.

## 8. Two-Ways CCC and Self-Model Residuals

The forward direction starts with a self-model hypothesis and checks predicted outcomes against observations. The reverse direction starts with an unexplained discrepancy and asks which missing perspective, constraint, relationship, or model assumption might account for it.

```text
Self-model claim / hypothesis
            |
            v
Forward CCC: conditions -> predictions -> observations
            |
            v
       Typed residual
            |
            v
Evidence audit / confounder checks
            |
            v
Reverse CCC: candidate missing conditions or perspectives
            |
            v
Independent test -> authorized model update or explicit leftover
```

A residual is evidence of a mismatch, **not** evidence by itself of a new mechanism or of an entity's subjective experience. Hypotheses generated by reverse search must be distinguished from validated findings.

### 8.1 Residual registry entry

A useful record may include `entityRef`, `selfPerspectiveId`, `expectation`, `observation`, `delta`, `time`, `evidence`, `uncertainty`, `candidateExplanations`, `tests`, `decision`, and `version`. Cross-entity comparison should respect permissions and privacy boundaries.

## 9. World, Observation, Knowledge, and Structural Delta

Self-model evolution requires careful separation of change types:

| Delta type | What changes | Example |
|---|---|---|
| World Delta | the modeled system or environment | battery capacity physically degrades |
| Observation Delta | available evidence or measurement | a sensor is recalibrated |
| Knowledge Delta | the self-model's beliefs or claims | endurance estimate is revised |
| Structural Delta | representation, index, or capability architecture | new battery-health perspective added |

A knowledge update does not itself imply a physical change. Reverting a model version does not undo the world. The same event can generate several linked deltas, but their types and provenance should remain distinct.

### 9.1 CDE integration

Constrained Delta Evolution (CDE) provides a candidate control plane for allowed self-model transitions:

\[
\Delta:(S,C)\rightharpoonup S'
\]

where \(S\) is the current model or system state and \(C\) denotes applicability and governance constraints. Candidate operations include `ADD_PERSPECTIVE`, `REVISE_CLAIM`, `SPLIT_MODEL`, `MERGE_MODEL`, `RECALIBRATE`, `DEPRECATE`, and `ROLLBACK_REPRESENTATION`.

The CDE kernel should not universally prohibit repeated deltas or revisited states. Chess and other cyclic domains demonstrate why path-memory and cycle restrictions must be configurable contracts rather than assumed universal axioms.

### 9.2 Safety and authorization

A system capable of revising its self-model must not be assumed authorized to revise its own permissions, goals, safety constraints, or governance policy. Model updates and action-authority updates are different operations. Proposals can be logged, tested, and rejected without execution.

## 10. Relation to Subjective Structural Intelligence (SSI)

SSI investigates subject boundaries, identity history, subjective world models, valuation, structural freedom, self-models, and metacognition. WE-SIO provides a possible **representation and operations substrate** for some of these topics; it does not replace SSI's broader conceptual questions.

The relationship can be described as:

- **WE-SIO:** How are entities, perspectives, evidence, and structural operations represented and evolved?
- **SME research:** Under what operational conditions does a system maintain and use a model of itself?
- **SSI:** How might subject-relative perspectives, value structures, identity, autonomy, and consciousness boundaries be analyzed?

Self-monitoring, self-reference, and goal-directed feedback are not sufficient evidence of phenomenal consciousness. Claims about experience require independent conceptual and empirical justification, which this paper does not provide.

## 11. Architectural Boundaries and Counterexamples

### Counterexample A — Passive database record

A database contains a detailed profile of a robot, but the robot cannot access or use it. This is a WE representation, not an SME of the robot under the operational contract.

### Counterexample B — Simple thermostat

A thermostat compares measured temperature to a setpoint. Is this an SME? A weak definition might say yes; a stronger definition requires explicit self-referential representation and revision that improves prediction or diagnosis. The example exposes a **definition boundary**, not a settled exclusion.

### Counterexample C — Misleading self-report

An agent reports high confidence and broad capabilities but repeatedly fails tests. Its self-report cannot be treated as verified capacity. External evaluation and provenance are required.

### Counterexample D — Model updated, world unchanged

A sensor correction changes the estimated location of a vehicle while the vehicle is stationary. This is primarily an observation/knowledge delta, not evidence of world movement.

### Counterexample E — Distributed collective

Several services jointly maintain a model of their collective state. Is the collective one SME or many? Identity and boundary policies may support multiple valid descriptions; conformance tests must state the selected scope.

### Counterexample F — Self-reference without update

A static system stores a description of itself but never uses or revises it. The representation is self-referential, yet it fails the proposed feedback-and-revision SME contract.

## 12. Candidate Conformance Contracts

The following tests are proposals for future implementations, not claims of completed validation.

| ID | Test | Expected evidence |
|---|---|---|
| SME-C01 | Self-reference resolves unambiguously within declared scope | resolver trace and boundary policy |
| SME-C02 | Identity remains distinct from perspective/index signature | identity continuity tests |
| SME-C03 | Model materially affects a consequential operation | matched baseline comparison |
| SME-C04 | Predictions and observations are versioned | reproducible event log |
| SME-C05 | Residuals preserve evidence and uncertainty | typed residual registry |
| SME-C06 | Candidate hypotheses remain separate from validated claims | state transition audit |
| SME-C07 | Self-view and external-view conflicts are representable | cross-perspective test |
| SME-C08 | World and knowledge deltas are not conflated | change-classification cases |
| SME-C09 | Unauthorized model/policy changes are rejected | permission tests |
| SME-C10 | Revision can be audited and, where possible, representation-rolled-back | version and rollback tests |
| SME-C11 | Reflection and reverse search respect budgets | bounded execution tests |
| SME-C12 | Missing evidence yields explicit unknown / leftover | negative-data tests |
| SME-C13 | Distributed identity policies handle membership changes | collective boundary tests |
| SME-C14 | Self-modeling adds measurable value over a simpler baseline | ablation results |
| SME-C15 | No consciousness inference follows solely from conformance | claim-scope review |

## 13. Testable Research Hypotheses

**H-SME-01 — Operational value.** An explicit self-model improves calibrated prediction or task recovery over a matched controller without such a model, under defined workloads.

**H-SME-02 — Multi-perspective diagnosis.** Distinguishing resource, capability, permission, and environmental perspectives reduces erroneous root-cause assignments.

**H-SME-03 — Residual retention.** Maintaining an evidence-rich self-residual registry improves future diagnosis compared with discarding unexplained errors after each episode.

**H-SME-04 — Two-way discovery.** Reverse CCC generates useful, independently testable missing-condition hypotheses at a higher rate than forward-only diagnosis, within comparable budgets.

**H-SME-05 — Typed deltas.** Separating world, observation, knowledge, and structural deltas reduces invalid updates and improves auditability.

**H-SME-06 — Adaptive intelligence.** On-demand MLIU activation yields a better resource–quality tradeoff than always-on heavyweight per-perspective agents.

**H-SME-07 — Definition boundary.** A minimal SME kernel plus conformance contracts discriminates meaningful self-modeling behavior from trivial feedback control more consistently than a broad self-reference-only definition.

These hypotheses can fail; failure should update the definition registry and research agenda rather than be concealed.

## 14. Validation Roadmap

### Phase 0 — Definitions and adversarial examples

Specify the SME kernel, identity policy, action/observation contracts, and candidate counterexamples. Review borderline systems such as thermostats, static self-descriptions, and distributed services.

### Phase 1 — Controlled simulation

Build two otherwise matched agents: one with an explicit, versioned self-model and one with a simpler state controller. Introduce sensor noise, tool denial, resource drift, and changed task constraints. Compare predictive calibration, task recovery, error diagnosis, and compute cost.

### Phase 2 — WE-HDT / MLIU / Two-Ways CCC integration

Implement a small multi-perspective self-model with typed residuals. Measure query correctness, explanation traceability, reverse-hypothesis precision, and latency. Include ablations for residual registry and reverse search.

### Phase 3 — CDE-governed evolution

Test authorized claim updates, new perspective creation, representation rollback, and cycle-policy choices. Verify that policy changes cannot be smuggled through ordinary knowledge updates.

### Phase 4 — Collective Learning relay

Publish specifications, synthetic traces, failed hypotheses, boundary counterexamples, and reproducible evaluation protocols. External participants should be able to reproduce or refute the claims without accepting the broader WE-SIO framework in advance.

## 15. Integration with the WE-SIO Research Program

| Related work | Interface to this paper |
|---|---|
| WE-SIO-001 | origin of WE representation and structural operations |
| WE-SIO-002 | entity identity and perspective descriptors |
| WE-SIO-003 | WE-HDT localization and cross-perspective access |
| WE-SIO-004 | adaptive variable-intelligence blocks |
| WE-SIO-005 | MLIU operations and lightweight capability activation |
| WE-SIO-006 | Two-Ways CCC and reverse condition discovery |
| WE-SIO-007 | residual-first discovery and evidence preservation |
| WE-SIO-008 | metric/perspective creation and validation |
| WE-SIO-009 | typed deltas and CDE-governed evolution |
| WE-SIO-011 | minimal kernel, contracts, and definition evolution |
| WE-SIO-012 | Collective Learning relay architecture |

**Suggested figure:** `figures/Fig-010-From-WE-to-Self-Modeling-Entity-and-Collective-Relay.png`, near Sections 2–3 or as a synthesis in Section 15.

## 16. Open Questions and Explicit Leftovers

1. What is the weakest nontrivial operational test that distinguishes self-modeling from ordinary feedback control?
2. Can a system be an SME if its self-model is maintained by an external service but used internally?
3. Which identity continuity contracts work for distributed or replaceable-component systems?
4. How should self-referential model recursion be bounded without discarding useful metacognition?
5. What evidence is sufficient to promote a self-model hypothesis to an operationally trusted claim?
6. How should contradictory self-view and external-view perspectives be scored without hiding dissent?
7. When does a new self-perspective improve explanation rather than merely overfit residuals?
8. Can typed delta separation improve diagnosis in practice, and under what workloads?
9. How should self-model revision permissions be separated from governance and goal permissions?
10. Which aspects of SSI can be represented operationally without conflating representation with experience?
11. Can multi-agent collectives possess useful shared self-models without a single centralized identity?
12. What failures or counterexamples would require narrowing, splitting, or abandoning the SME definition?

## 17. Collective Learning Relay Contract

To make this paper a useful relay piece rather than a closed thesis, each follow-up contribution should identify:

- **Claim ID and version:** the exact proposition being tested;
- **Definition version:** which SME kernel and boundary contract were used;
- **Scenario and baseline:** the environment and competing simpler explanation;
- **Evidence:** data provenance, observation uncertainty, and replication details;
- **Counterexamples:** conditions where the claim fails;
- **Decision:** retain, revise, split, reject, or leave unresolved;
- **Residuals:** unexplained mismatches preserved for future work;
- **Relay interface:** what another researcher or agent can reproduce next.

The repository's `research-trace/` registries should hold these records, with cross-links to `SPEC-001`, `SPEC-004`, `SPEC-005`, and `SPEC-006` when those contracts are completed.

## 18. Conclusion

WE-SIO begins with the representation and structural indexing of World Entities. Extending it to a Self-Modeling Entity requires more than adding a self-referential label: it requires a declared identity boundary, consequential use of a self-model, observable prediction–outcome comparisons, evidence-preserving revision, and constrained evolution. WE-HDT and MLIU provide candidate access and operational mechanisms; Two-Ways CCC and residual-first discovery provide a route from mismatch to testable questions; CDE provides a candidate governance structure for changes in the representation.

The resulting SME is an **operational research construct**, not proof of subjectivity or consciousness. Its value depends on whether the proposed distinctions produce measurable gains, clearer failure analysis, and reproducible Collective Learning. The appropriate next step is to test the minimal kernel against difficult counterexamples and let the definition evolve with evidence.

---

**Research principle:** *A model of the self is not the self; a self-modeling loop is not proof of experience; and a useful definition must survive counterexamples.*

**License note:** Intended for inclusion in the WE-SIO repository under its selected Apache-2.0 license; verify repository-level attribution and release metadata before publication.
