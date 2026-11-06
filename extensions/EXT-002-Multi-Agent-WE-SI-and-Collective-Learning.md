# EXT-002 — Multi-Agent WE-SI and Collective Learning

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research extension / hypothesis, not validated implementation  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Specifications-first research proposal; open for collective testing  
**Companion:** EXT-001 — WE-HDT as an SIF Localization Pillar

## Abstract

A World Entity (WE) can be represented through multiple typed perspectives, indexed through a WE Hybrid Differential Tree (WE-HDT), and supported by Metric Leaf Intelligence Units (MLIUs). This extension asks what happens when **multiple bounded WE-SI agents** operate over overlapping but nonidentical evidence, capabilities, objectives, and authority. We propose a contract-driven architecture for delegation, collaboration, competition, verification, and knowledge relay. Its central hypothesis is not that more agents automatically produce more intelligence; rather, diversity of perspectives combined with explicit evidence provenance, disagreement preservation, and controlled promotion may improve discovery and decision quality under selected workloads.

The architecture connects WE-SIO to the Structural Intelligence Framework (SIF), Universal Intelligence Evolution and Relay Unit (UIERU), Strategic Structural Intelligence and Competitive Relay (SSICR), Autonomous Questioning Structural Intelligence (AQSI), Constrained Delta Evolution (CDE), and residual-first metric discovery. We specify falsifiable hypotheses, interface contracts, failure modes, baselines, and a staged validation program. No empirical gains are asserted.

## 1. Research question and scope

**Question:** Under what conditions can a population of WE-SI agents learn collectively without conflating entity identity, perspective semantics, evidence quality, or decision authority?

An agent here is an **operational role with bounded capabilities and resources**, not necessarily an independent LLM, process, or conscious subject. An MLIU can be a deterministic rule, small model, tool wrapper, human reviewer, or composite service. Agent multiplicity may be logical rather than physical.

### 1.1 In scope

- Typed multi-perspective entity localization, interpretation, and question generation.
- Delegation and verification across heterogeneous agents.
- Collaborative, adversarial, and mixed relay topologies.
- Evidence-preserving disagreement and residual management.
- Bounded learning, versioning, rollback, and reproducibility.
- Collective learning as both knowledge transfer and repeated-execution data accumulation.

### 1.2 Out of scope

- Claims of AGI, consciousness, or subjective experience.
- A universal optimal agent organization.
- Unrestricted autonomous execution in external systems.
- Assuming all numeric perspectives are mathematical metrics.
- Treating a consensus vote as independent evidence or ground truth.

## 2. Conceptual foundations

### 2.1 World Entity, perspective, and agent are distinct

A **WE** is the referent under study. A **perspective** is a typed observation or interpretation contract. An **agent** is a capability-bearing operator that uses one or more perspectives to act on an authorized task. These identities must not be collapsed.

For example, three agents may inspect the same shipment: one estimates location, another evaluates schedule constraints, and a third audits source reliability. They share an entity reference but not necessarily the same observations, confidence calibration, or objective function.

### 2.2 Four independently versioned layers

| Layer | Typical object | Must preserve |
|---|---|---|
| Entity | `entityRef`, alias/equivalence claims | Identity provenance and scope |
| Perspective | Descriptor, units, relation semantics | Type and conformance |
| Agent | Capabilities, permissions, budgets | Accountability and authority |
| Relay | Task, artifacts, decisions, residuals | Lineage and reproducibility |

A new agent does not imply a new entity. A new metric hypothesis does not automatically change the canonical entity schema. A successful relay does not automatically validate its scientific claims.

### 2.3 Intelligence distribution as a design variable

Possible deployments include centralized orchestration with specialized leaf services, peer-to-peer collaboration, federated domain teams, or competitive search portfolios. The correct architecture depends on evidence dependencies, task decomposition, latency, resource constraints, and failure correlations.

## 3. Proposed architecture

