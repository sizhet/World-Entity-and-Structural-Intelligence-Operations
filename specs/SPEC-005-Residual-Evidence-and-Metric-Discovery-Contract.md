# SPEC-005 — Residual, Evidence, and Metric Discovery Contract

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** 0.1.0 — Candidate Research Specification  
**Status:** Proposed; not an implementation standard  
**Scope:** Residual qualification, epistemic separation, evidence provenance, candidate perspective discovery, mask-safe investigation, validation, promotion, and rollback  
**Dependencies:** WE-SIO-002, WE-SIO-006–009; SPEC-001–004  
**License:** Apache-2.0 (repository-level license, when adopted)

## 1. Purpose

This specification defines how a WE-SIO implementation MAY record discrepancies between observations and expectations, preserve the evidence underlying those discrepancies, propose new measurement or relational perspectives, and validate such proposals before they influence authoritative reasoning or retrieval. The central goal is **accountable discovery**, not automatic scientific truth production.

A residual is evidence of a gap between a stated expectation and an observation under a declared context. **Unknown is not a residual**: absence of a prediction, missing data, an unasked question, or an SQL NULL MUST NOT automatically qualify for the Residual Evidence Registry (RER). It is **not** by itself proof of an undiscovered causal mechanism, a new mathematical metric, or a physical law.

Normative terms **MUST**, **MUST NOT**, **SHOULD**, and **MAY** apply to implementations claiming conformance to this *candidate* specification. These terms do not imply external standardization.

## 2. Semantic distinctions

| Term | Meaning | Key boundary |
|---|---|---|
| World Entity (WE) | Referent tracked through an entity identity contract | Not identical to a record or index |
| Observation | Reported or measured value, with time and provenance | Not automatically ground truth |
| Expectation | Predicted, assumed, or contractually expected outcome | Must identify model and conditions |
| Residual | Typed comparison between observation and expectation | May be noise, error, bias, or a substantive gap |
| Evidence | Source-linked support or challenge for a claim | Evidence quality varies |
| Hypothesis | Testable proposed explanation | Not an established finding |
| Perspective | Declared method of observing, comparing, or relating entities | Not every perspective is a metric |
| Metric candidate | Proposed distance function with a specified domain | Cannot claim metric status without testing axioms |
| Relational candidate | Proposed typed relation, possibly asymmetric or directional | Cannot inherit metric pruning guarantees |
| Knowledge Delta | Change in a system's claims or models | Not necessarily a change in the world |
| Structural Delta | Change in index, registry, or computational structure | Must preserve declared guarantees |

**Invariant R-01:** An implementation MUST preserve the distinction between the world, its observations, the model's expectations, and the model's revisions.

## 3. Minimal interoperable records

### 3.1 ResidualRecord

```json
{
  "residualId": "res-001",
  "schemaVersion": "0.1.0",
  "entityRefs": ["we-123"],
  "perspectiveId": "treatment-response-v2",
  "expectationRef": "prediction-17",
  "observationRefs": ["observation-88"],
  "comparisonOperator": "observed-minus-predicted",
  "residualValue": {"value": -0.23, "unit": "normalized-response"},
  "uncertainty": {"kind": "interval", "lower": -0.31, "upper": -0.15},
  "contextRef": "cohort-definition-4",
  "eventTime": "2026-11-05T15:00:00Z",
  "recordedAt": "2026-11-05T15:05:00Z",
  "evidenceRefs": ["evidence-41"],
  "qualityFlags": ["confounding-not-excluded"],
  "status": "untriaged",
  "version": 1,
  "provenance": {"producer": "research-pipeline-A", "methodVersion": "0.3"}
}
```

Fields such as numerical value and uncertainty MAY be replaced by a typed categorical or relational discrepancy when subtraction is not meaningful. A missing value MUST NOT be silently interpreted as zero.

### 3.2 EvidenceRecord

```json
{
  "evidenceId": "evidence-41",
  "sourceRef": "dataset-release-7",
  "sourceType": "dataset",
  "claimRefs": ["res-001"],
  "role": "supports",
  "collectionMethod": "observational",
  "collectedAt": "2026-11-05T14:00:00Z",
  "integrity": {"digestAlgorithm": "sha256", "digest": "<actual-digest-required>"},
  "limitations": ["selection-bias-possible"],
  "accessPolicy": "restricted",
  "provenance": {"curator": "study-team"}
}
```

The digest above is a placeholder, not a valid checksum. Real records MUST provide an actual digest when claiming content integrity. Source access controls MUST be enforced independently of registry visibility.

### 3.3 PerspectiveCandidate

