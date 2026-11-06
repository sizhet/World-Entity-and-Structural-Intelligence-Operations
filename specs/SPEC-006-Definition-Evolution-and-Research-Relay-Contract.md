# SPEC-006 — Definition Evolution and Research Relay Contract

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research Specification  
**Status:** Proposed / not empirically validated  
**Scope:** Definition governance, counterexample handling, provenance, and Collective Learning Relay  
**Related:** WE-SIO-011, WE-SIO-012; SPEC-001 through SPEC-005  
**Authors:** Sizhe Tan & GPT-Obot

## Abstract

This specification defines a portable, inspectable contract for evolving research definitions without erasing their origins, rejected alternatives, counterexamples, or unresolved limitations. It formalizes a **Definition Evolution Loop (DEL)** and a **Research Relay Contract (RRC)** for WE-SIO and adjacent Structural Intelligence (SI) research. Its central distinction is between a definition's minimal semantic kernel, its optional extension contracts, and its evidence-based claims of applicability. Conformance means that an implementation or repository preserves the specified records and transitions; it does **not** establish the scientific truth of a hypothesis.

> Define the invariant, not the inventory. Preserve not only what we know, but also how we arrived there, what challenged it, and what remains unknown.

## 1. Normative language and status

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate proposed conformance requirements for this version. These requirements govern record integrity and research process, not the correctness of any unvalidated scientific theory. The contract is intentionally implementation-neutral: Git files, databases, event logs, and federated repositories MAY satisfy it.

### 1.1 Non-goals

- Proving WE-SIO, CDE, or any SI hypothesis by formalizing its documentation.
- Requiring a single universal ontology or metric for all world entities.
- Forcing every research project to adopt the same extension set.
- Requiring every proposal to become accepted, or every counterexample to invalidate a whole framework.
- Treating traceability as a substitute for independent replication or scientific review.

## 2. Minimal semantic kernel

A conformant definition record MUST identify:

1. **Referent** — what concept or operation is being defined.
2. **Core invariants** — the minimal properties claimed necessary for the definition.
3. **Scope** — the domain, assumptions, and known exclusions.
4. **Version** — an immutable identifier for the recorded formulation.
5. **Evidence and rationale** — references supporting or motivating its formulation.
6. **Challenge interface** — a mechanism for recording counterexamples and unresolved gaps.
7. **Evolution relation** — explicit links to predecessor and successor definitions, when any.

These are documentation-level requirements, not an assertion that seven properties constitute the minimal kernel of every mathematical or computational object.

A definition MAY have extension contracts, optional profiles, examples, implementation guidance, and performance claims. These MUST be distinguishable from its required invariants.

### 2.1 Definition completeness versus precision

A definition can be **precise within its declared scope** while remaining incomplete across future applications. A revision SHOULD specify whether it broadens, narrows, partitions, corrects, or replaces the prior scope. Mere addition of more examples does not itself change the kernel.

### 2.2 Anti-vacuity test

A candidate definition SHOULD be evaluated for:

- **Nontriviality:** Does it exclude at least some meaningful countercases?
- **Explanatory gain:** Does it distinguish phenomena better than an existing description?
- **Operational gain:** Does it support a useful test, interface, prediction, or procedure?
- **Compatibility:** Are its stated invariants mutually consistent?
- **Falsifiability where applicable:** What observation or constructed case would challenge it?

If the definition reduces to an unconstrained label for any state transition, similarity, or relation, the registry MUST flag the risk of vacuous generalization.

## 3. Canonical research records

The following schemas are illustrative JSON objects. A conformant implementation MAY use other serializations provided the required semantics remain recoverable.

### 3.1 DefinitionRecord

