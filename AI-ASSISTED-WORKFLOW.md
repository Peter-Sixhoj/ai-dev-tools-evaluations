# AI-Assisted Workflow Guide

How to use an AI assistant (like me!) to complete a comparative research project using this methodology.

---

## Overview

This guide shows you how to **collaborate with an AI assistant** to systematically evaluate and compare multiple options. The AI helps you:

✅ Structure your requirements  
✅ Generate comprehensive evaluation frameworks  
✅ Research and document each option  
✅ Synthesize findings into actionable recommendations

**Time Investment**: 2-4 hours with AI vs. 8-16 hours manually

---

## Prerequisites

### You Provide
1. **Problem definition** - What are you trying to choose between?
2. **Requirements** - What must the solution do?
3. **Context** - Who will use it? What constraints exist?
4. **Options** - Which alternatives should be evaluated?

### AI Provides
1. **Structure** - Organizes your inputs into frameworks
2. **Research** - Gathers evidence from documentation and reviews
3. **Analysis** - Compares options systematically
4. **Documentation** - Generates markdown files following templates

---

## Table of Contents

- [The 4-Phase AI Workflow](#the-4-phase-ai-workflow) - Starting from scratch
- [Extending Existing Research](#extending-existing-research) - Adding options, updating evaluations ⭐ **NEW**
- [Advanced AI Collaboration](#advanced-ai-collaboration)
- [Tips & Best Practices](#tips-for-effective-ai-collaboration)
- [Common Workflows](#common-workflows)
- [Quality Checklists](#quality-checklist)
- [Troubleshooting](#troubleshooting)

---

## The 4-Phase AI Workflow

### Phase 0: Define Research Context (15-30 minutes)

**Goal**: Create `research-context.md` documenting your problem, requirements, and scope.

#### Starting Prompt

```
I want to use the Comparative Research Methodology from 
https://github.com/Peter-Sixhoj/ai-dev-tools-evaluations to evaluate [CATEGORY].

I need to choose between:
1. [Option A]
2. [Option B]
3. [Option C]
...

The solution will be used by [STAKEHOLDERS] for [USE CASES].

Please help me complete Phase 0 by creating a research-context.md file.
```

#### AI Will Ask You

1. **What problem are you solving?**
   - Example: "Need a CRM for 50-person sales team with complex pipelines"

2. **What are your deal-breaker requirements? (CRITICAL)**
   - Example: "Must integrate with Salesforce, must support custom fields"

3. **What are important requirements? (HIGH priority)**
   - Example: "Email integration, mobile apps, reporting dashboards"

4. **What are nice-to-have features? (MEDIUM priority)**
   - Example: "AI insights, workflow automation, API access"

5. **What's your budget and timeline?**
   - Example: "$50-100/user/month, decision needed in 2 weeks"

6. **What's your technical context?**
   - Example: "Team uses Google Workspace, needs SSO, cloud-only"

#### What You'll Get

A complete `research-context.md` file structured as:
- Decision objective
- 3-5 CRITICAL requirements (deal-breakers)
- 40-50 HIGH priority requirements
- 50-60 MEDIUM priority requirements
- Stakeholder analysis
- Use cases
- Technical context
- Success criteria

#### Example Reference

See how this was done: [`projects/ai-dev-tools/research-context.md`](projects/ai-dev-tools/research-context.md)

---

### Phase 1: Define Evaluation Framework (30-60 minutes)

**Goal**: Create evaluation framework in `framework/` folder with dimensions, questions, and scoring.

#### Starting Prompt

```
Based on my research-context.md, please create the Phase 1 evaluation framework:

1. evaluation-dimensions.md - Define 15-25 dimensions with 80-120 specific questions
2. scoring-criteria.md - Assign CRITICAL/HIGH/MEDIUM priorities to each question
3. evaluation-template.md - Create the format for individual evaluations

Use the templates in /templates/ as starting points.
```

#### AI Will Generate

**1. Evaluation Dimensions** (`evaluation-dimensions.md`)

15-25 dimensions organized by theme:
- Technical Capabilities (Language support, Integrations, APIs)
- Workflow Support (Git, Collaboration, Deployment)
- Scale & Performance (Codebase limits, Team size, Speed)
- Cost & Licensing (Pricing model, Enterprise options)
- Security & Compliance (Certifications, Data residency)

Each dimension has 3-7 specific questions:
```markdown
## Dimension 5: Git Integration

**5.1**: Does it have native Git integration?
- Answer Format: Yes/No
- Rationale: [Why this matters]

**5.2**: Can you push directly to GitHub/GitLab?
- Answer Format: Both/GitHub only/GitLab only/Neither
- Rationale: [Why this matters]
```

**2. Scoring Criteria** (`scoring-criteria.md`)

Priority assignments:
- 🔴 **CRITICAL** (4 questions × 10 points = 40 points)
- 🟡 **HIGH** (45 questions × 1 point = 45 points)
- 🟢 **MEDIUM** (54 questions × 0.28 points = 15 points)
- **Total**: 100 points

**3. Evaluation Template** (`evaluation-template.md`)

Format specification for Phase 2 evaluations.

#### What to Review

✅ **Check dimensions are mutually exclusive** (no overlap)  
✅ **Verify questions are specific and measurable**  
✅ **Confirm CRITICAL requirements match your deal-breakers**  
✅ **Adjust priorities if needed** (more or fewer questions per priority)

#### Iteration Example

```
You: "Add a dimension for 'Customer Support' with questions about 
response time, support channels, and documentation quality."

AI: [Updates evaluation-dimensions.md with new dimension]
```

#### Example Reference

See completed framework: [`projects/ai-dev-tools/framework/`](projects/ai-dev-tools/framework/)

---

### Phase 2: Conduct Individual Evaluations (1-2 hours)

**Goal**: Research each option and create `evaluations/[option]-evaluation.md` files.

#### Starting Prompt (Per Option)

```
Please evaluate [OPTION NAME] using the framework in my 
evaluation-dimensions.md and evaluation-template.md.

For each dimension:
1. Research the option's capabilities
2. Answer all questions with evidence (cite sources as P1/P2/P3)
3. Provide a narrative assessment
4. Document strengths and limitations

Create evaluations/[option-name]-evaluation.md following the template.
```

#### AI Research Process

**Evidence Levels** (P1 > P2 > P3):
- **P1** (Primary): Official documentation, pricing pages, vendor statements
- **P2** (Secondary): Verified user reports (<6 months), technical reviews with examples
- **P3** (Tertiary): Reasonable inferences from stated capabilities (marked clearly)

**For Each Dimension**, AI will:
1. Search official documentation
2. Review recent user reports (Reddit, forums, reviews)
3. Answer all questions with evidence citations
4. Calculate dimension score
5. Note strengths and limitations

#### What You'll Get (Per Option)

A complete evaluation file with:
- Executive summary
- Narrative assessment for each dimension
- Answers to all 80-120 questions with evidence
- Decision Scorecard:
  - CRITICAL score: X/40
  - HIGH score: Y/45
  - MEDIUM score: Z/15
  - **Total**: N/100
- Key differentiators (strengths/limitations)

#### Reviewing AI Research

**Verify Critical Claims**:
```
You: "Can you verify the claim that [Option X] requires vendor SDK 
for deployment? Check their official docs."

AI: [Provides P1 evidence with direct link to documentation]
```

**Request Additional Evidence**:
```
You: "Find recent user reports about [Option X]'s performance 
with large codebases."

AI: [Searches and summarizes P2 evidence from past 6 months]
```

#### Parallel Evaluation

You can ask AI to evaluate multiple options in parallel:
```
Please evaluate all 5 options:
1. Option A
2. Option B
3. Option C
4. Option D
5. Option E

Create separate evaluation files for each.
```

#### Example Reference

See completed evaluations: [`projects/ai-dev-tools/evaluations/`](projects/ai-dev-tools/evaluations/)

---

### Phase 3: Generate Comparison Report (30-45 minutes)

**Goal**: Synthesize all evaluations into `comparison-report.md` at project root.

#### Starting Prompt

```
Based on the 6 individual evaluations in evaluations/, please create 
the Phase 3 comparison-report.md.

Include:
1. Overall rankings by total score
2. Critical requirement analysis (which options pass/fail?)
3. Dimension-by-dimension comparison tables
4. Use case recommendations
5. Decision framework

Use comparison-report-template.md as the format.
```

#### AI Will Generate

**1. Overall Rankings**

Scorecard table:
| Rank | Option | Total | CRITICAL | HIGH | MEDIUM | Status |
|------|--------|-------|----------|------|--------|--------|
| 1 | Option A | 85/100 | 40/40 ✅ | 38/45 | 7/15 | ✅ Pass |
| 2 | Option B | 73/100 | 30/40 ⚠️ | 35/45 | 8/15 | ⚠️ Partial |
| 3 | Option C | 45/100 | 10/40 ❌ | 30/45 | 5/15 | ❌ Fail |

**2. Critical Analysis**

Which options are disqualified?
- Option C fails 3/4 CRITICAL requirements → **Disqualified**
- Option B fails 1/4 CRITICAL requirements → **Proceed with caution**
- Options A qualified → **Proceed to detailed comparison**

**3. Comparison Tables**

For each dimension, side-by-side comparison:

| Dimension 5: Git Integration | Option A | Option B | Option C |
|------------------------------|----------|----------|----------|
| Native Git integration? | ✅ Yes | ✅ Yes | ❌ No |
| Push to GitHub/GitLab? | Both | GitHub only | Neither |
| Visual Git UI? | ✅ Yes | ❌ No | N/A |

**4. Use Case Recommendations**

```markdown
### Scenario 1: Enterprise Team (100+ developers)
🏆 **Recommendation**: Option A

Why:
- ✅ Proven at scale (Fortune 500 companies)
- ✅ Full polyglot support
- ✅ Zero vendor lock-in

Avoid:
- ❌ Option C (severe vendor lock-in)
```

**5. Decision Framework**

Step-by-step guide:
1. Check CRITICAL requirements → Eliminate failures
2. Prioritize by primary need → Match use case
3. Evaluate budget → Select tier

#### Refining the Report

```
You: "Add a section comparing pricing models across all 5 options."

AI: [Adds detailed pricing comparison table]

You: "Emphasize the vendor lock-in risk in the executive summary."

AI: [Updates summary with prominent warning]
```

#### Example Reference

See completed report: [`projects/ai-dev-tools/comparison-report.md`](projects/ai-dev-tools/comparison-report.md) ⭐

---

## Extending Existing Research

### Overview

**Use Case**: You've completed a comparison but need to:
- Add a new option to evaluate
- Re-evaluate an existing option (after updates)
- Expand the framework (add dimensions)
- Update priorities (requirements changed)

**Why This Matters**: Research is iterative. Markets change, new products emerge, requirements evolve. The methodology supports living documents.

---

### Adding a New Option (30-60 minutes)

**Scenario**: You've evaluated 6 AI dev tools but discovered a 7th option worth considering.

#### Starting Prompt

```
Add [PRODUCT NAME] to my existing project at projects/[project-name]/.

Steps:
1. Read the framework from projects/[project-name]/framework/
2. Evaluate [PRODUCT NAME] using those exact criteria
3. Create evaluations/[product-name]-evaluation.md
4. Update comparison-report.md to include this new option
5. Recalculate rankings and comparison tables
```

#### What AI Will Do

1. **Read Existing Framework**
   - Loads `evaluation-dimensions.md` (all questions)
   - Loads `scoring-criteria.md` (priorities)
   - Loads `evaluation-template.md` (format)

2. **Evaluate New Option**
   - Researches [PRODUCT NAME]
   - Answers all 80-120 questions with evidence
   - Calculates Decision Scorecard
   - Creates `evaluations/[product-name]-evaluation.md`

3. **Read Existing Evaluations**
   - Loads all files in `evaluations/` folder
   - Extracts scores and key findings

4. **Update Comparison Report**
   - Adds new option to rankings table
   - Recalculates ranks (1st, 2nd, 3rd...)
   - Adds new column to all comparison tables
   - Updates use case recommendations if needed
   - Saves updated `comparison-report.md`

#### Example Conversation

```
You: "Add Cline to my AI Dev Tools project."

AI: "I'll evaluate Cline using your existing framework. Give me a moment 
to research Cline and answer all 103 questions...

[Research happens]

Completed! Here's what I found:
- Cline scores 78/100 (40/40 CRITICAL, 32/45 HIGH, 6/15 MEDIUM)
- Passes all CRITICAL requirements ✅
- Ranks 3rd overall (between Windsurf and Bolt.new)
- Key strength: Strong Git integration
- Key limitation: Limited language support vs. Cursor

I've created evaluations/cline-evaluation.md and updated 
comparison-report.md with Cline included in all tables."

You: "Show me the updated rankings table."

AI: [Displays updated table with 7 options]
```

#### Verification Checklist

✅ New evaluation file created  
✅ All questions answered with evidence  
✅ Scores calculated correctly  
✅ Comparison report updated  
✅ Rankings recalculated  
✅ New option added to all comparison tables  
✅ Use case recommendations reviewed

---

### Re-Evaluating an Existing Option (30-45 minutes)

**Scenario**: A tool you evaluated 6 months ago released major updates.

#### Starting Prompt

```
Re-evaluate [EXISTING OPTION] in my project at projects/[project-name]/.

Context:
- [OPTION] released version [X.Y] on [DATE]
- Major changes: [list key changes]

Steps:
1. Read the existing evaluation: evaluations/[option]-evaluation.md
2. Research current capabilities (as of [DATE])
3. Update answers where capabilities changed
4. Recalculate scores
5. Create evaluations/[option]-evaluation-v2.md (preserve original)
6. Update comparison-report.md with new scores
```

#### What AI Will Do

1. **Read Original Evaluation**
   - Loads previous assessment
   - Notes original scores

2. **Research Current State**
   - Searches for recent documentation
   - Looks for version-specific changes
   - Finds user reports from past 3 months

3. **Compare Old vs. New**
   - Identifies changed answers
   - Calculates score delta
   - Highlights key improvements/regressions

4. **Update Comparison**
   - Updates rankings if position changed
   - Updates comparison tables
   - Notes "Updated [DATE]" in report

#### Example Conversation

```
You: "Re-evaluate Bolt.new. They added TypeScript support and 
improved Git integration in v2.0 (Jan 2026)."

AI: "I'll re-evaluate Bolt.new with v2.0 capabilities...

[Research happens]

Key changes found:
- TypeScript support: No → Yes (Question 1.2 changed)
- Git UI improvements: Limited → Full (Question 5.3 changed)
- Score change: 67/100 → 74/100 (+7 points)
- Ranking change: 5th → 4th (passed Replit)

Created evaluations/bolt-new-evaluation-v2.md
Updated comparison-report.md with new scores and rankings."
```

---

### Expanding the Framework (45-60 minutes)

**Scenario**: You realize you forgot to evaluate an important dimension.

#### Starting Prompt

```
Expand my framework at projects/[project-name]/framework/ by adding:

New Dimension: [DIMENSION NAME]
Questions:
1. [Question 1]
2. [Question 2]
3. [Question 3]

Priorities:
- Question 1: CRITICAL
- Question 2: HIGH
- Question 3: MEDIUM

Then:
1. Update evaluation-dimensions.md
2. Update scoring-criteria.md
3. Re-evaluate all options for this new dimension
4. Update all evaluation files
5. Update comparison-report.md
```

#### What AI Will Do

1. **Update Framework Files**
   - Adds new dimension to `evaluation-dimensions.md`
   - Updates `scoring-criteria.md` with new priorities
   - Adjusts scoring weights if needed

2. **Re-Evaluate All Options**
   - Answers new questions for each existing evaluation
   - Adds new dimension section to each file
   - Recalculates all scores

3. **Update Comparison**
   - Adds new dimension comparison table
   - Recalculates rankings (if scores changed)
   - Updates executive summary if rankings changed

#### Example Conversation

```
You: "Add a 'Mobile Development' dimension with 3 questions:
1. Does it support mobile app development? (CRITICAL)
2. iOS development support? (HIGH)
3. Android development support? (HIGH)"

AI: "I'll add the Mobile Development dimension and re-evaluate all 6 tools...

[Research happens]

Completed! Key findings:
- 4/6 tools support mobile development
- Replit and Lovable have strong mobile support
- Cursor and Windsurf have limited mobile capabilities
- Rankings changed: Replit moved from 4th → 3rd

All evaluation files and comparison report updated."
```

---

### Updating Priorities (15-30 minutes)

**Scenario**: Your requirements changed - something that was MEDIUM is now CRITICAL.

#### Starting Prompt

```
Update priorities in my framework at projects/[project-name]/framework/:

Changes:
- Move Question [X.Y] from [OLD] to [NEW] priority
- Move Question [A.B] from [OLD] to [NEW] priority

Then:
1. Update scoring-criteria.md
2. Recalculate all scores in evaluation files
3. Update comparison-report.md with new rankings
```

#### What AI Will Do

1. **Update Scoring Criteria**
   - Modifies `scoring-criteria.md`
   - Adjusts point allocations if needed

2. **Recalculate All Scores**
   - Recalculates Decision Scorecards in all evaluations
   - Updates each evaluation file

3. **Update Rankings**
   - Recalculates overall rankings
   - Updates comparison report

#### Example Conversation

```
You: "Move 'Vendor Lock-in' (Question 10.1) from HIGH to CRITICAL. 
This is now a deal-breaker for us."

AI: "I'll update the priority and recalculate scores...

[Calculations happen]

Critical change:
- Bolt.new and Lovable now FAIL CRITICAL requirements (vendor lock-in)
- Status changed from 'Pass with caution' → 'Disqualified'
- New rankings: Only 4 tools qualify (Cursor, Windsurf, Replit, Base44)

Updated scoring-criteria.md, all evaluation files, and comparison-report.md."
```

---

### Quick Reference: Extension Prompts

#### Add New Option
```
"Add [PRODUCT] to my [PROJECT] project."
```

#### Re-Evaluate After Updates
```
"Re-evaluate [PRODUCT] in my [PROJECT]. They released [VERSION] with [CHANGES]."
```

#### Add Dimension
```
"Add '[DIMENSION]' dimension to my [PROJECT] framework with these questions: [LIST]."
```

#### Change Priorities
```
"Move Question [X.Y] from [OLD] to [NEW] priority in my [PROJECT] framework."
```

#### Batch Update
```
"Update my [PROJECT] project:
1. Add [PRODUCT A]
2. Re-evaluate [PRODUCT B] (v2.0)
3. Add '[DIMENSION]' dimension
4. Move Question [X.Y] to CRITICAL"
```

---

## Advanced AI Collaboration

### Iterative Refinement

**Round 1**: Initial framework
```
You: "Generate Phase 1 framework"
AI: [Creates evaluation-dimensions.md with 20 dimensions]
```

**Round 2**: Add missing dimension
```
You: "Add a dimension for 'Developer Experience' covering 
onboarding time, learning curve, and documentation quality."
AI: [Updates framework]
```

**Round 3**: Adjust priorities
```
You: "Move question 5.3 from MEDIUM to HIGH priority."
AI: [Updates scoring-criteria.md]
```

### Evidence Validation

**Request Verification**:
```
You: "Verify that [Option X] really supports Rust. Check their 
official docs and recent user reports."

AI: [Provides P1 evidence from docs + P2 evidence from user reports]
```

**Challenge AI Inferences**:
```
You: "You marked [Option Y] as having 'full API support' based on 
inference (P3). Can you find official documentation (P1)?"

AI: [Searches for P1 evidence or clarifies that only P3 is available]
```

### Staying Organized

**Save AI Outputs to Files**:
```
You: "Save the evaluation-dimensions.md content you just generated 
to projects/my-project/framework/evaluation-dimensions.md"

AI: [Creates file with generated content]
```

**Track Versions**:
```
You: "Add version numbers to all framework files (v1.0)"

AI: [Updates metadata in each file]
```

---

## Tips for Effective AI Collaboration

### ✅ Do This

1. **Be Specific**: "Add questions about mobile app support" → "Add 3 questions: iOS app availability, Android app availability, offline mode support"

2. **Reference Examples**: "Use the same structure as projects/ai-dev-tools/framework/evaluation-dimensions.md"

3. **Iterate**: Start with basics, refine based on results

4. **Validate Critical Claims**: Always verify P1 evidence for CRITICAL requirements

5. **Use the Templates**: Point AI to templates in `/templates/`

6. **Break It Down**: Evaluate 1-2 options at a time instead of all at once

### ❌ Avoid This

1. **Vague Requests**: "Make it better" → AI doesn't know what to improve

2. **Skipping Phase 0**: Jumping to evaluations without defining requirements

3. **Accepting Everything**: Review AI outputs, especially evidence quality

4. **Too Many Options**: 10+ options is overwhelming; start with 3-5 finalists

5. **Ignoring Evidence Levels**: P3 (inference) is not sufficient for CRITICAL questions

---

## Common Workflows

### Quick Start (2-3 hours)

**Best for**: Familiar domain, clear requirements, 3-5 options

```
1. [15 min] Tell AI your problem → Get research-context.md
2. [30 min] AI generates framework → Quick review
3. [90 min] AI evaluates all options → Review CRITICAL questions
4. [30 min] AI generates comparison report → Done!
```

### Thorough Analysis (4-6 hours)

**Best for**: Unfamiliar domain, complex requirements, 5-8 options

```
1. [30 min] Detailed discussion with AI → Comprehensive research-context.md
2. [60 min] AI generates framework → Iterate to refine
3. [2-3 hours] AI evaluates options one-by-one → Verify each
4. [45 min] AI generates report → Refine recommendations
5. [30 min] Add custom analysis sections
```

### Collaborative Team Research (1-2 days)

**Best for**: Team decisions, stakeholder buy-in needed, 8-10 options

```
Day 1:
1. [1 hour] Team workshop → Draft research-context.md with AI
2. [1 hour] Team reviews → Refine requirements
3. [2 hours] AI generates framework → Team validates

Day 2:
4. [3 hours] AI evaluates all options → Team members verify evidence
5. [1 hour] AI generates report → Team reviews
6. [1 hour] Team discussion → Final recommendations
```

### Living Document (Ongoing)

**Best for**: Long-term research, market monitoring, continuous evaluation

```
Initial (Week 1):
1. Complete Phases 0-3 with 5 initial options

Month 2:
2. Add 2 new market entrants
3. Re-evaluate 1 option that released major update

Quarter 2:
4. Add 'Security Compliance' dimension (new requirement)
5. Move 2 questions from MEDIUM to CRITICAL
6. Remove 1 discontinued product

Ongoing:
7. Monthly: Check for product updates
8. Quarterly: Re-evaluate top 3 options
9. Annually: Full framework review
```

---

## Quality Checklist

Before finalizing, verify with AI:

### Phase 0 ✅
- [ ] Decision objective is clear
- [ ] 3-5 CRITICAL requirements defined
- [ ] 40-50 HIGH requirements documented
- [ ] 50-60 MEDIUM requirements listed
- [ ] Stakeholders identified
- [ ] Use cases described

### Phase 1 ✅
- [ ] 15-25 dimensions defined
- [ ] 80-120 questions total
- [ ] All questions have answer formats
- [ ] All questions have rationale
- [ ] CRITICAL priorities match Phase 0
- [ ] Scoring totals to 100 points

### Phase 2 ✅
- [ ] All options evaluated
- [ ] All questions answered
- [ ] Evidence levels marked (P1/P2/P3)
- [ ] CRITICAL questions have P1 or P2 evidence
- [ ] Decision Scorecards calculated
- [ ] Strengths and limitations documented

### Phase 3 ✅
- [ ] Overall rankings table complete
- [ ] Critical analysis identifies disqualifications
- [ ] Comparison tables for all dimensions
- [ ] Use case recommendations provided
- [ ] Decision framework included
- [ ] Executive summary clear

### Extensions ✅
- [ ] New evaluations use same framework
- [ ] Scores recalculated after changes
- [ ] Comparison report updated
- [ ] Version history maintained
- [ ] Update dates documented

---

## Example Conversation Starters

### Starting a New Project

```
"I want to use the Comparative Research Methodology to evaluate 
project management tools. I'm comparing Jira, Linear, Asana, 
Monday.com, and ClickUp for a 30-person product team. 

Please help me complete Phase 0 using the research-context-template."
```

### Generating Framework

```
"Based on my research-context.md, generate the Phase 1 framework 
with evaluation-dimensions.md (20 dimensions, 100 questions), 
scoring-criteria.md (CRITICAL/HIGH/MEDIUM priorities), and 
evaluation-template.md.

Use projects/ai-dev-tools/framework/ as a reference for structure."
```

### Evaluating Options

```
"Please evaluate Jira using my evaluation-dimensions.md. 

For each dimension:
- Answer all questions with evidence
- Cite official docs (P1), user reports (P2), or mark inferences (P3)
- Calculate scores
- Note strengths and limitations

Create evaluations/jira-evaluation.md following the template."
```

### Creating Comparison

```
"Based on the 5 evaluations in evaluations/, create comparison-report.md 
at the project root.

Emphasize:
- Which tools pass all CRITICAL requirements?
- Which is best for agile teams vs. waterfall?
- Cost comparison for 30 users

Use projects/ai-dev-tools/comparison-report.md as format reference."
```

### Adding New Option (Extension)

```
"Add ClickUp to my project management tools comparison."
```

### Re-Evaluating (Extension)

```
"Re-evaluate Linear in my project. They released v2.5 with 
improved API and Slack integration."
```

---

## Troubleshooting

### "AI generated too few/many questions"

```
You: "I need exactly 100 questions total. Currently have 85. 
Add 15 more questions covering [missing areas]."
```

### "AI lacks domain knowledge"

```
You: "Here's context about [domain]: [paste brief explanation]. 
Now regenerate the framework."
```

### "Evidence quality is weak"

```
You: "Question 3.2 has P3 evidence but it's CRITICAL. 
Find P1 or P2 evidence, or mark as 'Unable to verify'."
```

### "Scores seem wrong"

```
You: "Recalculate the Decision Scorecard for [Option X]. 
Show your work: CRITICAL (N questions × 10 points) + 
HIGH (N questions × 1 point) + MEDIUM (N questions × 0.28 points)."
```

### "Report is too long"

```
You: "Create an executive summary version (2 pages max) with:
- Rankings table
- Critical findings
- Top recommendation only"
```

### "I added an option but comparison wasn't updated"

```
You: "Update comparison-report.md to include [NEW OPTION]. 
Add to rankings table and all comparison tables."
```

### "Scores changed but rankings are wrong"

```
You: "Recalculate rankings in comparison-report.md based on 
updated scores in all evaluation files."
```

---

## Next Steps

Ready to start? 

1. **Copy this prompt** and start a conversation with an AI assistant:
   ```
   I want to use the Comparative Research Methodology from 
   https://github.com/Peter-Sixhoj/ai-dev-tools-evaluations 
   to evaluate [YOUR CATEGORY].
   
   Please help me complete Phase 0.
   ```

2. **Reference the example project** as you go:
   - [AI Dev Tools Research Context](projects/ai-dev-tools/research-context.md)
   - [Framework](projects/ai-dev-tools/framework/)
   - [Evaluations](projects/ai-dev-tools/evaluations/)
   - [Comparison Report](projects/ai-dev-tools/comparison-report.md) ⭐

3. **Iterate and refine** - Research is iterative, not linear

4. **Share your results** - Add your project to `projects/` and contribute back!

---

## Getting Help

Stuck? Ask AI:
```
"I'm stuck on [Phase/Step]. Can you:
1. Explain what's needed
2. Show an example from projects/ai-dev-tools/
3. Generate a starting point for me to refine"
```

Still stuck? [Create an issue](../../issues) or reach out to the community.

---

**Methodology Version**: 1.0  
**AI Workflow Version**: 1.1  
**Last Updated**: 2026-02-04
