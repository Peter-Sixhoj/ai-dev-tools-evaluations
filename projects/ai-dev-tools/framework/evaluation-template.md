# AI Development Tools Evaluation Template

**Version**: 2.0  
**Date Created**: 2026-02-03  
**Last Updated**: 2026-02-04  
**References**: evaluation-metrics.md v2.0, decision-criteria.md v2.0  
**Status**: Active

## Purpose

This template defines the structure, formatting, and evidence requirements for all AI development tool evaluations. Use in conjunction with:
- `evaluation-metrics.md` (v2.0) which defines the 20 metrics + 103 embedded decision questions
- `decision-criteria.md` (v2.0) which provides question definitions and priority levels

**Key Enhancement (v2.0)**: Each metric section now includes sub-sections for embedded decision questions, enabling evaluations to automatically answer all 103 critical decision criteria while maintaining narrative depth.

## Report Structure

### Executive Summary

Start each evaluation with **2-3 sentences** covering:
- Product's primary value proposition
- Core deployment model (cloud/local/hybrid)
- Primary target audience or use case

**Example**:
> Cursor is a VS Code fork that integrates AI code generation directly into the IDE experience. It operates as a local desktop application with cloud-based AI model access, targeting professional developers working on enterprise-scale codebases. The tool emphasizes multi-file context awareness and existing workflow integration over standalone web-based development.

---

## Metric Sections with Embedded Questions

Create a dedicated section for each of the **20 metrics** defined in `evaluation-metrics.md` using this structure:

### Section Header
Use metric name exactly as defined in evaluation-metrics.md (use `##` heading level)

### Capability Assessment
**Format**: 2-4 sentences covering:
1. Current capability assessment - What it does and does not do
2. Evidence with citations - Official documentation, reviews, or verified sources
3. Limitations or constraints - Discovered restrictions or caveats

### Embedded Decision Questions
**Format**: Sub-section (use `###` heading) with answers to all embedded questions for that metric

Structure each question answer as:
```markdown
- **[Priority Icon] [Question ID]: [Question Text]**
  Answer: [Specific response per question's answer format]
  Evidence: [P1/P2/P3 citation]
  Notes: [Any clarifications or context]
```

**Example for Metric 5 (Git Integration)**:

```markdown
## 5. Git Integration

[Narrative assessment paragraph here]

**Evidence**: Official documentation v2.3 (January 2026) confirms UI-based Git operations. Community reports indicate terminal access for advanced Git features (P2 evidence from verified user reports December 2025).

**Limitations**: No GitLab or Bitbucket native integration; GitHub-focused workflows only.

### Decision Questions for Git Integration

- **🟡 SHOULD-HAVE | 5.1: Does it have native Git integration?**
  Answer: Yes
  Evidence: Official docs show built-in Git UI with commit/push/pull operations
  Notes: Terminal access available for advanced operations

- **🟡 SHOULD-HAVE | 5.2: Can you push directly to GitHub/GitLab?**
  Answer: GitHub only
  Evidence: Verified user reports confirm GitHub native integration, GitLab requires manual CLI
  Notes: GitLab support on roadmap (Beta Q2 2026)

- **🟡 SHOULD-HAVE | 5.3: Does it support pull request workflows?**
  Answer: Yes
  Evidence: Official feature documentation, tested on 10+ enterprise repos
  Notes: Full PR review UI with commenting, approval gates, CI/CD integration

- **🟢 NICE-TO-HAVE | 5.4: Does it have a visual Git UI?**
  Answer: Yes
  Evidence: VS Code-like Git panel with visual file staging, history, blame
  Notes: N/A

- **🟢 NICE-TO-HAVE | 5.5: Can it handle branch management?**
  Answer: Yes
  Evidence: Official docs, tested branch creation, switching, merging
  Notes: Interactive rebase requires terminal
```

---

## Complete Metric Template

Here's the full structure to use for each metric section:

```markdown
## [X]. [Metric Name]

### Capability Assessment
[2-4 sentence narrative assessment]

**Evidence**: [Citations with P1/P2/P3 markers]

**Limitations**: [Specific constraints]

### Decision Questions for [Metric Name]

- **[Priority] | [ID]: [Question]**
  Answer: [Specific response per answer format]
  Evidence: [P1/P2/P3 source]
  Notes: [Additional context]

- **[Priority] | [ID]: [Question]**
  Answer: [Specific response per answer format]
  Evidence: [P1/P2/P3 source]
  Notes: [Additional context]

[Repeat for all embedded questions in this metric]
```

---

