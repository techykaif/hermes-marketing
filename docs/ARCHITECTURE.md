# Hermes Marketing Architecture

## Purpose

Hermes is the marketing operating layer shared by independently deployed products. It is not the product application and must not become a dependency of Keanso or AI-Bid's runtime.

## Product adapters

Each managed product gets a small adapter describing:

- repository
- production origin
- canonical product facts
- audience
- positioning
- approved claims
- prohibited claims
- available metrics
- marketing channels
- important product events

Adapters may read source repositories, but the final knowledge artifact is normalized into Hermes-owned files.

## Knowledge lifecycle

```text
Source discovery
  → evidence collection
  → claim extraction
  → confidence/provenance
  → normalized product knowledge
  → strategy context
```

Every material claim should retain provenance so Hermes can distinguish verified facts from hypotheses.

## Strategy lifecycle

```text
Current knowledge
  + market research
  + competitor changes
  + campaign performance
  + product changes
       ↓
Weekly strategy
       ↓
Prioritized experiments
       ↓
Content / campaign briefs
       ↓
Execution
       ↓
Measurement
       ↓
Learning
```

## Execution boundary

Research and planning may be autonomous. Publishing can be automated only through explicitly configured integrations and policies. Financial commitments, irreversible destructive actions, credential changes, and high-risk external communications require a separate authorization boundary.

## Scheduling

The first deployment target is scheduled execution. A persistent worker can be introduced later without changing the knowledge or strategy model.

## Repository layout

```text
brands/
  <product>/
    product.md
    audience.md
    positioning.md
    claims.md
    channels.md
    strategy/

hermes/
  policies/
  prompts/
  skills/
  workflows/

integrations/

scheduler/

docs/
```
