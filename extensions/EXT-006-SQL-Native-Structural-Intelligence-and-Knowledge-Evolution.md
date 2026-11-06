# EXT-006 — SQL-Native Structural Intelligence and Knowledge Evolution

**WE-SIO v0.1.0 — Research Extension**  
**Subtitle:** *From Relational Schemas and Metric Indices to Mask-First SQL Intelligence and Open-Ended Knowledge Discovery*  
**Authors:** Sizhe Tan & GPT-Obot  
**Date:** 2026-11-05  
**Status:** Hypothesis-driven architectural proposal; not an implemented or empirically validated framework  
**License:** Apache-2.0

## Abstract

This extension investigates whether **World Entity and Structural Intelligence Operations (WE-SIO)** can provide a **SQL-native structural-intelligence layer** over existing relational database systems. The proposal maps relational schema objects, records, constraints, queries, and change events to typed World Entity (WE) representations and perspective-aware operations, while explicitly rejecting simplistic equivalences such as *row = entity*, *column = metric*, or *SQL index = semantic index*. It combines **Mask-First Structural Intelligence (MFSI)** for selective schema and operation activation, **epistemic separation** of established knowledge, open questions, and residual evidence, and **Constrained Delta Evolution (CDE)** for controlled changes in knowledge and structure. The aim is not another text-to-SQL interface or a replacement database engine, but a testable architecture in which relational data can support evidence-grounded retrieval, diagnosis, hypothesis generation, validation, and versioned knowledge promotion. We define mappings, invariants, operational contracts, counterexamples, falsifiable hypotheses, a reference pipeline, and a phased validation roadmap. No accuracy, efficiency, or scientific-discovery advantage is claimed without comparative experiments.

## 1. Motivation: SQL as a structural-intelligence testbed

Relational databases offer mature, widely deployed mechanisms for schema declarations, typed values, keys, referential integrity, joins, transactions, access controls, indexing, and query optimization. These are unusually valuable substrates for testing a structural-intelligence architecture: the underlying operations have established semantics, the data can be large and heterogeneous, and many outputs can be checked against executable SQL.

Existing database AI systems already support natural-language query generation, semantic layers, catalog retrieval, query validation, and agent-assisted analytics. **WE-SIO must therefore demonstrate a distinct contribution**, not merely relabel these capabilities. The proposed research distinction is the integration of:

1. **Typed relational-to-WE mapping** with identity, temporal, and provenance contracts.
2. **Task-conditioned computational masks** over schemas, columns, relationships, perspectives, and operations.
3. **Knowledge-state separation** between evidence-qualified assertions, unresolved questions, and qualified residuals.
4. **Bidirectional inquiry**, where queries retrieve known results while discrepancies and unanswered questions generate candidate tests.
5. **Versioned evolution**, where activation, epistemic, structural, and external-world changes remain distinguishable.
6. **Reusable relay artifacts**, including validated mappings, mask policies, test cases, and evidence trails.

**Research question:** Under what conditions can a SQL-backed WE-SIO layer improve correctness, efficiency, explainability, or knowledge-discovery workflows over strong database-AI baselines without violating SQL semantics, governance, or evidence standards?

## 2. Scope and non-goals

### In scope

- Read-oriented SQL database discovery and metadata introspection under authorized access.
- Explicit mapping of tables, views, columns, keys, relationships, constraints, and source events into WE descriptors.
- Schema/column/relationship localization and query-planning assistance.
- Evidence-backed, versioned knowledge claims and unresolved hypotheses.
- Residual qualification and controlled generation of candidate perspectives and tests.
- Mask policies, evaluation traces, and collective-learning transfer under compatibility contracts.
- Optional, governed structural extensions to WE-SIO's *derived* representation.

### Out of scope for the initial release

- Replacing SQL execution engines, query optimizers, transaction managers, or security systems.
- Autonomous production writes, schema migrations, or data correction.
- Assuming all tables model real-world entities or all columns are metrics.
- Inferring causal laws directly from SQL correlations.
- Claiming that generated hypotheses are validated discoveries.
- Claiming that WE-SIO is already a complete SQL AI product.

