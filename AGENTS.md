# Agent notes

- Single service: FastAPI (`committee.api:app`) serves both `/api/*` and the static `web/` UI. Compose runs uvicorn directly on 0.0.0.0:8000 (host 3000) because `committee serve` binds 127.0.0.1.
- Reload watches `backend/src` and `web/`. The venv lives in a Docker volume; `uv sync --frozen` runs at startup.
- `OPENAI_API_KEY` is optional: without it `/api/config` lists only the `mock` provider. Use `synthetic` data to avoid Yahoo network calls.
- Tests: `docker compose -f docker-compose.base44.yml exec app uv run pytest`.