```text
World Entities + typed perspectives + observation streams
                         |
                  WE-HDT / SIF Locator
                         |
              Candidate entities / residuals
                         |
             SIF / UIERU Control Plane
                         |
       +-----------------+-----------------+
       |                 |                 |
   Agent A           Agent B           Agent C
   Locate            Relate            Question
       |                 |                 |
       +-------- Evidence / Hypothesis Bus-+
                         |
            Independent Validator / Audit
                         |
             Relay Portfolio + Registry
                         |
         Promote / Reject / Hold / Rollback
                         |
            Revised perspectives, policies,
           questions, and reproducible traces
```

The diagram represents **logical contracts**, not a prescribed microservice deployment. One component may implement several roles, provided independence claims are not fabricated.

### 3.1 Role catalog

1. **Locator:** retrieves candidates using WE-HDT or an alternative SIF localization method.
2. **Resolver:** disambiguates identities and applies typed evidence constraints.
3. **Relator:** evaluates directed, symmetric, or conditional relations without changing their semantics.
4. **Inferencer:** proposes bounded predictions and their uncertainty.
5. **Questioner:** transforms residuals and disagreements into testable questions (AQSI).
6. **Explorer:** proposes candidate perspectives, policies, or Delta sequences (CDE).
7. **Critic:** searches for counterexamples and invalid assumptions.
8. **Validator:** checks conformance, held-out evidence, leakage, and provenance.
9. **Steward:** manages permissions, resource budgets, promotion, and rollback.

These are **separable responsibilities**, not mandatory dedicated agents.

## 4. Minimal multi-agent contract

An agent is described by:

```yaml
agentId: agent-locator-01
version: 0.1.0
roles: [locate]
capabilities: [candidate_generation]
supportedPerspectives: [spatial.v1, route_relation.v2]
inputs:
  schema: we_sio.task.v1
outputs:
  schema: we_sio.relay_artifact.v1
constraints:
  latencyBudgetMs: 1500
  computeBudget: bounded
  externalActions: denied
  privacyClass: restricted
assurance:
  guarantees: [candidate_recall_requires_verified_bounds]
  uncertainty: required
  provenance: required
```

The illustrative schema is not a published machine-readable standard. All fields require formalization and validation before implementation.

### 4.1 Task envelope

A task envelope should carry `taskId`, `entityRefs` or discovery scope, `perspectiveIds`, requested operation, input evidence references, uncertainty tolerance, budget, deadline, authorization, expected output contract, and trace identifiers.

### 4.2 Relay artifact

A relay artifact should include `artifactId`, `taskId`, producer and version, input lineage, typed claims, evidence links, uncertainty, counterevidence, residuals, method/configuration, validation status, cost, and explicit leftovers. An empty residual set is not proof of completeness.

### 4.3 State and lifecycle

`proposed → dispatched → executed → checked → {accepted, rejected, quarantined, deferred} → archived`.

A checked artifact may be accepted for a narrow operational use without being promoted to a general scientific principle. Every promotion has a target scope, owner, evidence threshold, rollback route, and expiry/review policy.

## 5. Relay topologies

### 5.1 Sequential relay

One agent localizes candidates, another resolves identity, another validates claims. This reduces capability requirements per agent but can propagate early omissions. If candidate generation is not recall-complete, downstream correctness cannot repair missing candidates without a fallback path.

### 5.2 Parallel specialization

Agents inspect distinct perspectives concurrently. This may improve coverage when perspectives are complementary, but evidence correlation must be measured; three agents reading the same faulty source are not three independent confirmations.

### 5.3 Competitive relay

Multiple agents propose competing hypotheses or strategies under a shared evaluation contract. Selection must account for search cost, leakage, benchmark overfitting, and the possibility that the evaluator is wrong. Competition is a means of generating alternatives, not an epistemic guarantee.

### 5.4 Adversarial verification

A critic deliberately attempts to falsify the leading proposal. Its counterexamples are first-class relay artifacts. Reward structures should not incentivize fabricated objections or endless vetoes.

### 5.5 Repeated-execution relay

Repeating a bounded operation can accumulate calibration data, edge-case distributions, latency profiles, and drift signals. Such repetition becomes **learning** only if observations are retained, compared, and used under a governed update process. Repetition alone is not improvement.

## 6. Two-Ways CCC across agents

