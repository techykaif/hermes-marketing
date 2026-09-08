# Channel Policy

This policy is the approval boundary for external marketing actions.

## Global rules

- No action without a concrete product, channel, content brief, and evidence reference.
- No fabricated claims, testimonials, metrics, customer stories, or urgency.
- No mass engagement, unsolicited DMs, automated likes/follows, or repetitive spam.
- Use official APIs or supported integrations only.
- Respect platform-specific rate limits and automation rules.
- Never publish on Sunday intelligence runs.
- Never spend money or create billing commitments.
- Every external action gets an audit record.

## Risk classes

### R0 — Internal

Examples: research, strategy, drafts, analytics processing, content scoring.

**Approval:** none.

### R1 — Prepared external action

Examples: creating a Postiz draft, validating a post, generating UTM links, preparing a reply for review.

**Approval:** none, but no external publication.

### R2 — Scheduled publishing

Examples: scheduling an original promotional/product post through Postiz.

**Approval:** explicit human approval until the channel has passed the autonomous-publishing gate.

### R3 — Community interaction

Examples: replies, comments, DMs, mentions, engagement actions.

**Default:** prohibited for autonomous execution.

These actions require a separate channel-specific policy and, where the platform requires it, explicit platform authorization.

### R4 — Financial / irreversible

Examples: ad spend, budget changes, paid campaigns, destructive account changes.

**Approval:** explicit human authorization plus a configured budget boundary.

## Initial channels

| Channel | Research | Draft | Schedule | Autonomous publish | Engagement |
| --- | --- | --- | --- | --- | --- |
| X | Yes | Yes | Approval | Off | Off |
| LinkedIn | Yes | Yes | Approval | Off | Off |
| Reddit | Yes | Yes | Approval | Off | Off |
| YouTube | Yes | Yes | Approval | Off | Off |
| Instagram | Yes | Yes | Approval | Off | Off |
| TikTok | Yes | Yes | Approval | Off | Off |

The matrix is intentionally conservative. A channel can be promoted only after API connectivity, attribution, duplication protection, audit logging, and policy validation are demonstrated.
