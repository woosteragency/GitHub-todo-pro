# GitHub-todo-pro

## OmniRoute integration

This project ships [OmniRoute](https://github.com/diegosouzapw/OmniRoute) as its AI gateway — a self-hosted, OpenAI-compatible proxy in front of 290+ LLM providers (OpenAI, Anthropic, Gemini, etc.). The app talks to one stable endpoint instead of wiring a separate SDK per provider.

### Run it

```bash
cp .env.example .env
docker compose up -d
```

Dashboard and API come up at `http://localhost:20128` (API under `/v1`).

### First login

The dashboard's default admin password is `CHANGEME` — **change it immediately** on first login, before exposing the port beyond `127.0.0.1`.

### Using it from the app

Point the app's LLM client at `OMNIROUTE_BASE_URL` (`http://localhost:20128/v1`) with `OMNIROUTE_API_KEY` as the bearer token — same shape as calling the OpenAI API directly. Configure actual provider keys (OpenAI, Anthropic, etc.) inside the OmniRoute dashboard itself; the app only needs the gateway's own key.

### Stopping / data

State (routing config, keys, logs) persists in the `omniroute-data` Docker volume across restarts. `docker compose down` stops the service without deleting that volume; add `-v` to wipe it.
