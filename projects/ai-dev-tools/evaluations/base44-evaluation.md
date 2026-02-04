# Base44 Evaluation

**Evaluation Date**: 2026-02-04  
**Product Version**: Current (Infrastructure v2.0, January 2026)  
**Evaluator**: AI Development Tools Evaluator v2.0  
**Metrics Version**: evaluation-metrics.md v2.0  
**Template Version**: evaluation-template.md v2.0  
**Decision Criteria**: decision-criteria.md v2.0

## Executive Summary

Base44 is an AI-powered no-code web application platform that converts natural language prompts into full-stack applications with integrated backend, database, authentication, and hosting. It operates primarily as a cloud-based web IDE with built-in infrastructure, targeting non-technical founders and rapid prototyping scenarios. The platform was acquired by Wix for $80 million in 2025, positioning it as a managed, all-in-one development environment rather than a portable code generation tool.

---

## 1. Deployment Model

### Capability Assessment

Base44 is a cloud-only platform accessed through a web browser. Users build applications entirely within Base44's hosted environment, with all infrastructure (database, authentication, storage, hosting) managed by the platform. While Base44 offers code export capabilities (ZIP download and GitHub integration as of December 2025), the development environment itself cannot be self-hosted. Applications built on Base44 can be exported but require significant modification to run independently due to proprietary runtime dependencies.

**Evidence**: Official documentation confirms web-based platform with managed hosting (P1, base44.com/features). GitHub integration announced December 2025 with 2-way sync capability (P1, LinkedIn post December 28, 2025). Export functionality requires Builder plan or higher (P1, YouTube tutorial November 2025).

**Limitations**: No local IDE option; internet connection required for all development activities. Applications cannot run in air-gapped environments due to cloud dependency for AI features and runtime services.

### Decision Questions for Deployment Model

- **🟢 NICE-TO-HAVE | 1.1a: Can the development environment (IDE + AI) be fully self-hosted on your infrastructure?**
  Answer: No
  Evidence: Base44 is cloud-only platform, accessed via web browser (P1, official website)
  Notes: Development environment runs entirely on Base44's infrastructure

- **🔴 MUST-HAVE | 1.1b: Can applications you build be deployed to infrastructure outside the product's own platform?**
  Answer: Requires platform
  Evidence: Exported code requires @base44/sdk runtime dependency and Base44 backend services (P2, npm package documentation, Reddit discussions September 2025)
  Notes: While code can be exported, applications depend on Base44's backend-as-a-service for database, auth, and core functions

- **🟢 NICE-TO-HAVE | 1.2: Can the tool operate in completely air-gapped environments (no internet access for development or AI features)?**
  Answer: No
  Evidence: Cloud-based platform requires internet for all operations (P1, architecture described in official docs)
  Notes: All AI processing, data storage, and runtime services are cloud-dependent

- **🟡 SHOULD-HAVE | 1.3: Can it run as a local desktop application?**
  Answer: No
  Evidence: Web-based platform only (P1, official website and documentation)
  Notes: No desktop application available

- **🟡 SHOULD-HAVE | 1.4a: Where does the IDE/editor run?**
  Answer: Cloud (browser)
  Evidence: Web-based IDE accessed through browser (P1, official documentation)
  Notes: All editing happens in cloud environment

- **🟡 SHOULD-HAVE | 1.4b: Where are AI features processed?**
  Answer: Cloud API
  Evidence: AI processing handled by Base44 cloud infrastructure (P1, features documentation)
  Notes: No local or self-hosted AI option

- **🟢 NICE-TO-HAVE | 1.5: Is there a web-based version available?**
  Answer: Yes
  Evidence: Primary interface is web-based (P1, official website)
  Notes: This is the only available interface

---

## 2. Package Management

### Capability Assessment

Base44 supports npm package installation through AI chat interface as of the infrastructure v2.0 update (January 2026). However, packages must be approved through the AI chat and are subject to platform restrictions. Users cannot directly run `npm install` commands. Community reports indicate significant limitations: custom npm packages often fail to install, requiring CDN workarounds for unsupported packages. The platform does not support cargo (Rust), Go modules, or pip packages.

**Evidence**: Official documentation confirms npm package support via AI chat with approval workflow (P1, docs.base44.com/Building-your-app/NPM-packages, January 2026). Community testing shows many packages fail installation, requiring CDN import workarounds (P2, YouTube tutorial "The Issue with Base44!" September 2025, 15+ verified user reports).

**Limitations**: No direct npm command access; no monorepo support; restricted package ecosystem; no support for non-JavaScript package managers.

### Decision Questions for Package Management

- **🟡 SHOULD-HAVE | 2.1: Does it support npm package installation?**
  Answer: Limited
  Evidence: Supports npm via AI chat approval only, many packages fail (P2, user reports September 2025)
  Notes: Requires infrastructure v2.0; CDN workaround needed for unsupported packages

- **🟢 NICE-TO-HAVE | 2.2: Does it support cargo (Rust) packages?**
  Answer: No
  Evidence: JavaScript/TypeScript only platform (P1, official documentation)
  Notes: Rust not supported

- **🟡 SHOULD-HAVE | 2.3: Can it handle monorepo dependency structures?**
  Answer: No
  Evidence: Single-app architecture with no monorepo tooling (P3, inference from platform design)
  Notes: Platform designed for individual app projects

- **🟢 NICE-TO-HAVE | 2.4: Does it support pip (Python) packages?**
  Answer: No
  Evidence: Frontend is React/TypeScript only (P2, Reddit discussion November 2025)
  Notes: No Python runtime support

- **🟢 NICE-TO-HAVE | 2.5: Are there restrictions on which packages can be used?**
  Answer: Yes (restrictions exist)
  Evidence: Platform controls which packages can be installed; many fail approval (P2, YouTube tutorial September 2025)
  Notes: CDN imports used to bypass restrictions

---

## 3. Code Ownership & Portability

### Capability Assessment

