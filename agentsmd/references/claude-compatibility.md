# Claude Code Compatibility

Verified against [Anthropic's memory documentation](https://code.claude.com/docs/en/memory#agentsmd) on 2026-10-28. Recheck the source when observed behavior differs.

## Direct Loading

Require Claude Code 2.1.277+ and its enabled built-in AGENTS.md plugin. Prefer 2.1.281+ for fixes affecting providers and telemetry-disabled sessions. An initial post-upgrade session may still lack support.

The default `claude-md-or-agents-md` mode skips direct loading if `CLAUDE.md`, `.claude/CLAUDE.md`, or `CLAUDE.local.md` exists in the working directory or an ancestor. User-level `~/.claude/CLAUDE.md`, managed instructions, and `.claude/rules/` do not count.

Check `/config` > Project instructions. `claude-md-and-agents-md` loads both; `claude-md` and `managed-only` do not load AGENTS.md directly. Do not change personal or managed settings as a side effect of repository maintenance.

## Compatibility Exceptions

Keep an import when supporting older or unsupported sessions. Direct loading also differs for `InstructionsLoaded` hooks, `--add-dir` instructions, and external imports requiring approval; consult the linked documentation before migrating these workflows.

## Verification

Start a fresh session in the intended working directory and check the startup notice identifying the loaded AGENTS.md. Check nested instructions separately when used. If the session cannot run, retain the existing import unless the project explicitly excludes the unverified environments from support. An existing `@AGENTS.md` import loads content correctly without duplication; removing it is optional.