## 3. Relational semantics and WE mapping

A mapping is **conditional and typed**, not a one-to-one ontology. Every mapped element should retain its original SQL meaning and source location.

| SQL construct | Candidate WE-SIO interpretation | Boundary / contract |
|---|---|---|
| Database / schema | Domain namespace and source boundary | Schema is not automatically a coherent ontology |
| Base table | Entity collection, event collection, or association relation | Classify table role; do not assume entity table |
| Row | Source record, observation, event, or entity representation | Row identity is not world identity |
| Primary / unique key | Source-scoped record identity | Composite keys and temporal validity matter |
| Foreign key | Declared directional relation / reference | Cardinality and nullability must be preserved |
| Column | Typed attribute or candidate perspective | Numeric data is not automatically a mathematical metric |
| Cell | Qualified observation/value | Preserve type, units, provenance, time, and NULL |
| SQL index | Physical access path | Not identical to WE-HDT or perspective semantics |
| View / materialized view | Derived perspective / representation | Preserve derivation, dependencies, refresh state |
| JOIN | Typed relational composition | JOIN result does not establish entity equivalence |
| Predicate / WHERE | Candidate constraint / selection | Preserve SQL three-valued logic |
| Aggregate / GROUP BY | Derived statistic over a defined population | Grouping and denominators must remain explicit |
| Transaction / CDC event | Source-state change event | Not necessarily a real-world or knowledge change |
| CHECK / UNIQUE / FK | Declared structural constraints | Database enforcement may be partial or deferred |
| Query plan | Execution trace / optimization artifact | Cost estimate is not a scientific confidence score |

**Core invariant:** `Source Record ≠ World Entity ≠ Perspective Descriptor ≠ Physical Index ≠ Evidence Claim`.

### 3.1 Table-role classification

A `Customers` table may be an entity-record collection, an `Orders` table may represent events, an `OrderItems` table may be an association with attributes, and a reporting table may contain aggregates. The WE mapper must record `tableRole` as a qualified assertion with supporting schema evidence, not force every table into one category.

### 3.2 Identity and joins

A primary key identifies a record within its declared source scope. Cross-database identity requires explicit evidence and conflict resolution. A foreign-key join demonstrates a database relationship, not necessarily physical or semantic identity. Entity resolution must be a separate, versioned operation with false-merge and false-split evaluations.

### 3.3 Column versus metric

A column can be a nominal attribute, timestamp, identifier, categorical label, measurement, score, similarity, relation endpoint, or derived feature. A mathematical metric must satisfy its specified axioms on a defined domain. Similarity scores, asymmetric distances, directional evidence, and business KPIs require different contracts. The word *metric* in business analytics must not silently imply a metric-space distance.

### 3.4 SQL NULL and epistemic states

SQL `NULL` participates in three-valued logic (`TRUE`, `FALSE`, `UNKNOWN`) and may reflect missing, inapplicable, withheld, or not-yet-recorded data. WE-SIO's `Established`, `Open`, and `Residual` are **epistemic states of claims or investigations**, not SQL scalar values. An `IS NULL` observation does not by itself justify labeling a row as residual evidence. Preserve source NULL semantics before adding a separate knowledge annotation.

### 3.5 Temporal and derived data

Distinguish event time, observation time, ingestion time, transaction time, and knowledge-assertion time. A view can be stale; an aggregate may change when its population changes; a corrected record may alter what is known without implying that the historical world changed. Provenance and version boundaries are mandatory for scientific claims.

## 4. Proposed SQL-native WE-SIO architecture

```text
Authorized SQL Sources
  |  schemas, constraints, statistics, records, CDC, query traces
  v
Source Adapters + Typed SQL Semantic Contracts
  |  provenance, identity scope, nullability, temporal semantics
  v
WE Mapping and Perspective Registry
  |  Entity/Record/Observation distinctions; metric/relation types
  v
WE-HDT / Optional Localization Structures + Catalog Metadata
  |  candidate retrieval; physical SQL optimizer remains authoritative
  v
Control Plane + Task/Perspective/Context/Budget Mask Generator
  |  schema/table/column/relation/operation masks
  v
Authorized SQL Planner and Execution Engine
  |  executable SQL, source permissions, result and plan traces
  v
MLIU / Evidence and Epistemic Layer
  |  Established Knowledge | Open Knowledge | Residual Evidence Registry
  v
Two-Ways CCC + Hypothesis/Test Generator
  |  candidate perspectives, counterexamples, validation proposals
  v
Evaluation / Knowledge Promotion / CDE / Collective Relay
  |  versioned decisions; optional authorized structural changes
```

