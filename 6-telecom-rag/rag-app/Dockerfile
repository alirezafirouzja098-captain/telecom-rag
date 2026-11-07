from python:3.12-slim

copy --from=ghcr.io/astral-sh/uv:0.6.14 /uv /usr/local/bin/uv

workdir /app

env UV_LINC_MODE=copy \
PYTHONUNBUFFERED=1 \
PATH="/app/.venv/bin:$PATH"

copy pyproject.toml uv.lock ./

run --mount=type=cache,target=/root/.cache/uv \
uv sync --frozen --no-dev --no-install-project

copy . .

cmd ["streamlit","run","src/app.py","--server.address=0.0.0.0","--server.port=8501","--server.headless=true"]




