# Comparative Research Methodology

**Version**: 1.0  
**Last Updated**: 2026-02-04  
**Purpose**: A systematic framework for evaluating and comparing multiple options using evidence-based analysis

---

## Overview

This methodology provides a structured, repeatable process for conducting comparative research across any domain—whether comparing software tools, database systems, cloud providers, CRM platforms, or any other set of options requiring systematic evaluation.

### When to Use This Framework

**Good fit:**
- ✅ Comparing 3-10 similar options (tools, products, services)
- ✅ Decision requires systematic evaluation (not gut feeling)
- ✅ Stakeholders need justification (evidence-based)
- ✅ Options have measurable, comparable characteristics
- ✅ Framework can be reused for future evaluations

**Poor fit:**
- ❌ Only 2 options (simpler pro/con list sufficient)
- ❌ Decision is purely subjective (aesthetic preference)
- ❌ Options are too dissimilar (comparing apples to oranges)
- ❌ One-time decision with no reuse value
- ❌ Time-sensitive decision requiring immediate action

---

## The 4-Phase Process

### Phase 0: Define Research Scope & Context
### Phase 1: Define Evaluation Framework
### Phase 2: Conduct Individual Evaluations
### Phase 3: Generate Comparison Report

---

## Phase 0: Define Research Scope & Context

**Purpose:** Establish what you're comparing and why

**Output File:** `research-context.md`

### Activities

#### 0.1: Define the Decision
- What are you trying to choose between?
- What problem are you solving?
- What is the business/technical context?

**Example:**
> "Select an AI development tool for enterprise TypeScript projects with 10-50 developers building 100K+ LOC applications."

#### 0.2: Document Constraints and Requirements
Classify requirements by criticality:

**CRITICAL (Deal-breakers):**
- Requirements that eliminate options if not met
- Typically 3-5 requirements
- Example: "Must export code without proprietary runtime dependencies"

**HIGH (Important):**
- Core functionality requirements
- Typically 40-50 requirements
- Example: "Should support TypeScript with first-class tooling"

**MEDIUM (Nice-to-have):**
- Differentiating features
- Typically 50-60 requirements
- Example: "Nice to have real-time collaboration features"

#### 0.3: Identify Stakeholders and Use Cases
- Who will use this?
- What are the primary workflows?
- What are the scale requirements?
- What are the integration needs?

#### 0.4: Set Evaluation Scope
- How many options to evaluate? (Recommend 3-10)
- Evidence recency requirements (e.g., <6 months old)
- Timeline for completion
- Budget constraints (if applicable)

### Validation Checklist

- [ ] Decision objective clearly stated
- [ ] Must-have requirements enumerated (3-5)
- [ ] Should-have requirements enumerated (40-50)
- [ ] Nice-to-have requirements enumerated (50-60)
- [ ] Stakeholder needs documented
- [ ] Use cases identified
- [ ] Evaluation scope defined

---

## Phase 1: Define Evaluation Framework

**Purpose:** Create standardized criteria for apples-to-apples comparison

**Output Files:**
- `framework/evaluation-dimensions.md` - Core dimensions and questions
- `framework/scoring-criteria.md` - Priority weights and scoring rules
- `framework/evaluation-template.md` - Output format specification

### Activities

#### 1.1: Identify Evaluation Dimensions

Break the domain into logical dimensions (typically 15-25):

**Guidelines:**
- Each dimension should be **mutually exclusive** (no overlap)
- Questions within dimensions should be **specific and measurable**
- Aim for 3-7 questions per dimension
- Total questions typically 80-120 for comprehensive analysis

**Example structure:**
```markdown
## Dimension 1: [Name]

### Description
Brief explanation of what this dimension covers and why it matters.

### Questions

**1.1: [Question text]**
- Answer format: [Yes/No/Specific value/Descriptive]
- Rationale: Why this question matters

**1.2: [Question text]**
- Answer format: [Expected format]
- Rationale: Why this question matters
```

