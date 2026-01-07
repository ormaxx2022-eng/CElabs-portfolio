# On-Chain Data — Evolution

This document describes how the on-chain observability layer
evolves over time without compromising data integrity,
interpretability, or governance trust.

Evolution is treated as a controlled process,
not as an ad-hoc reaction to changing requirements.

---

## Purpose of evolution design

On-chain systems evolve continuously:
- protocol upgrades
- parameter changes
- infrastructure shifts
- governance process updates

The observability layer must adapt to these changes
while preserving consistent interpretation boundaries.

The goal is to ensure that visibility degrades gracefully
and recovers predictably during transitions.

---

## What is allowed to evolve

The following elements are expected to evolve:

- data schemas and field availability
- aggregation dimensions and role mappings
- reconciliation heuristics and metadata
- lag and finality thresholds
- invariant signal definitions

All evolution is **explicit and versioned**.

---

## What must remain stable

The following properties are treated as stable guarantees:

- distinction between provisional and finalized data
- reorganization-aware handling
- separation between observation and action
- role-based aggregation boundaries
- explicit uncertainty signaling

These properties define the trust model of observability.

---

## Schema evolution

Schema changes are handled through:

- additive changes where possible
- versioned schemas with clear activation points
- parallel support for legacy and new formats
- explicit deprecation windows

Backward compatibility is preferred,
but not assumed indefinitely.

---

## Handling protocol upgrades

Protocol upgrades introduce structural discontinuities.

The observability layer responds by:
- isolating pre- and post-upgrade data views
- preventing cross-version aggregation
- annotating transition windows explicitly
- delaying invariant evaluation until stability is restored

Continuity is preserved through segmentation,
not forced unification.

---

## Observability during degradation

During partial failures or infrastructure stress:

- data availability may decrease
- lag may increase beyond normal bounds
- reconciliation windows may widen

The system prioritizes:
- correctness over completeness
- transparency over immediacy
- bounded uncertainty over silent failure

Degradation is surfaced, not hidden.

---

## Governance interaction during evolution

Governance participates in observability evolution by:

- approving schema and aggregation changes
- setting acceptable lag and uncertainty thresholds
- reviewing post-transition behavior
- coordinating cross-layer upgrades

Governance acts as an overseer,
not as an operator of the data layer.

---

## Versioning and rollout strategy

Evolution follows a staged rollout model:

1. proposal and documentation
2. parallel observation (old + new)
3. validation against invariant signals
4. activation of new version
5. deprecation of legacy paths

Rollback paths are defined where feasible.

---

## Long-term perspective

The observability layer is designed for:

- continuous protocol evolution
- shifting participation patterns
- changing infrastructure constraints

Stability is achieved through controlled change,
clear boundaries, and explicit uncertainty.

The observability layer evolves to remain legible,
not to become predictive.

