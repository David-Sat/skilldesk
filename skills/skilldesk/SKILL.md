---
name: skilldesk
description: Skill & MCP Manager for AI Coding Agents. Use when the user asks to inspect installed skills, manage MCP servers, or check prompt token weights. Also triggered by /skills or /skilldesk.
---

# SkillDesk: Skill & MCP Manager

SkillDesk manages skills and MCP servers across installed agent harnesses (Google Antigravity, Claude Code, Cursor, Windsurf, Cline, Roo Code, Claude Desktop).

## Workflow

### 1. Default Action: Launch the Dashboard
When the user runs `/skills`, `/skilldesk`, or asks to open or inspect their skills:
Call `skilldesk_launch_ui` (or `skill_hub_launch_ui`) to open the local web interface:

```json
{
  "name": "skilldesk_launch_ui"
}
```

Inform the user that the SkillDesk dashboard is open at `http://127.0.0.1:4350`.

### 2. In-Chat Audit (Only When Explicitly Requested)
Only call `skilldesk_audit` if the user specifically asks for an in-chat audit, prompt token breakdown, or text summary (e.g., *"audit my skills"*, *"which skills are heavy?"*):

```json
{
  "name": "skilldesk_audit"
}
```

Provide a concise summary of active harnesses, total skills/MCPs, oversized skills, and pending updates.
