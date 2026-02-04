# AI Development Tools Decision Criteria v2.0

**Version**: 2.0.1  
**Date Created**: 2026-02-04  
**Last Updated**: 2026-02-04  
**Supersedes**: decision-criteria.md v1.0  
**Status**: Active

## Change Summary from v1.0

### Major Changes
- Split ambiguous questions for clarity (1.1 → 1.1a/1.1b, 1.4 → 1.4a/1.4b, 8.1 → 8.1a/8.1b)
- Merged duplicate air-gapped questions (1.2 and 20.1 → 1.2)
- Adjusted 8 CRITICAL questions based on user priorities
- Refined answer formats for unambiguous scoring
- Added 3 new questions: Team Size, Learning Curve, Vendor Stability
- Updated priorities based on actual use case requirements
- Enhanced priority labels with text (v2.0.1)

### Priority Realignment
- **Air-gapped**: MUST-HAVE → Nice-to-have
- **Self-hosted dev environment**: MUST-HAVE → Nice-to-have  
- **Rust LSP**: MUST-HAVE → Nice-to-have
- **TypeScript**: MUST-HAVE → SHOULD-HAVE
- **Application deployment flexibility**: Elevated to MUST-HAVE

### Result
- **v1.0**: 8 MUST-HAVE questions (eliminated all tools)
- **v2.0**: 4 MUST-HAVE questions (focused on code portability)

---

## Purpose

This framework enables systematic, unambiguous comparison of AI development tools based on refined, user-validated criteria. Use this to:
- Evaluate tools against clear, specific questions
- Make data-driven tool selection decisions
- Avoid vendor lock-in through portability requirements
- Compare tools side-by-side objectively

---

## Question Priority Levels

- 🔴 **MUST-HAVE**: Deal-breaker if answered unfavorably (critical requirement)
- 🟡 **SHOULD-HAVE**: Heavily weighted in decision-making (important feature)
- 🟢 **NICE-TO-HAVE**: Important but not decisive (bonus feature)

---

## Decision Questions by Category

### 1. Deployment Model

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 **NICE-TO-HAVE** | 1.1a | Can the **development environment** (IDE + AI) be fully self-hosted on your infrastructure? | Yes / Partial / No |
| 🔴 **MUST-HAVE** | 1.1b | Can **applications you build** be deployed to infrastructure outside the product's own platform? | Yes / Requires platform / No |
| 🟢 **NICE-TO-HAVE** | 1.2 | Can the tool operate in **completely air-gapped environments** (no internet access for development or AI features)? | Yes / Partial (internet for AI only) / No |
| 🟡 **SHOULD-HAVE** | 1.3 | Can it run as a local desktop application? | Yes / No |
| 🟡 **SHOULD-HAVE** | 1.4a | Where does the **IDE/editor** run? | Local (desktop) / Cloud (browser) / Both |
| 🟡 **SHOULD-HAVE** | 1.4b | Where are **AI features processed**? | Local / Cloud API / Self-hosted option / Hybrid |
| 🟢 **NICE-TO-HAVE** | 1.5 | Is there a web-based version available? | Yes / No |

### 2. Package Management

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 2.1 | Does it support npm package installation? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 2.2 | Does it support cargo (Rust) packages? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 2.3 | Can it handle monorepo dependency structures? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 2.4 | Does it support pip (Python) packages? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 2.5 | Are there restrictions on which packages can be used? | Yes (restrictions exist) / No (unrestricted) |

### 3. Code Ownership & Portability

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 **MUST-HAVE** | 3.1 | Can you export 100% of generated code? | Yes / No |
| 🔴 **MUST-HAVE** | 3.2 | Does exported code avoid **proprietary runtime dependencies** (runs with standard npm/cargo/pip, no vendor-specific SDK required)? | Yes / Requires vendor SDK / No |
| 🟡 **SHOULD-HAVE** | 3.3 | Is exported code in **standard project format** (package.json, Cargo.toml, standard directories)? | Yes / No |
| 🟡 **SHOULD-HAVE** | 3.4 | Can exported code **run with zero modifications** (npm start works immediately after export)? | Yes / Requires npm install only / Requires setup / No |
| 🟢 **NICE-TO-HAVE** | 3.5 | Can you export project history/version control? | Yes / No |

### 4. Framework Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 4.1 | Does it have first-class TypeScript support? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 4.2 | Does it support Rust with LSP integration (rust-analyzer)? | Yes / Syntax only / No |
| 🟡 **SHOULD-HAVE** | 4.3 | Does it support React/Next.js? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 4.4 | Does it support Python? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 4.5 | Does it support Go? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 4.6 | Does it support Vue.js? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 4.7 | Does it support Angular? | Yes / Limited / No |