**Domain-specific examples:**

*Software Tools:*
- Deployment Model
- Package Management
- Code Ownership & Portability
- Framework Support
- Git Integration
- Collaboration Features
- Pricing Model

*Database Systems:*
- Data Model
- Query Language
- Scalability
- Consistency Model
- Operational Complexity
- Cost Structure

*Cloud Providers:*
- Compute Options
- Storage Services
- Networking
- Cost Transparency
- Geographic Coverage
- Developer Experience

#### 1.2: Assign Priorities to Questions

Classify each question by criticality:

| Priority | Symbol | Description | Points Each | Typical Count |
|----------|--------|-------------|-------------|---------------|
| **CRITICAL** | 🔴 | Deal-breakers that eliminate options | 10 | 3-5 questions |
| **HIGH** | 🟡 | Important features for core functionality | 1 | 40-50 questions |
| **MEDIUM** | 🟢 | Nice-to-have differentiators | 0.25-0.5 | 50-60 questions |

**Scoring Formula:**
```
Total Points = (CRITICAL × 10) + (HIGH × 1) + (MEDIUM × weight)

Example: (4 × 10) + (45 × 1) + (54 × 0.28) = 40 + 45 + 15 = 100 points
```

**Why This Weighting?**
- CRITICAL = 40% of score (emphasizes deal-breakers)
- HIGH = 45% of score (core functionality)
- MEDIUM = 15% of score (differentiators)

**Adjust the MEDIUM weight** to reach exactly 100 points:
```
MEDIUM weight = 15 / (number of MEDIUM questions)

Example: 15 / 54 = 0.278 points per MEDIUM question
```

#### 1.3: Define Evidence Standards

Establish source credibility hierarchy:

| Level | Symbol | Source Type | Example | Reliability |
|-------|--------|-------------|---------|-------------|
| **P1 (Primary)** | 📘 | Official documentation, vendor statements, published specs | Product docs, pricing pages, official blog posts | Highest |
| **P2 (Secondary)** | 📰 | Verified user reports, technical reviews, reproducible tests | Recent reviews (<6 months), case studies, benchmarks | Medium |
| **P3 (Tertiary)** | 💭 | Reasonable inferences from stated capabilities | "If it has X feature, it likely supports Y" | Lowest (mark clearly) |

**Conflict Resolution Rule:**
When P1 and P2 sources conflict:
1. Document both perspectives
2. Justify your assessment based on:
   - Recency (newer information preferred)
   - Specificity (detailed claims over vague)
   - Reproducibility (can claims be verified?)

#### 1.4: Create Evaluation Template

Standardize output format for individual evaluations:

```markdown
# [Option Name] Evaluation

**Evaluation Date**: YYYY-MM-DD
**Version Evaluated**: [version number]
**Evaluator**: [name/team]
**Framework Version**: evaluation-dimensions.md vX.X

## Executive Summary

[2-3 paragraph overview of the option, its positioning, 
and high-level assessment]

---

## Dimension 1: [Name]

### Capability Assessment

[Narrative evaluation with evidence citations. Describe what 
the option can do in this dimension, how it works, and any 
limitations. Cite evidence as (P1, source), (P2, source), 
or (P3, inference basis).]

**Evidence**: [Detailed citations]

**Limitations**: [Known constraints or weaknesses]

### Decision Questions for [Dimension Name]

- **🔴 CRITICAL | [ID]: [Question text]**
  Answer: [Specific response]
  Evidence: [P1/P2/P3 citation with source]
  Notes: [Any clarifications or context]

- **🟡 HIGH | [ID]: [Question text]**
  Answer: [Specific response]
  Evidence: [P1/P2/P3 citation with source]
  Notes: [Any clarifications or context]

- **🟢 MEDIUM | [ID]: [Question text]**
  Answer: [Specific response]
  Evidence: [P1/P2/P3 citation with source]
  Notes: [Any clarifications or context]

[Repeat for all questions in this dimension]

---

[Repeat Dimension structure for all dimensions]

---

## Key Differentiators

**Unique Strengths:**
- ✅ [Strength 1 with dimension reference]
- ✅ [Strength 2]
- ✅ [Strength 3]

**Critical Limitations:**
- ❌ [Limitation 1]
- ⚠️ [Limitation 2]
- ❌ [Limitation 3]

**Best Suited For:**
[Specific use cases where this option excels]

**Not Recommended For:**
[Scenarios where this option has significant constraints]

---

## Decision Scorecard

### Critical Requirements (CRITICAL)

| Question | Answer | Status |
|----------|--------|--------|
| [ID]: [Question] | [Answer] | ✅ PASS / ❌ FAIL |
| [ID]: [Question] | [Answer] | ✅ PASS / ❌ FAIL |
| **CRITICAL SCORE** | **X/40** | **Status** |

### Scoring Summary

- **CRITICAL Score**: X/40 (percentage)
- **HIGH Score**: Y/45 (percentage)
- **MEDIUM Score**: Z/15 (percentage)
- **TOTAL SCORE**: N/100

### Assessment

[2-3 sentence summary: Does this option pass all CRITICAL 
requirements? What are its strengths and weaknesses? Where 
does it rank overall?]

---

## Export Metadata

**File Path**: `/evaluations/raw/[option-name]-evaluation.md`  
**Evaluation Date**: YYYY-MM-DD  
**Evaluator**: [name]  
**Framework Version**: evaluation-dimensions.md vX.X  
**Template Version**: evaluation-template.md vX.X  
**Scoring Version**: scoring-criteria.md vX.X  

**Status**: [Draft / Under Review / Complete]

**Questions Answered**: X/Y decision questions  
**Dimensions Covered**: X/Y dimensions  
**Critical Requirements**: X/Y CRITICAL questions passed
```

### Validation Checklist

- [ ] All dimensions mutually exclusive
- [ ] All questions specific and measurable
- [ ] Priority distribution appropriate (~4 CRITICAL, ~45 HIGH, ~50 MEDIUM)
- [ ] Scoring totals exactly 100 points
- [ ] Evidence standards defined (P1/P2/P3)
- [ ] Template includes all required sections
- [ ] Template specifies answer formats for questions

---

## Phase 2: Conduct Individual Evaluations

**Purpose:** Systematically assess each option against the framework

**Output Files:** `evaluations/raw/[option-name]-evaluation.md` (one per option)

### Activities

#### 2.1: Research Process (Per Option)

**Step 1: Retrieve Framework Files**
Ensure you're using the latest version:
- `framework/evaluation-dimensions.md`
- `framework/scoring-criteria.md`
- `framework/evaluation-template.md`

**Step 2: Gather Evidence**

*P1 Sources (Primary):*
- Official product documentation
- Feature comparison pages
- Pricing pages
- Official blog posts and announcements
- Published roadmaps
- Technical specifications

*P2 Sources (Secondary):*
- Technical reviews published <6 months ago
- Verified user reports (Reddit, Stack Overflow, forums)
- Case studies with reproducible results
- Benchmark comparisons
- Conference talks and demos

*P3 Inferences (Tertiary):*
- Reasonable conclusions from stated capabilities
- Industry standard assumptions
- Always mark clearly as inference
- Example: "If tool supports React, likely supports JSX syntax (P3, inference from React requirement)"

**Step 3: Answer All Questions Systematically**

Go dimension by dimension:

1. **Read dimension description** to understand context
2. **Answer each question** with specific responses:
   - Avoid vague answers ("good", "fast", "many")
   - Provide concrete data ("200K tokens", "$20/month", "Yes (via GitHub integration)")
   - Use consistent answer formats (Yes/No/Limited/Partial)
3. **Cite evidence** with level:
   - Format: `(P1, official docs page title)`
   - Format: `(P2, Reddit thread r/subreddit, 15+ confirmations, January 2026)`
   - Format: `(P3, inferred from X capability)`
