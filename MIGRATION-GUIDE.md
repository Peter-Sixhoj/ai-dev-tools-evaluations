# Repository Restructuring Migration Guide

**Date**: 2026-02-04  
**Purpose**: Move existing AI dev tools evaluation files into new `projects/` structure while preserving Git history

---

## What Changed

The repository has been restructured to support multiple research projects using the Comparative Research Methodology.

**New Improved Structure:**

```
project-name/
├── README.md                           # Project overview
├── research-context.md                 # Phase 0: Problem statement
├── comparison-report.md                # Phase 3: Final synthesis ⭐ PRIME ARTIFACT
├── framework/                          # Phase 1: Evaluation framework
│   ├── evaluation-dimensions.md
│   ├── scoring-criteria.md
│   ├── evaluation-template.md
│   └── decision-rationale.md
└── evaluations/                        # Phase 2: Individual evaluations
    ├── cursor-evaluation.md
    ├── windsurf-evaluation.md
    └── ...
```

**Key Improvements:**
- ✅ Comparison report at project root (prime artifact visible immediately)
- ✅ No `/raw` subfolder (simpler hierarchy)
- ✅ Fewer nested folders (easier navigation)

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
mkdir -p projects/ai-dev-tools/evaluations
```

### Step 3: Move Framework Files

```bash
git mv evaluations/evaluation-metrics.md projects/ai-dev-tools/framework/evaluation-dimensions.md
git mv evaluations/decision-criteria.md projects/ai-dev-tools/framework/scoring-criteria.md
git mv evaluations/evaluation-template.md projects/ai-dev-tools/framework/
git mv evaluations/decision-rationale.md projects/ai-dev-tools/framework/
```

**Note**: We're renaming files during move to match template naming:
- `evaluation-metrics.md` → `evaluation-dimensions.md`
- `decision-criteria.md` → `scoring-criteria.md`

### Step 4: Move Comparison Report (to project root)

```bash
git mv evaluations/comparison-report.md projects/ai-dev-tools/
```

### Step 5: Move Individual Evaluations (no /raw subfolder)

```bash
# Move directly to evaluations/ folder
git mv evaluations/raw-threads/cursor-evaluation.md projects/ai-dev-tools/evaluations/
git mv evaluations/raw-threads/windsurf-evaluation.md projects/ai-dev-tools/evaluations/
git mv evaluations/raw-threads/bolt-evaluation.md projects/ai-dev-tools/evaluations/
git mv evaluations/raw-threads/replit-evaluation.md projects/ai-dev-tools/evaluations/
git mv evaluations/raw-threads/lovable-evaluation.md projects/ai-dev-tools/evaluations/
git mv evaluations/raw-threads/base44-evaluation.md projects/ai-dev-tools/evaluations/
```

### Step 6: Archive Working Documents

```bash
mkdir -p archive
git mv evaluations/decision-framework-review.md archive/
git mv evaluations/framework-refinement-worksheet.md archive/
git mv evaluations/phase1-comparison-summary.md archive/
git mv evaluations/space-instructions.txt archive/
```

### Step 7: Clean Up Empty Folders

```bash
rmdir evaluations/raw-threads
rmdir evaluations/
```

### Step 8: Commit and Push

```bash
git commit -m "Restructure: Move AI dev tools to projects/ with improved hierarchy

- Move framework files to projects/ai-dev-tools/framework/
- Rename: evaluation-metrics.md → evaluation-dimensions.md
- Rename: decision-criteria.md → scoring-criteria.md
- Move comparison-report.md to project root (prime artifact)
- Move evaluations directly to evaluations/ (no /raw subfolder)
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
│       ├── README.md                          # Project overview
│       ├── research-context.md                # Phase 0
│       ├── comparison-report.md               # Phase 3 ⭐ PRIME ARTIFACT
│       ├── framework/                         # Phase 1
│       │   ├── evaluation-dimensions.md       # (renamed from evaluation-metrics.md)
│       │   ├── scoring-criteria.md            # (renamed from decision-criteria.md)
│       │   ├── evaluation-template.md
│       │   └── decision-rationale.md
│       └── evaluations/                       # Phase 2 (no /raw subfolder)
│           ├── cursor-evaluation.md
│           ├── windsurf-evaluation.md
│           ├── bolt-evaluation.md
│           ├── replit-evaluation.md
│           ├── lovable-evaluation.md
│           └── base44-evaluation.md
└── archive/
    ├── decision-framework-review.md
    ├── framework-refinement-worksheet.md
    ├── phase1-comparison-summary.md
    └── space-instructions.txt
