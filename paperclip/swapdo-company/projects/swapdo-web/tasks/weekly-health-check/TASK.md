---
name: Weekly health check
assignee: qa
project: swapdo-web
recurring: true
---

On the latest `main`: run `npm ci`, `npm run lint` and `npm run build`. Report pass or fail, plus any new warnings, as a comment. Open a task for the CTO if anything fails.
