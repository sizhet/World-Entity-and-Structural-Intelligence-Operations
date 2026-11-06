# SPEC-001 — World Entity Identity and Perspective Descriptor Contract

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** 0.1.0 (Research Candidate)  
**Status:** Proposed / Not Yet Validated  
**Scope:** Entity identity, representation boundaries, perspective descriptors, and conformance requirements  
**Related:** WE-SIO-001, WE-SIO-002, WE-SIO-003, WE-SIO-011; SPEC-002; SPEC-003

## 1. Purpose

This specification establishes a minimal, testable interface between a **World Entity (WE)**, its identity, its time-dependent representations, and the perspectives by which it is observed, compared, or related to other entities. It does **not** assert that an entity is reducible to its index, that all perspectives define mathematical metrics, or that a particular physical index is mandatory.

The intended research contribution is a reusable contract for interoperable WE-HDT, Metric-Leaf Intelligence Unit (MLIU), Two-Ways CCC, residual discovery, and Collective Learning Relay implementations. This is a proposed research contract rather than an established interoperability standard.

## 2. Normative Language and Conformance Scope

**MUST**, **MUST NOT**, **SHOULD**, and **MAY** express requirements for implementations claiming conformance to this candidate specification. An implementation MUST declare which optional capabilities it supports. Passing the tests here establishes contract conformance, **not** empirical superiority, scientific validity, or completeness of world modeling.

Three levels are distinguished:

- **Core conformance:** stable identity reference, explicit representation boundary, typed perspective descriptor, provenance and versioning.
- **Extended conformance:** temporal observations, uncertainty, comparison contracts, relational and directional perspectives.
- **Research conformance:** residual-driven descriptor proposals, evidence-based revisions, rollback, and relay records.

## 3. Semantic Kernel

### 3.1 Entity, identity, representation, and index

The following are distinct concepts:

1. **World Entity:** the referent under discussion, which may be physical, conceptual, institutional, computational, or composite, subject to an explicit ontology and scope.
2. **Entity Identity:** a system-managed reference to a referent under an identity policy. It is not necessarily a globally unique natural-world identifier.
3. **Entity Representation:** a versioned, partial, perspective-dependent account of an entity.
4. **Perspective Descriptor:** a contract describing how a particular aspect is observed, encoded, compared, or related.
5. **Perspective Value / Observation:** an evidence-bearing value or relation obtained under a descriptor.
6. **Index:** a retrieval or acceleration structure built from representations and descriptors; it is not the entity itself.

A useful conceptual notation is:

`WERef -> {Representation(version, time, perspective observations)} -> {optional indices}`

The original `Object[metricIdx]` formulation is retained as a motivating shorthand, **not** as a claim that all indexed dimensions satisfy mathematical metric axioms.

### 3.2 Identity policy

An identity policy MUST state the referent domain, scope, authority, persistence assumptions, and rules for identity resolution, merges, splits, and deprecation. Identical attributes do not imply identical identity; changed attributes do not necessarily imply a new identity.

An identity claim MAY remain unresolved. Systems MUST NOT silently force uncertain matches into definitive merges.

## 4. Candidate Data Contracts

The following JSON-like structures are illustrative schemas. They are not a published JSON Schema; concrete implementations SHOULD publish a machine-checkable schema and specify serialization details.

### 4.1 World Entity reference

```json
{
  "entityRef": "we:example:entity-42",
  "identityPolicyId": "policy:example:v1",
  "entityType": "vehicle",
  "scope": "fleet-example",
  "identityStatus": "active",
  "createdAt": "2026-11-05T00:00:00Z",
  "version": "1",
  "provenanceRef": "prov:entity-registration-42"
}
```

**Required:** `entityRef`, `identityPolicyId`, `entityType`, `scope`, `identityStatus`, `version`, `provenanceRef`. The timestamp is SHOULD when meaningful. `entityRef` MUST be unique within the declared scope and MUST NOT be recycled for a different referent under the same identity policy. A canonicalization policy MUST specify whether two reference strings denote the same entity.

### 4.2 Perspective descriptor

```json
{
  "perspectiveId": "perspective:vehicle-position:v1",
  "name": "Observed vehicle position",
  "targetEntityTypes": ["vehicle"],
  "kind": "measurement",
  "valueDomain": "latitude-longitude",
  "unitsOrEncoding": "WGS84 degrees",
  "observationContract": "obs:geolocation:v1",
  "comparisonContract": "compare:geodesic-distance:v1",
  "comparisonProperties": {
    "symmetric": true,
    "triangleInequality": true,
    "identityOfIndiscernibles": "depends-on-domain-and-precision"
  },
  "validityScope": "surface-position-estimates",
  "uncertaintyModel": "uncertainty:radius-and-confidence:v1",
  "provenanceRequirement": "source-and-method-required",
  "version": "1.0.0",
  "lifecycle": "candidate"
}
```

