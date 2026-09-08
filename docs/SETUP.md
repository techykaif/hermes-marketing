# Hermes Marketing Setup

The repository is intentionally wired for GitHub Actions first so it does not require a VPS. GitHub scheduled workflows can run the intelligence jobs on standard hosted runners. urlGitHub Actions workflow documentationhttps://docs.github.com/en/actions/concepts/workflows-and-actions/workflows

Hermes supports scripted one-shot execution with `hermes -z`, which is the execution mode used by the workflows. urlHermes CLI documentationhttps://hermes-agent.nousresearch.com/docs/reference/cli-commands

## Required repository configuration

### Secret

Add this repository secret:

`OPENROUTER_API_KEY`

The workflow does not print the secret and Hermes secret redaction remains enabled.

### Repository variable

Add:

`HERMES_INFERENCE_MODEL`

Set it to the OpenRouter model identifier you want Hermes to use. Keep this as a repository variable rather than hard-coding a model into the workflow so the model can be changed without a code commit.

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
