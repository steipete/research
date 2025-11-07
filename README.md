# Async Code Research

This repository is a scratchpad for running self-contained experiments with asynchronous coding agents. Treat every branch or folder as a short-lived research project that proves or disproves a concrete question by writing and executing code.

## Inspiration

Simon Willison’s blog post “Code research projects with async coding agents like Claude Code and Codex” (November 6, 2025) outlines a workflow where agents such as Codex Cloud, Claude Code for web, Gemini Jules, or GitHub Copilot’s coding agent take a prompt, work unattended, and file results back to a GitHub repo. A few of his key practices shape this repo:

- **Code research mindset:** the fastest way to answer “Will this work?” is to build a focused proof-of-concept, gather data, and read the outputs instead of debating hypotheticals.
- **Asynchronous agents:** fire-and-forget agents churn through experiments while you do something else, then return with commits, reports, or pull requests for review.
- **Dedicated playground:** isolating research in its own public repo encourages aggressive exploration, cross-project reuse (each project lives in its own folder), and low-risk automation such as bots that summarize results.
- **Full network access:** when the repo is intentionally disposable, agents can install dependencies, download datasets, and reach external APIs without jeopardizing production secrets.

Read the original article for deeper context: https://simonwillison.net/2025/Nov/6/async-code-research/

## Suggested Workflow

1. **Define the research question.** Phrase it so running code can produce evidence (benchmarks, compatibility checks, deployment spikes, etc.).
2. **Prepare the prompt.** Include the question, constraints (folder layout, tooling, tests to run), and expected artifacts (reports, charts, transcripts).
3. **Launch an asynchronous agent.** Point it at this repository with network access enabled. Encourage it to commit frequently and to collect logs of commands, datasets, and decisions.
4. **Review and merge.** When the agent files a branch or PR, verify the code, rerun critical steps, and note any follow-up work before merging.
5. **Document outcomes.** Each project folder should contain a README that states the prompt, the experiments performed, and the conclusions so future projects can reuse the findings.

## Repository Conventions

- One subdirectory per research task (e.g., `python-markdown-comparison/`), containing code, data snapshots (if size allows), and a concise report.
- Optional `AGENTS.md` (or similar) to brief future agents on expectations, security posture, and coding standards.
- Keep automation lightweight: GitHub Actions or simple scripts can regenerate an index of projects, lint agent output, or archive prompts/transcripts.
- Prefer reproducible environments (`requirements.txt`, `uv`, `pipx`, `npm`, etc.) so humans can validate findings quickly.

## Next Steps

- Seed the repo with an initial research question (for example, reproducing one of Willison’s benchmarking studies).
- Add guardrails for agents (testing scripts, lint configs, datasets mirrors) that encourage higher-quality outputs.
- Track experiment metadata (prompt, agent, runtime, status) so you can mine the repository for patterns and lessons learned.

Happy researching!
