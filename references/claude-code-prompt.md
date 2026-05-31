# Claude Code Prompt

Use this prompt after cloning this repository into a clean project workspace as `.skill-job-board-coding`.

Recommended command:

```powershell
claude --permission-mode acceptEdits
```

Prompt:

```text
First read `.skill-job-board-coding/SKILL.md` and `.skill-job-board-coding/references/goal-prompt.md`. Treat them as the execution protocol for this project.

Goal: build a runnable "求职申请进度管理看板" from scratch in the current directory.

Follow this process:
1. Briefly summarize the project goal, feature scope, and acceptance criteria you read from the skill.
2. Propose the project structure.
3. Create the project files directly in the current directory.
4. Before installing dependencies, tell me what command you plan to run.
5. Run build verification.
6. If there are obvious errors, keep fixing until `npm run build` passes.
7. Write `README.md`.
8. Finish with an acceptance summary: main files, implemented features, startup command, build result, and follow-up improvements.

Do not only provide code snippets. Complete the project in the current directory.
```

For a less supervised one-shot run in a disposable workspace, start Claude Code with:

```powershell
claude --dangerously-skip-permissions
```

Use this only when the workspace contains no private data or important uncommitted work.
