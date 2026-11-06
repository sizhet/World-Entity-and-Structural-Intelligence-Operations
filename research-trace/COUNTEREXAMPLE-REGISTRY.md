# WE-SIO Counterexample Registry

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Release:** v0.1.0 · Hypothesis / Research Framework  
**Registry revision:** CER-0.1.0 · 2026-11-05  
**Research attribution:** Sizhe Tan & GPT-Obot  
**Repository location:** `research-trace/COUNTEREXAMPLE-REGISTRY.md`  
**Status:** Proposed challenges; no empirical result or implementation validation implied

> **Principle:** A counterexample is a test of the boundary of a claim, not a nuisance to be erased. Preserve the failed claim, the conditions that exposed it, and the repair or unresolved residual.

## 1. Purpose and evidence discipline

This registry collects **candidate counterexamples, adversarial cases, boundary conditions, and failure modes** across the WE-SIO research program. Its role is to challenge definitions, architecture assumptions, algorithmic guarantees, scientific-discovery claims, and governance policies. The entries are **test designs or conceptual counterexamples**, not claims that WE-SIO code has been executed or that a named experiment has failed.

A counterexample may be (a) a logically decisive contradiction of a universal statement, (b) a synthetic test input demonstrating an invalid assumption, (c) an empirical falsification candidate requiring measurement, or (d) an operational safety hazard. These categories must not be conflated. A failure in one domain does not refute a narrower, explicitly scoped claim in another domain.

### 1.1 Status and type

- **Type L — Logical:** contradiction under the stated premises; may be settled by reasoning and formal proof.
- **Type S — Synthetic:** constructed data/state for reproducible contract tests.
- **Type E — Empirical:** a potential negative outcome to be measured against a baseline.
- **Type G — Governance:** safety, authorization, privacy, provenance or misuse boundary.
- **State:** `Proposed`, `Specified`, `Reproduced`, `Resolved`, `Unresolved`, `Superseded`.
- **Default:** `Proposed / E0`; the present document does not assert executed results.

Every item uses an immutable `CE-WE-###` identifier. The shorthand links to `DEF-###` and `WEH-###` refer to `DEFINITION-REGISTRY.md` and `HYPOTHESIS-REGISTRY.md`; slash-separated identifiers denote distinct IDs, not an interval.

## 2. Counterexample master index

