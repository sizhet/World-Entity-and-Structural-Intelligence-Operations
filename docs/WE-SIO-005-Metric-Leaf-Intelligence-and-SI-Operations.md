# WE-SIO-005 — Metric-Leaf Intelligence and Structural Intelligence Operations

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis / proposed interface  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Exploratory specification-oriented research; no implementation or empirical performance claim

## Abstract

World Entity Hybrid Differential Trees (WE-HDT) need more than a means of locating candidates. They need a controlled way to interpret entity evidence under heterogeneous perspectives, identify unresolved discrepancies, and relay findings to other perspectives or research processes. This paper proposes the **Metric-Leaf Intelligence Unit (MLIU)** as a logical, addressable intelligence unit and defines six candidate Structural Intelligence (SI) operations: **Locate, Resolve, Relate, Infer, Question, and Evolve**. A metric leaf need not be a physical tree leaf, a mathematical metric, or an autonomous agent. The design distinguishes observation from hypothesis, indexing from interpretation, and evidence from inference. It specifies operation contracts, lifecycle and governance rules, two-way discovery, residual propagation, conformance tests, and falsifiable research hypotheses. This updated edition also separates established and open knowledge from residual evidence, and introduces task-scoped Metric/Operation Masks without confusing computational activation with knowledge validation.

## 1. Research problem and scope

A conventional index answers questions about *where* qualifying records can be found. A WE-SIO intelligence layer must additionally ask: *What does the match mean under this perspective? Which assumptions support it? What remains unexplained? What other perspectives could test it?* This motivates a small, composable unit that connects an entity reference to a perspective-specific interpretation and a constrained set of operations.

The MLIU is proposed as a **logical intelligence address** rather than a mandatory process or a one-agent-per-leaf deployment model. A physical storage node may host many MLIUs; one MLIU may reference several storage structures. Conversely, an MLIU may exist without a Euclidean index.

The paper does **not** claim that the proposed operations are unique to WE-SIO, that every leaf needs reasoning, or that residuals imply new scientific laws. Its contribution is a candidate interoperable contract and a research program for testing whether the combination improves traceability and discovery.

## 2. Terminology and semantic boundaries

- **World Entity (WE):** a referent of interest, distinct from any single representation or index entry.
- **Entity reference:** a versioned, resolvable identity pointer; it is not a claim that identity can always be established unambiguously.
- **Perspective:** a descriptor specifying observations, comparison semantics, scope, uncertainty, and provenance.
- **Metric perspective:** a perspective with a declared distance function and explicit mathematical guarantees, if any.
- **Relational/directional perspective:** a perspective whose scores or links need not satisfy metric axioms.
- **Metric leaf:** a historical shorthand for a logical perspective-specific resolution point. The term does **not** require a mathematical metric or physical tree-leaf placement.
- **Residual:** a recorded discrepancy between an expectation and observation, with an explanation status and evidence lineage.
- **SI operation:** a contract-governed transformation or query over entity/perspective evidence, potentially producing a result, uncertainty, or explicit leftover.

The central separation is:

> Entity ≠ Representation ≠ Index ≠ Intelligence Unit.

## 3. Candidate MLIU contract

```yaml
MetricLeafIntelligenceUnit:
  unitId: stable-logical-id
  entityRef: versioned-entity-reference
  perspectiveId: versioned-perspective-descriptor
  metricOrRelationContract:
    kind: metric | pseudometric | similarity | directional | relational | other
    semantics: declared-comparison-and-applicability-rules
    guarantees: explicitly-validated-properties
  observations: []
  hypotheses: []
  evidence: []
  uncertainty:
    representation: declared-method
    limitations: []
  establishedKnowledgeRefs: []  # evidence-supported, scoped, versioned
  openKnowledgeRefs: []         # questions and candidate hypotheses
  residualEvidenceRefs: []     # discrepancies with explicit baselines
  epistemicStatePolicyRef: declared
  maskPolicyRef: optional-task-scoped-policy
  activeComputationViewRef: optional-transient-view
  residuals: []               # legacy compatibility alias; not a catch-all
  openQuestions: []
  supportedOperations: [Locate, Resolve, Relate, Infer, Question, Evolve]
  resourceBudget:
    compute: bounded-or-declared
    memory: bounded-or-declared
    externalCalls: bounded-or-declared
  provenance:
    sourceRefs: []
    transformationHistory: []
  version: semantic-version-or-content-hash
  relayInterfaces: []
```

