# Architecture Context

<!-- Keep under ~120 lines when filled. -->

## Stack

| Layer     | Technology                                  | Role |
| --------- | ------------------------------------------- | ---- |
| Server    | [e.g. Python 3.x stdlib: http.server + asyncio] | [Serves the page, JSON API, SSE stream, runs integrations] |
| Frontend  | [e.g. One static HTML file, vanilla JS/CSS]  | [Entire UI; no build step] |
| Integrations | [e.g. tmux, a CLI's hooks, an MCP server]  | [What the tool drives or listens to] |
| Fonts/libs | [e.g. CDN fonts and one JS library, pinned]  | [Role] |

## System Boundaries

- `server/` — [the process: HTTP, SSE, state derivation, subprocess lifecycle]
- `server/hooks/` — [tiny scripts other tools call; append one line and exit]
- `web/` — [the single frontend file; talks only to the API]
- `web/fake/` — [simulated backend for visual work without live integrations]
- `tools/` — [install script, replay/debug utilities]

## Storage Model

- **Config file** (`~/.[tool]/config.json`): [hand-editable settings]
- **Event log** (`~/.[tool]/events.jsonl`): [append-only, replayable]
- **Derived state** (`~/.[tool]/state.json`): [rebuilt on restart]
- **External files the tool reads**: [list; mark read-only]

## Core Entities

| Entity   | Key Fields                 | Relationships |
| -------- | -------------------------- | ------------- |
| [Entity] | [id, name, state, ...]     | [relationships] |
| Event    | ts, subject, kind, payload | belongs to [Entity] |

## Auth and Access Model

- Localhost only; the server binds 127.0.0.1 and refuses other hosts.
- No accounts: anyone at the keyboard is the user.
- [Any per-launch tokens for embedded helpers]

## Environment and Setup

- Env vars: [e.g. none; `TOOL_HOME` overrides the data dir]
- Local services: [binaries on PATH, installed by tools/install.sh]
- Seed data: [e.g. tools/replay.py feeds a recorded event log; ?fake=1 runs the simulator]
- Secrets: [e.g. none]

## Invariants

1. The frontend is one file with no build step; libraries pinned by exact version.
2. The tool never writes to the external files it observes, beyond [its own hook registration].
3. Every state shown derives from the event log plus config; a restart reproduces the view.
4. Hooks return in under 100 ms and never block the host tool; work happens in the server.
5. [Invariant specific to this tool]
