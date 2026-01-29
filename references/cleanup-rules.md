# Cleanup Rules Reference

## Light Cleanup (< 30 seconds)

### Step 1: Remove Garbage Files

Auto-delete these files:
- `.DS_Store`
- `Thumbs.db`
- `*.swp`, `*.swo` (Vim swap files)
- `*~` (backup files)
- `._*` (macOS metadata)

### Step 2: Clean Temporary Directories

Remove contents of:
- `_temp/`
- `.cache/` (project-level only)

### Step 3: Update Index

Regenerate `PROJECT_INDEX.json` if exists.

## Deep Cleanup (1-5 minutes)

### All Light Cleanup Steps Plus:

### Step 4: Detect Misplaced Files

Check for files in wrong locations:

| File Type | Should Be In |
|-----------|-------------|
| `*.tsx`, `*.jsx` | `src/components/` |
| `*.test.ts` | `tests/` |
| `*.md` (docs) | `docs/` |
| Research notes | `00-research/` |

### Step 5: Detect Duplicates

Find files with same name in different locations.
Report but don't auto-delete.

### Step 6: Archive Old Files

Move files older than 30 days (and not accessed) to `_archive/`.

### Step 7: Update CODEMAPS

If `docs/CODEMAPS/` exists, regenerate module maps.

## Safe Files (Never Touch)

- `package.json`, `package-lock.json`
- `tsconfig.json`, `*.config.js`
- `.env`, `.env.*`
- `README.md`, `CLAUDE.md`
- `.git/`, `node_modules/`
- Any file currently open/modified

## Cleanup Log

Every cleanup generates a log entry:

```json
{
  "timestamp": "2026-01-30T10:00:00Z",
  "type": "light",
  "actions": [
    {"action": "delete", "file": ".DS_Store"},
    {"action": "update", "file": "PROJECT_INDEX.json"}
  ]
}
```

Log location: `_temp/cleanup-log.json`
