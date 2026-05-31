# job-board-coding

Coding Agent demo protocol for building a practical job application progress board.

This repository works in two modes:

- **Codex CLI**: install it as a Codex skill.
- **Claude Code**: clone it into the project workspace and ask Claude Code to read `SKILL.md` plus the reference prompts.

The demo is designed for a direction-3 coding-agent case: a real, useful frontend project rather than a toy snippet. It focuses on first-pass engineering completion quality: planning, file creation, build verification, README, and a screenshot-friendly final app.

## What It Builds

A local job application tracking board for internship, campus recruiting, and job-search workflows.

Core features:

- Five kanban stages: submitted, written test, interview, offer, rejected
- Application cards with company, role, direction, dates, priority, notes, and next action
- Add, edit, delete, drag between stages
- Seven-day deadline reminders
- Dashboard stats and simple distributions
- Fictional seed data
- localStorage persistence
- React + TypeScript + Vite
- README and build verification

## Option A: Use With Codex CLI

### Install The Skill

Clone this repository into your Codex skills folder:

```powershell
mkdir $env:USERPROFILE\.codex\skills -Force
git clone https://github.com/jjyaoao/job-board-coding.git $env:USERPROFILE\.codex\skills\job-board-coding
```

Update later with:

```powershell
cd $env:USERPROFILE\.codex\skills\job-board-coding
git pull
```

### Configure StepFun For Codex CLI

Important: recent Codex CLI versions no longer support `wire_api = "chat"`. They require `wire_api = "responses"` for custom providers. StepFun `step-3.7-flash` quickstart uses the Chat Completions endpoint, so direct Codex CLI integration may require either:

- a StepFun endpoint that supports OpenAI Responses-compatible requests, or
- a small local bridge that exposes `/v1/responses` to Codex and forwards requests to StepFun `/v1/chat/completions`.

If you see this error, your Codex CLI is enforcing the new Responses-only provider path:

```text
Error loading config.toml: `wire_api = "chat"` is no longer supported.
How to fix: set `wire_api = "responses"` in your provider config.
```

Open Codex config:

```powershell
mkdir $env:USERPROFILE\.codex -Force
notepad $env:USERPROFILE\.codex\config.toml
```

Add:

```toml
[model_providers.stepfun]
name = "StepFun"
base_url = "https://api.stepfun.com/v1"
env_key = "STEPFUN_API_KEY"
wire_api = "responses"
requires_openai_auth = false
request_max_retries = 4
stream_max_retries = 10
stream_idle_timeout_ms = 300000

[profiles.step37]
model_provider = "stepfun"
model = "step-3.7-flash"
```

Set the API key in your shell. Do not commit it to this repository.

```powershell
$env:STEPFUN_API_KEY="your-stepfun-api-key"
```

For a persistent Windows environment variable:

```powershell
setx STEPFUN_API_KEY "your-stepfun-api-key"
```

Then restart the terminal.

### Run The Demo With Codex

Create a clean workspace:

```powershell
mkdir job-board-demo-run
cd job-board-demo-run
git init
```

Start Codex CLI with the StepFun profile and goals enabled:

```powershell
codex --enable goals --profile step37 -C . -s workspace-write -a on-request --no-alt-screen
```

Paste this prompt:

```text
Use $job-board-coding to build and verify a runnable job application tracking board in the current workspace.

Please follow the skill workflow: plan the structure, create the project files, install dependencies, run build verification, fix obvious errors, and stop only after the app can be run locally and README is complete.
```

For the full prompt, see [`references/goal-prompt.md`](references/goal-prompt.md).

## Option B: Use With Claude Code

Claude Code does not automatically load Codex skills. Use this repository as a task protocol: clone it into the project workspace and ask Claude Code to read the skill files before implementation.

Create a clean workspace:

```powershell
mkdir job-board-claude-run
cd job-board-claude-run
git init
git clone https://github.com/jjyaoao/job-board-coding.git .skill-job-board-coding
```

Start Claude Code in a supervised mode:

```powershell
claude --permission-mode acceptEdits
```

Then paste the Claude-specific prompt from [`references/claude-code-prompt.md`](references/claude-code-prompt.md).

If you intentionally want a less supervised one-shot run, use Claude Code's bypass mode only inside a clean throwaway workspace:

```powershell
claude --dangerously-skip-permissions
```

Recommended StepFun environment variables for Claude Code / Step Plan:

```powershell
$env:ANTHROPIC_BASE_URL="https://api.stepfun.ai/step_plan"
$env:ANTHROPIC_AUTH_TOKEN="your-stepfun-api-key"
$env:ANTHROPIC_MODEL="step-3.5-flash"
```

Use the StepFun model that your Step Plan subscription supports.

## Evidence To Capture

Recommended screenshots:

- Coding agent setup: Codex profile or Claude Code provider, with API key hidden
- StepFun model/base URL status
- `$job-board-coding` installed or `.skill-job-board-coding` cloned
- Goal prompt submitted
- Agent planning and editing files
- Dependency install and build verification
- Final running job board
- README and project file tree

See [`references/screenshot-checklist.md`](references/screenshot-checklist.md).

## Content Notes

Recommended framing:

- Real engineering task
- First usable version
- Faster path from idea to runnable draft
- Human review and verification still matter

Avoid claims like:

- Replaces programmers
- One-shot perfect production launch
- Zero bugs
- 100% correct
- No code knowledge needed

See [`references/xhs-content-brief.md`](references/xhs-content-brief.md).

## Repository Layout

```text
.
+-- SKILL.md
+-- agents/
|   +-- openai.yaml
+-- references/
    +-- claude-code-prompt.md
    +-- goal-prompt.md
    +-- screenshot-checklist.md
    +-- xhs-content-brief.md
```