### 5. Git Integration

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 5.1 | Does it have native Git integration? | Yes / CLI only / No |
| 🟡 **SHOULD-HAVE** | 5.2 | Can you push directly to GitHub/GitLab? | Both / GitHub only / No |
| 🟡 **SHOULD-HAVE** | 5.3 | Does it support pull request workflows? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 5.4 | Does it have a visual Git UI? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 5.5 | Can it handle branch management? | Yes / Limited / No |

### 6. Multi-file Context Awareness

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 6.1 | Can it understand relationships between files? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 6.2 | Can it refactor across multiple files? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 6.3 | What is the maximum **AI context size**? | Specify unit: tokens / files / LOC (e.g., "200K tokens" or "50 files") |
| 🟢 **NICE-TO-HAVE** | 6.4 | Does it maintain consistency when generating new files? | Yes / Sometimes / No |
| 🟢 **NICE-TO-HAVE** | 6.5 | Can it analyze entire codebase for suggestions? | Yes / Limited / No |

### 7. Backend Capabilities

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 7.1 | Which backend languages can it generate? | List: Node.js, Python, Go, Rust, Other |
| 🟡 **SHOULD-HAVE** | 7.2 | Can it create database schemas? | Yes / No |
| 🟡 **SHOULD-HAVE** | 7.3 | Does it support API generation (REST/GraphQL)? | Both / REST only / No |
| 🟢 **NICE-TO-HAVE** | 7.4 | Can it scaffold full-stack applications? | Yes / Frontend only / No |
| 🟢 **NICE-TO-HAVE** | 7.5 | Does frontend/backend integration work seamlessly? | Yes / Manual setup / No |

### 8. Collaboration Features

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 **NICE-TO-HAVE** | 8.1a | Does it support **real-time multiplayer** collaboration (simultaneous editing)? | Yes / No |
| 🟡 **SHOULD-HAVE** | 8.1b | Does it support **Git-based** collaboration workflows (branches, PRs, code review)? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 8.2 | Are there role-based permissions? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 8.3 | Can multiple developers work simultaneously? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 8.4 | Does it support code review workflows? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 8.5 | Are there live cursors for real-time editing? | Yes / No |

### 9. Deployment Automation

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 **NICE-TO-HAVE** | 9.1 | Does it have built-in deployment automation? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 9.2 | Which platforms does it deploy to? | List platforms |
| 🟢 **NICE-TO-HAVE** | 9.3 | Does it support CI/CD pipeline integration? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 9.4 | Can it handle database migrations on deploy? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 9.5 | Is deployment configuration customizable? | Yes / Limited / No |

### 10. Local Development Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 **MUST-HAVE** | 10.1 | Can exported projects **run using standard dev commands** (npm start, cargo run) in any IDE/terminal, without requiring the tool's IDE? | Yes / Requires tool IDE / No |
| 🟡 **SHOULD-HAVE** | 10.2 | Does it work offline? | Yes / Limited / No |
| 🟡 **SHOULD-HAVE** | 10.3 | Is local debugging supported? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 10.4 | Are there performance differences local vs cloud? | Same / Slower local / Faster local |
| 🟢 **NICE-TO-HAVE** | 10.5 | Can you use your own dev tools alongside it? | Yes / No |

### 11. AI Model Selection

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 11.1 | Which AI models does it support? | List models |
| 🟡 **SHOULD-HAVE** | 11.2 | Can you switch between models? | Yes / No |
| 🟡 **SHOULD-HAVE** | 11.3 | Can you **bring your own API keys (BYOK)** for AI providers (OpenAI, Anthropic, etc.)? | Yes / Enterprise only / No |
| 🟢 **NICE-TO-HAVE** | 11.4 | Is model selection transparent to users? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 11.5 | Does it support local/open-source models? | Yes / No |

### 12. IDE Type

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 12.1 | What is the primary interface? | Desktop IDE / Web IDE / VS Code Extension / CLI |
| 🟡 **SHOULD-HAVE** | 12.2 | Is it based on VS Code? | Yes (fork) / Yes (extension) / No |
| 🟢 **NICE-TO-HAVE** | 12.3 | Does it have terminal access? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 12.4 | Can you customize the IDE? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 12.5 | Does it support keyboard shortcuts? | Yes / Limited / No |

### 13. Codebase Scale Limits

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 13.1 | What is the maximum **total file count** the tool can index/navigate? | Number (e.g., "100,000 files") or "Unlimited" |
| 🟡 **SHOULD-HAVE** | 13.2 | What is the **AI context window** (how much code can AI consider at once)? | Specify unit and value (e.g., "200K tokens" or "50 files") |
| 🟡 **SHOULD-HAVE** | 13.3 | Has the tool been **proven on enterprise-scale codebases** (100K+ LOC)? | Yes (with evidence) / Likely / No |
| 🟢 **NICE-TO-HAVE** | 13.4 | Does it support large monorepos? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 13.5 | Are there performance degradation thresholds? | At X files/LOC / No known threshold |

