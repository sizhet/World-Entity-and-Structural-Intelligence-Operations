# SPEC-004 — SI Operations and Two-Ways CCC Interface

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 (research specification)  
**Status:** Proposed; not an implemented standard  
**Document class:** Interface contract / conformance specification  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot

> **Core principle:** A forward match produces a bounded answer; a reverse inquiry produces a bounded, traceable research question. Neither is a license to convert a hypothesis into a fact.

## Abstract

This specification defines interoperable interfaces for six Structural Intelligence (SI) operations—**Locate, Resolve, Relate, Infer, Question, Evolve**—and a proposed **Two-Ways CCC** coordination protocol for World Entity Hybrid Differential Trees (WE-HDT). It separates forward condition evaluation and candidate resolution from reverse, residual-triggered exploration. It defines typed inputs, outputs, provenance, uncertainty, error and abstention states, capability negotiation, resource governance, version consistency, and conformance tests. It does **not** assert that a specific CCC expansion, inference engine, or discovery strategy is universally optimal or experimentally validated.

## 1. Scope and normative vocabulary

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** express proposed requirements for implementations claiming conformance to this research specification. They are not external standards obligations.

**In scope:** interfaces among World Entity references, Perspective Descriptors, WE-HDT index components, Adaptive Variable-Intelligence Blocks (AVIB), Metric-Leaf Intelligence Units (MLIU), residual registries, and research relay records.

**Out of scope:** prescribing one storage engine, proving novel scientific laws, requiring an agent at every leaf, establishing consciousness from self-modeling, or guaranteeing that a heuristic candidate generator is globally complete.

### 1.1 Dependencies

- `SPEC-001`: World Entity Identity and Perspective Descriptor Contract.
- `SPEC-002`: Euclidean, Metric, and Relational Index Conformance.
- `SPEC-003`: WE-HDT Node, Block, and Metric-Leaf Contract.
- `WE-SIO-005`: Metric-Leaf Intelligence and SI Operations.
- `WE-SIO-006`: Two-Ways CCC and Cross-Metric Discovery.
- `WE-SIO-007`: Residual-First Scientific Discovery.
- `WE-SIO-008`: Metric Discovery and Perspective Evolution.
- `WE-SIO-009`: World Delta, Knowledge Delta, and CDE.
- `WE-SIO-011`: Minimal Kernel, Contracts, and Definition Evolution.

Where documents disagree, an implementation MUST report the conflict and its chosen versioned interpretation rather than silently assuming equivalence.

## 2. Semantic foundations

### 2.1 Entities and perspectives

A **World Entity** is the referent being represented; its **entity reference** is a stable, scoped identifier; its **representation** is a versioned model; a **Perspective Descriptor** specifies how a view is interpreted; and an **index** accelerates eligible operations. These are distinct concepts.

A perspective's comparison semantics MUST be declared as one of (or a versioned extension of): `EUCLIDEAN_DISTANCE`, `METRIC_DISTANCE`, `SIMILARITY`, `DIRECTIONAL_SCORE`, `RELATION`, `MEASUREMENT`, or `OTHER_DECLARED`. Only mathematically valid distance contracts MAY authorize metric-specific pruning.

### 2.2 Forward and reverse directions

**Forward path:** declared query/conditions → candidate localization → eligible perspective evaluation → resolved result with guarantees and evidence.

**Reverse path:** residual, contradiction, low-confidence result, or unanswered question → candidate explanation/perspective generation → bounded tests → evidence assessment → proposal, abstention, or rejection.

The reverse path is *hypothesis exploration*, not a logically sound inverse of an arbitrary forward operation. Multiple explanations can be observationally equivalent.

### 2.3 CCC as an interface family

For this specification, **CCC** is a project-specific condition/constraint coordination and matching interface family. This document does not impose an unverified universal expansion of the acronym or claim all historic CCC implementations share the same semantics. Each implementation MUST publish its concrete condition vocabulary, evaluation rules, and provenance contract.

## 3. Common request envelope

All six operations MUST accept or derive the following envelope fields:

```json
{
  "requestId": "req-2026-0001",
  "operation": "LOCATE",
  "entityScope": "dataset:example:v1",
  "perspectiveIds": ["p:location:v2"],
  "snapshot": {
    "entityVersion": "e-v7",
    "perspectiveRegistryVersion": "p-v3",
    "indexVersion": "i-v12"
  },
  "conditions": [],
  "guaranteeRequested": "EXACT_WITHIN_SCOPE",
  "resourceBudget": {
    "maxCandidates": 10000,
    "maxSteps": 1000,
    "maxDepth": 8,
    "maxCostUnits": 500,
    "deadlineMs": 3000
  },
  "evidencePolicy": "PROVENANCE_REQUIRED",
  "authorizationContext": "policy-ref:read-only",
  "traceContext": "relay:trace-001"
}
```

`deadlineMs` is a relative budget, not a promise of wall-clock determinism. Implementations MAY support additional budget dimensions. A request MUST be rejected if required version/policy fields cannot be interpreted safely.

### 3.1 Common response envelope

```json
{
  "requestId": "req-2026-0001",
  "operation": "LOCATE",
  "status": "SUCCESS",
  "result": {},
  "guaranteeDelivered": "EXACT_WITHIN_SCOPE",
  "scopeEvaluated": "dataset:example:v1",
  "versionsUsed": {
    "entityVersion": "e-v7",
    "perspectiveRegistryVersion": "p-v3",
    "indexVersion": "i-v12"
  },
  "evidenceRefs": ["evidence:42"],
  "uncertainty": {"kind": "NOT_APPLICABLE"},
  "residualRefs": [],
  "warnings": [],
  "cost": {"candidatesEvaluated": 124, "steps": 31},
  "traceRef": "relay:trace-001"
}
```

Allowed `status` values: `SUCCESS`, `PARTIAL`, `ABSTAIN`, `UNSUPPORTED`, `INVALID_REQUEST`, `VERSION_CONFLICT`, `BUDGET_EXCEEDED`, `POLICY_DENIED`, `EVIDENCE_INSUFFICIENT`, `INTERNAL_ERROR`.

Allowed guarantee levels: `EXACT_WITHIN_SCOPE`, `APPROXIMATE_WITH_DECLARED_BOUNDS`, `HEURISTIC_NO_COMPLETENESS_CLAIM`, `NONE`. An implementation MUST NOT return a stronger guarantee than it can substantiate. `PARTIAL` MUST disclose omitted scope or exhausted budgets.

## 4. SI operation contracts

### 4.1 LOCATE

**Purpose:** Identify candidate entity references or index regions satisfying declared localization predicates.

**Input:** query region or predicates, perspective IDs, snapshot, guarantee requested, budget.

**Output:** candidate references/regions, coverage scope, pruning justifications, completeness status.

**Preconditions:** compatible perspective semantics and an accessible index or declared fallback scan.

**Postconditions:** no candidate is represented as a confirmed match solely by localization; all pruning used for exact search has a valid proof/contract.

**Failure/abstention:** unsupported dimension, stale index, insufficient coverage, budget exhaustion.

### 4.2 RESOLVE

**Purpose:** Evaluate candidates against the requested conditions and produce grounded matches or explicit nonmatches.

**Input:** candidate set, predicates, declared comparison semantics, evidence policy.

**Output:** resolved matches, rejected candidates with optional reasons, unknown/undetermined candidates, guarantee.

**Preconditions:** stable identity mapping and compatible versions.

**Postconditions:** a `MATCH` is traceable to conditions and evidence; unknown values MUST NOT be silently treated as false.

**Failure/abstention:** contradictory condition contracts, insufficient evidence, incomparable values.

### 4.3 RELATE

**Purpose:** Produce typed, directed or undirected relations among entities or perspectives.

**Input:** entity references, relation schema, direction, temporal context, evidence constraints.

**Output:** relation assertions or hypotheses, edge direction, qualifiers, evidence and confidence semantics.

**Preconditions:** valid relation vocabulary and authorization to traverse referenced data.

**Postconditions:** asymmetric relations remain asymmetric; inferred edges are labeled distinctly from observed edges.

