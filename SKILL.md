---
name: auto-tidy
description: 自動整理專案檔案系統 - 零手動、全自動。在開發過程中自動歸檔、索引、清理，讓 AI 和人類都能快速找到資料。
triggers:
  # 手動觸發
  - "/tidy"
  - "/整理"
  - "整理一下"
  - "清理專案"
  - "找不到檔案"
  # 離開觸發（自動執行淺層整理）
  - "晚安"
  - "我去睡覺了"
  - "我去睡觉了"
  - "我去休息"
  - "我出去"
  - "我出門"
  - "我出门"
  - "明天見"
  - "明天见"
  - "bye"
  - "掰掰"
  - "88"
  # 存檔觸發（自動執行淺層整理 + 記錄進度）
  - "存檔"
  - "存档"
  - "save"
  - "存一下"
  - "記錄一下"
  - "记录一下"
  - "checkpoint"
  - "存個進度"
  - "存个进度"
---

# Auto-Tidy 自動整理系統

零手動檔案整理系統，由和心村（Washin Village）團隊開發 🐾

## 核心理念

```
你瘋狂開發 → Claude 自動整理 → 乾乾淨淨
```

**你什麼都不用做，我來搞定一切。**

---

## 🌙 離開時自動整理（重要！）

當你說以下任何一句話時，**立即執行淺層整理**：

| 觸發詞 | 動作 |
|-------|------|
| 晚安、我去睡覺了、我去休息 | 淺層整理 → 說晚安 |
| 我出去、我出門、掰掰、88 | 淺層整理 → 說再見 |
| 明天見、bye | 淺層整理 → 說再見 |
| 存檔、save、scale、checkpoint | 淺層整理 → 記錄進度摘要 |
| 存一下、記錄一下 | 淺層整理 → 記錄進度摘要 |

### 淺層整理（離開時做）⚡ 快速

執行時間：< 30 秒

1. ✅ 清理 .DS_Store、Thumbs.db
2. ✅ 清理 _temp/ 中超過 7 天的檔案
3. ✅ 更新 PROJECT_INDEX.json
4. ✅ 簡短報告今天做了什麼
5. ✅ 說晚安/再見

**不做：**
- ❌ 不搬移檔案
- ❌ 不重新組織結構
- ❌ 不檢查重複檔案

### 深層整理（手動觸發）🔍 完整

執行時間：1-5 分鐘

1. ✅ 所有淺層整理項目
2. ✅ 歸類未分類的檔案到正確位置
3. ✅ 檢測重複檔案並提出建議
4. ✅ 更新 CODEMAPS
5. ✅ 整理 _archive
6. ✅ 完整報告

**觸發方式：**
```
/tidy --full
"深度整理"
"完整整理一下"
```

---

## 標準專案結構

當整理或建立新專案時，使用這個結構：

```
project-name/
├── 00-research/              # 📚 資料收集階段
│   ├── _raw/                 # 原始資料（可刪除）
│   ├── _archive/             # 已整理歸檔
│   ├── references/           # 參考資料
│   └── summary.md            # 研究摘要 ⭐
│
├── 01-knowledge/             # 🧠 知識整理階段
│   ├── database/             # 結構化資料
│   ├── wiki/                 # 知識庫文章
│   └── glossary.md           # 術語表
│
├── 02-ideation/              # 💡 想法構思階段
│   ├── ideas/                # 想法筆記
│   ├── drafts/               # 草稿
│   └── brainstorm.md         # 腦力激盪記錄
│
├── 03-specs/                 # 📋 規格計劃階段
│   ├── spec.md               # 規格書 ⭐
│   ├── plan.md               # 計劃書 ⭐
│   ├── decisions/            # 決策記錄 (ADR)
│   └── meetings/             # 會議記錄
│
├── 04-src/                   # 💻 程式碼
│   └── [依專案結構]
│
├── 05-tests/                 # 🧪 測試
│   ├── unit/
│   ├── integration/
│   ├── e2e/
│   └── fixtures/             # 測試資料
│
├── docs/                     # 📖 最終文檔
│   ├── CODEMAPS/             # 程式碼地圖
│   ├── api/                  # API 文檔
│   ├── guides/               # 使用指南
│   └── CHANGELOG.md          # 變更日誌 ⭐
│
├── _archive/                 # 📦 歸檔（舊版本、已完成）
├── _temp/                    # 🗑️ 暫存（可隨時刪除）
│
├── PROJECT_INDEX.json        # 🔍 專案索引（自動生成）
├── CLAUDE.md                 # 📍 Claude 專案說明
└── README.md                 # 📍 專案說明
```

## 自動整理流程

### 🔄 每次 Session 結束時

1. **掃描新增檔案**
   - 識別未歸類的檔案
   - 自動移到正確位置

