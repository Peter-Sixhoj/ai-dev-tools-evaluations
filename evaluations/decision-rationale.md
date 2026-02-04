# AI Development Tools Decision Rationale

**Version**: 1.0  
**Date Created**: 2026-02-04  
**Last Updated**: 2026-02-04  
**References**: decision-criteria.md v1.0  
**Status**: Active

## Purpose

This document explains the reasoning behind each decision question in [decision-criteria.md](./decision-criteria.md). Use this to:
- Understand why each question matters for tool selection
- Assess decision impact on your specific requirements
- Identify what evidence to look for during evaluation
- Justify tool selection decisions to stakeholders

---

## 1. Deployment Model

### 1.1 Can the tool be fully self-hosted on-premises?

**Why This Matters**: Self-hosting provides complete data control, compliance with data sovereignty requirements, and independence from vendor availability. Cloud-only tools send your code to external servers, which may violate security policies or regulations.

**Decision Impact**: Critical for regulated industries, security-conscious organizations, and teams requiring data sovereignty.

**Evidence to Look For**: Docker/Kubernetes deployment guides, on-premises installation documentation, self-hosted pricing tier, customer case studies of on-premises deployments.

---

### 1.2 Does it work in air-gapped environments without internet?

**Why This Matters**: Air-gapped operation is required for defense, government, financial institutions, and high-security environments. If the tool requires internet access for core functionality (AI API calls, license validation, telemetry), it cannot be used in these environments.

**Decision Impact**: Deal-breaker for high-security and classified environments.

**Evidence to Look For**: Offline mode documentation, local AI model support, explicit air-gapped deployment guides, government/defense customer references.

---

### 1.3 Can it run as a local desktop application?

**Why This Matters**: Local desktop apps provide lower latency, work offline, avoid browser limitations, and give you control over updates. Web-only tools require constant internet connectivity and may have performance issues.

**Decision Impact**: High priority for developer experience and offline productivity.

**Evidence to Look For**: Desktop app downloads for Windows/Mac/Linux, Electron-based apps, installation guides, system requirements.

---

### 1.4 Where is code processed? (local vs cloud)

**Why This Matters**: Local processing keeps your code on your machine, preventing IP leakage and enabling offline work. Cloud processing sends code to vendor servers for AI analysis, raising security and privacy concerns.

**Decision Impact**: High priority for IP protection and security compliance.

**Evidence to Look For**: Architecture diagrams, privacy policy statements about code processing, local vs cloud feature comparisons, data residency documentation.

---

### 1.5 Is there a web-based version available?

**Why This Matters**: Web versions enable quick access from any device, no installation required, and easier team collaboration. Useful for demos, trials, and teams with diverse hardware.

**Decision Impact**: Nice-to-have for accessibility and ease of adoption.

**Evidence to Look For**: Web app URL, browser requirements, feature parity between web and desktop versions.

---

## 2. Package Management

### 2.1 Does it support npm package installation?

**Why This Matters**: npm is the standard package manager for TypeScript/JavaScript. Without npm support, you can't use React, Next.js, Express, or thousands of other essential packages, severely limiting development capabilities.

**Decision Impact**: High priority for TypeScript/JavaScript development.

**Evidence to Look For**: npm install commands in documentation, package.json examples, dependency installation screenshots, supported package managers list.

---

### 2.2 Does it support cargo (Rust) packages?

**Why This Matters**: Cargo is Rust's package manager and build system. Without cargo support, Rust development is severely limited—you can't use popular crates like serde, tokio, or actix-web.

**Decision Impact**: High priority for Rust development.

**Evidence to Look For**: Cargo.toml examples, cargo build/run commands, crates.io integration, Rust project scaffolding.

---

### 2.3 Can it handle monorepo dependency structures?

**Why This Matters**: Monorepos (Nx, Turborepo, Lerna) organize multiple related projects in one repository with shared dependencies. Tools that don't understand monorepo structure may fail to resolve imports, break builds, or provide incorrect AI suggestions.

**Decision Impact**: High priority for teams using monorepo architecture.

**Evidence to Look For**: Monorepo examples, workspace configuration support, documentation about Nx/Turborepo/pnpm workspaces, multi-package project demos.

---

### 2.4 Does it support pip (Python) packages?

**Why This Matters**: pip is Python's package manager. Without pip support, you can't use Django, Flask, FastAPI, pandas, numpy, or most Python libraries, making Python development impractical.

**Decision Impact**: Nice-to-have unless Python is a primary language.

**Evidence to Look For**: requirements.txt examples, pip install commands, virtual environment support, Python project templates.

---

### 2.5 Are there restrictions on which packages can be used?

**Why This Matters**: Some platforms restrict packages due to sandboxing, security scanning, or runtime limitations. Package restrictions prevent using essential tools and force workarounds or abandoning the platform.

**Decision Impact**: Nice-to-have for ensuring full development flexibility.

**Evidence to Look For**: Blocked package lists, security policy documentation, sandbox limitations, user reports of package installation failures.

---

## 3. Code Ownership

### 3.1 Can you export 100% of generated code?

**Why This Matters**: Full code export ensures you're never locked into a platform. If you can't export all code, you lose work if the vendor shuts down, changes pricing, or removes features.

**Decision Impact**: Deal-breaker for avoiding vendor lock-in.

**Evidence to Look For**: Export functionality in UI, download/clone options, documentation about exporting projects, user reports of export completeness.

---

### 3.2 Is exported code dependency-free from the platform?