| ID | Domain | Boundary case | Primary cross-reference | State |
|---|---|---|---|---|
| CE-WE-001 | Entity identity | Two distinct people share name, birthdate, and location | DEF-001/002/003 | Proposed |
| CE-WE-002 | Entity identity | One person has two source-local patient identifiers | DEF-002 | Proposed |
| CE-WE-003 | Entity identity | One database row denotes a clinical encounter, not the patient | DEF-001/003 | Proposed |
| CE-WE-004 | Perspective semantics | A numerical age column is called a metric space | DEF-004/005/006 | Proposed |
| CE-WE-005 | Perspective semantics | A directional trust score is treated as symmetric distance | DEF-005/006/007 | Proposed |
| CE-WE-006 | Perspective semantics | Missing observation is encoded as zero | DEF-006/008/009 | Proposed |
| CE-WE-007 | Perspective semantics | Two measurement values use incompatible units | DEF-004/006 | Proposed |
| CE-WE-008 | Perspective semantics | An abstract mathematical object lacks physical coordinates | DEF-001/010 | Proposed |
| CE-WE-009 | WE-HDT indexing | Candidate pruning excludes a true nearest neighbor | DEF-010/011 | Proposed |
| CE-WE-010 | WE-HDT indexing | Highly skewed data makes block boundaries unstable | DEF-011/012 | Proposed |
| CE-WE-011 | WE-HDT indexing | k-d tree with adaptive splitting already handles variable regions | DEF-011/012 | Proposed |
| CE-WE-012 | WE-HDT indexing | High-dimensional concentration defeats spatial pruning | DEF-010/011 | Proposed |
| CE-WE-013 | WE-HDT indexing | An index is updated without matching entity-version snapshot | DEF-002/010/013 | Proposed |
| CE-WE-014 | WE-HDT indexing | Physical leaf is mistaken for semantic metric leaf | DEF-013/014 | Proposed |
| CE-WE-015 | Adaptive intelligence | Every metric leaf spawns a heavyweight autonomous agent | DEF-014/015 | Proposed |
| CE-WE-016 | Adaptive intelligence | An AVIB split improves local fit but degrades global accuracy | DEF-012/014/016 | Proposed |
| CE-WE-017 | Two-Ways CCC | Reverse questioning loops back to its own unverified claim | DEF-016/017 | Proposed |
| CE-WE-018 | Two-Ways CCC | Cross-perspective join conflates similar labels | DEF-004/016 | Proposed |
| CE-WE-019 | Residual discovery | An outlier is a sensor fault, not a new law | DEF-017/018 | Proposed |
| CE-WE-020 | Residual discovery | A treatment subgroup difference is confounded by severity | DEF-017/019 | Proposed |
| CE-WE-021 | Residual discovery | Same dataset generates and validates hypothesis | DEF-018/019 | Proposed |
| CE-WE-022 | Residual discovery | Rare subgroup is suppressed by global aggregate score | DEF-017/019 | Proposed |
| CE-WE-023 | Metric generation | Learned dissimilarity violates triangle inequality | DEF-005/019 | Proposed |
| CE-WE-024 | Metric generation | Generated perspective encodes protected or proxy information | DEF-004/019/021 | Proposed |
| CE-WE-025 | Delta semantics | Database correction is labeled real-world change | DEF-022/023 | Proposed |
| CE-WE-026 | Delta semantics | Undo of an index operation is called undo of a real event | DEF-022/023 | Proposed |
| CE-WE-027 | CDE boundary | Chess player legally repeats a move pattern | DEF-024/025/026 | Proposed |
| CE-WE-028 | CDE boundary | Identical board placement has different castling rights | DEF-022/024/025 | Proposed |
| CE-WE-029 | CDE boundary | Transposition and cycle are conflated | DEF-024/025 | Proposed |
| CE-WE-030 | CDE boundary | Unbounded delta generator never terminates | DEF-024/025/026 | Proposed |
| CE-WE-031 | SIF localization | A search method is renamed Localization without addressing contract | DEF-010/032 | Proposed |
| CE-WE-032 | Multi-agent relay | Five agents copy one source and vote unanimously | DEF-029/030/031 | Proposed |
| CE-WE-033 | Multi-agent relay | Competitive agents optimize proxy score by hiding failures | DEF-030/031 | Proposed |
| CE-WE-034 | Multi-agent relay | Repeated execution accumulates only duplicate traces | DEF-030/031 | Proposed |
| CE-WE-035 | Self-modeling | System predicts itself accurately but has no subjective evidence | DEF-027/028 | Proposed |
| CE-WE-036 | Self-modeling | Self-report changes when prompt wording changes | DEF-002/027 | Proposed |
| CE-WE-037 | Self-modeling | Self-model update improves confidence but worsens calibration | DEF-027/028 | Proposed |
| CE-WE-038 | Definition evolution | World Entity defined as everything whatsoever | DEF-001/020/021 | Proposed |
| CE-WE-039 | Definition evolution | Definition narrowed to exclude inconvenient counterexample | DEF-020/021 | Proposed |
| CE-WE-040 | Governance | An automated clinical discovery output is treated as treatment advice | DEF-018/019/021 | Proposed |

---

## 3. Detailed counterexample records

### CE-WE-001 — Two distinct people share name, birthdate, and location

- **Domain / type:** Entity identity; S/E (classification provisional).
- **Challenge:** Similarity-based entity merge creates false identity.
- **Minimal scenario:** Two distinct people share name, birthdate, and location. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-001/002/003`. **Hypothesis links:** `WEH-001/028`.
- **Primary research source:** `CASE-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Use scoped identifiers and evidence-backed resolution; abstain on ambiguity.
- **Conformance or falsification probe:** Measure Identity precision, false-merge rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-002 — One person has two source-local patient identifiers

- **Domain / type:** Entity identity; S/E (classification provisional).
- **Challenge:** Primary-key equality fails to unify cross-source references.
- **Minimal scenario:** One person has two source-local patient identifiers. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-002`. **Hypothesis links:** `WEH-001/028`.
- **Primary research source:** `CASE-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Separate record identity from entity resolution.
- **Conformance or falsification probe:** Measure False-split rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-003 — One database row denotes a clinical encounter, not the patient