4. **Add clarifying notes** when needed:
   - Implementation details
   - Version requirements
   - Known limitations
   - Future roadmap items

**Step 4: Calculate Scorecard**

*CRITICAL Questions (Pass/Fail):*
- Each worth 10 points
- "Yes" = 10 points
- "No" or "Partial" = 0 points (no partial credit for CRITICAL)
- Failing any CRITICAL = potential disqualification

*HIGH Questions (Weighted):*
- Each worth 1 point
- "Yes" or "Full" = 1 point
- "Limited" or "Partial" = 0.5 points
- "No" = 0 points

*MEDIUM Questions (Weighted):*
- Each worth calculated weight (e.g., 0.28 points)
- Same scoring as HIGH (Yes = full, Limited = half, No = zero)

**Example Calculation:**
```
CRITICAL: 4 questions, 3 passed = 3 × 10 = 30/40
HIGH: 45 questions, 36 full + 5 partial = (36 × 1) + (5 × 0.5) = 38.5/45
MEDIUM: 54 questions @ 0.28 each, 40 full + 10 partial + 4 no = 
  (40 × 0.28) + (10 × 0.14) + (4 × 0) = 11.2 + 1.4 = 12.6/15

TOTAL: 30 + 38.5 + 12.6 = 81.1/100
```

**Step 5: Identify Differentiators**

What makes this option unique?
- Strengths: Features/capabilities that stand out
- Limitations: Critical weaknesses or constraints
- Best for: Specific use cases where this excels
- Avoid if: Scenarios where constraints are problematic

**Step 6: Export Evaluation**

Save to `evaluations/raw/[option-name]-evaluation.md`

**File Naming Convention:**
- Use lowercase with hyphens
- Be specific (not "tool1", "tool2")
- Match official product name
- Examples: `cursor-evaluation.md`, `postgresql-evaluation.md`, `salesforce-crm-evaluation.md`

#### 2.2: Quality Assurance

**Self-Review Checklist:**
- [ ] All dimensions covered
- [ ] All questions answered (no "TBD" or skips)
- [ ] Evidence level marked on all claims (P1/P2/P3)
- [ ] Sources cited with sufficient detail for verification
- [ ] Scorecard calculated correctly
- [ ] Arithmetic verified (CRITICAL + HIGH + MEDIUM = Total)
- [ ] Differentiators section complete
- [ ] Export metadata includes framework versions
- [ ] File saved to correct location with correct naming

**Common Pitfalls to Avoid:**

❌ **Subjective claims without quantification:**
- Bad: "Very fast performance"
- Good: "Query latency <50ms for 95th percentile (P1, benchmark docs)"

❌ **Marketing language without verification:**
- Bad: "Enterprise-grade security"
- Good: "SOC2 Type II certified (P1, compliance page)"

❌ **Mixing evidence levels:**
- Bad: Citing user report as P1
- Good: "User reports 300K LOC project (P2, Reddit, verified November 2025)"

❌ **Skipping questions:**
- Bad: Leaving questions unanswered
- Good: "Unknown - no documentation found (P1, absence in official docs as of 2026-02-04)"

❌ **Inconsistent answer formats:**
- Bad: Mixing "Yes", "True", "Supported" for boolean questions
- Good: Use consistent "Yes"/"No"/"Limited" across all evaluations

#### 2.3: Version Control

**Commit Strategy:**
- Commit after each complete evaluation
- Use descriptive commit messages:
  - ✅ "Complete PostgreSQL evaluation (v16.1, 2026-02-04)"
  - ❌ "Update file"

**Metadata to Track:**
- Evaluation date
- Product version evaluated
- Framework version used
- Evidence recency (all sources <6 months? Note exceptions)

### Validation Checklist

- [ ] All dimensions covered
- [ ] All questions answered
- [ ] Evidence levels marked (P1/P2/P3)
- [ ] Scorecard calculated correctly
- [ ] Differentiators documented
- [ ] Framework versions referenced
- [ ] File naming convention followed
- [ ] Committed to version control

