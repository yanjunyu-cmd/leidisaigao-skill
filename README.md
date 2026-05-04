# Leidisaigao Skill — Self-Evolving AI Meta-Skill

<p align="center"><img src="leidisaigao-logo.png" alt="Leidisaigao" width="300"></p>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Meta%20Skill-blue)](https://claude.ai/code)

> *"每个成功男人背后都应该有一个能干的女人——蕾蒂赛高！"*
>
> *"Behind every successful man stands a capable woman — Leidi is the BEST!"*

**Leidisaigao** is a meta-skill that makes Claude Code agents continuously smarter. It autonomously discovers, evaluates, and installs new capabilities — then cleans up old versions so your disk never fills up.

## What Leidisaigao Does

| Phase | Action |
|-------|--------|
| 🔍 **Search** | Scans GitHub, web, and marketplaces for new MCP servers, plugins, and skills |
| 📊 **Evaluate** | Checks compatibility, usefulness, and whether it duplicates existing tools |
| 📦 **Install** | Downloads to E drive, creates junctions, updates configs |
| 🧪 **Test** | Verifies the new capability loads and works |
| 🧹 **Cleanup** | Runs leidicleanup-skill to remove old versions and duplicate skills |
| 📝 **Log** | Records every upgrade for audit and rollback |

## Why Leidisaigao?

Claude Code's ecosystem evolves fast. New MCP servers, plugins, and skills appear daily. Without Leidisaigao, you'd need to manually search, install, and clean up — wasting time and disk space. Leidisaigao automates the entire self-improvement cycle.

## Quick Start

```bash
git clone https://github.com/yanjunyu-cmd/leidisaigao-skill.git ~/.claude/skills/leidisaigao-skill
```

Then say: **"蕾蒂赛高！升级自己！"** and Leidisaigao activates.

## Dependencies

Leidisaigao works best with:
- [leidicleanup-skill](https://github.com/yanjunyu-cmd/leidicleanup-skill) — Cleanup partner
- GitHub CLI (`gh`) — For searching GitHub repos
- WebSearch — For discovering new tools

## Contributing

**This skill is open for anyone to modify and improve.** Found a better search strategy? A new capability source? Submit a PR!

## License

MIT © 2026 — Free to use, modify, and redistribute.