This is an illustrative schema, **not** a frozen wire format. Fields may be stored by reference, lazily resolved, or shared among many units. The minimal semantic kernel is: **addressable entity/perspective binding; declared comparison or relation semantics; evidence lineage; uncertainty/unknown representation; operation capabilities; and versioned outcomes**. Whether all six are irreducible is a testable definition question, not a settled fact.

### 3.1 Invariants

1. **Identity separation:** a change of perspective or index location must not silently change the entity identity.
2. **Semantic typing:** a directional score must not be presented as a mathematical distance without verification.
3. **Evidence separation:** raw observation, derived feature, inference, and hypothesis have distinguishable statuses.
4. **Explicit unknown:** missing evidence, inapplicability, uncertainty, and negative evidence are distinct states. Open questions are not residuals unless a specific discrepancy baseline is recorded.
5. **Traceability:** every material result records its perspective, version, source lineage, and applied operation.
6. **Budget governance:** potentially expensive operations can be denied, deferred, delegated, or degraded without corrupting stored evidence.
7. **Revisability:** new evidence may revise interpretation while preserving earlier versions for audit.

## 4. Six candidate SI operations

The operations are composable, not necessarily sequential. Their output is a structured **Result** with `status`, `entityRef`, `perspectiveId`, `evidenceRefs`, `uncertainty`, `provenance`, `residualRefs`, and `nextActions` where applicable.

### 4.1 Locate — find candidate entities or perspective units

**Purpose:** resolve an address or query to candidates without pretending that retrieval proves semantic equivalence.

**Inputs:** query descriptor, applicable perspective(s), constraints, resource budget.  
**Outputs:** candidate references, coverage statement, retrieval method, score semantics, and any approximation caveats.

**Contract:** if a result is advertised as complete, its retrieval strategy must satisfy the declared completeness assumptions. Approximate retrieval must be labeled as such. A Euclidean-first path is an optional optimization, not a universal entry requirement.

**Failure/leftover:** no applicable index, stale index, uncertain identity, or insufficient budget.

### 4.2 Resolve — interpret evidence under one perspective

**Purpose:** produce a perspective-specific, evidence-grounded interpretation for an entity or candidate set.

**Inputs:** entity reference, perspective contract, observations, requested resolution level.  
**Outputs:** supported interpretations, confidence/uncertainty representation, conflicts, and unresolved evidence.

**Contract:** the interpretation must cite the observations and rules that support it. A missing or conflicting attribute cannot be silently imputed as fact.

**Failure/leftover:** incompatible units, missing observations, temporal mismatch, or unresolved ambiguity.

### 4.3 Relate — construct and test cross-entity or cross-perspective links

**Purpose:** compare, associate, align, or contrast units using declared relation semantics.

**Inputs:** one or more MLIUs, relation descriptor, matching policy.  
**Outputs:** typed links, supporting evidence, directional information, alternative explanations.

**Contract:** similarity is not identity, correlation is not causation, and a directed relation need not be symmetric. Cross-perspective mapping must state what information is preserved or lost.

**Failure/leftover:** incompatible perspective definitions, spurious linkage, unresolved confounding.

### 4.4 Infer — generate bounded conclusions or predictions

**Purpose:** apply declared rules or models to produce derived claims.

**Inputs:** evidence graph, inference contract, model/version, assumptions, budget.  
**Outputs:** derived claims or predictions with evidence lineage and validation status.

