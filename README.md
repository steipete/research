# Async Code Research

This repository is a scratchpad for running self-contained experiments with asynchronous coding agents. Treat every branch or folder as a short-lived research project that proves or disproves a concrete question by writing and executing code.

## Inspiration

Simon Willison’s blog post “Code research projects with async coding agents like Claude Code and Codex” (November 6, 2025) outlines a workflow where agents such as Codex cloud, Claude Code on the web, Jules, or GitHub Copilot cloud agent take a prompt, work unattended, and file results back to a GitHub repo. A few of his key practices shape this repo:

- **Code research mindset:** the fastest way to answer “Will this work?” is to build a focused proof-of-concept, gather data, and read the outputs instead of debating hypotheticals.
- **Asynchronous agents:** fire-and-forget agents churn through experiments while you do something else, then return with diffs, reports, branches, or pull requests for review.
- **Dedicated playground:** isolating research in its own public repo encourages aggressive exploration, cross-project reuse (each project lives in its own folder), and low-risk automation such as bots that summarize results.
- **Scoped network access:** a disposable repository reduces the blast radius, but arbitrary dependencies, install scripts, and downloaded data remain untrusted. Enable only the access an experiment needs, and never expose production credentials or private data.

Read the original article for deeper context: https://simonwillison.net/2025/Nov/6/async-code-research/

Current service documentation: [Codex cloud](https://developers.openai.com/codex/cloud/), [Claude Code on the web](https://code.claude.com/docs/en/claude-code-on-the-web), [Jules](https://jules.google/docs/), and [GitHub Copilot cloud agent](https://docs.github.com/en/copilot/how-tos/copilot-on-github/use-copilot-agents/overview).

## Suggested Workflow

1. **Define the research question.** Phrase it so running code can produce evidence (benchmarks, compatibility checks, deployment spikes, etc.).
2. **Prepare the prompt.** Include the question, constraints (folder layout, tooling, tests to run), and expected artifacts (reports, charts, transcripts).
3. **Launch an asynchronous agent.** Grant the repository and network access required for the experiment, preferably with an allowlist. Do not provide secrets unless the experiment explicitly requires them and the agent platform can scope them safely. Collect logs of commands, data sources, and decisions.
4. **Review and merge.** Inspect generated code, setup scripts, dependencies, and data before running them. Reproduce critical results in an isolated environment, then note any follow-up work before merging.
5. **Document outcomes.** Each project folder should contain a README that states the prompt, the experiments performed, and the conclusions so future projects can reuse the findings.

## Repository Conventions

- One subdirectory per research task (e.g., `python-markdown-comparison/`), containing code, data snapshots (if size allows), and a concise report.
- Optional `AGENTS.md` (or similar) to brief future agents on expectations, security posture, and coding standards.
- Keep automation lightweight: GitHub Actions or simple scripts can regenerate an index of projects, lint agent output, or archive prompts/transcripts.
- Prefer reproducible project environments and dependency inputs (`uv.lock`, pinned requirements files, `package-lock.json`, etc.). Record runtime and tool versions; commit generated lockfiles or checksums where supported so humans can validate findings quickly. Use isolated runners such as `pipx` for one-off tools.
- Treat prompts, fetched content, package install scripts, and generated output as untrusted input. Never commit secrets, credentials, personal data, or proprietary source to this public repository.

## Next Steps

- Seed the repo with an initial research question (for example, reproducing one of Willison’s benchmarking studies).
- Add guardrails for agents (testing scripts, lint configs, datasets mirrors) that encourage higher-quality outputs.
- Track experiment metadata (prompt, agent, runtime, status) so you can mine the repository for patterns and lessons learned.

Happy researching!