```json
{
  "candidateId": "pc-009",
  "kind": "directional-relation",
  "name": "context-conditional-response-shift",
  "domainRef": "cohort-definition-4",
  "inputPerspectiveRefs": ["treatment-response-v2", "baseline-state-v1"],
  "definitionRef": "definition-pc-009-v1",
  "proposer": "discovery-agent-2",
  "motivatingResidualRefs": ["res-001"],
  "hypothesisRefs": ["hyp-012"],
  "validationPlanRef": "validation-pc-009",
  "status": "proposed",
  "version": 1
}
```

The candidate's `kind` MUST be one of a declared set, such as `measurement`, `mathematical-metric`, `similarity`, `directional-relation`, `categorical-relation`, or `composite-perspective`. Implementations MAY extend this vocabulary with a versioned type registry.

### 3.4 ValidationDecision

```json
{
  "decisionId": "vd-002",
  "candidateId": "pc-009",
  "candidateVersion": 1,
  "outcome": "hold",
  "evaluations": ["semantic-review-3", "holdout-test-5"],
  "unresolvedIssues": ["external-replication-needed"],
  "decisionAuthority": "review-board-A",
  "decidedAt": "2026-11-05T17:00:00Z",
  "effectiveScope": "sandbox-only",
  "rationale": "Insufficient independent evidence"
}
```

A decision MUST identify its authority, effective scope, evidence basis, and candidate version. `hold` is not equivalent to `reject`.

## 4. Residual lifecycle contract

The candidate lifecycle is:

`DETECTED → TRIAGED → INVESTIGATING → {EXPLAINED | RETAINED_OPEN | INVALIDATED}`

A record MAY be reopened from `EXPLAINED` or `INVALIDATED` when new evidence emerges. An implementation MUST retain prior states and the rationale for every transition; it MUST NOT rewrite history to make a hypothesis appear retrospectively confirmed.

**Required operations:**

- `registerResidual(record)`: validate references and persist a new immutable version.
- `triageResidual(id, classification, evidenceRefs)`: classify likely error, noise, model misspecification, distribution shift, unknown, or mixed causes without asserting certainty.
- `linkResiduals(ids, relation, rationale)`: create an auditable, directional or symmetric relation as declared.
- `proposeExplanation(id, hypothesisRef)`: register a candidate explanation, not a fact.
- `resolveResidual(id, outcome, evidenceRefs)`: preserve explanation and alternative hypotheses.
- `reopenResidual(id, reason, evidenceRefs)`: append a new state transition.

**Invariant R-02:** Every nontrivial state transition MUST include actor, timestamp, previous version, new version, reason, and evidence references or an explicit `evidence-not-yet-available` flag.

**Invariant R-03:** Records with insufficient evidence MUST remain queryable as unresolved; they MUST NOT be silently discarded solely because they fail a significance threshold.

**Invariant R-04:** Retention is subject to privacy, safety, and data-governance policies; an immutable audit trail MAY store redacted references rather than protected raw content.

## 5. Evidence provenance and quality

Every evidence reference MUST declare a resolvable source identifier or a documented reason it cannot be disclosed. Evidence SHOULD include acquisition method, event time, recording time, transformation lineage, relevant sampling frame, measurement uncertainty, and known limitations.

Evidence roles MUST distinguish `supports`, `challenges`, `context`, and `inconclusive`. An evidence item MAY play different roles for different claims; the relationship MUST be explicit.

A quality assessment SHOULD examine:

1. Measurement and labeling error.
2. Missingness and selection bias.
3. Confounding and alternative explanations.
4. Temporal leakage and distribution shift.
5. Repeated testing and multiple-comparison effects.
6. Independence of evaluation data.
7. Reproducibility and provenance integrity.
8. Privacy, consent, and permissible reuse.

**Invariant E-01:** A claim MUST NOT inherit the certainty of its most favorable evidence while ignoring contradictory evidence.

**Invariant E-02:** Observation, inference, simulation, and externally verified result MUST remain distinguishable in storage and presentation.

**Invariant E-03:** Confidence or score values MUST declare their interpretation and calibration status; arbitrary scores MUST NOT be presented as probabilities.

## 6. Residual-to-discovery pipeline

```text
Observed outcomes + declared expectations
                 |
                 v
       Typed residual registration
                 |
                 v
       Quality and confounder triage
                 |
                 v
      Cross-entity / cross-perspective
             residual analysis
                 |
                 v
     Candidate measurement / metric /
        relation / perspective
                 |
                 v
      Semantic + formal validation
                 |
                 v
     Holdout + negative controls +
       replication where feasible
                 |
                 v
     Governance decision and scope
          /             |           \
       reject          hold        promote
          \             |           /
           Versioned research trace
```