The architecture is a **logical separation of responsibilities**, not a requirement for separate services or materialized indices. In a minimal implementation, most components may be metadata tables and library functions adjacent to an existing SQL engine.

### 4.1 Two-stage localization

- **Stage A — candidate localization:** use catalog, key/foreign-key graph, metadata embeddings if permitted, schema statistics, and a task mask to identify relevant tables, columns, and paths.
- **Stage B — semantic resolution:** validate join cardinality, predicate meaning, temporal and NULL semantics, permissions, metric contracts, and answer provenance before execution or claim formation.

WE-HDT is an optional candidate structure, **not a replacement for B-trees, hash indexes, columnar scans, or the SQL optimizer**. Any claimed advantage must be demonstrated against native catalog retrieval and strong schema-linking methods.

## 5. Mask-first SQL intelligence

A mask is a task-conditioned selection or weighting policy over the permitted computational scope. Let:

`M = G(q, P, C, B, A, S_v, H)`

where `q` is the task, `P` perspectives, `C` context, `B` budget, `A` the authorization boundary, `S_v` the versioned mapped structure, and `H` prior evaluation traces.

Candidate mask dimensions:

| Mask | Example selection | Principal failure risk |
|---|---|---|
| Schema/table | Relevant business domains and tables | Omitted table needed for answer |
| Column | Candidate measures, dimensions, keys | Missing join key or confounder |
| Relationship/JOIN | Authorized foreign-key paths | Incorrect join or fan-out |
| Perspective/metric | Units, time window, aggregation definition | Metric incompatibility |
| Operation | Retrieve, infer, diagnose, question | Unapproved operation or overreach |
| Depth | Join hops, graph expansion, exploration horizon | Under-retrieval |
| Budget | Tokens, SQL executions, runtime, sample size | Biased truncation |
| Epistemic | Established claims vs open hypotheses | Treating conjecture as fact |

**Mask ≠ access control.** The mask must be intersected with independently enforced database permissions; it cannot broaden the accessible scope. Mask policies must also preserve dependencies: selecting a measure may require grouping keys, join predicates, temporal filters, and provenance fields that are not explicitly mentioned in the user's question.

### 5.1 Mask contract

A minimal mask record should contain:

```yaml
maskId: mask-001
schemaVersion: catalog-v12
questionRef: q-017
perspectiveRefs: [p-revenue-v3]
authorizationScopeRef: policy-tenant-4
selectedTables: [orders, order_items]
selectedColumns: [orders.order_id, orders.created_at, order_items.amount]
selectedRelations: [orders.order_id = order_items.order_id]
allowedOperations: [read, aggregate]
budget: {maxQueries: 3, maxJoinDepth: 2}
policyVersion: mask-generator-v1
fallback: expand-and-revalidate
traceRef: trace-017
```

This example is illustrative; its join and aggregate semantics must be verified against an actual schema before use. Mask decisions should be inspectable and reversible without modifying the underlying records or schema.

### 5.2 Mask failure and fallback

If the initial mask omits a needed relationship or cannot establish a valid query, the system should expand candidate scope, record the failed assumption, and revalidate. A full-schema baseline should remain available in controlled experiments. Mask quality is measured by **end-to-end answer fidelity**, not merely reduced token count.

## 6. Epistemic separation over relational data

Three logically separate registries/views are proposed; they need not be separate physical tables.

### 6.1 Established Knowledge (`EK`)

Evidence-qualified assertions with declared scope, perspective, source query or derivation, version, uncertainty, time validity, and known limitations. *Established* means usable under its contract, not universally true.

### 6.2 Open Knowledge (`OK`)

