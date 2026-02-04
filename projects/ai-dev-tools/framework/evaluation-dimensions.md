# AI Development Tools Evaluation Metrics

**Version**: 2.0  
**Date Created**: 2026-02-03  
**Last Updated**: 2026-02-04  
**Status**: Active  
**Related**: decision-criteria.md v2.0 (question definitions), evaluation-template.md v2.0 (answering structure)

## Purpose

This document defines the standardized evaluation criteria for assessing AI development platforms and code generation tools. These metrics enable consistent, structured analysis of tool capabilities, limitations, and suitability for enterprise software development.

This framework is designed to evaluate both cloud-hosted platforms (e.g., Lovable, Bolt.new) and IDE-integrated assistants (e.g., Cursor, Windsurf) against a common set of technical and operational criteria.

**Version 2.0 Enhancement**: Each metric now includes embedded decision questions from decision-criteria.md v2.0, enabling evaluations to simultaneously provide:
- ✅ Narrative technical assessment (qualitative)
- ✅ Structured decision question answers (quantitative)
- ✅ Automatic scoring capability
- ✅ Direct comparison across tools

## Evaluation Principles

- **Evidence-Based**: Every claim must be supported by official documentation, verified user reports, or direct observation
- **Prioritization**: P1 = official documentation, P2 = recent verified reports (6 months), P3 = reasonable inferences clearly marked
- **Objectivity**: Highlight both strengths and limitations; avoid marketing language
- **Completeness**: Evaluate all 21 metrics + 103 embedded questions even if some are not applicable (mark as N/A with reasoning)
- **Audience**: Evaluations assume technical reader with software development expertise
- **Comparability**: All evaluations answer the same 103 questions in the same format, enabling side-by-side comparison

## Evaluation Metrics (21 Total)

### Metric Overview

These 21 metrics organize the 103 decision questions into coherent capability areas:

| # | Metric | Questions | Total |
|---|--------|-----------|-------|
| 1 | Deployment Model | 1.1a, 1.1b, 1.2, 1.3, 1.4a, 1.4b, 1.5 | 7 |
| 2 | Package Management | 2.1-2.5 | 5 |
| 3 | Code Ownership & Portability | 3.1-3.5 | 5 |
| 4 | Framework Support | 4.1-4.7 | 7 |
| 5 | Git Integration | 5.1-5.5 | 5 |
| 6 | Multi-file Context Awareness | 6.1-6.5 | 5 |
| 7 | Backend Capabilities | 7.1-7.5 | 5 |
| 8 | Collaboration Features | 8.1a, 8.1b, 8.2-8.5 | 6 |
| 9 | Deployment Automation | 9.1-9.5 | 5 |
| 10 | Local Development Support | 10.1-10.5 | 5 |
| 11 | AI Model Selection | 11.1-11.5 | 5 |
| 12 | IDE Type | 12.1-12.5 | 5 |
| 13 | Codebase Scale Limits | 13.1-13.5 | 5 |
| 14 | API/Service Integration | 14.1-14.5 | 5 |
| 15 | Code Generation Scope | 15.1-15.5 | 5 |
| 16 | Extension Ecosystem | 16.1-16.5 | 5 |
| 17 | Pricing Model | 17.1-17.5 | 5 |
| 18 | Mobile Support | 18.1-18.5 | 5 |
| 19 | Performance Optimization | 19.1-19.5 | 5 |
| 20 | Security & Compliance | 20.2-20.5 | 4 |
| 21 | Team & Adoption *(NEW)* | 21.1-21.3 | 3 |
| **TOTAL** | **21 Metrics** | **103 Questions** | **103** |

---

## Metric Definitions with Embedded Questions

### 1. Deployment Model
**Definition**: Whether the tool is cloud-hosted (browser-based), self-hosted (on-premises), or local IDE (desktop application).

**Evaluation Guidance**: Identify primary deployment method. Note if multiple deployment options exist. Consider whether user data stays local or is processed on remote servers. Answer all 7 embedded questions (1.1a through 1.5) per evaluation-template.md structure.

**Embedded Questions**:
- 1.1a: Can dev environment be fully self-hosted?
- 1.1b: Can applications deploy outside platform?
- 1.2: Air-gapped environment support?
- 1.3: Run as local desktop app?
- 1.4a: Where does IDE run?
- 1.4b: Where are AI features processed?
- 1.5: Web-based version available?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 2. Package Management
**Definition**: Support for third-party package managers (npm, pip, cargo, etc.) and ability to install arbitrary dependencies.