## Key Differentiators Section

Conclude with a dedicated section highlighting:
- What makes this tool unique compared to similar products
- Critical strengths and limitations for the target stack
- Primary competitive advantages
- Decision-making recommendations (when to use vs. alternatives)

**Example**:

```markdown
## Key Differentiators

**Unique Strengths**:
- Multi-file context awareness across entire codebase (10k+ files)
- Native VS Code extension compatibility (90%+ of marketplace)
- Local-first architecture with offline capability

**Critical Limitations**:
- Requires local compute resources (8GB RAM minimum)
- No built-in deployment automation
- Limited collaboration features (Git-only workflows)

**Best Suited For**: Teams with existing VS Code workflows, large enterprise codebases requiring deep context awareness, developers who prefer local-first tooling.

**Not Recommended For**: Teams requiring real-time collaborative editing, beginners seeking guided full-stack scaffolding, projects requiring integrated deployment pipelines.
```

---

## Decision Scorecard Summary

After the Key Differentiators section, include a **Decision Scorecard** that summarizes the evaluation against decision criteria:

```markdown
## Decision Scorecard

### Critical Requirements (MUST-HAVE)
| Question | Answer | Status |
|----------|--------|--------|
| 1.1b: Applications deployable outside platform? | Yes | ✅ PASS |
| 3.1: Export 100% of code? | Yes | ✅ PASS |
| 3.2: No proprietary runtime dependencies? | Yes | ✅ PASS |
| 10.1: Standard dev commands work? | Yes | ✅ PASS |
| **MUST-HAVE SCORE** | **40/40** | **✅ ALL PASS** |

### Scoring Summary
- **MUST-HAVE Score**: 40/40 (100%)
- **SHOULD-HAVE Score**: 38/45 (84%)
- **NICE-TO-HAVE Score**: 12/15 (80%)
- **TOTAL SCORE**: 90/100

### Assessment
[2-3 sentence summary of evaluation results and primary findings]
```

---

## Formatting Requirements

### Markdown Standards

- Use `##` (h2) for metric section headers
- Use `###` (h3) for subsections (Decision Questions, etc.)
- Use bullet points (`-` or `*`) for question lists
- Use comparison tables **only** when directly comparing multiple specific values
- Keep narrative sections concise: **2-4 sentences per metric** unless complexity requires more
- Use **bold** for emphasis on key terms or capabilities
- Use `code formatting` for technical terms, file paths, commands, question IDs

### Code Blocks

When including code examples or configuration:

````markdown
```typescript
// Example of generated code structure
interface Config {
  apiKey: string;
  endpoint: string;
}
```
````

### Tables

Use tables for structured comparisons and scoring only:

```markdown
| Feature | Support Level | Evidence |
|---------|---------------|----------|
| React | Full | Official docs v1.2 |
| Vue | Experimental | Beta announcement Jan 2026 |
| Angular | Not supported | Product roadmap |
```

---

## Citation Requirements

Every claim must include:

1. **Source reference**: Official docs, verified reports, direct observation
2. **Version numbers or dates**: When capabilities may change over time
3. **Beta/experimental flags**: Where applicable
4. **Clear marking of assumptions**: Or unverified claims

### Citation Format Examples

**Official Documentation**:
> "Supports TypeScript 5.3+ with full type inference" (Official Docs, v2.1, January 2026)

**Verified User Reports**:
> "Community testing confirms 10k+ file context awareness" (P2: Reddit thread with 50+ confirmations, December 2025)

**Reasonable Inference**:
> "Likely supports Rust given VS Code extension compatibility" (P3: Inference from VS Code marketplace compatibility claim)

**Beta/Experimental**:
> "Vue 3 support available in beta" (Beta program announcement, January 15, 2026)

---

## Evidence Prioritization Framework

Apply **P1/P2/P3 hierarchy** when conflicting information appears:

### P1: Official Sources (Highest Priority)
- Official product documentation
- Vendor statements and announcements
- Published roadmaps
- Official blog posts
- Pricing pages

**When to use**: This is the primary evidence source. Always prefer P1 when available.

### P2: Verified User Reports (Secondary)
- Recent technical reviews (within 6 months)
- Community forum discussions with multiple confirmations
- GitHub issues with vendor responses
- Stack Overflow answers from verified users
- Technical blog posts with reproducible examples

**When to use**: When P1 evidence is unavailable, outdated, or contradicted by consistent user experience.

### P3: Reasonable Inference (Tertiary)
- Framework defaults or expected behavior
- Logical deductions from stated capabilities
- Industry standard assumptions

