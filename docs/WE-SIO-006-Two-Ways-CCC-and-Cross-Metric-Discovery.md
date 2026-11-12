# WE-SIO-006 — Two-Ways CCC and Cross-Metric Discovery

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research hypothesis / architecture proposal  
**Date:** 2026-11-05  
**Authors:** Sizhe Tan & GPT-Obot  
**Status:** Proposed; not an empirically validated algorithm  
**Repository location:** `docs/WE-SIO-006-Two-Ways-CCC-and-Cross-Metric-Discovery.md`

## Abstract

World Entity (WE) representations may be indexed through heterogeneous perspectives: Euclidean coordinates, mathematically defined metrics, and directional or relational descriptions that are not metrics. Conventional retrieval often proceeds from a query to candidate objects and then evaluates predicates against those objects. WE-SIO proposes **Two-Ways CCC** as a research architecture in which candidate localization and conditional evaluation are complemented by an evidence-grounded reverse path: unresolved outcomes, contradictions, and residuals can prompt revisions to queries, perspectives, candidate generators, and hypotheses. This paper defines a provisional operational contract for this bidirectional loop, introduces a cross-metric discovery process, identifies safety and epistemic constraints, and specifies falsifiable experiments. “CCC” is retained as a project term for condition/constraint-guided candidate coordination; the precise expansion and compatibility with earlier CCC variants remain subjects of definition governance.

**Keywords:** World Entity; Two-Ways CCC; cross-metric discovery; residual; weak evidence; WE-HDT; MLIU; perspective; structural relay; metric discovery.

## 1. Research position and scope

This paper follows WE-SIO-001 through WE-SIO-005. Its central question is:

> Can a system use the *failures and residuals of one perspective* to discover useful candidate structures, questions, or descriptors in another perspective, without confusing exploratory hypotheses with validated facts?

The proposed contribution is **not** the invention of bidirectional search, feedback loops, anomaly detection, or metric learning. Those fields have established precedents. The research target is a coherent, traceable interface between (i) heterogeneous entity perspectives, (ii) conditional candidate coordination, (iii) residual evidence, and (iv) controlled structural evolution.

The following distinctions are mandatory:

- **Entity**: the referent under study, not equivalent to its records or indexes.
- **Representation**: a versioned, evidence-linked account of an entity.
- **Perspective**: a descriptor with domain, semantics, comparison rules, limitations, and provenance.
- **Metric**: a distance function satisfying metric axioms on a specified domain; not a generic synonym for score.
- **Relation / directional score**: an admissible perspective that need not satisfy symmetry or triangle inequality.
- **Residual**: a documented mismatch between an expectation and an observation; not automatically evidence of a new causal mechanism.

## 2. From one-way retrieval to two-way coordination

### 2.1 Forward path

A conventional forward path is:

`Question → Perspective selection → Candidate localization → Conditional evaluation → Evidence-ranked result`

For WE-HDT, localization may be Euclidean, metric, relational, or a hybrid. Euclidean-first is an optimization option, **not** a universal entry requirement. A relational-only entity must remain queryable.

### 2.2 Reverse path

The proposed reverse path is:

`Observed mismatch / missing explanation → Residual registration → Candidate explanation or perspective proposal → Targeted retrieval / test → Validation or explicit leftover`

“Reverse” refers to the direction of **inquiry and control**, not necessarily inversion of a mathematical function or a causal inference. The reverse path may discover that the original query was wrong, the evidence was noisy, the indexing policy was too restrictive, or a new descriptor is worth testing.

### 2.3 Two-Ways CCC loop