**Evaluation Guidance**: Can the tool create projects that use npm packages? Are there restrictions on which packages can be installed? Can users work with monorepos with complex dependency trees? Answer all 5 embedded questions (2.1-2.5).

**Embedded Questions**:
- 2.1: npm package installation support?
- 2.2: cargo (Rust) package support?
- 2.3: Monorepo dependency handling?
- 2.4: pip (Python) package support?
- 2.5: Package restrictions?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 3. Code Ownership & Portability
**Definition**: Whether you can export source code, own the codebase fully, or are locked into the platform. **Note**: Renamed from "Code Ownership" to emphasize portability.

**Evaluation Guidance**: Can code be downloaded as a standard project structure? Are there platform lock-in mechanisms? What format is exported code in? Can you immediately run exported code in a local environment without platform dependencies? Answer all 5 embedded questions (3.1-3.5).

**Embedded Questions**:
- 3.1: Export 100% of code?
- 3.2: No proprietary runtime dependencies?
- 3.3: Standard project format?
- 3.4: Run with zero modifications?
- 3.5: Export project history/version control?

**CRITICAL METRIC**: 3 of 4 MUST-HAVE questions are in this category (3.1, 3.2 are MUST-HAVE).

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 4. Framework Support
**Definition**: Specific frameworks and languages supported (React, Vue, Angular, Python, Go, Rust, TypeScript, etc.).

**Evaluation Guidance**: List explicitly supported frameworks. Note limitations (e.g., only React, not Vue). For multi-language support, specify which languages have first-class vs. limited support. Answer all 7 embedded questions (4.1-4.7).

**Embedded Questions**:
- 4.1: TypeScript support?
- 4.2: Rust with LSP integration?
- 4.3: React/Next.js support?
- 4.4: Python support?
- 4.5: Go support?
- 4.6: Vue.js support?
- 4.7: Angular support?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 5. Git Integration
**Definition**: Level of version control support—native Git, GitHub integration, or proprietary versioning.

**Evaluation Guidance**: Can users commit to GitHub directly? Is there a Git UI or must users work via command line? Are there branching/merging workflows? Can teams work via traditional pull request processes? Answer all 5 embedded questions (5.1-5.5).

**Embedded Questions**:
- 5.1: Native Git integration?
- 5.2: Push to GitHub/GitLab?
- 5.3: Pull request workflows?
- 5.4: Visual Git UI?
- 5.5: Branch management?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 6. Multi-file Context Awareness
**Definition**: Ability to understand and maintain consistency across multiple files in a codebase.

**Evaluation Guidance**: When generating code, does the tool understand relationships between files? Can it refactor across a project? Does it consider existing code patterns when generating new files? Answer all 5 embedded questions (6.1-6.5).

**Embedded Questions**:
- 6.1: Understand file relationships?
- 6.2: Refactor across multiple files?
- 6.3: Maximum AI context size?
- 6.4: Maintain consistency in new files?
- 6.5: Analyze entire codebase for suggestions?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 7. Backend Capabilities
**Definition**: Whether the tool generates only frontend/UI or supports full-stack development including databases and APIs.

**Evaluation Guidance**: Can it scaffold backend code (Node.js, Python, Go, Rust)? Can it create database schemas? Does it support API generation? For full-stack: does the frontend and backend integration work seamlessly? Answer all 5 embedded questions (7.1-7.5).

**Embedded Questions**:
- 7.1: Backend language support?
- 7.2: Database schema creation?
- 7.3: API generation (REST/GraphQL)?
- 7.4: Full-stack scaffolding?
- 7.5: Seamless frontend/backend integration?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 8. Collaboration Features
**Definition**: Real-time multiplayer editing, team permissions, live cursors, or traditional Git-based workflows.

**Evaluation Guidance**: Can multiple developers work simultaneously? Is collaboration real-time or Git-based? Are there role-based permissions? Can teams review changes before merging? Answer all 6 embedded questions (8.1a, 8.1b, 8.2-8.5).