---

## Phase 3: Generate Comparison Report

**Purpose:** Synthesize individual evaluations into actionable decision guidance

**Output File:** `evaluations/comparison-report.md`

### Activities

#### 3.1: Create Comparison Matrices

For **each dimension**, create a comparison table:

**Table Format:**
```markdown
### Dimension N: [Name]

| Option | Question A<br><sub>🔴 CRITICAL</sub> | Question B<br><sub>🟡 HIGH</sub> | Question C<br><sub>🟢 MEDIUM</sub> |
|--------|------|------|------|
| Option 1 | Answer | Answer | Answer |
| Option 2 | Answer | Answer | Answer |
| Option 3 | Answer | Answer | Answer |

**Key Insight**: [Pattern you should notice - what does this table tell you?]

**Winner**: [Best option(s) for this dimension, or "Tie" if no clear winner]
```

**Table Design Principles:**

✅ **Visual hierarchy:**
- Use icons: ✅ (Yes), ❌ (No), ⚠️ (Limited/Partial)
- Use priority icons: 🔴 CRITICAL, 🟡 HIGH, 🟢 MEDIUM
- Keep consistent icon usage across all tables

✅ **Scanability:**
- Limit columns to 5-8 max (avoid horizontal scrolling)
- Use `<br><sub>` for priority labels (smaller font beneath header)
- Summarize complex answers (full details in individual evaluations)

✅ **Actionability:**
- Every table must have "Key Insight" (what pattern emerges?)
- Every table must have "Winner" (which option(s) excel here?)

**Example Table:**
```markdown
### Dimension 3: Code Ownership & Portability

| Tool | Export 100% Code<br><sub>🔴 CRITICAL</sub> | No Proprietary SDK<br><sub>🔴 CRITICAL</sub> | Standard Format<br><sub>🟡 HIGH</sub> |
|------|-------------|-------------------|-----------------|
| **Cursor** | ✅ Yes | ✅ Yes | ✅ Yes |
| **Tool B** | ✅ Yes | ⚠️ Requires vendor SDK | ✅ Yes |
| **Tool C** | ❌ Partial export | ❌ Platform-locked | ⚠️ Limited |

**Key Insight**: Only Cursor passes both CRITICAL portability requirements; 
Tool B has moderate lock-in via SDK dependency; Tool C fails portability entirely.

**Winner**: Cursor (zero vendor lock-in)
```

#### 3.2: Generate Overall Rankings

**Summary Ranking Table:**
```markdown
## Overall Rankings

| Rank | Option | Total Score | CRITICAL | HIGH | MEDIUM | Status |
|------|--------|-------------|----------|------|--------|--------|
| 1 | Option A | 85/100 | 40/40 ✅ | 36/45 | 9/15 | ✅ All critical passed |
| 2 | Option B | 73/100 | 40/40 ✅ | 25/45 | 8/15 | ✅ All critical passed |
| 3 | Option C | 60/100 | 30/40 ⚠️ | 23/45 | 7/15 | ⚠️ 1 critical failed |
| 4 | Option D | 43/100 | 10/40 ❌ | 26/45 | 7/15 | ❌ 3 critical failed |
```

**Disqualification Analysis:**

Explicitly call out options failing CRITICAL requirements:

```markdown
### Critical Finding: Only N Options Pass All CRITICAL Requirements

**CRITICAL Requirements (Deal-Breakers):**
1. **[ID]**: [Requirement description]
2. **[ID]**: [Requirement description]
3. **[ID]**: [Requirement description]
4. **[ID]**: [Requirement description]

**❌ DISQUALIFIED:**
- **Option D**: Fails 3/4 (specific failures: [list])
  Impact: [Explain why this eliminates the option]
- **Option C**: Fails 1/4 (specific failure: [describe])
  Impact: [Explain constraint this creates]

**✅ QUALIFIED** (Pass all CRITICAL):
- Option A, Option B
```

