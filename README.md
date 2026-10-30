# elysium-agent-harness

Minimal, auditable agent harness for ElysiumForge Labs research — a Pi-inspired core with hierarchical orchestration (depth ≤ 2) and streaming quality gates as first-class, opt-in extensions.

Part of [ElysiumForge Labs](https://github.com/ElysiumForge-Labs).

> **Independent research repository.** Not affiliated with, endorsed by, or sponsored by Kinetiq or Hyperliquid. Run agents only against throwaway credentials and sandboxed workspace roots.

## Features

- Agent loop with a small tool surface (`read` / `write` / `edit` / `bash`)
- JSONL session tree and typed event bus
- Depth-2 orchestrator for controlled sub-agent work
- Streaming quality gates as an opt-in extension
- Providers: deterministic mock and OpenAI-compatible HTTP
- CLI: `elysium demo`, `run`, and `orchestrate`
- Shipped skills: `living-dashboard`, `elysium-swarmloop`, `elysium-bench-operations`

## Packages

| Package | Kind | Role |
| --- | --- | --- |
| `@elysium/core` | core | Agent loop, tools, session tree, orchestrator, quality gate, providers, event bus |
| `@elysium/meta-layer` | extension | Software Factory meta-layer: telemetry, improvement hypotheses, controlled application |
| `@elysium/extension-tools` | extension | `grep`, `glob`, `http_fetch` |
| `@elysium/tui` | extension | Readline REPL with live streaming |
| `@elysium/benchmarks` | extension | Benchmark and eval suite |
| `@elysium/cli` | extension | CLI entry points |

## Layout

| Path | Role |
| --- | --- |
| `packages/` | TypeScript packages (pnpm workspace) |
| `bin/` | CLI entry scripts |
| `skills/` | Shipped skills indexed into the CLI |
| `examples/` | Offline demo runner |
| `agent-python/` | Legacy Python v0.16 web harness (FastAPI + Alpine SPA), kept for reference |
| `docs/` | Design notes |

## Stack

| Item | Value |
| --- | --- |
| Language | TypeScript (Node ≥ 22) |
| Package manager | pnpm ≥ 9 |
| Tests | Vitest |
| Lint / format | Biome |
| Legacy harness | Python (FastAPI) under `agent-python/` |

## Getting started

### Prerequisites

| Program | Version |
| --- | --- |
| Node.js | ≥ 22 |
| pnpm | ≥ 9 |

### Install, build, test

```bash
pnpm install
pnpm build          # typechecks every package
pnpm test           # unit + integration
pnpm demo           # offline end-to-end run on the deterministic mock provider
```

Useful environment variables: `ELYSIUM_BASH_TIMEOUT_MS`, `ELYSIUM_SPAWN_TIMEOUT_MS`, `ELYSIUM_RAIN_MS=0`, `ELYSIUM_SKILLS_DIR`.

Legacy Python harness:

```bash
cd agent-python
python -m venv .venv && .venv/bin/pip install -r requirements.txt
.venv/bin/python -m pytest -q
```

## Security

- Prefer the mock provider for local demos.
- Restrict bash and file tools to a sandboxed root.
- Do not point live providers at production credentials from this repository.

## License

See `LICENSE` in this repository.