```text
                           ┌──────────────────────┐
                           │ Question / Hypothesis│
                           └──────────┬───────────┘
                                      │ forward
                                      ▼
                           ┌──────────────────────┐
                           │ Perspective & Query  │
                           │ Contracts             │
                           └──────────┬───────────┘
                                      ▼
                           ┌──────────────────────┐
                           │ Candidate Localization│
                           │ (WE-HDT / other index)│
                           └──────────┬───────────┘
                                      ▼
                           ┌──────────────────────┐
                           │ CCC Evaluation / MLIU│
                           └──────────┬───────────┘
                                      ▼
                           ┌──────────────────────┐
                           │ Results + Uncertainty│
                           │ + Residuals           │
                           └──────────┬───────────┘
                                      │ reverse inquiry
                                      ▼
                           ┌──────────────────────┐
                           │ Residual Registry    │
                           │ & Question Generator │
                           └──────────┬───────────┘
                                      ▼
                           ┌──────────────────────┐
                           │ Candidate Perspective│
                           │ / Hypothesis / Query │
                           └──────────┬───────────┘
                                      │ controlled test
                                      └───────────► forward path
```

The loop must have a termination/budget policy. Unbounded reverse questioning is neither a correctness guarantee nor an acceptable execution default.

## 3. Candidate CCC semantics

The project uses CCC provisionally as **Condition/Constraint-guided Candidate Coordination**. This wording is a working operational gloss, not a retroactive redefinition of all prior SI CCC usage. A definition-registry entry should record historical variants and resolve the canonical expansion before a stable specification release.

A CCC request can be modeled as:

$$
Q = (E_0, P, C, G, B, V)
$$

where:

- $E_0$: starting entity set or discovery scope;
- $P$: requested perspectives and their contracts;
- $C$: hard constraints and soft conditions, separately typed;
- $G$: goal or evidence question;
- $B$: resource, risk, and exploration budget;
- $V$: version and provenance context.

A candidate evaluation yields:

$$
R = (E_c, S, X, U, L)
$$

where $E_c$ is a candidate set, $S$ contains scores or predicate outcomes with explicit semantics, $X$ supporting evidence, $U$ uncertainty, and $L$ explicit leftovers including unresolved residuals. Scores from different perspectives must not be aggregated as if they shared a scale without calibration or a declared aggregation policy.

### 3.1 Hard constraints vs soft evidence

Hard constraints define eligibility. Soft evidence supports ranking or hypothesis generation. A reverse-loop proposal **must not silently relax hard constraints**. Any relaxation requires an explicit authorized policy change and a trace entry.

### 3.2 Conditional coordination vs causality

A condition that improves prediction is not automatically causal. Directional associations may be useful for candidate generation while remaining unsuitable for causal claims.

## 4. Perspective contracts and cross-metric mappings

Each perspective descriptor should declare at least:

```yaml
perspective_id: string
version: string
domain: entity_type_or_scope
kind: euclidean | metric | relational | directional | categorical | other
value_schema: schema_ref
comparison_semantics: documented_rule
units_or_scale: optional
missingness_policy: explicit
uncertainty_model: optional
provenance_requirements: explicit
validity_context: optional
privacy_and_access_policy: policy_ref
conformance_tests: test_refs
```

A **cross-perspective mapping** is a versioned hypothesis or validated transform, not an assumed identity. For perspectives $P_i$ and $P_j$, represent a mapping as:

$$
T_{i\to j}: (x_i, c, e) \mapsto (\widehat{x}_j, u, p)
$$

where $c$ is context, $e$ supporting evidence, $u$ uncertainty, and $p$ provenance. Some mappings are partial, many-to-many, stochastic, or impossible. Reverse mappings need not exist; $T_{j\to i}$ is not automatically an inverse.

### 4.1 Four discovery patterns

1. **Metric → Metric:** residual clustering under one distance geometry motivates a second metric or embedding.
2. **Euclidean → Relational:** spatially near entities differ because of organizational or interaction relationships.
3. **Relational → Metric:** a relational pattern motivates a measurable descriptor, subject to operationalization and validation.
4. **Residual → New perspective:** persistent, reproducible mismatch motivates a new candidate dimension, not an immediate schema promotion.

## 5. Residual-driven cross-metric discovery

### 5.1 Residual record

A first-class residual should include:

```yaml
residual_id: string
entity_refs: [entity_id]
question_id: string
perspective_versions: [perspective_ref]
expectation: documented_prediction_or_constraint
observation: evidence_ref
mismatch_definition: comparator_ref
magnitude_or_category: optional
uncertainty_and_missingness: documented
possible_artifacts: [noise, confounding, selection_bias, leakage, drift]
status: open | under_test | explained | rejected | unresolved
hypothesis_refs: []
provenance: event_log_ref
```

