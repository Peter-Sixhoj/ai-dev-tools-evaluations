# AI Development Tools Decision Rationale

**Version**: 3.0  
**Date Created**: 2026-02-04  
**Last Updated**: 2026-02-04  
**References**: decision-criteria.md v2.0, evaluation-metrics.md v2.0  
**Status**: Active

## Purpose

This document explains **why each decision question exists** and **what it evaluates**, independent of any specific project's priorities. This rationale is reusable across different projects with different prioritization schemes.

**Priority information belongs in `decision-criteria.md`**, not here. Different projects may assign different priorities to the same questions based on their specific needs.

## Organization

Questions are ordered by ID (1.1a, 1.1b, 1.2, ..., 21.3) for easy reference and lookup.

---

## 1. Deployment Model Questions

### 1.1a: Can the development environment be fully self-hosted?

**What This Evaluates**: Whether the IDE and AI processing can run entirely on your own infrastructure, or requires vendor services.

**Why It Matters**: Self-hosting provides data control, offline operation, and compliance benefits for high-security environments.

**Evidence to Look For**: 
- Self-hosted deployment options or documentation
- Docker containers or VM images
- No mandatory vendor services
- Community reports of on-premises deployments

---

### 1.1b: Can applications you build be deployed outside the product's platform?

**What This Evaluates**: Whether the applications you create can run on any infrastructure you choose, or only on the vendor's platform.

**Why It Matters**: Deployment flexibility determines your operational independence. Platform-locked deployment creates ongoing vendor dependency.

**Evidence to Look For**: 
- Exported code runs on AWS, GCP, Azure, on-premises
- No platform-specific deployment requirements
- Standard deployment processes (Docker, traditional hosting, serverless)
- User reports of diverse deployment targets

**Examples**:
- ✅ YES: Exports standard Next.js app deployable anywhere
- ⚠️ REQUIRES PLATFORM: Must deploy to vendor infrastructure
- ❌ NO: Only runs on vendor's hosted platform

---

### 1.2: Can the tool operate in completely air-gapped environments?

**What This Evaluates**: Whether the tool functions without any internet access, including for AI features.

**Why It Matters**: Air-gapped environments (high-security, classified, or disconnected networks) require complete offline capability.

**Answer Formats**:
- "Yes": Full offline support
- "Partial (internet for AI only)": Development works offline, AI requires internet
- "No": Requires internet

**Evidence to Look For**: 
- Documentation for offline operation
- No mandatory cloud API calls
- Local model support
- Community reports from disconnected environments

---

### 1.3: Can it run as a local desktop application?

**What This Evaluates**: Whether the tool is available as a native desktop application (not just web-based).

**Why It Matters**: Desktop applications provide lower latency, offline capability, better integration with local dev tools, and avoid browser limitations.

**Evidence to Look For**: 
- Desktop installers (Windows, macOS, Linux)
- Native application performance
- Offline functionality
- Local file system integration

---

### 1.4a: Where does the IDE/editor run?

**What This Evaluates**: The execution location of the user interface (editor).

**Answer Formats**:
- "Local (desktop)": Native application on user's machine
- "Cloud (browser)": Runs in web browser
- "Both": Offers both options

**Why It Matters**: Execution location affects responsiveness, offline capability, and integration with local tools.

---

### 1.4b: Where are AI features processed?

**What This Evaluates**: Where code generation and AI operations execute.

**Answer Formats**:
- "Local": AI runs on user's machine
- "Cloud API": AI provided by vendor's cloud service
- "Self-hosted option": User can host AI processing
- "Hybrid": Mix of local and cloud

**Why It Matters**: Processing location affects latency, data privacy, offline capability, and cost structure.

---

### 1.5: Is there a web-based version available?

**What This Evaluates**: Whether the tool offers browser-based access.

**Why It Matters**: Web versions enable quick access from any device without installation, useful for accessing from different machines.

---

## 2. Package Management Questions

### 2.1: Does it support npm package installation?

**What This Evaluates**: Can the tool create and work with projects using npm (Node Package Manager).

**Why It Matters**: npm is the standard for JavaScript/TypeScript projects. Essential for React, Vue, Next.js, and thousands of Node.js libraries.

