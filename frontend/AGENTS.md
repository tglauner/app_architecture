# AGENTS.md — /frontend

## Tech
- React + Vite
- Keep dependencies minimal.

## Conventions
- Prefer functional components.
- Keep API calls in a single client module (e.g., src/api/client.js).
- Env vars: use Vite convention (VITE_*). If adding one, update /.env.example at repo root.

## Quality Gates
- `npm run lint`
- `npm run build`