### 5.2 Discovery pipeline

**D0 — Detect:** Record mismatch without interpreting it as a discovery.  
**D1 — Qualify:** Check data quality, leakage, missingness, confounding, and model misspecification.  
**D2 — Compare:** Search related entities and perspectives; test whether the residual replicates.  
**D3 — Propose:** Generate competing explanations, new descriptors, or query revisions.  
**D4 — Challenge:** Seek counterexamples and negative controls.  
**D5 — Validate:** Evaluate out of sample and against strong baselines.  
**D6 — Promote or retain:** Promote a perspective only if it passes its contract; otherwise retain a traceable leftover.

The system should support multiple competing hypotheses for the same residual. A single residual may be explained by a data artifact, a context change, or a genuine missing variable.

## 6. MLIU operation mapping

Two-Ways CCC should be expressed through the six candidate Metric-Leaf Intelligence Unit (MLIU) operations from WE-SIO-005:

| Operation | Forward contribution | Reverse contribution |
|---|---|---|
| **Locate** | Retrieve eligible candidate entities | Identify where relevant unexplained cases may be found |
| **Resolve** | Evaluate descriptors and conditions | Re-examine failed assumptions and comparison contracts |
| **Relate** | Traverse explicit entity relationships | Propose candidate relations, with evidence labels |
| **Infer** | Produce calibrated, scoped hypotheses | Generate alternative explanations for residuals |
| **Question** | Ask for missing data or clarification | Form discriminating tests and counterexample searches |
| **Evolve** | Apply approved representation/index updates | Propose contract changes through controlled governance |

A logical MLIU need not correspond to a physical tree leaf or a dedicated autonomous agent. Shared services and lazy activation are valid implementation choices.

## 7. WE-HDT integration

WE-HDT offers candidate localization and perspective-addressable resolution. Two-Ways CCC is a **control and discovery layer**, not a replacement for the underlying retrieval structure.

A proposed query execution plan:

```text
Plan(Q):
  verify perspective contracts and access policy
  choose eligible candidate generators (Euclidean / metric / relational)
  obtain candidate sets with declared recall guarantees or limitations
  evaluate hard constraints without silent relaxation
  invoke MLIU Resolve/Relate/Infer where budget permits
  return results + uncertainty + explicit residuals
  optionally schedule bounded reverse-inquiry proposals
```

For approximate indexes, recall is empirical or bounded by the implementation's documented guarantees; it must not be described as exact. Reverse inquiry should not contaminate the evaluation dataset used to judge the same hypothesis.

## 8. Worked example A — Spatial proximity is insufficient

Suppose a delivery network indexes facilities by coordinates. Two facilities are spatially close but have very different transit times. A forward Euclidean search identifies both; a downstream time prediction generates a residual.

The reverse path tests competing hypotheses: congestion, restricted routes, transfer schedules, operating hours, and network connectivity. A **graph-travel-time** perspective may outperform straight-line distance for this task. However, the result depends on time, mode, and network state. The graph descriptor is not automatically a metric; directed travel times may be asymmetric.

A valid promotion test uses held-out origin-destination pairs, time windows, and distribution shifts. Compare against routing baselines before claiming a WE-SIO-specific gain.

## 9. Worked example B — Clinical response heterogeneity

Consider an observational cohort where patients with similar recorded baseline attributes exhibit different treatment responses. The mismatch is registered as a residual rather than dismissed or treated as evidence of a novel biological mechanism.

Possible follow-up perspectives include treatment adherence, comorbidity, timing, laboratory markers, or care-pathway differences. The system may propose stratified analyses and discriminating questions, but **must not infer treatment efficacy or recommend clinical care from these exploratory patterns**. Confounding, selection effects, measurement error, multiple testing, and external replication remain central. Patient privacy, consent, governance, and domain-expert review are mandatory.

This case tests whether the residual registry improves the *quality and traceability of research questions*, not whether the system independently discovers a clinical truth.

## 10. Worked example C — Cross-metric entity reconciliation