#### 3.3: Create Use-Case Recommendations

Map scenarios to best options:

```markdown
## Use Case Recommendations

### Scenario 1: [Use Case Description]

**🏆 Top Choice: Option A or Option B**

**Why:**
- ✅ [Reason 1 - maps to CRITICAL/HIGH requirement]
- ✅ [Reason 2]
- ✅ [Reason 3]
- ✅ [Reason 4]

**Choose Option A if:** [Specific condition or preference]
**Choose Option B if:** [Alternative condition]

**⚠️ Avoid Option X:** [Reason - which requirement failed?]

---

### Scenario 2: [Another Use Case]
[Repeat structure]
```

**Cover Common Scenarios:**
- Best for beginners / non-technical users
- Best for large-scale enterprise use
- Best for budget-conscious users
- Best for specific technical requirements
- Best for specific workflows or integrations
- Best for teams of different sizes

#### 3.4: Build Decision Framework

Create step-by-step selection guide:

```markdown
## Decision Framework

### Step 1: Check CRITICAL Requirements

Does your use case require:
1. ✅ [CRITICAL requirement 1]?
2. ✅ [CRITICAL requirement 2]?
3. ✅ [CRITICAL requirement 3]?
4. ✅ [CRITICAL requirement 4]?

**If YES to all** → Options A, B, C
**If YES to 3/4** → Option D (acceptable trade-off?)
**If NO to multiple** → Option E, F (acknowledge limitations)

---

### Step 2: Prioritize by Need

**Primary Need: [Dimension/Feature]**
- Best: Option A ([score/capability])
- Alternative: Option B ([score/capability])

**Primary Need: [Alternative Dimension]**
- Best: Option C
- Alternative: Option D

---

### Step 3: Evaluate Budget

**Budget Tier 1 (<$X/month):**
- Recommended: Option A, Option B

**Budget Tier 2 ($X-Y/month):**
- Recommended: Option C

**Budget Tier 3 (>$Y/month or Enterprise):**
- Recommended: Option D, Option E
```

#### 3.5: Synthesize Strengths & Weaknesses

Per-option summary:

```markdown
## Detailed Analysis by Option

### Option A

**Strengths:**
- ✅ [Strength 1] (Dimension X, score Y)
- ✅ [Strength 2] (Dimension Z)
- ✅ [Strength 3]
- ✅ [Strength 4]

**Weaknesses:**
- ❌ [Limitation 1] (Dimension A)
- ⚠️ [Limitation 2] (Dimension B)
- ❌ [Limitation 3]

**Best for:** [Specific use cases where strengths align]

**Avoid if:** [Scenarios where weaknesses are problematic]

**Score Breakdown:**
- CRITICAL: X/40
- HIGH: Y/45
- MEDIUM: Z/15
- **TOTAL: N/100**

---

[Repeat for each option]
```

#### 3.6: Document Methodology

Include methodology section in report:

```markdown
## Evaluation Methodology

### Scoring System

- **CRITICAL (40 points)**: Deal-breaker requirements (10 points each, N questions)
  - Any "No" = 0 points (no partial credit)
  - Failing any CRITICAL may disqualify option
- **HIGH (45 points)**: Core features (1 point each, N questions)
  - "Yes"/"Full" = 1 point
  - "Limited"/"Partial" = 0.5 points
  - "No" = 0 points
- **MEDIUM (15 points)**: Differentiators (X points each, N questions)
  - Same scoring as HIGH (scaled to total 15 points)

**Total Possible**: 100 points

### Evidence Levels

- **P1 (Primary)**: Official documentation, vendor statements, published specs
- **P2 (Secondary)**: Verified user reports (<6 months), technical reviews with reproducible results
- **P3 (Tertiary)**: Reasonable inferences from stated capabilities (clearly marked)

**Conflict Resolution**: When P1 and P2 conflict, documented both perspectives and justified assessment based on recency, specificity, and reproducibility.

### Evaluation Date

All evaluations completed: YYYY-MM-DD

### Framework Versions

- **Dimensions**: evaluation-dimensions.md vX.X
- **Scoring**: scoring-criteria.md vX.X
- **Template**: evaluation-template.md vX.X

### Options Evaluated

1. [Option A] (version X, evaluated YYYY-MM-DD)
2. [Option B] (version Y, evaluated YYYY-MM-DD)
3. [Option C] (version Z, evaluated YYYY-MM-DD)
```