Required fields: `perspectiveId`, `targetEntityTypes`, `kind`, `valueDomain`, `observationContract`, `validityScope`, `version`, `lifecycle`. `unitsOrEncoding`, `comparisonContract`, `comparisonProperties`, `uncertaintyModel`, and `provenanceRequirement` are REQUIRED whenever the declared operation depends on them.

`kind` MUST be one of the following registered categories or an explicitly namespaced extension:

| Kind | Meaning | Mathematical metric assumed? |
|---|---|---|
| `measurement` | Observed or derived attribute | No |
| `metric` | Distance with declared domain and metric axioms | Yes, within stated scope |
| `similarity` | Comparison score without general metric guarantees | No |
| `directional` | Ordered or asymmetric comparison | No |
| `relational` | Typed relationship between entities | No |
| `categorical` | Label, class, or state | No |
| `composite` | Derived from multiple descriptors | Only if separately proven |

A descriptor MUST NOT claim `kind: metric` without identifying the domain and stating how the metric axioms are checked or justified. A descriptor MAY carry a metric hypothesis without certifying it; that hypothesis MUST be marked as such.

### 4.3 Perspective observation

```json
{
  "observationId": "obs:vehicle-42:position:1001",
  "entityRef": "we:example:entity-42",
  "perspectiveId": "perspective:vehicle-position:v1",
  "value": {"lat": 37.87, "lon": -122.27},
  "observedAt": "2026-11-05T12:00:00Z",
  "recordedAt": "2026-11-05T12:00:03Z",
  "uncertainty": {"radiusMeters": 12},
  "sourceRef": "source:gps-sample-1001",
  "methodRef": "method:gps-processing-v2",
  "representationVersion": "rep:vehicle-42:v8",
  "status": "observed"
}
```

An observation MUST identify the entity, descriptor, evidence source, and representation version. `observedAt` and `recordedAt` SHOULD be separate when event time differs from ingestion time. A missing value MUST be represented as missing/unknown, not silently converted to zero. Estimated, imputed, inferred, and observed values MUST be distinguishable.

### 4.4 Identity resolution assertion

```json
{
  "assertionId": "identity-claim:101",
  "leftEntityRef": "we:source-a:17",
  "rightEntityRef": "we:source-b:93",
  "relation": "possible-same-referent",
  "confidence": 0.72,
  "evidenceRefs": ["evidence:match-101"],
  "identityPolicyId": "policy:cross-source:v1",
  "decisionStatus": "unresolved",
  "version": "1"
}
```

An assertion is not a merge operation. The system MUST preserve both references until an authorized identity decision is recorded. `confidence` MUST NOT be interpreted as calibrated probability unless calibration has been validated.

## 5. Required Invariants

**I-001 — Identity/representation separation.** Updating a perspective value MUST NOT silently change `entityRef`.

**I-002 — Identity/index separation.** Rebuilding, changing, or deleting an index MUST NOT by itself delete or merge entities.

**I-003 — Descriptor traceability.** Every stored perspective observation MUST resolve to a descriptor identifier and version, or be explicitly marked as legacy/unresolved.

**I-004 — Type discipline.** Metric, similarity, directional, relational, and categorical operations MUST NOT be treated as interchangeable without an explicit adapter contract.

**I-005 — Scope discipline.** Comparison semantics MUST specify the domain, units/encoding, and applicable conditions; out-of-scope operations MUST return an explicit unsupported or indeterminate result.

**I-006 — Uncertainty preservation.** Unknown, missing, low-confidence, and conflicting observations MUST remain distinguishable.

**I-007 — Evidence provenance.** Claims promoted to accepted observations MUST retain source/method provenance or an explicit exception record.

**I-008 — Temporal semantics.** If temporal data are supported, observation time and knowledge/recording time MUST NOT be conflated.

**I-009 — Versioned change.** Descriptor revisions that alter semantics MUST create a new version; historical observations MUST remain interpretable against their original descriptor.

**I-010 — Explicit unresolved identity.** Ambiguous identity mappings MUST remain unresolved unless an authorized policy permits a decision.

**I-011 — Representation incompleteness.** An absent perspective MUST NOT imply a negative observation or nonexistence of the entity.

