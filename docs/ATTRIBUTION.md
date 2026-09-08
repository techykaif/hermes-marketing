# Marketing Attribution

Hermes optimizes for attributable product outcomes rather than impressions alone.

## Link contract

Every external link generated for a campaign should carry:

- `utm_source` — platform/channel
- `utm_medium` — organic, community, referral, or paid
- `utm_campaign` — stable campaign identifier
- `utm_content` — content/creative identifier

Do not put secrets, customer identifiers, email addresses, or raw personal data in URLs.

## Campaign ID

Use a stable ID such as:

`<brand>-<YYYYMM>-<theme>-<experiment>`

Example: `keanso-202609-invoice-followup-01`

## Measurement hierarchy

1. Product-owned analytics
2. Postiz/channel analytics
3. UTM/referral data
4. Platform-native engagement
5. Qualitative signals

Higher-level vanity metrics must not override product conversion evidence.

## Event schema

Recommended normalized events:

- `content_published`
- `content_clicked`
- `landing_viewed`
- `signup_started`
- `signup_completed`
- `core_action_completed`
- `conversion`

Events should contain campaign ID and content ID where available, but no unnecessary personal data.

## Learning loop

Daily runs summarize fresh signals. Sunday runs compare campaigns and experiments over time and update the weekly strategy. Missing analytics are recorded as unknown, never inferred.