**Embedded Questions**:
- 8.1a: Real-time multiplayer collaboration?
- 8.1b: Git-based collaboration workflows?
- 8.2: Role-based permissions?
- 8.3: Multiple simultaneous developers?
- 8.4: Code review workflows?
- 8.5: Live cursors for real-time editing?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 9. Deployment Automation
**Definition**: Built-in deployment to production (CDN, cloud providers, app stores) vs. manual deployment required.

**Evaluation Guidance**: Can the tool automatically deploy to Vercel, Netlify, AWS, or other platforms? Does it support CI/CD pipeline integration? Can it handle database migrations on deploy? Answer all 5 embedded questions (9.1-9.5).

**Embedded Questions**:
- 9.1: Built-in deployment automation?
- 9.2: Which deployment platforms?
- 9.3: CI/CD pipeline integration?
- 9.4: Database migrations on deploy?
- 9.5: Customizable deployment config?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 10. Local Development Support
**Definition**: Ability to work offline, run locally, or exclusively cloud-dependent. **CRITICAL**: Includes MUST-HAVE question 10.1.

**Evaluation Guidance**: Can developers run projects locally on their machine? Is local debugging supported? Can work continue without internet connectivity? Are there performance differences between local and cloud execution? Answer all 5 embedded questions (10.1-10.5).

**Embedded Questions**:
- 10.1: Standard dev commands work locally? *(MUST-HAVE)*
- 10.2: Offline support?
- 10.3: Local debugging?
- 10.4: Performance: local vs cloud?
- 10.5: Use own dev tools alongside?

**CRITICAL METRIC**: 10.1 is a MUST-HAVE question (one of only 4).

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 11. AI Model Selection
**Definition**: Single AI model vs. multi-model support (OpenAI, Anthropic, Google, etc.).

**Evaluation Guidance**: Which AI models power code generation? Can users switch models? Can they use their own API keys? Is model selection transparent to the user? Answer all 5 embedded questions (11.1-11.5).

**Embedded Questions**:
- 11.1: Which AI models supported?
- 11.2: Switch between models?
- 11.3: Bring your own API keys (BYOK)?
- 11.4: Transparent model selection?
- 11.5: Local/open-source models?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 12. IDE Type
**Definition**: Standalone web IDE, VS Code fork/extension, or command-line interface.

**Evaluation Guidance**: What is the primary interface? For web IDEs: does it have VS Code-like features? For VS Code forks: how diverged is it from base VS Code? For CLI tools: how ergonomic is the interface? Answer all 5 embedded questions (12.1-12.5).

**Embedded Questions**:
- 12.1: Primary interface type?
- 12.2: Based on VS Code?
- 12.3: Terminal access?
- 12.4: IDE customization?
- 12.5: Keyboard shortcuts support?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 13. Codebase Scale Limits
**Definition**: Resource constraints for small prototypes vs. enterprise-scale repositories.

**Evaluation Guidance**: How large can a codebase be before performance degrades? Are there file count limits? Context window constraints? How does it handle large monorepos? Answer all 5 embedded questions (13.1-13.5).

**Embedded Questions**:
- 13.1: Maximum file count indexable?
- 13.2: AI context window size?
- 13.3: Proven on enterprise-scale codebases?
- 13.4: Large monorepo support?
- 13.5: Performance degradation thresholds?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 14. API/Service Integration
**Definition**: Ease of integrating third-party APIs, databases (Supabase, PostgreSQL), and external services.

**Evaluation Guidance**: Can it scaffold code for API calls? Does it have templates for common integrations (auth providers, payment processors, databases)? Can it generate type-safe API clients? Answer all 5 embedded questions (14.1-14.5).

**Embedded Questions**:
- 14.1: Supabase integration scaffolding?
- 14.2: Type-safe API client generation?
- 14.3: Auth provider templates?
- 14.4: Payment processor integration?
- 14.5: GraphQL code generation?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 15. Code Generation Scope
**Definition**: UI components only vs. complete application scaffolding vs. inline code completion.

**Evaluation Guidance**: What can it generate? Full apps from scratch? Only UI components? Inline suggestions within existing code? Can it generate entire features or just snippets? Answer all 5 embedded questions (15.1-15.5).

**Embedded Questions**:
- 15.1: Generate full apps from scratch?
- 15.2: Generate complete features/modules?
- 15.3: Inline code completion?
- 15.4: UI components only?
- 15.5: Generate test files?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 16. Extension Ecosystem
**Definition**: Compatibility with existing IDE extensions (VS Code marketplace, etc.).