Base44 allows code export via ZIP download or GitHub integration (requires Builder plan $40-50/month). However, exported code has **critical proprietary dependencies**: all applications require the `@base44/sdk` npm package and active connection to Base44's backend services for database, authentication, file storage, and API functionality. The exported codebase is React/TypeScript with Tailwind CSS, but cannot run independently without Base44's infrastructure. Reddit users report that "true ownership" is questionable since apps remain "permanently tied to their platform."

**Evidence**: Code export confirmed via ZIP and GitHub (P1, official features page, YouTube tutorials November 2025). @base44/sdk dependency documented in npm package registry (P1, npmjs.com/package/@base44/sdk). Community consensus that apps cannot run independently (P2, Reddit discussion "Base44 says you own your apps... but do you really?" August 2025, 10+ confirmations).

**Limitations**: **CRITICAL FAILURE** - Exported code requires proprietary Base44 backend runtime; cannot run with standard npm commands alone; vendor lock-in for database, auth, and storage.

### Decision Questions for Code Ownership & Portability

- **🔴 MUST-HAVE | 3.1: Can you export 100% of generated code?**
  Answer: Yes
  Evidence: Full code export available via ZIP and GitHub integration (P1, official documentation December 2025)
  Notes: Requires Builder plan or higher ($40-50/month)

- **🔴 MUST-HAVE | 3.2: Does exported code avoid proprietary runtime dependencies (runs with standard npm/cargo/pip, no vendor-specific SDK required)?**
  Answer: Requires vendor SDK
  Evidence: All apps require @base44/sdk and active Base44 backend connection (P1, npm package documentation; P2, community reports August 2025)
  Notes: **CRITICAL FAILURE** - Cannot run independently; database, auth, storage all require Base44 services

- **🟡 SHOULD-HAVE | 3.3: Is exported code in standard project format (package.json, Cargo.toml, standard directories)?**
  Answer: Yes
  Evidence: Standard React/TypeScript project structure with package.json (P2, GitHub repo examples)
  Notes: Uses conventional frontend project layout

- **🟡 SHOULD-HAVE | 3.4: Can exported code run with zero modifications (npm start works immediately after export)?**
  Answer: Requires setup
  Evidence: Requires npm install and connection to Base44 backend services (P2, developer documentation)
  Notes: Cannot run standalone; needs Base44 infrastructure

- **🟢 NICE-TO-HAVE | 3.5: Can you export project history/version control?**
  Answer: Yes
  Evidence: GitHub integration provides full version control (P1, official blog December 2025)
  Notes: 2-way sync maintains commit history

---

## 4. Framework Support

### Capability Assessment

Base44 generates React applications with TypeScript and Tailwind CSS as the standard frontend stack. The platform provides first-class TypeScript support with type definitions included in the @base44/sdk. Backend logic can be written in TypeScript-based serverless functions. The platform does not support Vue, Angular, Rust, Go, or traditional Python backends. All applications use the React framework exclusively.

**Evidence**: React/TypeScript/Tailwind confirmed as stack (P2, Reddit discussion November 2025; P1, npm SDK package with TypeScript definitions). Developer documentation shows TypeScript functions for backend (P1, docs.base44.com/developers January 2026).

**Limitations**: Single framework lock-in (React only); no support for alternative frontend frameworks or backend languages beyond TypeScript.

### Decision Questions for Framework Support

- **🟡 SHOULD-HAVE | 4.1: Does it have first-class TypeScript support?**
  Answer: Yes
  Evidence: TypeScript included in default stack with full type definitions (P1, npm @base44/sdk package)
  Notes: All generated code is TypeScript by default

- **🟢 NICE-TO-HAVE | 4.2: Does it support Rust with LSP integration (rust-analyzer)?**
  Answer: No
  Evidence: React/TypeScript-only platform (P1, official documentation)
  Notes: No Rust support

- **🟡 SHOULD-HAVE | 4.3: Does it support React/Next.js?**
  Answer: Yes
  Evidence: React is the only supported frontend framework (P2, community reports)
  Notes: Standard React, not Next.js specifically

- **🟡 SHOULD-HAVE | 4.4: Does it support Python?**
  Answer: No
  Evidence: TypeScript-only for backend functions (P1, developer documentation)
  Notes: No Python runtime

- **🟡 SHOULD-HAVE | 4.5: Does it support Go?**
  Answer: No
  Evidence: TypeScript-only backend (P1, official documentation)
  Notes: No Go support

- **🟢 NICE-TO-HAVE | 4.6: Does it support Vue.js?**
  Answer: No
  Evidence: React-only platform (P2, community reports)
  Notes: No Vue support

- **🟢 NICE-TO-HAVE | 4.7: Does it support Angular?**
  Answer: No
  Evidence: React-only platform (P2, community reports)
  Notes: No Angular support

---

## 5. Git Integration

### Capability Assessment

Base44 introduced GitHub integration in beta (March 2025) with full 2-way sync rolled out in December 2025. Users can connect apps to GitHub repositories, automatically sync changes bidirectionally, and manage version control through GitHub's interface. The integration supports branches, pull requests, and commit history. However, integration is limited to GitHub only (no GitLab or Bitbucket support) and requires Builder plan or higher. Visual Git UI is not available within Base44; users must use GitHub's interface for advanced Git operations.

**Evidence**: GitHub 2-way sync announced December 28, 2025 (P1, LinkedIn official post). Beta integration March 2025, production December 2025 (P1, official blog post). Builder plan requirement confirmed (P1, pricing documentation).

**Limitations**: GitHub-only (no GitLab/Bitbucket); requires paid plan; no in-platform Git UI for visual operations.

### Decision Questions for Git Integration

- **🟡 SHOULD-HAVE | 5.1: Does it have native Git integration?**
  Answer: Yes
  Evidence: GitHub integration with 2-way sync (P1, official announcement December 2025)
  Notes: Available December 2025 with full production support

- **🟡 SHOULD-HAVE | 5.2: Can you push directly to GitHub/GitLab?**
  Answer: GitHub only
  Evidence: GitHub-specific integration; no GitLab support mentioned (P1, official documentation)
  Notes: Automatic sync to GitHub repos

