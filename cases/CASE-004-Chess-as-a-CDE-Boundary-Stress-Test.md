# CASE-004 — Chess as a CDE Boundary Stress Test

**Project:** World Entity and Structural Intelligence Operations (WE-SIO)  
**Version:** v0.1.0 — Research case / definition stress test  
**Status:** Proposed contracts and falsifiable tests; not an implementation or empirical validation  
**Related work:** WE-SIO-009, WE-SIO-011, SPEC-006; Constrained Delta Evolution (CDE); Chess Strategic Structural Intelligence Laboratory (Chess-SSIL)

## Abstract

Chess is a deliberately adversarial boundary case for Constrained Delta Evolution (CDE). Unlike a monotonic search in which a particular delta is never reused along a path, chess allows recurring move types, repeated positions, reversible moves, competing agents, and cycles. The game is nevertheless finite in its legal state description and governed by explicit rules. This makes it a useful setting for distinguishing the **minimal CDE semantic kernel** from optional, application-specific policies inherited from Dynamic Bucket Tree of Permutation (D-BTP). This case proposes a typed chess state, legal transition contract, path-memory policies, termination and draw handling, adversarial decision operators, and a conformance-first experimental program. It also examines how WE-SIO's perspective descriptors, residuals, and research trace can document failures of overgeneralized definitions. No performance advantage or general theorem of CDE is claimed.

## 1. Research motivation

D-BTP-inspired search can impose a **no-delta-reuse-on-a-path** restriction to prevent revisiting previously consumed choices. That restriction can be appropriate for assignment, permutation, or inventory-constrained problems. However, treating it as a universal CDE axiom would exclude ordinary chess play: a knight may move out and back, the same move pattern may occur repeatedly, and a legal position may recur.

The central research question is therefore:

> Which aspects of delta evolution remain invariant across constrained search problems, and which are optional policies determined by the application?

This case is a **definition stress test**, not evidence that chess is the canonical application of CDE or that CDE improves on existing chess engines.

## 2. Minimal CDE kernel and application contracts

A candidate minimal kernel comprises:

1. **State** `S`: a typed representation of the current system.
2. **Delta** `δ`: a proposed change or action.
3. **Applicability** `A(S, δ, C)`: whether the delta is permitted under constraints `C`.
4. **Transition** `T(S, δ) -> S'`: a well-defined state update when applicable.
5. **Evolution policy** `Π`: a method for selecting, evaluating, or generating candidate deltas.

For deterministic chess rules, `T` can be a partial function. In a more general nondeterministic setting it may instead be a transition relation or distribution. A kernel this small risks collapsing into a generic state-transition model; CDE must therefore demonstrate additional explanatory or operational value through typed contracts, compositional delta handling, controlled search, traceability, or reusable evolution policies.

**Optional application contracts** include path-memory rules, cycle policy, branch generation, resource budget, stopping conditions, evaluation perspectives, multi-agent/adversarial choice, and rollback. These are not all mandatory kernel axioms.

## 3. Chess state model

A chess state must contain enough information to determine legal moves and applicable game outcomes. A board diagram alone is insufficient.

```text
ChessState {
  board: PiecePlacement,
  sideToMove: White | Black,
  castlingRights: Set<CastlingRight>,
  enPassantTarget: Square | None,
  halfmoveClock: NonnegativeInteger,
  fullmoveNumber: PositiveInteger,
  repetitionHistory: PositionKeyHistory,
  rulesetVersion: Identifier,
  optionalSearchMetadata: SearchMetadata
}
```

The history used for repetition and draw adjudication may be external to the current-position key but must remain available to a full game-state evaluator. Repetition equivalence depends on the board, side to move, castling rights, and relevant en-passant rights; it is not the same as equality of every field in `ChessState`.

The chess game state is a **representation of a rule-governed game**, not a physical World Entity. WE-SIO may represent a game, player, move, or board state as an entity or event, but should not conflate a game-state encoding with the real-world identity of a player.

