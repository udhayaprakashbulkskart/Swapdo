---
name: swapdo-safe-change
description: Make a code change to the SWAPDO repo safely, from branch to pull request, without touching production or the shared database.
---

# Safe change to SWAPDO

1. `git fetch origin && git checkout -b <short-task-name> origin/main`
2. `npm ci`
3. For database work, use a local Postgres or a throwaway Neon branch in `.env.local`. Never the real `DATABASE_URL`.
4. Make the smallest change that solves the task.
5. `npm run lint` and `npm run build`. Fix what fails. (`npm test` currently fails at startup on `main` too, so report it but do not block on it.)
6. Commit, push the branch, and open a pull request with: what changed, why, how you checked it, and any database impact.
7. Stop. The owner reviews and merges. Do not merge, deploy, or run migrations.