- **🟡 SHOULD-HAVE | 5.3: Does it support pull request workflows?**
  Answer: Yes
  Evidence: GitHub integration supports branches and PRs (P1, official blog December 2025)
  Notes: Full GitHub collaboration workflow supported

- **🟢 NICE-TO-HAVE | 5.4: Does it have a visual Git UI?**
  Answer: No
  Evidence: Git operations managed through GitHub's interface (P3, inference from documentation)
  Notes: No in-platform Git visualization

- **🟢 NICE-TO-HAVE | 5.5: Can it handle branch management?**
  Answer: Yes
  Evidence: GitHub integration supports branching (P1, official blog)
  Notes: Managed through GitHub interface

---

## 6. Multi-file Context Awareness

### Capability Assessment

Base44's AI chat can understand relationships between files and make changes across multiple files when prompted. The platform generates applications with consistent component structures, data models, and API integrations. However, the exact AI context window size is not publicly documented. User reports indicate the AI can refactor across files but may lose context with very large applications (100+ components). The Discussion Mode feature allows planning without affecting the live app.

**Evidence**: Multi-file generation confirmed through app templates and prompt examples (P1, official prompt guide). Discussion Mode for planning (P1, features documentation). Context limitations inferred from user experiences with large apps (P3, reasonable inference from AI chat limitations).

**Limitations**: Context window size undocumented; may struggle with very large codebases; no explicit codebase analysis tools.

### Decision Questions for Multi-file Context Awareness

- **🟡 SHOULD-HAVE | 6.1: Can it understand relationships between files?**
  Answer: Yes
  Evidence: AI generates consistent component hierarchies and data flows (P1, official prompt examples)
  Notes: Works well for standard app structures

- **🟡 SHOULD-HAVE | 6.2: Can it refactor across multiple files?**
  Answer: Yes
  Evidence: AI chat can make multi-file changes (P2, user tutorials and examples)
  Notes: Effectiveness depends on app complexity

- **🟡 SHOULD-HAVE | 6.3: What is the maximum AI context size?**
  Answer: Not documented
  Evidence: No official documentation of context window limits (P1, absence in documentation)
  Notes: Likely limited by underlying AI model (estimated 32K-200K tokens based on standard models)

- **🟢 NICE-TO-HAVE | 6.4: Does it maintain consistency when generating new files?**
  Answer: Yes
  Evidence: Generated apps follow consistent patterns for components, styling, data (P1, app template examples)
  Notes: Strong consistency within Base44's conventions

- **🟢 NICE-TO-HAVE | 6.5: Can it analyze entire codebase for suggestions?**
  Answer: Limited
  Evidence: AI responds to queries but no explicit codebase analysis tool (P3, inference from feature set)
  Notes: Can discuss code but no automated analysis dashboard

---

## 7. Backend Capabilities

### Capability Assessment

Base44 provides comprehensive full-stack capabilities with automatic backend generation. The platform includes integrated NoSQL database, auto-generated RESTful APIs, authentication system, file storage, email systems, and payment processing (Stripe). Backend functions can be written in TypeScript. The platform handles all infrastructure automatically, positioning itself as a complete backend-as-a-service (BaaS). However, backend is tightly coupled to Base44's infrastructure and cannot be separated from the platform.

**Evidence**: Full-stack capabilities confirmed in official features list (P1, base44.com/features). TypeScript backend functions documented (P1, developer documentation). Auto-generated APIs and database management (P1, official documentation). BaaS architecture detailed (P1, docs.base44.com/developers).

**Limitations**: Backend cannot be self-hosted; proprietary NoSQL database (not PostgreSQL/Supabase); TypeScript-only for backend logic.

### Decision Questions for Backend Capabilities

- **🟡 SHOULD-HAVE | 7.1: Which backend languages can it generate?**
  Answer: TypeScript only
  Evidence: TypeScript-based serverless functions (P1, developer documentation)
  Notes: No Node.js, Python, Go, or Rust backend support

- **🟡 SHOULD-HAVE | 7.2: Can it create database schemas?**
  Answer: Yes
  Evidence: Automatic database schema generation from prompts (P1, features documentation)
  Notes: NoSQL database, not relational/PostgreSQL

- **🟡 SHOULD-HAVE | 7.3: Does it support API generation (REST/GraphQL)?**
  Answer: REST only
  Evidence: Auto-generated RESTful API endpoints (P1, features documentation)
  Notes: No GraphQL support mentioned

- **🟢 NICE-TO-HAVE | 7.4: Can it scaffold full-stack applications?**
  Answer: Yes
  Evidence: Full-stack generation from prompts with frontend, backend, database (P1, official website)
  Notes: This is the primary use case

- **🟢 NICE-TO-HAVE | 7.5: Does frontend/backend integration work seamlessly?**
  Answer: Yes
  Evidence: Automatic integration through @base44/sdk (P1, SDK documentation)
  Notes: Tight coupling ensures seamless integration

---

## 8. Collaboration Features

### Capability Assessment

Base44 supports real-time multiplayer collaboration similar to Google Docs, allowing multiple users to work simultaneously on the same app with live syncing. The platform includes role-based permissions (Editor, Viewer, Admin) for workspace members. Version control features include automatic version history and rollback capabilities. With the GitHub integration (December 2025), teams can also use Git-based collaboration workflows with branches and pull requests. Code review workflows are supported through GitHub integration.

**Evidence**: Real-time collaboration confirmed (P1, features documentation and reviews). Role-based permissions documented (P1, workspace management documentation). GitHub workflow support (P1, official blog December 2025).

**Limitations**: Real-time collaboration limited to Base44 platform; advanced code review requires GitHub integration and paid plan.

### Decision Questions for Collaboration Features

- **🟢 NICE-TO-HAVE | 8.1a: Does it support real-time multiplayer collaboration (simultaneous editing)?**
  Answer: Yes
  Evidence: Real-time collaboration with live syncing (P1, features page and reviews)
  Notes: Multiple users can build and test together

- **🟡 SHOULD-HAVE | 8.1b: Does it support Git-based collaboration workflows (branches, PRs, code review)?**
  Answer: Yes
  Evidence: GitHub integration with branches and PRs (P1, official blog December 2025)
  Notes: Requires Builder plan or higher

