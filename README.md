# LogCopilot

A multi-tenant security and log-analysis platform for SMBs. Organizations
register, connect their assets (GitHub repos, log sources, cloud accounts), and
get findings explained in plain English by an LLM. Internally the backend is
branded "SurfaceAI – Attack Surface Monitor".

## What it does

- **Attack surface** — register GitHub repositories and scan them for exposure
  findings (`/api/attack-surface`).
- **Log intelligence** — register log sources and run anomaly detection over
  ingested logs (`/api/logs`).
- **Cloud monitor** — track cloud accounts and network findings (`/api/cloud`).
- **Pentest** — record pentest sessions and findings (`/api/pentest`).
- **Dashboard** — unified summary across all finding types (`/api/dashboard`).
- **AI explanations** — OpenAI turns technical findings into business-friendly
  explanations and remediation steps.
- **Multi-tenant** — JWT auth with users, organizations, members, and
  per-organization data isolation; subscription records per organization.

## Stack

- **Backend:** Node.js + TypeScript, Express, PostgreSQL (`pg`), JWT auth
  (`jsonwebtoken` + `bcryptjs`), `zod`, OpenAI SDK, Winston logging.
- **Frontend:** Next.js (App Router) + React, TanStack Query, Zustand, Axios,
  Tailwind/`globals.css`, `lucide-react`.
- **Infra:** `docker-compose.yml` runs Postgres + backend + frontend.

## Backend setup

```bash
cd backend
npm install
npm run migrate      # apply src/db/migrations against DATABASE_URL
npm run dev          # tsx watch on PORT (default 3001)
npm run build        # tsc -> dist/
npm start            # node dist/index.js
```

Environment variables (see `docker-compose.yml` for examples):

| Variable | Description |
| --- | --- |
| `DATABASE_URL` | PostgreSQL connection string |
| `JWT_SECRET` | Secret used to sign auth tokens |
| `JWT_EXPIRES_IN` | Token lifetime (default `7d`) |
| `OPENAI_API_KEY` | Key for AI explanations |
| `PORT` | Backend port (default `3001`) |
| `FRONTEND_URL` | Allowed CORS origin |

Health check: `GET /health`.

## Run with Docker

```bash
docker compose up
```

Starts Postgres, the backend (`:3001`), and the frontend (`:3000`).

> Note: the `frontend/` app is wired against the backend API but does not yet
> ship its own `package.json`; the backend is the buildable, tested component.

## Repository structure

```text
backend/    # Express + TypeScript API, Postgres schema/migrations, OpenAI service
frontend/   # Next.js App Router UI (login, organizations, attack-surface, dashboard)
docs/       # architecture and roadmap notes
docker-compose.yml
```
