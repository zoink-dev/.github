
# Zoink

**Multi-Framework AI Agent Swarm Orchestration**

Zoink is an open-source CLI, terminal dashboard, and web dashboard for running AI agent swarms inside Docker. Define your team in `swarm.yaml`, launch it with one command, then manage runtime, health, logs, state, task flow, and chat from the CLI, the TUI, or a browser.

```bash
npm install -g @zoink-dev/zoink-cli
zoink config init
zoink up
```

[View on GitHub »](https://github.com/zoink-dev/zoink-cli) &nbsp;·&nbsp; [npm package »](https://www.npmjs.com/package/@zoink-dev/zoink-cli)

---

## What is Zoink?

Zoink is a **multi-framework control plane** for AI agents. v0.3 evolved it from a single-framework orchestrator into a tool that can run [OpenClaw](https://github.com/openclaw/openclaw) and [Hermes](https://hermes-agent.nousresearch.com/) agents **side-by-side in the same swarm**, sharing one Docker network, one workspace, and one Kanban board.

Each agent runs in its own isolated Docker container with persistent state, health checks, resource limits, and bearer-authenticated HTTP access for chat and config reload.

**Who it's for**

- AI-heavy developers building multi-agent workflows on a local machine
- Platform teams running a shared agent control plane behind a daemon
- OSS contributors exploring runtime-agnostic agent orchestration

---

## Features

### Orchestration

- **Multi-framework swarms** — Mix OpenClaw and Hermes via a per-agent `runtime` field
- **Declarative `swarm.yaml` v2.0** — `frameworks`, `runtime`, `provider`, `image`, `profiles`, `cpu_limit`, `memory_limit`, `gateway`, `ports`, `persistState`, `autoPickup`, `temperature`, `skills`, optional `kanban` block
- **One-command lifecycle** — `zoink up` / `zoink down` handles networks, containers, volumes, and the Kanban board
- **Idempotent operations** — Re-run `zoink up` safely; containers are matched by `zoink.swarm` + `zoink.agent` labels
- **Schema validation with line numbers** — `zoink config validate` reports issues with file, line, and column context
- **Graceful config reload** — Hot-applies safe changes (`model`, `temperature`, `skills`) and prompts before restarts for critical changes
- **Starter templates** — `default`, `hybrid`, and `coding-team` via `zoink config init --template`