**Answer Formats**: "Yes / Limited / No"

**Evidence to Look For**: 
- npm project creation
- package.json generation
- Dependency resolution
- Third-party package usage

---

### 2.2: Does it support cargo (Rust) packages?

**What This Evaluates**: Can the tool create and work with Rust projects using cargo.

**Why It Matters**: Cargo support enables Rust development with proper dependency management.

**Answer Formats**: "Yes / Limited / No"

**Evidence to Look For**: 
- Cargo.toml generation
- Rust project scaffolding
- Dependency resolution for Rust

---

### 2.3: Can it handle monorepo dependency structures?

**What This Evaluates**: Understanding of monorepo patterns (multiple projects with shared dependencies in single repo).

**Why It Matters**: Monorepos require special handling. Tools that don't understand monorepo structure provide incorrect suggestions and break builds.

**Answer Formats**: "Yes / Limited / No"

**Evidence to Look For**: 
- Workspace configuration support
- Cross-workspace dependency resolution
- Monorepo-aware linting and building
- User reports with monorepos

---

### 2.4: Does it support pip (Python) packages?

**What This Evaluates**: Can the tool create and work with Python projects using pip.

**Why It Matters**: pip is the standard for Python. Essential for data science, backends, and ML workflows.

**Answer Formats**: "Yes / Limited / No"

---

### 2.5: Are there restrictions on which packages can be used?

**What This Evaluates**: Whether all packages in registries (npm, PyPI, crates.io) are available, or only a curated list.

**Answer Formats**: 
- "Yes (restrictions exist)": Only certain approved packages
- "No (unrestricted)": Full access to all packages

**Why It Matters**: Package restrictions limit development options. Unrestricted access provides full development freedom.

---

## 3. Code Ownership & Portability Questions

### 3.1: Can you export 100% of generated code?

**What This Evaluates**: Whether all code created in the tool can be exported/downloaded.

**Why It Matters**: Incomplete exports mean lost work if you migrate tools. Export completeness is essential for code ownership.

**Answer Formats**: "Yes / No"

**Evidence to Look For**: 
- Export/download functionality
- User reports of completeness
- Documentation about exports
- Community discussions on missing exports

---

### 3.2: Does exported code avoid proprietary runtime dependencies?

**What This Evaluates**: Whether exported code uses only standard, open-source dependencies or requires vendor-specific SDKs.

**Why It Matters**: Proprietary dependencies create permanent vendor lock-in, even after exporting code.

**Answer Formats**: 
- "Yes": Only standard npm/cargo/pip packages
- "Requires vendor SDK": Needs vendor-specific library
- "No": Heavily vendor-dependent

**What Counts as Proprietary**:
- ❌ Vendor-specific runtime library required
- ❌ Hard-coded to vendor's services
- ⚠️ Vendor-preferred but swappable (e.g., Supabase client)
- ✅ Standard open-source packages

**Evidence to Look For**: 
- package.json / Cargo.toml contents
- Import statements in exported code
- User reports about dependencies
- Documentation about vendor SDKs

---

### 3.3: Is exported code in standard project format?

**What This Evaluates**: Whether exported code uses industry-standard structure (package.json, Cargo.toml, conventional directories).

**Why It Matters**: Standard formats mean immediate compatibility with industry tools and build processes.

**Answer Formats**: "Yes / No"

**Evidence to Look For**: 
- Standard directory structure
- package.json or equivalent
- No proprietary configuration formats
- Compatibility with build tools (webpack, Vite, cargo)

---

### 3.4: Can exported code run with zero modifications?

**What This Evaluates**: Whether code works immediately after export without any changes.

**Answer Formats**: 
- "Yes": `npm start` works immediately
- "Requires npm install only": Need dependency install but no code changes
- "Requires setup": Must modify config or code
- "No": Substantial changes needed

**Why It Matters**: Immediate execution means smooth transitions. Requiring modifications creates friction and delays.

---

### 3.5: Can you export project history/version control?

**What This Evaluates**: Whether Git history and commit logs are included in exports.

**Why It Matters**: Version history preserves development context and blame information.

**Answer Formats**: "Yes / No"

---

## 4. Framework Support Questions