Unresolved questions, unverified candidate relations, unknown measurements, competing explanations, and proposed tests. Open items do not require an observed prediction error.

### 6.3 Residual Evidence Registry (`RER`)

A residual must refer to a **declared baseline**—a model prediction, expected constraint, reconciliation target, or explanatory claim—and a traceable discrepancy or conflict. It is not a miscellaneous bucket for missing columns, nulls, or unanswered questions.

Example:

```text
Claim: expected monthly revenue = 120,000 under model v3
Observation: reconciled monthly revenue = 108,000 under query q42
Residual: -12,000, relative to model v3 and a fixed reporting scope
Status: unresolved; investigate late-arriving events, refunds, joins,
        missing records, definition changes, and model misspecification
```

A discrepancy does not automatically imply a new business law, causal effect, or valid metric. Data defects and incorrect joins must be investigated before promoting a hypothesis.

### 6.4 Knowledge promotion and retraction

`Open -> Evaluated -> Established` requires an evidence gate. `Established -> Contested -> Revised/Retired` must remain possible when contradictions or drift emerge. All transitions preserve prior versions and provenance. An unresolved residual may lead to a question, a data-quality issue, or a model revision; it must not be promoted solely because it is surprising.

## 7. SQL-native SI operations and Two-Ways CCC

Proposed operations over mapped relational structures:

- **Locate:** identify source records, tables, or candidate perspectives under a typed query.
- **Resolve:** determine entity/record references and compatible joins with evidence.
- **Relate:** traverse declared or validated relationships with direction and cardinality.
- **Infer:** derive qualified conclusions using explicit aggregation and model contracts.
- **Question:** produce a traceable, testable unresolved question.
- **Diagnose:** investigate a qualified residual against competing explanations.
- **Evolve:** propose and, after authorization, update derived perspectives, masks, or knowledge contracts.

**Forward CCC:** question -> constraints -> masked candidate scope -> validated SQL -> qualified answer.

**Reverse CCC:** discrepancy or open question -> candidate missing constraints/perspectives -> tests -> evaluation -> potential knowledge update.

The reverse direction must not mutate source data by default. New columns or indexes are **proposals**, not automatic DDL commands.

## 8. Four delta families and CDE boundaries

| Delta | Example | Governance implication |
|---|---|---|
| Activation (`ΔA`) | Change selected tables/columns/paths for this question | Cheap and reversible in principle; revalidate completeness |
| Epistemic (`ΔK`) | Promote or retract a claim; update evidence | Versioned audit and evidence thresholds |
| Structural (`ΔS`) | Add derived perspective, WE index, or mapping contract | Migration and regression tests |
| World/source-state (`ΔW`) | Authorized SQL `UPDATE`/`INSERT` affecting source records | Transactional authorization, audit, rollback policy |

An SQL transaction is a source-state operation, but it may represent correction of an earlier recording error rather than a real-world event. A WE metadata change does not imply an SQL write. **Undoing a knowledge assertion is not undoing the world.**

CDE should choose among `ΔA`, `ΔK`, and `ΔS` based on expected benefit, computational cost, semantic risk, and preservation of mature paths. Mask-first is a default **candidate policy**, not a universal requirement; a genuine schema mismatch may demand structural change.

## 9. Example workflow: order revenue discrepancy

Consider a database with `orders(order_id, customer_id, created_at, status)`, `order_items(order_id, quantity, unit_price)`, and `refunds(refund_id, order_id, amount, created_at)`.

**Task:** “Explain why this month's recognized revenue differs from the forecast.”

1. **Locate:** identify relevant tables, date fields, recognized-revenue definitions, and permissions.
2. **Mask:** activate the order, line-item, and refund paths; retain necessary keys and grouping fields.
3. **Resolve:** verify `orders` to `order_items` cardinality; prevent refund join fan-out; confirm time-zone and recognition rules.
4. **Execute:** run read-only parameterized SQL through the database engine; capture SQL, plan, snapshot/time, and result lineage.
5. **Compare:** use a named forecast and consistent accounting scope; if discrepancy remains, register a qualified residual.
6. **Question:** propose candidate explanations such as refunds, late-arriving orders, definition drift, or model error.
7. **Test:** perform independent queries and counterchecks; compare alternatives and document uncertainty.
8. **Promote:** only evidence-supported findings become established claims; unresolved alternatives remain open.
9. **Relay:** store reusable query tests and mask policy with schema and governance compatibility conditions.

