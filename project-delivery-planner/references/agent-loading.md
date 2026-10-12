# Verify how generated rules load

Read when the intended coding agent is known. The skill folder and application project are separate locations: installing the skill does not prove that the generated project rules load.

## Identify the host

Use exposed host/session metadata, user context, or an accessible version command where available. If the host is unknown and automatic loading matters, ask which agent will be used. Do not guess from a file extension or change every agent's configuration.

Check current official documentation when the loading decision depends on a version or configuration not already established. If access is unavailable, label the configuration unverified and provide a manual reading instruction.

## Codex

Canonical project rules are normally in the application's `AGENTS.md`. Inspect applicable ancestor/nested instructions and overrides to avoid contradictions. Confirm the intended working directory and applicable file rather than assuming every repository file is loaded globally.

If the host exposes a supported loaded-instructions report, use it as evidence for that session. Otherwise mark the documented path **CONFIGURED, NOT VERIFIED**. A model's ability to quote a file it explicitly opened is not independent startup-loading evidence.

Reference: [official AGENTS.md documentation](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

## Claude Code

Direct `AGENTS.md` loading depends on version/configuration and whether applicable `CLAUDE.md`/local instructions already exist. Check those conditions before choosing an adapter. Do not assume every Claude Code session loads `AGENTS.md` automatically, or that none can.

When canonical rules are not loaded directly and project-local imports are supported, preserve existing `CLAUDE.md` content and add a minimal import such as `@AGENTS.md` using the correct relative path. Keep the canonical rule body in one place. If the import would leave the project or expand access, follow the host's permissions rather than assuming authorization.

Where available, the user can inspect `/context` and its Memory files in the intended session. Record what was actually observed. If only an import has been added, use **CONFIGURED, NOT VERIFIED**; do not claim a new/future session was verified.

Do not change global settings, remove existing instruction files, or create a new chat merely to force loading.

Reference: [official Claude Code memory and AGENTS.md documentation](https://code.claude.com/docs/en/memory#agentsmd).

## Other agents or plain chat

Use the host's official project-instruction mechanism when known and available. Add only a documented, authorized project-local adapter if needed. Otherwise use **MANUAL LOAD REQUIRED** and give an instruction such as:

> Read the application's AGENTS.md and linked project brief before continuing this task. Apply them within the host's instruction hierarchy.

Manual reading applies to the current context; it does not prove persistence across chats. If the host cannot read local files, explain what the user must provide through its supported interface. Do not claim installation, editing tools, or automatic discovery that the host lacks.

## Report evidence accurately

| State | Evidence needed |
| --- | --- |
| VERIFIED LOADED | The host's supported loaded-file/context report identifies the relevant project instruction file for that session. |
| CONFIGURED, NOT VERIFIED | The documented location/import exists, but actual loading has not been observed. |
| MANUAL LOAD REQUIRED | Native loading is absent/unknown; explicit current-session reading is necessary. |

This check should not block creation of the brief/rules when runtime host evidence is unavailable. Report the limitation and a proportionate next verification step.