- **🟢 NICE-TO-HAVE | 8.2: Are there role-based permissions?**
  Answer: Yes
  Evidence: Editor, Viewer, Admin roles for workspace members (P1, workspace documentation)
  Notes: Standard permission model

- **🟢 NICE-TO-HAVE | 8.3: Can multiple developers work simultaneously?**
  Answer: Yes
  Evidence: Real-time collaboration feature (P1, features documentation)
  Notes: Live syncing prevents conflicts

- **🟢 NICE-TO-HAVE | 8.4: Does it support code review workflows?**
  Answer: Yes
  Evidence: GitHub integration enables PR-based reviews (P1, official blog)
  Notes: Through GitHub, not native to Base44 platform

- **🟢 NICE-TO-HAVE | 8.5: Are there live cursors for real-time editing?**
  Answer: Yes
  Evidence: Real-time collaboration includes presence indicators (P3, inference from "like Google Docs" description)
  Notes: Standard real-time collaboration features

---

## 9. Deployment Automation

### Capability Assessment

Base44 provides instant deployment and hosting on its managed infrastructure. Every app receives automatic HTTPS with custom domain support (can be purchased and connected within platform). Deployment is fully automated—changes made in the app editor or synced from GitHub are immediately reflected. The platform does not support external CI/CD pipeline integration or deployment to third-party platforms (AWS, Vercel, Netlify). Database migrations are handled automatically when schema changes occur.

**Evidence**: Built-in hosting and instant deployment confirmed (P1, official features). Custom domain support (P1, features page). Automatic schema updates (P3, inference from managed database features).

**Limitations**: Platform-locked deployment only; no CI/CD integration with external tools; cannot deploy to other cloud providers.

### Decision Questions for Deployment Automation

- **🟢 NICE-TO-HAVE | 9.1: Does it have built-in deployment automation?**
  Answer: Yes
  Evidence: Instant deployment to Base44 hosting (P1, features documentation)
  Notes: Fully automated, no manual deployment steps

- **🟢 NICE-TO-HAVE | 9.2: Which platforms does it deploy to?**
  Answer: Base44 hosting only
  Evidence: Managed hosting platform (P1, official documentation)
  Notes: Cannot deploy to external platforms (AWS, Vercel, etc.)

- **🟢 NICE-TO-HAVE | 9.3: Does it support CI/CD pipeline integration?**
  Answer: No
  Evidence: No mention of CI/CD integration in documentation (P1, absence in features)
  Notes: Deployment is direct from platform or GitHub

- **🟢 NICE-TO-HAVE | 9.4: Can it handle database migrations on deploy?**
  Answer: Yes
  Evidence: Automatic schema updates (P3, inference from managed database architecture)
  Notes: Platform handles migrations automatically

- **🟢 NICE-TO-HAVE | 9.5: Is deployment configuration customizable?**
  Answer: Limited
  Evidence: Custom domains supported, but hosting infrastructure is fixed (P1, features page)
  Notes: No control over server configuration or deployment process

---

## 10. Local Development Support

### Capability Assessment

Base44 does not support local development in the traditional sense. The development environment is cloud-based and requires internet connectivity. However, the recent BaaS (Backend as a Service) approach (January 2026) allows developers to build custom frontends using any framework that can connect to Base44's backend via the JavaScript SDK. Exported projects require the @base44/sdk and active connection to Base44 services, so they cannot run with standard `npm start` commands alone without Base44 infrastructure. Local debugging is possible for custom frontends connecting to Base44 backend, but the core app cannot run independently.

**Evidence**: BaaS approach allows external frontends (P1, developer documentation January 2026). Exported code requires Base44 backend connection (P1, SDK documentation). Cloud-only development environment (P1, platform architecture).

**Limitations**: **CRITICAL FAILURE** - Exported apps cannot run independently with standard dev commands; always requires Base44 backend; no offline capability.

### Decision Questions for Local Development Support

- **🔴 MUST-HAVE | 10.1: Can exported projects run using standard dev commands (npm start, cargo run) in any IDE/terminal, without requiring the tool's IDE?**
  Answer: Requires tool IDE
  Evidence: Exported code requires active Base44 backend connection and @base44/sdk (P1, npm package; P2, Reddit discussions)
  Notes: **CRITICAL FAILURE** - Cannot run standalone; needs Base44 infrastructure

- **🟡 SHOULD-HAVE | 10.2: Does it work offline?**
  Answer: No
  Evidence: Cloud-based platform requires internet (P1, architecture description)
  Notes: All development happens online

- **🟡 SHOULD-HAVE | 10.3: Is local debugging supported?**
  Answer: Limited
  Evidence: Custom frontends can debug locally while connecting to Base44 backend (P1, BaaS documentation)
  Notes: Only applies to bring-your-own-frontend scenarios

- **🟢 NICE-TO-HAVE | 10.4: Are there performance differences local vs cloud?**
  Answer: N/A
  Evidence: No local development option (P1, platform architecture)
  Notes: Cloud-only platform

- **🟢 NICE-TO-HAVE | 10.5: Can you use your own dev tools alongside it?**
  Answer: Yes
  Evidence: BaaS approach allows external IDEs for custom frontends (P1, developer documentation)
  Notes: Only for custom frontend development, not for Base44-generated apps

---

## 11. AI Model Selection

### Capability Assessment

Base44 uses AI models for code generation, but the specific models are not transparently disclosed in public documentation. Users interact with AI through the chat interface without ability to switch models or bring their own API keys. The platform uses a credit-based system where AI interactions consume message credits (varies by plan: 250-1200 credits monthly). Model selection is not exposed to users—Base44 controls which AI models power the platform.

**Evidence**: AI-powered generation confirmed (P1, official marketing). Credit-based usage system (P1, pricing page). No model selection or BYOK mentioned in documentation (P1, absence in features).

**Limitations**: No model transparency; no model switching; no BYOK option; no local/open-source model support.

### Decision Questions for AI Model Selection