Two records have similar textual descriptions but conflicting location and affiliation information. A text similarity score proposes a match; identity constraints reject automatic merging. Reverse inquiry requests authoritative identifiers and time-scoped affiliation evidence. The system retains both hypotheses until identity evidence passes the merge contract.

This illustrates an essential boundary: **cross-metric similarity does not imply entity identity**. Provenance and conflict handling take precedence over convenient folding.

## 11. Learning and governance

### 11.1 Proposal lifecycle

`candidate → registered → tested → challenged → accepted / rejected / deferred → monitored`

Every proposal should record its originating residual, supporting and contradicting evidence, dataset partitions, evaluator, and decision rationale. The decision may revise a query, a perspective, an index, or an MLIU capability; these are distinct actions.

### 11.2 CDE interface

Constrained Delta Evolution (CDE) can express approved representation changes as typed transitions:

$$
(S_{t+1},\tau)=\mathrm{Apply}(S_t,\Delta,C)
$$

Here $S_t$ is a versioned representation state, $\Delta$ a proposed change, $C$ applicability/constraint policy, and $\tau$ the trace. The physical world need not change when the representation changes. No-Delta-Reuse is **not** a universal CDE axiom; path-memory and cycle policies are application-specific contracts.

### 11.3 Three kinds of delta

- **World Delta:** an observed or hypothesized change in the external referent.
- **Epistemic Delta:** a change in the system's knowledge or representation.
- **Operational Delta:** a change in query plans, indexes, budgets, or execution policies.

Do not conflate them. A newly discovered relationship can be an epistemic delta without a world delta.

### 11.4 Safe execution boundaries

The reverse loop may propose actions, but should not autonomously change high-stakes decisions, access controls, or source-of-truth records without the appropriate authorization and review. Preserve rollback and auditability for accepted structural updates.

## 12. Minimal interface proposal

```text
TwoWaysCCC.evaluate(request, perspective_contracts)
  -> EvaluationResult {
       candidates, evidence, uncertainty, residual_refs,
       constraint_outcomes, provenance, budget_usage
     }

TwoWaysCCC.propose_reverse(residual_refs, exploration_policy)
  -> ProposalSet {
       alternative_questions, candidate_perspectives,
       candidate_relations, counterexample_tests,
       expected_information_gain, uncertainty, provenance
     }

TwoWaysCCC.validate(proposal_id, validation_contract)
  -> ValidationRecord {
       dataset_scope, baselines, outcomes, failure_modes,
       acceptance_decision, reviewer, provenance
     }

TwoWaysCCC.commit(proposal_id, authorization, cde_contract)
  -> VersionedDeltaRecord | RejectionRecord
```

`expected_information_gain` is optional and must declare how it is estimated; it is not a guaranteed measure of discovery value.

## 13. Candidate conformance tests

| ID | Test | Pass condition |
|---|---|---|
| CCC-T01 | Perspective type safety | Directional scores are not silently treated as mathematical metrics |
| CCC-T02 | Identity preservation | Similar records are not merged without identity contract satisfaction |
| CCC-T03 | Hard-constraint integrity | Reverse proposals do not silently relax eligibility constraints |
| CCC-T04 | Missingness propagation | Missing values remain visible in evidence and uncertainty |
| CCC-T05 | Reverse provenance | Every reverse proposal links to its originating residual(s) |
| CCC-T06 | Competing hypotheses | Contradictory explanations can coexist until adjudicated |
| CCC-T07 | No circular validation | Discovery and confirmatory test partitions are separated |
| CCC-T08 | Budget termination | Reverse inquiry stops under declared limits |
| CCC-T09 | Non-Euclidean entry | Relational-only entities can be searched without fake coordinates |
| CCC-T10 | Mapping directionality | A mapping is not assumed invertible or symmetric |
| CCC-T11 | Delta separation | World, epistemic, and operational changes are typed separately |
| CCC-T12 | Versioned rollback | Accepted structural changes are auditable and reversible where feasible |
| CCC-T13 | Baseline parity | Performance claims use comparable budgets and evaluation sets |
| CCC-T14 | Privacy boundary | Unauthorized data and inferred sensitive attributes are not exposed |

