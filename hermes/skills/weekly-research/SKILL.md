# Weekly Marketing Intelligence Skill

## Mission

Produce a defensible intelligence snapshot for Keanso and AI-Bid. Research first, reason second, and preserve evidence for every material conclusion.

## Required workflow

### 1. Load product truth

Read:

- `brands/keanso/product.md`
- `brands/keanso/audience.md`
- `brands/ai-bid/product.md`
- `brands/ai-bid/audience.md`
- `hermes/research/SOURCES.md`
- `hermes/policies/marketing-policy.md`
- `hermes/policies/sunday-mode.md`

Then inspect the current product repositories when the run has repository access:

- `techykaif/Keanso`
- `techykaif/aibid`

For AI-Bid, prefer `IMPLEMENTATION_STATUS.md` over the old MVP-spec wording in `README.md` when the two conflict.

### 2. Verify production

Inspect the public production sites and record only observable facts. Do not infer private analytics, internal configuration, or unavailable features.

For each product, check:

- homepage/product promise
- primary user journey
- important launch-facing pages
- obvious errors or broken links
- pricing/payment claims visible publicly
- metadata/SEO basics where relevant
- visible product changes compared with the previous snapshot

### 3. Market research

Research current public information relevant to the product's target audience.

Keanso themes:

- invoice collection
- late payment pain
- freelancer cash flow
- payment follow-up workflows
- invoice/reminder software
- alternatives and competitors

AI-Bid themes:

- AI product discovery
- launch visibility
- AI directories
- paid discovery/ranking
- indie maker growth
- game discovery for the launch expansion
- comparable leaderboard/pay-to-rank products

Search for meaningful changes, not generic SEO filler.

### 4. Opportunity scoring

Score opportunities using:

- relevance to target audience: 0–5
- evidence strength: 0–5
- timing: 0–5
- product fit: 0–5
- execution cost: 0–5, where higher means cheaper/easier

Do not publish solely because an opportunity scores highly. Safety and platform policy still apply.

### 5. Change detection

Compare against the latest available snapshot under `state/` or `reports/`.

Classify changes as:

- `new`
- `changed`
- `unchanged`
- `removed`
- `uncertain`

If there is no prior snapshot, explicitly mark the run as a baseline.

### 6. Strategy output

Produce a prioritized next-week strategy with:

- objective
- audience
- hypothesis
- channel
- proposed content/experiment
- evidence
- expected signal
- measurement method
- risk/compliance note
- whether human approval is required

### 7. Sunday restriction

When this skill is run in Sunday mode, it must not publish, reply, DM, follow, like, submit directories, or spend money. Sunday output is intelligence and planning only.

## Evidence format

Every important finding should use this structure:

```yaml
finding: "..."
source: "https://..."
source_type: "first_party|competitor|community|publication|platform"
observed_at: "ISO-8601"
brand: "keanso|ai-bid|both"
confidence: "high|medium|low"
verification: "direct|inferred"
impact: "low|medium|high"
```

## Output files

Write:

- `reports/latest/keanso.md`
- `reports/latest/ai-bid.md`
- `reports/latest/market.md`
- `reports/latest/strategy.md`
- `reports/latest/system.md`
- `state/latest.json`

Keep reports concise enough to remain useful to later agent runs.

## Failure behavior

If a source cannot be reached, record the failure and continue with other sources. Never replace missing evidence with guesses.

If a claim cannot be verified, label it `uncertain` and keep it out of factual marketing copy.