**Forward path:** task → perspective selection → candidate localization → typed resolution → accountable answer.

**Reverse path:** answer failure, disagreement, or residual → diagnosis → candidate missing factor → question or new perspective → controlled experiment → possible revision.

The two directions may involve different agents, but share an evidence lineage. Reverse discovery must not silently rewrite the assumptions used in the forward evaluation.

### 6.1 Disagreement as an addressable object

Define a disagreement record:

`D = (claim, scope, agentClaims, sharedEvidence, independentEvidence, conflicts, uncertainty, nextTest, status)`.

A disagreement is not resolved by majority vote alone. The system should distinguish contradictory observations, incompatible perspective contracts, differing priors, time-version mismatch, and genuinely unresolved hypotheses.

### 6.2 Residual routing

Residuals can be routed by type: data-quality anomalies to auditors, model mismatch to inferencers, entity ambiguity to resolvers, constraint violation to CDE explorers, and unknown factor candidates to AQSI questioners. Routing itself is a policy subject to testing.

## 7. Collective learning mechanisms

### 7.1 Evidence accumulation

New observations update an evidence registry with provenance, timestamp, scope, source dependencies, and uncertainty. Historical evidence is not overwritten merely because a new hypothesis is preferred.

### 7.2 Capability learning

A capability registry tracks agent-specific competence by task family, perspective, data regime, and cost. Routing can use calibrated performance estimates, but must reserve exploration to avoid locking into early winners.

### 7.3 Perspective learning

Agents propose new descriptors or relations from persistent residual patterns. Promotion requires semantic typing, data quality assessment, incremental utility, robustness, and governance review. A derived score is not automatically a metric.

### 7.4 Policy learning

The control plane may adjust delegation, portfolio allocation, stopping criteria, or validator selection. Such policy changes are **operational Deltas** and require versioned evaluation against a fixed baseline.

### 7.5 Structural learning

The architecture may split/merge blocks, activate MLIUs, add interfaces, or replace a locator. Structural changes are not equivalent to world changes or evidence changes; they require separate logs and rollback.

## 8. CDE integration and bounded evolution

A candidate state container is:

`S = (entityView, perspectiveRegistry, agentPortfolio, evidenceRegistry, policyVersion, resourceState, trace)`.

A candidate Delta changes one or more explicitly named components under a contract. Examples include `delegate(task, agent)`, `addPerspective(candidate)`, `reviseRoutingPolicy(policy)`, or `quarantineEvidence(source)`.

CDE contributes applicability checks, constrained branching, rollback, cycle policies, and exploration strategies. **No-Delta-Reuse is not a universal axiom**: repeating a calibration task or revisiting a strategy can be valid. Cycle detection must be tied to the relevant state equivalence and resource budget, not a blanket ban on repeated actions.

### 8.1 Safety and termination

Each run has a finite budget, maximum depth or iteration count, stop criteria, authorization boundary, and an explicit incomplete-result status. Open-ended research direction does not authorize an unbounded runtime.

## 9. Identity, trust, and sovereignty

A multi-agent system must separate **source trust**, **agent reliability**, **authorization**, and **claim validity**. A trustworthy agent can make a false claim; a low-reputation source can provide verifiable evidence; authorization to read does not imply authorization to change.

Entity linkage is a hypothesis subject to confidence and provenance, not an automatic merge operation. Cross-organizational relay should support redacted artifacts, source-scoped identifiers, minimum-necessary disclosure, and auditability. Privacy-preserving collaboration remains an open engineering problem rather than a guaranteed feature of this design.

## 10. Worked scenario A — logistics entity resolution

**Task:** Determine whether two route records refer to the same physical shipment and whether a delayed arrival requires replanning.

1. Locator A retrieves candidates by geospatial and temporal bounds.
2. Resolver B compares source-scoped IDs and directional route relations.
3. Auditor C finds a timestamp offset inconsistency.
4. Questioner D proposes a test: did a sensor clock drift explain the residual?
5. Validator E checks independent logs and holds the identity merge pending evidence.
6. CDE Explorer F proposes constrained schedule revisions without modifying the original evidence.
7. Steward archives the accepted plan, rejected merge, and unresolved clock hypothesis.

