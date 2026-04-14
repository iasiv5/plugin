This repository is a GitHub Copilot plugin repository, not an application codebase.

Treat the plugin root as the distribution payload. Keep the plugin portable: prefer relative paths, avoid user-specific absolute paths, and do not assume the presence of `.claude`, `/memories`, or machine-local bootstrap state.

The primary runtime asset in this repository is `skills/`. When adding or modifying a skill, keep the parent folder name identical to the `name` field in `SKILL.md`, preserve referenced resource paths, and avoid introducing environment-specific setup unless it is clearly documented.

When evolving this repository, prefer the smallest plugin surface that solves the task. Add `agents/`, `hooks`, or `.mcp.json` only when the use case truly requires them.

Do not convert this repository into a generic workspace bootstrap repo. Optimize for reusable Copilot plugin assets that can be installed from source.