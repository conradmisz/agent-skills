# Code Standards

<!-- Keep under ~120 lines when filled. -->

## General

- Keep modules small and single-purpose; the server is a few files, not a framework.
- Fix root causes; a misfiring hook gets fixed in the hook, not patched in the UI.
- Stdlib first. Add a dependency only if the stdlib path costs more than a day.

## Python

- [Version], type hints on every public function.
- Validate every event line and API body before use; malformed input is logged and dropped.
- `asyncio` for I/O; subprocesses via `asyncio.create_subprocess_exec`, never `shell=True` with user data.
- Paths from config go through `pathlib` and are resolved once at load.

## Frontend

- Vanilla JS in one file; state lives in one object; `render()` is idempotent.
- The DOM is rebuilt from state, never mutated ad hoc, except [library-owned regions].
- CDN scripts pinned to exact versions.
- The simulator implements the same API surface as the server.

## Styling

- Colours and fonts come from the tokens in `ui-context.md`; no new hex values without a token.
- [Theme rule — e.g. every control must look like X; screenshot check before merge]

## API and events

- JSON over HTTP on 127.0.0.1; live updates over one SSE stream.
- Event lines are `{ts, subject, kind, ...}`; unknown kinds are kept but ignored.
- Hooks append and exit; they never read state or call the API.

## Data and Storage

- The config file is the only file a human edits; the server rewrites it atomically.
- The event log is append-only and never rewritten.

## Testing and Verification

- Framework: `pytest` for the server; [Playwright] for frontend screenshots and flows.
- Must have tests: event parsing, state derivation, [tool-specific core logic].
- Definition of verified: spec criteria pass, `pytest` passes, and the flow was exercised against a live integration or a replayed event log.
- Never mark work complete on a passing build alone.

## File Organization

- `server/` — [app.py, state.py, ...]
- `web/` — [the single UI file, fake/sim.js]
- `tools/` — [install.sh, replay.py, screenshot.py]
- `tests/` — pytest files mirroring `server/`

## Never Do

- Never write into the external tool's own data files.
- Never add a hook that does network or disk work beyond appending one line.
- Never use `shell=True` with any string that came from outside the codebase.
- Never introduce a build step or a second frontend file for UI.
- [Tool-specific prohibition]
- [Tool-specific prohibition]