**Why This Matters**: Platform dependencies mean exported code requires proprietary runtime libraries, SDKs, or services to function. This creates vendor lock-in and prevents switching tools or running code independently.

**Decision Impact**: Deal-breaker for true code ownership.

**Evidence to Look For**: Exported code samples, runtime requirements, proprietary SDK usage, documentation about code dependencies, community discussions about lock-in.

---

### 3.3 Is code export in standard project format (no proprietary structure)?

**Why This Matters**: Standard formats (standard package.json, Cargo.toml, standard directory structure) mean exported code works immediately with industry-standard tools. Proprietary formats require conversion or specialized tools.

**Decision Impact**: High priority for toolchain compatibility.

**Evidence to Look For**: Exported project examples, file structure documentation, compatibility with standard build tools (webpack, vite, cargo), no custom configuration files.

---

### 3.4 Can exported code run immediately in local environment?

**Why This Matters**: Immediate local execution means no additional setup, configuration, or migration work. If exported code requires modifications to run, it wastes development time and creates migration friction.

**Decision Impact**: High priority for smooth workflow transitions.

**Evidence to Look For**: "Export and run" tutorials, npm start/cargo run examples after export, user testimonials about export experience, quick-start guides with exported projects.

---

### 3.5 Can you export project history/version control?

**Why This Matters**: Exporting Git history preserves commit messages, blame information, and development timeline. Without history, you lose context for code changes and debugging information.

**Decision Impact**: Nice-to-have for maintaining development history.

**Evidence to Look For**: Git repository export, .git folder inclusion, commit history preservation, branch export capabilities.

---

## 4. Framework Support

### 4.1 Does it have first-class TypeScript support?

**Why This Matters**: First-class TypeScript support means full type inference, intelligent autocomplete, accurate refactoring, and TypeScript-aware AI suggestions. Basic support leads to type errors, poor suggestions, and reduced productivity.

**Decision Impact**: Deal-breaker for TypeScript-first development.

**Evidence to Look For**: TypeScript LSP integration, tsconfig.json support, type-aware code completion, TypeScript-specific examples, ts-node/tsx execution support.

---

### 4.2 Does it support Rust with LSP integration?

**Why This Matters**: Rust LSP (rust-analyzer) provides type checking, cargo integration, error diagnostics, and intelligent code completion. Without LSP, Rust development lacks essential tooling for catching errors and understanding complex types.

**Decision Impact**: Deal-breaker for serious Rust development.

**Evidence to Look For**: rust-analyzer integration, cargo check/clippy integration, Rust-specific autocomplete, compiler error display, Rust documentation in-editor.

---

### 4.3 Does it support React/Next.js?

**Why This Matters**: React is the most popular frontend framework, and Next.js is the leading React framework for production apps. Support means component scaffolding, JSX/TSX syntax understanding, and framework-specific patterns.

**Decision Impact**: High priority for modern web development.

**Evidence to Look For**: React component generation, Next.js project templates, JSX syntax highlighting, React Hooks understanding, App Router vs Pages Router support.

---

### 4.4 Does it support Python?

**Why This Matters**: Python is essential for backend APIs (FastAPI, Django), data science, machine learning, and scripting. Support means Python-aware AI suggestions, pip integration, and virtual environment handling.

**Decision Impact**: High priority for backend or data-focused development.

**Evidence to Look For**: Python project templates, FastAPI/Django examples, pip/poetry support, virtual environment integration, Python debugger support.

---

### 4.5 Does it support Go?

**Why This Matters**: Go is popular for backend services, microservices, and cloud-native applications. Support means Go module understanding, goroutine handling, and idiomatic Go code generation.

**Decision Impact**: High priority for Go-based backend development.

**Evidence to Look For**: Go module support, go.mod understanding, Go project scaffolding, goroutine and channel code examples, Go standard library integration.

---

### 4.6 Does it support Vue.js?

**Why This Matters**: Vue.js is a popular progressive framework with a large community. Support means Single File Components (SFC) understanding, Vue 3 Composition API, and Vue-specific tooling.

**Decision Impact**: Nice-to-have for Vue-focused teams.

**Evidence to Look For**: .vue file support, Vue project templates, Composition API examples, Pinia/Vuex integration, Vue Router scaffolding.

---

### 4.7 Does it support Angular?

**Why This Matters**: Angular is used in many enterprise applications. Support means TypeScript decorators, RxJS integration, Angular CLI compatibility, and Angular-specific patterns.

**Decision Impact**: Nice-to-have for Angular-focused teams.

**Evidence to Look For**: Angular project templates, component/service generation, @angular/cli compatibility, RxJS observable handling, Angular Material integration.

---

## 5. Git Integration

### 5.1 Does it have native Git integration?

**Why This Matters**: Native Git integration enables committing, viewing diffs, and managing branches within the tool. CLI-only means constant context switching to terminal, slowing down workflow.

**Decision Impact**: High priority for developer productivity.

**Evidence to Look For**: Built-in Git panel/sidebar, commit UI, branch visualization, diff viewer, Git status indicators in file tree.

---

### 5.2 Can you push directly to GitHub/GitLab?

**Why This Matters**: Direct push capability streamlines collaboration by connecting to your existing repositories. Manual export-then-push workflow adds friction and delays team collaboration.

**Decision Impact**: High priority for team workflows.

**Evidence to Look For**: GitHub/GitLab authentication flows, push/pull buttons in UI, remote repository configuration, OAuth integration documentation.

