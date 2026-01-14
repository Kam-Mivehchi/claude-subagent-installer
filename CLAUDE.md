# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A Bash CLI tool that fetches and installs Claude Code subagents from the [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) repository.

## Commands

```bash
# Run the installer (interactive)
./subagent-installer

# Force overwrite existing agents
./subagent-installer --force

# Show help
./subagent-installer --help
```

## Dependencies

- `gum` - Interactive terminal UI (install: `brew install gum`)
- `curl` - HTTP requests
- `jq` - JSON parsing

## Architecture

Single Bash script (`subagent-installer`) with the following structure:

- **GitHub API functions**: Fetch categories and agent lists from the repository
- **Installed agents detection**: Scans `~/.claude/agents/` (global) and `./.claude/agents/` (local)
- **Interactive menus**: Uses `gum choose` for category/agent selection
- **Installation logic**: Downloads markdown content and writes to appropriate agents folder

## Key Paths

- Global agents: `~/.claude/agents/*.md`
- Local agents: `./.claude/agents/*.md`
- Source repo API: `https://api.github.com/repos/VoltAgent/awesome-claude-code-subagents/contents`