**I-012 — Controlled evolution.** A proposed new perspective MUST NOT automatically become an accepted descriptor solely because it improves training-set fit.

## 6. Operations and Failure Semantics

| Operation | Input | Output | Required behavior |
|---|---|---|---|
| `registerEntity` | identity claim, policy, provenance | entity reference | Reject collision or unresolved policy |
| `resolveEntity` | reference, scope | resolved / ambiguous / missing | Do not silently choose ambiguous referent |
| `registerPerspective` | descriptor, validation evidence | candidate/accepted/rejected | Validate fields and declared semantics |
| `recordObservation` | entity, descriptor, value, evidence | versioned observation | Check descriptor compatibility |
| `compare` | two values, descriptor, scope | result + applicability + uncertainty | Do not invent metric guarantees |
| `relate` | entity refs, relational descriptor | typed relation assertion | Preserve direction and provenance |
| `reviseDescriptor` | old version, proposed version, rationale | versioned transition | Preserve history and regression evidence |
| `proposeIdentityMerge` | references, evidence, policy | unresolved/approved/rejected proposal | Separate proposal from mutation |
| `buildIndex` | representations, descriptor, policy | index handle + version | Declare completeness and false-negative risks |

Failure states SHOULD include `UNKNOWN_ENTITY`, `AMBIGUOUS_IDENTITY`, `UNKNOWN_PERSPECTIVE`, `TYPE_MISMATCH`, `OUT_OF_SCOPE`, `INSUFFICIENT_EVIDENCE`, `UNSUPPORTED_OPERATION`, `STALE_VERSION`, and `CONFLICTING_OBSERVATIONS`. A system MUST NOT disguise these as successful zero-valued results.

## 7. Index and Retrieval Boundary

An index MAY use Euclidean partitioning, metric search, graph traversal, relational joins, or a hybrid plan. Euclidean-first is a **query-planning heuristic**, not a mandatory WE ontology. Implementations MUST state whether their retrieval stage is exact, approximate, or candidate-generating. Approximate retrieval MUST report its completeness limitations where measurable.

Physical index topology MUST NOT be conflated with intelligence abstraction topology. A Metric Leaf Intelligence Unit may be a logical service linked to a node, block, or entity, rather than a literal physical tree leaf.

## 8. Descriptor Lifecycle and Definition Evolution

Candidate lifecycle:

`proposed -> reviewed -> validated -> accepted -> deprecated`

Rejection and suspension branches are also permitted. A revision MUST record:

- prior descriptor version and proposed semantic delta;
- motivating evidence, residuals, or counterexamples;
- affected observations, indices, and downstream consumers;
- validation results and known failure cases;
- rollback or migration policy; and
- unresolved questions for Collective Learning Relay.

A revision MAY narrow, split, merge, or retire a perspective. The Definition Evolution Loop MUST preserve prior definitions and counterexamples, not overwrite their history.

## 9. Conformance Test Matrix

| ID | Test | Pass criterion |
|---|---|---|
| CT-001 | Change a measured value | Entity reference remains unchanged |
| CT-002 | Rebuild a physical index | Identity and observation records remain intact |
| CT-003 | Submit duplicate identity reference for different referent | Rejected or explicitly adjudicated |
| CT-004 | Compare asymmetric relation as a metric | Rejected unless validated adapter exists |
| CT-005 | Use metric outside declared domain | Explicit out-of-scope result |
| CT-006 | Record missing observation | Missing remains distinct from zero |
| CT-007 | Record conflicting observations | Both remain inspectable with provenance |
| CT-008 | Modify descriptor semantics | New version required; old version resolvable |
| CT-009 | Resolve ambiguous cross-source identity | Returns ambiguity, not silent merge |
| CT-010 | Store inferred value | Labeled inferred with method and evidence |
| CT-011 | Record event after delayed ingestion | Event and recording times retained separately |
| CT-012 | Add a candidate perspective | Not accepted without declared validation path |
| CT-013 | Build approximate retrieval index | Approximation/completeness status disclosed |
| CT-014 | Remove a perspective index | Does not imply entity or observation deletion |
| CT-015 | Propose descriptor split after counterexample | Prior definition, reason, and regression test retained |
| CT-016 | Query absent perspective | Unknown/unsupported rather than false or zero |

**Testing protocol:** Each test SHOULD specify fixture data, expected outputs, policy version, and a reproducible implementation environment. A conformance report MUST disclose unimplemented optional operations and failed tests; it MUST NOT claim empirical validation based only on contract tests.

## 10. Illustrative Edge Cases

### 10.1 Two vehicles with identical positions