**Key point:** operational replanning may be authorized even while scientific or identity uncertainty remains unresolved.

## 11. Worked scenario B — scientific discovery relay

**Task:** Explain a persistent prediction residual in a heterogeneous observational dataset.

A baseline model yields subgroup residuals. One agent checks data quality, another tests plausible confounders, a third proposes a conditional perspective, and a critic tests negative controls. The validator uses an untouched holdout dataset and a predeclared analysis plan. If the candidate fails, the residual and failed hypothesis remain discoverable. If it succeeds, promotion is limited to the validated population and measurement regime.

**Boundary:** observational association does not establish causality. In clinical settings, this research process does not authorize treatment recommendations or deployment without appropriate domain oversight.

## 12. Worked scenario C — self-modeling agent portfolio

An agent predicts its own success probability for a task. A second agent evaluates its calibration, a third audits the evidence, and a steward changes task routing only after prospective tests. The self-model is a revisable operational hypothesis; the system's ability to describe itself is not evidence of consciousness.

## 13. Formal research propositions

Let `Q` denote externally evaluated task quality, `C` total resource cost, `P` provenance completeness, `R` validated candidate recall, and `U` calibration error. Compare all systems on identical task sets and evaluation protocols.

- **H-MA-001 (Complementarity):** Heterogeneous perspective portfolios improve `Q` at matched `C` on tasks with complementary evidence, relative to a best single-agent baseline.
- **H-MA-002 (Adversarial checking):** Independent critics reduce unsupported claim promotion without an unacceptable loss of validated discovery recall.
- **H-MA-003 (Residual relay):** Typed residual routing increases validated hypothesis yield per unit cost versus unstructured brainstorming.
- **H-MA-004 (Provenance):** Mandatory lineage increases reproducibility and correction speed, with measurable overhead.
- **H-MA-005 (Adaptive routing):** Calibrated capability-aware routing improves quality–latency tradeoffs under workload shift relative to static routing.
- **H-MA-006 (Repeated execution):** Versioned repeated-execution traces improve future calibration compared with discarding execution history.
- **H-MA-007 (Federated privacy):** Redacted relay artifacts retain sufficient utility for selected cross-boundary tasks while reducing exposed sensitive information.

Each hypothesis may fail. Define acceptance thresholds, confidence intervals, and multiplicity correction before testing.

## 14. Baselines and experimental controls

| ID | Baseline | Purpose |
|---|---|---|
| B0 | Single capable agent, no relay | Establish standalone performance |
| B1 | Single agent with retrieval/tools | Control for tool access |
| B2 | Parallel identical agents, majority vote | Test diversity vs replication |
| B3 | Specialized agents, no shared residual registry | Isolate residual memory |
| B4 | Specialized agents with registry, no independent validator | Isolate verification |
| B5 | Full WE-SI relay with fixed routing | Isolate adaptive control |
| B6 | Full WE-SI relay with adaptive routing | Evaluate proposed system |

Match token/compute/time budgets and data access. Randomize task assignment, preserve independent test splits, report all failed runs, and evaluate across seeds and distribution shifts. Compare against simpler non-agentic pipelines where appropriate.

### 14.1 Measurement plan

Measure exactness/recall where ground truth exists; calibration (Brier score or expected calibration error with caveats); false promotion rate; validated discovery rate; source dependence; contradiction resolution time; latency; cost; privacy exposure; rollback success; and human review burden. Avoid collapsing all dimensions into one opaque score.

### 14.2 Ablation plan

Remove one at a time: critics, provenance, typed perspective contracts, residual registry, capability routing, cross-agent independence, and rollback. An ablation is valid only if resource allocation remains comparable.

## 15. Conformance tests

