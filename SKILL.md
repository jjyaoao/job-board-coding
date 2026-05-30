---
name: job-board-coding
description: Build and document a direction-3 Coding Agent demo for a practical job application tracking board. Use when Codex should use a StepFun/Step 3.7 Flash powered coding workflow to create, verify, or explain a React + TypeScript + Vite job-search kanban app with drag-and-drop stages, deadline reminders, localStorage persistence, README, screenshot evidence, or Xiaohongshu-ready process documentation.
---

# Job Board Coding

Use this skill to run a practical Coding Agent demo: a job application progress board for internship, campus recruiting, and job-search tracking. The goal is to show a real engineering workflow, not a toy code snippet.

## Default Outcome

Create a runnable React + TypeScript + Vite app in the current workspace:

- Job stages: `已投递`, `笔试中`, `面试中`, `已拿 Offer`, `已拒绝`
- Application cards with company, role, direction, applied date, deadline, priority, notes, and next action
- Add, edit, delete, drag between stages, sort by priority/deadline
- Seven-day deadline reminders and highlighted urgent cards
- Dashboard stats: total applications, interview conversion, offer count, seven-day deadlines
- Stage distribution and role-direction distribution
- Realistic fictional seed data
- localStorage persistence
- Polished, practical UI suitable for screenshots
- README with setup, usage, feature list, and local data notes
- Verification by installing dependencies and running build

If the user asks for the reusable prompt rather than implementation, read `references/goal-prompt.md` and adapt it.

## Workflow

1. Confirm the current directory is the intended project workspace.
2. Plan the project structure briefly.
3. Create the app files directly; do not only provide snippets.
4. Use conservative dependencies. Prefer built-in React state and browser drag events unless a drag library is clearly worth it.
5. Keep data local. Do not add a backend or app-side API key unless explicitly requested.
6. Run installation and verification commands, typically `npm install` and `npm run build`.
7. Fix obvious build or runtime errors until the first pass is runnable.
8. Leave a clear final summary with startup command, verification result, and follow-up ideas.

## StepFun / Step 3.7 Flash Framing

For the commercial demo, the important proof is that Codex CLI or another coding agent is configured to use StepFun `step-3.7-flash` as the coding model. The generated job-board app itself does not need to call StepFun API unless the user specifically asks for an AI feature inside the app.

Never write API keys into files, screenshots, README, logs, or generated code. Use environment variable names such as `STEPFUN_API_KEY`.

## UI Direction

Make the app feel like a useful productivity tool:

- Dense but readable layout
- Neutral background with restrained accent colors
- Clear cards and columns
- No landing page
- No oversized marketing hero
- No decorative gradient blobs or one-note purple/blue theme
- Responsive enough for desktop screenshots and basic mobile use

## Evidence Capture

When preparing screenshots or a post, read `references/screenshot-checklist.md`.

The strongest proof points are:

- Codex CLI profile points to StepFun model provider without exposing key
- Goal prompt submitted
- Agent plan and file edits
- Build/test output
- Final running board
- README and file structure

## Content Boundary

When writing Xiaohongshu copy or commercial notes, read `references/xhs-content-brief.md`.

Use measured language:

- Say “first usable version”, “可运行初稿”, “减少从想法到初版的时间”
- Avoid “替代程序员”, “一次完美上线”, “零 bug”, “不用懂代码”, “100% 正确”