```json
{
  "record_type": "definition",
  "definition_id": "DEF-WE-001",
  "version": "0.1.0",
  "title": "World Entity — candidate representation",
  "status": "proposed",
  "kernel": ["stable referent within declared identity scope", "one or more perspective-addressable descriptions"],
  "scope": {"includes": ["represented physical and abstract referents"], "excludes": ["claims of direct access to reality"]},
  "extensions": ["EXT-WE-HDT-001"],
  "evidence_refs": ["SRC-001"],
  "counterexample_refs": [],
  "predecessor_refs": [],
  "decision_ref": "DEC-001",
  "open_residual_refs": ["RES-001"],
  "created_at": "2026-11-05T00:00:00Z",
  "provenance": {"contributors": ["Sizhe Tan", "GPT-Obot"], "source_kind": "research discussion"}
}
```

The timestamp above is an illustrative schema value, not a verified historical event time.

### 3.2 HypothesisRecord

```json
{
  "record_type": "hypothesis",
  "hypothesis_id": "HYP-001",
  "statement": "A hybrid perspective index improves some mixed-query workloads",
  "status": "untested",
  "applicability": "specified workload family, hardware and data distributions",
  "baseline_refs": ["BASELINE-KDTREE", "BASELINE-SQL"],
  "predicted_observables": ["latency", "recall", "memory"],
  "falsification_plan": "compare under matched correctness and resource constraints",
  "evidence_refs": [],
  "owner_or_relay_ref": "RELAY-001"
}
```

### 3.3 CounterexampleRecord

```json
{
  "record_type": "counterexample",
  "counterexample_id": "CE-CDE-CHESS-001",
  "target_definition_id": "DEF-CDE-001",
  "target_version": "0.1.0",
  "claim_challenged": "A delta cannot recur on a valid path",
  "construction": "A legal chess sequence can revisit a prior board configuration under the game's rules",
  "assumptions": ["legal move generation", "explicit history-dependent rules"],
  "reproducibility": "provide legal move list and position/history states",
  "assessment": "candidate counterexample; rule-sensitive",
  "disposition": "requires scoped path-memory policy",
  "evidence_refs": [],
  "status": "open"
}
```

A counterexample MUST name the **specific claim and version** challenged. It MUST NOT automatically be treated as a refutation of unrelated claims. For chess, repeated board configurations and full game states are not necessarily identical because turn, castling rights, en-passant state, repetition history, and other rules may matter.

### 3.4 DecisionRecord

```json
{
  "record_type": "decision",
  "decision_id": "DEC-002",
  "question": "Should no-delta-reuse be mandatory for CDE?",
  "options": ["universal invariant", "optional path-memory contract"],
  "chosen": "optional path-memory contract",
  "rationale": "repetition may be valid in cyclic and adversarial systems",
  "evidence_refs": ["CE-CDE-CHESS-001"],
  "tradeoffs": ["termination must be managed by separate policies"],
  "status": "proposed",
  "supersedes": null
}
```

### 3.5 ResidualRecord

```json
{
  "record_type": "research_residual",
  "residual_id": "RES-001",
  "context": "entity identity across inconsistent perspectives",
  "expected": "stable resolution under a declared identity contract",
  "observed": "unresolved conflicting identifiers",
  "gap_type": "definition_or_evidence_gap",
  "possible_explanations": ["insufficient evidence", "ambiguous identity scope"],
  "next_tests": ["construct merge/split adversarial cases"],
  "status": "open",
  "provenance_refs": ["DEF-WE-001"]
}
```

### 3.6 RelayRecord

```json
{
  "record_type": "research_relay",
  "relay_id": "RELAY-001",
  "source_refs": ["DEF-WE-001", "HYP-001", "CE-CDE-CHESS-001"],
  "purpose": "test and refine candidate invariants",
  "claims": [{"text": "Hybrid indexing is promising", "epistemic_status": "hypothesis"}],
  "artifacts": ["test specification", "benchmark protocol"],
  "limitations": ["no controlled benchmark yet"],
  "open_residual_refs": ["RES-001"],
  "requested_next_actions": ["execute baseline comparison", "submit counterexamples"],
  "handoff_status": "ready_for_review",
  "provenance": {"contributors": ["Sizhe Tan", "GPT-Obot"]}
}
```

