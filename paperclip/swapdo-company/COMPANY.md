---
schema: agentcompanies/v1
kind: company
slug: swapdo
name: SWAPDO
description: AI team that builds, tests and grows the SWAPDO luxury marketplace (Next.js + Prisma + Neon, hosted on Vercel).
version: 0.1.0
license: MIT
goals:
  - Ship a fast, trustworthy luxury marketplace where people buy, sell and swap verified luxury items.
  - Keep production stable. Every change goes through a pull request that the owner reviews and merges.
---

SWAPDO is a luxury marketplace web app. Code lives in https://github.com/udhayapragu/swapdo.

House rules for every agent in this company:

1. Never push to `main`. Work on a branch and open a pull request. Only the human owner merges.
2. Never deploy, promote, or roll back on Vercel yourself.
3. Never run `prisma migrate`, `prisma db push`, seed scripts, or any SQL against a real `DATABASE_URL`.
   Preview and Production may share one database, so treat every database URL as production.
4. Never write passwords, API keys, or database URLs into code, issues, or comments.
5. Run `npm run lint` and `npm run build` before asking for review, and say honestly what passed and what failed.
