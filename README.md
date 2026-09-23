# MarkItDown Skill

A reusable agent skill for converting local files and supported URLs into Markdown with Microsoft's [MarkItDown](https://github.com/microsoft/markitdown) CLI. It guides the agent through choosing an output path, installing only the needed optional dependencies, running the conversion, and checking the result.

## Skill files

The skill is mirrored in both supported layouts in this repository:

- `.agents/skills/markitdown/SKILL.md`
- `.claude/skills/markitdown/SKILL.md`

Use or copy the directory matching your agent's skill convention. Keep the two `SKILL.md` files identical when making changes.

## Requirements

- [`uv`](https://docs.astral.sh/uv/) for automatically running MarkItDown with format-specific extras.
- The MarkItDown CLI. The skill can use an existing `markitdown` command, install it with `uv tool install markitdown`, or run it with `uvx`.

## Usage

Ask your agent to convert a supported file or URL to Markdown, for example:

> Convert `report.pdf` to Markdown and save it as `report.md`.

For formats with optional integrations, run MarkItDown with the matching extra. For example, PDF conversion:

```sh
uvx --from 'markitdown[pdf]' markitdown 'report.pdf' -o 'report.md'
```

For an input that needs no optional extra, use the installed CLI:

```sh
markitdown 'page.html' -o 'page.md'
```

The skill's optional-extra guide covers PDF, DOCX, PPTX, XLSX, XLS, Outlook files, audio transcription, and YouTube transcription. It also explains when cloud services or plugins require explicit user direction.

## Maintaining the mirror

After editing either skill file, copy the updated content to the other location and verify they match:

```sh
cmp -s .agents/skills/markitdown/SKILL.md .claude/skills/markitdown/SKILL.md
```