| Test | Requirement | Expected outcome |
|---|---|---|
| MA-001 | Distinct entity and agent identifiers | No implicit identity merge |
| MA-002 | Source-scoped record ID | Not treated as universal WE identity |
| MA-003 | Perspective unit mismatch | Rejected or explicit conversion |
| MA-004 | Asymmetric relation | Direction preserved |
| MA-005 | Nonmetric score | No triangle-inequality claim |
| MA-006 | Unauthorized operation | Denied and logged |
| MA-007 | Missing provenance | Quarantine, not silent acceptance |
| MA-008 | Duplicated evidence across agents | Dependence detected or flagged |
| MA-009 | Contradictory claims | Disagreement artifact retained |
| MA-010 | Stale perspective version | Version mismatch detected |
| MA-011 | Incomplete candidate retrieval | Guarantee downgraded/fallback |
| MA-012 | Residual without observation context | Marked non-actionable |
| MA-013 | Failed hypothesis | Preserved with rejection reason |
| MA-014 | Agent crash mid-relay | Recoverable status, no false completion |
| MA-015 | Retry of same task | Idempotent or explicitly versioned |
| MA-016 | Budget exhausted | Bounded stop and explicit leftover |
| MA-017 | Policy rollback | Prior valid version restored |
| MA-018 | New metric proposal | Validation before promotion |
| MA-019 | Evaluation leakage | Detected by split/protocol audit |
| MA-020 | Self-model claim | No inference of consciousness |
| MA-021 | Redacted cross-boundary relay | Restricted fields not exposed |
| MA-022 | Repeat execution | Distinguishes evidence gain from duplicate count |
| MA-023 | Cross-agent circular citation | Not counted as independent support |
| MA-024 | World vs knowledge Delta | Recorded in separate event classes |

## 16. Counterexample registry

**CE-MA-001 — Echo chamber:** Ten agents repeat one incorrect source; agreement rises while accuracy does not.  
**CE-MA-002 — Validator capture:** A competitive proposer learns the evaluator's shortcuts.  
**CE-MA-003 — Localization omission:** A high-precision resolver cannot recover a missing candidate.  
**CE-MA-004 — Perspective collision:** Two numeric values with incompatible units appear equal.  
**CE-MA-005 — Agent proliferation:** Coordination cost exceeds any quality improvement.  
**CE-MA-006 — Correlated failure:** Diverse model labels conceal shared training or source dependence.  
**CE-MA-007 — Endless debate:** Critics generate objections without discriminating tests.  
**CE-MA-008 — Feedback contamination:** Hypotheses are evaluated on data used to generate them.  
**CE-MA-009 — Authority escalation:** A relay artifact is mistaken for permission to act.  
**CE-MA-010 — False identity merge:** Similar perspective signatures collapse two entities.  
**CE-MA-011 — Residual fetishism:** Random noise is repeatedly promoted as a discovery.  
**CE-MA-012 — Nonstationarity:** A previously competent agent degrades after distribution shift.  
**CE-MA-013 — Hidden privacy leakage:** Explanations expose restricted observations.  
**CE-MA-014 — Cyclic dependency:** Agents wait on each other's unresolved artifacts.  
**CE-MA-015 — Historical erasure:** New consensus overwrites earlier counterevidence.

Each counterexample should become a reproducible fixture where feasible, not merely a cautionary label.

## 17. Validation roadmap

### Phase 0 — Contract and ontology freeze

Define entity/perspective/agent/relay schemas, threat model, typed operations, version semantics, and baseline tasks. Exit when all critical contracts have executable validation fixtures.

### Phase 1 — Synthetic multi-perspective benchmark

Construct controlled worlds with known entities, correlated and independent sensors, deliberate ambiguity, missing factors, and seeded faults. Test MA-001 through MA-024.

### Phase 2 — Relay and disagreement benchmark

Compare sequential, parallel, competitive, and adversarial configurations. Quantify false consensus, recall loss, overhead, and correction latency.

### Phase 3 — Residual-first discovery

Seed discoverable conditional factors and pure-noise distractors. Measure verified discovery yield on held-out worlds; publish failures and false positives.

### Phase 4 — CDE and adaptive portfolio

Introduce constrained policy and structural Deltas. Test stopping, rollback, distribution shift, and whether adaptive routing beats fixed baselines.

### Phase 5 — Federated collective learning

