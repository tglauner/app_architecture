# AGENTS.md — /backend

## Tech
- FastAPI + Uvicorn (ASGI)
- Pydantic models for request/response
- SQLite local/MVP; Postgres in production (Neon)

## Conventions
- Keep routes grouped by feature (e.g., app/api/routes/*).
- Centralize settings/env parsing (e.g., app/core/config.py).
- DB access via a small, consistent layer; do not sprinkle raw connection code everywhere.
- If adding a new env var, update /.env.example.

## Quality Gates
- App must start: `python -c "from app.main import app; print('ok')"`
- Run tests if present: `pytest`