### 14. API/Service Integration

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 14.1 | Can it scaffold Supabase integration? | Yes / Manual / No |
| 🟡 **SHOULD-HAVE** | 14.2 | Can it generate type-safe API clients? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 14.3 | Does it have templates for auth providers? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 14.4 | Can it integrate payment processors? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 14.5 | Does it support GraphQL code generation? | Yes / No |

### 15. Code Generation Scope

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 15.1 | Can it generate full applications from scratch? | Yes / No |
| 🟡 **SHOULD-HAVE** | 15.2 | Can it generate complete features/modules? | Yes / No |
| 🟡 **SHOULD-HAVE** | 15.3 | Does it provide inline code completion? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 15.4 | Can it generate only UI components? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 15.5 | Can it generate test files? | Yes / No |

### 16. Extension Ecosystem

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 16.1 | Does it support VS Code extensions? | Yes / Limited / No |
| 🟢 **NICE-TO-HAVE** | 16.2 | What percentage of VS Code marketplace works? | Percentage or "N/A" |
| 🟢 **NICE-TO-HAVE** | 16.3 | Can you install custom extensions? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 16.4 | Does it have its own plugin system? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 16.5 | Are popular extensions supported? (ESLint, Prettier) | Yes / Some / No |

### 17. Pricing Model

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 17.1 | Is there a free tier? | Yes / Trial only / No |
| 🟡 **SHOULD-HAVE** | 17.2 | What is the monthly cost per developer? | $ amount or range |
| 🟡 **SHOULD-HAVE** | 17.3 | Is there enterprise licensing? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 17.4 | How is usage measured? | Time / Tokens / Seats / Other |
| 🟢 **NICE-TO-HAVE** | 17.5 | Are there usage limits on paid tiers? | Yes (describe) / No |

### 18. Mobile Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 **NICE-TO-HAVE** | 18.1 | Can it generate native mobile apps? | iOS+Android / One platform / No |
| 🟢 **NICE-TO-HAVE** | 18.2 | Does it support React Native? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 18.3 | Can it generate responsive web apps? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 18.4 | Does it support Flutter? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 18.5 | Can it scaffold mobile-specific code? | Yes / No |

### 19. Performance Optimization

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 **NICE-TO-HAVE** | 19.1 | Does it provide optimization suggestions? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 19.2 | Can it analyze bundle sizes? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 19.3 | Does it implement lazy loading automatically? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 19.4 | Does it support code splitting? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 19.5 | Can it measure performance metrics? | Yes / No |

### 20. Security & Compliance

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 20.2 | Does it scan for security vulnerabilities? | Yes / No |
| 🟡 **SHOULD-HAVE** | 20.3 | Does it handle authentication scaffolding? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 20.4 | Does it support GDPR compliance features? | Yes / No |
| 🟢 **NICE-TO-HAVE** | 20.5 | Does it have SOC2/ISO certification? | Yes / No |

### 21. Team & Adoption (NEW)

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 **SHOULD-HAVE** | 21.1 | What team sizes does it support well? | Solo / Small (2-10) / Medium (10-50) / Enterprise (50+) |
| 🟢 **NICE-TO-HAVE** | 21.2 | What is the learning curve for developers familiar with VS Code? | Minimal (< 1 day) / Moderate (1-3 days) / Significant (1+ weeks) |
| 🟡 **SHOULD-HAVE** | 21.3 | What is the vendor's funding/stability status? | Public company / Well-funded (Series B+) / Early-stage / Open source |

---

## Critical Questions Summary (Must Pass)

| Question ID | Requirement | Why Critical |
|-------------|-------------|-------------|
| 1.1b | Applications deployable outside platform | Avoid deployment lock-in |
| 3.1 | Export 100% of code | Avoid vendor lock-in |
| 3.2 | No proprietary runtime dependencies | Ensure code portability |
| 10.1 | Run with standard commands outside tool | Avoid IDE lock-in |

**Rule**: Fail any MUST-HAVE question = SERIOUS CONCERN (may eliminate tool)

---

## Scoring System v2.0

### Question Count by Priority
- **MUST-HAVE (🔴)**: 4 questions
- **SHOULD-HAVE (🟡)**: 45 questions
- **NICE-TO-HAVE (🟢)**: 54 questions
- **Total**: 103 questions

### Scoring Formula

```
Must-Have Score = (passed / 4) × 40 points (max 40)
Should-Have Score = (favorable / 45) × 45 points (max 45)
Nice-to-Have Score = (favorable / 54) × 15 points (max 15)
Total = Must-Have + Should-Have + Nice-to-Have (max 100 points)
```