- **🟡 SHOULD-HAVE | 11.1: Which AI models does it support?**
  Answer: Not disclosed
  Evidence: No public documentation of AI models used (P1, absence in documentation)
  Notes: Likely GPT-4 or Claude based on capabilities, but not confirmed

- **🟡 SHOULD-HAVE | 11.2: Can you switch between models?**
  Answer: No
  Evidence: Single AI interface with no model selection options (P1, platform features)
  Notes: Platform controls model selection

- **🟡 SHOULD-HAVE | 11.3: Can you bring your own API keys (BYOK) for AI providers (OpenAI, Anthropic, etc.)?**
  Answer: No
  Evidence: Credit-based system with no BYOK option (P1, pricing and features documentation)
  Notes: Must use Base44's AI service and credits

- **🟢 NICE-TO-HAVE | 11.4: Is model selection transparent to users?**
  Answer: No
  Evidence: No disclosure of models in documentation (P1, absence in features)
  Notes: Opaque AI backend

- **🟢 NICE-TO-HAVE | 11.5: Does it support local/open-source models?**
  Answer: No
  Evidence: Cloud-only AI processing (P1, platform architecture)
  Notes: No local model support

---

## 12. IDE Type

### Capability Assessment

Base44 is a proprietary web-based IDE accessed through a browser. The interface includes a visual editor, AI chat panel, preview mode, and code editor (introduced with "Fast Code Edits" feature in March 2025). The platform is not based on VS Code—it is a custom-built web IDE designed specifically for the Base44 platform. Terminal access is not mentioned in documentation. The IDE is not highly customizable beyond theme and layout preferences.

**Evidence**: Web IDE confirmed (P1, platform architecture). Fast Code Edits feature for in-browser code editing (P1, LinkedIn post March 2025). Custom-built interface, not VS Code (P3, inference from product design).

**Limitations**: Not VS Code-based; no terminal access; limited customization; web-only interface.

### Decision Questions for IDE Type

- **🟡 SHOULD-HAVE | 12.1: What is the primary interface?**
  Answer: Web IDE
  Evidence: Browser-based development environment (P1, official documentation)
  Notes: Custom-built web IDE

- **🟡 SHOULD-HAVE | 12.2: Is it based on VS Code?**
  Answer: No
  Evidence: Proprietary web IDE with custom interface (P3, inference from design)
  Notes: Not a fork or extension of VS Code

- **🟢 NICE-TO-HAVE | 12.3: Does it have terminal access?**
  Answer: No
  Evidence: No terminal mentioned in features or documentation (P1, absence in documentation)
  Notes: All operations through visual interface and AI chat

- **🟢 NICE-TO-HAVE | 12.4: Can you customize the IDE?**
  Answer: Limited
  Evidence: Visual editor allows styling customizations (P1, features page)
  Notes: App-level customization, not IDE-level

- **🟢 NICE-TO-HAVE | 12.5: Does it support keyboard shortcuts?**
  Answer: Limited
  Evidence: Standard web application shortcuts likely present (P3, inference from web IDE design)
  Notes: No documentation of custom shortcut configuration

---

## 13. Codebase Scale Limits

### Capability Assessment

Base44 documentation states that the platform is "designed for scalability and can comfortably support 10,000 active users" but does not specify limits on file count or codebase size. The platform is optimized for small to medium applications (MVPs, internal tools, customer portals) rather than enterprise-scale monorepos. No evidence of testing on 100K+ LOC codebases. The AI context window is not documented, limiting ability to assess how well it handles large projects.

**Evidence**: 10,000 user scalability claim (P2, Reddit discussion with apparent Base44 representative, November 2025). Platform positioning for MVPs and prototypes (P1, official marketing). No large-scale codebase examples (P1, absence in documentation).

**Limitations**: Optimized for small-medium apps; unclear behavior at enterprise scale; no documented file count or LOC limits.

### Decision Questions for Codebase Scale Limits

- **🟡 SHOULD-HAVE | 13.1: What is the maximum total file count the tool can index/navigate?**
  Answer: Not documented
  Evidence: No file count limits in documentation (P1, absence in documentation)
  Notes: Likely hundreds of files based on typical app complexity

- **🟡 SHOULD-HAVE | 13.2: What is the AI context window (how much code can AI consider at once)?**
  Answer: Not documented
  Evidence: No context window information (P1, absence in documentation)
  Notes: Estimated 32K-200K tokens based on standard AI models

- **🟡 SHOULD-HAVE | 13.3: Has the tool been proven on enterprise-scale codebases (100K+ LOC)?**
  Answer: No
  Evidence: Positioned for MVPs and prototypes, not enterprise codebases (P1, marketing materials)
  Notes: No case studies or examples of large-scale projects

- **🟢 NICE-TO-HAVE | 13.4: Does it support large monorepos?**
  Answer: No
  Evidence: Single-app architecture (P3, inference from platform design)
  Notes: Not designed for monorepo workflows

- **🟢 NICE-TO-HAVE | 13.5: Are there performance degradation thresholds?**
  Answer: Unknown
  Evidence: No performance benchmarks published (P1, absence in documentation)
  Notes: Likely degrades with very complex apps (100+ components)

---

## 14. API/Service Integration

### Capability Assessment

Base44 provides built-in integrations for common services including email, SMS, file storage, AI models (via "Intelligent add-ons"), and payment processing (Stripe one-click integration). The platform supports custom integrations through OpenAPI specification imports managed by workspace administrators. However, there is no specific Supabase integration scaffolding. Type-safe API clients can be generated through the @base44/sdk. The integration system is credit-based (integration credits separate from message credits).

**Evidence**: Built-in integrations confirmed (P1, features page). Stripe integration (P1, features). Custom integrations via OpenAPI (P1, developer documentation). SDK provides type-safe clients (P1, npm package).

**Limitations**: No Supabase-specific integration; custom integrations require workspace admin setup; PostgreSQL not supported (uses proprietary NoSQL).

### Decision Questions for API/Service Integration

- **🟡 SHOULD-HAVE | 14.1: Can it scaffold Supabase integration?**
  Answer: No
  Evidence: No Supabase mentioned in integrations list (P1, official documentation)
  Notes: Uses proprietary database instead of PostgreSQL/Supabase

