# Paperclip for SWAPDO

[Paperclip](https://github.com/paperclipai/paperclip) is an open-source app that runs a team of AI agents like a company.
This folder holds a ready-made **SWAPDO company** for it: a CEO, CTO, Engineer and QA agent who work on this repo
through branches and pull requests.

Paperclip runs **on your own computer or server**, not on Vercel. Nothing in this folder changes the SWAPDO website,
its build, or its database.

## What you get

| Agent    | Reports to | Job |
| -------- | ---------- | --- |
| CEO      | you        | Turns your goals into small tasks |
| CTO      | CEO        | Plans and reviews technical work |
| Engineer | CTO        | Builds features and fixes bugs, opens PRs |
| QA       | CTO        | Tests PRs before you see them |

Plus:

- Project **SWAPDO Web** with this repo as its workspace (`npm ci` on setup).
- Starter task **Launch readiness audit** (assigned to the CTO, read-only, no code changes).
- Weekly routine **Weekly health check** (Mondays 09:00 IST: lint + build on `main`).
- Skill **swapdo-safe-change**: branch, test, open a PR, never merge, deploy, or touch the real database.
- Monthly budgets: CEO $10, CTO $15, Engineer $25, QA $10. Change them in the Paperclip UI.

## Set it up (about 5 minutes)

You need **Node.js 24.11 or newer** and either Claude Code signed in or an `ANTHROPIC_API_KEY`.

```bash
# 1. Install and start Paperclip (opens http://localhost:3100)
npx paperclipai@latest onboard --yes

# 2. In a second terminal, from this repo's root, import the SWAPDO company
npx paperclipai company import ./paperclip/swapdo-company

#    Or straight from GitHub, without cloning:
npx paperclipai company import udhayapragu/swapdo/paperclip/swapdo-company
```

Then in the Paperclip UI:

1. Open the **SWAPDO** company and check the org chart.
2. Add a `GH_TOKEN` secret for the Engineer if you want it to push branches and open PRs.
3. Turn on the agents' heartbeats when you are ready. Imported agents start with heartbeats off.
4. Assign **Launch readiness audit** to start the first piece of work.

## Safety rules baked in

- Agents never push to `main`, never merge, and never deploy. You review and merge every PR.
- Agents never run Prisma migrations, seeds, or SQL against a real `DATABASE_URL`
  (Preview and Production may share one Neon database).
- No secrets are stored in this folder. Paperclip keeps secrets in its own encrypted store.

## Editing the company

The files are plain Markdown (`COMPANY.md`, `agents/*/AGENTS.md`, `projects/**/TASK.md`, `skills/*/SKILL.md`)
plus `.paperclip.yaml` for Paperclip-only settings (adapter, budgets, schedule, workspace).
After changing them, re-import with `--target existing --collision replace`, or edit directly in the UI and export with
`npx paperclipai company export <company-id> --out ./paperclip/swapdo-company`.