- **Domain / type:** Entity identity; S/E (classification provisional).
- **Challenge:** Row-as-entity assumption changes ontological type.
- **Minimal scenario:** One database row denotes a clinical encounter, not the patient. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-001/003`. **Hypothesis links:** `WEH-028`.
- **Primary research source:** `CASE-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Declare entity kind and event-to-person relationship.
- **Conformance or falsification probe:** Measure Type conformance; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-004 — A numerical age column is called a metric space

- **Domain / type:** Perspective semantics; S/E (classification provisional).
- **Challenge:** Scalar measurement is mistaken for a distance function.
- **Minimal scenario:** A numerical age column is called a metric space. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-004/005/006`. **Hypothesis links:** `WEH-002/028`.
- **Primary research source:** `CASE-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Require explicit distance operator and axioms.
- **Conformance or falsification probe:** Measure Metric-axiom tests; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-005 — A directional trust score is treated as symmetric distance

- **Domain / type:** Perspective semantics; S/E (classification provisional).
- **Challenge:** d(A,B) need not equal d(B,A).
- **Minimal scenario:** A directional trust score is treated as symmetric distance. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-005/006/007`. **Hypothesis links:** `WEH-002`.
- **Primary research source:** `EXT-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Type directional relations separately.
- **Conformance or falsification probe:** Measure Symmetry violation count; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-006 — Missing observation is encoded as zero

- **Domain / type:** Perspective semantics; S/E (classification provisional).
- **Challenge:** Unknown conflated with measured zero.
- **Minimal scenario:** Missing observation is encoded as zero. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-006/008/009`. **Hypothesis links:** `WEH-002/009`.
- **Primary research source:** `CASE-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Represent missingness and uncertainty explicitly.
- **Conformance or falsification probe:** Measure Missingness integrity; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-007 — Two measurement values use incompatible units

- **Domain / type:** Perspective semantics; S/E (classification provisional).
- **Challenge:** Cross-perspective aggregation yields meaningless comparisons.
- **Minimal scenario:** Two measurement values use incompatible units. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-004/006`. **Hypothesis links:** `WEH-002/012`.
- **Primary research source:** `SPEC-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Unit-aware typed contracts and conversions.
- **Conformance or falsification probe:** Measure Unit conformance; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-008 — An abstract mathematical object lacks physical coordinates

- **Domain / type:** Perspective semantics; S/E (classification provisional).
- **Challenge:** Euclidean-first localization rejects valid WE.
- **Minimal scenario:** An abstract mathematical object lacks physical coordinates. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-001/010`. **Hypothesis links:** `WEH-003/016`.
- **Primary research source:** `EXT-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Allow non-Euclidean and relation-first routes.
- **Conformance or falsification probe:** Measure Recall by entity kind; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-009 — Candidate pruning excludes a true nearest neighbor

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Two-phase pipeline cannot recover omitted result.
- **Minimal scenario:** Candidate pruning excludes a true nearest neighbor. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-010/011`. **Hypothesis links:** `WEH-003/004`.
- **Primary research source:** `CASE-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Prove conservative bounds or declare approximate recall.
- **Conformance or falsification probe:** Measure Exact recall / approximation bound; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-010 — Highly skewed data makes block boundaries unstable

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Repeated split/merge costs exceed lookup benefit.
- **Minimal scenario:** Highly skewed data makes block boundaries unstable. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-011/012`. **Hypothesis links:** `WEH-004/005`.
- **Primary research source:** `CASE-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Hysteresis and amortized update accounting.
- **Conformance or falsification probe:** Measure Update cost, oscillations; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-011 — k-d tree with adaptive splitting already handles variable regions

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Variable-sized partition alone is not a novel advantage.
- **Minimal scenario:** k-d tree with adaptive splitting already handles variable regions. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-011/012`. **Hypothesis links:** `WEH-004/005`.
- **Primary research source:** `CASE-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Compare against tuned adaptive k-d tree.
- **Conformance or falsification probe:** Measure Latency-memory Pareto frontier; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-012 — High-dimensional concentration defeats spatial pruning

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Euclidean routing approaches brute-force cost.
- **Minimal scenario:** High-dimensional concentration defeats spatial pruning. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-010/011`. **Hypothesis links:** `WEH-003/004`.
- **Primary research source:** `CASE-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Measure dimensionality and switch route or abstain.
- **Conformance or falsification probe:** Measure Visited fraction, latency; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-013 — An index is updated without matching entity-version snapshot

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Stale candidate points to wrong or obsolete record.
- **Minimal scenario:** An index is updated without matching entity-version snapshot. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-002/010/013`. **Hypothesis links:** `WEH-003`.
- **Primary research source:** `EXT-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Snapshot/version consistency and invalidation.
- **Conformance or falsification probe:** Measure Stale-read rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-014 — Physical leaf is mistaken for semantic metric leaf

