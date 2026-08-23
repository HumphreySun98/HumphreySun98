# Agent Etna — Contract & Guardrails

This file is maintained automatically by **Agent Etna** for **HumphreySun98**.
It is this agent's behavioral **contract**: what it's for, who it serves, what's
in and out of scope, plus a log of every change Etna has applied — so the whole
footprint is visible and auditable in your own repo.

_Maintained by Agent Etna. Don't edit by hand — it is rewritten on every shipped change._

## Agent
- **Repo:** `HumphreySun98/HumphreySun98` (branch `main`)

## Behavioral contract
_No calibration set yet — Agent Etna uses general defaults until you calibrate this agent._

## Guardrails
- No behavioral calibration set yet — Agent Etna uses general defaults until you calibrate this agent.

## Change history

### 2026-08-23 · Cycle 1 · 1 change · merged
- **safety:memory-retention** — The agent falsely denied intra-conversation memory when asked to recall REF-2C5C17; adding an explicit rule that within-session context is retained and identifiers must be quoted back directly fixes this class of failure.