### 4.1: Does it have first-class TypeScript support?

**What This Evaluates**: Level of TypeScript integration (type inference, autocomplete, refactoring).

**Answer Formats**: "Yes / Limited / No"

**What First-Class Means**:
- ✅ Full type inference
- ✅ Intelligent autocomplete
- ✅ TypeScript-aware refactoring
- ✅ Type error detection
- ⚠️ Limited: Syntax highlighting but limited type support

**Why It Matters**: First-class support enables type safety. Basic support leads to type errors and poor suggestions.

---

### 4.2: Does it support Rust with LSP integration (rust-analyzer)?

**What This Evaluates**: Level of Rust IDE support.

**Answer Formats**: 
- "Yes": Full rust-analyzer integration
- "Syntax only": Highlighting but no LSP
- "No": No Rust support

**Why It Matters**: LSP integration enables type checking and intelligent completion. Without it, Rust development is painful.

---

### 4.3: Does it support React/Next.js?

**What This Evaluates**: Level of React ecosystem support.

**Answer Formats**: "Yes / Limited / No"

**What Support Includes**:
- JSX/TSX generation
- Component best practices
- Next.js-specific features (routing, API routes)
- React hooks patterns

---

### 4.4: Does it support Python?

**What This Evaluates**: Level of Python support for backend, data science, or ML work.

**Answer Formats**: "Yes / Limited / No"

---

### 4.5: Does it support Go?

**What This Evaluates**: Level of Go support for microservices and backend work.

**Answer Formats**: "Yes / Limited / No"

---

### 4.6: Does it support Vue.js?

**What This Evaluates**: Level of Vue.js support for frontend development.

**Answer Formats**: "Yes / Limited / No"

---

### 4.7: Does it support Angular?

**What This Evaluates**: Level of Angular support for enterprise frontend development.

**Answer Formats**: "Yes / Limited / No"

---

## 5. Git Integration Questions

### 5.1: Does it have native Git integration?

**What This Evaluates**: Level of Git UI in the tool.

**Answer Formats**: 
- "Yes": Visual Git interface
- "CLI only": Must use terminal commands
- "No": No Git support

**Why It Matters**: Git UI enables version control without context switching.

---

### 5.2: Can you push directly to GitHub/GitLab?

**What This Evaluates**: Which Git hosting platforms are natively supported.

**Answer Formats**: 
- "Both": GitHub and GitLab support
- "GitHub only": Only GitHub integration
- "No": No native Git push

**Why It Matters**: Native push streamlines collaboration and CI/CD integration.

---

### 5.3: Does it support pull request workflows?

**What This Evaluates**: Can developers create, review, and merge pull requests within the tool.

**Answer Formats**: "Yes / No"

**Why It Matters**: PR workflows are standard for professional teams and code review.

---

### 5.4: Does it have a visual Git UI?

**What This Evaluates**: Whether Git operations have visual interface elements.

**Answer Formats**: "Yes / No"

**What This Includes**: File staging UI, commit history visualization, diff viewing, branch visualization.

---

### 5.5: Can it handle branch management?

**What This Evaluates**: Support for creating, switching, and managing branches.

**Answer Formats**: "Yes / Limited / No"

**Examples**:
- ✅ Full: Create, switch, merge, delete branches
- ⚠️ Limited: Create and switch, but not merge
- ❌ No: No branch management

---

## 6. Multi-file Context Awareness Questions

### 6.1: Can it understand relationships between files?

**What This Evaluates**: Whether AI understands how files depend on each other (imports, exports, cross-references).

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: File relationship understanding enables coherent suggestions across files.

---

### 6.2: Can it refactor across multiple files?

**What This Evaluates**: Can the tool rename variables, functions, or classes across the entire codebase.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Cross-file refactoring is essential for maintaining code consistency during changes.

---

### 6.3: What is the maximum AI context size?

**What This Evaluates**: How much code the AI can consider at once.

**Answer Formats**: Specify unit and value
- Examples: "200K tokens", "50 files", "10,000 LOC"

**Why It Matters**: Larger context enables understanding complex features spanning many files.

---

### 6.4: Does it maintain consistency when generating new files?

**What This Evaluates**: Whether AI-generated new files follow existing code patterns and style.

