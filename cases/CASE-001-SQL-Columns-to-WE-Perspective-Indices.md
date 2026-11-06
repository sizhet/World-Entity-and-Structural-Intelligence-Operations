# CASE-001 — From SQL Columns to World Entity Perspective Indices

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 (research case; not an implementation standard)  
**Status:** Proposed case study / conformance and boundary analysis  
**Date:** 2026-11-05  
**Related:** WE-SIO-001, WE-SIO-002, WE-SIO-003, WE-SIO-008, WE-SIO-011; SPEC-001, SPEC-002, SPEC-003, SPEC-005, SPEC-006

## Abstract

A relational database offers a useful, familiar stress test for the proposed World Entity (WE) representation. A table row can describe an entity, columns can supply candidate perspectives, keys can support identity resolution, and indexes can accelerate queries. None of these correspondences is unconditional: a row may describe an event rather than an entity; a primary key is a database-local identifier, not necessarily a real-world identity; a numeric column is not automatically a metric; and an SQL index is a physical access path rather than a semantic perspective. This case specifies a disciplined mapping from relational records to WE perspective descriptors, demonstrates query and update paths, identifies failure modes, and proposes measurable conformance tests. The objective is interoperability and testability—not replacement of SQL systems or a claim that WE-SIO has established superior retrieval performance.

## 1. Research question and scope

**Question:** Under which contracts can a relational schema and its data be represented as WE identities, observations, perspectives, and optional WE-HDT access structures without changing the source database's meaning?

The case examines:

1. Identity resolution across rows, tables, and time.
2. The classification of SQL attributes as measurements, mathematical metrics, similarities, or relational/directional perspectives.
3. Preservation of NULL, units, timestamps, provenance, and cardinality.
4. Candidate localization and second-stage semantic resolution.
5. Residual-driven discovery of useful new perspectives under validation controls.
6. Synchronization of SQL changes with WE representation and index versions.

It does **not** assume that all SQL columns are metrics, that every row denotes a unique real-world object, or that a new index is justified for every perspective.

## 2. Relational-to-WE mapping: a conditional correspondence

| Relational construct | Candidate WE interpretation | Necessary qualification |
|---|---|---|
| Table | Entity type, collection, or observation/event collection | Some tables represent associations, logs, or aggregates |
| Row | Entity record or observation about an entity | A row is not always the entity itself |
| Primary key | Source-scoped record identifier | Not proof of cross-source entity identity |
| Foreign key | Typed reference / relational edge | Relationship semantics and direction require explicit description |
| Column | Candidate perspective descriptor | Column type alone does not determine metric semantics |
| Cell value | Perspective observation or attribute value | Preserve NULL, time, units, and provenance |
| SQL index | Physical query acceleration | Not synonymous with a perspective or semantic index |
| JOIN | Relational traversal or entity-resolution evidence | Join equality is not necessarily real-world identity |
| WHERE | Selection predicate / candidate filtering | SQL three-valued logic must be preserved |
| UPDATE | Source-record change and possible knowledge delta | Does not necessarily mean the world changed |
| Materialized view | Derived representation | Must retain lineage and refresh semantics |

**Invariant:** `World Entity ≠ Entity Identity ≠ Representation ≠ Perspective ≠ Index`.

## 3. Worked example: a small clinical-like dataset

The following synthetic data illustrate schema mapping only; no clinical efficacy claim is implied.

```sql
CREATE TABLE person (
  person_id BIGINT PRIMARY KEY,
  birth_year INTEGER,
  region_code TEXT
);

CREATE TABLE encounter (
  encounter_id BIGINT PRIMARY KEY,
  person_id BIGINT NOT NULL REFERENCES person(person_id),
  observed_at TIMESTAMP NOT NULL,
  systolic_bp_mmHg NUMERIC,
  treatment_code TEXT,
  outcome_score NUMERIC
);

CREATE INDEX encounter_person_time_idx
  ON encounter(person_id, observed_at);
```

Candidate representations:

- `person.person_id` identifies a **source record**; a WE identity may be linked to it by an explicit mapping and resolution policy.
- `encounter.encounter_id` identifies an **encounter event**, not another person.
- `birth_year` is a measured attribute with uncertainty and potential correction; it is not itself a distance function.
- `systolic_bp_mmHg` is a numeric observation with a unit and observation time. An application may define a distance on such observations, but must state its scale and validity domain.
- `treatment_code` is categorical; equality, ontology distance, or learned similarity would be distinct contracts.
- `outcome_score` is meaningful only with its scale, measurement procedure, and direction of interpretation.
- `encounter.person_id` expresses a relationship to a source person record, subject to referential integrity and entity-resolution policies.

### 3.1 Candidate WE record

```json
{
  "we_id": "we:person:000042",
  "entity_type": "Person",
  "identity_links": [
    {
      "source": "sql:person",
      "source_record_key": "42",
      "resolution_status": "source-linked",
      "policy_version": "identity-v1"
    }
  ],
  "representation_version": "we-repr-v3",
  "perspective_refs": [
    "perspective:birth-year:v1",
    "perspective:region:v1",
    "perspective:systolic-bp:v2",
    "perspective:treatment-history:v1"
  ]
}
```

This is an illustrative envelope, not a normative serialization. The WE identity is not derived by asserting that the primary key uniquely identifies the person across all data sources.

### 3.2 Candidate perspective descriptor

```json
{
  "perspective_id": "perspective:systolic-bp:v2",
  "subject_type": "Person",
  "value_type": "decimal",
  "semantic_class": "measurement",
  "unit": "mmHg",
  "observation_granularity": "encounter",
  "time_policy": "observed_at",
  "null_policy": "unknown-not-zero",
  "comparison_contract": {
    "kind": "absolute-difference",
    "domain": "finite-valid-measurements",
    "distance_unit": "mmHg",
    "metric_claim": "conditional-on-domain"
  },
  "provenance_requirement": "source-table-key-and-version",
  "descriptor_version": "v2"
}
```

A numeric absolute difference can be a metric over a suitable domain of numeric values; that mathematical property does not make the measure a clinically appropriate similarity criterion. The domain and application thresholds require separate validation.

## 4. Classification rules for perspective indices

### 4.1 Euclidean perspective

A column or derived vector may participate in a Euclidean perspective if the system specifies a coordinate domain, dimension, units or normalization, missing-value handling, and a valid distance function. Numeric storage type alone is insufficient. For example, latitude/longitude in degrees cannot simply be treated as planar meters over arbitrary global ranges.

### 4.2 General metric perspective

A comparison `d(x,y)` may be advertised as a mathematical metric only after checking, on its declared domain:

1. Non-negativity.
2. Identity of indiscernibles (relative to the represented objects).
3. Symmetry.
4. Triangle inequality.

Some distances are pseudometrics or only approximate; the descriptor must not silently claim stronger properties. Metric-based pruning is permitted only when its preconditions hold.

### 4.3 Relational or directional perspective

Foreign-key links, temporal precedence, ownership, influence, treatment exposure, and other typed relations may be asymmetric, conditional, or many-to-many. They must not be treated as symmetric distances without an explicit justified transformation.

### 4.4 Derived and learned perspectives

Computed columns, embeddings, aggregates, and learned comparisons require derivation lineage, training/version information where applicable, leakage checks, and a policy for invalidation when inputs change. A new derived descriptor is a **candidate** until validated.

## 5. Identity and cardinality stress tests

### 5.1 One row, one entity: sometimes valid

A canonical `person` table may be a reasonable entity collection when source keys are stable. Even then, duplicate records and mistaken merges remain possible.

### 5.2 One entity, many rows

Multiple encounters, addresses, or sensor measurements may represent a single entity across time. A WE must support time-indexed observations rather than collapsing these rows into contradictory timeless attributes.

### 5.3 One row, many entities

A transaction row may reference payer, payee, intermediary, and an event. Treating the transaction as the sole world entity loses the participating identities and relations.

### 5.4 Unknown or contested identity

