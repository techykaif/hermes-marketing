# External Action Audit

Each external action must have a machine-readable record here or in an equivalent persistent store.

Required fields:

- `schema_version`
- `timestamp`
- `product`
- `channel`
- `action_type`
- `risk_class`
- `content_id` or `brief_id`
- `approval_status`
- `provider`
- `external_id` when available
- `result`
- `error` when applicable

Never store API keys, cookies, access tokens, private customer data, or unnecessary personal information.
