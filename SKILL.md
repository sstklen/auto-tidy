---
name: auto-tidy
description: Zero-effort file organization for Claude Code. Say "goodnight" and your project gets organized automatically. Cleans garbage files, updates index, moves misplaced files.
argument-hint: [--light|--full|goodnight|save]
---

# Auto-Tidy 🧹

> Zero-effort file organization — Say "goodnight" and your project gets organized automatically.

## Quick Reference

### Triggers

| Action | What Happens |
|--------|--------------|
| "Goodnight!" / "晚安" / "88" | ⚡ Light cleanup + goodbye |
| "Save" / "存檔" | ⚡ Light cleanup + progress summary |
| "Tidy up" | ⚡ Light cleanup |
| `/tidy --full` | 🔍 Deep cleanup |

### Light vs Deep

| | ⚡ Light | 🔍 Deep |
|---|---------|---------|
| **Time** | < 30 seconds | 1-5 minutes |
| Clean garbage | ✅ | ✅ |
| Update index | ✅ | ✅ |
| Move files | ❌ | ✅ |
| Detect duplicates | ❌ | ✅ |

## Safety Rules

- ❌ Never auto-deletes non-temporary files
- ❌ Never touches `.git`, `node_modules`
- ❌ Never moves files being edited
- ✅ Always asks before moving files
- ✅ Always logs operations for undo

## Standard Structure

Auto-Tidy organizes into this structure:

```
project/
├── 00-research/          # 📚 Research
├── 01-knowledge/         # 🧠 Knowledge base
├── 02-ideation/          # 💡 Ideas & drafts
├── 03-specs/             # 📋 Specifications
├── src/                  # 💻 Source code
├── tests/                # 🧪 Tests
├── docs/                 # 📖 Documentation
├── _archive/             # 📦 Archived
├── _temp/                # 🗑️ Temporary
└── CLAUDE.md             # 📍 Project memory
```

## Additional Resources

- For cleanup rules, see [references/cleanup-rules.md](references/cleanup-rules.md)
- For trigger phrases, see [references/triggers.md](references/triggers.md)

## Related Skills

- **ai-dojo** — Foundation (environment tools + file placement)
- **project-index** — Auto-generate project index

---

*Part of 🥋 AI Dojo Series by [Washin Village](https://washinmura.jp) 🐾*