---

### 5.3 Does it support pull request workflows?

**Why This Matters**: PR workflows (creating PRs, reviewing code, addressing comments) are standard for team collaboration. Without PR support, teams must use external tools, breaking workflow continuity.

**Decision Impact**: High priority for collaborative development.

**Evidence to Look For**: Create PR functionality, PR review interface, inline comment support, PR status tracking, approval workflows.

---

### 5.4 Does it have a visual Git UI?

**Why This Matters**: Visual Git UI (commit graph, branch diagram, visual diff) makes Git operations accessible to less experienced users and speeds up understanding repository state.

**Decision Impact**: Nice-to-have for improved user experience.

**Evidence to Look For**: Commit history visualization, branch diagram, visual merge conflict resolution, diff visualization with highlighting.

---

### 5.5 Can it handle branch management?

**Why This Matters**: Branch management (create, switch, merge, delete branches) is essential for feature development and collaboration. Without it, developers must use command line, increasing complexity.

**Decision Impact**: Nice-to-have for Git workflow efficiency.

**Evidence to Look For**: Branch creation UI, branch switching, branch comparison, merge UI, branch deletion capabilities.

---

## 6. Multi-file Context Awareness

### 6.1 Can it understand relationships between files?

**Why This Matters**: Understanding file relationships means the AI knows how components import each other, database schemas relate to API routes, and types flow between files. Without this, suggestions are isolated and may break integrations.

**Decision Impact**: High priority for coherent multi-file development.

**Evidence to Look For**: Cross-file type inference, import path suggestions, "find all references" across files, refactoring that updates imports automatically.

---

### 6.2 Can it refactor across multiple files?

**Why This Matters**: Multi-file refactoring (rename component, move function, extract shared code) maintains consistency across codebase. Single-file refactoring creates broken imports and inconsistent naming.

**Decision Impact**: High priority for maintaining codebase consistency.

**Evidence to Look For**: Rename symbol across files, move file with import updates, extract to new file functionality, user examples of multi-file refactoring.

---

### 6.3 What is the maximum file context size?

**Why This Matters**: Context size determines how many files the AI can consider simultaneously. Larger context enables better understanding of complex features spanning many files but costs more and may be slower.

**Decision Impact**: High priority for large feature development.

**Evidence to Look For**: Documented token/file limits, context window specifications (e.g., "200K tokens", "50 files"), performance with different context sizes.

---

### 6.4 Does it maintain consistency when generating new files?

**Why This Matters**: Consistent generation means new files follow existing patterns (naming conventions, code style, architecture). Inconsistent generation creates technical debt and requires manual cleanup.

**Decision Impact**: Nice-to-have for maintaining code quality.

**Evidence to Look For**: Style matching examples, naming convention adherence, architectural pattern consistency, user reports of generated code quality.

---

### 6.5 Can it analyze entire codebase for suggestions?

**Why This Matters**: Codebase-wide analysis identifies patterns, unused code, inconsistencies, and improvement opportunities across all files. Single-file analysis misses architectural issues and duplication.

**Decision Impact**: Nice-to-have for code quality and optimization.

**Evidence to Look For**: Whole-codebase scanning, unused code detection, duplicate code identification, architectural suggestions, refactoring recommendations.

---

## 7. Backend Capabilities

### 7.1 Can it generate backend code (Node.js/Python/Go/Rust)?

**Why This Matters**: Backend code generation enables building complete full-stack applications. Frontend-only tools require manually writing all backend code, doubling development time.

**Decision Impact**: High priority for full-stack development.

**Evidence to Look For**: API endpoint generation, database query code, authentication logic, backend project templates, Express/FastAPI/Gin/Actix examples.

---

### 7.2 Can it create database schemas?

**Why This Matters**: Database schema generation (SQL DDL, Prisma schemas, SQLAlchemy models) accelerates backend development. Manual schema writing is time-consuming and error-prone.

**Decision Impact**: High priority for data-driven applications.

**Evidence to Look For**: SQL schema generation, ORM model generation (Prisma, TypeORM, SQLAlchemy), migration file creation, schema visualization.

---

### 7.3 Does it support API generation (REST/GraphQL)?

**Why This Matters**: API generation creates endpoints, request/response types, validation, and documentation. Manual API development is repetitive and requires maintaining type consistency.

**Decision Impact**: High priority for API-first development.

**Evidence to Look For**: REST endpoint scaffolding, GraphQL resolver generation, API documentation generation (OpenAPI/Swagger), type-safe API client generation.

---

### 7.4 Can it scaffold full-stack applications?

**Why This Matters**: Full-stack scaffolding generates connected frontend and backend with authentication, database, and API integration. Saves weeks of boilerplate development and ensures architectural consistency.

**Decision Impact**: Nice-to-have for rapid prototyping and MVPs.

**Evidence to Look For**: Full-stack templates (Next.js + API, React + Express), authentication flow scaffolding, database integration, API client generation.

---

### 7.5 Does frontend/backend integration work seamlessly?

**Why This Matters**: Seamless integration means type-safe API calls, automatic client generation, shared types between frontend/backend. Manual integration requires duplicating types and is error-prone.

**Decision Impact**: Nice-to-have for type safety and productivity.

**Evidence to Look For**: Type-safe API clients (tRPC, GraphQL Codegen), shared type definitions, automatic API endpoint discovery, end-to-end type safety examples.

---

## 8. Collaboration Features

### 8.1 Does it support team collaboration?