### 3.1 Delta contract

```text
ChessDelta {
  from: Square,
  to: Square,
  promotion: PieceType | None,
  specialMove: Normal | Castle | EnPassant | Promotion,
  actor: White | Black,
  sourceStateVersion: Identifier
}
```

`Applicable(S, δ)` requires the correct side to move, valid piece movement, satisfaction of special-move preconditions, and absence of self-check in the resulting position. Applying a move must update all state fields, including castling rights, en-passant target, move clocks, and repetition context. A move leaving the moving side's king in check is illegal.

### 3.2 State identity and transpositions

Distinguish:

- **Game-history identity:** two move sequences can be different histories even when they reach an equivalent position.
- **Position equivalence:** sufficient for many transposition-table comparisons, with rule-sensitive fields included.
- **Search-node identity:** includes search depth, perspective, and evaluation context where relevant.
- **World Entity identity:** if modeling a tournament game or player, its identifier is not a board hash.

A transposition table can reuse evaluations only when the stored assumptions and depth/bound semantics remain valid. Hash collisions require a documented risk policy.

## 4. Why universal no-delta-reuse fails

Consider a legal opening sequence from the standard initial position:

```text
1. Nf3 Nf6 2. Ng1 Ng8
```

The pieces return to the initial arrangement; the side to move is again White, and castling rights remain unchanged. The halfmove clock and fullmove number differ, and the game history has advanced. The sequence is legal. A blanket ban on reversing a prior delta would wrongly exclude `Ng1` and `Ng8`.

A second cycle can arise from king or rook movement, but that may permanently alter castling rights; hence the resulting state is not necessarily equivalent. This distinction is a valuable conformance check: *visually identical boards do not imply equivalent legal states*.

**Counterexample CE-CDE-CHESS-001:** A universal prohibition on repeating or reversing a delta rejects legal chess continuations.

**Required definition refinement:** Move no-delta-reuse into an optional `PathMemoryPolicy`, not the CDE minimal kernel.

## 5. Cycle policies and stopping conditions

Chess does not imply unrestricted infinite execution. A search must explicitly declare a stopping policy, and game adjudication must follow the chosen ruleset.

| Policy | Meaning | Appropriate use |
|---|---|---|
| `NO_REUSE` | Forbid previously consumed delta tokens on a path | Some permutation/assignment tasks, not general chess |
| `NO_POSITION_REPEAT` | Avoid equivalent positions within a search path | Optional search heuristic; may discard legal chess lines |
| `ALLOW_WITH_HISTORY` | Permit repetition and retain history | Faithful chess game evolution |
| `BOUNDED_REPETITION` | Permit cycles with explicit bounds | Experimental search policy |
| `RULE_ADJUDICATED` | Apply official game rules for claims/automatic draws | Rules-aware chess play |

A chess ruleset must distinguish claimable draws (such as threefold repetition and the 50-move rule, subject to the ruleset) from automatic draws (such as fivefold repetition and the 75-move rule in standard FIDE chess, with checkmate precedence where applicable). Stalemate and checkmate are terminal by the rules; a fixed-depth search cutoff is a computational boundary, not a game outcome.

Search termination can be ensured by finite depth, node budget, wall-clock budget, or other explicit limits. **Finite branching alone does not guarantee a finite search tree when cycles are permitted.**

## 6. Adversarial evolution and multi-agent policy

The mover alternates between players with potentially opposed objectives. A single scalar maximization over both players' turns is incorrect for standard zero-sum chess.

A simplified minimax recursion is:

\[
V(s,d)=\begin{cases}
U(s), & \text{terminal}(s) \\
E(s), & d=0 \\
\max_{a\in L(s)} V(T(s,a),d-1), & \text{White to move} \\
\min_{a\in L(s)} V(T(s,a),d-1), & \text{Black to move}
\end{cases}
\]