**Contract:** hypotheses and unvalidated predictions remain labeled as such; model uncertainty and known failure modes accompany the result. No causal claim follows solely from observational association.

**Failure/leftover:** underdetermination, out-of-distribution inputs, unsupported inference, conflicting models.

### 4.5 Question — surface gaps and propose discriminating tests

**Purpose:** convert uncertainty, residuals, and disagreements into explicit questions or test proposals.

**Inputs:** residual registry entries, evidence gaps, conflicting perspectives, research constraints.  
**Outputs:** questions, candidate hypotheses, expected information gain or heuristic priority, proposed tests.

**Contract:** the output distinguishes a discrepancy from its possible explanations. Candidate questions must be reproducibly linked to triggering evidence and must allow a null or mundane explanation.

**Failure/leftover:** untestable question, low evidence quality, circular hypothesis, inadequate control group.

### 4.6 Evolve — revise representation, contracts, or capabilities

**Purpose:** propose controlled changes to perspective definitions, MLIU configuration, block placement, or inference policies.

**Inputs:** proposed delta, preconditions, validation evidence, migration/rollback plan, authority.  
**Outputs:** accepted/rejected/deferred change record, new version, regression results, preserved provenance.

**Contract:** no semantic change silently overwrites a previously published definition. Evolve is subject to conformance checks, resource limits, and rollback or compensating-action policies. In WE-SIO this is a possible interface to Constrained Delta Evolution (CDE), not proof that CDE is the optimal engine.

**Failure/leftover:** contract regression, unresolved identity migration, incompatible versions, unsafe update.

## 5. Operation composition and dispatch

A candidate query path is:

```text
Question / Query
      |
      v
  Locate candidates ----> [coverage / approximation report]
      |
      v
  Resolve evidence ------> [uncertainty / conflicts]
      |
      v
  Relate perspectives ---> [typed links / alternatives]
      |
      v
  Infer cautiously ------> [claims / predictions]
      |
      v
  Question residuals ----> [testable questions]
      |
      v
  Evolve by contract ----> [validated version delta]
      |
      +------ feedback to Locate / Resolve / Relate
```

This is an illustrative path, **not** a compulsory pipeline. A simple lookup may use only Locate. A scientific anomaly workflow may begin at Question. A relational-only entity may bypass Euclidean localization entirely. The dispatcher should select the cheapest sufficient capability and record the reason for escalation.

### 5.1 Capability levels

| Level | Typical capability | Activation condition |
|---|---|---|
| L0 | identity and index lookup | ordinary retrieval |
| L1 | perspective resolution | semantic interpretation requested |
| L2 | typed relations and cross-perspective comparison | multiple views or entities |
| L3 | bounded inference and question generation | unresolved evidence or prediction request |
| L4 | governed evolution and relay | validated change proposal |

Levels are optional deployment profiles, not a ranking of entity intelligence. An implementation may provide a different capability lattice.

## 6. Two-Ways CCC and cross-metric relay

Two-Ways CCC is treated here as a **bidirectional condition/trigger and correspondence mechanism**. A forward route may localize candidates under a well-supported perspective and then resolve them under a second perspective. A backward route begins with an unexpected result or residual and asks which entities, comparisons, or missing perspectives could explain it.

```text
Forward:  query -> perspective A -> candidate set -> perspective B -> result
Backward: residual in B -> candidate questions -> revise A/B search -> test
```

A relay record should contain `sourcePerspective`, `targetPerspective`, `trigger`, `transformation`, `assumptions`, `evidenceRefs`, `uncertainty`, `result`, and `leftovers`. Backward traversal is hypothesis generation, not an inverse function unless invertibility has been established.

## 7. Residual-first intelligence without residual mysticism

A residual is modeled as:

```text
ResidualRecord = {
  entityRef, perspectiveId, expectationRef, observationRef,
  discrepancy, measurementUncertainty, alternativeExplanations,
  evidenceRefs, timestamp, status, proposedTests, provenance
}
```