**Failure example:** a direct three-table join may duplicate order-item amounts when an order has multiple refunds. WE-SIO must catch this with cardinality checks or preaggregation; it must not turn the resulting numerical difference into a “scientific residual.”

## 10. Minimal implementation contracts

**SQL-WE-001 — Source fidelity.** Preserve SQL types, NULL/three-valued logic, key constraints, cardinality, time, collation, and aggregate semantics; explicitly record any lossy conversion.

**SQL-WE-002 — Identity separation.** Source record identifiers and resolved World Entity identities are distinct, versioned references.

**SQL-WE-003 — Perspective typing.** Every promoted metric or relation declares units, domain, algebraic properties where applicable, provenance, and validity scope.

**SQL-WE-004 — Authorization monotonicity.** WE-SIO operations and masks cannot expand the source's permissions. No hidden bypass through caches, relay artifacts, or metadata.

**SQL-WE-005 — Query reproducibility.** Consequential answers retain executable SQL or a stable query representation, parameters, source version/snapshot when available, and result lineage.

**SQL-WE-006 — Mask dependency closure.** Selected scope includes required keys, join predicates, grouping and filter dependencies; incompleteness triggers fallback or an explicit uncertainty report.

**SQL-WE-007 — Epistemic separation.** Established, Open, and Residual are distinct claim states; SQL `NULL` is not automatically any one of them.

**SQL-WE-008 — Residual qualification.** Each residual names a comparison baseline, observed evidence, scope, discrepancy, uncertainty, and investigation status.

**SQL-WE-009 — Promotion gate.** No generated hypothesis becomes established without declared validation, counterexample checks, and provenance.

**SQL-WE-010 — Delta separation.** Mask, knowledge, derived structure, and source-state changes are independently recorded and authorized.

**SQL-WE-011 — Safe execution.** Initial runtime is read-only; any write/DDL capability requires separate explicit authorization and source-native controls.

**SQL-WE-012 — Relay compatibility.** Shared masks, mappings, and tests include schema versions, permission assumptions, and provenance; consensus alone is not independent evidence.

## 11. Counterexamples and boundary tests

| ID | Counterexample / failure | Required response |
|---|---|---|
| SQL-CE-001 | A table stores events rather than entities | Map as event records; do not fabricate entity identity |
| SQL-CE-002 | Two databases reuse the same primary key | Preserve source-scoped identity; require resolution evidence |
| SQL-CE-003 | A numeric column is a category code | Reject mathematical metric inference |
| SQL-CE-004 | SQL `NULL` indicates not applicable | Preserve NULL semantics; do not label as residual |
| SQL-CE-005 | A many-to-many JOIN multiplies measures | Detect cardinality/fan-out before inference |
| SQL-CE-006 | A materialized view is stale | Record freshness; avoid unqualified current claims |
| SQL-CE-007 | A masked column is needed for a filter | Expand dependency closure or fail explicitly |
| SQL-CE-008 | A mask excludes a counterexample | Measure omission; expand and revalidate |
| SQL-CE-009 | An observed anomaly comes from ETL corruption | Classify as data-quality issue, not novel law |
| SQL-CE-010 | A source update corrects a typo | Do not infer a real-world change |
| SQL-CE-011 | Two business metrics share a name but differ in definition | Require typed perspective and scope reconciliation |
| SQL-CE-012 | A relay policy exposes restricted metadata | Enforce permission-safe artifact transfer |
| SQL-CE-013 | Query succeeds but result violates expected population | Audit denominator, filters, and time window |
| SQL-CE-014 | Strong text-to-SQL baseline already performs equally well | Report null result; do not claim WE-SIO superiority |

## 12. Testable hypotheses

These are proposals for a separate registry; **none is validated by this document**.