Here `L(s)` denotes legal moves, `U` terminal utility, and `E` a heuristic evaluation from a consistent reference perspective. Alpha-beta pruning, iterative deepening, transposition tables, or Monte Carlo Tree Search are candidate **evolution policies**, not novel consequences of CDE. Their correctness and performance assumptions must be stated separately.

### 6.1 M-to-N branching

CDE's adaptive `M -> N` branching can represent changes in the number of candidate actions, search breadth, or hypothesis variants. In chess, legal branching varies by position. A policy that prunes candidate moves must distinguish **complete legal-move enumeration** from **selective search**; selective search cannot claim exhaustive minimax correctness without further guarantees.

### 6.2 Evaluation perspective

Perspective descriptors may include material balance, king safety, mobility, pawn structure, initiative, and endgame-specific features. These are heuristic evaluation dimensions; most are **not mathematical metrics**. The evaluation function must identify whose utility is being estimated and which assumptions are learned, hand-crafted, or unvalidated.

## 7. WE-SIO integration

### 7.1 Entity and perspective layer

A chess position may be indexed by exact position key, feature vector, graph relation, or learned embedding. A metric index is permitted only if its declared distance contract holds. Similarity scores and directional tactical relations must not be mislabeled as metrics.

### 7.2 WE-HDT and localization

WE-HDT could support retrieval of similar positions or strategic motifs, but **Euclidean-first is optional**. A rules-sensitive exact-key lookup or graph-based relation may be more suitable for some queries. No claim is made that WE-HDT beats conventional chess data structures.

### 7.3 MLIU operations

- **Locate:** retrieve positions matching a rule- and perspective-aware query.
- **Resolve:** reconstruct complete legal state and ambiguity.
- **Relate:** connect positions through legal moves, transpositions, or motifs.
- **Infer:** estimate tactical or strategic consequences with uncertainty.
- **Question:** record discrepancies between predicted and observed outcomes.
- **Evolve:** propose and validate changes to evaluation, search, or representation policies.

### 7.4 Two-Ways CCC and residuals

Forward reasoning evaluates candidate positions under declared constraints. Reverse analysis starts from a failed prediction (for example, an evaluation that misses a tactical resource), then proposes candidate missing features or search conditions. Such proposals are hypotheses, not automatically improved evaluation metrics. Validation requires held-out positions, adversarial tests, and comparisons with baseline search.

### 7.5 World, observation, knowledge, and structural deltas

- **Game-world delta:** a move changes the formal game state.
- **Observation delta:** a corrected record or newly available move annotation changes what is observed.
- **Knowledge delta:** an evaluator revises its assessment of a position.
- **Structural delta:** the system modifies a search tree, feature registry, or evaluation model.

These changes must not be silently conflated. The same position can be re-evaluated without a new chess move.

## 8. Worked test scenarios

### Scenario A — reversible knight sequence

Initial position; apply `g1f3`, `g8f6`, `f3g1`, `f6g8`. All moves are legal. Verify that the board and side to move match the initial arrangement while move counters and history differ. A `NO_REUSE` policy should fail to represent the legal continuation; an `ALLOW_WITH_HISTORY` policy should succeed.

### Scenario B — castling-right loss

Construct a legal sequence in which a rook moves away and returns to its original square without being captured. The board may later resemble an earlier arrangement, but the affected castling right remains lost. A board-only equivalence check must fail conformance.

### Scenario C — transposition

Generate two legal move orders leading to the same rule-equivalent position. Verify that a transposition lookup can share suitable position information while preserving distinct game histories and relevant draw context.

### Scenario D — tactical evaluation residual

Use a curated tactical suite and compare a shallow evaluator's prediction against deeper, independently verified analysis. Register each discrepancy with source, evaluator version, depth, and uncertainty. Evaluate whether residual-driven feature proposals improve held-out accuracy rather than merely fitting the original positions.

### Scenario E — bounded adversarial search

