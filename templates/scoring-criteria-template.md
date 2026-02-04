# Scoring Criteria

**Version**: 1.0  
**Created**: YYYY-MM-DD  
**Last Updated**: YYYY-MM-DD  
**Project**: [Project Name]

---

## Scoring System

### Priority Levels

| Priority | Symbol | Description | Points Each | Question Count | Total Points |
|----------|--------|-------------|-------------|----------------|-------------|
| **CRITICAL** | 🔴 | Deal-breakers that eliminate options | 10 | [X] | [X × 10] |
| **HIGH** | 🟡 | Important features for core functionality | 1 | [Y] | [Y × 1] |
| **MEDIUM** | 🟢 | Nice-to-have differentiators | [Z points] | [N] | [N × Z] |
| **TOTAL** | | | | **[Total Qs]** | **100** |

### Calculating MEDIUM Weight

```
MEDIUM weight = (100 - CRITICAL_total - HIGH_total) / MEDIUM_count

Example:
MEDIUM weight = (100 - 40 - 45) / 54 = 15 / 54 = 0.278 points per question
```

---

## Question Priority Assignments

### CRITICAL Questions (🔴 Deal-Breakers)

*These questions eliminate options if not met. Each worth 10 points.*

| Question ID | Question Text | Dimension |
|-------------|---------------|----------|
| [1.1] | [Question text] | [Dimension name] |
| [X.Y] | [Question text] | [Dimension name] |
| ... | ... | ... |

**Total CRITICAL**: [X] questions × 10 points = [Total] points

---

### HIGH Priority Questions (🟡 Core Functionality)

*Important features for core functionality. Each worth 1 point.*

| Question ID | Question Text | Dimension |
|-------------|---------------|----------|
| [1.2] | [Question text] | [Dimension name] |
| [2.1] | [Question text] | [Dimension name] |
| ... | ... | ... |

**Total HIGH**: [Y] questions × 1 point = [Total] points

---

### MEDIUM Priority Questions (🟢 Differentiators)

*Nice-to-have features. Each worth [Z] points.*

| Question ID | Question Text | Dimension |
|-------------|---------------|----------|
| [3.2] | [Question text] | [Dimension name] |
| [4.3] | [Question text] | [Dimension name] |
| ... | ... | ... |

**Total MEDIUM**: [N] questions × [Z] points = 15 points

---

## Scoring Rules

### CRITICAL Questions (Pass/Fail)

- **"Yes" or "Full"** = 10 points
- **"No", "Partial", or "Limited"** = 0 points
- **No partial credit** for CRITICAL questions
- **Failing any CRITICAL** = potential disqualification

### HIGH Questions (Weighted)

- **"Yes" or "Full"** = 1 point (100%)
- **"Limited" or "Partial"** = 0.5 points (50%)
- **"No"** = 0 points (0%)

### MEDIUM Questions (Weighted)

- **"Yes" or "Full"** = [Z] points (100%)
- **"Limited" or "Partial"** = [Z/2] points (50%)
- **"No"** = 0 points (0%)

---

## Example Calculation

**Option A:**
- CRITICAL: 3/4 passed = 3 × 10 = 30/40
- HIGH: 36 full + 5 partial = (36 × 1) + (5 × 0.5) = 38.5/45
- MEDIUM: 40 full + 10 partial + 4 no = (40 × 0.278) + (10 × 0.139) = 12.6/15
- **TOTAL**: 30 + 38.5 + 12.6 = **81.1/100**

---

## Validation Checklist

- [ ] Total points = 100
- [ ] CRITICAL typically 40% (3-5 questions × 10 points)
- [ ] HIGH typically 45% (40-50 questions × 1 point)
- [ ] MEDIUM typically 15% (50-60 questions × calculated weight)
- [ ] All questions from evaluation-dimensions.md assigned priority
- [ ] No questions missing priority assignment

---

## Version History

**v1.0** (YYYY-MM-DD)
- Initial scoring criteria
- CRITICAL: [X] questions, HIGH: [Y] questions, MEDIUM: [Z] questions
