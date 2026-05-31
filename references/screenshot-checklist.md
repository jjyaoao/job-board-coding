# Screenshot Checklist

Capture the process as evidence for a direction-3 Coding Agent demo.

## Codex CLI Setup Evidence

- Codex CLI version
- `~/.codex/config.toml` StepFun provider/profile, with API key hidden
- Terminal environment showing `STEPFUN_API_KEY` exists without printing its value
- Launch command, for example:

```powershell
codex --enable goals --profile step37 -C . -s workspace-write -a on-request --no-alt-screen
```

## Claude Code Setup Evidence

- Claude Code version or `/status`
- CC Switch or Claude Code provider config, with API key hidden
- `ANTHROPIC_BASE_URL` points to StepFun Step Plan
- `ANTHROPIC_MODEL` uses the model supported by the current plan
- `.skill-job-board-coding` cloned in the workspace
- Launch command, for example:

```powershell
claude --permission-mode acceptEdits
```

## Agent Process

- The full goal prompt or its opening section
- Agent reading `SKILL.md` and `references/goal-prompt.md`
- Agent planning the project structure
- Agent creating/editing files
- Dependency installation approval if shown
- Build command output
- Any error and the follow-up fix if one occurs

## Final Product

- Running board overview
- Add/edit form
- Dragging or moved card state
- Deadline reminder/highlight
- Statistics area
- README or file tree
- Build success output

## Privacy

Do not show:

- API keys
- Real private application data
- Personal email, phone number, or resume content