Compare fixed-depth minimax/alpha-beta with a CDE-wrapped policy using the same legal move generator, evaluator, compute budget, and terminal rules. Measure overhead, node counts, correctness of selected moves against a reference, and trace completeness. Do not infer CDE advantage from unequal budgets.

## 9. Conformance suite

| ID | Test | Pass criterion |
|---|---|---|
| CHESS-CF-001 | Legal move generation | Matches an independent rules implementation on test positions |
| CHESS-CF-002 | King safety | No accepted move leaves own king in check |
| CHESS-CF-003 | Castling | Rights, paths, and attacked-square conditions enforced |
| CHESS-CF-004 | En passant | Target, capture, and discovered-check legality handled |
| CHESS-CF-005 | Promotion | All permitted promotion choices supported |
| CHESS-CF-006 | State restoration | Undo reproduces full prior state, not just board |
| CHESS-CF-007 | Reversible moves | Legal out-and-back sequences remain representable |
| CHESS-CF-008 | Position equivalence | Rights, turn, and relevant en-passant semantics included |
| CHESS-CF-009 | Repetition history | Repetition detection is ruleset-aware |
| CHESS-CF-010 | Draw adjudication | Claimable and automatic draws distinguished |
| CHESS-CF-011 | Terminal precedence | Checkmate, stalemate, and draws handled correctly |
| CHESS-CF-012 | Finite search budget | Every run obeys declared resource limits |
| CHESS-CF-013 | Adversarial turns | Player-dependent objectives applied correctly |
| CHESS-CF-014 | Selective search labeling | Pruned search does not claim exhaustive guarantee |
| CHESS-CF-015 | Perspective typing | Non-metric evaluation features are not labeled metrics |
| CHESS-CF-016 | Residual provenance | Each discrepancy records source, model, and version |
| CHESS-CF-017 | Definition revision | Counterexample links to proposed contract change |
| CHESS-CF-018 | Regression preservation | New kernel version retains previously valid cases |
| CHESS-CF-019 | Transposition safety | Cache reuse respects search and rule context |
| CHESS-CF-020 | Baseline parity | Comparative experiments use matched budgets |

These are proposed tests. They have **not** been executed by this document.

## 10. Falsifiable hypotheses

**H-CHESS-001 — Definition portability.** A CDE kernel with configurable path-memory and cycle policies can express both a no-reuse assignment task and rules-faithful chess without altering kernel semantics. *Falsifier:* either task requires incompatible mandatory kernel axioms.

**H-CHESS-002 — Trace utility.** Structured counterexample and definition records reduce time needed by independent contributors to diagnose an invalid CDE constraint. *Falsifier:* controlled reviewers show no reproducible improvement.

**H-CHESS-003 — Residual-driven evaluation.** A validated residual registry improves discovery of missing evaluation features on held-out tactical positions compared with an equally resourced baseline. *Falsifier:* no out-of-sample gain or worse calibration.

**H-CHESS-004 — Policy portability.** Common transition and conformance contracts allow multiple search policies to be exchanged without rewriting chess legality logic. *Falsifier:* policy substitution requires extensive application-specific kernel changes.

**H-CHESS-005 — Operational benefit.** CDE's trace and evolution interfaces provide measurable debugging or reproducibility benefits despite runtime overhead. *Falsifier:* benefits are absent or outweighed under predefined evaluation criteria.

## 11. Definition Evolution Loop: a concrete revision

**Initial candidate definition D0:** Every delta used on a path is consumed and cannot recur.

**Application:** Chess with reversible moves.

**Counterexample:** `1. Nf3 Nf6 2. Ng1 Ng8` is legal.

**Residual:** D0 excludes a valid application while claiming universality.

**Revision D1:** Delta reuse is controlled by an explicit application-level `PathMemoryPolicy`; the kernel requires only typed applicability and transition semantics.

**Regression obligations:** Preserve D-BTP-specific no-reuse behavior when `NO_REUSE` is selected; preserve chess legality when `ALLOW_WITH_HISTORY` is selected; demonstrate finite resource-bounded search without assuming global acyclicity.

