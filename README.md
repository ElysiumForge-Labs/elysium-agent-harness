# elysium-agent-harness

Next-generation agent harness for ElysiumForge Labs: a **minimal, auditable core** (Pi-inspired) with **hierarchical orchestration (depth ≤ 2)** and **streaming quality gates** as first-class, opt-in extensions.

Part of [ElysiumForge Labs](https://github.com/ElysiumForge-Labs).

> **Independent research repository.** Not affiliated with, endorsed by, or sponsored by Kinetiq or Hyperliquid. Run agents only against throwaway credentials and sandboxed roots.

## Repository layout

| Path | Role |
| --- | --- |
| Root (`packages/`, `bin/`, `skills/`) | TypeScript / pnpm harness — this README |
| `agent-python/` | Legacy Python v0.16 web harness (FastAPI + Alpine SPA), kept for reference |
| `skills/` | Shipped skills indexed into the CLI (`living-dashboard`, `elysium-swarmloop`, `elysium-bench-operations`) |

## Packages

| Package | Kind | What it gives you |
| --- | --- | --- |
| `@elysium/core` | core | Agent loop, tool system (`read`/`write`/`edit`/`bash`), JSONL session tree, depth-2 orchestrator, quality gate, providers (mock + OpenAI-compatible), typed event bus |
| `@elysium/meta-layer` | extension | Software Factory meta-layer: telemetry, improvement hypotheses, controlled application |
| `@elysium/extension-tools` | extension | `grep`, `glob`, `http_fetch` tools |
| `@elysium/tui` | extension | Readline REPL with live streaming |
| `@elysium/benchmarks` | extension | Benchmark / eval suite |
| `@elysium/cli` | extension | `elysium demo / run / orchestrate` |

## Getting started

Requires Node ≥ 22 and pnpm ≥ 9.

```bash
pnpm install
pnpm build          # typechecks every package
pnpm test           # unit + integration
pnpm demo           # offline end-to-end run on the deterministic mock provider
```

Useful env vars: `ELYSIUM_BASH_TIMEOUT_MS`, `ELYSIUM_SPAWN_TIMEOUT_MS`, `ELYSIUM_RAIN_MS=0`, `ELYSIUM_SKILLS_DIR`.

Legacy Python harness: `cd agent-python && python -m pytest -q` (after a local venv).

## License

See `LICENSE` in this repository.
