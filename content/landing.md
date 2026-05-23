# Clawie

> The open-source framework for running an autonomous software agency.

Teams of AI agents that take ideas from brief to launched product, end to end. In your infrastructure. Under your governance. Every decision auditable. Every configuration version-controlled in git. Every agent rollback-able to last Tuesday with one command.

## Why it exists

Most "agent frameworks" mash four concerns into one — runtime, control plane, security boundary, and evaluation harness — and ship a single layer well while the others rot. The result: agents that stop responding, secrets that leak, work that disappears on restart, regressions that nobody noticed because nobody measured.

Clawie keeps the four layers explicitly separate, swappable, and observable. Every layer earns its keep.

## What v0.1.0 ships

The smallest possible vertical slice: a durable task lifecycle, audited via hash-chained immutable log, exposed via CLI and REST. No LLMs, no Docker, no Outcall yet — those land in later phases. v0.1.0 is the foundation everything else extends.

```bash
node ace task:run --intent echo --payload '"world"'
# task d3f8... → completed
#   result: {"message":"hello: world"}
```

## Roadmap

| Version | Capability |
|---|---|
| v0.1.0 | Durable task lifecycle |
| v0.2.0 | Tasks run inside ephemeral Docker containers |
| v0.3.0 | Real LLM via model router |
| v0.4.0 | Policy engine + approval queue |
| v0.5.0 | Outcall sidecar (egress isolation) |
| v0.6.0 | Dashboard MVP |
| v0.7.0 | Agent files + self-modification PRs |
| v0.8.0 | Teams + multi-agent flows |
| v0.9.0 | Scheduler + dual-mode crons |
| v1.0.0 | Full software agency pipeline, Linear/Jira drivers, backup, upgrades, webhooks, marketplace |

See [PHASES.md](https://github.com/clawie-dev/specs/blob/main/PHASES.md).

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
