# 🧹 Auto-Tidy

> **Zero-effort file organization for Claude Code**
> Say "goodnight" and your project gets organized automatically.

[![Made by Washin Village](https://img.shields.io/badge/Made%20by-Washin%20Village%20🐾-orange)](https://washinmura.jp)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://claude.ai/code)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## ✨ What is Auto-Tidy?

Auto-Tidy is a Claude Code skill that **automatically organizes your project files** when you're done working. No manual effort required.

```
You: "Goodnight! 🌙"
Claude: *organizes files* *updates index* "Goodnight! Cleaned up 5 files."
```

---

## 🎯 Features

| Feature | Description |
|---------|-------------|
| 🌙 **Auto-trigger on goodbye** | Say "goodnight", "bye", or "88" → auto cleanup |
| 💾 **Auto-trigger on save** | Say "save" or "checkpoint" → auto cleanup + progress summary |
| ⚡ **Light cleanup** | Quick 30-second tidy (garbage files, update index) |
| 🔍 **Deep cleanup** | Full organization (move files, detect duplicates) |
| 📁 **Standard structure** | Opinionated project structure template |
| 🔒 **Safe by default** | Never auto-deletes important files |

---

## 🚀 Quick Start

### 1. Install the Skill

Copy `SKILL.md` to your Claude Code skills directory:

```bash
# Global installation
cp SKILL.md ~/.claude/skills/auto-tidy.md

# Or project-specific
cp SKILL.md .claude/skills/auto-tidy.md
```

### 2. Use It

Just talk naturally:

```
"Goodnight!"           → Light cleanup + goodbye
"I'm going to sleep"   → Light cleanup + goodbye
"Save"                 → Light cleanup + progress summary
"Tidy up"              → Light cleanup
"/tidy --full"         → Deep cleanup
```

---

## 📁 Standard Project Structure

Auto-Tidy uses this opinionated structure:

```
project/
├── 00-research/          # 📚 Research & raw materials
├── 01-knowledge/         # 🧠 Structured knowledge
├── 02-ideation/          # 💡 Ideas & drafts
├── 03-specs/             # 📋 Specifications & plans
├── 04-src/               # 💻 Source code
├── 05-tests/             # 🧪 Tests
├── docs/                 # 📖 Documentation
├── _archive/             # 📦 Archived files
├── _temp/                # 🗑️ Temporary files
├── PROJECT_INDEX.json    # 🔍 Auto-generated index
└── CLAUDE.md             # 📍 Project memory
```

---

## ⚡ Light vs Deep Cleanup

| | ⚡ Light | 🔍 Deep |
|---|---------|---------|
| **Time** | < 30 seconds | 1-5 minutes |
| **Trigger** | Goodbye / Save | Manual |
| **Clean garbage** | ✅ | ✅ |
| **Update index** | ✅ | ✅ |
| **Move files** | ❌ | ✅ |
| **Detect duplicates** | ❌ | ✅ |
| **Update CODEMAPS** | ❌ | ✅ |

---

## 🔒 Safety Rules

Auto-Tidy is **safe by default**:

- ❌ Never auto-deletes non-temporary files
- ❌ Never touches `.git`, `node_modules`
- ❌ Never moves files being edited
- ❌ Never processes sensitive files (`.env`, credentials)
- ✅ Always asks before moving files
- ✅ Always logs operations for undo
- ✅ Always preserves file modification times

---

## 🌍 Multilingual Triggers

Auto-Tidy understands multiple languages:

| Language | Goodbye | Save |
|----------|---------|------|
| English | goodnight, bye | save, checkpoint |
| 中文 | 晚安, 我去睡覺了, 掰掰, 88 | 存檔, 存一下 |
| 日本語 | (coming soon) | (coming soon) |

---

## 🐾 About Washin Village

This skill is made by **Washin Village (和心村)** — a sanctuary for 28 cats and dogs in Japan's Boso Peninsula.

We build AI tools to help animals get seen by the world. Every star ⭐ helps us rescue more animals!

🌐 [washinmura.jp](https://washinmura.jp)

---

## 📚 Related Skills

- [Infinite Gratitude](https://github.com/sstklen/infinite-gratitude) - Multi-agent research skill
- [Claude API Cost Optimization](https://github.com/sstklen/claude-api-cost-optimization) - Save 50-90% on API costs

---

## 📄 License

MIT License - Feel free to use, modify, and share!

---

<p align="center">
  <b>Made with 🐾 by 28 cats & dogs from Japan</b><br>
  <a href="https://washinmura.jp">Washin Village</a>
</p>
