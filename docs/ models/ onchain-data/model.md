# On-Chain Data — Model

This document defines a system-level model for on-chain data
treated as an observability layer.

The model focuses on structural properties, failure modes,
and architectural constraints inherent to on-chain observation.

---

## 1. System boundary

**Inside the observability layer:**
- data ingestion and indexing processes (abstract)
- state reconstruction and reconciliation logic
- role-based aggregation views
- invariant signal extraction
- observability metadata (timestamps, lag indicators)

**Outside the observability layer:**
- execution semantics of the protocol
- off-chain interpretation or decisioning
- market behavior and valuation
- proprietary analytics pipelines

---

## 2. Core properties of on-chain data

On-chain data exhibits several non-negotiable properties:

- **eventual consistency:** final state is known only after delays
- **reorganization risk:** previously observed state may be invalidated
- **partial availability:** not all data is available at all times
- **schema drift:** data structures evolve across protocol versions
- **observer asymmetry:** different observers see different subsets of data

Any architecture that ignores these properties
produces unreliable conclusions.

---

## 3. Observation latency and lag

Observation lag is treated as a first-class concern.

Sources of lag include:
- block finality delays
- indexing and ingestion backlogs
- network or provider partial outages
- reconciliation after reorganization events

Lag is not an error condition.
It is a normal operating mode that must be surfaced explicitly.

---

## 4. Reorganization-aware observation

The model assumes that:

- observed state may be provisional
- historical data may require revision
- consumers must tolerate state rollbacks
- invariants must be evaluated against finalized views

Reorg-awareness is mandatory for any trustworthy observability layer.

---

## 5. Reconciliation and consistency

Reconciliation is the process of aligning observed data
with the canonical system state.

This includes:
- detecting divergence between expected and observed state
- resolving conflicts after reorganization
- surfacing uncertainty during reconciliation windows
- marking data as provisional or finalized

Consistency is treated as a spectrum, not a binary property.

---

## 6. Role-based aggregation

Observation is organized around **system roles**, not entities.

Typical aggregation dimensions include:
- participant role categories
- protocol component boundaries
- governance action timelines
- invariant classes

This avoids overfitting observation to individual addresses
or transient identifiers.

---

## 7. Invariant signal extraction

The observability layer may surface signals related to:

- invariant breaches or near-breaches
- delayed state transitions
- abnormal role distribution shifts
- missing or inconsistent data segments

Signals are descriptive indicators,
not actionable instructions.

---

## 8. Failure modes

Common failure modes in on-chain observability include:

- silent data loss during partial outages
- false confidence due to ignored lag
- inconsistent views across observers
- schema mismatch after upgrades
- overinterpretation of provisional data

These failures affect **visibility**, not execution.

---

## 9. Guard rails for interpretation

To prevent misuse, the model enforces:

- explicit labeling of provisional vs finalized data
- separation between observation and action
- bounded aggregation scopes
- governance-mediated interpretation

The observability layer informs,
but does not decide.

---

## 10. Relationship to other models

- tokenomics relies on observability for feedback, not control
- protocol execution defines the source of truth
- infrastructure constraints bound data availability

This layer exists to make system behavior legible,
not predictable.