## 4. Definition Evolution Loop (DEL)

A DEL iteration is a traceable transition:

```text
Definition(v)
   → application / adversarial probe
   → evidence and counterexample capture
   → residual classification
   → proposed revision or scoped extension
   → impact analysis and conformance tests
   → decision (accept / reject / defer / split)
   → Definition(v+1) or retained Definition(v)
   → relay to the next researcher or system
```

A conformant DEL implementation MUST:

- Retain the original definition version and its original scope.
- Preserve the challenge even when rejected, with a reasoned disposition.
- Distinguish a **definition error** from an **implementation bug**, **data error**, or **open empirical question**.
- Link every accepted revision to a decision record and an explicit change description.
- Record affected downstream contracts, examples, tests, and indexes.
- Permit a **no-change** decision; evolution is not obligatory expansion.
- Preserve unresolved residuals rather than silently marking them resolved.

### 4.1 Allowed revision operations

| Operation | Semantics | Required record |
|---|---|---|
| `CLARIFY` | Remove ambiguity without intended semantic change | rationale and equivalence argument |
| `NARROW` | Restrict scope or assumptions | excluded cases and migration impact |
| `BROADEN` | Admit additional cases | evidence and new tests |
| `SPLIT` | Partition a concept into distinct definitions | mapping and compatibility notes |
| `MERGE` | Combine compatible concepts | conflict analysis and invariants |
| `REPLACE` | Supersede an unsuitable kernel | explicit incompatibilities |
| `DEPRECATE` | Stop recommending a definition | successor or retirement reason |
| `REVERT` | Restore an earlier version | rollback reason and affected dependents |

A revision MUST NOT overwrite the prior record in place without retaining a recoverable historical version.

## 5. Conformance and versioning

### 5.1 Immutable identity

Every record MUST have a stable identifier and a revision/version reference. An identifier SHOULD be globally unique within its declared namespace. Content hashes MAY be added for tamper detection; hashes do not establish truth or authorship.

### 5.2 Evidence statuses

The registry MUST distinguish at least:

- `proposed` — a candidate statement or definition;
- `untested` — no qualifying test has been executed;
- `under_test` — testing is underway;
- `supported_within_scope` — evidence supports the claim within declared conditions;
- `challenged` — material contrary evidence exists;
- `rejected` — not retained under specified criteria;
- `superseded` — replaced by a newer version;
- `unresolved` — insufficient grounds for a decision.

Statuses MUST NOT imply universal validation. A rejected hypothesis MAY remain in the archive to prevent redundant rediscovery.

### 5.3 Provenance minimum

Each consequential claim, decision, or revision MUST carry a source reference or an explicit `source_unavailable` marker; a creation or revision time; the responsible contributor or system identifier when known; and an epistemic status. AI-assisted text SHOULD identify assistance transparently without attributing unverified experiments to the assistant.

### 5.4 Referential integrity

All references MUST resolve to existing records or be marked as external/unresolved. Broken links MUST be surfaced by conformance checks, not silently discarded. An external source reference SHOULD include a stable URI, title, access date where relevant, and content/version fingerprint when available.

### 5.5 Version compatibility

- Patch changes SHOULD preserve semantics and correct wording or formatting.
- Minor changes MAY add optional extensions or compatible fields.
- Major changes SHOULD be used for incompatible kernel or contract changes.

These are proposed conventions, not guarantees that semantic compatibility can be inferred from a version number alone. Every change MUST have an explicit compatibility assessment.

## 6. Collective Learning Relay Contract (RRC)

A Relay Piece is a handoff artifact carrying **claims, constraints, evidence, counterexamples, unresolved questions, and actionable next steps**. It is not merely a narrative summary.

### 6.1 Required relay payload

A conformant relay MUST provide:

1. **Context and scope** — research problem and applicable definitions.
2. **Claims with epistemic statuses** — facts, hypotheses, design proposals, and unknowns separated.
3. **Source and provenance links** — traceable origins of claims and changes.
4. **Relevant counterexamples** — including known limitations and failures.
5. **Residuals and explicit leftovers** — unresolved issues with owners or suggested follow-up.
6. **Validation contract** — tests or evidence needed to promote claims.
7. **Compatibility metadata** — applicable definition/specification versions.
8. **Next-step interface** — what another agent, researcher, or repository can do.

### 6.2 Relay modes

| Mode | Payload emphasis | Success criterion |
|---|---|---|
| Execution Relay | repeatable operation and its outputs | reproducible execution record |
| Knowledge Relay | evidence-backed findings and scope | inspectable claim/evidence mapping |
| Structural Relay | revised definitions, interfaces, or algorithms | explicit versioned change with tests |

Repeated execution MAY qualify as relay when it contributes new data, reliability estimates, or longitudinal evidence. A duplicate run with no recorded output or provenance does not automatically add scientific value.

### 6.3 Federated contributions

Independent contributors MAY fork, challenge, and extend records. A merge or promotion process MUST retain source attribution and conflicting evidence. Conflicts MAY remain unresolved; forced consensus is not a conformance requirement. Permissions and governance rules MUST be explicit where the relay can trigger code execution, model updates, external publication, or irreversible changes.

## 7. Integration with WE-SIO components

| Component | DEL / RRC responsibility |
|---|---|
| WE identity and perspective descriptors (SPEC-001) | version semantic scopes and identity assumptions |
| Euclidean, metric, relational indexes (SPEC-002) | record mathematical guarantees and invalid pruning counterexamples |
| WE-HDT nodes, blocks, MLIU (SPEC-003) | trace structural decisions, budgets, and capability changes |
| SI Operations and Two-Ways CCC (SPEC-004) | preserve forward answers and reverse questions separately |
| Residual and Metric Discovery (SPEC-005) | link anomaly, evidence, hypothesis, validation, promotion |
| CDE | represent definition and structure changes as constrained, typed transitions |
| AQSI | generate and prioritize questions without automatically promoting answers |
| UIERU / Collective Learning | transport and integrate provenance-preserving relay units |
| SIF | provide localization and governance interfaces for research operations |
| SSI | distinguish self-model claims from claims of subjective experience |

The table describes proposed integration contracts, not demonstrated interoperability.

## 8. Boundary stress tests

### 8.1 Chess and CDE

**Problem:** A D-BTP-specific no-delta-reuse constraint is generalized into a purported universal CDE invariant.  
**Challenge:** Chess permits some repeated moves and positions, subject to rule-dependent state and history.  
**Required response:** Split universal transition semantics from optional path-memory and cycle-control policies; preserve the challenged version, test case, and decision.  
**Expected outcome:** A narrower, more defensible kernel rather than an unqualified assertion of universality.

### 8.2 World Entity and index identity

**Problem:** A change in metric representation is mistaken for creation of a new real-world entity.  
**Required response:** Maintain entity identity and representation version separately; mark ambiguous identity cases as unresolved and retain evidence.

### 8.3 Mathematical metric versus directional relation

**Problem:** An asymmetric preference score is used with metric-tree triangle-inequality pruning.  
**Required response:** Reject unsupported pruning guarantees, revise the descriptor contract, and preserve the failing query as a regression case.

### 8.4 Clinical residuals

**Problem:** A treatment-response residual is declared a new biological mechanism without ruling out confounding, noise, missingness, or selection bias.  
**Required response:** Record alternative explanations, preregister validation where feasible, and maintain the hypothesis as unconfirmed until appropriate independent evidence exists. No clinical recommendation follows from the registry alone.

### 8.5 Self-modeling versus subjective experience

**Problem:** A self-referential prediction loop is presented as proof of consciousness.  
**Required response:** Separate functional self-modeling properties from claims about phenomenal experience and record the latter as unresolved.