Two records that share an email address, name, or other signature are not necessarily the same entity. Identity hypotheses should carry evidence, confidence or uncertainty, and reversible decisions.

**Counterexample CE-SQL-001:** `JOIN person USING (name)` can produce false identity merges; equality of an attribute is not a sufficient identity contract.

## 6. Query plan: SQL baseline and optional WE-HDT

Consider a request: *Find encounters in a time window whose measurements are similar under a specified comparison, then explain any unexpected outcome pattern.*

**SQL baseline:** filter by time and join source records; calculate comparison scores with SQL or an external analytic component; preserve the complete eligible cohort under the query's declared semantics.

**WE-HDT candidate pipeline:**

```text
Request + Perspective Contracts
          |
          v
Candidate Localization (SQL / Euclidean / Metric / Graph)
          |
          v
Candidate Set + Completeness/Approximation Declaration
          |
          v
Perspective Resolution (MLIU / Two-Ways CCC)
          |
          v
Answers + Evidence + Uncertainty + Residuals
          |
          v
Optional Reverse Discovery / Candidate New Perspective
          |
          v
Validation -> Versioned Promotion or Rejection
```

The first stage may use existing SQL indexes; WE-HDT need not duplicate them. A two-stage query is not globally exact if its candidate stage silently drops valid matches. Each result must declare whether the guarantee is exact, bounded-approximate, or heuristic.

### 6.1 Illustrative baseline query

```sql
SELECT e.encounter_id, e.person_id, e.observed_at,
       e.systolic_bp_mmHg, e.outcome_score
FROM encounter AS e
WHERE e.observed_at >= TIMESTAMP '2026-01-01 00:00:00'
  AND e.observed_at <  TIMESTAMP '2026-02-01 00:00:00'
  AND e.systolic_bp_mmHg IS NOT NULL;
```

This query is a reproducible selection baseline, not a causal analysis or clinical recommendation. A WE-HDT implementation should compare candidate coverage against the exact SQL predicate on a controlled dataset.

## 7. Delta and synchronization semantics

A source `UPDATE` can represent several distinct phenomena:

| Source event | Candidate classification | Required handling |
|---|---|---|
| New encounter arrives | Observation / knowledge delta | Append observation; maintain event time |
| Typographical correction | Knowledge/representation delta | Preserve correction lineage; avoid asserting world change |
| Patient changes region | Potential world delta, observed through a source update | Distinguish effective time from recording time |
| Column renamed | Schema/structural delta | Migrate descriptors or aliases; preserve meaning |
| Comparison function revised | Perspective/epistemic structural delta | Version contract; rebuild affected index if necessary |
| Identity merge reversed | Identity-resolution delta | Reconcile references and downstream derived results |

Use a source change log or equivalent capture mechanism with idempotency keys, ordering rules, and replay semantics. A database rollback does not undo the real-world event that a record described.

### 7.1 Minimal change envelope

```json
{
  "event_id": "change:encounter:991:v4",
  "source_ref": "sql:encounter:991",
  "source_version": "v4",
  "effective_time": "2026-01-17T09:00:00Z",
  "recorded_time": "2026-01-18T12:00:00Z",
  "change_kind": "observation-correction",
  "affected_perspectives": ["perspective:systolic-bp:v2"],
  "lineage_ref": "source-change-log:991:4"
}
```

## 8. Residual-first discovery: a controlled extension

Suppose an outcome model consistently mispredicts a subgroup. WE-SIO may record residuals, cluster them across perspectives, and propose a new conditional descriptor (for example, an interaction between treatment history and measurement time). This is a **hypothesis-generation workflow**, not evidence of a new causal mechanism.

Proposed stages:

1. Record expectation, observation, residual, population definition, and model version.
2. Rule out data-entry errors, time misalignment, unit mismatch, leakage, and confounding where possible.
3. Generate candidate relations or perspectives with explicit assumptions.
4. Test on held-out or independently collected data with prespecified metrics.
5. Compare against SQL-only and conventional analytic baselines.
6. Promote a perspective only with a documented decision and rollback plan.