- **Domain / type:** WE-HDT indexing; S/E (classification provisional).
- **Challenge:** Rebalancing unexpectedly changes intelligence ownership.
- **Minimal scenario:** Physical leaf is mistaken for semantic metric leaf. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-013/014`. **Hypothesis links:** `WEH-006`.
- **Primary research source:** `WE-SIO-005` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Separate logical MLIU address from physical node.
- **Conformance or falsification probe:** Measure Rebalance stability; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-015 — Every metric leaf spawns a heavyweight autonomous agent

- **Domain / type:** Adaptive intelligence; S/E (classification provisional).
- **Challenge:** Resource overhead dominates search and reasoning.
- **Minimal scenario:** Every metric leaf spawns a heavyweight autonomous agent. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-014/015`. **Hypothesis links:** `WEH-006/007`.
- **Primary research source:** `WE-SIO-005` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Budgeted, lazy or shared intelligence services.
- **Conformance or falsification probe:** Measure Cost per useful operation; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-016 — An AVIB split improves local fit but degrades global accuracy

- **Domain / type:** Adaptive intelligence; S/E (classification provisional).
- **Challenge:** Local scoring misaligns with end-to-end objective.
- **Minimal scenario:** An AVIB split improves local fit but degrades global accuracy. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-012/014/016`. **Hypothesis links:** `WEH-005/007`.
- **Primary research source:** `WE-SIO-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Global guardrails, rollback, held-out evaluation.
- **Conformance or falsification probe:** Measure Global utility regression; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-017 — Reverse questioning loops back to its own unverified claim

- **Domain / type:** Two-Ways CCC; S/E (classification provisional).
- **Challenge:** Self-reinforcing feedback produces spurious confidence.
- **Minimal scenario:** Reverse questioning loops back to its own unverified claim. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-016/017`. **Hypothesis links:** `WEH-008/010`.
- **Primary research source:** `WE-SIO-006` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Evidence lineage, independent checks, loop limits.
- **Conformance or falsification probe:** Measure Circular-support rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-018 — Cross-perspective join conflates similar labels

- **Domain / type:** Two-Ways CCC; S/E (classification provisional).
- **Challenge:** Inference silently crosses incompatible semantic types.
- **Minimal scenario:** Cross-perspective join conflates similar labels. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-004/016`. **Hypothesis links:** `WEH-008/012`.
- **Primary research source:** `WE-SIO-006` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Typed mapping and explicit compatibility contract.
- **Conformance or falsification probe:** Measure Invalid-join rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-019 — An outlier is a sensor fault, not a new law

- **Domain / type:** Residual discovery; S/E (classification provisional).
- **Challenge:** Residual-triggered discovery overfits noise.
- **Minimal scenario:** An outlier is a sensor fault, not a new law. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-017/018`. **Hypothesis links:** `WEH-009/011`.
- **Primary research source:** `CASE-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Data-quality gate before hypothesis promotion.
- **Conformance or falsification probe:** Measure False-discovery rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-020 — A treatment subgroup difference is confounded by severity

- **Domain / type:** Residual discovery; S/E (classification provisional).
- **Challenge:** Observational association is misread as causal response.
- **Minimal scenario:** A treatment subgroup difference is confounded by severity. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-017/019`. **Hypothesis links:** `WEH-009/029`.
- **Primary research source:** `CASE-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Causal identification or explicit noncausal labeling.
- **Conformance or falsification probe:** Measure Bias / confounding sensitivity; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-021 — Same dataset generates and validates hypothesis