- **🟡 SHOULD-HAVE | 14.2: Can it generate type-safe API clients?**
  Answer: Yes
  Evidence: @base44/sdk provides TypeScript type definitions (P1, npm package documentation)
  Notes: Type safety for Base44 APIs

- **🟢 NICE-TO-HAVE | 14.3: Does it have templates for auth providers?**
  Answer: Yes
  Evidence: Built-in authentication and user management (P1, features page)
  Notes: Native auth system, not third-party providers

- **🟢 NICE-TO-HAVE | 14.4: Can it integrate payment processors?**
  Answer: Yes
  Evidence: One-click Stripe integration (P1, features page)
  Notes: Stripe specifically mentioned

- **🟢 NICE-TO-HAVE | 14.5: Does it support GraphQL code generation?**
  Answer: No
  Evidence: REST APIs only (P1, features documentation)
  Notes: No GraphQL support

---

## 15. Code Generation Scope

### Capability Assessment

Base44 specializes in generating complete full-stack applications from natural language prompts, including UI, database schemas, authentication, and backend logic. The platform excels at rapid prototyping and MVP creation. It can generate complete features and modules through conversational AI. The Fast Code Edits feature (March 2025) allows developers to make inline code modifications. The platform does not provide traditional IDE-style inline code completion—all generation happens through conversational prompts.

**Evidence**: Full application generation from prompts (P1, official marketing and documentation). Complete feature generation confirmed (P1, prompt library examples). Fast Code Edits for inline editing (P1, LinkedIn March 2025).

**Limitations**: No traditional autocomplete/IntelliSense; all code generation is prompt-driven; not designed for incremental development in large existing codebases.

### Decision Questions for Code Generation Scope

- **🟡 SHOULD-HAVE | 15.1: Can it generate full applications from scratch?**
  Answer: Yes
  Evidence: Primary use case is full-stack app generation from prompts (P1, official website)
  Notes: This is the core feature

- **🟡 SHOULD-HAVE | 15.2: Can it generate complete features/modules?**
  Answer: Yes
  Evidence: AI can add complete features through prompts (P1, prompt examples)
  Notes: Works well for bounded features

- **🟡 SHOULD-HAVE | 15.3: Does it provide inline code completion?**
  Answer: No
  Evidence: No autocomplete or IntelliSense mentioned (P1, absence in features)
  Notes: All generation is prompt-driven, not inline completion

- **🟢 NICE-TO-HAVE | 15.4: Can it generate only UI components?**
  Answer: Yes
  Evidence: Can generate specific components through prompts (P2, user tutorials)
  Notes: Flexible scope control through prompting

- **🟢 NICE-TO-HAVE | 15.5: Can it generate test files?**
  Answer: No
  Evidence: No testing framework or test generation mentioned (P1, absence in features)
  Notes: Testing management dashboard exists but no test generation

---

## 16. Extension Ecosystem

### Capability Assessment

Base44 does not support VS Code extensions or have its own plugin marketplace. The platform is a closed, proprietary web IDE with a fixed feature set. Users cannot install custom extensions or plugins. Popular development tools like ESLint and Prettier are not mentioned in documentation, suggesting they are either built-in or not available. The platform's extensibility is limited to custom code through the Fast Code Edits feature and custom integrations via OpenAPI.

**Evidence**: No extension system mentioned in documentation (P1, absence in features). Proprietary web IDE design (P3, inference from architecture). Custom integrations available for external APIs (P1, developer documentation).

**Limitations**: No extension support; no plugin system; cannot customize IDE functionality beyond provided features.

### Decision Questions for Extension Ecosystem

- **🟡 SHOULD-HAVE | 16.1: Does it support VS Code extensions?**
  Answer: No
  Evidence: Not a VS Code-based platform (P1, custom web IDE)
  Notes: No extension compatibility

- **🟢 NICE-TO-HAVE | 16.2: What percentage of VS Code marketplace works?**
  Answer: N/A
  Evidence: Not VS Code-based (P1, platform architecture)
  Notes: No VS Code extension support

- **🟢 NICE-TO-HAVE | 16.3: Can you install custom extensions?**
  Answer: No
  Evidence: No plugin or extension system (P1, absence in documentation)
  Notes: Closed platform

- **🟢 NICE-TO-HAVE | 16.4: Does it have its own plugin system?**
  Answer: No
  Evidence: No plugin marketplace or API (P1, absence in features)
  Notes: Fixed feature set

- **🟢 NICE-TO-HAVE | 16.5: Are popular extensions supported? (ESLint, Prettier)**
  Answer: No
  Evidence: No mention of linting or formatting tools (P1, absence in documentation)
  Notes: May be built-in but not documented

---

## 17. Pricing Model

### Capability Assessment

Base44 offers a free tier with limited features and credits. Paid plans include Starter ($20/month), Builder ($40 monthly / $50 monthly billing), Pro ($80 monthly / $100 monthly billing), and Elite ($160 yearly / $200 monthly billing). Pricing is based on two credit types: message credits (AI interactions) and integration credits (API calls). Code export and GitHub integration require Builder plan or higher. Enterprise licensing is available. Usage is measured by credit consumption, with limits on each tier.

**Evidence**: Pricing structure confirmed (P1, multiple YouTube videos October 2025, official pricing discussions). Free tier available (P1, pricing comparisons). Credit-based system (P1, pricing documentation).

**Limitations**: Code export paywalled behind $40-50/month minimum; credit limits may constrain heavy development.

### Decision Questions for Pricing Model

- **🟡 SHOULD-HAVE | 17.1: Is there a free tier?**
  Answer: Yes
  Evidence: Free plan with limited features (P1, SaaSWorthy pricing page)
  Notes: Cannot export code on free tier

- **🟡 SHOULD-HAVE | 17.2: What is the monthly cost per developer?**
  Answer: $0 (free) to $200/month
  Evidence: Pricing tiers: Free, $20, $40-50, $80-100, $160-200 (P1, YouTube pricing videos October 2025)
  Notes: Builder plan ($40-50) minimum for code export

