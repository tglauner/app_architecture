# RUNBOOK

## Production Overview
- DigitalOcean droplet (single server)
- Apache reverse proxy (TLS) -> Uvicorn (localhost)
- Database: Neon Postgres (production), SQLite (local)

## Deploy (high level)
1. Pull latest code on droplet
2. Backend: update venv deps, restart systemd service
3. Frontend: build assets, deploy to served directory
4. Verify health endpoint

## Rollback
- Revert git commit (or checkout previous tag) and redeploy
- Restart services

## Logs
- Apache: /var/log/apache2/*
- systemd backend service: `journalctl -u <service> -n 200 --no-pager`

## Safety
- Never commit secrets
- All secrets via env vars on server