For health-related data, privacy protections, access controls, and qualified domain review are prerequisites to real-world deployment.

## 9. Counterexample registry for this case

| ID | Tempting assumption | Counterexample / correction |
|---|---|---|
| CE-SQL-001 | Shared column value proves identity | Two people may share a name |
| CE-SQL-002 | Every numeric column defines Euclidean distance | Numeric identifiers have no meaningful geometric distance |
| CE-SQL-003 | Every comparison is a metric | Directed influence violates symmetry |
| CE-SQL-004 | NULL equals zero or absence | Unknown and measured zero differ |
| CE-SQL-005 | SQL index equals semantic perspective | B-tree access path can index a nonmetric category |
| CE-SQL-006 | UPDATE proves physical-world change | Correcting a typo changes knowledge only |
| CE-SQL-007 | JOIN proves same entity | Foreign keys often express relationships, not identity |
| CE-SQL-008 | Candidate refinement guarantees exact results | Candidate stage can omit true matches |
| CE-SQL-009 | Correlated residual proves a causal relation | Confounding and leakage can create spurious patterns |
| CE-SQL-010 | One row maps to one WE | Event and association rows have different semantics |

Each counterexample should link to the research-trace registry when implemented. Counterexamples are evidence for definition refinement, not merely exceptions to hide.

## 10. Conformance checks

| Test ID | Requirement | Observable pass condition |
|---|---|---|
| SQL-WE-001 | Stable source linkage | Each mapped record has a resolvable source reference |
| SQL-WE-002 | Identity separation | Source PK is not asserted as universal identity without policy |
| SQL-WE-003 | Entity/event distinction | Encounter rows map to events or observations, not extra people |
| SQL-WE-004 | NULL semantics | Unknown is not silently mapped to zero |
| SQL-WE-005 | Unit preservation | Measurement unit is retained or explicitly converted |
| SQL-WE-006 | Time semantics | Effective and recorded times remain distinguishable |
| SQL-WE-007 | Metric honesty | Claimed metric properties pass property tests on declared domain |
| SQL-WE-008 | Directionality | Relation reversal is not assumed without contract |
| SQL-WE-009 | Exact-query coverage | Exact mode reproduces baseline eligible results |
| SQL-WE-010 | Approximation declaration | Approximate mode exposes recall/guarantee limits |
| SQL-WE-011 | Provenance | Derived result resolves to source and transformation version |
| SQL-WE-012 | Schema evolution | Renames/type changes trigger compatible migration or rejection |
| SQL-WE-013 | Identity revision | Split/merge corrections propagate to dependent references |
| SQL-WE-014 | Replay idempotency | Duplicate change events do not duplicate observations |
| SQL-WE-015 | Candidate validation | New perspective is not promoted without evidence and decision |
| SQL-WE-016 | Privacy boundary | Unauthorized source attributes are not exposed via WE layer |

These are proposed tests. No test execution or empirical validation is claimed by this document.

## 11. Comparative experiment design

**Baselines:** indexed SQL queries; SQL plus conventional feature engineering; optionally a graph index or vector/metric index where the workload warrants it.

**WE-SIO candidates:** SQL-backed WE descriptors; SQL plus WE-HDT routing; SQL plus MLIU/Two-Ways CCC and residual registry.

**Workloads:** point/range selection, joins, multi-perspective filtering, time-varying observations, schema changes, entity-resolution corrections, and held-out residual discovery.

**Measures:** exact-match recall and precision; latency percentiles; memory/storage overhead; index update cost; trace completeness; number and quality of independently validated discoveries; false-discovery rate; operator review time.

**Controls:** identical source snapshots, declared resource budgets, comparable query semantics, repeated trials, and separated discovery/evaluation datasets. Report negative findings and cases where plain SQL is simpler or faster.

## 12. Falsifiable hypotheses