**Why This Matters**: Team collaboration enables multiple developers working together, code reviews, and shared projects. Solo-only tools don't scale beyond individual developers.

**Decision Impact**: High priority for team development.

**Evidence to Look For**: Team workspace features, user invitation/management, shared project access, collaboration documentation, team pricing tiers.

---

### 8.2 Are there role-based permissions?

**Why This Matters**: Role-based permissions (admin, developer, viewer) control access to projects, settings, and sensitive operations. Without permissions, all team members have full access, creating security risks.

**Decision Impact**: Nice-to-have for larger teams and security.

**Evidence to Look For**: Permission management UI, role definitions, access control documentation, enterprise security features.

---

### 8.3 Can multiple developers work simultaneously?

**Why This Matters**: Simultaneous editing enables pair programming and parallel development on the same project. Sequential-only access creates bottlenecks and delays.

**Decision Impact**: Nice-to-have for team productivity.

**Evidence to Look For**: Real-time collaboration features, conflict resolution, simultaneous edit support, multi-user session documentation.

---

### 8.4 Does it support code review workflows?

**Why This Matters**: Code review workflows (review requests, inline comments, approval) maintain code quality and knowledge sharing. Without reviews, code quality suffers.

**Decision Impact**: Nice-to-have for code quality assurance.

**Evidence to Look For**: Code review UI, comment threads, approval systems, review request notifications, integration with GitHub/GitLab reviews.

---

### 8.5 Are there live cursors for real-time editing?

**Why This Matters**: Live cursors show where teammates are editing in real-time, preventing edit conflicts and enabling pair programming. Improves collaboration awareness.

**Decision Impact**: Nice-to-have for real-time collaboration.

**Evidence to Look For**: Cursor presence indicators, real-time edit synchronization, user avatars in editor, Google Docs-style collaboration.

---

## 9. Deployment Automation

### 9.1 Does it have built-in deployment automation?

**Why This Matters**: Built-in deployment (one-click deploy) eliminates manual deployment configuration and reduces time-to-production. Manual deployment requires DevOps knowledge and setup time.

**Decision Impact**: Nice-to-have for rapid deployment and MVPs.

**Evidence to Look For**: Deploy buttons in UI, automated deployment pipelines, deployment status tracking, rollback capabilities.

---

### 9.2 Which platforms does it deploy to?

**Why This Matters**: Platform variety (Vercel, Netlify, AWS, GCP, Azure) provides flexibility and prevents vendor lock-in. Single-platform deployment limits hosting options.

**Decision Impact**: Nice-to-have for deployment flexibility.

**Evidence to Look For**: Supported platform list, deployment configuration examples, multi-cloud support, custom deployment target options.

---

### 9.3 Does it support CI/CD pipeline integration?

**Why This Matters**: CI/CD integration (GitHub Actions, GitLab CI, CircleCI) enables automated testing, building, and deployment. Fits into existing DevOps workflows.

**Decision Impact**: Nice-to-have for enterprise DevOps integration.

**Evidence to Look For**: CI/CD configuration files, pipeline examples, GitHub Actions workflows, integration documentation with popular CI/CD tools.

---

### 9.4 Can it handle database migrations on deploy?

**Why This Matters**: Automated database migrations prevent deployment failures from schema mismatches and reduce manual work. Manual migrations are error-prone.

**Decision Impact**: Nice-to-have for database-driven applications.

**Evidence to Look For**: Migration file generation, automated migration execution on deploy, rollback support, schema versioning.

---

### 9.5 Is deployment configuration customizable?

**Why This Matters**: Customization (environment variables, build settings, resource limits) enables production-grade deployments. Fixed configuration may not meet security or performance requirements.

**Decision Impact**: Nice-to-have for production deployments.

**Evidence to Look For**: Environment variable configuration, build script customization, deployment settings UI, resource allocation options.

---

## 10. Local Development Support

### 10.1 Can you run projects locally without the tool?

**Why This Matters**: Running projects without the tool means you're not locked in. If you can only run projects inside the tool, you lose access if the vendor shuts down or changes pricing.

**Decision Impact**: Deal-breaker for avoiding tool lock-in.

**Evidence to Look For**: Standard npm start/cargo run commands work, no proprietary runtime required, exported code runs in any IDE, documentation for running without tool.

---

### 10.2 Does it work offline?

**Why This Matters**: Offline capability enables development during flights, in remote locations, or when internet is unreliable. Cloud-only tools stop working completely without connectivity.

**Decision Impact**: High priority for uninterrupted development.

**Evidence to Look For**: Offline mode documentation, local AI model support, cached functionality, user reports of offline usage.

---

### 10.3 Is local debugging supported?

**Why This Matters**: Debugging (breakpoints, variable inspection, step-through) is essential for fixing bugs. Without debugging, developers resort to console.log debugging, which is inefficient.

**Decision Impact**: High priority for productive development.

**Evidence to Look For**: Debugger integration, breakpoint support, variable inspection, debug console, Chrome DevTools integration, language-specific debuggers.

---

### 10.4 Are there performance differences local vs cloud?

**Why This Matters**: Performance differences affect development speed. Slow local performance frustrates developers, while cloud-faster means you can't work offline efficiently.

**Decision Impact**: Nice-to-have for understanding tradeoffs.

**Evidence to Look For**: Performance benchmarks, user reports of speed differences, local vs cloud feature comparisons, latency measurements.

---

### 10.5 Can you use your own dev tools alongside it?