### Validation Checklist

- [ ] All dimensions have comparison tables
- [ ] Criticality indicators on all table columns
- [ ] Overall rankings with disqualification analysis
- [ ] Use-case recommendations for common scenarios (minimum 3-5 scenarios)
- [ ] Decision framework with step-by-step guidance
- [ ] Per-option strengths/weaknesses summaries
- [ ] Methodology section documenting process
- [ ] Framework versions referenced
- [ ] Evaluation dates documented

---

## Key Principles (Domain-Agnostic)

### 1. Evidence-Based Evaluation
- Always cite sources (P1 > P2 > P3)
- When sources conflict, document both perspectives
- Never make unsupported claims
- Absence of evidence is not evidence of absence (mark as "Unknown")

### 2. Structured Consistency
- Use same dimensions for all options
- Answer same questions for all options
- Apply same scoring rules uniformly
- Use consistent answer formats (Yes/No/Limited)

### 3. Actionable Synthesis
- Comparison report must guide decisions
- Map scenarios to best options
- Provide step-by-step selection framework
- Balance comprehensiveness with usability

### 4. Transparent Methodology
- Document scoring system
- Explain evidence standards
- Include framework versions
- Enable reproducibility and auditing

### 5. Critical Requirement Focus
- Identify deal-breakers early (CRITICAL questions)
- Disqualify options failing CRITICAL requirements
- Don't waste time on minor differentiators if core needs unmet
- Acknowledge trade-offs explicitly when relaxing CRITICAL requirements

### 6. Visual Hierarchy
- Use tables for scanability
- Use icons for quick interpretation (✅ ❌ ⚠️ 🔴 🟡 🟢)
- Include inline priority context
- Maintain visual consistency across all tables

### 7. Versioned Framework
- Tag framework versions (v1.0, v2.0, etc.)
- Reference versions in all outputs
- Enables auditing and reproducibility
- Allows framework evolution while maintaining compatibility

---

## Maintenance & Iteration

### When to Update Framework

**Major Version (e.g., v1.0 → v2.0):**
- Changed dimensions (added, removed, renamed)
- Changed scoring system (different weights or totals)
- Changed evidence standards
- Incompatible with previous evaluations

**Minor Version (e.g., v2.0 → v2.1):**
- Added/removed questions within existing dimensions
- Clarified question wording
- Updated answer formats
- Backward compatible with previous evaluations

**Patch Version (e.g., v2.1 → v2.1.1):**
- Fixed typos or formatting
- Clarified documentation
- No changes to evaluation criteria

### Re-evaluation Triggers

**When to re-evaluate an option:**
- Option releases major version
- Framework updated to new major version
- Significant market changes (acquisitions, pricing shifts, feature announcements)
- Initial evaluation >12 months old
- Stakeholder requirements change

### Quality Improvement

**Retrospective after completing comparison report:**
- Which dimensions provided most differentiation?
- Which questions were hardest to answer (evidence gaps)?
- Which questions had minimal variance (all options similar)?
- Did scoring weights reflect actual priorities?
- Were use-case recommendations actionable?

**Iterate framework for next research project:**
- Refine dimensions based on learnings
- Adjust question clarity where answers were ambiguous
- Modify weights if they didn't reflect true priorities
- Improve evidence standards if sources were unclear

---

## Repository Structure

Recommended folder layout for projects using this methodology:

```
project-name/
├── README.md                                # Project overview
├── research-context.md                      # Phase 0: Problem statement
├── framework/
│   ├── evaluation-dimensions.md             # Phase 1: Dimensions & questions
│   ├── scoring-criteria.md                  # Phase 1: Priority weights
│   ├── evaluation-template.md               # Phase 1: Output format
│   └── [optional-rationale.md]              # Optional: Question rationale
└── evaluations/
    ├── raw/
    │   ├── option-a-evaluation.md           # Phase 2: Individual evaluations
    │   ├── option-b-evaluation.md
    │   └── option-c-evaluation.md
    └── comparison-report.md                 # Phase 3: Final synthesis
```

---

## Adaptations for Different Domains

This methodology is domain-agnostic. Examples of how it adapts:

### Software Tools / Platforms
**Example dimensions:**
- Deployment Model, Package Management, Code Ownership, Framework Support, Git Integration, Collaboration Features, Pricing Model, IDE Type, Scale Limits, Security & Compliance

**CRITICAL questions typically focus on:**
- Portability (vendor lock-in)
- Core technical requirements (language support, infrastructure compatibility)
- Legal/compliance constraints

---

### Database Systems
**Example dimensions:**
- Data Model, Query Language, Scalability, Consistency Model, Operational Complexity, Cost Structure, Backup & Recovery, Security Model, Performance Characteristics, Ecosystem & Integrations

**CRITICAL questions typically focus on:**
- Data model fit (relational vs. document vs. graph)
- Consistency requirements (ACID vs. eventual)
- Scale requirements (horizontal vs. vertical)
- Deployment constraints (self-hosted vs. managed)

---

### Cloud Providers
**Example dimensions:**
- Compute Options, Storage Services, Networking, Cost Transparency, Geographic Coverage, Developer Experience, Security & Compliance, Support & SLA, Migration Tools, AI/ML Services

**CRITICAL questions typically focus on:**
- Geographic/compliance requirements (data residency)
- Cost predictability (budget constraints)
- Existing workload compatibility (migration feasibility)
- Required certifications (SOC2, HIPAA, etc.)

---

### CRM Software
**Example dimensions:**
- Contact Management, Sales Pipeline, Marketing Automation, Reporting & Analytics, Integrations, Mobile Access, Customization, User Experience, Pricing Model, Training & Support

**CRITICAL questions typically focus on:**
- Integration with existing tools (email, calendar, marketing)
- Scale (number of contacts, users)
- Budget constraints
- Required features (specific sales processes)

---

### SaaS Applications
**Example dimensions:**
- Core Functionality, User Management, API Access, Data Export, Uptime & Reliability, Security & Privacy, Customization, Integrations, Pricing Model, Support Quality

**CRITICAL questions typically focus on:**
- Core functionality must-haves
- Data portability (export capabilities)
- Privacy/compliance requirements
- Integration requirements (must connect to X, Y, Z)

---

## Conclusion

This methodology provides a **systematic, evidence-based, and repeatable** process for comparative research. By following the 4 phases—Define Scope, Create Framework, Evaluate Options, Generate Report—you create:

✅ **Defensible decisions** backed by documented evidence
✅ **Comprehensive analysis** covering all relevant dimensions
✅ **Actionable guidance** for stakeholders and decision-makers
✅ **Reusable framework** for future evaluations
✅ **Auditable process** with version-controlled methodology

### Success Criteria

You've successfully applied this methodology when:

- [ ] Decision-makers can understand the recommendation without reading individual evaluations
- [ ] All claims can be traced back to sources (P1/P2/P3)
- [ ] Options failing CRITICAL requirements are clearly disqualified with justification
- [ ] Use-case recommendations map specific scenarios to best options
- [ ] Framework can be reused for future comparisons in the same domain
- [ ] Report is actionable (readers know what to do next)

---

**Version**: 1.0  
**Last Updated**: 2026-02-04  
**License**: [Your License]  
**Maintainer**: [Your Name/Team]
