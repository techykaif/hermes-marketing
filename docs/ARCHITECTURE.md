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
Drafts
       ↓
Approval boundary
       ↓
Postiz / approved channel integration
       ↓
Measurement + attribution
       ↓
Learning
```

## Execution boundary

Research and planning are autonomous. External publishing is isolated behind a dedicated publishing boundary. The research workflows do not receive publishing credentials. Financial commitments, irreversible destructive actions, credential changes, and high-risk external communications require a separate authorization boundary.

Postiz is the initial publishing adapter. Its API can list connected integrations and create/schedule posts, but Hermes remains responsible for product truth, channel policy, approval state, duplication checks, attribution, and audit records.

## Scheduling

The first deployment target is scheduled execution on GitHub Actions. Hermes installation is cached between hosted-runner jobs while configuration and secrets are recreated per run. A persistent worker/VPS can be introduced later without changing the knowledge or strategy model.

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
  postiz/

docs/
  ANALYTICS.md
  ATTRIBUTION.md
  SETUP.md

reports/
  drafts/
  daily/
  weekly/
  latest/

state/
  audit/
  publishing.json
```

## Safety model

Every external action is classified as R0-R4 in `hermes/policies/channel-policy.md`. The default state is draft-only. Publishing credentials are never exposed to research jobs, and all external actions require an audit record.