**Why This Matters**: Using existing tools (Postman, database clients, design tools) alongside the AI tool preserves workflows and avoids learning new tools. Forced replacement reduces productivity.

**Decision Impact**: Nice-to-have for workflow flexibility.

**Evidence to Look For**: Tool integration documentation, extension support, ability to run external tools, no restrictions on process execution.

---

## 11. AI Model Selection

### 11.1 Which AI models does it support?

**Why This Matters**: Different AI models have different strengths: GPT-4 for general code, Claude for complex reasoning, Gemini for multimodal tasks. Multiple model support provides flexibility to choose the best model for each task.

**Decision Impact**: High priority for code quality and flexibility.

**Evidence to Look For**: List of supported models, model version numbers (GPT-4 Turbo, Claude 3.5 Sonnet), model update frequency, model comparison features.

---

### 11.2 Can you switch between models?

**Why This Matters**: Model switching enables using GPT-4 for frontend, Claude for complex backend logic, or cost optimization by using cheaper models for simple tasks. Locked to one model limits flexibility.

**Decision Impact**: High priority for optimization and cost control.

**Evidence to Look For**: Model selection UI, per-project model settings, per-conversation model switching, documentation about model switching capabilities.

---

### 11.3 Can you use your own API keys?

**Why This Matters**: Using your own API keys provides cost control, usage transparency, and independence from platform pricing. Platform-only pricing may be expensive or have usage limits.

**Decision Impact**: High priority for cost management and enterprise budgeting.

**Evidence to Look For**: API key configuration settings, BYOK (Bring Your Own Key) pricing tier, documentation about using OpenAI/Anthropic keys directly.

---

### 11.4 Is model selection transparent to users?

**Why This Matters**: Transparency about which model is being used helps understand code quality, debug issues, and verify billing. Hidden model selection makes troubleshooting difficult.

**Decision Impact**: Nice-to-have for understanding tool behavior.

**Evidence to Look For**: Model name shown in UI, model version information, ability to see which model generated specific code, model usage logs.

---

### 11.5 Does it support local/open-source models?

**Why This Matters**: Local models (Llama, Code Llama, StarCoder) enable fully offline operation, no data leaving your infrastructure, and zero per-token costs. Important for air-gapped environments and cost optimization.

**Decision Impact**: Nice-to-have for privacy and cost reduction.

**Evidence to Look For**: Local model integration (Ollama, LM Studio), documentation about running local models, examples with open-source models, performance comparisons.

---

## 12. IDE Type

### 12.1 What is the primary interface?

**Why This Matters**: Interface type determines workflow integration. VS Code fork/extension integrates with existing workflows, web IDE enables browser access, CLI suits automation. Choice affects adoption and productivity.

**Decision Impact**: High priority for developer experience and team adoption.

**Evidence to Look For**: Screenshots of interface, download links for desktop apps, web app URLs, CLI installation commands, interface comparison documentation.

---

### 12.2 Is it based on VS Code?

**Why This Matters**: VS Code base means familiar interface, existing muscle memory works, and potentially VS Code extensions work. Reduces learning curve and leverages existing VS Code ecosystem.

**Decision Impact**: High priority for developer productivity and onboarding.

**Evidence to Look For**: "Built on VS Code" statements, VS Code version information, fork details, architectural documentation showing VS Code foundation.

---

### 12.3 Does it have terminal access?

**Why This Matters**: Terminal access enables running git commands, package managers, build scripts, database CLIs, and custom tools. Essential for professional development workflows beyond just coding.

**Decision Impact**: Nice-to-have but nearly essential for real development work.

**Evidence to Look For**: Integrated terminal screenshots, shell support (bash/zsh/PowerShell), terminal configuration options, multi-terminal support.

---

### 12.4 Can you customize the IDE?

**Why This Matters**: Customization includes themes, keybindings, layout, settings. Developers have strong preferences and customization improves productivity and comfort.

**Decision Impact**: Nice-to-have for developer experience.

**Evidence to Look For**: Settings/preferences UI, theme marketplace, keybinding configuration, workspace settings, user settings sync.

---

### 12.5 Does it support keyboard shortcuts?

**Why This Matters**: Keyboard shortcuts dramatically improve productivity for experienced developers. Mouse-only interfaces slow down development. Familiar shortcuts (Cmd+P, Cmd+Shift+F) are muscle memory.

**Decision Impact**: Nice-to-have for power user productivity.

**Evidence to Look For**: Keyboard shortcut documentation, customizable shortcuts, VS Code-compatible shortcuts, shortcut cheat sheets.

---

## 13. Codebase Scale Limits

### 13.1 What is the maximum file count supported?

**Why This Matters**: File count limits determine if tool can handle your codebase. Small projects: 100-500 files. Medium: 1k-5k files. Enterprise: 10k-100k+ files. Exceeding limits causes performance degradation or failures.

**Decision Impact**: High priority for ensuring tool works with your actual codebase size.

**Evidence to Look For**: Official file count limits, performance benchmarks with various repo sizes, user reports on large repositories, "unlimited" claims with caveats.

---

### 13.2 What is the context window size?

**Why This Matters**: Context window determines how much code the AI can "see" at once (measured in tokens or files). Larger context enables better cross-file understanding but costs more and may be slower.

**Decision Impact**: High priority for code quality on large codebases.

**Evidence to Look For**: Token/file count specifications, context window documentation (e.g., "200K tokens"), pricing per context tier, model-specific context limits.