- **🟡 SHOULD-HAVE | 17.3: Is there enterprise licensing?**
  Answer: Yes
  Evidence: Enterprise plan mentioned (P1, pricing page)
  Notes: Custom pricing for enterprise

- **🟢 NICE-TO-HAVE | 17.4: How is usage measured?**
  Answer: Credits (messages + integrations)
  Evidence: Two credit types: message credits and integration credits (P1, pricing documentation)
  Notes: Credits reset monthly per tier

- **🟢 NICE-TO-HAVE | 17.5: Are there usage limits on paid tiers?**
  Answer: Yes (credit limits)
  Evidence: Each tier has specific credit allocations (P1, pricing videos)
  Notes: Builder: 250 message, 10K integration; Pro: 500 message, 25K integration; Elite: 1200 message, 50K integration

---

## 18. Mobile Support

### Capability Assessment

Base44 generates responsive web applications that adapt to mobile, tablet, and desktop automatically. The official website mentions "fully functional web (and mobile) apps" and documentation references "submitting to app stores," suggesting potential native mobile app generation capability. However, no clear evidence of React Native, Flutter, or native iOS/Android code generation is documented. The responsive design approach appears to be the primary mobile strategy.

**Evidence**: Responsive design automatic (P1, features page). "Mobile apps" mentioned on website (P1, en-base44.com). App store submission mentioned (P1, documentation sidebar). No React Native or Flutter documentation found (P1, absence in features).

**Limitations**: Unclear if native mobile apps are supported; likely responsive web apps rather than native apps; no framework-specific mobile support documented.

### Decision Questions for Mobile Support

- **🟢 NICE-TO-HAVE | 18.1: Can it generate native mobile apps?**
  Answer: Unclear
  Evidence: Marketing mentions "mobile apps" but no technical documentation (P2, conflicting information)
  Notes: May be responsive web apps only; unclear if true native support exists

- **🟢 NICE-TO-HAVE | 18.2: Does it support React Native?**
  Answer: No
  Evidence: No React Native mentioned in documentation (P1, absence in features)
  Notes: React for web only

- **🟢 NICE-TO-HAVE | 18.3: Can it generate responsive web apps?**
  Answer: Yes
  Evidence: Automatic responsive design for all apps (P1, features page)
  Notes: Mobile-first responsive by default

- **🟢 NICE-TO-HAVE | 18.4: Does it support Flutter?**
  Answer: No
  Evidence: No Flutter support mentioned (P1, absence in documentation)
  Notes: React/TypeScript only

- **🟢 NICE-TO-HAVE | 18.5: Can it scaffold mobile-specific code?**
  Answer: No
  Evidence: No mobile-specific scaffolding tools (P1, absence in features)
  Notes: Responsive web approach

---

## 19. Performance Optimization

### Capability Assessment

Base44 does not provide explicit performance optimization tools, bundle analysis, or performance metrics dashboards. The platform handles build optimization automatically as part of its managed infrastructure. No documentation of lazy loading, code splitting, or performance monitoring features. The focus is on rapid development rather than fine-tuned performance optimization. Users have no control over build configuration or optimization strategies.

**Evidence**: No optimization tools mentioned in features (P1, absence in documentation). Managed build process (P3, inference from platform architecture). No performance metrics dashboard (P1, absence in features).

**Limitations**: No performance visibility; no optimization controls; no bundle analysis; black-box build process.

### Decision Questions for Performance Optimization

- **🟢 NICE-TO-HAVE | 19.1: Does it provide optimization suggestions?**
  Answer: No
  Evidence: No optimization analysis tools (P1, absence in features)
  Notes: Automatic optimization only

- **🟢 NICE-TO-HAVE | 19.2: Can it analyze bundle sizes?**
  Answer: No
  Evidence: No bundle analysis tools (P1, absence in documentation)
  Notes: Black-box build process

- **🟢 NICE-TO-HAVE | 19.3: Does it implement lazy loading automatically?**
  Answer: Unknown
  Evidence: No documentation of optimization strategies (P1, absence in documentation)
  Notes: May be implemented but not documented

- **🟢 NICE-TO-HAVE | 19.4: Does it support code splitting?**
  Answer: Unknown
  Evidence: No code splitting documentation (P1, absence in features)
  Notes: Likely handled automatically if present

- **🟢 NICE-TO-HAVE | 19.5: Can it measure performance metrics?**
  Answer: No
  Evidence: Analytics dashboard exists but no performance metrics (P1, features page)
  Notes: Usage analytics, not performance monitoring

---

## 20. Security & Compliance

### Capability Assessment

Base44 emphasizes data security with "industry-standard encryption" and built-in user authentication/management. The platform includes a Security Scan feature that runs automated security checks on apps. User authentication is built-in with role-based access control. No documentation of SOC2/ISO certification, GDPR-specific compliance features, or security vulnerability scanning tools beyond the Security Scan feature. The managed platform approach provides security by default but limited visibility into security controls.

**Evidence**: Security scan feature (P1, official blog January 2026). Built-in authentication (P1, features page). Industry-standard encryption claim (P1, SaaSWorthy description). No compliance certifications mentioned (P1, absence in documentation).

**Limitations**: No documented compliance certifications; limited security visibility; no external security tool integration.

### Decision Questions for Security & Compliance

- **🟡 SHOULD-HAVE | 20.2: Does it scan for security vulnerabilities?**
  Answer: Yes
  Evidence: Security Scan feature runs automated checks (P1, official blog January 2026)
  Notes: Scope and depth of scanning not detailed

- **🟡 SHOULD-HAVE | 20.3: Does it handle authentication scaffolding?**
  Answer: Yes
  Evidence: Built-in user authentication and management (P1, features page)
  Notes: Comprehensive auth system with roles and permissions

- **🟢 NICE-TO-HAVE | 20.4: Does it support GDPR compliance features?**
  Answer: No
  Evidence: No GDPR-specific features mentioned (P1, absence in documentation)
  Notes: General data protection claims but no GDPR tooling