Forward Two-Ways CCC MAY generate candidate sets and predictions. Reverse Two-Ways CCC MAY use residual patterns to propose missing conditions, additional perspectives, or alternative queries. Reverse discovery MUST NOT alter authoritative indices or conclusions without an explicit promotion decision.

## 7. Candidate classification and formal obligations

### 7.1 Mathematical metrics

A candidate `d : X × X → ℝ` claiming to be a mathematical metric MUST satisfy, over its declared domain:

1. `d(x,y) ≥ 0`.
2. `d(x,y) = 0` if and only if `x = y` under the declared identity relation.
3. `d(x,y) = d(y,x)`.
4. `d(x,z) ≤ d(x,y) + d(y,z)`.

Finite property tests can identify violations but cannot generally prove universal validity over an infinite domain. Formal proof, construction-based guarantees, or carefully bounded claims SHOULD be used where exact metric indexing depends on these properties. A pseudometric MUST be labeled separately when distinct entities may have zero distance.

### 7.2 Similarities and directional relations

Similarity functions MUST declare range, ordering, null handling, symmetry assumptions, and normalization. Directional relations MUST preserve argument order, direction semantics, and temporal/context qualifiers. Neither type MAY use triangle-inequality pruning without a separately validated bound.

### 7.3 Measurements and composites

Measurements MUST specify units, admissible values, acquisition procedure, missingness semantics, and uncertainty. Composite perspectives MUST identify inputs, transformations, leakage risks, and version dependencies.

**Invariant M-01:** A candidate's type determines its legal inference and indexing operations.

**Invariant M-02:** A candidate MUST NOT be promoted merely because it improves fit on the same data used to generate it.

## 8. Candidate validation gates

Promotion MUST be preceded by a recorded decision across six gates:

| Gate | Required question | Typical evidence |
|---|---|---|
| G1 — Semantic | Is the candidate well-defined and interpretable within scope? | Descriptor review, edge cases |
| G2 — Formal | Are claimed mathematical properties valid? | Proof, bounded checks, counterexamples |
| G3 — Data | Is the motivating residual reliable? | Source audit, noise/confounder analysis |
| G4 — Incremental | Does it improve a declared objective beyond baselines? | Holdout comparison, ablations |
| G5 — Robustness | Does it generalize and avoid harmful failure modes? | Shift tests, negative controls, replication |
| G6 — Governance | Is the intended deployment authorized and reversible? | Approval, monitoring, rollback plan |

A gate MAY return `pass`, `fail`, `hold`, or `not-applicable-with-rationale`. Promotion requires every applicable gate to pass; exceptions MUST be explicitly scoped and authorized. Sandbox evaluation MAY proceed with `hold` status, but MUST remain isolated from production guarantees.

## 9. Promotion, versioning, and rollback

Candidate status lifecycle:

`PROPOSED → SANDBOX → UNDER_VALIDATION → {PROMOTED | REJECTED | HELD}`

`PROMOTED → {MONITORED | DEPRECATED | ROLLED_BACK}`

Promotion MUST bind an immutable candidate version, a declared application scope, validation evidence, an accountable authority, and effective time. Revisions MUST create new versions rather than silently mutate published definitions.

When a promoted perspective changes:

- A **Knowledge Delta** records changes to accepted claims or models.
- A **Structural Delta** records registry, index, or MLIU changes.
- An **Observation Delta** records newly ingested or corrected observations.
- A **World Delta** is asserted only when evidence supports a change in the referent world, not merely in its representation.

CDE MAY orchestrate these transitions subject to preconditions, invariants, resource budgets, rollback semantics, and policy controls. Rollback of a model or index MUST NOT be described as reversal of an external world event.

**Invariant P-01:** Promotion MUST NOT retroactively rewrite historical evidence or residual records.

**Invariant P-02:** Rollback MUST identify affected dependent perspectives, indices, queries, and published claims.

**Invariant P-03:** An experimental candidate MUST NOT silently affect a query advertised as exact or validated.

## 10. API-level interface contracts

The following signatures are conceptual, not a prescribed programming language:

```text
registerResidual(ResidualRecord) -> ResidualRef | ContractError
attachEvidence(ClaimRef, EvidenceRef, EvidenceRole) -> LinkRef
queryResiduals(Filter, AccessContext) -> Page<ResidualRef>
clusterResiduals(Query, MethodDescriptor, Budget) -> HypothesisSet
proposePerspective(CandidateDescriptor, MotivatingEvidence) -> CandidateRef
validateCandidate(CandidateRef, ValidationPlan) -> ValidationReport
recordDecision(CandidateRef, ValidationReportRefs, Authority) -> DecisionRef
promotePerspective(CandidateRef, DecisionRef, Scope) -> PerspectiveVersion
rollbackPerspective(PerspectiveVersion, Reason, Authority) -> DeltaRecord
exportResearchRelay(ResearchScope, AccessPolicy) -> RelayBundle
```

Every operation MUST return a structured status distinguishing success, incomplete evidence, authorization failure, invalid contract, resource exhaustion, and internal error. Discovery operations SHOULD expose budgets, termination criteria, and reproducibility seeds when applicable. Asynchronous results MUST preserve input version references.

## 11. Security, privacy, and scientific integrity

Residual registries can contain sensitive observations or reveal protected patterns. Implementations MUST enforce authorization, data minimization, and applicable retention policies. Public research relays SHOULD export metadata, hashes, aggregate statistics, or synthetic examples when raw records cannot be shared. A hash alone does not guarantee anonymity.

Automated discovery SHOULD use safeguards against fabricated provenance, circular evidence, data poisoning, post-selection inference, and uncontrolled hypothesis proliferation. Clinical or other high-stakes hypotheses MUST be treated as research proposals until validated under domain-appropriate oversight; this specification does not authorize medical decisions.

## 12. Conformance tests

| ID | Test | Expected outcome |
|---|---|---|
| CT-001 | Register residual with valid references | Accepted with immutable version |
| CT-002 | Register residual without expectation context | Rejected or explicitly marked incomplete |
| CT-003 | Missing numeric residual | Never coerced to zero |
| CT-004 | Non-numeric discrepancy | Typed comparison accepted |
| CT-005 | Observation and expectation timestamps differ | Distinction preserved |
| CT-006 | Change a historical residual value | New version, no silent overwrite |
| CT-007 | Resolve residual without evidence | Blocked or flagged as unsupported |
| CT-008 | Reopen invalidated residual | Prior rationale retained |
| CT-009 | Attach contradictory evidence | Both roles remain visible |
| CT-010 | Uncalibrated score labeled probability | Rejected or relabeled |
| CT-011 | Asymmetric candidate claims metric status | Fails formal gate |
| CT-012 | Triangle inequality counterexample | Exact metric-pruning claim rejected |
| CT-013 | Pseudometric labeled metric without identity caveat | Fails or requires revision |
| CT-014 | Directional relation reversed | Different semantics preserved |
| CT-015 | Candidate evaluated on discovery data only | Cannot pass incremental gate |
| CT-016 | Negative controls fail | Promotion held or rejected |
| CT-017 | Candidate lacks provenance | Promotion blocked |
| CT-018 | Candidate has unresolved applicable gate | Production promotion blocked |
| CT-019 | Sandbox candidate used in exact production retrieval | Prevented or guarantee downgraded explicitly |
| CT-020 | Rollback a promoted perspective | Dependents identified and audit preserved |
| CT-021 | World unchanged, knowledge revised | Knowledge Delta only |
| CT-022 | Evidence redacted for public export | Access policy honored; provenance retained |
| CT-023 | Discovery exceeds resource budget | Terminates with partial status |
| CT-024 | Repeat validation with fixed inputs | Comparable reproducibility metadata |
| CT-025 | Duplicate candidate proposal | Linked or versioned, not silently conflated |
| CT-026 | Conflicting validation decisions | Both recorded with authorities and scope |
| CT-027 | Unsupported source checksum placeholder | Not treated as verified integrity |
| CT-028 | Historical query after perspective update | Version-pinned semantics preserved |

A test result MUST record implementation version, fixture identifiers, expected/actual outcome, and pass/fail/blocked status. These tests are **proposed**; no passing implementation is asserted here.

## 13. Conformance profiles

- **R0 — Evidence-Aware Residual Registry:** CT-001–010, CT-022, CT-027, and invariants R/E.
- **R1 — Candidate Perspective Registry:** R0 plus CT-011–014, CT-025 and M invariants.
- **R2 — Validated Discovery Workflow:** R1 plus CT-015–018, CT-024, CT-026 and all six gates.
- **R3 — Controlled Production Evolution:** R2 plus CT-019–021, CT-023, CT-028 and P invariants.

Profiles are cumulative. An implementation MUST declare supported profile, exceptions, and test evidence. Profile labels do not indicate scientific validity of any particular discovered perspective.

## 14. Testable research hypotheses

