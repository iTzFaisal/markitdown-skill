# Repository guide

- This repository contains one MarkItDown skill, mirrored at `.agents/skills/markitdown/SKILL.md` and `.claude/skills/markitdown/SKILL.md`; keep both copies identical when editing.
- There are no package manifests or build, lint, or test configuration files. For skill-only changes, validate the mirror with `cmp -s .agents/skills/markitdown/SKILL.md .claude/skills/markitdown/SKILL.md`.
