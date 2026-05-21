# Skills

Personal agent-agnostic skills for use with [skills.sh](https://skills.sh/).

Each skill lives in a top-level folder and contains a `SKILL.md` file with `name` and `description` frontmatter.

## Skills

- `agentsmd`: Create, update, and maintain an `AGENTS.md` file as the source of truth for repository agent instructions, with a `CLAUDE.md` proxy when needed.

## Usage

Install skills from this repository with:

```sh
npx skills add .
```

List available skills without installing:

```sh
npx skills add . --list
```

## Creating Skills

Create a new skill with:

```sh
npx skills init <skill-name>
```

Then edit `<skill-name>/SKILL.md` to keep the instructions concise, procedural, and agent-agnostic.

## Repository Instructions

`AGENTS.md` is the source of truth for agent guidance in this repository. `CLAUDE.md` is a proxy that points Claude-compatible tools back to `AGENTS.md`.