Use permission-separated simulated organizations and redacted relay. Measure privacy exposure, trace completeness, and cross-boundary utility.

### Phase 6 — External replication

Publish schemas, generators, seeds, configurations, evaluation scripts, negative results, and a provenance manifest for independent teams. No claim of validation before replication.

## 18. Definition evolution and governance

The minimal kernel should remain small: **typed entities, typed perspectives, bounded operators, evidence-linked claims, controlled relay, and versioned revision**. Do not define collective intelligence so broadly that any communication qualifies.

A proposed definition change must specify: triggering counterexample, old/new definition, changed invariants, impacted contracts, migration plan, regression tests, and explicit leftovers. Definitions may be narrowed, split, or rolled back when counterexamples require it.

Governance separates proposing, checking, and promoting. A human or authorized control plane may override an operational decision, but the override itself must be recorded with rationale and scope. Governance is part of the architecture, not an afterthought.

## 19. Collective Learning Relay package

Each released relay package should contain:

```text
relay-package/
  MANIFEST.yaml
  task-and-scope.md
  entity-and-perspective-contracts.yaml
  agent-capability-contracts.yaml
  evidence-lineage.jsonl
  hypotheses-and-counterexamples.md
  evaluation-protocol.md
  results-and-negative-results.csv
  residuals-and-open-questions.md
  decisions-and-rollback.md
  reproducibility-notes.md
```

The package is a proposed interchange convention. Schemas, security rules, and conformance tooling remain to be implemented.

## 20. Open questions and explicit leftovers

1. What minimum agent diversity predicts independent information gain?
2. How should the system estimate correlated evidence without revealing restricted sources?
3. Can relay portfolio selection be robust to strategic manipulation of evaluator scores?
4. What is the right granularity for MLIU activation versus shared agent infrastructure?
5. How can we distinguish new knowledge from duplicate evidence and mere repetition?
6. When does adaptive coordination outperform a single well-equipped agent at matched cost?
7. How should confidence be propagated across incompatible but composable perspectives?
8. What are practical guarantees for distributed candidate completeness?
9. How can false scientific discoveries be rolled back across dependent agents and artifacts?
10. How should SIF Control Plane policies interact with domain-specific sovereignty constraints?
11. Which CDE operators are genuinely general, rather than renamings of conventional workflow transitions?
12. What constitutes a useful, falsifiable definition of *collective structural learning*?

**Explicit leftover:** WE-SIO does not yet supply a verified formal semantics for all relay operations, a secure federation protocol, calibrated agent reliability estimators, or experimental evidence of superiority over strong single-agent baselines. These are research obligations, not implementation details to hide.

## 21. Relationship to the WE-SIO repository

- `docs/WE-SIO-003-WE-Hybrid-Differential-Tree-Architecture.md` — candidate localization and typed index semantics.
- `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md` — MLIU operation boundaries.
- `docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md` — bidirectional evidence and question flow.
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md` — residual governance.
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md` — Delta separation and constrained evolution.
- `docs/WE-SIO-012-WE-SIO-as-a-Collective-Learning-Relay-Piece.md` — broader relay positioning.
- `specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md` — operation interface obligations.
- `specs/SPEC-005-Residual-Evidence-and-Metric-Discovery-Contract.md` — evidence and discovery contracts.
- `specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md` — governance and research provenance.
- `extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md` — SIF integration.
- `extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md` — proposed next scientific extension.

## 22. Closing position

The proposed path from **World Entity → Multi-Perspective Intelligence → Multi-Agent Relay → Collective Structural Learning** is promising only insofar as it preserves semantic contracts, independent evidence, accountable disagreements, and reproducible improvements. The critical unit of progress is not the number of agents, but a **validated and transferable structural change**: a better question, a corrected relation, a new tested perspective, a safer policy, or a reproducible counterexample.

> Collective learning should accumulate not only answers, but the evidence, questions, failures, and boundaries that make future answers more trustworthy.

---

**License intent:** Apache-2.0 (repository-level license governs).  
**Citation:** See repository `CITATION.cff` when published.  
**Research status:** Hypotheses and architecture proposals; not empirically validated.