**Answer Formats**: "Yes / Sometimes / No"

**Why It Matters**: Consistency reduces refactoring and makes codebases maintainable.

---

### 6.5: Can it analyze entire codebase for suggestions?

**What This Evaluates**: Whether the tool can scan the full codebase and provide improvement suggestions.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Full codebase analysis enables finding and fixing issues systematically.

---

## 7. Backend Capabilities Questions

### 7.1: Which backend languages can it generate?

**What This Evaluates**: Supported backend programming languages.

**Answer Format**: List of languages
- Examples: "Node.js, Python, Go, Rust"

**Why It Matters**: Backend language support determines full-stack capability.

---

### 7.2: Can it create database schemas?

**What This Evaluates**: Whether the tool can generate database table definitions and migrations.

**Answer Formats**: "Yes / No"

**Why It Matters**: Schema generation accelerates database design and backend setup.

---

### 7.3: Does it support API generation (REST/GraphQL)?

**What This Evaluates**: Can the tool scaffold APIs in different styles.

**Answer Formats**: 
- "Both": REST and GraphQL
- "REST only": Only REST APIs
- "No": No API generation

**Why It Matters**: API generation is core to backend development.

---

### 7.4: Can it scaffold full-stack applications?

**What This Evaluates**: Complete frontend + backend + database project generation.

**Answer Formats**: 
- "Yes": Full-stack scaffolding
- "Frontend only": Only frontend
- "No": No scaffolding

**Why It Matters**: Full-stack scaffolding accelerates project creation.

---

### 7.5: Does frontend/backend integration work seamlessly?

**What This Evaluates**: Whether frontend and backend integrate without manual setup.

**Answer Formats**: 
- "Yes": Seamless integration
- "Manual setup": Requires configuration
- "No": Separate toolchains

**Why It Matters**: Seamless integration enables rapid full-stack development.

---

## 8. Collaboration Features Questions

### 8.1a: Does it support real-time multiplayer collaboration?

**What This Evaluates**: Can multiple developers edit simultaneously (like Google Docs).

**Answer Formats**: "Yes / No"

**Why It Matters**: Real-time collaboration enables simultaneous development without merge conflicts.

---

### 8.1b: Does it support Git-based collaboration workflows?

**What This Evaluates**: Can developers use traditional Git workflows (branches, PRs, code review).

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Git workflows are industry standard for professional teams.

---

### 8.2: Are there role-based permissions?

**What This Evaluates**: Can different team members have different access levels (viewer, editor, admin).

**Answer Formats**: "Yes / No"

**Why It Matters**: Permissions protect code and enforce review processes.

---

### 8.3: Can multiple developers work simultaneously?

**What This Evaluates**: Multiple concurrent users on the same project.

**Answer Formats**: "Yes / No"

**Why It Matters**: Parallel work accelerates development.

---

### 8.4: Does it support code review workflows?

**What This Evaluates**: Structured process for reviewing changes before merge.

**Answer Formats**: "Yes / No"

**Why It Matters**: Code review improves quality and prevents bugs.

---

### 8.5: Are there live cursors for real-time editing?

**What This Evaluates**: Visual indicators of other users' positions during real-time editing.

**Answer Formats**: "Yes / No"

**Why It Matters**: Live cursors prevent edit conflicts in real-time collaboration.

---

## 9. Deployment Automation Questions

### 9.1: Does it have built-in deployment automation?

**What This Evaluates**: Can the tool deploy applications automatically.

**Answer Formats**: "Yes / No"

**Why It Matters**: Built-in deployment reduces operational overhead.

---

### 9.2: Which platforms does it deploy to?

**What This Evaluates**: Supported deployment targets.

**Answer Format**: List of platforms
- Examples: "Vercel, Netlify, AWS, Heroku"

---

### 9.3: Does it support CI/CD pipeline integration?

**What This Evaluates**: Integration with GitHub Actions, GitLab CI, Jenkins, etc.

**Answer Formats**: "Yes / No"

**Why It Matters**: CI/CD integration enables automated testing and deployment.

---

### 9.4: Can it handle database migrations on deploy?

**What This Evaluates**: Automatic database schema updates during deployment.

