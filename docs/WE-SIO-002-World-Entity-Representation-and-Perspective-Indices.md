# WE-SIO-002 — World Entity Representation and Perspective Indices

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Framework / Collective Learning Relay  
**Status:** Proposed architecture; definitions and contracts subject to refinement  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Companion documents:** WE-SIO-001; WE-SIO-003; WE-SIO-011; SPEC-001; SPEC-002

## Abstract

This paper develops a minimal, extensible representation of a *World Entity* (WE) for structural-intelligence operations. Starting from the motivating notation `Object[metricIdx]`, it distinguishes the entity from its representations, separates stable identity from perspective-dependent descriptions, and specifies Euclidean, metric, and relational perspective descriptors. It treats indices as access and interpretation mechanisms, not as an exhaustive ontology. A candidate hybrid differential-tree (WE-HDT) view combines efficient Euclidean localization with optional metric and relational resolution. The paper also establishes explicit uncertainty, evidence, temporal, and provenance requirements; describes representation deltas; and proposes falsifiable conformance tests. None of the proposed structures is claimed to be universally optimal or empirically validated.

## 1. Motivation and scope

A variable-size block index organizes data for efficient search. The WE-SIO research program asks whether such adaptive localization can be extended to a representation in which an entity can be located, compared, related, questioned, and re-described across perspectives. This paper answers a prerequisite question: **what exactly is indexed?**

The initial notation is deliberately compact:

```text
WE as Object[metricIdx]
```

The notation is a useful engineering entry point, but its literal reading risks conflating an entity with its measured attributes and confusing a database column with a mathematical metric. Our task is to preserve the simplicity of the entry point while establishing testable boundaries.

**In scope:** entity identity, representation, perspective descriptors, index classes, evidence and uncertainty, temporal validity, and cross-perspective mappings. **Out of scope:** a complete ontology of reality, a proof of subjectivity, an optimized physical index, or a validated scientific-discovery engine.

## 2. Three distinct levels: entity, representation, index

Let `e` denote a referent in the chosen domain, `p` a perspective, and `t` a time or validity interval. Define:

$$
R(e,p,t) = (\mathrm{id},\mathrm{schema},\mathrm{values},\mathrm{evidence},\mathrm{uncertainty},\mathrm{provenance})_{p,t}.
$$

`R` is a representation *of* `e`; it is not identical to `e`. An index `I` is a mechanism for retrieving or comparing selected parts of `R` under an explicit query contract:

$$
I_{p,q}: R(e,p,t) \longrightarrow \mathrm{KeysOrFeatures}_{p,q}.
$$

Here `q` is a task or query context. A missing or unobservable attribute must not be silently converted into a zero-valued attribute. An unindexed entity can still exist in the domain of discourse.

### 2.1 Identity is not a metric signature

Two entities may share all observed feature values without being identical; one entity may change all its observed features without ceasing to be the same referent. Accordingly:

$$
\mathrm{EntityID}(e) \ne \mathrm{FeatureSignature}(R(e,p,t)).
$$

Entity identity requires a declared resolution policy, with provenance, time and ambiguity handling. The policy may be application-specific; a globally infallible identity oracle is not assumed.

### 2.2 A minimal WE representation kernel

A candidate minimum is:

```yaml
world_entity_representation:
  entity_ref: stable-or-versioned-reference
  perspective_ref: perspective-identifier
  valid_time: interval-or-event-time
  observed_time: timestamp
  descriptors: []
  evidence_refs: []
  uncertainty: explicit-or-unknown
  provenance: source-and-transformation-chain
  schema_version: semver-or-revision-id
```

This is a semantic sketch, not a mandatory serialization format. Concrete contracts belong in `SPEC-001`.

## 3. Perspective as a first-class object

A perspective is a bounded interpretation context, not merely a column name. Define a descriptor:

$$
P=(\mathrm{scope},\mathrm{domain},\mathrm{semantics},\mathrm{operations},\mathrm{validity},\mathrm{evidencePolicy}).
$$

Two perspectives may disagree without one being immediately discarded. They may use different populations, scales, observational windows, causal assumptions, or definitions. A WE representation therefore consists of one or more *perspective views* sharing a referent where identity resolution permits:

$$
\mathcal R(e)=\{R(e,p,t):p\in\mathcal P_e\}.
$$

Views can be materialized, computed on demand, or linked by references. The model does **not** require physically duplicating the entire tree for each perspective.

### 3.1 Descriptor contract

Each descriptor should declare:

| Field | Meaning | Requirement |
|---|---|---|
| `descriptor_id` | Stable reference to the dimension or relation | Required |
| `value_domain` | Admissible values, units and null semantics | Required |
| `comparison_contract` | Equality, order, similarity, distance or relation | Required |
| `metric_properties` | Which metric axioms, if any, are satisfied | Explicit |
| `perspective_ref` | Interpretation and task context | Required |
| `time_semantics` | Validity and observation timestamps | Required |
| `uncertainty_model` | Unknown, interval, distribution or other policy | Required |
| `provenance` | Source and transformation lineage | Required |
| `access_policy` | Authorized uses and privacy constraints | Application-dependent |

A descriptor may have no distance function. This is a legitimate relational descriptor, not a defective metric descriptor.

## 4. Three index classes

### 4.1 Euclidean perspective indices

An Euclidean descriptor maps selected observations into a vector space:

$$
\phi_{E,p}(e,t)\in\mathbb R^{d_p}.
$$

A Euclidean distance is meaningful only if dimensions, units, scaling, missingness and query semantics justify it. A numeric SQL column does not automatically pass this test. Space-time coordinates, for example, require an explicit weighting or a more appropriate geometric model; physical spacetime is not generally a four-dimensional Euclidean metric.

Euclidean indices are candidates for fast block-based localization and two-phase candidate retrieval. Their efficiency depends on dimension, distribution, update frequency and workload, not solely on the index's name.

### 4.2 General metric perspective indices

A metric descriptor supplies a function `d` satisfying, on its stated domain, nonnegativity, identity of indiscernibles, symmetry and the triangle inequality:

$$
d(x,y)\ge 0,\quad d(x,y)=0\Leftrightarrow x=y,\quad d(x,y)=d(y,x),
$$

$$
d(x,z)\le d(x,y)+d(y,z).
$$

Some useful comparisons are pseudometrics, quasi-metrics, divergences or task-specific scores instead. They must be labeled accurately rather than silently treated as metrics. A metric may be non-Euclidean, and a Euclidean embedding may distort its original relationships.

### 4.3 Relational and directional perspective indices

Examples include dependency, trust, causality hypotheses, role, precedence, graph reachability and directional preference. Such relations need not be symmetric or even scalar-valued. Represent them as typed predicates or operators:

$$
\rho_p(e_i,e_j,\mathrm{context})\to\mathrm{ResultWithEvidence}.
$$

These descriptors may be indexed through graph, inverted, symbolic or learned structures; WE-HDT must not force them into a Euclidean distance.

### 4.4 Orthogonal epistemic status

Known/unknown is not an index class. Each of the three classes can be well-observed, partially observed, inferred, contested or unobserved. Thus:

$$
\mathrm{IndexClass}\ \perp\ \mathrm{EpistemicStatus}
$$

as a **modeling separation**, not a statistical independence claim.

## 5. WE-HDT as a logical access architecture

The candidate World Entity Hybrid Differential Tree (WE-HDT) has a practical default path:

```text
World Entity reference
    |
Perspective / identity resolution
    |
Euclidean candidate localization (when conformant)
    |
Metric and relational resolution (on demand)
    |
Evidence, uncertainty, residual and query result
    |
Feedback to perspective and index evolution
```

The diagram describes **query planning**, not an invariant physical storage hierarchy. Some queries begin with relational predicates, graph neighborhoods or a symbolic filter; others bypass Euclidean localization entirely. Cross-entity and cross-perspective references should be shared rather than copied into every leaf.

### 5.1 Index hierarchy versus intelligence abstraction hierarchy

These are distinct structures:

- **Index hierarchy:** determines candidate retrieval and access cost.
- **Intelligence abstraction hierarchy:** determines interpretation, hypothesis generation, reasoning and learning.

A mapping or relay interface connects them. An efficient index does not by itself establish a better explanation or a more intelligent model.

### 5.2 Two-phase search

Phase 1 retrieves candidates with a justified inexpensive predicate. Phase 2 evaluates expensive metric or relational predicates, including evidence and uncertainty. Exactness requires either a sound candidate superset or a documented approximation policy; otherwise the first phase may irretrievably discard relevant entities.

## 6. Mapping relational databases to WE

SQL provides a useful starting analogy:

| SQL concept | WE interpretation | Caveat |
|---|---|---|
| Table | Entity collection or type | A table may also encode events or relations |
| Row | Entity representation or observation | Multiple rows may describe one entity |
| Primary key | Local identity key | Not always real-world identity |
| Column | Candidate perspective descriptor | Not necessarily a metric |
| Column value | Observation or attribute value | Needs time, units and provenance |
| Foreign key / JOIN | Relation resolution | Meaning depends on schema |
| Physical SQL index | Retrieval acceleration | Not the same as semantic metric index |
| Schema migration | Representation evolution | Does not imply scientific discovery |

Example:

```sql
CREATE TABLE PatientObservation (
    observation_id BIGINT PRIMARY KEY,
    patient_ref BIGINT NOT NULL,
    observed_at TIMESTAMP NOT NULL,
    systolic_bp DOUBLE PRECISION,
    treatment_code VARCHAR(64),
    outcome_code VARCHAR(64)
);
```

Blood pressure is numeric but requires units, measurement context and temporal semantics; treatment and outcome codes are categorical; `patient_ref` is a database reference, not an infallible identity. An intelligent layer may propose new descriptors, but their acceptance must be governed by evidence and validation.

## 7. Representation changes and two kinds of delta

Distinguish changes in the referent from changes in the system's knowledge:

- **World Delta:** the represented domain entity or process actually changes.
- **Epistemic Delta:** the representation changes because evidence, interpretation or uncertainty changes.

The two can coincide, diverge, or be unidentifiable from available observations. A representation update should carry an explicit `delta_kind`, evidence references, a before/after version and a constraint check. A CDE-inspired transition contract is:

$$
R_{t+1}=\mathrm{Apply}(R_t,\Delta_t;C_t)
$$

when the applicability contract `C_t` passes. This does not require that all deltas be invertible or that repeated deltas be universally forbidden. Path-memory and cycle policies are optional, domain-specific contracts.

## 8. Residuals and missing perspectives

A residual is a recorded mismatch between an expectation and observation, or between competing structural descriptions. It should be typed:

```yaml
residual:
  residual_id: reference
  entity_refs: []
  perspective_refs: []
  expected: value-or-structure
  observed: value-or-structure
  discrepancy_contract: comparator-and-scale
  evidence_refs: []
  candidate_explanations: []
  validation_status: untested
```

Residuals may indicate missing variables, flawed metrics, sampling bias, measurement error, random variation or a genuinely new mechanism. They are prompts for inquiry, not proof of new laws. A Residual Registry may span multiple WE-HDT nodes and multiple entities.

## 9. Cross-perspective operations

The following are *candidate* WE-SIO operations:

1. `Locate(e,p,q)`: retrieve candidate references with recall/precision policy.
2. `Resolve(e,p)`: materialize or compute a perspective view.
3. `Relate(e_i,e_j,p)`: evaluate typed relationships and provenance.
4. `Compare(e_i,e_j,p,d)`: apply a conformant metric or comparator.
5. `Infer(e,p,h)`: propose a hypothesis with uncertainty and evidence.
6. `Question(e,p,r)`: formulate a testable question from a residual.
7. `Evolve(R,delta,C)`: validate and apply a representation update.

A Metric Leaf Intelligence Unit (MLIU) may hold lightweight state and invoke shared services for these operations. No assumption is made that every leaf must host a full autonomous agent.

### 9.1 Two-Ways CCC integration

A forward route may use known descriptors to locate candidate relationships and residuals. A reverse route may use residuals to propose alternative descriptors, candidate sets or queries:

$$
\mathrm{Descriptors}\to\mathrm{Candidates}\to\mathrm{Residuals}
\to\mathrm{Hypotheses}\to\mathrm{RevisedDescriptors}.
$$

Any newly proposed metric or relation must pass its own conformance and out-of-sample validation before being promoted to a trusted index. This is a proposed discovery loop, not a demonstrated performance result.

## 10. Example: conflicting perspectives on one entity

Suppose a professional's self-assessed expertise differs from an independent skills assessment. Store both as separate perspective claims with evidence, dates and measurement procedures. Do not average them without a defensible measurement model. A query can return both views, the disagreement and the outstanding validation question. A subsequent assessment may change *knowledge* without changing the person's underlying skill.

This illustrates why an entity's representation is better modeled as a set of traceable perspective views than as one definitive row of attributes.

## 11. Conformance and falsification plan

