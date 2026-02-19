# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Ansible Galaxy role (`brianhartsock.osx_terminal_themes`) that downloads and configures macOS Terminal.app themes from the [macos-terminal-themes](https://github.com/lysyi3m/macos-terminal-themes) repository. Requires Ansible >= 2.4, macOS only.

## Architecture

Standard Ansible role layout with a single task file (`tasks/main.yml`) that uses FQCNs:
1. Clones the themes git repo to a local directory (`ansible.builtin.git`)
2. Checks if the desired theme is already installed via `defaults read` (`ansible.builtin.command`)
3. Opens the `.terminal` theme file to install it if missing (`ansible.builtin.command`)
4. Sets the theme as the default via `community.general.osx_defaults`

Role variables (defined in `defaults/main.yml`):
- `osx_terminal_themes_theme` — theme name (default: `Afterglow`)
- `osx_terminal_themes_directory` — clone destination (default: `~/.osx-terminal-themes`)
- `osx_terminal_themes_repo` — themes git repo URL
- `osx_terminal_themes_version` — git revision to checkout (commit, tag, or branch)

## Setup

Dependencies are managed with [uv](https://docs.astral.sh/uv/). Install dev tools:
```bash
uv sync
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

## CI

GitHub Actions workflows in `.github/workflows/`:
- **ci.yml** — runs on pushes to `master` and all PRs. Lints with ansible-lint, yamllint, and flake8 via uv.
- **release.yml** — publishes the role to Ansible Galaxy on GitHub release (uses `GALAXY_API_KEY` secret).

## Development Workflow

Follow this workflow for all code changes.

```
Code → Document → Verify → Code Review
  ^                              |
  └──── fix issues ──────────────┘
```

### 1. Code

Make the implementation changes. Use FQCNs, name all tasks, and follow the patterns in existing task files.

### 2. Document

Update README.md and CLAUDE.md to reflect any changes to variables, platforms, commands, or architecture. If the ansible plugin is installed, use the `documentator` agent.

### 3. Verify

Run linters (yamllint, ansible-lint, flake8) and pre-commit hooks. All checks must pass before proceeding. If the ansible plugin is installed, use the `verifier` agent.

### 4. Code Review

Review the changes for Ansible best practices, idempotency, security, cross-platform correctness, and test coverage. If the ansible plugin is installed, use the `code-reviewer` agent.

### 5. Iterate

If verification or code review flags issues, fix them and repeat from step 2. Continue until all checks pass and the review is clean.