**Answer Formats**: "Yes / No"

**Why It Matters**: Migration automation prevents manual database errors.

---

### 9.5: Is deployment configuration customizable?

**What This Evaluates**: Can developers customize deployment settings.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Customization enables complex deployment scenarios.

---

## 10. Local Development Support Questions

### 10.1: Can exported projects run using standard dev commands in any IDE?

**What This Evaluates**: Whether `npm start`, `cargo run`, or equivalent works outside the tool.

**Answer Formats**: 
- "Yes": Runs anywhere with standard commands
- "Requires tool IDE": Only works inside the tool
- "No": Cannot run externally

**Why It Matters**: Standard commands ensure IDE independence and onboard ability.

---

### 10.2: Does it work offline?

**What This Evaluates**: Can development continue without internet access.

**Answer Formats**: "Yes / Limited / No"

**Clarification**: 
- "Limited" means: Core development works, but AI/cloud features require internet

**Why It Matters**: Offline capability enables work anywhere (planes, disconnected networks, offline-first workflows).

---

### 10.3: Is local debugging supported?

**What This Evaluates**: Can developers debug code locally (breakpoints, step through, inspect).

**Answer Formats**: "Yes / No"

**Why It Matters**: Debugging is essential for efficient bug fixing.

---

### 10.4: Are there performance differences local vs cloud?

**What This Evaluates**: Whether cloud version is faster, slower, or equivalent to local.

**Answer Formats**: 
- "Same": Performance equivalent
- "Slower local": Cloud is faster
- "Faster local": Local is faster

**Why It Matters**: Understanding performance tradeoffs helps optimize workflow.

---

### 10.5: Can you use your own dev tools alongside it?

**What This Evaluates**: Whether the tool integrates with or interferes with other IDEs and tools.

**Answer Formats**: "Yes / No"

**Why It Matters**: Tool flexibility enables preserving existing workflows.

---

## 11. AI Model Selection Questions

### 11.1: Which AI models does it support?

**What This Evaluates**: Available AI models (GPT-4, Claude, Gemini, etc.).

**Answer Format**: List of models
- Examples: "GPT-4, Claude 3, Gemini"

---

### 11.2: Can you switch between models?

**What This Evaluates**: User ability to choose different AI models.

**Answer Formats**: "Yes / No"

**Why It Matters**: Model switching enables optimization and experimentation.

---

### 11.3: Can you bring your own API keys (BYOK)?

**What This Evaluates**: Whether users can provide their own OpenAI, Anthropic, etc. API keys.

**Answer Formats**: 
- "Yes": Full BYOK support
- "Enterprise only": BYOK available in enterprise tier
- "No": Vendor keys only