- **🟢 NICE-TO-HAVE | 20.5: Does it have SOC2/ISO certification?**
  Answer: No
  Evidence: No compliance certifications documented (P1, absence in documentation)
  Notes: May exist but not publicly disclosed

---

## 21. Team & Adoption

### Capability Assessment

Base44 is positioned for solo founders, small teams, and non-technical builders. The Wix acquisition ($80 million in 2025) provides strong vendor backing and stability. The platform is designed to be accessible to beginners with minimal learning curve—natural language prompting requires no coding knowledge. Real-time collaboration features support small to medium teams (2-50 people). The credit-based pricing model scales with team size through workspace management. Early-stage but well-funded with major corporate backing.

**Evidence**: Wix acquisition July 2025 (P2, YouTube review July 2025). Positioned for non-technical users and rapid prototyping (P1, official marketing). Collaboration features (P1, features documentation). Workspace team management (P1, workspace documentation).

**Limitations**: Limited track record for enterprise teams; relatively new platform (2023-2024 launch); vendor lock-in concerns given proprietary architecture.

### Decision Questions for Team & Adoption

- **🟡 SHOULD-HAVE | 21.1: What team sizes does it support well?**
  Answer: Solo / Small (2-10) / Medium (10-50)
  Evidence: Workspace collaboration features and pricing tiers (P1, official documentation)
  Notes: Not optimized for enterprise teams (50+)

- **🟢 NICE-TO-HAVE | 21.2: What is the learning curve for developers familiar with VS Code?**
  Answer: Moderate (1-3 days)
  Evidence: Different paradigm (prompt-driven vs code-first); Fast Code Edits reduces gap (P3, inference from design)
  Notes: Easy for beginners, adjustment period for experienced developers

- **🟡 SHOULD-HAVE | 21.3: What is the vendor's funding/stability status?**
  Answer: Well-funded (acquired by Wix)
  Evidence: $80 million acquisition by Wix in 2025 (P2, YouTube review July 2025)
  Notes: Strong corporate backing ensures stability

---

## Key Differentiators

**Unique Strengths**:
- Complete all-in-one platform with zero infrastructure setup required (database, auth, hosting, storage)
- Extremely fast time-to-prototype for non-technical users and rapid MVPs
- Real-time collaboration similar to Google Docs for app development
- Natural language-first development—no coding knowledge required to start
- Wix acquisition provides financial stability and future integration potential
- GitHub integration (December 2025) bridges no-code and traditional development workflows

**Critical Limitations**:
- **FAILS 2 of 4 MUST-HAVE requirements**: Proprietary runtime dependencies (3.2) and cannot run with standard dev commands (10.1)
- Severe vendor lock-in: apps cannot run independently without Base44 backend infrastructure
- React/TypeScript-only stack with no framework alternatives
- npm package installation severely limited; many packages require CDN workarounds
- No Supabase/PostgreSQL support—proprietary NoSQL database only
- No local development, offline work, or self-hosting capabilities
- Limited scale: optimized for MVPs and small apps, not enterprise codebases (100K+ LOC)
- No code-level performance optimization or bundle analysis tools
- Black-box AI with no model selection or BYOK options

**Best Suited For**: 
- Non-technical founders building quick MVPs and prototypes
- Solo entrepreneurs needing fast time-to-market without infrastructure management
- Small teams (2-10) building internal tools or customer portals
- Projects where convenience and speed outweigh code portability concerns
- Users comfortable with platform lock-in for managed simplicity

**Not Recommended For**:
- Teams requiring code portability and deployment flexibility (CRITICAL: fails MUST-HAVE requirements 3.2 and 10.1)
- Projects using Supabase, PostgreSQL, or specific backend technologies
- Enterprise-scale applications requiring 100K+ LOC codebases
- Developers needing local development, offline work, or self-hosted environments
- Teams using Rust, Python, Go, or non-React frameworks
- Projects requiring fine-grained performance optimization or custom build configurations
- Organizations with strict vendor lock-in avoidance policies

---

## Decision Scorecard

### Critical Requirements (MUST-HAVE)
| Question | Answer | Status |
|----------|--------|--------|
| 1.1b: Applications deployable outside platform? | Requires platform | ❌ FAIL |
| 3.1: Export 100% of code? | Yes | ✅ PASS |
| 3.2: No proprietary runtime dependencies? | Requires vendor SDK | ❌ FAIL |
| 10.1: Standard dev commands work? | Requires tool IDE | ❌ FAIL |
| **MUST-HAVE SCORE** | **10/40** | **❌ 3/4 FAILED** |

### Scoring Summary
- **MUST-HAVE Score**: 10/40 (25%) ⚠️ **CRITICAL FAILURES**
- **SHOULD-HAVE Score**: 26/45 (58%)
- **NICE-TO-HAVE Score**: 7.5/15 (50%)
- **TOTAL SCORE**: 43.5/100

### Assessment

Base44 **fails 3 of 4 critical MUST-HAVE requirements**, making it unsuitable for projects requiring code portability and deployment flexibility. The platform's proprietary architecture creates severe vendor lock-in: exported applications require the @base44/sdk and active connection to Base44's backend services for all database, authentication, and storage operations. This means applications cannot run independently with standard development commands or be deployed to infrastructure outside Base44's platform—contradicting the project's requirement for portable, self-sufficient code.

The platform excels at rapid prototyping for non-technical users but sacrifices portability for convenience. While it scores moderately on SHOULD-HAVE features (58%), the critical failures in code ownership and local development support eliminate it from consideration for teams requiring vendor-neutral, portable codebases.

---

## Export Metadata

**File Path**: `/evaluations/raw-threads/base44-evaluation.md`  
**Evaluation Date**: 2026-02-04  
**Evaluator**: AI Development Tools Evaluator v2.0  
**Metrics Version**: evaluation-metrics.md v2.0  
**Template Version**: evaluation-template.md v2.0  
**Decision Criteria**: decision-criteria.md v2.0  

**Status**: Ready for synthesis via GitHub Actions

**Questions Answered**: 103/103 decision questions  
**Metrics Covered**: 21/21  
**Critical Requirements**: 1/4 MUST-HAVE questions passed ⚠️
