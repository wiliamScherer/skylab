

# skyLab — Decisions (ADR-lite)

Short, dated notes for key decisions.
Keep them brief: context → decision → consequences.

---

## 2026-02-07 — SoS is the default notebook engine

**Context**
We want first-class multi-language notebooks (Python + R) without fragile bridges.

**Decision**
Use SoS as the default notebook type. Python-only and R-only remain CLI launch options.

**Consequences**
- Clear default workflow.
- Compatibility preserved.
- Multi-language is standard, not an add-on.

---

## 2026-02-07 — DuckDB is always available; Parquet `.pq` is SSOT

**Context**
We need a stable, scalable way to share data across Python and R.

**Decision**
Parquet (`.pq`) in `data/pq/` is the SSOT. DuckDB is always available as the query engine.
A persistent `duckdb/lake.duckdb` file is optional per project.

**Consequences**
- Predictable data spine (SQL over Parquet).
- Faster iteration without heavy infrastructure.
- Optional persistence for advanced use cases.

---

## 2026-02-07 — Per-project environments (uv + renv)

**Context**
Global environments create "works on my machine" failures.

**Decision**
Every project initializes Python venv (uv-compatible) and R renv.
Kernels must be per-project.

**Consequences**
- Higher reliability and reproducibility.
- More setup steps, mitigated by Doctor automation.

---

## 2026-02-07 — Personal-only security defaults

**Context**
A personal lab tool must not accidentally expose a server.

**Decision**
Bind localhost only, random port, token enabled, server lifecycle bound to the open project.

**Consequences**
- Safer defaults.
- No out-of-the-box remote access.

---

_End of decisions._