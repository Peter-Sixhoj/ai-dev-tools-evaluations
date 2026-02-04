# AI Development Tools Decision Rationale v2.0

**Version**: 2.0  
**Date Created**: 2026-02-04  
**Last Updated**: 2026-02-04  
**Supersedes**: decision-rationale.md v1.0  
**References**: decision-criteria-v2.md  
**Status**: Active

## Changes from v1.0

This version includes updated rationale for:
- Split questions (1.1 → 1.1a/1.1b, 1.4 → 1.4a/1.4b, 8.1 → 8.1a/8.1b)
- Removed duplicate (20.1 air-gapped merged into 1.2)
- Priority adjustments with new justifications
- 3 new questions (21.1, 21.2, 21.3)
- Clarified critical questions (3.2, 10.1)

---

## Critical Questions (🔴) - The 4 Deal-Breakers

These questions determine **code portability and vendor lock-in avoidance**. Failing these means you cannot easily migrate away from the tool or deploy your applications freely.

### 1.1b: Can applications you build be deployed outside the product's own infrastructure?

**Why This Matters**: You need freedom to deploy your applications wherever your business requires—AWS, GCP, Azure, on-premises, or any hosting provider. Platform-locked deployment means ongoing dependency on vendor infrastructure, pricing, and availability.

**Decision Impact**: CRITICAL for deployment flexibility and avoiding operational lock-in.

**Evidence to Look For**: 
- Exported code runs on any hosting provider
- No platform-specific deployment requirements
- Standard deployment processes (Docker, Kubernetes, traditional hosting)
- User reports of deploying to various platforms

**Examples**:
- ✅ YES: Exports standard Next.js app that deploys anywhere
- ⚠️ REQUIRES PLATFORM: Must deploy to vendor's proprietary hosting
- ❌ NO: Only runs on vendor infrastructure

---

### 3.1: Can you export 100% of generated code?

**Why This Matters**: Incomplete code export means you lose work if you need to migrate tools. If only 80% exports, you must recreate the missing 20%, creating substantial migration costs and delays.

**Decision Impact**: CRITICAL for avoiding vendor lock-in and ensuring work is never lost.

**Evidence to Look For**: 
- Export/download functionality
- User reports of export completeness
- Documentation about what gets exported
- Community discussions about missing exports

---

### 3.2: Does exported code avoid proprietary runtime dependencies?

**Why This Matters**: Proprietary runtime dependencies mean your application cannot run without vendor-specific SDKs, libraries, or services. This creates permanent vendor lock-in even after exporting code.

**Decision Impact**: CRITICAL for true code ownership and portability.

**What Counts as Proprietary Dependency**:
- ❌ BAD: Requires vendor-specific runtime library to execute
- ❌ BAD: Hard-coded to vendor's proprietary services
- ⚠️ ACCEPTABLE: Uses standard npm packages (even if vendor-preferred)
- ✅ GOOD: Uses only open-source, swappable dependencies

**Examples**:
- ✅ YES: Uses Supabase client (npm package, can swap for Firebase/PocketBase)
- ✅ YES: Uses standard React, Express, PostgreSQL libraries
- ⚠️ VENDOR SDK: Requires AWS Amplify SDK (vendor-specific but open source)
- ❌ NO: Requires proprietary runtime that only vendor provides

**Evidence to Look For**: 
- package.json / Cargo.toml dependencies
- No proprietary imports in exported code
- Runs with standard package managers
- Documentation about dependencies

---

### 10.1: Can exported projects run using standard dev commands in any IDE?

**Why This Matters**: IDE lock-in means you cannot use industry-standard tools, onboard new developers easily, or maintain projects long-term. If projects only run inside the tool's IDE, you're locked in.

**Decision Impact**: CRITICAL for development flexibility and avoiding tool dependency.

**What This Checks**:
- Can you run `npm start` / `cargo run` in VS Code, IntelliJ, or terminal?
- Does exported code work without the tool installed?
- Can other team members work on the code without the tool?

**Evidence to Look For**: 
- "Export and run" tutorials showing standard commands
- User reports of running projects in other IDEs
- Standard project structure that any IDE recognizes
- No tool-specific configuration required

---

## High Priority Questions (🟡) - Core Functionality

These questions determine **productivity, developer experience, and feature completeness**. Important for daily work but not absolute deal-breakers.

