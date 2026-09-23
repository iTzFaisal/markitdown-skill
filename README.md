# MarkItDown Skill

A reusable agent skill for converting local files and supported URLs into Markdown with Microsoft's [MarkItDown](https://github.com/microsoft/markitdown) CLI. It guides the agent through choosing an output path, installing MarkItDown with all optional integrations, running the conversion, and checking the result.

## Install

Install the skill with the [`skills` CLI](https://skills.sh/docs/cli):

```sh
npx skills add iTzFaisal/markitdown-skill
```

The CLI prompts you to choose the agent and installation location. To target Claude Code directly, for example:

```sh
npx skills add iTzFaisal/markitdown-skill --skill markitdown --agent claude-code
```

## Skill files

The skill is mirrored in both supported layouts in this repository:

- `.agents/skills/markitdown/SKILL.md`
- `.claude/skills/markitdown/SKILL.md`

## Requirements

- Network access to install [`uv`](https://docs.astral.sh/uv/) with Astral's official installer when it is missing.
- The MarkItDown CLI. When needed, the skill installs it once with `uv tool install 'markitdown[all]'`; conversions then use the installed `markitdown` command.

## Usage

Ask your agent to convert a supported file or URL to Markdown, for example:

> Convert `report.pdf` to Markdown and save it as `report.md`.

Install MarkItDown and all optional integrations once:

```sh
uv tool install 'markitdown[all]'
```

Then use the installed CLI directly for conversions:

```sh
markitdown 'report.pdf' -o 'report.md'
```

The `[all]` extra includes MarkItDown's optional format integrations.

## Maintaining the mirror

After editing either skill file, copy the updated content to the other location and verify they match:

```sh
cmp -s .agents/skills/markitdown/SKILL.md .claude/skills/markitdown/SKILL.md
```
