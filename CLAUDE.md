# Node-RED Flows — Project Guide

This repo holds the Node-RED flow definitions for the home-automation system. It exists as a separate repo only because Node-RED's Projects feature requires its own dedicated Git repo — the rest of the system (HA config, docs, staging infrastructure) lives in [`garycuppett/homeassistant-config`](https://github.com/garycuppett/homeassistant-config), which is the canonical entry point.

## Read this first

For any non-trivial change in this repo, start with the main project guide and docs over there:

- `homeassistant-config/CLAUDE.md` — entry point, conventions, the system in one paragraph
- `homeassistant-config/docs/nodered/overview.md` — tab-by-tab index of what's in `flows.json`
- `homeassistant-config/docs/workflows/staging.md` — how to edit flows safely (never edit prod NR directly)

## What's in this repo

- `flows.json` — the full Node-RED flow definitions (~11 tabs, ~480 nodes)
- `flows_cred.json` — encrypted credentials, **per-branch** (`main` = prod, `staging` = staging)
- `package.json` — Node-RED dependencies

## Branch model

- `main` — production credentials, deployed to the Pi
- `staging` — staging credentials, used by the Docker Compose stack in `homeassistant-config/staging/`
- Edit on `staging`, never on `main` directly. Use `homeassistant-config/staging/deploy.sh` to merge — it preserves `flows_cred.json` correctly. **Never force-push `main`.**

## Agent skills

### Issue tracker

Issues live as GitHub issues in this repo, managed via the `gh` CLI. See [`docs/agents/issue-tracker.md`](docs/agents/issue-tracker.md).

### Triage labels

Canonical defaults — `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See [`docs/agents/triage-labels.md`](docs/agents/triage-labels.md).

### Domain docs

Single-context layout — one `CONTEXT.md` + `docs/adr/` at the repo root. See [`docs/agents/domain.md`](docs/agents/domain.md).
