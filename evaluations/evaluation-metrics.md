# AI Development Tools Evaluation Metrics

**Version**: 1.0  
**Date Created**: 2026-02-03  
**Last Updated**: 2026-02-03  
**Status**: Active

## Purpose

This document defines the standardized evaluation criteria for assessing AI development platforms and code generation tools. These metrics enable consistent, structured analysis of tool capabilities, limitations, and suitability for enterprise software development.

This framework is designed to evaluate both cloud-hosted platforms (e.g., Lovable, Bolt.new) and IDE-integrated assistants (e.g., Cursor, Windsurf) against a common set of technical and operational criteria.

## Evaluation Principles

- **Evidence-Based**: Every claim must be supported by official documentation, verified user reports, or direct observation
- **Prioritization**: P1 = official documentation, P2 = recent verified reports (6 months), P3 = reasonable inferences clearly marked
- **Objectivity**: Highlight both strengths and limitations; avoid marketing language
- **Completeness**: Evaluate all 20 metrics even if some are not applicable (mark as N/A with reasoning)
- **Audience**: Evaluations assume technical reader with software development expertise

## Evaluation Metrics

### 1. Deployment Model
**Definition**: Whether the tool is cloud-hosted (browser-based), self-hosted (on-premises), or local IDE (desktop application).

**Evaluation Guidance**: Identify primary deployment method. Note if multiple deployment options exist. Consider whether user data stays local or is processed on remote servers.

---

### 2. Package Management
**Definition**: Support for third-party package managers (npm, pip, cargo, etc.) and ability to install arbitrary dependencies.

**Evaluation Guidance**: Can the tool create projects that use npm packages? Are there restrictions on which packages can be installed? Can users work with monorepos with complex dependency trees?

---

### 3. Code Ownership
**Definition**: Whether you can export source code, own the codebase fully, or are locked into the platform.

**Evaluation Guidance**: Can code be downloaded as a standard project structure? Are there platform lock-in mechanisms? What format is exported code in? Can you immediately run exported code in a local environment without platform dependencies?

---

### 4. Framework Support
**Definition**: Specific frameworks and languages supported (React, Vue, Angular, Python, Go, Rust, TypeScript, etc.).

**Evaluation Guidance**: List explicitly supported frameworks. Note limitations (e.g., only React, not Vue). For multi-language support, specify which languages have first-class vs. limited support.

---

### 5. Git Integration
**Definition**: Level of version control support—native Git, GitHub integration, or proprietary versioning.

**Evaluation Guidance**: Can users commit to GitHub directly? Is there a Git UI or must users work via command line? Are there branching/merging workflows? Can teams work via traditional pull request processes?

---

### 6. Multi-file Context Awareness
**Definition**: Ability to understand and maintain consistency across multiple files in a codebase.

**Evaluation Guidance**: When generating code, does the tool understand relationships between files? Can it refactor across a project? Does it consider existing code patterns when generating new files?

---

### 7. Backend Capabilities
**Definition**: Whether the tool generates only frontend/UI or supports full-stack development including databases and APIs.

**Evaluation Guidance**: Can it scaffold backend code (Node.js, Python, Go, Rust)? Can it create database schemas? Does it support API generation? For full-stack: does the frontend and backend integration work seamlessly?

---

### 8. Collaboration Features
**Definition**: Real-time multiplayer editing, team permissions, live cursors, or traditional Git-based workflows.

**Evaluation Guidance**: Can multiple developers work simultaneously? Is collaboration real-time or Git-based? Are there role-based permissions? Can teams review changes before merging?

---

### 9. Deployment Automation
**Definition**: Built-in deployment to production (CDN, cloud providers, app stores) vs. manual deployment required.

**Evaluation Guidance**: Can the tool automatically deploy to Vercel, Netlify, AWS, or other platforms? Does it support CI/CD pipeline integration? Can it handle database migrations on deploy?

---

### 10. Local Development Support
**Definition**: Ability to work offline, run locally, or exclusively cloud-dependent.

**Evaluation Guidance**: Can developers run projects locally on their machine? Is local debugging supported? Can work continue without internet connectivity? Are there performance differences between local and cloud execution?

---

### 11. AI Model Selection
**Definition**: Single AI model vs. multi-model support (OpenAI, Anthropic, Google, etc.).

**Evaluation Guidance**: Which AI models power code generation? Can users switch models? Can they use their own API keys? Is model selection transparent to the user?

---

### 12. IDE Type
**Definition**: Standalone web IDE, VS Code fork/extension, or command-line interface.

**Evaluation Guidance**: What is the primary interface? For web IDEs: does it have VS Code-like features? For VS Code forks: how diverged is it from base VS Code? For CLI tools: how ergonomic is the interface?

---

### 13. Codebase Scale Limits
**Definition**: Resource constraints for small prototypes vs. enterprise-scale repositories.

**Evaluation Guidance**: How large can a codebase be before performance degrades? Are there file count limits? Context window constraints? How does it handle large monorepos?

---

### 14. API/Service Integration
**Definition**: Ease of integrating third-party APIs, databases (Supabase, PostgreSQL), and external services.

**Evaluation Guidance**: Can it scaffold code for API calls? Does it have templates for common integrations (auth providers, payment processors, databases)? Can it generate type-safe API clients?

---

### 15. Code Generation Scope
**Definition**: UI components only vs. complete application scaffolding vs. inline code completion.

**Evaluation Guidance**: What can it generate? Full apps from scratch? Only UI components? Inline suggestions within existing code? Can it generate entire features or just snippets?

---

### 16. Extension Ecosystem
**Definition**: Compatibility with existing IDE extensions (VS Code marketplace, etc.).

**Evaluation Guidance**: For IDE-integrated tools: do existing VS Code extensions work? Can you install custom extensions? For web IDEs: does it have a plugin system?

---

### 17. Pricing Model
**Definition**: Free tier availability, pay-per-use, subscription tiers, or enterprise licensing.

**Evaluation Guidance**: What are all pricing tiers? Are there free/hobby tiers? Is pricing based on usage, time, or seat count? What features require paid plans?

---

### 18. Mobile Support
**Definition**: Native mobile app generation (iOS/Android) vs. responsive web only.

**Evaluation Guidance**: Can it generate native mobile apps? React Native support? Can it scaffold mobile-specific code? Or is it web-only?

---

### 19. Performance Optimization
**Definition**: Automatic code optimization, bundle analysis, and performance monitoring capabilities.

**Evaluation Guidance**: Does the tool provide optimization suggestions? Can it analyze bundle sizes? Does it implement best practices for performance (lazy loading, code splitting)? Does it measure performance metrics?

---

### 20. Security & Compliance
**Definition**: Built-in security scanning, compliance features, authentication handling.

**Evaluation Guidance**: Does it scan for security vulnerabilities? Does it handle authentication (auth providers, JWT, etc.)? Does it support compliance requirements (GDPR, eIDAS, NIS2)? Can it work in air-gapped environments?

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

---

## Change Log

### v1.0 (2026-02-03)
- Initial release
- 20 evaluation metrics defined
- Targeting evaluation of cloud-hosted and IDE-integrated AI development tools

---

## Usage Notes

- Use this metrics file as the definitive reference for all product evaluations
- Store evaluation reports in `/evaluations/raw-threads/` with naming: `[product-name]-evaluation.md`
- The synthesis script will validate that each evaluation covers all 20 metrics
- When metrics evolve, create versioned copies in `/evaluations/archive/` before updating this file
- Reference this file's version in each evaluation report for traceability
