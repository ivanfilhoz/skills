# Repository Guidelines

This repository is a personal skills collection using the skills.sh `SKILL.md` format.

## Tooling

- Each skill lives in a top-level folder named after the skill and contains a `SKILL.md` file with `name` and `description` frontmatter.
- Use `npx skills init <skill-name>` when creating new skills if network access is available, then edit the generated `SKILL.md`.

## Working Conventions

- Keep skills agent-agnostic unless the user explicitly asks for agent-specific metadata or integrations.
- Prefer concise procedural guidance over broad advice, and use progressively disclosed references only when a skill needs more detail.
- Keep this `AGENTS.md` file as the source of truth for repository instructions.
