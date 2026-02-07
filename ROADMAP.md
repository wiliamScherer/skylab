

# skyLab — Roadmap

This roadmap is intentionally minimal.
The goal is to prevent scope drift and keep v1 boring, stable, and useful.

---

## v0.1 — Launcher that always opens

- Create a Tauri app that:
  - selects an existing folder (project root)
  - starts a local JupyterLab session for that folder
  - embeds the JupyterLab UI in a webview
  - stops the server when the project is closed
- Hardening defaults:
  - bind `127.0.0.1` only
  - random port
  - token always enabled
  - no accidental network exposure
- Show server logs in-app.

## v0.2 — Doctor (bootstrap + diagnostics)

- Detect whether the folder is already a skyLab project (`project.sl`).
- If not, initialize a project skeleton:
  - `renv/` + `renv.lock`
  - Python venv (uv-compatible) + lock files
  - default folder layout (`data/pq/`, `notebooks/`, `scripts/`)
- Provide “Doctor” checks:
  - Python present / correct interpreter
  - JupyterLab installed
  - SoS installed and available
  - R present
  - IRkernel installed + kernelspec registered
  - renv initialized/restored
- Provide guided fix actions (one-click or copy/paste commands).

## v0.3 — Opinionated defaults

- New notebook defaults to SoS.
- CLI options to start with Python-only or R-only kernel.
- Curated extension set + explicit advanced mode.
- Parquet `.pq` conventions enforced by templates.

## v1.0 — Polished personal tool

- Smooth UX for open/start/stop/reopen.
- Clear error messages and recovery paths.
- Minimal, stable feature set.

---

## v2+ (explicitly not v1)

- Data Hub (Parquet/DuckDB browser)
- Query Pad (SQL workspace)
- Quarto Preview/Render UI
- Rich dashboards
- Team/multi-user modes

---

_End of roadmap._