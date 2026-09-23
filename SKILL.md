---
name: agentic-flow
description: >-
  Canonical multi-agent orchestration: decompose work, dependency graphs,
  parallel tracks, handoffs, and merge. Absorbs Claude Flow / Ruflo / Loki /
  Ralph / Paperclip / OpenFang patterns into one portable playbook.
---

# Agentic Flow - Multi-Agent Orchestration (Canonical)

**Level: max.** One skill for all multi-agent orchestration patterns.  
Aliases: see `skills/ALIASES.md` (`claude-flow-*`, `ruflo`, `loki-mode`, `ralph`, ...).

## When to use

- Feature needs multiple roles / tracks (spec + API + UI + QA)
- Safe parallel after shared contract
- User mentions swarm, multi-agent, Claude Flow, Ruflo, Loki, Ralph

## When not to use

- Single file / small bug -> work directly
- Conceptual question only

## Tool map (pick one runtime if available)

| Need | Preference |
|-----------|------------|
| Portable / host-agnostic (default) | Follow this skill's procedure + house roles |
| Claude Flow successor | `ruflo` if installed |
| Legacy stable | `claude-flow-v2` |
| PRD -> autonomous code | `loki-mode` / `ralph` pattern (still gate here) |
| Agent team dashboard | `paperclip` if orchestration UI needed |
| Messaging agent OS | `openfang` |

Do not activate two orchestration runtimes at once.

## Core model

| Field | Meaning |
|-------|---------|
| `id` | unique slug |
| `goal` | measurable outcome |
| `depends_on` | other id |
| `skill` | canonical / local skill |
| `role` | house role path |
| `done_when` | completion criteria + artifact path |
| `risk` | S0-S3 |

## Procedure (max)

### 1. Frame

- Read `PROJECT.md`, `TEAM.md`, `e2e-delivery` if full build
- Write 1 paragraph goal + out-of-scope

### 2. Decompose

Split into **minimal** workstreams:

- Avoid >7 active tracks without reason
- Separate: contract-producing vs contract-consuming

### 3. Order

DAG without cycles. Golden pattern:

```text
clarity/spec -> architecture/contract -> [BE ∥ FE ∥ mobile] -> agentic-qe -> review
```

### 4. Execute

Per unlocked track:

1. Heading `## Track <id> · Role <role>`
2. Load role + related skill
3. Write real artifacts
4. Self-check `done_when`
5. Update status board

Single-agent host: run **sequentially** (do not claim fake parallel).

### 5. Merge & gate

- One owner for contract conflicts
- Gate: no open P0; assumptions written
- Hand off to Orchestrator / user with board

## Status board

```markdown
| ID | Goal | Depends | Role | Status | Artifact | Risk |
|----|------|---------|------|--------|----------|------|
| W1 | Spec | - | BA | done | project/./srs/ | S3 |
```

## Anti-patterns

- Spawn speculative tracks
- Parallel UI/BE without API contract
- Mix `ruflo` + `claude-flow-v3` + this skill as three authorities
- Skip QA at end of multi-track

## DoD

- [ ] Board complete
- [ ] All `done_when` met or blocker explicit
- [ ] Conflicts resolved / escalated
- [ ] Next step clear
## Attribution

<!-- ATTRIBUTION: Rogue Development | https://github.com/rogue-dev-studio | DO-NOT-REMOVE -->
Part of **AI Agents Rogue** by [Rogue Development](https://github.com/rogue-dev-studio) (`@rogue-dev-studio`).
Do not remove, hide, rename, or replace this attribution.