Residuals can arise from noise, selection bias, measurement error, model misspecification, temporal drift, or a genuinely missing mechanism. A useful MLIU preserves these possibilities rather than equating every anomaly with discovery.

A candidate discovery loop is:

1. Register a discrepancy with its measurement conditions.
2. Test mundane explanations and data quality.
3. Compare across entities and perspectives with suitable controls.
4. Propose a new relation, feature, metric, or model only if warranted.
5. Validate on independent or held-out evidence.
6. Record rejection, revision, or acceptance, preserving the history.

**Research hypothesis:** making residuals addressable and relayable may improve reproducibility and question quality compared with ad hoc anomaly notes. This requires empirical testing.

## 8. Connection to adaptive variable-intelligence blocks

WE-SIO-004 distinguishes **partition granularity** from **intelligence capability**. MLIUs supply the capability side. A dense, stable block may need only lookup and resolution; a sparse but anomalous region may justify richer question generation. Conversely, expensive reasoning may be wasteful for high-volume routine retrieval.

A candidate dispatcher optimizes an explicit objective:

$$
J = \alpha Q_{\mathrm{task}} + \beta G_{\mathrm{evidence}} - \gamma C_{\mathrm{compute}} - \delta R_{\mathrm{error}}
$$

where quality, evidence gain, compute cost, and error risk require task-specific operational definitions. This is a **design heuristic**, not a validated universal scoring law. Any adaptive policy must be benchmarked against simpler static policies and measured for calibration and selection bias.

## 9. World Delta, epistemic delta, and CDE

An MLIU should distinguish:

- **World Delta:** evidence that the referent or environment changed.
- **Epistemic Delta:** a change in what the system knows, assumes, models, or indexes.
- **Operational Delta:** a change to resources, dispatch policy, index placement, or supported operations.

These can co-occur but are not interchangeable. For example, correcting a mislabeled observation is an epistemic change without evidence of a physical-world change. A new sensor reading may reveal a world change only after validation.

CDE can be investigated as a change-control framework with state, applicable delta, constraints, transition, and validation. Path-memory and no-reuse constraints must be **policy-specific**, not universal axioms; chess-like cyclic domains provide a counterexample to blanket no-reuse rules.

## 10. Governance, safety, and epistemic controls

1. **Provenance:** every output references source evidence and model/contract versions.
2. **Authority:** only authorized components may commit an Evolve delta; other agents may propose it.
3. **Resource caps:** compute, memory, external data access, and relay fan-out have explicit limits.
4. **Privacy:** identity linkage across perspectives requires domain-appropriate access controls and minimization.
5. **Uncertainty calibration:** numeric confidence is used only with a stated interpretation and calibration evidence.
6. **Auditability:** keep rejected hypotheses, failed tests, and superseded definitions discoverable.
7. **Domain validation:** medical, security, or scientific conclusions require appropriate independent expert and empirical validation.
8. **Failure transparency:** explicit `unknown`, `inapplicable`, `conflict`, and `budget_exceeded` statuses are preferable to invented precision.

## 11. Candidate conformance suite

| ID | Test | Passing criterion |
|---|---|---|
| MLIU-C01 | Entity/index separation | reindexing does not silently change entity reference |
| MLIU-C02 | Perspective typing | nonmetric relation cannot claim unverified metric guarantees |
| MLIU-C03 | Evidence lineage | derived claims identify inputs and transformation versions |
| MLIU-C04 | Unknown states | missing, negative, uncertain, inapplicable remain distinguishable |
| MLIU-C05 | Locate correctness | complete vs approximate retrieval labels are accurate |
| MLIU-C06 | Resolve conflict | contradictory observations remain visible |
| MLIU-C07 | Relate directionality | asymmetric relation is not silently symmetrized |
| MLIU-C08 | Infer qualification | prediction is not mislabeled as observed fact |
| MLIU-C09 | Question falsifiability | candidate question includes a feasible disconfirming outcome or explicit untestability |
| MLIU-C10 | Evolve regression | changed contract is versioned and conformance checked |
| MLIU-C11 | Budget control | exhausted budget returns bounded, explicit status |
| MLIU-C12 | Relay trace | forward/backward cross-perspective links are reproducible |
| MLIU-C13 | World/knowledge separation | epistemic revision is not recorded as a physical event by default |
| MLIU-C14 | Non-Euclidean entry | relation-only entity can be resolved without fake coordinates |

