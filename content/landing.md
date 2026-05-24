# Clawie

> The open-source framework for running an autonomous software agency.

Teams of AI agents that take ideas from brief to launched product, end to end. In your infrastructure. Under your governance. Every decision auditable. Every configuration version-controlled in git. Every agent rollback-able to last Tuesday with one command.

## Why it exists

Most "agent frameworks" mash four concerns into one — runtime, control plane, security boundary, and evaluation harness — and ship a single layer well while the others rot. The result: agents that stop responding, secrets that leak, work that disappears on restart, regressions that nobody noticed because nobody measured.

Clawie keeps the four layers explicitly separate, swappable, and observable. Every layer earns its keep.

## What v1.0 ships

Every intent runs in an ephemeral Docker container. LLM calls (Anthropic / OpenAI) cost-track to a ledger. A default-deny policy gates sensitive intents through an approval queue. A web dashboard reads the same state as the CLI and REST API. On Linux, [Outcall](https://github.com/outcall-dev/root) adds host-level egress isolation per team. Every state transition lands in a hash-chained audit log you can `VACUUM INTO` and verify.

```bash
node ace task:run --intent echo --payload '"world"'
# task d3f8... → completed
#   result: {"message":"hello: world"}

ANTHROPIC_API_KEY=… node ace task:run --intent chat --payload '{"prompt":"hi"}'
# container spawned, LLM called, cost recorded, audit row chained
```

## Phases shipped

| Tag | Capability |
|---|---|
| v0.1.0 | Durable task lifecycle (state machine + hash-chained audit) |
| v0.2.1 | Container execution — every intent runs in `clawie/agent-runtime` |
| v0.3.0 | Real LLM intent (Anthropic / OpenAI) with cost ledger |
| v0.4.0 | Default-deny policy + approval queue |
| v0.5.2 | Pluggable egress (`null` default, Outcall provider for Linux) |
| v0.6.1 | Dashboard at `/dashboard` — Tasks / Approvals / Audit / Egress / Self-Mods |
| v0.7.1 | Agent files (SOUL.md / AGENTS.yaml / TOOLS.yaml) + `agent.self_mod` intent |
| v0.8.1 | Teams + multi-agent (per-team Outcall network) |
| v0.9.0 | Scheduler + crons (`scheduler:tick` host-cron entry-point) |
| v1.0.0 | Ship-grade: backup/verify, HMAC-signed outbound webhooks, full docs |

See [PHASES.md](https://github.com/clawie-dev/specs/blob/main/PHASES.md) for the
full implementation history.

## Repositories

| Repo | Purpose |
|---|---|
| [clawie](https://github.com/clawie-dev/clawie) | The AdonisJS framework |
| [specs](https://github.com/clawie-dev/specs) | End-goal architecture + 31 feature specs |
| [docs](https://github.com/clawie-dev/docs) | User-facing documentation |
| [agent-runtime](https://github.com/clawie-dev/agent-runtime) | Docker base image (Phase 2+) |
| [schemas](https://github.com/clawie-dev/schemas) | JSON Schemas for every config |
| [default-agency](https://github.com/clawie-dev/default-agency) | 9-agent starter pack (Phase 7+) |
| [sdk-typescript](https://github.com/clawie-dev/sdk-typescript) | Typed REST/WS SDK |
| [outcall-presets](https://github.com/clawie-dev/outcall-presets) | Egress rule packs |
| [market.clawie.dev](https://github.com/clawie-dev/market.clawie.dev) | Plugin marketplace (Phase 10) |
| [.github](https://github.com/clawie-dev/.github) | Org profile |

## License

MIT. Self-hosted forever. Core features never gated.