---

### 13.3 Can it handle enterprise-scale codebases (100k+ LOC)?

**Why This Matters**: Enterprise-scale support means the tool can index, search, and provide AI suggestions on large codebases without crashing or slowing down. Small-scale tools fail on enterprise projects.

**Decision Impact**: High priority for enterprise development.

**Evidence to Look For**: Enterprise customer case studies, large repository examples, performance benchmarks on 100k+ LOC projects, scalability documentation.

---

### 13.4 Does it support large monorepos?

**Why This Matters**: Large monorepos (multiple apps, shared libraries, thousands of files) require special handling for dependency resolution and performance. Tools that don't support monorepos may be unusable for monorepo teams.

**Decision Impact**: Nice-to-have for monorepo teams.

**Evidence to Look For**: Monorepo-specific features, Nx/Turborepo compatibility, workspace indexing, monorepo customer examples.

---

### 13.5 Are there performance degradation thresholds?

**Why This Matters**: Knowing performance thresholds helps plan for growth. If tool slows down at 5k files and you have 10k, you'll face constant performance issues.

**Decision Impact**: Nice-to-have for capacity planning.

**Evidence to Look For**: Performance documentation by codebase size, user reports of slowdowns, benchmark results, recommended maximum project sizes.

---

## 14. API/Service Integration

### 14.1 Can it scaffold Supabase integration?

**Why This Matters**: Supabase is a popular PostgreSQL-based backend-as-a-service. Scaffolding integration generates authentication, database client setup, and type-safe queries, saving hours of boilerplate work.

**Decision Impact**: High priority for Supabase-based projects.

**Evidence to Look For**: Supabase templates, authentication setup, database client generation, Row Level Security examples, Supabase-specific tutorials.

---

### 14.2 Can it generate type-safe API clients?

**Why This Matters**: Type-safe API clients prevent runtime errors by catching API contract mismatches at compile time. Manual API calls lack type safety and require duplicating types.

**Decision Impact**: High priority for large applications with many API calls.

**Evidence to Look For**: tRPC integration, GraphQL Codegen support, OpenAPI client generation, type inference from API schemas, end-to-end type safety examples.

---

### 14.3 Does it have templates for auth providers?

**Why This Matters**: Auth provider templates (Auth0, Clerk, Firebase Auth, Supabase Auth) accelerate authentication implementation. Manual auth setup is complex and error-prone.

**Decision Impact**: Nice-to-have for rapid auth implementation.

**Evidence to Look For**: Auth provider integration templates, OAuth flow setup, JWT handling, session management, protected route examples.

---

### 14.4 Can it integrate payment processors?

**Why This Matters**: Payment processor integration (Stripe, PayPal) is complex and requires secure handling. Templates reduce integration time and security risks.

**Decision Impact**: Nice-to-have for e-commerce and SaaS applications.

**Evidence to Look For**: Stripe integration examples, payment flow scaffolding, webhook handling, subscription management, checkout page generation.

---

### 14.5 Does it support GraphQL code generation?

**Why This Matters**: GraphQL code generation creates type-safe queries, mutations, and subscriptions from GraphQL schemas. Manual GraphQL development lacks type safety and is repetitive.

**Decision Impact**: Nice-to-have for GraphQL-based APIs.

**Evidence to Look For**: GraphQL Codegen integration, schema-to-types generation, Apollo Client setup, GraphQL query scaffolding, type-safe hooks generation.

---

## 15. Code Generation Scope

### 15.1 Can it generate full applications from scratch?

**Why This Matters**: Full application generation (project structure, routing, state management, styling) creates production-ready starting points in minutes. Component-only generation requires manually setting up infrastructure.

**Decision Impact**: High priority for rapid prototyping and MVPs.

**Evidence to Look For**: Full-stack templates, end-to-end application examples, user testimonials about generating complete apps, demo videos showing app generation.

---

### 15.2 Can it generate complete features/modules?

**Why This Matters**: Feature generation (user management, blog system, dashboard) creates multiple interconnected files with consistent architecture. Single-file generation requires manual integration.

**Decision Impact**: High priority for feature development velocity.

**Evidence to Look For**: Multi-file feature generation, architectural consistency, examples of generated features (auth, CRUD, dashboards), feature template library.

---

### 15.3 Does it provide inline code completion?

**Why This Matters**: Inline completion (Copilot-style suggestions) accelerates coding by predicting next lines. Without inline completion, developers type everything manually.

**Decision Impact**: High priority for coding speed and productivity.

**Evidence to Look For**: Autocomplete demonstrations, inline suggestion screenshots, multi-line completion, context-aware suggestions, latency of suggestions.

---

### 15.4 Can it generate only UI components?

**Why This Matters**: UI component generation (buttons, forms, cards) with styling is useful for frontend-focused work. Enables rapid UI prototyping without full application generation.

**Decision Impact**: Nice-to-have for UI-focused development.

**Evidence to Look For**: Component library generation, styled component examples, Tailwind/CSS module support, component variant generation, Storybook integration.

---

### 15.5 Can it generate test files?

**Why This Matters**: Test generation creates unit tests, integration tests, and e2e tests, improving code quality and coverage. Manual test writing is time-consuming and often skipped.

**Decision Impact**: Nice-to-have for test-driven development.

**Evidence to Look For**: Test file generation, Jest/Vitest/Playwright integration, test coverage analysis, test-specific AI suggestions, mocking generation.

---

## 16. Extension Ecosystem

