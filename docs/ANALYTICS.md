# Analytics Integration Contract

Analytics is read-only input to Hermes. The research workflows may consume approved public/product-owned metrics but must not modify analytics configuration.

## Sources

### Keanso

Use product-owned analytics and verified application events available to the marketing operator. Record the source, period, metric definition, and confidence in reports.

### AI-Bid

Use product-owned analytics/API/admin-safe aggregates available to the marketing operator. Treat leaderboard totals, clicks, submissions, bids, and conversions according to their actual implementation definitions; never infer missing values.

### Postiz

Once configured, Postiz can provide post/channel performance and publication state. Store normalized aggregates rather than raw account data where possible.

## Normalized metric record

```json
{
  "brand": "keanso",
  "source": "product",
  "metric": "signup_completed",
  "period_start": "YYYY-MM-DD",
  "period_end": "YYYY-MM-DD",
  "value": 0,
  "unit": "count",
  "campaign_id": null,
  "content_id": null,
  "confidence": "verified",
  "retrieved_at": "ISO-8601"
}
```

## Rules

- Missing data is `unknown`, not zero.
- Never mix incompatible time windows without labeling them.
- Never compare metrics with different definitions as if they were equivalent.
- Preserve the raw source reference in the report.
- Prefer conversion and qualified-usage metrics over reach or engagement.