### 1.3: Can it run as a local desktop application?

**Why This Matters**: Desktop apps provide lower latency, work offline, avoid browser limitations, and integrate better with local dev tools. Web-only means constant internet dependency and potential performance issues.

**Decision Impact**: HIGH for developer experience and productivity.

---

### 1.4a: Where does the IDE/editor run?

**Why This Matters**: Local IDEs feel more responsive and work offline. Cloud IDEs enable browser access but require internet. Understanding the tradeoffs helps match tool to your work environment.

**Decision Impact**: HIGH for workflow fit and performance expectations.

---

### 1.4b: Where are AI features processed?

**Why This Matters**: AI processing location affects latency, data privacy, and offline capability. Cloud processing enables better models but requires internet. Self-hosted provides control but requires infrastructure.

**Decision Impact**: HIGH for performance and data privacy considerations.

---

### 2.1: Does it support npm package installation?

**Why This Matters**: npm is the standard for TypeScript/JavaScript. Without npm support, you cannot use React, Next.js, or thousands of essential packages.

**Decision Impact**: HIGH for TypeScript/JavaScript development capability.

---

### 2.3: Can it handle monorepo dependency structures?

**Why This Matters**: Monorepos organize multiple projects with shared dependencies. Tools that don't understand monorepo structure provide incorrect suggestions and break builds.

**Decision Impact**: HIGH for teams using monorepo architecture.

---

### 3.3: Is exported code in standard project format?

**Why This Matters**: Standard formats (package.json, standard directories) mean exported code works immediately with industry tools. Proprietary formats require conversion.

**Decision Impact**: HIGH for toolchain compatibility.

---

### 3.4: Can exported code run with zero modifications?

**Why This Matters**: Immediate execution means no setup friction. Requiring modifications to run wastes time and creates migration barriers.

**Decision Impact**: HIGH for smooth workflow transitions.

**Clarification**: "Zero modifications" means:
- ✅ YES: `npm install && npm start` works immediately
- ⚠️ REQUIRES npm install: Need to install deps but no code changes
- ⚠️ REQUIRES SETUP: Must modify config files or code
- ❌ NO: Substantial changes needed to run

---

### 4.1: Does it have first-class TypeScript support?

**Why This Matters**: First-class TypeScript means full type inference, intelligent autocomplete, and TypeScript-aware AI. Basic support leads to type errors and poor suggestions.

**Decision Impact**: HIGH for TypeScript development quality.

**Note**: Downgraded from CRITICAL to HIGH because JavaScript-only is acceptable for some projects.

---

### 4.3-4.5: Framework Support (React/Next.js, Python, Go)

**Why This Matters**: Framework-specific support means scaffolding, best practices, and intelligent suggestions. Generic support misses framework patterns.

**Decision Impact**: HIGH for development speed in these frameworks.

---

### 5.1-5.3: Git Integration (Native, GitHub/GitLab, PR workflows)

**Why This Matters**: Git integration enables version control without context switching. Direct GitHub/GitLab push streamlines collaboration. PR workflows are standard for teams.

**Decision Impact**: HIGH for team collaboration and professional workflows.

---

### 6.1-6.3: Multi-file Context

**Why This Matters**: Understanding file relationships, cross-file refactoring, and large context windows enable working on complex features spanning many files.

**Decision Impact**: HIGH for complex application development.

---

### 7.1-7.3: Backend Capabilities

**Why This Matters**: Backend generation (multiple languages, database schemas, APIs) enables full-stack development. Frontend-only doubles development time.

**Decision Impact**: HIGH for full-stack applications.

---

### 8.1b: Git-based collaboration workflows

**Why This Matters**: Git workflows (branches, PRs, code review) are standard for professional teams. Essential for distributed teams and code quality.

**Decision Impact**: HIGH for team development.

---

### 10.2-10.3: Offline capability and debugging

**Why This Matters**: Offline work enables development anywhere. Debugging is essential for fixing bugs efficiently.

**Decision Impact**: HIGH for uninterrupted development.

---

### 11.1-11.3: AI Model Selection

**Why This Matters**: Different models have different strengths. Model switching and BYOK enable optimization and cost control.

**Decision Impact**: HIGH for code quality and cost management.

---

### 12.1-12.2: IDE Type

**Why This Matters**: Interface type (desktop, web, VS Code fork/extension) determines workflow integration and familiarity.