These are **proposed tests**, not a claim that a working implementation passes them.

## 14. Falsifiable research hypotheses

**H-CCC-01 — Residual traceability.** Compared with a forward-only retrieval pipeline, Two-Ways CCC produces more reproducible research trails for unresolved cases under a fixed annotation budget. **Measure:** trace completeness, independent reviewer agreement, and replay success.

**H-CCC-02 — Cross-perspective retrieval.** In datasets where relevant entities are not well captured by a single perspective, bounded cross-perspective proposals improve held-out recall or ranking quality at a fixed compute budget. **Measure:** recall@k, nDCG, latency, memory, and proposal overhead.

**H-CCC-03 — Useful question generation.** Reverse proposals increase the fraction of questions judged discriminating by blinded domain reviewers relative to generic anomaly prompts. **Measure:** blinded quality ratings and downstream information gain.

**H-CCC-04 — False discovery control.** Explicit residual qualification and negative controls reduce spurious descriptor promotion relative to a naive residual-to-feature pipeline. **Measure:** false discovery rate, calibration, and out-of-distribution degradation.

**H-CCC-05 — Structural evolution.** CDE-governed updates reduce invalid or irreproducible index/perspective changes relative to unversioned ad hoc adaptation. **Measure:** contract violations, rollback success, and reproducibility.

**H-CCC-06 — Efficiency boundary.** The two-way loop is not universally beneficial: on well-specified, stable, single-metric tasks, a simpler baseline may outperform it in cost and latency. **Measure:** break-even region over task complexity, drift, and residual frequency.

Negative findings are expected and should be published in the research trace.

## 15. Validation roadmap

**Phase 0 — Contract fixtures.** Build synthetic datasets with known identities, asymmetric relations, missing values, and deliberately incorrect perspectives. Verify CCC-T01–T14 where implementable.

**Phase 1 — Retrieval baselines.** Compare WE-HDT/CCC against SQL query plans, k-d/R-trees, graph indexes, and vector retrieval on tasks suited to each baseline. Report cases where WE-SIO is inferior.

**Phase 2 — Residual-to-question experiments.** Inject controlled model misspecification and confounding. Evaluate whether reverse proposals identify useful tests rather than merely adding features.

**Phase 3 — Versioned evolution.** Introduce changing data distributions; test accepted/rejected descriptor updates, provenance, rollback, and drift monitoring.

**Phase 4 — External domain review.** Run expert-led studies on realistic domains with appropriate privacy and safety controls. Separate exploratory findings from independently confirmed results.

Each phase should pre-register outcome metrics and resource budgets when practical.

## 16. Failure modes and counterexamples

1. **Residual from noise:** a random fluctuation triggers endless false hypothesis generation.
2. **Selection bias:** a discovered pattern disappears after cohort correction.
3. **Metric category error:** an asymmetric travel-time function is treated as a symmetric metric.
4. **Perspective leakage:** the new descriptor encodes the target label and inflates validation results.
5. **Search exclusion:** Euclidean prefiltering removes all relevant relational candidates.
6. **Identity collapse:** similarity-based matching merges distinct entities.
7. **Self-reinforcing loop:** the system uses its own proposals as independent evidence.
8. **Runaway adaptation:** repeated index changes consume more resources than they save.
9. **Concept drift:** a once-valid mapping becomes invalid under a changed context.
10. **Governance bypass:** a proposal is committed without approval or audit.

These counterexamples should be added to `research-trace/COUNTEREXAMPLE-REGISTRY.md` with stable IDs.

## 17. Integration with the broader SI program