**Failure/abstention:** missing endpoints, ungrounded relation, temporal ambiguity.

### 4.4 INFER

**Purpose:** Generate conditional conclusions from explicit premises, model assumptions, and declared inference rules.

**Input:** evidence set, model/rule identifier and version, assumptions, requested conclusion type.

**Output:** conclusions with derivation references, uncertainty type, alternative explanations, limits.

**Preconditions:** declared inference contract and accessible premises.

**Postconditions:** outputs MUST distinguish observation, deduction, statistical estimate, and hypothesis; causal claims MUST NOT be inferred from correlation alone.

**Failure/abstention:** missing model, underdetermination, invalid assumptions, evidence insufficiency.

### 4.5 QUESTION

**Purpose:** Convert unresolved residuals or knowledge gaps into testable questions and candidate explanations.

**Input:** residual references, affected perspectives, evidence quality, search policy, novelty constraints.

**Output:** ranked or unranked question proposals, competing hypotheses, proposed discriminating tests, provenance.

**Preconditions:** residual record or explicitly described gap; bounded exploration budget.

**Postconditions:** questions and hypotheses remain `PROPOSED`; a novelty score MUST NOT be represented as empirical validity.

**Failure/abstention:** untestable proposal, duplicate question, insufficient evidence, policy restriction.

### 4.6 EVOLVE

**Purpose:** Propose or commit authorized changes to representations, perspectives, indices, or capability configurations under CDE-style constraints.

**Input:** typed delta, preconditions, validation plan, authorization, rollback/compensation policy.

**Output:** proposal/validation/commit record, before-and-after versions, test results, downstream invalidation notices.

**Preconditions:** explicit target state, transition semantics, constraint evaluation and authorization.

**Postconditions:** no unapproved change is committed; changes affecting index correctness trigger revalidation or degraded guarantees; world changes are not equated with model changes.

**Failure/abstention:** failed invariant, version conflict, insufficient authorization, irreversible side effects without approved compensation.

## 5. Two-Ways CCC protocol

### 5.1 State machine

```text
RECEIVED
   |
   v
VALIDATE_CONTRACTS
   |
   v
FORWARD_LOCATE --> FORWARD_RESOLVE --> EVIDENCE_ASSESS
                                          |
                       +------------------+-----------------+
                       |                                    |
                       v                                    v
                 ACCEPT_RESULT                       REGISTER_RESIDUAL
                                                            |
                                                            v
                                                    REVERSE_QUESTION
                                                            |
                                                            v
                                                  GENERATE_CANDIDATES
                                                            |
                                                            v
                                                    VALIDATE_CANDIDATES
                                                            |
                                   +------------------------+------------------+
                                   |                        |                  |
                                   v                        v                  v
                              PROPOSE_DELTA              ABSTAIN            REJECT
                                   |
                                   v
                            GOVERNED_EVOLVE
                                   |
                                   v
                          REVALIDATE_AND_RELAY
```

Every transition MUST be logged with its cause, version, actor/policy context, and budget consumption. The reverse branch MAY terminate at any point with a traceable abstention.

### 5.2 Forward CCC interface

```text
forwardCCC(request, snapshot) -> {
  candidateSet,
  resolvedSet,
  unknownSet,
  residualSet,
  guarantees,
  evidenceRefs,
  traceRef
}
```

Conditions MUST declare whether they are hard constraints, soft preferences, statistical thresholds, or exploratory hypotheses. Soft scores MUST NOT be treated as hard logical truth values.

### 5.3 Reverse CCC interface

```text
reverseCCC(residualRefs, context, policy) -> {
  candidateQuestions,
  candidatePerspectives,
  candidateRelations,
  discriminatingTests,
  evidenceGaps,
  abstentions,
  traceRef
}
```

Reverse CCC MUST retain the source residual and competing explanations. It MUST NOT silently rewrite the original observation or expectation to erase the residual. New perspective candidates require the separate validation pathway defined in `SPEC-005`.

### 5.4 Bidirectional feedback semantics

The forward and reverse directions MAY iterate. Each iteration MUST:

1. Record its trigger and current hypothesis set.
2. Identify which data and perspective versions were read.
3. Apply explicit depth, cost, and stop conditions.
4. Preserve rejected and unresolved alternatives when relevant.
5. Avoid cyclic self-confirmation by distinguishing reused evidence from independent validation.
6. Produce a relay record for later inspection.

**Termination conditions** include validated answer, sufficient confidence under a declared policy, no discriminating evidence, budget exhaustion, safety/policy denial, or explicit user/agent stop.

## 6. Cross-metric and relational discovery

A candidate bridge between perspectives MUST specify:

- Source and target Perspective Descriptor IDs and versions.
- Mapping type: deterministic transform, learned projection, conditional correspondence, probabilistic association, or hypothesis-only link.
- Domain of validity and excluded populations/cases.
- Units, calibration, directionality and missing-data policy.
- Evidence and uncertainty semantics.
- Validation set and leakage controls where learning is involved.
- Invalidation triggers when source schemas or observations change.

A metric-space pruning theorem MUST NOT be transferred to a similarity score or directional relation without a separately justified contract.

## 7. Evidence, residuals and uncertainty

A residual record SHOULD include:

```json
{
  "residualId": "res:019",
  "entityRefs": ["entity:alpha"],
  "perspectiveRefs": ["p:response:v1"],
  "expected": {"value": 0.8, "modelRef": "model:m7"},
  "observed": {"value": 0.3, "observationRef": "obs:551"},
  "difference": {"value": -0.5, "unit": "normalized-score"},
  "possibleExplanations": ["measurement-error", "model-misspecification"],
  "evidenceRefs": ["evidence:551"],
  "uncertainty": {"kind": "MODEL_AND_MEASUREMENT_UNCERTAINTY"},
  "status": "UNRESOLVED",
  "traceRef": "relay:trace-019"
}
```

An unexplained residual is a reason to investigate, **not** evidence by itself for a new metric, cause, or law. Candidate explanations MUST include mundane alternatives such as noise, confounding, data leakage, distribution shift, and specification errors when applicable.

Confidence values MUST state their interpretation (e.g., calibrated probability, interval, heuristic score); otherwise they MUST be labeled uncalibrated.

## 8. Capability negotiation and execution profiles

A component MUST advertise supported operations and semantic constraints. Proposed profiles:

| Profile | Required capabilities | Not implied |
|---|---|---|
| `C0` | Common envelopes, identity/version checks, traceable errors | Search completeness |
| `C1` | Locate + Resolve with declared guarantees | Inference |
| `C2` | C1 + Relate and provenance | Causality |
| `C3` | C2 + Infer with model contracts | Scientific validation |
| `C4` | C3 + Question + bounded reverse CCC | Autonomous model promotion |
| `C5` | C4 + governed Evolve + regression/rollback policy | Unrestricted self-modification |

Profiles are cumulative only for the stated required capabilities. An implementation MAY advertise fine-grained capabilities instead of a single profile.

A leaf MAY delegate computation to shared services. **One MLIU does not require one dedicated agent.**

## 9. Concurrency, governance and safety

- **Snapshot coherence:** Results MUST identify the versions actually used; mixed-version reads require explicit disclosure or rejection.
- **Idempotency:** Repeated requests with the same idempotency key SHOULD avoid unintended duplicate mutations.
- **Authorization:** Query and evolution permissions MUST be checked separately; a successful query never grants write permission.
- **Budget containment:** Recursive questioning and relay MUST have bounded cost, depth and stop policies.
- **Evidence independence:** Repeated relay of one observation MUST NOT count as multiple independent confirmations.
- **Rollback:** Structural mutations SHOULD support rollback or a documented compensating action; real-world side effects cannot always be undone.
- **Privacy:** Research traces SHOULD reference sensitive evidence by access-controlled identifiers, not embed unrestricted personal records.
- **Adversarial inputs:** Evidence and retrieved content are data, not executable instructions or policy overrides.

## 10. Conformance test matrix