Coincident positions do not establish identity. Both entities retain distinct references under a fleet identity policy.

### 10.2 One patient, multiple conflicting records

A cross-system match is a hypothesis until identity evidence is sufficient. Clinical interpretations must not infer causal relationships from record linkage alone.

### 10.3 Directional reputation score

A score `A -> B` need not equal `B -> A`; therefore it is a directional perspective, not automatically a mathematical metric.

### 10.4 Chess position and move history

Two equal board arrangements may differ in legal state or strategic interpretation due to turn, castling rights, repetition history, or other rule-dependent context. Entity identity, state representation, and search equivalence require separate contracts.

### 10.5 Novel scientific measurement

A residual may motivate a new descriptor, but the candidate must be checked for confounding, leakage, noise, independent reproducibility, and operational utility before acceptance.

## 11. Security, Privacy, and Governance

Perspective descriptors may expose sensitive observations. Implementations SHOULD define authorization, purpose limitation, data minimization, retention, and audit policies. Entity resolution can cause privacy harm if weak evidence is promoted to definitive linkage. Provenance references may themselves be sensitive and require access control. Relay exports SHOULD support redaction without fabricating evidence or erasing the existence of unresolved constraints.

## 12. Research Hypotheses and Validation Roadmap

**H-001:** Explicit separation of entity identity, representation, and index reduces identity corruption during index evolution relative to an implementation that conflates them.

**H-002:** Typed perspective descriptors reduce invalid cross-perspective comparisons and improve failure explainability.

**H-003:** Versioned descriptor evolution improves reproducibility of residual-driven discovery.

**H-004:** Explicit ambiguity and uncertainty handling improves calibration and auditability of entity resolution.

**H-005:** Contract-first WE-HDT integration reduces cross-module semantic regressions, at a measurable implementation cost.

Suggested validation: (1) synthetic identity and descriptor fixtures; (2) contract-based reference implementation; (3) comparative error and overhead measurements; (4) independent cross-domain stress tests; (5) publish negative results and remaining gaps. No performance or discovery benefit is established by this document.

## 13. Open Questions and Explicit Leftovers

1. Which identity policies work for fluid, composite, or socially constructed entities?
2. What is the minimal interoperability descriptor that remains operationally meaningful?
3. How should equivalence, similarity, and identity evidence interact without collapsing into one score?
4. Can temporal and contextual scope be normalized across heterogeneous perspectives?
5. How can approximate retrieval guarantees be expressed consistently across index families?
6. What evidence suffices to promote a newly discovered perspective to accepted status?
7. How should access controls propagate across derived and relational perspectives?
8. When should a descriptor be split rather than expanded?
9. What is the measurable overhead of preserving full research provenance?
10. How can Collective Learning relay records remain portable without pretending that all ontologies agree?

## 14. Collective Learning Relay Record

Every research contribution based on this specification SHOULD include:

```yaml
relay_id: we-sio-spec-001-example
source_spec: SPEC-001
source_version: 0.1.0
claim_type: hypothesis | definition | counterexample | experiment | revision
entity_scope: explicit
perspective_ids: []
evidence_refs: []
method_or_test_ref: null
observed_result: null
limitations: []
counterexamples: []
proposed_definition_delta: null
open_residuals: []
next_validation_step: null
```

The relay record MUST distinguish observation from inference and proposal from acceptance. A negative or inconclusive result is a valid contribution.

## 15. Related Documents and Planned Interfaces

- **WE-SIO-001:** origin and research motivation.
- **WE-SIO-002:** world entity representation and perspective indices.
- **WE-SIO-003:** WE-HDT architecture and indexing boundaries.
- **WE-SIO-005:** MLIU and SI operation contracts.
- **WE-SIO-008:** metric discovery and perspective evolution.
- **WE-SIO-009:** World/Knowledge/Structural Delta and CDE.
- **WE-SIO-011:** minimal kernel and definition evolution methodology.
- **SPEC-002:** mathematical and operational index conformance.
- **SPEC-003:** node, block, and Metric Leaf contracts.
- **SPEC-006:** definition evolution and research relay contracts.

## 16. Conclusion

WE-SIO requires a disciplined boundary between **what exists**, **how it is identified**, **what is known about it**, **how it is observed or compared**, and **how that knowledge is indexed**. This candidate specification defines those boundaries without claiming to exhaust the possible forms of world entities or perspectives.

**Define the invariant, not the inventory. Preserve the evidence, the counterexample, and the next question.**

---

*WE-SIO v0.1.0 — Research specification. Proposed for discussion, conformance testing, and Collective Learning Relay; not an established standard.*