**Decision Impact**: HIGH for developer adoption and productivity.

---

### 13.1-13.3: Codebase Scale

**Why This Matters**: File count limits, context window, and enterprise-scale validation determine if tool works with your actual codebase size.

**Decision Impact**: HIGH for ensuring tool matches your scale.

**Clarification**:
- **13.1 (File count)**: Storage/indexing capacity
- **13.2 (Context window)**: How much code AI sees at once
- **13.3 (Enterprise proven)**: Real-world validation on large codebases

---

### 14.1-14.2: API Integration (Supabase, Type-safe clients)

**Why This Matters**: Supabase scaffolding and type-safe API clients accelerate backend integration with safety.

**Decision Impact**: HIGH for Supabase-based projects and type safety.

---

### 15.1-15.3: Code Generation Scope

**Why This Matters**: Full app generation, feature generation, and inline completion determine development velocity.

**Decision Impact**: HIGH for rapid development.

---

### 16.1: VS Code Extension Support

**Why This Matters**: VS Code marketplace has 40k+ extensions. Support means using existing workflow tools.

**Decision Impact**: HIGH for preserving workflows.

---

### 17.1-17.3: Pricing

**Why This Matters**: Free tier enables evaluation. Cost per developer affects budget. Enterprise licensing enables procurement.

**Decision Impact**: HIGH for budget and adoption decisions.

---

### 20.2-20.3: Security (Vulnerability scanning, Auth scaffolding)

**Why This Matters**: Security scanning detects vulnerabilities proactively. Auth scaffolding reduces security implementation errors.

**Decision Impact**: HIGH for secure applications.

---

### 21.1: Team Size Support

**Why This Matters**: Tools optimized for different team sizes. Solo tools don't scale; enterprise tools overwhelm small teams.

**Decision Impact**: HIGH for matching tool to team size.

---

### 21.3: Vendor Stability

**Why This Matters**: Vendor stability affects long-term tool availability. Early-stage startups risk shutdown; established vendors provide continuity.

**Decision Impact**: HIGH for long-term investment decisions.

---

## Medium Priority Questions (🟢) - Nice-to-Have

These questions provide **additional value** but are not decisive in tool selection.

### 1.1a: Can the development environment be self-hosted?

**Why This Matters**: Self-hosting the dev environment provides data control and compliance benefits.

**Decision Impact**: NICE-TO-HAVE for data sovereignty preferences.

**Note**: Downgraded from CRITICAL to nice-to-have because:
- Main concern is end-product portability (covered by 1.1b)
- Cloud IDE acceptable if code exports cleanly
- Most teams can work with cloud-based development

---

### 1.2: Can it operate in air-gapped environments?

**Why This Matters**: Air-gapped operation enables development in high-security environments.

**Decision Impact**: NICE-TO-HAVE unless you work in defense/classified environments.

**Note**: Downgraded from CRITICAL to nice-to-have because:
- User confirmed not working in classified/defense
- Future-proofing rather than current requirement
- Internet access acceptable for current use case

---

### 1.5: Web-based version available?

**Why This Matters**: Web version enables quick access from any device without installation.

**Decision Impact**: NICE-TO-HAVE for accessibility.

---

### 2.2: Rust (cargo) support?

**Why This Matters**: Cargo support enables Rust development.

**Decision Impact**: NICE-TO-HAVE for Rust projects.

---

### 2.4-2.5: Python packages and restrictions

**Why This Matters**: Python support and package freedom enable backend development flexibility.

**Decision Impact**: NICE-TO-HAVE unless Python is primary language.

---

### 3.5: Export project history?

**Why This Matters**: Git history preserves development context and blame information.

**Decision Impact**: NICE-TO-HAVE for maintaining history.

---

### 4.2: Rust with LSP integration?

**Why This Matters**: Rust LSP provides type checking and intelligent completion.

**Decision Impact**: NICE-TO-HAVE for Rust development.

**Note**: Downgraded from CRITICAL to nice-to-have because:
- Not actively developing Rust today
- Future-proofing rather than current requirement
- ALL 6 evaluated tools failed or barely passed this

---

### 4.6-4.7: Vue.js and Angular support

**Why This Matters**: Framework support for Vue and Angular teams.

**Decision Impact**: NICE-TO-HAVE unless these are primary frameworks.