**Evaluation Guidance**: For IDE-integrated tools: do existing VS Code extensions work? Can you install custom extensions? For web IDEs: does it have a plugin system? Answer all 5 embedded questions (16.1-16.5).

**Embedded Questions**:
- 16.1: VS Code extension support?
- 16.2: % of VS Code marketplace works?
- 16.3: Custom extension installation?
- 16.4: Own plugin system?
- 16.5: Popular extensions supported (ESLint, Prettier)?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 17. Pricing Model
**Definition**: Free tier availability, pay-per-use, subscription tiers, or enterprise licensing.

**Evaluation Guidance**: What are all pricing tiers? Are there free/hobby tiers? Is pricing based on usage, time, or seat count? What features require paid plans? Answer all 5 embedded questions (17.1-17.5).

**Embedded Questions**:
- 17.1: Free tier available?
- 17.2: Monthly cost per developer?
- 17.3: Enterprise licensing?
- 17.4: Usage measurement method?
- 17.5: Usage limits on paid tiers?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 18. Mobile Support
**Definition**: Native mobile app generation (iOS/Android) vs. responsive web only.

**Evaluation Guidance**: Can it generate native mobile apps? React Native support? Can it scaffold mobile-specific code? Or is it web-only? Answer all 5 embedded questions (18.1-18.5).

**Embedded Questions**:
- 18.1: Native mobile app generation?
- 18.2: React Native support?
- 18.3: Responsive web apps?
- 18.4: Flutter support?
- 18.5: Mobile-specific code scaffolding?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 19. Performance Optimization
**Definition**: Automatic code optimization, bundle analysis, and performance monitoring capabilities.

**Evaluation Guidance**: Does the tool provide optimization suggestions? Can it analyze bundle sizes? Does it implement best practices for performance (lazy loading, code splitting)? Does it measure performance metrics? Answer all 5 embedded questions (19.1-19.5).

**Embedded Questions**:
- 19.1: Optimization suggestions?
- 19.2: Bundle size analysis?
- 19.3: Lazy loading auto-implementation?
- 19.4: Code splitting support?
- 19.5: Performance metric measurement?

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 20. Security & Compliance
**Definition**: Built-in security scanning, compliance features, authentication handling.

**Evaluation Guidance**: Does it scan for security vulnerabilities? Does it handle authentication (auth providers, JWT, etc.)? Does it support compliance requirements (GDPR, SOC2)? Can it work in air-gapped environments? Answer all 4 embedded questions (20.2-20.5).

**Embedded Questions**:
- 20.2: Security vulnerability scanning?
- 20.3: Authentication scaffolding?
- 20.4: GDPR compliance features?
- 20.5: SOC2/ISO certification?

**Note**: Question 20.1 (air-gapped) moved to Metric 1 as question 1.2 (Deployment Model) for better categorization.

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

### 21. Team & Adoption *(NEW in v2.0)*
**Definition**: Team size support, learning curve, and vendor stability.

**Evaluation Guidance**: What team sizes does the tool support well? What is the learning curve for developers? How stable and well-funded is the vendor? Answer all 3 embedded questions (21.1-21.3).

**Embedded Questions**:
- 21.1: Team sizes supported well?
- 21.2: Learning curve for VS Code-familiar devs?
- 21.3: Vendor funding/stability status?

**NEW METRIC**: Added to capture organizational and adoption factors not covered by other metrics.

**Reference**: See decision-criteria.md v2.0 for full question text, priority levels, and answer formats.

---

## Critical Questions (MUST-HAVE)

Only **4 questions** are MUST-HAVE (deal-breaker if answered unfavorably):

| Question | Category | Requirement | Why Critical |
|----------|----------|-------------|-------------|
| **1.1b** | Deployment Model | Applications deployable outside platform | Avoid deployment lock-in |
| **3.1** | Code Ownership | Export 100% of code | Avoid vendor lock-in |
| **3.2** | Code Ownership | No proprietary runtime dependencies | Ensure code portability |
| **10.1** | Local Development | Standard dev commands work locally | Avoid IDE lock-in |

**Rule**: Failing any MUST-HAVE question = SERIOUS CONCERN (may eliminate tool from consideration)