- **H-SQL-001 — Semantic interoperability:** explicit WE descriptors reduce schema-to-model ambiguity on a preregistered mapping task compared with undocumented ad hoc mappings.
- **H-SQL-002 — Hybrid retrieval:** for selected multi-perspective workloads, WE-HDT routing improves a stated latency/recall tradeoff over a specified SQL baseline; the hypothesis fails if overhead dominates.
- **H-SQL-003 — Traceability:** WE-linked evidence lineage reduces time to reconstruct the source of a derived result.
- **H-SQL-004 — Controlled discovery:** residual-driven perspective proposals improve held-out predictive or explanatory measures beyond matched feature-engineering baselines without unacceptable false discoveries.
- **H-SQL-005 — Definition stress testing:** systematic counterexample capture detects more invalid identity/metric assumptions than a baseline review process.

Each hypothesis requires dataset definitions, thresholds, power considerations where appropriate, and a prespecified analysis plan before testing.

## 13. Minimal-kernel and definition-evolution implications

This case reinforces a minimal WE-SIO kernel: identifiable referents under explicit scope; typed perspectives; provenance-aware observations; declared comparison and relation semantics; and versioned structural operations. It does **not** establish that all world entities fit relational rows, or that all perspectives are indexed.

The Definition Evolution Loop should record:

```text
Initial correspondence hypothesis
  -> SQL schema and workload application
  -> counterexample (e.g., event row or numeric identifier)
  -> kernel/contract refinement
  -> regression test
  -> versioned research relay
```

Definitions may be narrowed or split; broadening is not automatically progress.

## 14. Collective Learning relay package

A reproducible follow-on contribution should include:

```yaml
relay_id: WE-SIO-CASE-001-EXPERIMENT-001
question: "Does WE-HDT add value over indexed SQL for this workload?"
source_schema_version: "..."
source_snapshot_or_synthetic_generator: "..."
identity_resolution_policy: "..."
perspective_descriptor_versions: ["..."]
query_semantics_and_guarantee: "exact-or-declared-approximate"
baselines: ["indexed-SQL"]
measurements: ["latency", "recall", "storage", "trace-completeness"]
counterexamples: ["CE-SQL-001", "CE-SQL-008"]
limitations: ["..."]
next_questions: ["..."]
```

Do not publish sensitive records or identifying information in a relay. The provenance record should remain meaningful even if source data cannot be shared.

## 15. Open questions and explicit leftovers

1. What is the smallest useful identity policy for cross-database WE mapping?
2. When is a perspective an attribute, a relation, a computed view, or a separate entity?
3. Which source semantics can be inferred automatically, and which require human/domain approval?
4. Can WE-HDT improve real workloads without duplicating SQL's mature indexing functions?
5. How should competing identity resolutions be represented and rolled back?
6. What is the appropriate interface for SQL three-valued logic and open-world uncertainty?
7. Which learned comparisons admit safe pruning, and when must search be heuristic?
8. How can residual discovery be audited for multiple testing, leakage, and confounding?
9. How should schema migrations preserve older research traces and query reproducibility?
10. When should a failed WE abstraction be removed in favor of the simpler relational model?

## 16. Conclusions

Relational databases are an informative boundary test for WE-SIO precisely because their semantics and performance are well developed. The defensible mapping is **conditional and contract-based**: tables and rows may describe entities or observations; columns may become perspective descriptors; keys and joins provide source-scoped identity and relational evidence; and indexes remain physical acceleration mechanisms. WE-SIO's proposed additional value lies in explicit multi-perspective semantics, residual-aware research operations, and traceable evolution—not in renaming existing SQL constructs. Whether that additional layer yields practical benefit is an empirical question.

---

### Suggested repository placement

`cases/CASE-001-SQL-Columns-to-WE-Perspective-Indices.md`

### Suggested figure references

- `Fig-002-From-Variable-Size-Blocks-to-World-Entity.png` — motivation and evolution.
- `Fig-003-WE-Hybrid-Differential-Tree.png` — optional hybrid routing.
- `Fig-009-Definition-Evolution-Loop.png` — counterexample-driven revision.

### Research status notice

This is a **conceptual specification and test design**. Examples are synthetic; hypotheses, performance gains, and scientific discovery capabilities remain unvalidated pending implementation and controlled experiments.
