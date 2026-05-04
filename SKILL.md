---
name: leidisaigao-skill
description: |
  Self-evolving meta-skill that continuously discovers, evaluates, and installs
  new capabilities for Claude Code agents. Automatically searches for plugins,
  MCP servers, and skills that enhance the agent's abilities, installs them,
  then runs leidicleanup-skill to remove outdated or duplicate skills.
  A self-improving AI that never stops growing.
allowed-tools:
  - Bash
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - WebSearch
  - WebFetch
  - Agent
  - Skill
metadata:
  trigger: |
    Upgrade yourself, find new plugins, install capabilities, self-improve,
    "蕾蒂赛高", self-evolve, discover skills, enhance abilities
  author: leidi (yanjunyu-cmd)
  repository: https://github.com/yanjunyu-cmd/leidisaigao-skill
  license: MIT (open to contributions and modifications by anyone)
---

# Leidisaigao Skill — Self-Evolving AI Meta-Skill

> *"每个成功男人背后都应该有一个能干的女人——蕾蒂赛高！"*

Leidisaigao (蕾蒂赛高) is a meta-skill that makes Claude Code continuously smarter. It periodically searches for new plugins, MCP servers, and skills, installs them, and cleans up outdated ones. Think of it as an AI that upgrades itself.

## Core Loop

```
🔍 Search for new capabilities
    ↓
📊 Evaluate: Is it useful? Compatible?
    ↓ Yes
📦 Install to E:\ClaudeSkills\ or E:\ClaudePlugins\
    ↓
🧪 TEST — Try to run/load the new capability
    ↓
  Works? → ✅ Continue
  Fails? → 🔧 Diagnose & Fix (up to 3 attempts)
    ↓
  Fix #1: Check framework/dependencies → reinstall → retest
  Fix #2: Check language/runtime mismatch → try alt version → retest  
  Fix #3: Check API/network/config → patch → retest
    ↓
  Still fails after 3 attempts?
    ↓ YES
    🗑️ Delete the failed capability completely
    📝 Log: "升级失败~ 欸嘿~ 原能力保留！"
    ✅ Original capability preserved untouched
    ↓ NO (it works now!)
🧹 Run leidicleanup-skill:
  - Remove old/duplicate versions
  - Clean orphaned files
    ↓
📝 Log upgrade to E:\ClaudeMemory\upgrade_log.md
    ↓
Repeat next session (or when triggered)
```

## Test & Troubleshoot Phase

**MANDATORY**: After every install, test the new capability before declaring success.

### Test Procedure
```bash
# For MCP servers: check if process starts and responds
node /e/ClaudePlugins/<name>/server.js --help 2>&1 || echo "FAILED"

# For npm-based tools: verify CLI works
npx <package-name> --version 2>&1 || echo "FAILED"

# For Python/uvx tools: check import
uvx python -c "import <module>" 2>&1 || echo "FAILED"

# For skills: verify SKILL.md is readable and has frontmatter
head -5 /e/ClaudeSkills/<name>/SKILL.md | grep "^---"
```

### Diagnose Failure (3-Attempt Loop)

**Attempt 1 — Framework/Dependencies**:
- Is the runtime installed? (Node.js? Python? uvx?)
- Missing npm dependencies? → `npm install` in the plugin dir
- Missing system libraries? → check with `ldd` or `where`

**Attempt 2 — Language/Runtime Mismatch**:
- ESM vs CommonJS conflict? → try `.mjs` or add `"type":"module"`
- Wrong Node version? → check `engines` in package.json
- Python version mismatch? → try `uvx python@3.11`

**Attempt 3 — Config/Network**:
- API key missing? → check env vars
- Wrong endpoint URL? → try with `--help` flag
- Network blocked? → try with proxy or mirror

### Fallback — Accept Failure Gracefully

After 3 failed fix attempts:
```
1. DELETE the entire failed capability directory
2. Log: "❌ [name] upgrade failed after 3 attempts"
3. Message: "升级 [name] 失败~ 欸嘿~ 蕾蒂没办法！原能力保留！✅"
4. Preserve: Original skill/plugin untouched
5. Record failure reason for future reference
```

**FAILURE LOG FORMAT**:
```
| Date | Capability | Attempts | Final Error | Action |
|------|-----------|----------|-------------|--------|
| 05-05 | playwright | 3 | ESM/CJS conflict | Deleted, original kept |
| 05-05 | serena | 3 | uvx timeout | Deleted, original kept |
```

## Search Sources

### GitHub
```bash
gh search repos "claude-code MCP server" --sort stars --limit 10
gh search repos "claude-code skill plugin" --sort stars --limit 10
```

### Web Search
```
WebSearch: "best Claude Code MCP servers 2026 new"
WebSearch: "Claude Code skills image generation latest"
```

### Official Marketplace
Check `.claude/plugins/marketplaces/claude-plugins-official/external_plugins/` for new entries.

## Installation Rules

1. **Install to E drive** — All plugins/skills go to `E:\ClaudePlugins\` or `E:\ClaudeSkills\`
2. **Create junction to C drive** — `cmd /c "mklink /J C:\Users\烟云\.claude\skills\<name> E:\ClaudeSkills\<name>"`
3. **Update CLAUDE.md** — Add skill reference with trigger words
4. **Test before committing** — Verify the skill loads correctly

## Cleanup (Delegates to leidicleanup-skill)

After every upgrade cycle:
1. Scan for duplicate skills (same function, different versions)
2. Remove failed/incomplete installs
3. Delete skills that were superseded by better alternatives
4. Clean orphaned junctions and symlinks

```bash
# Find duplicate skills
find /e/ClaudeSkills/ -name "SKILL.md" | while read f; do
  skillname=$(basename $(dirname $f))
  echo "$skillname"
done | sort | uniq -d
```

## Upgrade Log

```
E:\ClaudeMemory\upgrade_log.md
| Date | Skill | Version | Action | Result |
|------|-------|---------|--------|--------|
| 05-05 | leidicleanup | v1.1 | upgraded | added dead code scanner |
| 05-05 | leidisaigao | v1.0 | installed | self-evolution meta-skill |
```

## Open Source

This skill is open for contribution. Anyone can add new capabilities, improve the search algorithms, or extend the cleanup procedures. Submit PRs to https://github.com/yanjunyu-cmd/leidisaigao-skill