2. **更新索引**
   - 更新 PROJECT_INDEX.json
   - 更新 CODEMAPS

3. **清理暫存**
   - 刪除 _temp/ 中超過 7 天的檔案
   - 刪除 .DS_Store、*.log 等系統檔

### 📁 檔案分類規則

| 檔案類型 | 自動歸類到 |
|---------|-----------|
| *.md (研究筆記) | 00-research/ |
| *.md (規格/計劃) | 03-specs/ |
| *.json, *.csv (資料) | 01-knowledge/database/ |
| *.ts, *.tsx, *.js | 04-src/ |
| *.test.*, *.spec.* | 05-tests/ |
| *.log, *.tmp | _temp/ |
| 截圖、螢幕錄影 | 00-research/_raw/ |

### 🏷️ 檔案命名規範

```
YYYY-MM-DD-描述.ext          # 時間敏感檔案
描述-v1.ext                  # 版本檔案
category-subcategory-name.ext # 分類檔案
```

範例：
- `2026-01-29-meeting-notes.md`
- `washin-frontend-spec-v2.md`
- `api-auth-design.md`

## 使用方式

### 自動觸發（離開時）

| 你說的話 | 我會做的事 |
|---------|-----------|
| 晚安 / 我去睡覺了 | 淺層整理 → 晚安報告 |
| 我出去 / 掰掰 / 88 | 淺層整理 → 再見報告 |

### 手動觸發

```
/tidy                    # 淺層整理
/tidy --full            # 深度整理（含重複檔檢測）
/tidy --index           # 只更新索引
```

### 自然語言

```
"整理一下"               # 淺層整理
"深度整理"               # 深層整理
"檔案太亂了"             # 深層整理
"幫我清理暫存檔"          # 淺層整理
"更新專案索引"            # 只更新索引
```

### 建立新專案

```
"建立一個新專案結構: [專案名稱]"
```

## 整理操作清單

當執行整理時，按順序執行：

### Step 1: 分析現狀
```bash
# 統計檔案類型
find . -type f | sed 's/.*\.//' | sort | uniq -c | sort -rn

# 找出大檔案
find . -type f -size +10M -exec ls -lh {} \;

# 找出最近修改的檔案
find . -type f -mtime -7 -not -path './.git/*'
```

### Step 2: 清理垃圾
```bash
# 刪除系統檔
find . -name ".DS_Store" -delete
find . -name "*.log" -mtime +7 -delete
find . -name "Thumbs.db" -delete

# 清理 node_modules 中的暫存
find . -name "*.tsbuildinfo" -delete
```

### Step 3: 歸檔舊檔
```bash
# 移動超過 30 天未修改的暫存檔到 _archive
find _temp -type f -mtime +30 -exec mv {} _archive/ \;
```

### Step 4: 更新索引
- 生成/更新 PROJECT_INDEX.json
- 更新 docs/CODEMAPS/

### Step 5: 報告結果
```markdown
# 整理完成！✨

## 變更摘要
- 移動了 X 個檔案
- 清理了 Y MB 垃圾
- 更新了索引

## 新的檔案結構
[樹狀圖]

## 建議
- [任何需要手動處理的項目]
```

## 重複檔案處理

當發現重複檔案時：

1. **比較檔案**
   - 顯示路徑、大小、修改時間
   - 計算 hash 確認是否完全相同

2. **建議保留哪個**
   - 優先保留：最新的、位置正確的、命名較好的

3. **詢問確認**
   - 永遠不自動刪除，除非在 _temp 資料夾

## 安全規則

⚠️ **絕對不做的事：**
- 不自動刪除非暫存檔案
- 不移動正在編輯的檔案
- 不改動 .git、node_modules
- 不處理敏感檔案（.env, credentials）

✅ **總是會做的事：**
- 移動前先確認
- 保留檔案修改時間
- 記錄所有操作以便還原
- 遇到不確定的情況就問你

## 與其他 Skills 整合

- **doc-updater**: 整理後自動更新文檔
- **refactor-cleaner**: 整理時順便清理死代碼
- **claudeception**: 記錄整理過程中發現的知識

## 最佳實踐（來自資深工程師）

1. **每週清理 Downloads** - 不要堆積
2. **檔名加日期** - YYYY-MM-DD 開頭
3. **歸檔而非刪除** - 移到 _archive 而不是直接刪
4. **活動 vs 歸檔** - 清楚區分正在做的和已完成的
5. **信任系統** - 讓 Claude 處理認知負擔

## 快速指令

```bash
# 查看專案結構
tree -L 2 -I 'node_modules|.git'

# 找最近修改的檔案
find . -type f -mtime -7 -not -path './.git/*' | head -20

# 統計各資料夾大小
du -sh */ | sort -rh
```