**H-005-01 — Retention value.** A structured residual registry improves subsequent discovery of reproducible patterns versus a baseline that discards unexplained observations. *Metric:* independently validated discoveries per investigation hour, with false-discovery rate reported.

**H-005-02 — Cross-perspective gain.** Linking residuals across entity perspectives increases useful candidate generation relative to isolated single-perspective analysis. *Metric:* validated incremental predictive or explanatory value on held-out tasks.

**H-005-03 — Governance quality.** Six-gate validation reduces unsupported promotions relative to fit-only candidate selection. *Metric:* promotion precision and post-deployment reversals.

**H-005-04 — Traceability.** Provenance-complete relay bundles improve reproducibility by independent teams. *Metric:* successful reproduction rate and time to reproduce.

**H-005-05 — Cost control.** Budgeted reverse discovery maintains bounded resource consumption with acceptable loss in validated discoveries. *Metric:* compute cost versus discovery yield.

These hypotheses are not confirmed results. Negative outcomes and confounders MUST be recorded.

## 15. Validation roadmap

**Phase A — Contract fixtures:** Build synthetic residuals covering numerical, categorical, temporal, directional, missing, and contradictory cases. Verify CT-001–014.

**Phase B — Discovery baselines:** Compare residual retention and candidate generation against simple anomaly logging, conventional feature engineering, and non-relay workflows. Pre-register evaluation criteria where feasible.

**Phase C — Independent validation:** Use held-out datasets, negative controls, ablations, distribution-shift checks, and external replication when available. Evaluate CT-015–018 and research hypotheses.

**Phase D — Controlled evolution:** Integrate with WE-HDT, MLIU, Two-Ways CCC, and CDE in a sandbox. Validate version pinning, index guarantees, rollback, and CT-019–028.

**Phase E — Collective relay:** Publish reproducible, privacy-preserving hypothesis/evidence/decision bundles with explicit unresolved residuals and counterexamples.

## 16. Research trace and relay contract

Each proposed discovery SHOULD be traceable through:

```text
Residual IDs
  → Evidence IDs and quality assessment
  → Hypothesis IDs
  → Perspective Candidate and definition version
  → Validation plan and reports
  → Counterexamples and negative results
  → Decision and authority
  → Knowledge/Structural Delta
  → Downstream dependency list
  → Open questions and relay handoff
```

The repository's `research-trace/HYPOTHESIS-REGISTRY.md`, `DEFINITION-REGISTRY.md`, `COUNTEREXAMPLE-REGISTRY.md`, `DECISION-LOG.md`, and `UNRESOLVED-RESIDUALS.md` SHOULD cross-reference stable identifiers from this chain. Research-trace Markdown is a human-readable publication surface; machine-readable implementations MAY use other storage while preserving equivalent semantics.

## 17. Explicit leftovers and definition evolution

1. What minimum residual schema works across numerical, logical, relational, and multimodal discrepancies without becoming vacuous?
2. How should dependent evidence be aggregated without double-counting?
3. How should discovery control multiple comparisons and adaptive testing under continuous hypothesis generation?
4. Which candidate metrics can be formally verified, and which require bounded empirical guarantees?
5. When does a new perspective provide explanatory gain rather than merely extra model capacity?
6. How should contradictory perspectives coexist under differing provenance and temporal scope?
7. Can residual-sharing improve scientific discovery while protecting sensitive data?
8. Which CDE rollback semantics are meaningful when external data or world states are irreversible?
9. What is the right threshold for promoting a perspective from sandbox to operational use?
10. How can independent teams reproduce a relay without exposing restricted datasets?

These are first-class research questions, not omissions to conceal. The **Definition Evolution Loop** is:

`Minimal contract → application → counterexample → residual → revision proposal → conformance regression → versioned decision`.

Revisions MAY narrow, split, or deprecate concepts; they need not always generalize them. **Define the invariant, not the inventory.**

## 18. Cross-references

- `docs/WE-SIO-002-World-Entity-Representation-and-Perspective-Indices.md`
- `docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md`
- `docs/WE-SIO-008-Metric-Discovery-and-Perspective-Evolution.md`
- `docs/WE-SIO-009-World-Delta-Knowledge-Delta-and-CDE.md`
- `docs/WE-SIO-011-Minimal-Kernel-Contracts-and-Definition-Evolution.md`
- `specs/SPEC-001-World-Entity-Identity-and-Perspective-Descriptor-Contract.md`
- `specs/SPEC-002-Euclidean-Metric-and-Relational-Index-Conformance.md`
- `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md`
- `specs/SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md`
- `specs/SPEC-006-Definition-Evolution-and-Research-Relay-Contract.md` (planned)