---

### 5.4-5.5: Visual Git UI and branch management

**Why This Matters**: Visual Git tools improve accessibility and understanding.

**Decision Impact**: NICE-TO-HAVE for Git workflow enhancement.

---

### 6.4-6.5: Consistency and codebase analysis

**Why This Matters**: Consistency maintains code quality. Codebase analysis finds improvements.

**Decision Impact**: NICE-TO-HAVE for code quality.

---

### 7.4-7.5: Full-stack scaffolding and integration

**Why This Matters**: Accelerates full-stack development.

**Decision Impact**: NICE-TO-HAVE for rapid prototyping.

---

### 8.1a: Real-time multiplayer collaboration

**Why This Matters**: Real-time editing enables Google Docs-style collaboration.

**Decision Impact**: NICE-TO-HAVE; Git workflows often preferred by professional teams.

---

### 8.2-8.5: Advanced collaboration (permissions, simultaneous, review, cursors)

**Why This Matters**: Enhanced collaboration features for team workflows.

**Decision Impact**: NICE-TO-HAVE for team productivity.

---

### 9.1-9.5: Deployment Automation (all questions)

**Why This Matters**: Built-in deployment streamlines operations.

**Decision Impact**: NICE-TO-HAVE; most teams have existing CI/CD.

---

### 10.4-10.5: Performance differences and dev tools alongside

**Why This Matters**: Understanding performance and tool compatibility.

**Decision Impact**: NICE-TO-HAVE for workflow optimization.

---

### 11.4-11.5: Model transparency and local models

**Why This Matters**: Transparency aids debugging. Local models enable offline AI.

**Decision Impact**: NICE-TO-HAVE for advanced use cases.

---

### 12.3-12.5: Terminal, customization, keyboard shortcuts

**Why This Matters**: IDE customization and power-user features.

**Decision Impact**: NICE-TO-HAVE for developer experience.

---

### 13.4-13.5: Large monorepos and degradation thresholds

**Why This Matters**: Performance at scale.

**Decision Impact**: NICE-TO-HAVE for capacity planning.

---

### 14.3-14.5: Auth templates, payments, GraphQL

**Why This Matters**: Accelerate common integrations.

**Decision Impact**: NICE-TO-HAVE for specific use cases.

---

### 15.4-15.5: UI-only generation and test files

**Why This Matters**: Specialized generation capabilities.

**Decision Impact**: NICE-TO-HAVE for specific workflows.

---

### 16.2-16.5: Extension ecosystem details

**Why This Matters**: Extension compatibility details.

**Decision Impact**: NICE-TO-HAVE for extension power users.

---

### 17.4-17.5: Usage measurement and limits

**Why This Matters**: Understanding cost structure.

**Decision Impact**: NICE-TO-HAVE for cost forecasting.

---

### 18.1-18.5: Mobile Support (all questions)

**Why This Matters**: Mobile app development capabilities.

**Decision Impact**: NICE-TO-HAVE unless mobile is core requirement.

---

### 19.1-19.5: Performance Optimization (all questions)

**Why This Matters**: Optimization suggestions and tooling.

**Decision Impact**: NICE-TO-HAVE for performance-critical apps.

---

### 20.4-20.5: GDPR features and certifications

**Why This Matters**: Compliance features and vendor certifications.

**Decision Impact**: NICE-TO-HAVE for compliance-heavy environments.

---

### 21.2: Learning Curve

**Why This Matters**: Onboarding time affects team adoption speed.

**Decision Impact**: NICE-TO-HAVE for understanding adoption costs.

---

## Related Documents

- [decision-criteria-v2.md](./decision-criteria-v2.md) - Updated question framework
- [framework-refinement-worksheet.md](./framework-refinement-worksheet.md) - Refinement process
- [decision-rationale.md](./decision-rationale.md) - Original v1.0 (superseded)

---

## Change Log

### v2.0 (2026-02-04)
- Updated rationale for all 4 CRITICAL questions
- Added rationale for split questions (1.1a/b, 1.4a/b, 8.1a/b)
- Removed rationale for 20.1 (merged into 1.2)
- Updated priority explanations with user context
- Added clarifications for ambiguous questions
- Documented priority downgrades (air-gapped, self-hosted, Rust, TypeScript)

### v1.0 (2026-02-04)
- Initial release
