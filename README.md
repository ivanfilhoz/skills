# Skills

[![skills.sh](https://skills.sh/b/ivanfilhoz/skills)](https://skills.sh/ivanfilhoz/skills)

Personal agent-agnostic skills for use with [skills.sh](https://skills.sh/).

Each skill lives in a top-level folder and contains a `SKILL.md` file with `name` and `description` frontmatter.

## Skills

- [agentsmd](agentsmd/SKILL.md): Create, update, and maintain `AGENTS.md` as the source of truth for repository agent instructions. Prefer native loading and retain a `CLAUDE.md` import only when compatibility requires it.

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

`AGENTS.md` is the source of truth for agent guidance in this repository. For Claude Code, use a version and configuration that support direct loading; see [Claude compatibility](agentsmd/references/claude-compatibility.md) for prerequisites and fallback options.
