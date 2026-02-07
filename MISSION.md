

# skyLab — Mission

skyLab is a **personal, local-first laboratory** for scientific work that mixes **SoS (Python + R)** with **DuckDB/SQL** over a **Parquet (.pq) SSOT**.

## What skyLab optimizes for

- **Reliability over novelty**: the default path should “just work”.
- **Low cognitive friction**: one obvious way to start, run, and recover.
- **Reproducibility per project**: each project owns its Python + R environments.
- **Data gravity**: data flows through Parquet + DuckDB, not fragile object passing.
- **Personal-only safety**: localhost-only server, per-project lifecycle, no exposure.

## Success criteria for v1

- Open a folder as a skyLab project.
- Automatically create/restore:
  - Python venv (uv-compatible) + per-project Python kernel
  - renv + per-project R kernel
  - SoS notebook availability
- Start/stop a local JupyterLab session bound to the current project.
- Provide clear logs + a “Doctor” check that explains what is missing and how to fix it.

## Non-goals (v1)

- Multi-user or network access.
- Hosted service / cloud sync.
- Fancy dashboard UI panels (Data Hub, Query Pad, Quarto Preview) — these are v2.
- Reinventing JupyterLab or kernels.

## Decision rule when trade-offs exist

If two solutions are both correct:

1) Prefer the one that **reduces surprises** (predictable environments).
2) Prefer the one that **reduces moving parts** (fewer dependencies).
3) Prefer the one that keeps **Parquet + DuckDB as the data spine**.

---

_End of mission._