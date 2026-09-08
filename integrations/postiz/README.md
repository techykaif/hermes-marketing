# Postiz Publishing Integration

Postiz is the publishing boundary for Hermes. Research/planning remains independent from external publishing.

## Current mode

**DISABLED / DRAFT-ONLY** until the Postiz account, connected channels, API key, and approval policy are explicitly configured.

Postiz's public API is available at `https://api.postiz.com/public/v1` and supports listing integrations, creating/scheduling posts, media uploads, and post/analytics operations. Hermes must never place the Postiz API key in generated reports or repository files.

## Required secret

- `POSTIZ_API_KEY` — repository/environment secret, only available to a dedicated publishing workflow.

Do not expose this secret to the research workflows.

## Publishing contract

1. Hermes creates a channel-specific draft in `reports/drafts/`.
2. A publishing workflow validates the draft against `hermes/policies/channel-policy.md`.
3. The workflow requires the configured approval boundary for the action class.
4. Only approved, supported channels are sent to Postiz.
5. The resulting Postiz ID/status is written to `state/publishing.json` and an audit record is written under `state/audit/`.
6. Fail closed on missing approval, missing channel mapping, duplicate content, unsupported settings, or API errors.

## Postiz channel mapping

Keep account/integration IDs in GitHub Actions variables or environment configuration, never in strategy reports.

Suggested variables:

- `POSTIZ_KEANSO_X_INTEGRATION_ID`
- `POSTIZ_KEANSO_LINKEDIN_INTEGRATION_ID`
- `POSTIZ_AIBID_X_INTEGRATION_ID`
- `POSTIZ_AIBID_LINKEDIN_INTEGRATION_ID`

Add additional channels only after their policy entry exists.

## Initial rollout

Phase 1 is approval-only scheduling. Hermes can prepare and validate posts, but cannot publish autonomously.

Phase 2 may permit low-risk scheduled publishing for approved channels after successful dry runs and audit verification.

Phase 3 can expand channel coverage after per-channel policy, attribution, and failure handling are proven.