- **Domain / type:** Residual discovery; S/E (classification provisional).
- **Challenge:** Data leakage inflates apparent discovery quality.
- **Minimal scenario:** Same dataset generates and validates hypothesis. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-018/019`. **Hypothesis links:** `WEH-010/011`.
- **Primary research source:** `EXT-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Independent holdout, preregistration, external replication.
- **Conformance or falsification probe:** Measure Out-of-sample replication; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-022 — Rare subgroup is suppressed by global aggregate score

- **Domain / type:** Residual discovery; S/E (classification provisional).
- **Challenge:** High average performance hides consequential residual.
- **Minimal scenario:** Rare subgroup is suppressed by global aggregate score. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-017/019`. **Hypothesis links:** `WEH-009/013`.
- **Primary research source:** `CASE-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Stratified evaluation and subgroup uncertainty.
- **Conformance or falsification probe:** Measure Worst-group error; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-023 — Learned dissimilarity violates triangle inequality

- **Domain / type:** Metric generation; S/E (classification provisional).
- **Challenge:** Unqualified metric claim breaks metric-tree bounds.
- **Minimal scenario:** Learned dissimilarity violates triangle inequality. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-005/019`. **Hypothesis links:** `WEH-012/013`.
- **Primary research source:** `EXT-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Classify as dissimilarity or prove metric properties.
- **Conformance or falsification probe:** Measure Triangle-inequality tests; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-024 — Generated perspective encodes protected or proxy information

- **Domain / type:** Metric generation; G (classification provisional).
- **Challenge:** Predictive gain creates privacy or fairness harm.
- **Minimal scenario:** Generated perspective encodes protected or proxy information. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-004/019/021`. **Hypothesis links:** `WEH-012/030`.
- **Primary research source:** `EXT-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Governance review, minimization and restricted use.
- **Conformance or falsification probe:** Measure Privacy/fairness audit; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-025 — Database correction is labeled real-world change

- **Domain / type:** Delta semantics; S/E (classification provisional).
- **Challenge:** Observation delta conflated with world delta.
- **Minimal scenario:** Database correction is labeled real-world change. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-022/023`. **Hypothesis links:** `WEH-014`.
- **Primary research source:** `WE-SIO-009` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Typed delta provenance and causal status.
- **Conformance or falsification probe:** Measure Delta-type conformance; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-026 — Undo of an index operation is called undo of a real event

- **Domain / type:** Delta semantics; S/E (classification provisional).
- **Challenge:** Operational rollback cannot reverse physical history.
- **Minimal scenario:** Undo of an index operation is called undo of a real event. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-022/023`. **Hypothesis links:** `WEH-014`.
- **Primary research source:** `WE-SIO-009` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Separate compensating records and world actions.
- **Conformance or falsification probe:** Measure Rollback semantics; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-027 — Chess player legally repeats a move pattern

- **Domain / type:** CDE boundary; L (classification provisional).
- **Challenge:** Universal No-Delta-Reuse rule rejects valid paths.
- **Minimal scenario:** Chess player legally repeats a move pattern. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-024/025/026`. **Hypothesis links:** `WEH-015`.
- **Primary research source:** `CASE-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Treat no-reuse as optional policy, not kernel axiom.
- **Conformance or falsification probe:** Measure Legal-path coverage; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-028 — Identical board placement has different castling rights

- **Domain / type:** CDE boundary; S/E (classification provisional).
- **Challenge:** State equality by piece placement is unsound.
- **Minimal scenario:** Identical board placement has different castling rights. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-022/024/025`. **Hypothesis links:** `WEH-015`.
- **Primary research source:** `CASE-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Include rights, turn, en passant, counters as applicable.
- **Conformance or falsification probe:** Measure State-key conformance; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-029 — Transposition and cycle are conflated

- **Domain / type:** CDE boundary; S/E (classification provisional).
- **Challenge:** Global visited-set incorrectly prunes valid continuation.
- **Minimal scenario:** Transposition and cycle are conflated. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-024/025`. **Hypothesis links:** `WEH-015/017`.
- **Primary research source:** `CASE-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Separate path repetition from transposition cache.
- **Conformance or falsification probe:** Measure Search completeness; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-030 — Unbounded delta generator never terminates