---

## Question Priority Distribution

**Across all 103 questions**:
- 🔴 **MUST-HAVE**: 4 questions (3.9%)
- 🟡 **SHOULD-HAVE**: 45 questions (43.7%)
- 🟢 **NICE-TO-HAVE**: 54 questions (52.4%)

**Scoring weight**:
- MUST-HAVE: 40% (10 points each)
- SHOULD-HAVE: 45% (1 point each)
- NICE-TO-HAVE: 15% (0.28 points each)
- **Total**: 100 points maximum

---

## Scoring Guidance (Optional)

If you choose to add quantitative scoring to evaluations, use this framework:

**Capability Score** (0-5 for each metric):
- 5 = Full native support, no limitations
- 4 = Full support with minor limitations
- 3 = Partial support, significant workarounds required
- 2 = Limited support, mostly workarounds
- 1 = Minimal or experimental support
- 0 = Not supported
- N/A = Not applicable for this tool category

**Evidence Quality** (for each assessment):
- P1 = Explicit vendor documentation
- P2 = Recent verified user reports (within 6 months)
- P3 = Reasonable inference marked as such

**Decision Question Scoring**:
- "Yes" / "Both" / "Full" = Favorable (1 point toward favorable count)
- "Limited" / "Partial" / "Experimental" = Partial (0.5 points)
- "No" / "None" = Unfavorable (0 points)
- Use per-question answer format from decision-criteria.md for consistency

---

## Key Changes from v1.0 to v2.0

### New Metric (1 added)
- **Metric 21: Team & Adoption** - Captures team size support, learning curve, and vendor stability

### Enhanced Integration
- All 103 decision questions now embedded within 21 metrics
- Provides unified evaluation framework (narrative + structured questions)
- Enables automatic scoring and comparison
- Evaluation template shows how to answer embedded questions

### Reorganization
- Question 20.1 (air-gapped) merged into Metric 1, question 1.2 (for better categorization)
- Framework support metrics clarified (first-class vs. limited support)

### Clarity Improvements
- Split ambiguous questions (1.1 → 1.1a/1.1b, 1.4 → 1.4a/1.4b, 8.1 → 8.1a/8.1b)
- Added priority labels to all questions
- Clarified answer formats for unambiguous scoring
- Added explicit MUST-HAVE question summary

---

## Change Log

### v2.0.1 (2026-02-04)
- Fixed: Updated all references from "20 metrics" to "21 metrics" (Metric 21 Team & Adoption was added)
- Clarified that framework now has 21 total metrics (not 20)

### v2.0 (2026-02-04)
- **Major Enhancement**: Integrated all 103 decision questions as embedded sub-metrics within 21 evaluation metrics
- Added new Metric 21 (Team & Adoption) for organizational factors
- Updated metric guidance to reference embedded questions
- Added critical questions summary table
- Added question priority distribution and scoring guidance
- Added comprehensive change log vs v1.0
- Clarified relationship between metrics, questions, and evaluation template

### v1.0 (2026-02-03)
- Initial release
- 20 evaluation metrics defined
- Targeting evaluation of cloud-hosted and IDE-integrated AI development tools

---

## Usage Notes

- Use this metrics file as the definitive reference for all product evaluations
- Reference decision-criteria.md v2.0 for full question text, priority levels, and answer formats
- Reference evaluation-template.md v2.0 for how to answer embedded questions in evaluations
- Store evaluation reports in `/evaluations/raw-threads/` with naming: `[product-name]-evaluation.md`
- Each evaluation MUST answer all 103 questions to ensure comparability
- The synthesis script will validate that each evaluation covers all 21 metrics + 103 questions
- When metrics evolve, create versioned copies in `/evaluations/archive/` before updating this file
- Reference this file's version in each evaluation report for traceability

---

## Related Documents

- [decision-criteria.md](./decision-criteria.md) - Complete question definitions, priorities, answer formats, and scoring
- [evaluation-template.md](./evaluation-template.md) - How to structure evaluations and answer embedded questions
- [/evaluations/raw-threads/](./raw-threads/) - Directory for completed evaluations

---

## For Questions or Improvements

Open an issue in the repository to discuss:
- Additional metrics or questions needed
- Clarifications on existing metrics
- Feedback on question clarity or priority levels
- Suggestions for evaluation improvements