**WEH-035 — Relational mapping fidelity.** A contract-based SQL-WE mapper can preserve a specified set of SQL semantics across heterogeneous schemas with fewer critical semantic errors than a naive row/entity-column/metric mapping.

**WEH-036 — Mask-first schema localization.** On large schemas, task-conditioned masks can reduce catalog/context processing or execution cost while maintaining non-inferior end-to-end answer correctness relative to full-schema and strong schema-linking baselines.

**WEH-037 — Epistemic-state reliability.** Separating Established, Open, and Residual states reduces false promotion of unknowns or data defects into knowledge claims in a controlled evaluation.

**WEH-038 — Residual diagnosis quality.** Baseline-qualified residual records improve attribution accuracy and investigation reproducibility compared with an undifferentiated anomaly bucket.

**WEH-039 — Reusable mask relay.** Versioned mask policies can transfer between compatible tasks or schemas with measurable net benefit after adaptation and validation overhead.

**WEH-040 — Controlled knowledge evolution.** Explicit promotion/retraction contracts reduce unsupported or irreproducible derived claims compared with unconstrained agent-generated SQL analysis.

## 13. Validation roadmap

### P0 — Mapping and conformance before runtime

- Build a compact multi-schema corpus: entity tables, events, association tables, temporal tables, aggregates, and intentionally ambiguous schemas.
- Implement source metadata adapters and typed descriptors without automatic data writes.
- Test all SQL-WE-001..012 contracts and SQL-CE-001..014 counterexamples.
- Establish ground-truth SQL semantics for keys, NULL, joins, aggregates, time, and identity.
- **Exit criterion:** no critical fidelity or authorization failures on the declared conformance suite; publish known unsupported cases.

### P1 — Mask-first localization and query evaluation

- Compare against: native catalog/keyword search; full-schema prompting; a strong schema-linking/text-to-SQL baseline; and an ablation without masks.
- Measure: execution correctness, schema-link recall, join-path correctness, evidence completeness, token usage, database cost, end-to-end latency, and fallback rate.
- Stratify by schema size, query complexity, join depth, ambiguity, and schema drift.
- Report confidence intervals, per-class failure rates, and mask generation overhead.
- **Exit criterion:** a prespecified, reproducible quality/cost improvement or an explicit negative result.

### P2 — Epistemic and residual-driven discovery

- Seed known data-quality defects, model discrepancies, missing measurements, and genuinely open questions as distinct classes.
- Evaluate residual qualification, causal-overclaim prevention, hypothesis testability, evidence promotion, and retraction behavior.
- Require held-out checks and independent verification where feasible; separate data leakage from discovery.
- **Exit criterion:** measured gains in diagnostic precision or knowledge-state fidelity, with documented failure cases.

### P3 — CDE and collective-learning transfer

- Test reuse of mask policies and perspective contracts across related databases and schema versions.
- Compare activation-only adaptation with selective structural updates and full remapping.
- Measure catastrophic omission, regression burden, transfer cost, and governance compatibility.
- **Exit criterion:** transparent benefit/cost curves and versioned relay artifacts suitable for replication.

## 14. Threats to validity and governance

- **Semantic mismatch:** relational constraints do not fully capture business meaning; human-defined semantic layers may still be necessary.
- **Benchmark contamination:** evaluation data may overlap with model training or previously seen schemas.
- **Schema leakage:** a mask generator might infer restricted structure from error messages, logs, or cached metadata.
- **Optimization confounding:** the native SQL optimizer, not WE-SIO, may account for observed speedups.
- **Overfitting:** mask policies may work on narrow schemas and fail after drift.
- **False discoveries:** correlations, missing records, biased sampling, and ETL defects can masquerade as new knowledge.
- **Governance:** row-level security, tenant isolation, retention, and purpose limitations must apply to all derived artifacts.
- **Non-universality:** some workloads may benefit more from full-schema reasoning or explicit structural reorganization than from masking.

The framework should support abstention, provenance inspection, counterexample replay, and explicit unresolved leftovers.

## 15. Relationship to existing WE-SIO research

