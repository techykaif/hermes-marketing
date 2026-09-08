# Hermes Marketing Setup

The repository is intentionally wired for GitHub Actions first so it does not require a VPS. GitHub scheduled workflows can run the intelligence jobs on standard hosted runners. urlGitHub Actions workflow documentationhttps://docs.github.com/en/actions/concepts/workflows-and-actions/workflows

Hermes supports scripted one-shot execution with `hermes -z`, which is the execution mode used by the workflows. urlHermes CLI documentationhttps://hermes-agent.nousresearch.com/docs/reference/cli-commands

## Required repository configuration

### Inference secrets

Add these repository secrets when available:

`CEREBRAS_API_KEY` — primary inference provider

`OPENROUTER_API_KEY` — optional last-resort fallback

**Groq is intentionally not used by this repository.** It is already used by other systems and is not part of this marketing worker's quota budget.

The workflows use Hermes' native `fallback_providers` chain: **Cerebras first**, **OpenCode Free second**, and **OpenRouter Free last**. OpenCode Free is keyless and requires no account or credential. Hermes can automatically switch providers when the primary model encounters supported rate-limit, server, auth, connection, or invalid-response failures. urlHermes fallback provider documentationhttps://hermes-agent.nousresearch.com/docs/user-guide/features/fallback-providers urlHermes provider documentationhttps://hermes-agent.nousresearch.com/docs/integrations/providers

You do not need to configure `HERMES_INFERENCE_MODEL` anymore; the workflow pins the primary model and the fallback chain explicitly.

### Product repository access

`PRODUCT_REPO_READ_TOKEN` remains required for read-only cloning of the private Keanso and AI-Bid repositories.

## Provider/model policy

Primary:

- Cerebras custom OpenAI-compatible endpoint `gpt-oss-120b`
- Endpoint: `https://api.cerebras.ai/v1`

Fallback 1:

- OpenCode Free `deepseek-v4-flash-free`
- Keyless; Hermes can refresh the OpenCode Free catalog as models rotate

Fallback 2:

- OpenRouter `openrouter/free`

Cerebras documents GPT-OSS 120B as supporting function calling, structured outputs, tools, reasoning, and agentic research workflows. Hermes' current OpenCode Free provider is keyless and dynamically refreshes its free-model catalog. urlCerebras GPT-OSS 120B model documentationhttps://inference-docs.cerebras.ai/api-reference/models/public-models urlHermes provider documentationhttps://hermes-agent.nousresearch.com/docs/integrations/providers

The Hermes CI profile is deliberately bounded to reduce unnecessary agent turns: 12 turns for daily runs and 20 turns for Sunday intelligence. Native provider fallback preserves the conversation and continues from the failed turn instead of restarting the entire planning task.

## Workflows

### Daily

`.github/workflows/hermes-daily.yml`

Runs Monday-Saturday at 09:00 Asia/Kolkata. It performs focused research, product verification, strategy processing, and content drafting. It does not publish or engage externally.

### Sunday

`.github/workflows/hermes-sunday.yml`

Runs Sunday at 10:30 Asia/Kolkata. It performs the full weekly intelligence cycle and writes the next-week strategy. Sunday execution is explicitly prohibited from publishing, outreach, engagement, directory submissions, and ad spend.

Both workflows can also be started manually with `workflow_dispatch`.

## Persistent state

The agent writes intelligence into the repository under:

- `reports/daily/`
- `reports/weekly/`
- `reports/latest/`
- `state/`

The workflow commits changed intelligence files back to `main` using the workflow's GitHub token.

## Security boundary

The workflow has write access only to repository contents because it must persist reports. It does not receive social credentials or payment credentials.

Do not add platform credentials until the research/strategy loop has been verified.

## Next integration stage

After the intelligence loop is proven:

1. add persistent analytics sources
2. add Postiz publishing integration
3. create channel-specific approval policies
4. add human approval for higher-risk actions
5. enable limited autonomous publishing
6. add attribution and performance feedback

Publishing should remain separate from research so a research failure cannot silently become an external marketing action.
