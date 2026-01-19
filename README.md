# app_architecture
AI guidance for app architectures across all areas of Tim's applications and lectures

## Start a new project (template)
This repo is a template for structure and conventions. Create a new repo from it, then scaffold the actual app code.

1. Create a new repo from this template (or clone and re-init).
2. Scaffold `frontend/` and `backend/`; keep `frontend/AGENTS.md` and `backend/AGENTS.md` in place.
3. Add `.env.example` for any env vars; keep `.env` out of git.
4. Verify local dev.

Example scaffold (fresh repo):
```bash
mkdir -p frontend backend

# frontend (Vite + React)
npm create vite@latest frontend -- --template react
cd frontend && npm ci && cd ..

# backend (FastAPI)
cd backend
python -m venv .venv
source .venv/bin/activate
pip install fastapi uvicorn[standard]
mkdir -p app
cat > app/main.py <<'PY'
from fastapi import FastAPI

app = FastAPI()

@app.get("/health")
def health():
    return {"ok": True}
PY
cat > requirements.txt <<'REQ'
fastapi
uvicorn[standard]
REQ
```

Run locally:
```bash
cd frontend && npm run dev
cd backend && source .venv/bin/activate && uvicorn app.main:app --reload
```

Note: if `frontend/` or `backend/` already exist (because you used this repo as the starting point), scaffold into a temp dir and move the generated files in, leaving the `AGENTS.md` files intact.

## Refactor an existing repo to match this standard
1. Baseline current behavior with a smoke check or tests.
2. Introduce the standard layout using `git mv` where possible.
3. Migrate to Vite (frontend) and FastAPI (backend) in phases, starting with entrypoints.
4. Centralize config/env parsing, add `.env.example`, and remove secrets from git.
5. Update deploy notes to match Apache + systemd and run the quality gates.

## Pull selected files into a repo that does not fully match
If a repo cannot adopt everything here, pull the pieces you want and document the deviations.

1. Copy the docs and conventions you want: `AGENTS.md`, `ARCHITECTURE.md`, `RUNBOOK.md`, and the `AGENTS.md` files under `frontend/` and `backend/`.
2. Keep your existing stack and apply only the relevant conventions.
3. Add a short "Deviations" note in your README so future work stays consistent.