- **CASE-001 — SQL Columns to WE Perspective Indices:** foundational mapping and boundary case; this extension expands the application into an end-to-end SQL-native intelligence architecture.
- **EXT-005 — Mask-First Structural Intelligence and Epistemic Separation:** general principles instantiated here as schema/column/relation masks and claim-state separation.
- **WE-SIO-002 / 003:** perspective descriptors and optional WE-HDT localization.
- **WE-SIO-004 / 005:** adaptive blocks and metric-leaf operations.
- **WE-SIO-006 / 007 / 008:** Two-Ways CCC, residual-first diagnosis, and metric discovery.
- **WE-SIO-009:** activation, epistemic, structural, and world delta semantics.
- **SPEC-001 / 002 / 003 / 004 / 005 / 006:** identity, perspective, node/leaf, operation, evidence, and definition-evolution contracts.
- **SIF:** candidate localization/addressing, per-node intelligence, and control-plane integration; CDE remains a complementary structural-evolution/localization mechanism.

This extension **does not rename WE-SIO as SQL AI**. SQL is proposed as an especially useful engineering testbed and potential product domain, not the boundary of the underlying theory.

## 16. Open questions

1. What is the smallest SQL semantic kernel sufficient for useful WE mapping without a full business ontology?
2. When does a semantic layer outperform inferred perspective descriptors, and how should the two reconcile?
3. How can mask generators preserve recall on wide schemas without consuming more resources than they save?
4. Which schema statistics and query traces can be safely reused across tenant or privacy boundaries?
5. How should an epistemic registry represent conflicting evidence across reporting periods and perspectives?
6. Can residual-driven question generation yield independently validated findings beyond ordinary anomaly detection?
7. How should source CDC, derived index refresh, and knowledge-version changes be synchronized?
8. Under what workloads does CDE-based structural adaptation outperform stable structures plus masks?
9. What constitutes an independently reproducible SQL-native scientific-discovery benchmark?
10. Which relay artifacts are portable across database vendors, and which require vendor-specific contracts?

## 17. Proposed next artifacts and integration plan

**For WE-SIO v0.1.0:**

1. Add this file as `extensions/EXT-006-SQL-Native-Structural-Intelligence-and-Knowledge-Evolution.md`.
2. Update `CONTENTS.md`, `README.md`, and `CHANGELOG.md` with EXT-005 and EXT-006 entries.
3. Add WEH-035..040 to `TESTABLE-HYPOTHESES.md` after checking ID availability.
4. Cross-link `CASE-001` to this extension; keep the case focused on semantic mapping.
5. Add SQL-WE-001..012 as **proposed** conformance contracts; consider a future dedicated SQL specification rather than silently changing existing SPEC semantics.
6. Synchronize extension counts in release notes and ResearchGate materials if these additions are included in the tagged release.

**For a future implementation track:** publish a small reproducible reference dataset, schema mapping fixture, read-only adapter, baseline scripts, failure-case suite, and evidence audit format. Do not label the work a validated SQL AI framework until the benchmarks support that claim.

## 18. Conclusion

SQL is a promising **concrete proving ground** for WE-SIO because relational systems already expose typed structures, constraints, relationships, and executable queries. The proposed contribution is not merely natural-language-to-SQL conversion: it is a controlled transition from **relational data access** to **evidence-grounded structural intelligence**, with task-specific masks, explicit knowledge states, residual qualification, and versioned evolution. The central research obligation is to demonstrate that these additional structures yield measurable value without distorting SQL semantics, weakening authorization, or mistaking unexplained discrepancies for discoveries.

> **Reuse the SQL engine. Preserve relational meaning. Mask computation before rebuilding structure when appropriate. Separate the unknown from the residual. Validate knowledge before promotion.**

---

**Research status:** Proposed extension and test plan; no empirical performance or discovery claims.  
**Citation:** Sizhe Tan & GPT-Obot, *EXT-006 — SQL-Native Structural Intelligence and Knowledge Evolution*, WE-SIO v0.1.0, 2026-11-05.  
**Repository (intended):** https://github.com/sizhet/World-Entity-and-Structural-Intelligence-Operations  
**License:** Apache-2.0.