---

**Research principle:** *Unknown is not zero. Unexplained is not useless. A residual is evidence of a gap, not automatically evidence of a new law.*

**Relay principle:** *Preserve not only what we know, but also how we arrived there, what challenged it, and what remains unknown.*


## 19. Epistemic Separation Contract (ESC) — 2026-11-05 update

This section refines, rather than replaces, Sections 2–9. An implementation claiming the **ESC profile** MUST maintain three logically distinguishable views, even when they share one physical database or index:

| View | Admission criterion | Example | Prohibited inference |
|---|---|---|---|
| Established Knowledge (`EK`) | Evidence-supported claim with explicit scope, perspective, conditions, and version | A calibrated measurement within a declared range | “Established” means absolute or timeless truth |
| Open Knowledge (`OK`) | Unknown, untested, contested, or provisional claim/question | A candidate explanatory variable without a tested prediction | Unknown automatically implies observed discrepancy |
| Residual Evidence Registry (`RER`) | A qualified, evidence-linked discrepancy against a declared comparison baseline | Observed response deviates from a versioned prediction | Discrepancy proves a new mechanism |

**ESC-001 — Logical separation.** An implementation MUST expose the knowledge state of a material claim, including its applicable context and version. A shared physical table MAY implement all three views if their semantic boundaries remain testable.

**ESC-002 — Scope relativity.** Knowledge status MUST be evaluated relative to entity, perspective, population/context, observation time, and definition/model version. A claim MAY be established in one scope and open in another.

**ESC-003 — Missingness.** Missing, not applicable, withheld, unobserved, uncertain, negative evidence, and contradicted MUST NOT be silently mapped to one another. SQL `NULL` alone does not determine epistemic status.

**ESC-004 — Provenance.** Every material established assertion MUST identify supporting evidence, applicable conditions, validation authority or rule, and the current version. Open claims MUST identify why they remain open where known.

**ESC-005 — No automatic truth promotion.** A residual, repeated model output, high similarity score, or multi-agent consensus MUST NOT automatically convert an open hypothesis into established knowledge.

**ESC-006 — Non-destructive revision.** Promotion, revision, withdrawal, and demotion MUST preserve prior versions and downstream dependency references where legally and operationally permitted. Erasure required by privacy law MUST be honored through appropriately designed redaction/audit mechanisms.

## 20. Residual Qualification Contract (RQC)

The term **Residual Evidence Registry (RER)** denotes the qualified residual record collection, not a miscellaneous bucket for unanswered questions. The existing `ResidualRecord` of Section 3 remains the base record; conformant implementations MUST additionally provide, directly or by resolvable reference, the following semantic fields:

```yaml
ResidualQualification:
  residualId: stable-identifier
  entityRefs: [versioned-entity-reference]
  perspectiveRef: versioned-perspective-and-comparator-contract
  context: {scope: declared, timeWindow: declared}
  baseline:
    kind: prediction | expectation | constraint | explicit-explanatory-claim
    reference: versioned-model-or-rule
    conditions: declared
    expectedValueOrAssertion: typed
  observation:
    evidenceRefs: [source-linked-evidence]
    observedValueOrAssertion: typed
    uncertainty: declared
  discrepancy:
    comparatorRef: typed-versioned-comparison
    result: typed-discrepancy
    thresholdOrDecisionRule: declared
    uncertaintyAssessment: declared
  qualification:
    status: qualified | provisional | rejected | superseded
    assessor: policy-or-authority-reference
    reasons: [coded-or-text-reasons]
  investigation:
    alternativeExplanations: []
    followUpQuestions: []
    maskPolicyRef: optional
  provenance: {createdAt: timestamp, versions: [], lineage: []}
```

**RQC-001 — Baseline required.** RER admission MUST reference an explicit baseline or constraint and a comparator that is meaningful for the perspective. A numerical difference is not required for a relational or logical contradiction, but the comparison rule MUST be declared.

**RQC-002 — Observation required.** Admission MUST identify the observation and evidence lineage. A purely hypothetical counterexample with no observed case belongs in an open question or test-fixture registry unless explicitly labeled as synthetic.

**RQC-003 — Qualification decision.** The registry MUST distinguish `provisional`, `qualified`, `rejected`, and `superseded`; an implementation MUST NOT present a provisional mismatch as an independently validated discovery.

**RQC-004 — Error and confounding controls.** Before scientific interpretation or promotion, investigators SHOULD assess measurement error, model miscalibration, data leakage, duplicate observations, selection bias, confounding, and distribution shift. Unassessed alternatives MUST remain explicit leftovers.

