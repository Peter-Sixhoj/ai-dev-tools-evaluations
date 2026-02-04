# Repository Restructuring Migration Guide

**Date**: 2026-02-04  
**Purpose**: Move existing AI dev tools evaluation files into new `projects/` structure while preserving Git history

---

## What Changed

The repository has been restructured to support multiple research projects using the Comparative Research Methodology.

**New Structure Created:**
- ✅ `comparative-research-methodology.md` - Core methodology document
- ✅ `templates/` - Reusable templates for new projects
- ✅ `projects/ai-dev-tools/` - Project folder (README and research-context created)
- ✅ Updated root `README.md`

**Files to Move:**
- `evaluations/` folder contents → `projects/ai-dev-tools/`

---

## Quick Migration (Recommended)

### Step 1: Clone Repository

```bash
git clone https://github.com/Peter-Sixhoj/ai-dev-tools-evaluations.git
cd ai-dev-tools-evaluations
```

### Step 2: Create Folders

```bash
mkdir -p projects/ai-dev-tools/framework
mkdir -p projects/ai-dev-tools/evaluations/raw
```

### Step 3: Move Framework Files

```bash
git mv evaluations/evaluation-metrics.md projects/ai-dev-tools/framework/
git mv evaluations/decision-criteria.md projects/ai-dev-tools/framework/
git mv evaluations/evaluation-template.md projects/ai-dev-tools/framework/
git mv evaluations/decision-rationale.md projects/ai-dev-tools/framework/
```

### Step 4: Move Evaluation Files

```bash
# Rename raw-threads to raw during move
git mv evaluations/raw-threads/* projects/ai-dev-tools/evaluations/raw/
rmdir evaluations/raw-threads
```

### Step 5: Move Comparison Report

```bash
git mv evaluations/comparison-report.md projects/ai-dev-tools/evaluations/
```

### Step 6: Archive Working Documents

```bash
mkdir -p archive
git mv evaluations/*.md archive/  # Moves remaining .md files
git mv evaluations/*.txt archive/  # Moves .txt files
```

### Step 7: Remove Empty Folder

```bash
rmdir evaluations/
```

### Step 8: Commit and Push

```bash
git commit -m "Restructure: Move AI dev tools project to projects/ folder

- Move framework files to projects/ai-dev-tools/framework/
- Rename raw-threads to raw
- Move comparison report to projects/ai-dev-tools/evaluations/
- Archive working documents
- Preserve Git history for all files"

git push origin main
```

---

## Final Structure

After migration:

```
ai-dev-tools-evaluations/
├── README.md
├── MIGRATION-GUIDE.md
├── comparative-research-methodology.md
├── templates/
│   ├── research-context-template.md
│   ├── evaluation-dimensions-template.md
│   ├── scoring-criteria-template.md
│   ├── evaluation-template-template.md
│   └── comparison-report-template.md
├── projects/
│   └── ai-dev-tools/
│       ├── README.md
│       ├── research-context.md
│       ├── framework/
│       │   ├── evaluation-metrics.md
│       │   ├── decision-criteria.md
│       │   ├── evaluation-template.md
│       │   └── decision-rationale.md
│       └── evaluations/
│           ├── raw/
│           │   ├── cursor-evaluation.md
│           │   ├── windsurf-evaluation.md
│           │   ├── bolt-evaluation.md
│           │   ├── replit-evaluation.md
│           │   ├── lovable-evaluation.md
│           │   └── base44-evaluation.md
│           └── comparison-report.md
└── archive/  (optional - working documents)
```

---

## Verification

After migration, verify:

```bash
# Check new structure
ls projects/ai-dev-tools/framework/
ls projects/ai-dev-tools/evaluations/raw/

# Verify Git history preserved
git log --follow projects/ai-dev-tools/framework/evaluation-metrics.md

# Check for broken links
grep -r "evaluations/" projects/ai-dev-tools/README.md
```

---

## Rollback (If Needed)

```bash
# Undo uncommitted changes
git reset --hard HEAD

# Undo last commit
git reset --hard HEAD~1
```

---

## Delete This File

Once migration is complete and verified, delete this guide:

```bash
git rm MIGRATION-GUIDE.md
git commit -m "Remove migration guide after successful restructure"
git push origin main
```