```

---

## File Mapping

### Framework Files → `projects/ai-dev-tools/framework/`

| Old Path | New Path | Notes |
|----------|----------|-------|
| `evaluations/evaluation-metrics.md` | `projects/ai-dev-tools/framework/evaluation-dimensions.md` | ✏️ Renamed |
| `evaluations/decision-criteria.md` | `projects/ai-dev-tools/framework/scoring-criteria.md` | ✏️ Renamed |
| `evaluations/evaluation-template.md` | `projects/ai-dev-tools/framework/evaluation-template.md` | ✅ Same name |
| `evaluations/decision-rationale.md` | `projects/ai-dev-tools/framework/decision-rationale.md` | ✅ Same name |

### Comparison Report → `projects/ai-dev-tools/` (root)

| Old Path | New Path | Notes |
|----------|----------|-------|
| `evaluations/comparison-report.md` | `projects/ai-dev-tools/comparison-report.md` | ⭐ Project root |

### Individual Evaluations → `projects/ai-dev-tools/evaluations/` (no /raw)

| Old Path | New Path | Notes |
|----------|----------|-------|
| `evaluations/raw-threads/cursor-evaluation.md` | `projects/ai-dev-tools/evaluations/cursor-evaluation.md` | ✅ Direct |
| `evaluations/raw-threads/windsurf-evaluation.md` | `projects/ai-dev-tools/evaluations/windsurf-evaluation.md` | ✅ Direct |
| `evaluations/raw-threads/bolt-evaluation.md` | `projects/ai-dev-tools/evaluations/bolt-evaluation.md` | ✅ Direct |
| `evaluations/raw-threads/replit-evaluation.md` | `projects/ai-dev-tools/evaluations/replit-evaluation.md` | ✅ Direct |
| `evaluations/raw-threads/lovable-evaluation.md` | `projects/ai-dev-tools/evaluations/lovable-evaluation.md` | ✅ Direct |
| `evaluations/raw-threads/base44-evaluation.md` | `projects/ai-dev-tools/evaluations/base44-evaluation.md` | ✅ Direct |

---

## Why These Changes?

### 1. Comparison Report at Project Root
**Before**: `projects/ai-dev-tools/evaluations/comparison-report.md`  
**After**: `projects/ai-dev-tools/comparison-report.md`

**Rationale**: The comparison report is the **prime deliverable**—the final synthesis that decision-makers read. It should be immediately visible at the project level, not buried in a subfolder.

### 2. No /raw Subfolder
**Before**: `projects/ai-dev-tools/evaluations/raw/cursor-evaluation.md`  
**After**: `projects/ai-dev-tools/evaluations/cursor-evaluation.md`

**Rationale**: The `/raw` subfolder was redundant. All files in `evaluations/` are individual evaluations. Simpler hierarchy = easier navigation.

### 3. File Renaming for Consistency
**Before**: `evaluation-metrics.md`, `decision-criteria.md`  
**After**: `evaluation-dimensions.md`, `scoring-criteria.md`

**Rationale**: Match template naming conventions. "Dimensions" is clearer than "metrics", "scoring" matches methodology terminology.

---

## Verification

After migration, verify:

```bash
# Check project structure
ls projects/ai-dev-tools/
# Should show: README.md, research-context.md, comparison-report.md, framework/, evaluations/

# Check framework files
ls projects/ai-dev-tools/framework/
# Should show: evaluation-dimensions.md, scoring-criteria.md, evaluation-template.md, decision-rationale.md

# Check evaluations (no /raw)
ls projects/ai-dev-tools/evaluations/
# Should show: cursor-evaluation.md, windsurf-evaluation.md, bolt-evaluation.md, replit-evaluation.md, lovable-evaluation.md, base44-evaluation.md

# Verify Git history preserved
git log --follow projects/ai-dev-tools/framework/evaluation-dimensions.md
git log --follow projects/ai-dev-tools/comparison-report.md
```

---

## Update Project README Links

After migration, update `projects/ai-dev-tools/README.md` to reference new paths:

**Old structure references:**
```markdown
- [Comparison Report](evaluations/comparison-report.md)
- [Individual Evaluations](evaluations/raw/)
```

**New structure references:**
```markdown
- [Comparison Report](comparison-report.md)  ⭐ At project root
- [Individual Evaluations](evaluations/)
```

---

## Rollback (If Needed)

```bash
# Undo uncommitted changes
git reset --hard HEAD

# Undo last commit
git reset --hard HEAD~1

# Create backup before migration
git checkout -b backup-before-restructure
git push origin backup-before-restructure
```

---

## Summary of Improvements

✅ **Simpler hierarchy**: 2 levels instead of 3 (no /raw)  
✅ **Prominent output**: Comparison report at project root  
✅ **Consistent naming**: Matches methodology terminology  
✅ **Easier navigation**: Fewer clicks to any file  
✅ **Clearer structure**: Logical flow from README → context → comparison → details

---

## Delete This File

Once migration is complete and verified:

```bash
git rm MIGRATION-GUIDE.md
git commit -m "Remove migration guide after successful restructure"
git push origin main
```
