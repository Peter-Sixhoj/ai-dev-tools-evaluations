# Comparative Research Methodology

A systematic framework for evaluating and comparing multiple options (products, tools, services) using evidence-based analysis.

---

## Repository Contents

### 📘 Core Methodology
- **[`comparative-research-methodology.md`](comparative-research-methodology.md)**: The complete 4-phase process for conducting comparative research (domain-agnostic)

### 📁 Reusable Templates
- **[`templates/`](templates/)**: Blank templates for starting new research projects
  - `research-context-template.md` - Phase 0: Problem statement
  - `evaluation-dimensions-template.md` - Phase 1: Dimensions & questions
  - `scoring-criteria-template.md` - Phase 1: Priority weights
  - `evaluation-template-template.md` - Phase 2: Individual evaluation format
  - `comparison-report-template.md` - Phase 3: Final report format

### 🔬 Research Projects
- **[`projects/`](projects/)**: Individual research projects using this methodology
  - **[ai-dev-tools/](projects/ai-dev-tools/)**: Comparison of 6 AI development tools (Complete)
  - *(Add new projects here)*

---

## Quick Start Guide

### For New Research Projects

**1. Read the Methodology**
```bash
Read: comparative-research-methodology.md
```

**2. Copy Templates**
```bash
# Create new project folder
mkdir -p projects/your-project-name/{framework,evaluations}

# Copy templates
cp templates/research-context-template.md projects/your-project-name/research-context.md
cp templates/evaluation-dimensions-template.md projects/your-project-name/framework/
cp templates/scoring-criteria-template.md projects/your-project-name/framework/
cp templates/evaluation-template-template.md projects/your-project-name/framework/evaluation-template.md
```

**3. Follow the 4 Phases**
- **Phase 0**: Complete `research-context.md` (define your problem)
- **Phase 1**: Create evaluation framework in `framework/` folder
- **Phase 2**: Evaluate each option in `evaluations/`
- **Phase 3**: Generate `comparison-report.md` at project root

---

## The 4-Phase Process

### Phase 0: Define Research Scope & Context
**Output**: `research-context.md`

- Define decision objective
- Document CRITICAL/HIGH/MEDIUM requirements
- Identify stakeholders and use cases
- Set evaluation scope

### Phase 1: Define Evaluation Framework
**Outputs**: `framework/` folder

- Create evaluation dimensions (15-25 dimensions)
- Define 80-120 specific questions
- Assign priority weights (CRITICAL/HIGH/MEDIUM)
- Establish evidence standards (P1/P2/P3)

### Phase 2: Conduct Individual Evaluations
**Outputs**: `evaluations/[option]-evaluation.md`

- Research each option systematically
- Answer all questions with evidence
- Calculate Decision Scorecard
- Document strengths and limitations

### Phase 3: Generate Comparison Report
**Output**: `comparison-report.md` (at project root)

- Create comparison tables for all dimensions
- Rank options by total score
- Map use cases to best options
- Provide decision framework

---

## Project Structure

Each project follows this structure:

```
project-name/
├── README.md                           # Project overview
├── research-context.md                 # Phase 0: Problem statement
├── comparison-report.md                # Phase 3: Final synthesis ⭐ PRIME ARTIFACT
├── framework/                          # Phase 1: Evaluation framework
│   ├── evaluation-dimensions.md        # Dimensions & questions
│   ├── scoring-criteria.md             # Priority weights
│   ├── evaluation-template.md          # Output format specification
│   └── [optional-rationale.md]         # Optional: Question rationale
└── evaluations/                        # Phase 2: Individual evaluations
    ├── option-a-evaluation.md
    ├── option-b-evaluation.md
    └── option-c-evaluation.md
```

**Key Design Principles:**
- ✅ Comparison report at project root (prime deliverable)
- ✅ Simple hierarchy (no unnecessary nesting)
- ✅ Clear phase separation (0→1→2→3)
- ✅ Consistent naming across projects

---

## Current Research Projects

### ✅ AI Development Tools (Complete)
**Location**: [`projects/ai-dev-tools/`](projects/ai-dev-tools/)  
**Status**: Complete (2026-02-04)  
**Options Evaluated**: Cursor, Windsurf, Bolt.new, Replit, Lovable, Base44  
**Key Finding**: 4 tools pass all critical requirements; 2 disqualified due to vendor lock-in

**View Reports**:
- [Comparison Report](projects/ai-dev-tools/comparison-report.md) ⭐
- [Individual Evaluations](projects/ai-dev-tools/evaluations/)
- [Project README](projects/ai-dev-tools/README.md)

---

## When to Use This Methodology

**✅ Good Fit:**
- Comparing 3-10 similar options
- Decision requires systematic evaluation
- Stakeholders need evidence-based justification
- Framework will be reused for future evaluations

**❌ Poor Fit:**
- Only 2 options (simpler pro/con list sufficient)
- Purely subjective decision
- Time-sensitive decision requiring immediate action

---

## Key Principles

1. **Evidence-Based**: All claims cited (P1 > P2 > P3)
2. **Structured Consistency**: Same dimensions, questions, scoring for all options
3. **Actionable Synthesis**: Reports guide decisions with clear recommendations
4. **Transparent Methodology**: Documented process enables reproducibility
5. **Critical Focus**: Identify deal-breakers early (CRITICAL requirements)
6. **Visual Hierarchy**: Tables and icons for scanability
7. **Versioned Framework**: Enables auditing and iteration

---

## Contributing

To add a new research project:

1. Create folder: `projects/your-project-name/`
2. Follow the 4-phase process
3. Update this README with project link
4. Ensure all framework files reference correct versions

---

## Methodology Version

**Current Version**: 1.0  
**Last Updated**: 2026-02-04

### Version History
- **v1.0** (2026-02-04): Initial release with 4-phase process

---

## License

[Your License Here]

---

## Questions or Feedback?

For questions about the methodology or to share your research projects, [create an issue](../../issues) or reach out to [maintainer contact].