**Remaining issue:** Does the minimal kernel provide meaningful structural intelligence beyond a generic transition system? This is unresolved and requires operational comparisons.

## 12. Research trace and relay record

Suggested registry entries:

```yaml
case_id: CASE-004
hypothesis_id: H-CHESS-001
counterexample_id: CE-CDE-CHESS-001
initial_definition: D0-no-delta-reuse
revised_definition: D1-configurable-path-memory
status: proposed-definition-refinement
validation_status: not-executed
related_spec: SPEC-006
related_papers:
  - WE-SIO-009
  - WE-SIO-011
next_actions:
  - implement independent chess legality oracle
  - encode both D-BTP and chess policy profiles
  - run regression and resource-budget tests
  - compare against established search baselines
```

Record the proposal in `research-trace/COUNTEREXAMPLE-REGISTRY.md`, the revision in `DEFINITION-REGISTRY.md`, rationale in `DECISION-LOG.md`, and unresolved questions in `UNRESOLVED-RESIDUALS.md`. Version links should be explicit; do not retroactively rewrite earlier hypotheses as if they were never proposed.

## 13. Validation roadmap

**Phase 0 — Contract review.** Freeze ruleset, state equivalence, transition and path-policy definitions; solicit counterexamples.

**Phase 1 — Legality oracle.** Implement or use an independent rules engine; test move legality, special moves, undo, and adjudication.

**Phase 2 — Policy profiles.** Exercise `NO_REUSE`, `ALLOW_WITH_HISTORY`, and bounded-cycle variants on chess and D-BTP-style tasks.

**Phase 3 — Search comparison.** Run matched-budget minimax/alpha-beta baselines; record overhead, correctness, and reproducibility.

**Phase 4 — Residual learning.** Evaluate held-out tactical cases and metric/perspective candidate validation; audit leakage and selection bias.

**Phase 5 — Collective relay.** Hand the specification and traces to independent reviewers; measure reproducibility of findings and definition revisions.

Every phase should publish negative results and counterexamples alongside successful outcomes.

## 14. Open questions and explicit leftovers

1. What nontrivial invariant distinguishes CDE from an ordinary state-transition abstraction?
2. Should adversarial actor identity belong in the kernel or in a policy profile?
3. What is the minimum history needed for exact game-rule conformance versus search equivalence?
4. When is a cycle restriction a correctness condition, and when is it only a heuristic?
5. Can M-to-N branching be specified without assuming exhaustive enumeration?
6. How should nondeterministic and simultaneous-action games extend the transition contract?
7. Which WE-SIO perspectives improve retrieval or evaluation beyond existing chess representations?
8. Can residual-driven feature discovery improve held-out performance without overfitting?
9. What evidence would justify calling a proposed representation a new mathematical metric?
10. How can independent researchers replay a definition revision and challenge its premises?

## 15. Scope, limitations, and conclusion

This is a conceptual, contract-first research case. It does not contain a working chess engine, executed benchmarks, verified superiority, or evidence of autonomous strategic intelligence. Chess is a well-studied adversarial search domain; established rules engines and search methods remain essential baselines.

The principal result is a **testable definition refinement**: a no-delta-reuse restriction that is useful in some D-BTP paths must not be elevated to a universal CDE axiom. Chess exposes that boundary clearly and motivates configurable path memory, explicit cycle policies, adversarial evaluation, and rules-aware state equivalence.

For WE-SIO, the deeper value is methodological: a concrete counterexample becomes a persistent research artifact that can trigger a definition revision, conformance tests, regression obligations, and an independently replayable Collective Learning Relay.

---

**Repository placement:** `cases/CASE-004-Chess-as-a-CDE-Boundary-Stress-Test.md`  
**Suggested figure:** `figures/Fig-009-Definition-Evolution-Loop.png`  
**License:** Apache-2.0 (subject to repository LICENSE)  
**Research status:** Hypothesis and specification; empirical validation pending.