The tests are proposed **requirements**, not reported test results. SPEC-003 and SPEC-004 should convert them into machine-checkable fixtures when implementation begins.

## 12. Falsifiable research hypotheses

**H-MLIU-01 — Traceability.** Given comparable workflows, MLIU-based execution yields a higher fraction of claims with complete evidence lineage than an unstructured baseline.

**H-MLIU-02 — Selective intelligence.** A budget-aware dispatcher achieves similar task accuracy with lower average resource consumption than always-on reasoning, within predeclared tolerances.

**H-MLIU-03 — Residual relay.** Structured residual exchange improves the proportion of independently validated useful follow-up hypotheses compared with isolated residual logs.

**H-MLIU-04 — Cross-perspective coverage.** Two-way discovery finds valid relationships missed by a fixed one-way pipeline at controlled false-positive rates.

**H-MLIU-05 — Versioned evolution.** Explicit semantic versioning and regression contracts reduce undetected behavioral changes after perspective updates.

**H-MLIU-06 — Modularity.** Logical MLIUs implemented as shared services or lazy functions can match a per-leaf-agent design on specified tasks with lower orchestration overhead.

Each hypothesis requires baseline selection, datasets, metrics, error bars, and negative-case reporting. Failure is an informative research result.

## 13. Proposed validation roadmap

**Stage A — Semantic fixtures.** Construct small entity sets with Euclidean, non-Euclidean metric, and asymmetric relational perspectives. Exercise all six operations with explicit expected outcomes and counterexamples.

**Stage B — Retrieval and resolution.** Compare WE-HDT dispatch against a conventional index plus application-layer interpretation; report accuracy, recall, latency, and provenance completeness separately.

**Stage C — Residual-driven question generation.** Seed known data errors, confounders, and genuine held-out patterns. Measure whether Question differentiates them rather than rewarding sheer hypothesis volume.

**Stage D — Controlled evolution.** Apply contract-preserving and contract-breaking perspective changes; measure detection, rollback, and version reconciliation.

**Stage E — Collective relay.** Test independent agents or teams exchanging typed residuals and questions; measure reproducibility and incremental value over simple shared logs.

No benchmark result is asserted in this v0.1.0 research paper.

## 14. Integration map

| Related research | Proposed interface | Boundary |
|---|---|---|
| WE-SIO-002 | entity and perspective descriptors | does not equate identity with index |
| WE-SIO-003 | WE-HDT logical addressing | physical leaf placement is optional |
| WE-SIO-004 | adaptive capability allocation | capability and partition size vary independently |
| WE-SIO-006 | Two-Ways CCC relay | reverse discovery is not necessarily mathematical inversion |
| WE-SIO-007/008 | residual registry and metric discovery | new metrics require validation |
| WE-SIO-009 / CDE | governed structural delta | application-specific cycle policies |
| WE-SIO-010 / SSI | self-modeling extension | self-modeling does not establish consciousness |
| SIF | localization and per-node intelligence | architectural integration remains hypothetical |
| AQSI | autonomous question generation | questions require testability and governance |
| UIERU | cross-unit relay and collective learning | interoperability requires explicit contracts |

## 15. Open questions and explicit leftovers