- **WE-SIO-002:** identity and perspective descriptors supply the semantic types.
- **WE-SIO-003:** WE-HDT supplies hybrid candidate generation and structural addressing.
- **WE-SIO-004:** adaptive variable-intelligence blocks allocate capability and compute.
- **WE-SIO-005:** MLIU supplies the six operational interfaces.
- **WE-SIO-007:** residual-first scientific discovery deepens qualification and hypothesis testing.
- **WE-SIO-008:** perspective evolution governs candidate metric promotion.
- **WE-SIO-009 / CDE:** typed deltas and constrained structural transitions.
- **WE-SIO-011:** minimal kernels, conformance contracts, and definition evolution.
- **SIF:** WE-HDT is a candidate Localization/Addressing method; integration requires explicit contracts.
- **AQSI:** autonomous question generation can propose discriminating follow-ups, with validation gates.
- **UIERU / Relay:** hypotheses, residuals, and validated descriptors can move between agents and projects with provenance.
- **SSI:** self-modeling perspectives may use this architecture; no inference about subjective experience follows.

## 18. Research-trace obligations

This paper is a **relay piece**, not a declaration of completed discovery. Maintain the following companion records:

| File | Required trace |
|---|---|
| `HYPOTHESIS-REGISTRY.md` | H-CCC-01 through H-CCC-06, outcomes and revisions |
| `DEFINITION-REGISTRY.md` | CCC expansion, perspective, residual, mapping, and promotion definitions |
| `COUNTEREXAMPLE-REGISTRY.md` | Failure cases and boundary revisions |
| `DECISION-LOG.md` | Accepted/rejected schema and algorithm changes |
| `UNRESOLVED-RESIDUALS.md` | Open anomalies and missing evidence |
| `DISCUSSION-SYNTHESIS-2026-11-05.md` | Conceptual origin and initial decisions |

Suggested event schema:

```yaml
trace_id: string
source_question_or_residual: string
hypothesis_or_definition_version: string
proposed_action: string
supporting_evidence: []
contradicting_evidence: []
validation_contract: string
outcome: accepted | rejected | deferred | unresolved
next_questions: []
reviewer_and_timestamp: string
```

## 19. Open questions

1. What is the canonical expansion of CCC across earlier SI work, and what minimal invariant survives its variants?
2. When is reverse inquiry more effective than ordinary active learning or query expansion?
3. How can a candidate cross-perspective mapping be calibrated when domains and scales differ?
4. How should residual registries handle dependent observations and repeated tests?
5. Which query-planning policies avoid Euclidean-first exclusion errors?
6. What is the smallest MLIU interface that preserves meaningful cross-metric operations?
7. How should weak evidence be accumulated without creating self-confirming feedback?
8. What promotion threshold balances discovery with false-positive control?
9. Can structural relay preserve privacy and ownership while sharing useful residual abstractions?
10. How should the definition of “metric discovery” distinguish learning a distance function from discovering a new explanatory variable?
11. What are the strongest baseline systems and datasets for a fair comparison?
12. Under which conditions should the reverse loop be disabled entirely?

## 20. Conclusion

Two-Ways CCC is proposed as a **bounded, evidence-grounded coordination loop** joining forward entity retrieval to reverse inquiry driven by residuals and unresolved evidence. Its potential value lies not in claiming that every mismatch reveals a hidden metric, but in preserving and testing the chain from observation to question, competing hypothesis, validated descriptor, and controlled structural update.

The research standard is straightforward: **unknown is not zero; residual is not necessarily noise; and residual is not automatically a new law**. The system must be willing to conclude that a simpler baseline is better, that a proposal failed, or that the evidence remains insufficient. Those outcomes are part of Collective Learning.

---

### Figure integration guidance

- **Fig-006 — Two-Ways CCC Cross-Metric Discovery:** insert after §2.3.
- **Fig-007 — Residual-Driven Scientific Discovery Loop:** insert after §5.2.
- **Fig-003 — WE Hybrid Differential Tree:** optional cross-reference after §7; avoid duplicate full-size figures if already present in WE-SIO-003.

### Related documents

`WE-SIO-001`, `WE-SIO-002`, `WE-SIO-003`, `WE-SIO-004`, `WE-SIO-005`, `WE-SIO-007`, `WE-SIO-008`, `WE-SIO-009`, `WE-SIO-011`, and `SPEC-004-SI-Operations-and-Two-Ways-CCC-Interface.md`.

### License and citation

Intended repository license: Apache-2.0, subject to the repository's actual `LICENSE` file. Cite the eventual versioned WE-SIO release and DOI once issued; **no DOI is asserted in this draft**.