### 16.1 Does it support VS Code extensions?

**Why This Matters**: VS Code marketplace has 40k+ extensions for languages, frameworks, linters, formatters, themes, and productivity tools. Extension support means you can use your existing workflow tools.

**Decision Impact**: High priority for preserving existing workflows and tooling investments.

**Evidence to Look For**: "VS Code extensions compatible" statements, marketplace access, extension installation UI, compatibility percentage, known incompatible extensions list.

---

### 16.2 What percentage of VS Code marketplace works?

**Why This Matters**: Partial compatibility means some critical extensions may not work. 90%+ compatibility is good, 50% means many tools won't work. Quantifies extension ecosystem viability.

**Decision Impact**: Nice-to-have for understanding actual compatibility scope.

**Evidence to Look For**: Official compatibility statements, user reports of extension success/failure, tested extension lists, known issues documentation.

---

### 16.3 Can you install custom extensions?

**Why This Matters**: Custom extensions include proprietary company tools, beta extensions, or locally developed productivity tools. Installation capability enables full workflow customization.

**Decision Impact**: Nice-to-have for enterprise tooling and custom workflows.

**Evidence to Look For**: VSIX installation support, sideloading documentation, private extension hosting, extension development guides.

---

### 16.4 Does it have its own plugin system?

**Why This Matters**: Native plugin system enables tool-specific features that VS Code extensions can't provide. Indicates active ecosystem development and extensibility investment.

**Decision Impact**: Nice-to-have for future extensibility and ecosystem growth.

**Evidence to Look For**: Plugin API documentation, plugin marketplace, example plugins, plugin development tutorials, community plugin ecosystem.

---

### 16.5 Are popular extensions (ESLint, Prettier) supported?

**Why This Matters**: ESLint and Prettier are industry-standard for code quality and formatting. Support is essential for maintaining code standards and team consistency.

**Decision Impact**: Nice-to-have but nearly essential for professional development.

**Evidence to Look For**: ESLint integration examples, Prettier formatting, auto-fix on save, configuration file support, extension compatibility statements.

---

## 17. Pricing Model

### 17.1 Is there a free tier?

**Why This Matters**: Free tier enables evaluation, personal projects, open-source development, and small team usage without financial commitment. Trial-only means limited evaluation time.

**Decision Impact**: High priority for evaluation and small-scale usage.

**Evidence to Look For**: Free tier documentation, usage limits, feature restrictions, unlimited free tier vs trial period, student/OSS programs.

---

### 17.2 What is the monthly cost per developer?

**Why This Matters**: Per-developer cost determines budget impact for teams. $10/month is affordable, $50/month requires ROI justification, $100+/month needs strong business case.

**Decision Impact**: High priority for budgeting and cost-benefit analysis.

**Evidence to Look For**: Pricing page with per-seat costs, team/enterprise pricing, annual discount options, volume pricing, currency and regional pricing.

---

### 17.3 Is there enterprise licensing?

**Why This Matters**: Enterprise licensing provides volume discounts, dedicated support, SLAs, security reviews, and contract terms. Essential for large organization procurement processes.

**Decision Impact**: High priority for enterprise adoption.

**Evidence to Look For**: Enterprise tier documentation, contact sales options, contract terms, SLA guarantees, dedicated support, SSO/SAML support.

---

### 17.4 How is usage measured?

**Why This Matters**: Usage measurement affects cost predictability. Seat-based is predictable, token-based varies with usage, time-based penalizes heavy users. Understanding measurement enables cost planning.

**Decision Impact**: Nice-to-have for cost forecasting.

**Evidence to Look For**: Pricing model documentation, usage dashboards, overage charges, usage caps, metering documentation, billing transparency.

---

### 17.5 Are there usage limits on paid tiers?

**Why This Matters**: Usage limits (token caps, file count, API calls) on paid tiers can disrupt workflows when exceeded. Unlimited paid tiers provide predictable costs and uninterrupted usage.

**Decision Impact**: Nice-to-have for usage predictability.

**Evidence to Look For**: Tier comparison tables, usage limit documentation, overage pricing, throttling behavior, fair use policies.

---

## 18. Mobile Support

### 18.1 Can it generate native mobile apps?

**Why This Matters**: Native app generation (Swift/Kotlin or React Native/Flutter) enables building mobile applications. iOS+Android support provides full mobile coverage vs single-platform limitation.

**Decision Impact**: Nice-to-have unless mobile development is core requirement.

**Evidence to Look For**: React Native templates, Flutter support, native iOS/Android examples, mobile-specific component generation, platform-specific code.

---

### 18.2 Does it support React Native?

**Why This Matters**: React Native enables mobile apps using TypeScript/React knowledge. Shares code with web, leverages existing skills, unified codebase for web and mobile.

**Decision Impact**: Nice-to-have for TypeScript-focused teams doing mobile.

**Evidence to Look For**: React Native project creation, Expo integration, navigation libraries (React Navigation), native module integration, platform-specific code handling.

---

### 18.3 Can it generate responsive web apps?

**Why This Matters**: Responsive web apps work on mobile browsers without native apps. Faster to develop, easier to deploy, no app store requirements. Good mobile coverage for many use cases.

**Decision Impact**: Nice-to-have for mobile-friendly web applications.

**Evidence to Look For**: Responsive design examples, mobile-first CSS, Tailwind responsive utilities, viewport meta tags, touch interaction support.

---

### 18.4 Does it support Flutter?