- **Domain / type:** CDE boundary; S/E (classification provisional).
- **Challenge:** Open-ended evolution lacks resource and termination policy.
- **Minimal scenario:** Unbounded delta generator never terminates. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-024/025/026`. **Hypothesis links:** `WEH-015/017`.
- **Primary research source:** `CASE-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Bounded budget, stopping criteria, explicit leftovers.
- **Conformance or falsification probe:** Measure Termination / budget; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-031 — A search method is renamed Localization without addressing contract

- **Domain / type:** SIF localization; S/E (classification provisional).
- **Challenge:** Terminology adds no interoperable capability.
- **Minimal scenario:** A search method is renamed Localization without addressing contract. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-010/032`. **Hypothesis links:** `WEH-016/017`.
- **Primary research source:** `EXT-001` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Specify request, evidence, guarantee, failure modes.
- **Conformance or falsification probe:** Measure Interoperability tests; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-032 — Five agents copy one source and vote unanimously

- **Domain / type:** Multi-agent relay; S/E (classification provisional).
- **Challenge:** Agreement misrepresented as independent corroboration.
- **Minimal scenario:** Five agents copy one source and vote unanimously. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-029/030/031`. **Hypothesis links:** `WEH-018/019`.
- **Primary research source:** `EXT-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Track evidence dependence and source lineage.
- **Conformance or falsification probe:** Measure Effective independent evidence; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-033 — Competitive agents optimize proxy score by hiding failures

- **Domain / type:** Multi-agent relay; S/E (classification provisional).
- **Challenge:** Relay increases apparent success while harming validity.
- **Minimal scenario:** Competitive agents optimize proxy score by hiding failures. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-030/031`. **Hypothesis links:** `WEH-019/020`.
- **Primary research source:** `EXT-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Adversarial audit, negative-result preservation.
- **Conformance or falsification probe:** Measure Hidden-failure rate; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-034 — Repeated execution accumulates only duplicate traces

- **Domain / type:** Multi-agent relay; S/E (classification provisional).
- **Challenge:** Volume grows without transferable learning.
- **Minimal scenario:** Repeated execution accumulates only duplicate traces. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-030/031`. **Hypothesis links:** `WEH-020/021`.
- **Primary research source:** `EXT-002` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Deduplicate and measure reusable improvement.
- **Conformance or falsification probe:** Measure Transfer gain per cost; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-035 — System predicts itself accurately but has no subjective evidence

- **Domain / type:** Self-modeling; S/E (classification provisional).
- **Challenge:** Functional self-model falsely taken as consciousness proof.
- **Minimal scenario:** System predicts itself accurately but has no subjective evidence. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-027/028`. **Hypothesis links:** `WEH-022/023`.
- **Primary research source:** `CASE-005` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Separate functional criteria from phenomenology.
- **Conformance or falsification probe:** Measure Claim-boundary audit; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-036 — Self-report changes when prompt wording changes

- **Domain / type:** Self-modeling; S/E (classification provisional).
- **Challenge:** Narrative self-description mistaken for stable identity.
- **Minimal scenario:** Self-report changes when prompt wording changes. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-002/027`. **Hypothesis links:** `WEH-022/024`.
- **Primary research source:** `EXT-004` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Cross-context tests, calibrated uncertainty.
- **Conformance or falsification probe:** Measure Self-model stability; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-037 — Self-model update improves confidence but worsens calibration

- **Domain / type:** Self-modeling; S/E (classification provisional).
- **Challenge:** Self-referential learning rewards self-flattery.
- **Minimal scenario:** Self-model update improves confidence but worsens calibration. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-027/028`. **Hypothesis links:** `WEH-023/025`.
- **Primary research source:** `CASE-005` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** External outcome checks, calibration loss.
- **Conformance or falsification probe:** Measure Calibration / regret; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-038 — World Entity defined as everything whatsoever

- **Domain / type:** Definition evolution; L (classification provisional).
- **Challenge:** Universal definition becomes non-discriminating.
- **Minimal scenario:** World Entity defined as everything whatsoever. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-001/020/021`. **Hypothesis links:** `WEH-026/027`.
- **Primary research source:** `WE-SIO-011` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Require scope, type, identity and operational tests.
- **Conformance or falsification probe:** Measure Definition discrimination; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-039 — Definition narrowed to exclude inconvenient counterexample

