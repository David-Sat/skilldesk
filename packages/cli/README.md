# (ノ^_^)ノ┻━┻ SkillDesk

Skill & MCP manager for AI coding agents.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-38bdf8.svg)](https://modelcontextprotocol.io)

SkillDesk scans installed coding agents across your machine to inspect active skills and MCP servers, profile prompt token consumption, and manage updates.

Runs entirely locally on `127.0.0.1` with zero telemetry. Configuration changes create automatic backups in `~/.skilldesk/backups/`.

---

## Quickstart

```bash
# Launch the dashboard in your browser (http://127.0.0.1:4350)
npx skilldesk

# Optional: Run a terminal audit without opening the browser
npx skilldesk audit
```

*(Both `skilldesk` and `skill-desk` command names are supported.)*

---

## Features

- **Cross-Agent Visibility**: Inspect installed skills and MCP servers across Google Antigravity, Claude Code, Cursor, and Windsurf in a unified view.
- **Context Token Profiling**: Measure startup token consumption for each skill to catch overly verbose prompt instructions before they bloat your context window.
- **MCP Version Checks**: Check configured MCP packages against npm, PyPI, and GitHub registries, with one-click version bumps.
- **Safe Modifications**: Delete unused skills or modify configs with automated, timestamped backups saved locally.
- **In-Agent Integration**: Run `skilldesk mcp` to let agents open the dashboard or check skills directly from chat.

---

## Architecture

```text
  Coding Agents                                          Package Registries
  Antigravity · Claude Code · Cursor · Windsurf           npm · PyPI · GitHub
              │                                                   ▲
              ▼                                                   │
  ┌───────────────────────────────────────────────────────────────────────┐
  │ SkillDesk Core                                                        │
  │                                                                       │
  │   • Scanner          Discovers active configs and installed skills    │
  │   • Token Profiler   Estimates prompt weight and flags bloat          │
  │   • Version Checker  Queries upstream registries for package updates  │
  │   • Local HTTP API   Lightweight local server on 127.0.0.1:4350       │
  │   • Safety Store     Automated backups in ~/.skilldesk/backups/       │
  └───────────────────────────────────┬───────────────────────────────────┘
                                      │
                         ┌────────────┴────────────┐
                         ▼                         ▼
                  Web Dashboard              Terminal CLI
                 127.0.0.1:4350              npx skilldesk
```

---

## License

MIT © [David Satomi](https://github.com/David-Sat)