**Why It Matters**: BYOK enables cost control and compliance (data doesn't flow through vendor).

---

### 11.4: Is model selection transparent to users?

**What This Evaluates**: Can users know which model is being used for each operation.

**Answer Formats**: "Yes / No"

**Why It Matters**: Transparency aids debugging and understanding AI behavior.

---

### 11.5: Does it support local/open-source models?

**What This Evaluates**: Can use Llama, Mistral, or other local models.

**Answer Formats**: "Yes / No"

**Why It Matters**: Local models enable offline AI and full data privacy.

---

## 12. IDE Type Questions

### 12.1: What is the primary interface?

**What This Evaluates**: Main way users interact with the tool.

**Answer Formats**: 
- "Desktop IDE": Native application (Electron, etc.)
- "Web IDE": Browser-based
- "VS Code Extension": Extension in VS Code
- "CLI": Command-line interface

**Why It Matters**: Interface type determines workflow integration and user experience.

---

### 12.2: Is it based on VS Code?

**What This Evaluates**: Whether tool is built on VS Code codebase.

**Answer Formats**: 
- "Yes (fork)": Complete VS Code fork
- "Yes (extension)": VS Code extension
- "No": Separate implementation

**Why It Matters**: VS Code basis affects extension compatibility and familiarity.

---

### 12.3: Does it have terminal access?

**What This Evaluates**: Integrated terminal for running commands.

**Answer Formats**: "Yes / No"

**Why It Matters**: Terminal access enables full development workflow without context switching.

---

### 12.4: Can you customize the IDE?

**What This Evaluates**: Theme, layout, and feature customization.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Customization improves developer comfort and productivity.

---

### 12.5: Does it support keyboard shortcuts?

**What This Evaluates**: Keyboard-driven workflow support.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Keyboard shortcuts improve efficiency for power users.

---

## 13. Codebase Scale Limits Questions

### 13.1: What is the maximum total file count the tool can index?

**What This Evaluates**: How many files can the tool navigate and search.

**Answer Format**: Number or "Unlimited"
- Examples: "100,000 files", "Unlimited"

**Why It Matters**: File count limit determines if tool works with large codebases.

---

### 13.2: What is the AI context window?

**What This Evaluates**: How much code the AI can consider at once.

**Answer Format**: Specify unit and value
- Examples: "200K tokens", "50 files", "100K LOC"

**Why It Matters**: Larger context enables understanding complex multi-file features.

---

### 13.3: Has the tool been proven on enterprise-scale codebases?

**What This Evaluates**: Real-world validation on large projects (100K+ LOC).

**Answer Formats**: 
- "Yes (with evidence)": Documented use on large codebases
- "Likely": Probable but unconfirmed
- "No": No evidence of large-codebase use

**Why It Matters**: Enterprise validation provides confidence in scalability.

---

### 13.4: Does it support large monorepos?

**What This Evaluates**: Performance and usability with monorepo projects.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: Monorepo support is critical for organizations using monorepo architecture.

---

### 13.5: Are there performance degradation thresholds?

**What This Evaluates**: Known limits where performance declines.

**Answer Format**: Specify threshold
- Examples: "Slows at 50K files", "No known threshold"

**Why It Matters**: Knowing thresholds prevents unexpected performance issues.

---

## 14. API/Service Integration Questions

### 14.1: Can it scaffold Supabase integration?

**What This Evaluates**: Built-in support for setting up Supabase (PostgreSQL backend).

**Answer Formats**: 
- "Yes": Full scaffolding
- "Manual": Possible but requires manual setup
- "No": No Supabase support

**Why It Matters**: Supabase scaffolding accelerates backend setup.

---

### 14.2: Can it generate type-safe API clients?

**What This Evaluates**: Automatic generation of type-checked API clients from OpenAPI specs or similar.

**Answer Formats**: "Yes / No"

**Why It Matters**: Type-safe clients prevent API errors and improve IDE autocomplete.

---

### 14.3: Does it have templates for auth providers?

**What This Evaluates**: Pre-built patterns for common authentication systems (Auth0, Firebase, etc.).

**Answer Formats**: "Yes / No"

**Why It Matters**: Auth templates accelerate security implementation.

---

### 14.4: Can it integrate payment processors?

**What This Evaluates**: Support for payment systems (Stripe, PayPal, etc.).

**Answer Formats**: "Yes / No"

**Why It Matters**: Payment integration support accelerates commerce features.

---

### 14.5: Does it support GraphQL code generation?

**What This Evaluates**: Automatic generation of GraphQL queries, mutations, and types.

**Answer Formats**: "Yes / No"

**Why It Matters**: GraphQL code generation improves type safety and reduces boilerplate.

---

## 15. Code Generation Scope Questions

### 15.1: Can it generate full applications from scratch?

**What This Evaluates**: Complete project scaffolding from zero.

**Answer Formats**: "Yes / No"

**Why It Matters**: Full-app generation enables rapid prototyping.

---

### 15.2: Can it generate complete features/modules?

**What This Evaluates**: Multi-file feature generation.

**Answer Formats**: "Yes / No"

**Why It Matters**: Feature generation accelerates development beyond single files.

---

### 15.3: Does it provide inline code completion?

**What This Evaluates**: Suggestion completion while typing (like Copilot).

**Answer Formats**: "Yes / No"

**Why It Matters**: Inline completion improves coding speed.

---

### 15.4: Can it generate only UI components?

**What This Evaluates**: Component-level generation without full-stack.

**Answer Formats**: "Yes / No"

**Why It Matters**: Component generation is useful for frontend-focused workflows.

---

### 15.5: Can it generate test files?

**What This Evaluates**: Automatic test generation (unit, integration).

**Answer Formats**: "Yes / No"

**Why It Matters**: Test generation improves code coverage and quality.

---

## 16. Extension Ecosystem Questions

### 16.1: Does it support VS Code extensions?

**What This Evaluates**: Compatibility with VS Code marketplace extensions.

**Answer Formats**: "Yes / Limited / No"

**Why It Matters**: VS Code marketplace has 40k+ extensions; support preserves existing workflows.

---

### 16.2: What percentage of VS Code marketplace works?

**What This Evaluates**: Estimate of compatible extensions.

**Answer Format**: Percentage or "N/A"
- Examples: "90% compatible", "N/A" (not VS Code-based)

**Why It Matters**: Percentage indicates workflow compatibility.

---

### 16.3: Can you install custom extensions?

**What This Evaluates**: User ability to add plugins/extensions.

**Answer Formats**: "Yes / No"

**Why It Matters**: Custom extension support enables tool customization.

---

### 16.4: Does it have its own plugin system?

**What This Evaluates**: Native extension mechanism.

**Answer Formats**: "Yes / No"

**Why It Matters**: Plugin system enables community contributions and customization.

---

### 16.5: Are popular extensions supported (ESLint, Prettier)?

**What This Evaluates**: Compatibility with commonly-used tools.

**Answer Formats**: "Yes / Some / No"

**Why It Matters**: Popular extension support indicates production-readiness.

---

## 17. Pricing Model Questions

### 17.1: Is there a free tier?

**What This Evaluates**: Trial or free access for evaluation.

**Answer Formats**: 
- "Yes": Free tier available
- "Trial only": Time-limited trial
- "No": No free option

**Why It Matters**: Free tiers enable tool evaluation without commitment.

---

### 17.2: What is the monthly cost per developer?

**What This Evaluates**: Pricing structure and affordability.

**Answer Format**: $ amount or range
- Examples: "$20/month", "$50-200/month"

**Why It Matters**: Cost determines budget feasibility.

---

### 17.3: Is there enterprise licensing?

**What This Evaluates**: Volume discounts or special agreements.

**Answer Formats**: "Yes / No"

**Why It Matters**: Enterprise licensing enables large-scale adoption.

---

### 17.4: How is usage measured?

**What This Evaluates**: Pricing metric basis.

**Answer Format**: List metric types
- Examples: "Time, Tokens, Seats, Requests per month"

**Why It Matters**: Understanding pricing model enables cost forecasting.

---

### 17.5: Are there usage limits on paid tiers?

**What This Evaluates**: Caps on resource consumption.

**Answer Format**: Description or "No"
- Examples: "1000 tokens/month", "No limits"

**Why It Matters**: Usage limits affect total cost of ownership.

---

## 18. Mobile Support Questions

### 18.1: Can it generate native mobile apps?

**What This Evaluates**: iOS and Android app generation capability.

**Answer Formats**: 
- "iOS+Android": Both platforms
- "One platform": iOS or Android only
- "No": No mobile generation

**Why It Matters**: Mobile capability enables cross-platform development.

---

### 18.2: Does it support React Native?

**What This Evaluates**: React Native framework support.

**Answer Formats**: "Yes / No"

**Why It Matters**: React Native enables code sharing between iOS and Android.

---

### 18.3: Can it generate responsive web apps?

**What This Evaluates**: Mobile-responsive web application generation.

**Answer Formats**: "Yes / No"

**Why It Matters**: Responsive design is essential for web applications.

---

### 18.4: Does it support Flutter?

**What This Evaluates**: Flutter framework support.

**Answer Formats**: "Yes / No"

**Why It Matters**: Flutter enables high-performance cross-platform apps.

---

### 18.5: Can it scaffold mobile-specific code?

**What This Evaluates**: Mobile UX patterns and best practices.

**Answer Formats**: "Yes / No"

**Why It Matters**: Mobile-specific scaffolding improves UX.

---

## 19. Performance Optimization Questions

### 19.1: Does it provide optimization suggestions?

**What This Evaluates**: Performance analysis and recommendations.

**Answer Formats**: "Yes / No"

**Why It Matters**: Suggestions help identify performance issues.

---

### 19.2: Can it analyze bundle sizes?

**What This Evaluates**: JavaScript bundle analysis tools.

**Answer Formats**: "Yes / No"

**Why It Matters**: Bundle analysis identifies code bloat.

---

### 19.3: Does it implement lazy loading automatically?

**What This Evaluates**: Automatic code splitting and lazy imports.

**Answer Formats**: "Yes / No"

**Why It Matters**: Lazy loading reduces initial load time.

---

### 19.4: Does it support code splitting?

**What This Evaluates**: Automatic splitting of code into smaller chunks.

**Answer Formats**: "Yes / No"

**Why It Matters**: Code splitting reduces bundle sizes.

---

### 19.5: Can it measure performance metrics?

**What This Evaluates**: Integration with performance monitoring (Lighthouse, Web Vitals).

**Answer Formats**: "Yes / No"

**Why It Matters**: Metrics enable continuous performance tracking.

---

## 20. Security & Compliance Questions

### 20.2: Does it scan for security vulnerabilities?

**What This Evaluates**: Automated vulnerability detection.

**Answer Formats**: "Yes / No"

**Why It Matters**: Vulnerability scanning prevents security incidents.

---

### 20.3: Does it handle authentication scaffolding?

**What This Evaluates**: Automatic auth implementation (login, signup, sessions).

**Answer Formats**: "Yes / No"

**Why It Matters**: Auth scaffolding reduces security implementation errors.

---

### 20.4: Does it support GDPR compliance features?

**What This Evaluates**: Built-in GDPR compliance patterns (data export, deletion).

**Answer Formats**: "Yes / No"

**Why It Matters**: GDPR compliance is legally required for EU applications.

---

### 20.5: Does it have SOC2/ISO certification?

**What This Evaluates**: Third-party security audits.

**Answer Formats**: "Yes / No"

**Why It Matters**: Certifications provide assurance for enterprise use.

---

## 21. Team & Adoption Questions

### 21.1: What team sizes does it support well?

**What This Evaluates**: Optimal team scale for the tool.

**Answer Formats**: 
- "Solo": Best for individual developers
- "Small (2-10)": Best for small teams
- "Medium (10-50)": Best for medium teams
- "Enterprise (50+)": Best for large organizations

**Why It Matters**: Different tools have different team scaling characteristics.

---

### 21.2: What is the learning curve for developers familiar with VS Code?

**What This Evaluates**: Time to productivity for experienced developers.

**Answer Formats**: 
- "Minimal (< 1 day)": Quick adoption
- "Moderate (1-3 days)": Few days
- "Significant (1+ weeks)": Substantial learning period

**Why It Matters**: Learning curve affects team adoption time and productivity.

---

### 21.3: What is the vendor's funding/stability status?

**What This Evaluates**: Vendor viability and longevity.

**Answer Formats**: 
- "Public company": Established, low risk
- "Well-funded (Series B+)": Venture-backed, likely to continue
- "Early-stage": Startup, risk of shutdown
- "Open source": Community-driven

**Why It Matters**: Vendor stability determines long-term tool availability.

---

## Related Documents

- [decision-criteria.md](./decision-criteria.md) - Question definitions with **project-specific priorities**
- [evaluation-metrics.md](./evaluation-metrics.md) - 21 evaluation categories
- [evaluation-template.md](./evaluation-template.md) - How to structure evaluations

---

## Change Log

### v3.0 (2026-02-04)
- **MAJOR REFACTOR**: Reordered by question ID (1.1a, 1.1b, 1.2, ..., 21.3)
- **REMOVED** all priority information (MUST-HAVE, SHOULD-HAVE, NICE-TO-HAVE)
- **REMOVED** all rationale about priorities and project-specific decisions
- Pure rationale only: "Why does this question exist? What does it evaluate?"
- Made document reusable across projects with different prioritization schemes
- Clarified that priorities belong in decision-criteria.md, not here

### v2.0.1 (2026-02-04)
- Enhanced priority labels with text
- Organized by priority category

### v2.0 (2026-02-04)
- Updated rationale for all 4 CRITICAL questions
- Added rationale for split questions
- Updated priority explanations

### v1.0 (2026-02-04)
- Initial release