**RQC-005 — Unknown routing.** A record lacking a defensible baseline/comparator MUST be routed to `OK` (or an appropriately typed non-residual queue) rather than RER. The implementation MUST expose this routing decision for audit.

**RQC-006 — No residual laundering.** Repeated observations of the same source, correlated agents, or derivative datasets MUST NOT be counted as independent confirmation without an explicit dependence model.

**RQC-007 — Version sensitivity.** If an expectation or comparator changes, the earlier residual MUST remain attributable to its original baseline; recalculation creates a new assessment or linked revision, not a silent overwrite.

**RQC-008 — Privacy.** Residual evidence may reveal sensitive facts even when aggregate values seem harmless. Access control, minimization, retention, and relay restrictions MUST apply to residuals and their references.

### 20.1 Illustrative boundary fixtures

| Fixture | Input | Expected classification |
|---|---|---|
| `RER-B01` | Unknown patient variable, no predictive baseline | Open Knowledge |
| `RER-B02` | SQL NULL without declared missingness meaning | Missing/undetermined, not RER |
| `RER-B03` | Observed outcome differs from calibrated prediction; provenance retained | Qualified or provisional RER according to evidence checks |
| `RER-B04` | Explicit constraint contradicted by authenticated observation | RER, comparator `logical-constraint` |
| `RER-B05` | A hypothesis disagrees with another hypothesis; neither tested | Contested Open Knowledge, not automatically RER |
| `RER-B06` | Apparent deviation caused by duplicate JOIN rows | Rejected or superseded residual with error diagnosis retained |
| `RER-B07` | Baseline version changes after observation | Original residual version retained; new assessment linked |
| `RER-B08` | Mask excludes relevant observation from an exact investigation | Conformance failure or safe full-view fallback |

## 21. Knowledge Promotion and Withdrawal Contract (KPC)

Knowledge promotion is a controlled **epistemic transition**, not a structural reindexing and not a world-state mutation.

```text
Open Candidate
   | candidate test + declared criteria
   v
Validated-for-Scope  -- independent review --> Established-for-Scope
   |                                            |
   +-- failed / inconclusive --> Open / Rejected|
                                                v
                                        Revised / Withdrawn
```

**KPC-001 — Promotion gate.** An `OK → EK` transition MUST record the claim and scope, predeclared acceptance criteria where feasible, evidence, validation results, relevant negative tests, responsible evaluator, and decision version.

**KPC-002 — Scientific controls.** For predictive or explanatory claims, the evaluation SHOULD include held-out evidence, independent replication when feasible, confounding checks, multiple-testing controls, and comparison with simpler baselines. Passing a test does not prove a causal law.

**KPC-003 — Status is not certainty.** `Established-for-Scope` MUST remain revisable. Contradictory evidence SHOULD trigger reassessment rather than forced deletion or immediate unreviewed replacement.

**KPC-004 — Withdrawal and rollback.** A withdrawal MUST record reason, affected claims, downstream dependencies, and the action taken to suspend or revise dependent decisions. Epistemic rollback MUST NOT be represented as reversal of an irreversible external world event.

**KPC-005 — Candidate metric semantics.** A newly promoted perspective MUST retain its actual type: metric, pseudometric, similarity, relational, or directional. It MUST NOT gain triangle-inequality pruning or symmetry guarantees unless those properties are established under the declared domain.

**KPC-006 — Relay authority.** Multi-agent votes, repeated execution, and copied evidence are not independent validation. Promotion authority and provenance MUST be explicit.

## 22. Mask-First Investigation and Delta Separation (MIC)

A **Mask** selects an effective computational view over eligible nodes, perspectives, relationships, operations, depth, or budget; it is not a replacement for evidence, access control, or persistent storage. Mask-first is a candidate efficiency preference, not a universal requirement.

**MIC-001 — No mutation by selection.** `Mask`, `Unmask`, and `Remask` MUST NOT silently modify the underlying WE identity, source observation, established claim, or RER record.

**MIC-002 — Authorization monotonicity.** Unmasking MUST NOT expose data or operations beyond the requesting principal's authorization. Source database row/column permissions remain authoritative.

**MIC-003 — Exactness and completeness.** An investigation advertised as complete MUST use a coverage-safe mask, a proven conservative superset, or a verified full-view fallback. Approximate investigation MUST disclose its completeness/recall limits.

**MIC-004 — Evidence visibility.** A mask MUST NOT suppress mandatory provenance, contradictory evidence, or audit requirements while presenting the result as fully validated.

**MIC-005 — Invalidation.** Cached masks MUST be invalidated or revalidated when relevant schema, evidence, perspective, structural version, authorization, or policy changes.