## 9. Conformance test suite

The following tests define candidate acceptance criteria for the **research record system**. Each test SHOULD have a fixture, expected outcome, execution record, and failure explanation.

| ID | Test | Expected result |
|---|---|---|
| DEL-CT-001 | Create definition with missing scope | reject or mark incomplete |
| DEL-CT-002 | Record distinct kernel and extension fields | retain separation |
| DEL-CT-003 | Challenge a specific definition version | preserve target and claim |
| DEL-CT-004 | Submit unsupported counterexample | retain but mark unverified |
| DEL-CT-005 | Revise definition by narrowing | preserve excluded cases and predecessor |
| DEL-CT-006 | Revise definition by broadening | require new conformance/validation plan |
| DEL-CT-007 | Split a definition | maintain mapping from original |
| DEL-CT-008 | Reject a revision | keep original and rationale |
| DEL-CT-009 | Revert a revision | preserve intervening history |
| DEL-CT-010 | Change core invariant without compatibility review | fail conformance |
| DEL-CT-011 | Mark hypothesis as established without evidence | reject status promotion |
| DEL-CT-012 | Register conflicting evidence | preserve both sides |
| DEL-CT-013 | Reference a missing record | flag unresolved reference |
| DEL-CT-014 | Attempt silent deletion of counterexample | fail audit integrity |
| DEL-CT-015 | Record unresolved residual | keep visible in relay |
| DEL-CT-016 | Export and re-import relay | preserve identifiers and statuses |
| DEL-CT-017 | Import older schema | apply explicit migration or reject safely |
| DEL-CT-018 | Repeated execution with distinct outputs | preserve run-level provenance |
| DEL-CT-019 | Duplicate execution with no new evidence | do not claim independent validation |
| DEL-CT-020 | Chess cycle challenge | route to optional cycle/path-memory policy |
| DEL-CT-021 | Metric axiom failure | prevent unsupported index guarantee |
| DEL-CT-022 | Self-model consciousness overclaim | flag unsupported inference |
| DEL-CT-023 | Merge conflicting relay branches | retain provenance and conflict status |
| DEL-CT-024 | Trigger unauthorized structural promotion | block and record attempt |
| DEL-CT-025 | Inspect full definition ancestry | recover complete version lineage |
| DEL-CT-026 | Generate research handoff | include next tests and explicit leftovers |

Passing these tests establishes process conformance only. Performance, scientific utility, and explanatory gain require separate empirical studies.

## 10. Testable hypotheses

**H-DEL-01 — Reduced definition drift.** Versioned kernels and explicit scopes reduce unnoticed semantic drift compared with unstructured documentation. Measure reviewer agreement and incidence of contradictory downstream usage.

**H-DEL-02 — Improved counterexample retention.** An explicit counterexample registry increases reuse of prior failures and reduces repeated invalid claims. Compare matched research teams or simulated workflows.

**H-DEL-03 — Higher-quality relay.** Relay payloads with provenance and explicit leftovers improve downstream reproduction and follow-up quality relative to plain summaries. Measure successful reproduction and clarification burden.

**H-DEL-04 — Faster correction under challenge.** DEL reduces time to a justified scope revision when new boundary cases emerge. Control for documentation overhead and contributor experience.

**H-DEL-05 — Better hypothesis calibration.** Explicit epistemic statuses reduce premature promotion of conjectures to established findings. Assess calibration and independent review outcomes.

**H-DEL-06 — Manageable overhead.** Lightweight records provide net benefit for medium-to-large evolving research programs, but may be excessive for trivial tasks. Measure time and storage costs versus quality gains.

All six are **unverified hypotheses**, not results.

## 11. Validation roadmap

**Phase A — Static contract review.** Review schemas, required fields, definitions of status, and anti-vacuity criteria. Run document-level conformance checks and identify ambiguous terms.

