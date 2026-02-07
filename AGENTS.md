

# skyLab — Opinionated Architecture Specification

> Personal, local-first, hybrid R + Python laboratory.
> Designed for zero-friction scientific analysis with strong defaults.

---

## 1. Core Principles

- **Personal-only by default**: all execution is local; no remote exposure.
- **Opinionated > configurable**: safe, tested defaults first; advanced options are explicit.
- **Reproducibility per project**: every project owns its environments.
- **Data-first architecture**: data formats and flow are first-class decisions.

---

## 2. Notebook Engine

- **Default**: SoS Notebook
  - Enables multi-language notebooks with Python + R.
- **Optional (CLI-only)**: Python-only or R-only kernels.
  - Treated as launch options, not primary workflows.

---

## 3. Languages

- **Python**: always available via project-local virtual environment.
- **R**: always available via project-local renv.
- **SQL**: first-class citizen via DuckDB.

---

## 4. Data Engine

- **DuckDB is always available** as the SQL/query engine.
- DuckDB may run:
  - **In-memory only** (default), or
  - With a persistent database file (`duckdb/lake.duckdb`) **optionally**, when advanced features are needed.

DuckDB is never the authoritative data store.

---

## 5. Data Storage (SSOT)

- **Authoritative data format**: Apache Parquet
- **Official extension**: `.pq`
- **Single Source of Truth (SSOT)**: `data/pq/`

Rules:
- Data is append-oriented.
- No row-level mutation is assumed.
- Updates are handled via new Parquet files + query logic.

---

## 6. Interoperability (R ↔ Python)

- **Primary bridge**: DuckDB + Parquet
- Direct object exchange between languages is discouraged for non-trivial data.
- SoS variable exchange is allowed only for small, ephemeral objects.

---

## 7. Environments (Mandatory per Project)

Each skyLab project **always** initializes:

- **Python**: project-local virtual environment (`.venv/` or equivalent)
- **R**: `renv/` + `renv.lock`

No global environments are used implicitly.

---

## 8. Kernel Policy

- **Kernels are per-project**.
- Python kernel must point to the project virtual environment.
- R kernel must resolve packages through the project renv.

---

## 9. Security Model

- Jupyter server binds only to `127.0.0.1`.
- Random local port per project session.
- Token-based access always enabled.
- Server lifecycle is strictly bound to the currently opened project.

No network exposure is permitted by default.

---

## 10. Extensions

- skyLab ships with a **fixed, curated set** of Jupyter/SoS extensions.
- An **advanced mode** may allow manual extension management.

Stability > extensibility.

---

## 11. Project Descriptor

Each project may define a `project.sl` file.

Goals:
- TOML/YAML-like syntax
- Easy to parse
- Human-readable

Intended contents:
- Project metadata
- Paths (data, parquet, duckdb)
- Default kernel/engine preferences
- Optional policies (offline-only, no-persisted-db, etc.)

---

## 12. UI Scope (v1)

- Minimal launcher
- Open project
- Start/stop server
- Logs
- Environment checks ("Doctor")

Advanced UI panels (Data Hub, Query Pad, Quarto Preview) are explicitly deferred to v2.

---

## 13. Growth Strategy

- Current scope: **100% personal use**.
- Architecture must not block:
  - multi-project support
  - richer UI
  - future sharing or team use

Scaling is a design constraint, not a current feature.

---

## 14. Non-Goals

- Not a hosted service
- Not a multi-user server
- Not a general-purpose IDE

skyLab is a laboratory, not a platform.

---

_End of specification._