- **Domain / type:** Definition evolution; S/E (classification provisional).
- **Challenge:** Revision protects claim rather than improves model.
- **Minimal scenario:** Definition narrowed to exclude inconvenient counterexample. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-020/021`. **Hypothesis links:** `WEH-026/027`.
- **Primary research source:** `WE-SIO-011` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Record failed scope and regression suite.
- **Conformance or falsification probe:** Measure Revision audit; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

### CE-WE-040 — An automated clinical discovery output is treated as treatment advice

- **Domain / type:** Governance; G (classification provisional).
- **Challenge:** Research hypothesis crosses into clinical decision.
- **Minimal scenario:** An automated clinical discovery output is treated as treatment advice. Construct the smallest two-entity, two-state, or two-perspective fixture that isolates this failure; add a larger workload only when evaluating performance or robustness.
- **Claim at risk:** A universal or unconditional version of the associated design claim. The narrower, typed, scoped claim may remain valid.
- **Definition links:** `DEF-018/019/021`. **Hypothesis links:** `WEH-029/030`.
- **Primary research source:** `CASE-003` (research-file shorthand; verify exact path when linking in repository).
- **Proposed repair / boundary:** Human oversight, validation and nonclinical use boundary.
- **Conformance or falsification probe:** Measure Unsafe-deployment incidents; compare against an explicit baseline and record any false positive, false negative, or abstention.
- **State / evidence:** Proposed / E0. **Residual:** no executed test or independent replication attached.

---

## 4. Cross-cutting lessons and non-equivalences

1. **Identity ≠ similarity ≠ source record key.** Even perfect agreement on observed attributes does not establish identity without an identity policy and evidence.
2. **Metric ≠ measurement ≠ similarity ≠ relation.** Numeric output alone does not confer metric axioms or safe pruning guarantees.
3. **Logical intelligence unit ≠ physical tree leaf.** Index rebalancing must not silently redefine the semantics of a perspective or entity.
4. **Candidate generation ≠ verified answer.** Exact search requires sound bounds or complete candidate coverage; approximate search must report its approximation contract.
5. **Residual ≠ discovery ≠ causal mechanism.** A discrepancy may originate from noise, leakage, confounding, model error or genuine structural novelty.
6. **World Delta ≠ Observation Delta ≠ Knowledge Delta ≠ Structural Delta.** These change categories have different causal and rollback semantics.
7. **CDE kernel ≠ D-BTP-specific no-reuse policy.** Legal chess cycles show why policy must be parameterized.
8. **Multi-agent agreement ≠ independent evidence.** Shared sources and correlated failure modes must be represented.
9. **Self-model ≠ subjective experience.** Functional self-representation is testable without settling phenomenology.
10. **Definition extension ≠ universal truth.** New generality must retain discriminating invariants and regression tests.

## 5. Minimal counterexample-to-revision protocol

**CE-0 Intake.** Record the original claim verbatim, its quantifiers, assumptions, date and version. Assign an immutable CE ID and source pointer.

**CE-1 Reproduce or reason.** For logical cases, give a proof sketch; for executable cases, supply minimal fixture, seed, environment, expected and observed results. Never claim reproduction without an artifact.

**CE-2 Classify.** Distinguish a contract violation, implementation defect, missing assumption, empirical tradeoff, false discovery, and governance violation.

**CE-3 Scope the impact.** Link affected `DEF-###`, `WEH-###`, specifications, case studies and SIF interfaces. Identify whether the claim is universal or conditional.

**CE-4 Propose the smallest repair.** Narrow the domain, introduce a typed interface, revise an invariant, add an explicit failure return, or reject the claim. Avoid untestable exception clauses.

**CE-5 Regression.** Add a positive control and a negative control. Re-run prior conformance cases and report tradeoffs introduced by the repair.

**CE-6 Decide and relay.** Record accepted/rejected/suspended outcome, reviewer, evidence grade, superseded versions and explicit leftovers in `DECISION-LOG.md` and `UNRESOLVED-RESIDUALS.md`.