**Phase B — Replayed historical cases.** Reconstruct selected WE-SIO, CDE/chess, and index-conformance discussions as versioned definition and counterexample records. Evaluate whether provenance and decisions remain recoverable.

**Phase C — Controlled relay experiments.** Compare unstructured handoffs with RRC handoffs on identical tasks; preregister success criteria and assess evaluator agreement.

**Phase D — Multi-agent and multi-repository trials.** Test divergent branches, merge conflicts, schema migration, and authorization boundaries with audit logs.

**Phase E — External replication.** Publish fixtures, anonymized test data where permitted, failures, and independent assessments. Revise the contract based on documented counterexamples.

## 12. Repository trace layout

The recommended WE-SIO directory is:

```text
research-trace/
├── ORIGIN-AND-RESEARCH-QUESTIONS.md
├── DISCUSSION-SYNTHESIS-2026-11-05.md
├── HYPOTHESIS-REGISTRY.md
├── DEFINITION-REGISTRY.md
├── COUNTEREXAMPLE-REGISTRY.md
├── DECISION-LOG.md
└── UNRESOLVED-RESIDUALS.md
```

These Markdown files MAY be supplemented by machine-readable records. Each registry SHOULD document stable IDs, versioning rules, cross-references, status vocabulary, and review cadence. A directory tree alone does not satisfy the contract unless the records contain meaningful traceable content.

## 13. Governance, privacy, and security

Research traces MAY contain sensitive observations, confidential contributions, or unverified allegations. A conformant public relay MUST respect applicable consent, privacy, access-control, and data-minimization requirements. Raw personal or clinical records SHOULD NOT be published merely to improve traceability. Redaction MUST preserve an auditable statement of what was removed and why, without leaking the protected content. Model-generated hypotheses MUST NOT trigger autonomous real-world actions without an appropriate authorization and validation policy.

## 14. Open questions and explicit leftovers

1. What is the smallest useful definition kernel before it becomes vacuous?
2. How can conformance distinguish a true counterexample from a misunderstood scope condition?
3. Which forms of evidence warrant changing a kernel rather than adding an extension?
4. How should incompatible research branches coexist without forced consensus?
5. How can provenance remain portable across Git, databases, agents, and future protocols?
6. Which semantic changes can be detected automatically, and which require human review?
7. How should failed hypotheses be indexed for future discovery without amplifying misinformation?
8. What are appropriate budgets for recursive definition revisions and agent-driven questioning?
9. When is a repeated execution informative enough to constitute a new relay contribution?
10. How can a project measure whether its definition governance yields actual explanatory or operational gain?
11. How should partial, probabilistic, or contested identity claims be represented in shared registries?
12. How should external scientific validation and internal contract conformance be linked without conflation?

These questions MUST remain visible until addressed with traceable evidence and decisions.

## 15. Proposed acceptance criteria for v0.1.0

The specification is suitable for an initial research release when:

- Its record schemas and normative distinctions are internally consistent.
- Each of the seven trace files has a clear role and stable cross-reference conventions.
- At least one full DEL example, including a counterexample and no-change or revision decision, can be reconstructed.
- The 26 conformance tests are documented as proposed fixtures or explicit future work; unexecuted tests are not reported as passed.
- Unverified hypotheses are labeled accordingly.
- All downstream integration claims are framed as proposals until demonstrated.

## 16. Conclusion

Definition evolution is itself a structural intelligence problem: a research community must retain stable meaning where justified, revise meaning where challenged, and preserve the history of both. WE-SIO proposes a **minimal kernel + conformance contracts + open extensions** methodology supported by explicit counterexamples, residuals, decisions, and relay records. The resulting contract is designed to make research **inspectable, revisable, and transferable**—not to certify its scientific conclusions in advance.

**Guiding principle:** A useful relay transmits not only an answer, but also its assumptions, limitations, provenance, and next question.

---

*WE-SIO v0.1.0 — Proposed research contract. Contributions and counterexamples are welcome; no experimental results are claimed in this document.*