1. What is the smallest MLIU kernel that is still distinguishable from a generic record-plus-functions abstraction?
2. Should `Question` and `Evolve` be core operations, optional capabilities, or external services?
3. How should perspective compatibility be represented when no common metric exists?
4. Can a residual registry avoid selection bias toward highly instrumented entities?
5. Which uncertainty formalisms remain interoperable without misleading conversion?
6. How should identity resolution work for composite, changing, or contested entities?
7. When does cross-perspective relay outperform straightforward feature engineering?
8. What is the cost of retaining superseded evidence and definitions at scale?
9. How can data-access restrictions survive multi-agent relay?
10. Can MLIU operation contracts be independently certified and composed safely?
11. What evidence would falsify the claim that MLIUs add value beyond existing databases, knowledge graphs, and workflow engines?
12. How should negative results be made searchable without promoting false hypotheses?

These are research tasks, not deficiencies to conceal.

## 16. Collective Learning relay record

A minimum proposed relay artifact:

```yaml
relayId: WE-SIO-MLIU-EXAMPLE
originDocument: WE-SIO-005
entityAndPerspectiveRefs: []
triggeringQuestion: "What unexplained difference motivated this work?"
claimStatus: hypothesis
assumptions: []
evidenceRefs: []
operationTrace: []
negativeTests: []
counterexamples: []
residualRefs: []
proposedNextTests: []
versionAndTimestamp: required
ownerOrReviewAuthority: declared
```

Research trace files should record why a definition changed, not just its latest wording. In particular, `HYPOTHESIS-REGISTRY.md`, `DEFINITION-REGISTRY.md`, `COUNTEREXAMPLE-REGISTRY.md`, `DECISION-LOG.md`, and `UNRESOLVED-RESIDUALS.md` should link to stable operation/test identifiers.

## 17A. Epistemic separation: established, open, and residual (v0.1.0 update)

This section extends the original MLIU contract in response to `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md`. A Metric Index is an addressing and comparison structure; it must not implicitly certify the epistemic status of everything indexed. Three **logical views** are required for research-grade operation, although they need not be three physical tables or indexes.

| View | Admission criterion | Typical SI operations | Exclusion rule |
|---|---|---|---|
| **Established Knowledge** | Evidence-supported assertion with scope, applicability, provenance, version and validation policy | Locate, Resolve, Infer, Relate | Never equate “established” with universally true |
| **Open Knowledge** | Explicit unknown, question, untested hypothesis, candidate metric or unresolved relation | Question, Infer (provisional), Evolve (proposal) | Do not treat absence of data as measured deviation |
| **Residual Evidence Registry (RER)** | Observation/constraint/model discrepancy with an explicit baseline and evidence lineage | Resolve, Question, Relate, Evolve (proposal) | Do not use as a miscellaneous unknown bucket |

**Unknown ≠ Residual.** An unmeasured material property belongs to Open Knowledge. A measured property contradicting a stated prediction may create a residual, provided the prediction, observation, uncertainty and provenance are documented. A candidate explanation remains Open until evaluated; it is not promoted simply because a residual exists.

Epistemic status is **perspective-, context-, time-, and version-scoped**. An assertion may be established under one measurement contract and open under another. A SQL `NULL` may mean missing, unknown, withheld or inapplicable; it cannot be classified as a residual by syntax alone. Inferences, measurements, hypotheses, and entity identity remain separate objects.

### 17A.1 Suggested typed records

```yaml
EpistemicAssertion:
  assertionId: stable-id
  entityRef: versioned-reference
  perspectiveId: versioned-descriptor
  proposition: typed-claim
  status: established | open | revised | withdrawn
  applicability: context-and-time-scope
  evidenceRefs: []
  uncertainty: declared
  evaluatorPolicyRef: versioned
  provenance: required
  revisionHistory: []

ResidualEvidence:
  residualId: stable-id
  entityRef: versioned-reference
  perspectiveId: versioned-descriptor
  baselineRef: prediction-or-constraint-or-explanatory-model
  observationRefs: []
  discrepancySemantics: numeric | logical | structural | explanatory
  uncertaintyAndConfounders: []
  diagnosticStatus: untriaged | investigating | explained | unresolved
  candidateHypothesisRefs: []
  provenance: required
```