**MIC-006 — Cost accounting.** Performance studies MUST include mask construction, maintenance, invalidation, fallback, and missed-candidate costs.

**MIC-007 — Delta typing.** Implementations MUST distinguish:
- `ActivationDelta`: task-scoped selection of computation;
- `KnowledgeDelta`: claim/evidence/hypothesis-status revision;
- `StructuralDelta`: persistent index or service topology change;
- `WorldOrSourceStateDelta`: independently recorded external or source-data change.

An `ActivationDelta` does not itself establish knowledge. A `KnowledgeDelta` does not imply a physical world change. A `StructuralDelta` must preserve applicable identity, access, and coverage invariants. CDE MAY coordinate these transitions subject to domain-specific constraints.

## 23. Additional Conformance Cases and Profiles

The existing CT-001–028 remain applicable. The following identifiers are additive and MUST NOT be interpreted as renumbering prior tests.

| ID | Scenario | Pass criterion |
|---|---|---|
| CT-029 | Unknown without baseline | Routed to Open Knowledge, not RER |
| CT-030 | SQL NULL | No automatic residual or certainty classification |
| CT-031 | Typed relational contradiction | Comparator and explicit constraint preserved |
| CT-032 | Residual baseline version update | Earlier assessment and provenance remain resolvable |
| CT-033 | Duplicate/correlated evidence | Independence not overstated |
| CT-034 | Unsupported knowledge promotion | Promotion rejected or remains provisional |
| CT-035 | Contradictory post-promotion evidence | Review/withdrawal path and dependency impact recorded |
| CT-036 | Metric candidate fails symmetry or triangle inequality | No unauthorized metric label/pruning |
| CT-037 | Masked exact investigation excludes a valid case | Detect and fallback/fail closed |
| CT-038 | Unmask attempts unauthorized SQL column | Denied; no leakage |
| CT-039 | Cached mask with changed evidence/policy | Invalidation or revalidation required |
| CT-040 | Activation-only change | No persistent structural or knowledge mutation |
| CT-041 | Residual from JOIN duplication | Error diagnosis, qualification correction, history retained |
| CT-042 | Multi-agent consensus from one underlying source | Not accepted as independent corroboration |

**Optional profiles** (extensions to Section 13):
- `ESC-Core`: ESC-001–006 plus CT-029–030.
- `RER-Qualified`: `ESC-Core` plus RQC-001–008 and CT-031–033, CT-041.
- `Knowledge-Governed`: `RER-Qualified` plus KPC-001–006 and CT-034–036, CT-042.
- `Mask-Safe-Investigation`: `Knowledge-Governed` plus MIC-001–007 and CT-037–040.

Profile names describe proposed conformance scopes; they do not certify implementation maturity.

## 24. Updated Validation Priorities and Explicit Leftovers

**P0 — Semantic fixtures:** unknown-vs-residual, baseline/comparator typing, SQL missingness, knowledge-state versioning, and qualified RER admission.

**P1 — Governance:** blinded promotion decisions, negative controls, evidence-dependence handling, demotion, rollback, and downstream notification.

**P2 — Mask experiments:** compare full-view, static mask, adaptive mask, and mask-plus-structural adaptation at matched exactness or declared recall. Report generation overhead and stale-mask failures.

**P3 — Discovery experiments:** assess independently validated discovery yield, false-discovery rates, time to diagnosis, and transfer to new perspectives or datasets.

**Unresolved:** semantic classification of structural contradictions without numerical observations; uncertainty calibration across incompatible perspectives; privacy-preserving audit; cost-effective mask coverage certification; selective attention bias; and governance for contested “established” claims. These are research questions, not solved capabilities.

### Integration references

- `docs/WE-SIO-004-Adaptive-Variable-Intelligence-Blocks.md` — Mask/Unmask/Remask and delta distinctions.
- `docs/WE-SIO-005-Metric-Leaf-Intelligence-and-SI-Operations.md` — MLIU epistemic views and operation interfaces.
- `docs/WE-SIO-007-Residual-First-Scientific-Discovery.md` — unknown/residual separation and investigation pipeline.
- `extensions/EXT-005-Mask-First-Structural-Intelligence-and-Epistemic-Separation.md` — foundational proposal.
- `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md` — SQL-facing boundary and security cases.
- `specs/SPEC-003-WE-HDT-Node-Block-and-Metric-Leaf-Contract.md` — complementary mask-safe node and block contract.

**Research status:** These additions are proposed, falsifiable contracts. They are not claims of an implemented, independently certified, or empirically validated system.