### 5.1 Executable record template

```yaml
counterexample_id: CE-WE-XXX
claim_under_test: ""
claim_version: ""
type: logical | synthetic | empirical | governance
state: proposed
preconditions: []
fixture_or_dataset: null
expected_contract_behavior: null
observed_behavior: null   # never populate before execution
baseline: null
seed_and_environment: null
evidence_artifacts: []
linked_definitions: []
linked_hypotheses: []
proposed_repair: null
regression_tests: []
review_decision: pending
explicit_leftovers: []
```

## 6. Priority stress-test portfolio

| Priority | Counterexamples | Why first | Exit criterion |
|---|---|---|---|
| P0 | CE-WE-001–008, 009, 017, 023, 025–029, 035 | Foundational semantics, correctness and CDE boundaries | Deterministic fixtures and explicit guarantees |
| P0 | CE-WE-019–021, 040 | Scientific evidence and clinical safety | Data quality, leakage and deployment boundaries documented |
| P1 | CE-WE-010–016 | Index and intelligence cost tradeoffs | Matched benchmarks and resource accounting |
| P1 | CE-WE-030–034 | SIF and multi-agent interface validity | Contract and independent-evidence tests |
| P1 | CE-WE-036–039 | Self-model and definition evolution | Calibration and regression tests |
| P2 | All remaining cases | Broader robustness and generalization | Independent replication where feasible |

*Priorities are proposed, not approved deployment gates. A safety-critical use case may elevate any item to P0.*

## 7. Links to research documents

- `DEFINITION-REGISTRY.md`: authoritative conceptual cross-references and definition versions.
- `HYPOTHESIS-REGISTRY.md`: falsifiable claims and evidence-grade transitions.
- `DISCUSSION-SYNTHESIS-2026-11-05.md`: research trajectory and original questions, subject to source-verification limits.
- `../cases/CASE-001-SQL-Columns-to-WE-Perspective-Indices.md`: identity, SQL and perspective mapping.
- `../cases/CASE-002-Variable-Size-Blocks-vs-KD-Tree.md`: indexing, exactness and performance baselines.
- `../cases/CASE-003-Clinical-Treatment-Response-Residuals.md`: clinical research and causal caution.
- `../cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md`: path memory and repeat-state semantics.
- `../cases/CASE-005-Multi-Perspective-Self-Modeling-Entity.md`: self-modeling calibration and boundaries.
- `../extensions/EXT-001-WE-HDT-as-an-SIF-Localization-Pillar.md`: localization contracts.
- `../extensions/EXT-002-Multi-Agent-WE-SI-and-Collective-Learning.md`: collective relay and correlated evidence.
- `../extensions/EXT-003-Structural-Scientific-Discovery-and-Metric-Generation.md`: discovery and metric validation.
- `../extensions/EXT-004-Self-Referential-World-Entity-and-Subjective-SI.md`: self-reference and SSI boundaries.

## 8. Explicit leftovers

1. Formalize minimal executable fixtures for every logical and synthetic CE entry.
2. Audit all `DEF` and `WEH` cross-references against final repository versions before release.
3. Replace research-file shorthand in detailed records with canonical relative links.
4. Define proof obligations for WE-HDT exact pruning and versioned candidate validity.
5. Establish matched k-d tree, brute-force, and adaptive-block benchmark protocols.
6. Determine CDE's distinguishing operational value beyond a generic state-transition formalism.
7. Validate scientific discovery gains against leakage-safe and causally appropriate baselines.
8. Define privacy and authorization policy for cross-agent evidence relay.
9. Establish calibrated self-model baselines without consciousness claims.
10. Record real failed tests and external replications separately from proposed counterexamples.

## 9. Release discipline

A counterexample must never be deleted merely because a design was revised. Mark it `Resolved` or `Superseded`, attach the revised claim and regression evidence, and retain the original. A failed hypothesis can still be a valuable relay result. At v0.1.0, **all CE entries are proposed stress tests and boundary analyses, not verified empirical findings**.

---

**Research attribution:** Sizhe Tan & GPT-Obot  
**Version:** v0.1.0  
**License intention:** Apache-2.0, subject to repository license file.  
**Next research-trace artifact:** `DECISION-LOG.md`.
