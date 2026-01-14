# Claude Code Subagent Installer

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Made with Bash](https://img.shields.io/badge/Made%20with-Bash-1f425f.svg)](https://www.gnu.org/software/bash/)
[![Works with Claude Code](https://img.shields.io/badge/Works%20with-Claude%20Code-blueviolet)](https://claude.ai/code)

A friendly CLI tool that makes it easy to browse, discover, and install Claude Code subagents from the community-curated [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) repository.

![Demo](https://via.placeholder.com/800x400?text=Interactive+Terminal+Demo)

---

## :zap: Quick Start

For experienced users who want to get going fast:

```bash
# Install dependencies (macOS)
brew install gum curl jq

# Clone and run
git@github.com:Kam-Mivehchi/claude-subagent-installer.git
cd claude-subagent-installer
./subagent-installer
```

That's it! Follow the interactive prompts to install your first subagent.

---

## :sparkles: Features

- **:mag: Browse 100+ Subagents** - Explore agents across 10 categories including Core Development, Infrastructure, Quality & Security, Data & AI, and more
- **:package: One-Click Install** - Download and install agents to your global or local Claude agents folder
- **:eyes: Installation Status** - See which agents you already have installed at a glance
- **:repeat: Reinstall Support** - Easily update or reinstall existing agents with the `--force` flag
- **:art: Beautiful UI** - Interactive menus powered by [gum](https://github.com/charmbracelet/gum) for a delightful terminal experience
- **:globe_with_meridians: Global or Local** - Install agents globally (`~/.claude/agents/`) or locally (`./.claude/agents/`) for project-specific setups

---

## :open_book: Table of Contents

- [Quick Start](#zap-quick-start)
- [Features](#sparkles-features)
- [Installation](#wrench-installation)
  - [Prerequisites](#prerequisites)
  - [Installing Dependencies](#installing-dependencies)
  - [Getting the Installer](#getting-the-installer)
  - [Adding to PATH (Optional)](#adding-to-path-optional)
- [Usage](#rocket-usage)
  - [Basic Usage](#basic-usage)
  - [Command Line Options](#command-line-options)
  - [Examples](#examples)
- [How It Works](#gear-how-it-works)
- [Available Categories](#card_file_box-available-categories)
- [Troubleshooting](#ambulance-troubleshooting)
- [Contributing](#handshake-contributing)
- [License](#page_facing_up-license)

---

## :wrench: Installation

### Prerequisites

This tool requires the following dependencies:

| Dependency | Purpose | Required |
|------------|---------|----------|
| `gum` | Interactive terminal UI menus | Yes |
| `curl` | Downloading files from GitHub | Yes |
| `jq` | Parsing JSON responses | Yes |

### Installing Dependencies

#### macOS (Homebrew)

```bash
# Install all dependencies at once
brew install gum curl jq
```

#### Linux (Debian/Ubuntu)

```bash
# Install curl and jq
sudo apt-get update
sudo apt-get install curl jq

# Install gum (see https://github.com/charmbracelet/gum#installation)
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://repo.charm.sh/apt/gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/charm.gpg
echo "deb [signed-by=/etc/apt/keyrings/charm.gpg] https://repo.charm.sh/apt/ * *" | sudo tee /etc/apt/sources.list.d/charm.list
sudo apt update && sudo apt install gum
```

#### Linux (Fedora)

```bash
# Install curl and jq
sudo dnf install curl jq

# Install gum
echo '[charm]
name=Charm
baseurl=https://repo.charm.sh/yum/
enabled=1
gpgcheck=1
gpgkey=https://repo.charm.sh/yum/gpg.key' | sudo tee /etc/yum.repos.d/charm.repo
sudo dnf install gum
```

#### Linux (Arch)

```bash
# Install all dependencies
sudo pacman -S curl jq gum
```

### Getting the Installer

#### Option 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/claude-subagent-installer.git
cd claude-subagent-installer
```

#### Option 2: Download Directly

```bash
curl -O https://raw.githubusercontent.com/YOUR_USERNAME/claude-subagent-installer/main/subagent-installer
chmod +x subagent-installer
```

### Adding to PATH (Optional)

To run `subagent-installer` from anywhere on your system:

#### Option A: Symlink to /usr/local/bin

```bash
# From the repository directory
sudo ln -s "$(pwd)/subagent-installer" /usr/local/bin/subagent-installer
```

#### Option B: Add to your shell's PATH

Add the repository directory to your PATH by adding this line to your shell config file (`~/.bashrc`, `~/.zshrc`, etc.):

```bash
export PATH="$PATH:/path/to/claude-subagent-installer"
```

Then reload your shell:

```bash
source ~/.zshrc  # or ~/.bashrc
```

#### Option C: Copy to a directory already in PATH

```bash
cp subagent-installer ~/.local/bin/
# Make sure ~/.local/bin is in your PATH
```

---

## :rocket: Usage

### Basic Usage

Simply run the installer and follow the interactive prompts:

```bash
./subagent-installer
```

You'll be guided through:
1. **Select a category** - Choose from 10 different agent categories
2. **Select an agent** - Pick the specific agent you want (installed agents are marked)
3. **Choose install location** - Global (`~/.claude/agents/`) or Local (`./.claude/agents/`)
4. **Continue or exit** - Install more agents or finish

### Command Line Options

| Option | Description |
|--------|-------------|
| `-h`, `--help` | Show help message and exit |
| `-f`, `--force` | Overwrite existing agents without prompting |

### Examples

#### Interactive Mode (Default)

```bash
./subagent-installer
```

This launches the interactive menu where you can browse categories, see which agents are installed, and select agents to install.

#### Force Overwrite Mode

```bash
./subagent-installer --force
```

Use this when you want to update agents to the latest version. This will overwrite existing agents without asking for confirmation.

#### Show Help

```bash
./subagent-installer --help
```

Displays usage information and available options.

---

## :gear: How It Works

1. **Fetches Categories** - The installer queries the GitHub API to get the list of available agent categories from the [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) repository.

2. **Lists Agents** - When you select a category, it fetches all available agents (markdown files) in that category.

3. **Checks Installation Status** - The tool scans your global (`~/.claude/agents/`) and local (`./.claude/agents/`) folders to show which agents you already have installed.

4. **Downloads and Installs** - When you select an agent, the installer downloads the raw markdown content from GitHub and saves it to your chosen location.

### Where Agents Are Installed

| Location | Path | Use Case |
|----------|------|----------|
| **Global** | `~/.claude/agents/` | Available in all projects |
| **Local** | `./.claude/agents/` | Project-specific agents |

After installation, use `/agents` in Claude Code to see your installed agents.

---

## :card_file_box: Available Categories

The installer gives you access to 100+ specialized subagents across these categories:

| Category | Description |
|----------|-------------|
| **Core Development** | Essential coding tasks - API design, frontend/backend work, mobile development |
| **Language Specialists** | Experts in Python, JavaScript, Go, Rust, and other languages |
| **Infrastructure** | DevOps, cloud platforms, Kubernetes, database administration |
| **Quality & Security** | Testing, code review, security auditing, accessibility compliance |
| **Data & AI** | Machine learning, data engineering, analytics, NLP |
| **Developer Experience** | Build systems, CLI tools, documentation, refactoring |
| **Specialized Domains** | Blockchain, game dev, IoT, fintech, embedded systems |
| **Business & Product** | Project management, product strategy, technical writing |
| **Meta & Orchestration** | Multi-agent coordination, workflow automation |
| **Research & Analysis** | Market research, competitive intelligence, trend analysis |

---

## :ambulance: Troubleshooting

### "Missing required dependencies" Error

**Problem:** The installer shows an error about missing dependencies.

**Solution:** Install the missing dependencies listed in the error message:

```bash
# macOS
brew install gum curl jq

# Ubuntu/Debian
sudo apt-get install curl jq
# Then install gum from Charm's repository (see Installation section)
```

### "GitHub API rate limit exceeded" Error

**Problem:** You see a rate limit error when trying to fetch categories or agents.

**Solution:** GitHub's API has rate limits for unauthenticated requests (60 requests/hour). Wait a few minutes and try again. This is rare under normal usage.

### Agent Already Exists Warning

**Problem:** You see "Agent 'agent-name.md' already exists" when trying to install.

**Solution:** You have two options:
- Run with `--force` to overwrite: `./subagent-installer --force`
- Choose "Yes" when prompted to reinstall/overwrite in interactive mode

### "Command not found: gum" Error

**Problem:** After installing gum, you still get "command not found".

**Solution:** Make sure gum is in your PATH. Try:
```bash
# Check if gum is installed
which gum

# If not found, you may need to restart your terminal or run:
hash -r  # Bash
rehash   # Zsh
```

### Permission Denied When Running

**Problem:** `./subagent-installer: Permission denied`

**Solution:** Make the script executable:
```bash
chmod +x subagent-installer
```

### Agents Not Showing in Claude Code

**Problem:** Installed agents don't appear when using `/agents` in Claude Code.

**Solution:**
1. Verify the agent file exists:
   ```bash
   ls ~/.claude/agents/      # Global agents
   ls ./.claude/agents/      # Local agents (in current directory)
   ```
2. Make sure the agent file has the `.md` extension
3. Try restarting Claude Code

### Network/Connection Issues

**Problem:** "Failed to fetch categories from GitHub API"

**Solution:**
1. Check your internet connection
2. Verify you can reach GitHub: `curl -I https://api.github.com`
3. If you're behind a proxy, configure your proxy settings for curl

---

## :handshake: Contributing

Contributions are welcome! Here's how you can help:

1. **Report Bugs** - Open an issue describing the problem and steps to reproduce
2. **Suggest Features** - Have an idea? Open an issue to discuss it
3. **Submit PRs** - Fork the repo, make your changes, and submit a pull request

### Want to Contribute Subagents?

The subagents themselves live in the [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) repository. Head there to contribute new agents!

---

## :page_facing_up: License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## :star: Acknowledgments

- [VoltAgent](https://github.com/VoltAgent) for maintaining the awesome-claude-code-subagents repository
- [Charmbracelet](https://github.com/charmbracelet) for the fantastic `gum` library
- The Claude Code community for building amazing subagents

---

<p align="center">
  Made with :heart: for the Claude Code community
</p>
