# FieldTrack

A multi-tenant app for field sales reps: store visits, GPS check-ins, offline sync, approval workflows and a supervisor dashboard by district.

> **Status: in development.** This repo is the plan and the write-up; the interactive demo is being built next.
> Star or watch the repo to see it land. The live demo link will appear here.

Part of [Julynard Tago-on's portfolio](https://julynardtago-on.netlify.app/#projects). Based on the multi-tenant field-sales platform I work on at CoreProc (#2 contributor by commits).
Client code is private, so this is a clean-room demo with fictional data. No client names or real data.

## What the demo will show

- [ ] **Market switcher**: each market has its own isolated data
- [ ] **Request workflow**: a materials request moves Submit → Supervisor approval → Warehouse → Done; switch roles to approve, reject or return it
- [ ] **Offline sync**: go offline, log store visits with GPS, watch the pending-sync queue, come back online and sync
- [ ] **Language switcher** plus a translation upload that needs a second admin's approval before it goes live
- [ ] Supervisor dashboard grouped by district

Every key action will have an **"In production"** note explaining how the real system does it.

## How the production system works

The real system runs on Laravel. The demo simulates these behaviours in the browser so it can stay fast and always on.

- Database-per-tenant multitenancy: a landlord DB for tenants, one MySQL database and domain per market, a defensive domain tenant finder
- A workflow engine where stages, fields and post-completion actions are PHP classes stored as JSON templates, so new request types need no schema change
- Coverage/jurisdiction hierarchy with snapshot tables, so historical activities keep the coverage they had at the time
- Mobile sync hardened for wide-coverage users (chunked queries under MySQL's placeholder limit, heavy stock creation moved to background jobs)
- Import-driven translations with per-tenant and per-user locale, `Accept-Language` on the API, and maker-checker approval of translation files

## Planned stack

- Vue 3 + TypeScript + Vite
- Tailwind CSS v4
- Pinia (state saved in the browser, with a **Reset demo** button)
- Vitest for the domain logic, ESLint + Prettier + `vue-tsc` in CI
- GitHub Actions → GitHub Pages (free, always on)

## Roadmap

1. Project scaffold, CI (lint, type-check, test, build) and GitHub Pages deploy
2. Domain logic with Vitest tests
3. UI with seeded data, guided steps and "In production" notes
4. Screenshot/GIF in this README and the live demo link

## Author

**Julynard Tago-on**, Laravel / PHP full-stack engineer · [Portfolio](https://julynardtago-on.netlify.app) · [GitHub](https://github.com/Julynard) · [LinkedIn](https://www.linkedin.com/in/julynard-tago-on/)

## License

[MIT](LICENSE)