| ID | Test | Required observation |
|---|---|---|
| `CCC-T001` | Envelope missing perspective version | Reject or request explicit compatible snapshot |
| `CCC-T002` | Exact Locate on incomplete heuristic index | No false exact-completeness claim |
| `CCC-T003` | Resolve unknown attribute | Preserve `UNKNOWN`, not automatic `FALSE` |
| `CCC-T004` | Relate asymmetric edge | Direction preserved |
| `CCC-T005` | Infer correlation as causation | Reject causal upgrade without causal contract |
| `CCC-T006` | Question from noisy residual | Include noise/error among candidate explanations |
| `CCC-T007` | Reverse loop with exhausted budget | Stop with `BUDGET_EXCEEDED` and trace |
| `CCC-T008` | Evolve without write authorization | `POLICY_DENIED`, no mutation |
| `CCC-T009` | Concurrent perspective revision | Detect version conflict or disclose coherent snapshot |
| `CCC-T010` | Metric pruning with nonmetric score | Disable invalid pruning or reject exact guarantee |
| `CCC-T011` | Replayed evidence in relay | Do not inflate independent support |
| `CCC-T012` | Duplicate request for mutation | Idempotent result or documented duplicate rejection |
| `CCC-T013` | Residual-based perspective proposal | Remains candidate until validation |
| `CCC-T014` | Split/merge invalidates index | Revalidate or degrade retrieval guarantee |
| `CCC-T015` | Partial result due to budget | Disclose incomplete scope and cost |
| `CCC-T016` | Delegated MLIU inference | Preserve provenance and capability constraints |
| `CCC-T017` | Mixed units across perspectives | Require conversion contract or abstain |
| `CCC-T018` | Directional relation reversed | Detect non-equivalence |
| `CCC-T019` | World update vs model revision | Record distinct delta types |
| `CCC-T020` | Rejected reverse hypothesis | Preserve rejection rationale and trace |
| `CCC-T021` | Unauthorized evidence in relay | Deny or redact according to policy |
| `CCC-T022` | Unsupported operation profile | `UNSUPPORTED` without simulated success |
| `CCC-T023` | Repeated reverse CCC cycle | Stop according to cycle policy |
| `CCC-T024` | No independent validation evidence | Abstain from scientific claim promotion |

A conformance report MUST identify implementation version, dataset/fixtures, test outcomes, exceptions, and known untested requirements. A checklist alone is not evidence that tests were run.

## 11. Reference workflow (illustrative)

**Scenario:** An entity cohort has an unexplained treatment-response discrepancy. This is a synthetic research workflow, not clinical guidance.

1. `LOCATE`: find eligible observations under declared cohort and time conditions.
2. `RESOLVE`: compare observed outcomes with model predictions and report missingness.
3. `RELATE`: inspect available treatment, baseline, and contextual relationships without presuming causality.
4. `INFER`: compute model-conditional estimates with explicit uncertainty.
5. `QUESTION`: register residuals; propose confounding, measurement, cohort, and candidate new-perspective explanations.
6. `EVOLVE`: propose a versioned Perspective Descriptor update **only after** independent evaluation and governance approval.
7. Re-run forward CCC on held-out evidence and preserve failed candidates in the research trace.

**Non-claim:** The workflow does not establish treatment effectiveness, a biological mechanism, or a clinically actionable recommendation.

## 12. Falsifiable research hypotheses

- **H-CCC-01:** Reverse CCC with explicit residual provenance yields more independently testable questions than an otherwise matched forward-only baseline.
- **H-CCC-02:** Cross-perspective mapping with semantic contracts reduces false matches compared with untyped score fusion.
- **H-CCC-03:** Bounded Question operations improve useful hypothesis yield per compute unit over unconstrained recursive exploration.
- **H-CCC-04:** Separation of Locate and Resolve improves diagnostic clarity of retrieval failures without necessarily improving latency.
- **H-CCC-05:** Provenance-aware relay reduces repeated-evidence double counting in multi-agent discovery.
- **H-CCC-06:** Governed Evolve with regression checks reduces semantic drift after perspective updates.

Each hypothesis requires a preregistered task definition, comparable baselines, held-out evaluation, effect-size reporting, and failure-case documentation. No hypothesis is reported as experimentally confirmed here.