| Test | Question | Failure signal |
|---|---|---|
| ID-01 | Can two feature-identical entities remain distinct? | False identity merge |
| ID-02 | Can one entity change attributes without changing referent? | Identity tied to feature hash |
| P-01 | Are units, scales and task semantics explicit? | Invalid numeric distance |
| M-01 | Are metric axioms tested where claimed? | Triangle inequality or symmetry violation |
| R-01 | Can asymmetric relations be represented directly? | Forced symmetric metric |
| E-01 | Can unknown differ from zero and absent? | Silent value imputation |
| T-01 | Can valid time differ from observation time? | Temporal ambiguity |
| X-01 | Can perspectives disagree without forced reconciliation? | Evidence loss |
| Q-01 | Does two-phase retrieval preserve required recall? | Relevant candidates pruned |
| D-01 | Can epistemic change be recorded without world change? | Misclassified delta |
| V-01 | Can proposed new descriptors be rejected? | Unbounded schema growth |
| B-01 | Does a block index outperform baselines under specified loads? | No measured advantage |

For B-01 compare against appropriate k-d tree, R-tree, metric tree, graph or database-index baselines; report build cost, memory, update cost, latency, recall and dimensionality. The historical variable-size-block algorithm is a motivating hypothesis, not a verified universal winner.

## 12. Open questions and explicit leftovers

**OQ-001 — Ontology:** What is the minimum referent contract across physical, social, digital and abstract entities?

**OQ-002 — Identity:** How should uncertain, compositional and temporally changing identity be resolved?

**OQ-003 — Perspective:** When are two descriptors equivalent, compatible, incomparable or contradictory?

**OQ-004 — Metric:** Can a new distance or relation be generated from persistent residuals without overfitting?

**OQ-005 — Hybrid access:** Which query workloads justify Euclidean-first localization, and which do not?

**OQ-006 — Differential tree:** Which tree properties are semantic invariants versus implementation choices?

**OQ-007 — Provenance:** How can evidence from multiple observers be combined without erasing disagreements?

**OQ-008 — CDE:** Which representation deltas are admissible, and which path/cycle policies are domain-specific?

**OQ-009 — Self-reference:** What additional contracts distinguish a self-modeling entity from an ordinary represented entity?

**OQ-010 — Governance:** How should sensitive data, access boundaries and harmful inference be constrained?

These leftovers are intentional research outputs, not omissions to conceal.

## 13. Research claims and non-claims

**Claims proposed for examination:** a perspective-descriptor model can separate identity from measurements; Euclidean/metric/relational distinctions can improve interface clarity; residuals can be made traceable; and WE-HDT can serve as a modular research architecture.

**Not claimed:** that all reality can be exhaustively indexed; that WE-HDT always outperforms established databases; that residuals imply causal discovery; that a metric is available for every attribute; or that self-reference proves consciousness.

## 14. Collective-learning relay contract

Every substantive extension should provide:

```text
proposal_id
source_question_and_origin
kernel_or_extension_classification
changed_descriptors_or_operations
supporting_cases
counterexamples_and_failure_modes
conformance_tests
validation_status
version_and_provenance
unresolved_leftovers
```

Record candidate changes in `research-trace/HYPOTHESIS-REGISTRY.md`, definition changes in `DEFINITION-REGISTRY.md`, stress tests in `COUNTEREXAMPLE-REGISTRY.md`, and unresolved questions in `UNRESOLVED-RESIDUALS.md`. Preserve superseded definitions and decisions instead of silently rewriting history.

## 15. Connections and next steps

- **WE-SIO-003:** formalize the WE-HDT access and abstraction architectures.
- **WE-SIO-004:** investigate adaptive variable-intelligence blocks.
- **WE-SIO-005:** specify metric-leaf intelligence operations.
- **WE-SIO-006:** test Two-Ways CCC across metric and relational views.
- **WE-SIO-009:** connect representation evolution to CDE without overgeneralizing its constraints.
- **WE-SIO-010:** explore self-modeling entities and the boundary with SSI.
- **WE-SIO-011:** govern minimal kernels, contracts, counterexamples and definition evolution.
- **SPEC-001 / SPEC-002:** convert the semantic sketches into conformance-ready contracts.

## Conclusion

`Object[metricIdx]` is a productive starting notation precisely because it invites extension. A rigorous WE-SIO representation should nevertheless distinguish **the entity**, **its perspective-dependent representation**, and **the index that retrieves or compares it**. Euclidean, general metric and relational descriptors offer different operational affordances, while uncertainty and evidence status cut across all three. This foundation allows WE-HDT to remain an open, testable research proposal: preserve what is known, expose what is unknown, and let new cases and counterexamples refine the contracts.

---

**Research principle:** *Define the invariant, not the inventory.*  
**Relay principle:** *Preserve not only conclusions, but also their provenance, counterexamples, and explicit leftovers.*