An explanatory residual requires a declared explanatory commitment or constraint; mere curiosity about an unknown is not sufficient. A registry must preserve negative evidence and mundane failure explanations (measurement error, drift, leakage, join multiplicity, selection bias) before proposing a new mechanism.

### 17A.2 Promotion, demotion and rollback

A transition from `open` to `established` requires a declared validation gate, sufficient evidence, evaluator identity, applicability conditions and versioned decision. Counterevidence may trigger `established → revised/withdrawn`, without erasing the original evidence. Repeated agent agreement does not by itself count as independent validation. In regulated settings, access restrictions and approval policies govern what can be viewed or promoted.

## 17B. Metric Mask and operation-scoped computational activation

A **Metric Mask** selects which perspective descriptors, candidate metrics, relations or metric-leaf services are eligible for a particular task. It does not redefine the mathematical semantics of the selected descriptors. A **Node/Edge Mask** restricts traversals; an **Operation Mask** limits callable SI operations; **Depth/Budget Masks** bound exploration. These may be composed into a task-scoped active view while preserving the underlying MLIU identity and stored evidence.

```text
request = (task, entityScope, perspectiveScope, authorization, budget)
mask = GenerateMask(request, substrateVersion, policyVersion)
view = ApplyMask(eligibleMLIUs, mask)
result = ExecuteSI(view, requestedOperation)
report = ValidateCoverageAndEvidence(result, request)
feedback = RemaskOrEscalate(report)
```

Mask, Unmask and Remask are **execution-control operations**, not new evidence-producing SI operations by default. They may be exposed as control-plane interfaces to the six canonical operations. `Unmask` never widens permissions beyond the caller's authorization. Mask policy changes should be recorded as **Activation Delta**, not silently conflated with Knowledge Delta or persistent Structural Delta.

### 17B.1 Mask contract

A reproducible mask record should include: `maskId`, `taskId`, `perspectiveRefs`, `substrateVersion`, `policyVersion`, `authorizationScope`, `selectedEntityOrNodePredicates`, `selectedMetricOrRelationRefs`, `allowedOperations`, `depthLimit`, `resourceBudget`, `completenessMode`, `evidenceRefs`, and `provenance`.

For exact queries, a mask must preserve candidate **coverage**. If that cannot be established, the implementation must expand/fallback to a verified reference path or explicitly declare approximate results with measured recall. Masking cannot erase audit trails or circumvent database row/column security. Cache validity must be checked when schemas, perspective definitions, permissions, or data distributions change.

The cost model must include mask generation, compilation, execution, fallback, and cache invalidation. A mask that merely suppresses output but still performs full computation does not demonstrate computational savings.

### 17B.2 Separation of computational and epistemic states

- **Activation Delta:** changes which MLIUs, metrics and operations are active for a task.
- **Knowledge Delta:** changes evidence-backed epistemic assertions, hypotheses or uncertainty.
- **Structural Delta:** changes persistent topology, membership, indexing or capability organization.
- **World/Source-State Delta:** changes the represented external state or source records; not equivalent to a change in belief.

An effective mask may remain stable while knowledge changes, and knowledge may be revised without splitting a block. `WE-SIO-009` and CDE govern candidate evolution and application-specific constraints; no universal “never reuse a delta” rule is assumed.

## 17C. Updated operation contracts and conformance

The six canonical operations retain their original names and meanings, with the following additional obligations:

| Operation | Epistemic obligation | Mask obligation |
|---|---|---|
| Locate | Return typed status and evidence reference when requested | Preserve exact-query coverage or declare approximation |
| Resolve | Distinguish identity ambiguity, open knowledge and genuine discrepancy | Expand mask when needed to resolve conflicting evidence |
| Relate | Preserve directionality, provenance and scope of relations | Do not infer absent edges solely from masked-out edges |
| Infer | Mark provisional versus validated conclusions | Record mask/perspective limitations and excluded evidence risk |
| Question | Route unknowns to Open Knowledge; discrepancies to RER | May propose expanded exploration masks |
| Evolve | Produce proposals subject to validation/promotion contracts | Distinguish activation, knowledge and structural changes |

**Candidate conformance checks** (to be synchronized with `SPEC-003`, `SPEC-004`, and `SPEC-005`):

1. `MLIU-EPI-001`: a missing measurement without a baseline remains Open, not Residual.
2. `MLIU-EPI-002`: residual admission requires baseline, observation, discrepancy semantics and provenance.
3. `MLIU-EPI-003`: established assertions carry perspective, context, uncertainty and evidence lineage.
4. `MLIU-EPI-004`: promotion/demotion/withdrawal decisions are versioned and auditable.
5. `MLIU-MASK-001`: exact masked retrieval matches a full-view reference or fails closed.
6. `MLIU-MASK-002`: mask selection and remasking never bypass access controls.
7. `MLIU-MASK-003`: activation-only changes leave persistent entity identity and topology intact.
8. `MLIU-MASK-004`: mask performance reports include generation and fallback costs.
9. `MLIU-MASK-005`: stale masks are invalidated on relevant policy/schema/perspective changes.
10. `MLIU-RELAY-001`: shared masks disclose task and substrate compatibility and require target-task validation.

### 17C.1 Proposed experiments and falsification

Compare full-view execution, static masks, learned masks, and adaptive remasking across (a) structured metric retrieval, (b) mixed metric/relational inference, and (c) SQL-backed schema/column selection. Evaluate answer quality, recall, false exclusions, end-to-end latency, total compute, epistemic misclassification, residual false positives, auditability, and cross-task transfer. Include counterexamples where mask generation is more expensive than execution, masking omits decisive evidence, or a misleading residual arises from SQL JOIN duplication. These are hypotheses for validation, **not measured outcomes**.

**Related research:** `EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md` establishes the general framework; `EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md` develops a SQL-facing testbed; `WE-SIO-004` treats AVIB activation and mature-structure preservation; `WE-SIO-007` formalizes residual diagnosis; `WE-SIO-008` covers candidate metric promotion.

---

## 17. Conclusion

The proposed Metric-Leaf Intelligence Unit gives WE-SIO a candidate bridge between **retrieval** and **evidence-governed structural intelligence**. Its six operations—Locate, Resolve, Relate, Infer, Question, Evolve—provide a vocabulary for composition, escalation, uncertainty management, and versioned learning. The essential design choice is not to make every index leaf an intelligent agent, but to make perspective-specific interpretation **addressable, typed, testable, and relayable**. Whether this design yields a practical advantage is an open empirical question; the contracts and validation plan make that question answerable.

---

## Suggested figure insertion

- `Fig-005-Metric-Leaf-Intelligence-Unit.png`: after Section 3, showing logical unit, shared services, evidence, and relay interfaces.
- `Fig-006-Two-Ways-CCC-Cross-Metric-Discovery.png`: after Section 6, showing forward and backward pathways and residual triggers.
- `Fig-007-Residual-Driven-Scientific-Discovery-Loop.png`: after Section 7, showing mundane-error checks and independent validation.

## Research status and citation note

This is a proposed conceptual architecture prepared for WE-SIO v0.1.0. Terminology, interface schemas, and hypotheses are provisional. The paper reports **no empirical validation**. Related ideas in indexing, knowledge graphs, agent orchestration, scientific anomaly analysis, and schema evolution must be compared carefully before any novelty or performance claim is made.

**Repository:** `World-Entity-and-Structural-Intelligence-Operations`  
**License intent:** Apache-2.0 (subject to repository license file)
