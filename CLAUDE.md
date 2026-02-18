# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Ansible Galaxy role (`brianhartsock.osx_terminal_themes`) that downloads and configures macOS Terminal.app themes from the [macos-terminal-themes](https://github.com/lysyi3m/macos-terminal-themes) repository. Requires Ansible >= 2.4, macOS only.

## Architecture

Standard Ansible role layout with a single task file (`tasks/main.yml`) that:
1. Clones the themes git repo to a local directory
2. Checks if the desired theme is already installed via `defaults read`
3. Opens the `.terminal` theme file to install it (if missing)
4. Sets the theme as the default via `osx_defaults`

Role variables (defined in `defaults/main.yml`):
- `osx_terminal_themes_theme` — theme name (default: `Afterglow`)
- `osx_terminal_themes_directory` — clone destination (default: `~/.osx-terminal-themes`)
- `osx_terminal_themes_repo` — themes git repo URL

## Setup

Dependencies are managed with [uv](https://docs.astral.sh/uv/). Install dev tools:
```bash
uv sync
```

## Testing

```bash
uv run ansible-playbook tests/test.yml -i tests/inventory --connection=local
```

## Linting

Pre-commit hooks are configured (`.pre-commit-config.yaml`) for yamllint, ansible-lint, and flake8.

```bash
uv run pre-commit run --all-files
```

Run individually:
```bash
uv run yamllint .
uv run ansible-lint
uv run flake8
```
