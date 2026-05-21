---
name: agentsmd
description: Create, update, and maintain a repository AGENTS.md instruction file using progressive disclosure. Use when asked to add or revise AGENTS.md, CLAUDE.md, agent instructions, repo guidance for coding agents, or to consolidate Claude/Codex/Cursor/Gemini instructions into an agent-agnostic source of truth.
---

# AGENTS.md Maintainer

## Goal

Create and maintain a small, accurate `AGENTS.md` that helps agents work in the current repository without wasting instruction budget. Treat `AGENTS.md` as the source of truth for agent instructions, and keep other agent-specific instruction files as lightweight proxies when possible.

This workflow follows the AGENTS.md guidance from https://www.aihero.dev/a-complete-guide-to-agents-md: keep the root file small, avoid stale structure dumps, move narrower rules into progressively disclosed files, and include only guidance that is relevant often enough to justify loading on every session.

## Workflow

1. Inspect the repo before writing instructions.
   - Read any existing `AGENTS.md`, `CLAUDE.md`, `.cursor/rules`, `.github/copilot-instructions.md`, Gemini/Cline/Roo/OpenCode instruction files, and obvious docs that already describe build, test, style, and architecture.
   - Check package manifests and config files before naming tools or commands. Do not invent commands.

2. Decide what belongs in the root `AGENTS.md`.
   - Include a one-sentence project description.
   - Include the package manager or primary build tool only when it is not obvious or when using the wrong one would be costly.
   - Include non-standard build, test, typecheck, lint, or generation commands that agents commonly need.
   - Include repo-wide constraints that apply to nearly every task.
   - Exclude long style guides, obvious advice, volatile file maps, and language-specific details that only apply sometimes.

3. Use progressive disclosure for the rest.
   - Move narrow guidance into existing docs when a good home exists.
   - Otherwise create small, named markdown files such as `docs/agents/typescript.md`, `docs/agents/testing.md`, or package-level `AGENTS.md` files.
   - Link from root `AGENTS.md` with calm, discoverable phrasing such as `For TypeScript conventions, see docs/agents/typescript.md.`
   - In monorepos, keep the root file focused on workspace navigation and shared tooling, then place package-specific details in package-level `AGENTS.md` files.

4. Resolve existing instruction files carefully.
   - If instructions conflict and the correct choice is not obvious from code, ask the user which version to keep.
   - Preserve useful Claude/Cursor/Gemini/etc. guidance by migrating it into `AGENTS.md` or progressively disclosed docs before replacing proxy files.
   - Remove redundant, vague, or overly obvious instructions instead of moving clutter elsewhere.

5. Create or update `CLAUDE.md` as a proxy.
   - Prefer a plain file over a symlink unless the user explicitly asks for symlinks.
   - Its complete contents should be:

```md
@AGENTS.md

IMPORTANT: `./AGENTS.md` is the source of truth for agent instructions in this repo. On every new session, read and follow it before doing any work.
```

6. Verify the result.
   - Re-read the final files for contradictions, broken links, stale paths, and commands that do not exist.
   - If you added or changed commands, run the smallest relevant verification command when practical.
   - Summarize what moved into root `AGENTS.md`, what moved into progressive docs, and any unresolved decisions.

## Root AGENTS.md Shape

Use this shape unless the repository clearly calls for another concise structure:

```md
# Repository Guidelines

This repository is ...

## Tooling

- Use ...
- Run ...

## Working Conventions

- ...

## Further Guidance

- For ..., see ...
```

Keep the file short enough that an agent can read it on every session without distraction. Prefer accurate and minimal over comprehensive.
