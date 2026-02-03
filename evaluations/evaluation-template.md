# AI Development Tools Evaluation Template

**Version**: 1.0  
**Date Created**: 2026-02-03  
**Last Updated**: 2026-02-03  
**References**: evaluation-metrics.md v1.0  
**Status**: Active

## Purpose

This template defines the structure, formatting, and evidence requirements for all AI development tool evaluations. Use in conjunction with `evaluation-metrics.md` which defines the 20 metrics to assess.

## Report Structure

### Executive Summary

Start each evaluation with **2-3 sentences** covering:
- Product's primary value proposition
- Core deployment model (cloud/local/hybrid)
- Primary target audience or use case

**Example**:
> Cursor is a VS Code fork that integrates AI code generation directly into the IDE experience. It operates as a local desktop application with cloud-based AI model access, targeting professional developers working on enterprise-scale codebases. The tool emphasizes multi-file context awareness and existing workflow integration over standalone web-based development.

---

### Metric Sections

Create a dedicated section for each of the **20 metrics** defined in `evaluation-metrics.md` using this structure:

**Section Header**: Use metric name exactly as defined in evaluation-metrics.md (use `##` heading level)

**Content**: 2-4 sentences covering:
1. **Current capability assessment** - What it does and does not do
2. **Evidence with citations** - Official documentation, reviews, or verified sources
3. **Limitations or constraints** - Discovered restrictions or caveats

**Example**:

```markdown
## 5. Git Integration

[Product Name] provides native Git integration through its VS Code-based IDE. Users can commit, push, pull, and create branches directly from the UI without command-line interaction. GitHub pull request workflows are fully supported with inline code review capabilities. However, advanced Git operations like interactive rebase or cherry-picking require dropping to the integrated terminal.

**Evidence**: Official documentation v2.3 (January 2026) confirms UI-based Git operations. Community reports indicate terminal access for advanced Git features (P2 evidence from verified user reports December 2025).

**Limitations**: No GitLab or Bitbucket native integration; GitHub-focused workflows only.
```

---

### Key Differentiators

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

## Formatting Requirements

### Markdown Standards

- Use `##` (h2) for metric section headers
- Use `###` (h3) for subsections within metrics if needed
- Use bullet points (`-` or `*`) for lists of features and capabilities
- Use comparison tables **only** when directly comparing multiple specific values
- Keep sections concise: **2-4 sentences per metric** unless complexity requires more
- Use **bold** for emphasis on key terms or capabilities
- Use `code formatting` for technical terms, file paths, commands

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

Use tables for structured comparisons only:

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
**Metrics Version**: evaluation-metrics.md v1.0  
**Template Version**: evaluation-template.md v1.0  

**Status**: Ready for synthesis via GitHub Actions
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
- Specify exact limitations ("10k file limit" vs "large codebase support")

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
**Metrics Version**: evaluation-metrics.md v1.0  
**Template Version**: evaluation-template.md v1.0

## Executive Summary

[2-3 sentences: value proposition, deployment model, target audience]

---

## 1. Deployment Model

[Assessment + Evidence + Limitations]

## 2. Package Management

[Assessment + Evidence + Limitations]

## 3. Code Ownership

[Assessment + Evidence + Limitations]

## 4. Framework Support

[Assessment + Evidence + Limitations]

## 5. Git Integration

[Assessment + Evidence + Limitations]

## 6. Multi-file Context Awareness

[Assessment + Evidence + Limitations]

## 7. Backend Capabilities

[Assessment + Evidence + Limitations]

## 8. Collaboration Features

[Assessment + Evidence + Limitations]

## 9. Deployment Automation

[Assessment + Evidence + Limitations]

## 10. Local Development Support

[Assessment + Evidence + Limitations]

## 11. AI Model Selection

[Assessment + Evidence + Limitations]

## 12. IDE Type

[Assessment + Evidence + Limitations]

## 13. Codebase Scale Limits

[Assessment + Evidence + Limitations]

## 14. API/Service Integration

[Assessment + Evidence + Limitations]

## 15. Code Generation Scope

[Assessment + Evidence + Limitations]

## 16. Extension Ecosystem

[Assessment + Evidence + Limitations]

## 17. Pricing Model

[Assessment + Evidence + Limitations]

## 18. Mobile Support

[Assessment + Evidence + Limitations]

## 19. Performance Optimization

[Assessment + Evidence + Limitations]

## 20. Security & Compliance

[Assessment + Evidence + Limitations]

---

## Key Differentiators

**Unique Strengths**:
- [Bullet points]

**Critical Limitations**:
- [Bullet points]

**Best Suited For**: [Specific use cases]

**Not Recommended For**: [Specific scenarios]

---

## Export Metadata

**File Path**: `/evaluations/raw-threads/[product-name]-evaluation.md`  
**Evaluation Date**: YYYY-MM-DD  
**Evaluator**: [Name]  
**Metrics Version**: evaluation-metrics.md v1.0  
**Template Version**: evaluation-template.md v1.0  

**Status**: Ready for synthesis via GitHub Actions
```

---

## Quality Checklist

Before submitting an evaluation, verify:

- [ ] All 20 metrics from evaluation-metrics.md are addressed
- [ ] Executive summary is 2-3 sentences
- [ ] Each metric section includes assessment, evidence, and limitations
- [ ] All claims have citations with evidence priority (P1/P2/P3)
- [ ] Version numbers and dates are included for all references
- [ ] Key Differentiators section includes strengths, limitations, and recommendations
- [ ] Markdown formatting follows template standards
- [ ] Technical terms use code formatting
- [ ] Export metadata section is complete
- [ ] File naming follows convention: `[product-name]-evaluation.md`
- [ ] Tone is technical, direct, balanced, and concrete
- [ ] No marketing language or unsupported claims
- [ ] Beta/experimental features are clearly marked

---

## Change Log

### v1.0 (2026-02-03)
- Initial release
- Comprehensive template structure defined
- Evidence prioritization framework (P1/P2/P3)
- Complete formatting and citation requirements
- Quality checklist for validation

---

## Related Documents

- [evaluation-metrics.md](./evaluation-metrics.md) - Defines the 20 metrics to evaluate
- [/evaluations/raw-threads/](./raw-threads/) - Directory for completed evaluations

---

## Usage Notes

- Reference this template version in each evaluation report for traceability
- When template evolves, create versioned copies in `/evaluations/archive/` before updating
- GitHub Actions synthesis script validates compliance with this template structure
- For questions or template improvements, open an issue in the repository