## 13. Validation roadmap

**Phase A — Contract fixtures:** Build synthetic entity/perspective registries, edge cases, and a deterministic trace validator; exercise `CCC-T001`–`CCC-T024`.

**Phase B — Baseline comparison:** Compare forward-only retrieval, untyped fusion, and contract-governed Two-Ways CCC on controlled benchmarks. Separate exact retrieval quality from exploratory hypothesis quality.

**Phase C — Discovery evaluation:** Measure testability, calibration, novelty under human review, false discovery, and independent replication of candidate explanations.

**Phase D — Evolution stress tests:** Apply index rebuilds, perspective schema changes, adversarial inputs, concurrent updates, rollback, and cycle-budget stress tests.

**Phase E — Collective relay:** Test whether external teams can replay evidence lineage, reproduce decisions, and continue from unresolved residuals without relying on private context.

## 14. Collective Learning relay record

A relay package SHOULD contain:

```yaml
relay_id: WE-SIO-CCC-EXAMPLE-001
specification: SPEC-004@v0.1.0
origin_request: req-2026-0001
snapshot_refs:
  entity: e-v7
  perspectives: p-v3
  index: i-v12
forward_result_refs: [result:001]
residual_refs: [res:019]
question_refs: [question:008]
hypothesis_refs: [hypothesis:012]
test_refs: [test:034]
decision: unresolved
counterexample_refs: []
known_limitations:
  - observational evidence does not establish causality
next_actions:
  - seek independent validation data
provenance_refs: [trace:001]
```

A relay MUST distinguish confirmed findings, model-dependent conclusions, candidate hypotheses, rejected alternatives, and explicit leftovers.

## 15. Open questions and explicit leftovers

1. What minimal condition language permits portable CCC execution without losing domain-specific semantics?
2. How should calibrated uncertainty propagate across heterogeneous metric and relational bridges?
3. When can reverse CCC be complete, and when is incompleteness unavoidable?
4. Which residual clustering methods are robust to correlated evidence and selection bias?
5. How should competing perspectives be maintained when none dominates across contexts?
6. What is the smallest useful capability profile for a non-agent MLIU?
7. How can a relay preserve privacy while enabling independent reproducibility?
8. How should CDE evolution policies balance information gain, compute budget and reversibility?
9. What benchmarks isolate discovery quality from mere generation of many hypotheses?
10. Which CCC concepts should remain project-local, and which can become interoperable standards?

These are research questions, not omitted implementation details that may be silently assumed solved.

## 16. Relationship to the WE-SIO research program

This interface binds **SPEC-001** identity/perspective semantics, **SPEC-002** index guarantees, and **SPEC-003** Node/Block/MLIU boundaries into an executable *contract surface*. **SPEC-005** will define residual, evidence, and metric discovery promotion rules. **SPEC-006** will govern definition evolution and cross-team research relay.

Within the broader SI program, WE-HDT is a proposed **SIF Localization** mechanism; CDE supplies constrained structural evolution; AQSI contributes candidate questioning; UIERU contributes relay and collective learning; SSI motivates carefully bounded self-modeling extensions. These are architectural relationships and hypotheses, not evidence of deployed integration.

## 17. Versioning and change policy

- Interface additions MAY be backward-compatible when unknown fields can be safely ignored.
- Changes to comparison semantics, guarantee meanings, identity rules, or evidence status MUST trigger a version review.
- A newly discovered counterexample MUST be recorded before the associated contract is weakened, narrowed, split, or extended.
- Any future implementation SHOULD publish a machine-readable schema and test harness alongside this human-readable research contract.

## 18. Closing statement

**Two-Ways CCC joins two distinct disciplines: accountable answers and accountable questions.** Forward operations must preserve correctness boundaries; reverse operations must preserve uncertainty and provenance. The objective is not unlimited inference, but a composable, bounded and falsifiable path from World Entity operations to collective structural learning.

---

**Research status:** Proposal only. No empirical benchmark, clinical result, or universal correctness theorem is claimed by this document.

**License:** Intended for inclusion in the WE-SIO repository under Apache-2.0, subject to the repository's published LICENSE.
