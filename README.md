

# skyLab

A **personal, local-first laboratory** for scientific work that mixes **SoS (Python + R)** with **DuckDB/SQL** over a **Parquet (`.pq`) SSOT**.

skyLab is intentionally **opinionated**: it chooses strong defaults to reduce friction and surprises.

## What skyLab is

- A Tauri desktop app that launches a **local JupyterLab** session for a single project.
- **SoS is the default** notebook engine (Python + R in the same notebook).
- **DuckDB is always available** as the SQL engine.
- **Parquet (`.pq`) in `data/pq/` is the SSOT** (Single Source of Truth).
- **Per-project environments**: `uv`-compatible Python venv + `renv`.

## What skyLab is not

- Not a hosted service.
- Not multi-user.
- Not a general-purpose IDE.

## Project status

Work-in-progress. v1 is focused on a boring, stable launcher + Doctor (bootstrap/diagnostics).

See:
- `AGENTS.md` — Opinionated architecture specification
- `MISSION.md` — Mission and v1 success criteria
- `ROADMAP.md` — Minimal roadmap (prevents scope drift)
- `DECISIONS.md` — ADR-lite decisions log

## Core architecture (TL;DR)

- **Notebook engine**: SoS default; Python-only / R-only as CLI launch options.
- **Data spine**: Parquet `.pq` (SSOT) + DuckDB SQL.
- **Interop**: data moves via DuckDB/Parquet (not fragile object passing).
- **Security**: localhost only, random port, token always enabled; server lifecycle bound to the open project.

## License

Planned license: **MIT** (permissive and broadly compatible with typical Rust/Python/R dependencies).

---

_This is a personal tool. Defaults are strict on purpose._