**When to use**: Only when P1 and P2 are unavailable. **MUST be clearly marked as inference**.

### Handling Conflicts

```markdown
**Evidence Conflict**: Official docs claim "full Rust support" (P1, Dec 2025), 
but community reports indicate syntax highlighting only, no LSP integration 
(P2, 15+ verified reports Jan 2026). Assessment: Limited Rust support, 
primarily syntax highlighting.
```

---

## Export Instructions

Conclude each evaluation with:

```markdown
---

## Export Metadata

**File Path**: `/evaluations/raw-threads/[product-name]-evaluation.md`  
**Evaluation Date**: [YYYY-MM-DD]  
**Evaluator**: [Name/ID]  
**Metrics Version**: evaluation-metrics.md v2.0  
**Template Version**: evaluation-template.md v2.0  
**Decision Criteria**: decision-criteria.md v2.0  

**Status**: Ready for synthesis via GitHub Actions

**Questions Answered**: 103/103 decision questions
**Metrics Covered**: 20/20
**Critical Requirements**: [X/4 MUST-HAVE questions passed]
```

### File Naming Convention

- Use lowercase with hyphens: `cursor-evaluation.md`
- For versioned evaluations: `cursor-evaluation-2026-02.md`
- For company products with multiple tools: `github-copilot-evaluation.md`

---

## Technical Context for Evaluations

When assessing integration capability and suitability, evaluate against this **target stack**:

### Languages
- **TypeScript** (primary frontend/backend)
- **Rust** (systems programming, performance-critical components)
- Python (data processing, ML workflows)
- Go (microservices, CLI tools)

### Database
- **Supabase** (preferred PostgreSQL-based backend)
- **PostgreSQL** (direct database access)
- Redis (caching, session storage)

### Development Practices
- Git workflows (feature branches, pull requests)
- Issue tracking integration (GitHub Issues, Linear)
- Pull request processes (code review, CI/CD gates)
- Trunk-based development or GitFlow

### Scale Expectations
- **Enterprise-grade applications**, not just prototypes
- Monorepo support (multiple packages/services)
- Codebase size: 10k-100k+ lines of code
- Team size: 5-50+ developers

### Integration Points to Evaluate
- Authentication providers (Supabase Auth, Auth0, Clerk)
- API clients (REST, GraphQL, gRPC)
- Testing frameworks (Jest, Vitest, Playwright, pytest)
- Build tools (Vite, esbuild, Cargo, Go build)
- Deployment targets (Vercel, Netlify, AWS, Railway)

---

## Tone and Style Guidelines

### Audience Assumptions
- **Technical reader** with software development expertise
- Familiar with Git, CI/CD, modern web frameworks
- Makes architecture and tooling decisions for teams
- Values objective analysis over marketing claims

### Writing Style

**Technical and Precise**:
- Use specific version numbers, file counts, context window sizes
- Avoid vague terms like "good" or "fast" without quantification
- Specify exact limitations (e.g., "10k file limit" vs "large codebase support")

**Direct and Evidence-Based**:
- State capabilities clearly: "Supports X" not "Claims to support X"
- Avoid marketing language: "AI-powered" → "Uses GPT-4 for code generation"
- Back every claim with evidence

**Balanced**:
- Highlight both strengths AND limitations
- Don't oversell or undersell capabilities
- Acknowledge trade-offs explicitly

**Concrete Over Abstract**:
- Use specific examples:
  - ✅ "Generates TypeScript API client from OpenAPI spec"
  - ❌ "Helps with API integration"
- Show real capabilities:
  - ✅ "Refactored 50-file React component hierarchy in single prompt"
  - ❌ "Good at refactoring"

### Voice Examples

**Preferred**:
> Windsurf supports TypeScript 5.3+ with full type inference and automatic import resolution. Testing with a 15k-file Next.js monorepo showed consistent type checking across package boundaries. However, Rust support is limited to syntax highlighting without LSP integration (official docs v1.4, January 2026).

**Avoid**:
> Windsurf is amazing for TypeScript and works great with large projects! Rust support could be better but they're working on it.

---

## Complete Evaluation Template

Use this as a starting point for new evaluations:

```markdown
# [Product Name] Evaluation

**Evaluation Date**: YYYY-MM-DD  
**Product Version**: [version]  
**Evaluator**: [name]  
**Metrics Version**: evaluation-metrics.md v2.0  
**Template Version**: evaluation-template.md v2.0  
**Decision Criteria**: decision-criteria.md v2.0

## Executive Summary

[2-3 sentences: value proposition, deployment model, target audience]

---

## 1. Deployment Model

### Capability Assessment
[Narrative assessment]

**Evidence**: [Citations]

**Limitations**: [Constraints]

### Decision Questions for Deployment Model

- **🟢 NICE-TO-HAVE | 1.1a: [Question]**
  Answer: [Response]
  Evidence: [Citation]
  Notes: [Context]

[Repeat for all 7 questions in this metric: 1.1a, 1.1b, 1.2, 1.3, 1.4a, 1.4b, 1.5]

## 2. Package Management

### Capability Assessment
[Narrative assessment]

**Evidence**: [Citations]

**Limitations**: [Constraints]

### Decision Questions for Package Management

[5 questions: 2.1-2.5]

[Repeat structure for remaining 18 metrics: 3-20, plus new Metric 21]

---

## Key Differentiators

**Unique Strengths**:
- [Bullet points]

**Critical Limitations**:
- [Bullet points]

**Best Suited For**: [Specific use cases]

**Not Recommended For**: [Specific scenarios]

---

## Decision Scorecard

### Critical Requirements (MUST-HAVE)
[Table showing 4 MUST-HAVE questions and status]

### Scoring Summary
- **MUST-HAVE Score**: X/40
- **SHOULD-HAVE Score**: Y/45
- **NICE-TO-HAVE Score**: Z/15
- **TOTAL SCORE**: (X+Y+Z)/100

### Assessment
[Summary of results]

---

## Export Metadata

**File Path**: `/evaluations/raw-threads/[product-name]-evaluation.md`  
**Evaluation Date**: YYYY-MM-DD  
**Evaluator**: [Name]  
**Metrics Version**: evaluation-metrics.md v2.0  
**Template Version**: evaluation-template.md v2.0  
**Decision Criteria**: decision-criteria.md v2.0

**Status**: Ready for synthesis via GitHub Actions

**Questions Answered**: 103/103
**Metrics Covered**: 21/21
**Critical Requirements**: X/4 MUST-HAVE passed
```

---

## Quality Checklist

Before submitting an evaluation, verify:

- [ ] Executive summary is 2-3 sentences
- [ ] All 21 metrics from evaluation-metrics.md are addressed
- [ ] All 103 embedded decision questions are answered (across 21 metrics)
- [ ] Each metric section includes: capability assessment, evidence, limitations
- [ ] Each metric section includes: decision questions subsection with all embedded questions
- [ ] All claims have citations with evidence priority (P1/P2/P3)
- [ ] Version numbers and dates are included for all references
- [ ] Decision Scorecard section is complete with scoring summary
- [ ] Key Differentiators section includes strengths, limitations, and recommendations
- [ ] Markdown formatting follows template standards
- [ ] Technical terms use code formatting
- [ ] Question IDs (e.g., 1.1a, 5.3) are used consistently
- [ ] Export metadata section is complete
- [ ] File naming follows convention: `[product-name]-evaluation.md`
- [ ] Tone is technical, direct, balanced, and concrete
- [ ] No marketing language or unsupported claims
- [ ] Beta/experimental features are clearly marked
- [ ] All decision question answers use correct answer formats from decision-criteria.md

---

## Change Log

### v2.0 (2026-02-04)
- **Major Enhancement**: Added embedded decision question sections to all metric templates
- Integrated all 103 questions from decision-criteria.md v2.0
- Added Decision Scorecard summary section
- Updated template to show decision question sub-section structure
- Added Quality Checklist items for decision questions
- Updated Export Metadata to include decision-criteria version and question counts
- Clarified answer format requirements for each question type

### v1.0 (2026-02-03)
- Initial release
- Comprehensive template structure defined
- Evidence prioritization framework (P1/P2/P3)
- Complete formatting and citation requirements
- Quality checklist for validation

---

## Related Documents

- [evaluation-metrics.md](./evaluation-metrics.md) - Defines the 21 metrics + 103 embedded questions
- [decision-criteria.md](./decision-criteria.md) - Full question definitions, priorities, and scoring
- [/evaluations/raw-threads/](./raw-threads/) - Directory for completed evaluations

---

## Usage Notes

- Reference this template version in each evaluation report for traceability
- When template evolves, create versioned copies in `/evaluations/archive/` before updating
- GitHub Actions synthesis script validates compliance with this template structure
- Evaluators MUST answer all 103 decision questions to ensure comparability
- Use decision-criteria.md v2.0 as companion reference during evaluation
- For questions or template improvements, open an issue in the repository