**Why This Matters**: Flutter provides excellent performance and beautiful UIs for mobile apps. Dart language requirement, but strong for mobile-first applications.

**Decision Impact**: Nice-to-have for teams considering Flutter.

**Evidence to Look For**: Flutter project scaffolding, widget generation, Dart language support, Flutter packages, Material/Cupertino widgets.

---

### 18.5 Can it scaffold mobile-specific code?

**Why This Matters**: Mobile-specific code includes camera access, geolocation, push notifications, biometric auth. Platform-specific APIs require specialized scaffolding.

**Decision Impact**: Nice-to-have for feature-rich mobile applications.

**Evidence to Look For**: Camera integration, location services, notification setup, native module bridging, permission handling, platform APIs.

---

## 19. Performance Optimization

### 19.1 Does it provide optimization suggestions?

**Why This Matters**: Optimization suggestions identify performance issues (large bundles, render inefficiencies, memory leaks) and recommend fixes. Proactive performance improvement vs reactive debugging.

**Decision Impact**: Nice-to-have for performance-critical applications.

**Evidence to Look For**: Performance linting, bundle analysis suggestions, React re-render warnings, memory profiling, optimization recommendations.

---

### 19.2 Can it analyze bundle sizes?

**Why This Matters**: Bundle size analysis identifies large dependencies causing slow page loads. Enables data-driven optimization decisions and tracking bundle growth over time.

**Decision Impact**: Nice-to-have for web performance optimization.

**Evidence to Look For**: Bundle analyzer integration, dependency size reporting, tree-shaking effectiveness, chunk size visualization, size budget warnings.

---

### 19.3 Does it implement lazy loading automatically?

**Why This Matters**: Automatic lazy loading reduces initial bundle size by loading components/routes on-demand. Manual lazy loading is tedious and easy to forget.

**Decision Impact**: Nice-to-have for automatic performance best practices.

**Evidence to Look For**: Dynamic imports, React.lazy usage, route-based code splitting, image lazy loading, component-level splitting.

---

### 19.4 Does it support code splitting?

**Why This Matters**: Code splitting divides bundles into smaller chunks loaded as needed. Improves initial load time and perceived performance on large applications.

**Decision Impact**: Nice-to-have for large application performance.

**Evidence to Look For**: Route-based splitting, vendor chunk separation, dynamic imports, webpack/vite configuration, chunk optimization strategies.

---

### 19.5 Can it measure performance metrics?

**Why This Matters**: Performance measurement (Core Web Vitals, LCP, FID, CLS) provides objective performance data. Enables tracking performance over time and A/B testing optimizations.

**Decision Impact**: Nice-to-have for performance monitoring and optimization.

**Evidence to Look For**: Web Vitals integration, Lighthouse integration, performance monitoring setup, custom metrics, performance budgets.

---

## 20. Security & Compliance

### 20.1 Can it work in air-gapped/isolated environments?

**Why This Matters**: Air-gapped operation required for defense, finance, and high-security organizations. No external network access means tool must function completely offline including AI models.

**Decision Impact**: Deal-breaker for high-security and regulated environments.

**Evidence to Look For**: Air-gapped deployment guides, offline AI model support, no telemetry/phone-home, explicit isolation capability statements, government/defense customer case studies.

---

### 20.2 Does it scan for security vulnerabilities?

**Why This Matters**: Security scanning detects vulnerable dependencies, code injection risks, authentication flaws, and common security anti-patterns. Proactive security vs reactive incident response.

**Decision Impact**: High priority for security-conscious development.

**Evidence to Look For**: Dependency vulnerability scanning, SAST (static analysis), SQL injection detection, XSS prevention, secrets detection, CVE database integration.

---

### 20.3 Does it handle authentication scaffolding?

**Why This Matters**: Authentication scaffolding generates secure login, registration, password reset, and session management code. Reduces security implementation errors and saves development time.

**Decision Impact**: High priority for secure application development.

**Evidence to Look For**: Auth provider integration, JWT handling, session management, password hashing, OAuth flows, MFA setup, secure cookie handling.

---

### 20.4 Does it support GDPR compliance features?

**Why This Matters**: GDPR compliance requires data privacy controls, consent management, data deletion, and audit trails. Scaffolding reduces compliance implementation effort and legal risk.

**Decision Impact**: Nice-to-have for EU-facing applications.

**Evidence to Look For**: Consent management UI, data deletion endpoints, privacy policy templates, cookie banners, data export functionality, audit logging.

---

### 20.5 Does it have SOC2/ISO certification?

**Why This Matters**: SOC2/ISO certification demonstrates security controls, compliance processes, and third-party audits. Required for enterprise procurement and regulated industry sales.

**Decision Impact**: Nice-to-have for enterprise customer requirements.

**Evidence to Look For**: SOC2 Type II reports, ISO 27001 certification, security documentation, compliance page, audit reports, security questionnaire responses.

---

## Related Documents

- [decision-criteria.md](./decision-criteria.md) - 100 decision questions with comparison tables
- [evaluation-metrics.md](./evaluation-metrics.md) - 20 evaluation categories
- [evaluation-template.md](./evaluation-template.md) - Report structure and formatting
- [space-instructions.txt](./space-instructions.txt) - Workflow for conducting evaluations

---

## Change Log

### v1.0 (2026-02-04)
- Initial release
- Rationale for all 100 decision questions
- "Why This Matters" for each question
- "Decision Impact" assessments
- "Evidence to Look For" guidance