### Weights Rationale
- **MUST-HAVE**: 40% weight (10 points each) - Deal-breaker features
- **SHOULD-HAVE**: 45% weight (1 point each) - Core functionality
- **NICE-TO-HAVE**: 15% weight (0.28 points each) - Bonus features

---

## Decision Rules

### Phase 1: Critical Evaluation
1. Evaluate all 4 MUST-HAVE questions
2. Tools failing multiple MUST-HAVE questions raise serious concerns
3. Tools failing all MUST-HAVE questions should be eliminated
4. Document WHY failures matter for your use case

### Phase 2: Comprehensive Scoring
1. Score all remaining questions
2. Calculate total score (0-100 points)
3. Rank tools by score

### Phase 3: Qualitative Assessment
Consider:
- Score trends (which categories are strongest?)
- Cost per developer vs value
- Team familiarity and adoption friction
- Vendor stability and ecosystem
- Support quality and documentation

### Phase 4: Final Selection
Balance:
- Quantitative score (objective)
- Qualitative factors (subjective)
- Team consensus and preference
- Budget constraints
- Timeline requirements

---

## Comparison Table Template

Use this template to compare tools side-by-side:

```markdown
| Priority | ID | Question | Tool A | Tool B | Tool C |
|----------|----|----|--------|--------|--------|
| 🔴 **MUST-HAVE** | 1.1b | App deploy anywhere? | | | |
| 🔴 **MUST-HAVE** | 3.1 | Export 100%? | | | |
| 🔴 **MUST-HAVE** | 3.2 | No proprietary deps? | | | |
| 🔴 **MUST-HAVE** | 10.1 | Standard commands? | | | |
| **MUST-HAVE SCORE** || **/40** | X/40 | Y/40 | Z/40 |
| 🟡 **SHOULD-HAVE** | 4.1 | TypeScript? | | | |
| ... | ... | ... | ... | ... | ... |
| **SHOULD-HAVE SCORE** || **/45** | X/45 | Y/45 | Z/45 |
| **NICE-TO-HAVE SCORE** || **/15** | X/15 | Y/15 | Z/15 |
| **TOTAL SCORE** || **/100** | X/100 | Y/100 | Z/100 |
```

---

## Key Improvements from v1.0

### 1. Eliminated False Eliminations
- v1.0 had 8 MUST-HAVE questions that eliminated all tools
- v2.0 has 4 MUST-HAVE questions focused on actual deal-breakers (code portability)

### 2. Clarified Ambiguous Questions
- Split "self-hosted" into dev tool vs app deployment
- Split "code processing" into IDE location vs AI location
- Split "collaboration" into real-time vs Git-based
- Clarified "platform dependencies" with examples

### 3. Aligned Priorities with Use Case
- Downgraded air-gapped from MUST-HAVE to nice-to-have
- Downgraded self-hosted dev env from MUST-HAVE to nice-to-have
- Downgraded Rust from MUST-HAVE to nice-to-have
- Elevated app deployment flexibility to MUST-HAVE

### 4. Added Missing Dimensions
- Team size support
- Learning curve
- Vendor stability

### 5. Improved Scoring Transparency
- Clear point allocation (40/45/15)
- Quantitative + qualitative decision process
- Documented rationale for each priority level

### 6. Enhanced Scannability (v2.0.1)
- Added text labels to priority indicators
- MUST-HAVE / SHOULD-HAVE / NICE-TO-HAVE for immediate clarity
- Improved accessibility and comparison table readability

---

## Related Documents

- [evaluation-metrics.md](./evaluation-metrics.md) - 21 evaluation categories with embedded questions
- [evaluation-template.md](./evaluation-template.md) - Report structure for answering embedded questions
- [framework-refinement-worksheet.md](./framework-refinement-worksheet.md) - Refinement process (if applicable)

---

## Change Log

### v2.0.1 (2026-02-04)
- Enhanced priority labels with text: MUST-HAVE / SHOULD-HAVE / NICE-TO-HAVE
- Improved table scannability and accessibility
- Updated comparison table template
- Updated terminology throughout document

### v2.0 (2026-02-04)
- Refined all ambiguous questions based on user feedback
- Reduced CRITICAL questions from 8 to 4
- Added 3 new questions (21.1, 21.2, 21.3)
- Split 3 questions into sub-questions (1.1, 1.4, 8.1)
- Merged duplicate air-gapped questions
- Realigned priorities to match actual use case
- Updated scoring system with clearer weights
- Added comprehensive examples and clarifications

### v1.0 (2026-02-04)
- Initial release
- 100 questions across 20 categories
- 8 CRITICAL questions (later found to be too restrictive)
