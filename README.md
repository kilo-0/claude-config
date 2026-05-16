# claude-config

Claude Code global configuration — settings, custom agents, and agent memory.

## Install on a new machine

**Windows (PowerShell):**
```powershell
# Clone into your ~/.claude directory (backs up existing files first)
$dest = "$env:USERPROFILE\.claude"
if (Test-Path $dest) { Rename-Item $dest "$dest.bak" }
git clone https://github.com/kilo-0/claude-config $dest
```

**macOS / Linux:**
```bash
# Clone into your ~/.claude directory (backs up existing files first)
[ -d ~/.claude ] && mv ~/.claude ~/.claude.bak
git clone https://github.com/kilo-0/claude-config ~/.claude
```

## Structure

```
~/.claude/
├── settings.json          # Model, voice, cleanup, feature flags
├── settings.local.json    # Permission allowlist (shell, git, npm, web, MCP)
├── agents/
│   ├── aws-builder.md     # AWS architect — CDK, CloudFormation, Terraform
│   ├── aws-python-dev.md  # boto3, Lambda, S3, DynamoDB
│   ├── code-reviewer.md   # Security, correctness, reliability review
│   ├── python-tutor.md    # Beginner Python, pandas, ML (persistent memory)
│   ├── qc-agent.md        # Pre-deploy QC gate
│   └── report-writer.md   # Morning trading email digest
└── agent-memory/
    └── python-tutor/      # Persistent tutoring context across sessions
```

## Updating from another machine

```bash
cd ~/.claude && git pull
```
