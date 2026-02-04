# AI Development Tools Decision Criteria

**Version**: 1.0  
**Date Created**: 2026-02-04  
**Last Updated**: 2026-02-04  
**References**: evaluation-metrics.md v1.0  
**Status**: Active

## Purpose

This document defines specific, answerable questions for each evaluation metric that enable systematic comparison of AI development tools. Use this to:
- Quickly compare multiple tools side-by-side
- Identify deal-breakers early in the evaluation process
- Make data-driven tool selection decisions
- Generate comparative analysis reports

## How to Use This File

1. **During Evaluation**: Answer each question for the tool being evaluated
2. **For Comparison**: Fill in the comparison table with answers from multiple tool evaluations
3. **Decision Making**: Apply priority weights and identify deal-breakers
4. **Documentation**: Reference question IDs (e.g., 1.1, 4.2) in detailed evaluation reports
5. **Understanding**: Click question links to see rationale in [decision-rationale.md](./decision-rationale.md)

## Question Priority Levels

- 🔴 **CRITICAL**: Deal-breaker if answered unfavorably (must-have)
- 🟡 **HIGH**: Heavily weighted in decision-making (should-have)
- 🟢 **MEDIUM**: Important but not decisive (nice-to-have)

---

## Decision Questions by Category

### 1. Deployment Model

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 | 1.1 | [Can the tool be fully self-hosted on-premises?](./decision-rationale.md#11-can-the-tool-be-fully-self-hosted-on-premises) | Yes / Partial / No |
| 🔴 | 1.2 | [Does it work in air-gapped environments without internet?](./decision-rationale.md#12-does-it-work-in-air-gapped-environments-without-internet) | Yes / No |
| 🟡 | 1.3 | [Can it run as a local desktop application?](./decision-rationale.md#13-can-it-run-as-a-local-desktop-application) | Yes / No |
| 🟡 | 1.4 | [Where is code processed? (local vs cloud)](./decision-rationale.md#14-where-is-code-processed-local-vs-cloud) | Local / Cloud / Hybrid |
| 🟢 | 1.5 | [Is there a web-based version available?](./decision-rationale.md#15-is-there-a-web-based-version-available) | Yes / No |

### 2. Package Management

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 2.1 | [Does it support npm package installation?](./decision-rationale.md#21-does-it-support-npm-package-installation) | Yes / Limited / No |
| 🟡 | 2.2 | [Does it support cargo (Rust) packages?](./decision-rationale.md#22-does-it-support-cargo-rust-packages) | Yes / Limited / No |
| 🟡 | 2.3 | [Can it handle monorepo dependency structures?](./decision-rationale.md#23-can-it-handle-monorepo-dependency-structures) | Yes / Limited / No |
| 🟢 | 2.4 | [Does it support pip (Python) packages?](./decision-rationale.md#24-does-it-support-pip-python-packages) | Yes / Limited / No |
| 🟢 | 2.5 | [Are there restrictions on which packages can be used?](./decision-rationale.md#25-are-there-restrictions-on-which-packages-can-be-used) | Yes / No |

### 3. Code Ownership

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 | 3.1 | [Can you export 100% of generated code?](./decision-rationale.md#31-can-you-export-100-of-generated-code) | Yes / No |
| 🔴 | 3.2 | [Is exported code dependency-free from the platform?](./decision-rationale.md#32-is-exported-code-dependency-free-from-the-platform) | Yes / No |
| 🟡 | 3.3 | [Is code export in standard project format?](./decision-rationale.md#33-is-code-export-in-standard-project-format-no-proprietary-structure) | Yes / No |
| 🟡 | 3.4 | [Can exported code run immediately in local environment?](./decision-rationale.md#34-can-exported-code-run-immediately-in-local-environment) | Yes / Requires setup / No |
| 🟢 | 3.5 | [Can you export project history/version control?](./decision-rationale.md#35-can-you-export-project-historyversion-control) | Yes / No |

### 4. Framework Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 | 4.1 | [Does it have first-class TypeScript support?](./decision-rationale.md#41-does-it-have-first-class-typescript-support) | Yes / Limited / No |
| 🔴 | 4.2 | [Does it support Rust with LSP integration?](./decision-rationale.md#42-does-it-support-rust-with-lsp-integration) | Yes / Syntax only / No |
| 🟡 | 4.3 | [Does it support React/Next.js?](./decision-rationale.md#43-does-it-support-reactnextjs) | Yes / Limited / No |
| 🟡 | 4.4 | [Does it support Python?](./decision-rationale.md#44-does-it-support-python) | Yes / Limited / No |
| 🟡 | 4.5 | [Does it support Go?](./decision-rationale.md#45-does-it-support-go) | Yes / Limited / No |
| 🟢 | 4.6 | [Does it support Vue.js?](./decision-rationale.md#46-does-it-support-vuejs) | Yes / Limited / No |
| 🟢 | 4.7 | [Does it support Angular?](./decision-rationale.md#47-does-it-support-angular) | Yes / Limited / No |

### 5. Git Integration

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 5.1 | [Does it have native Git integration?](./decision-rationale.md#51-does-it-have-native-git-integration) | Yes / CLI only / No |
| 🟡 | 5.2 | [Can you push directly to GitHub/GitLab?](./decision-rationale.md#52-can-you-push-directly-to-githubgitlab) | Both / GitHub only / No |
| 🟡 | 5.3 | [Does it support pull request workflows?](./decision-rationale.md#53-does-it-support-pull-request-workflows) | Yes / No |
| 🟢 | 5.4 | [Does it have a visual Git UI?](./decision-rationale.md#54-does-it-have-a-visual-git-ui) | Yes / No |
| 🟢 | 5.5 | [Can it handle branch management?](./decision-rationale.md#55-can-it-handle-branch-management) | Yes / Limited / No |

### 6. Multi-file Context Awareness

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 6.1 | [Can it understand relationships between files?](./decision-rationale.md#61-can-it-understand-relationships-between-files) | Yes / Limited / No |
| 🟡 | 6.2 | [Can it refactor across multiple files?](./decision-rationale.md#62-can-it-refactor-across-multiple-files) | Yes / Limited / No |
| 🟡 | 6.3 | [What is the maximum file context size?](./decision-rationale.md#63-what-is-the-maximum-file-context-size) | Number of files |
| 🟢 | 6.4 | [Does it maintain consistency when generating new files?](./decision-rationale.md#64-does-it-maintain-consistency-when-generating-new-files) | Yes / Sometimes / No |
| 🟢 | 6.5 | [Can it analyze entire codebase for suggestions?](./decision-rationale.md#65-can-it-analyze-entire-codebase-for-suggestions) | Yes / Limited / No |

### 7. Backend Capabilities

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 7.1 | [Can it generate backend code?](./decision-rationale.md#71-can-it-generate-backend-code-nodejspythongorust) | All / Some / None |
| 🟡 | 7.2 | [Can it create database schemas?](./decision-rationale.md#72-can-it-create-database-schemas) | Yes / No |
| 🟡 | 7.3 | [Does it support API generation?](./decision-rationale.md#73-does-it-support-api-generation-restgraphql) | Both / REST only / No |
| 🟢 | 7.4 | [Can it scaffold full-stack applications?](./decision-rationale.md#74-can-it-scaffold-full-stack-applications) | Yes / Frontend only / No |
| 🟢 | 7.5 | [Does frontend/backend integration work seamlessly?](./decision-rationale.md#75-does-frontendbackend-integration-work-seamlessly) | Yes / Manual setup / No |

### 8. Collaboration Features

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 8.1 | [Does it support team collaboration?](./decision-rationale.md#81-does-it-support-team-collaboration) | Real-time / Git-based / No |
| 🟢 | 8.2 | [Are there role-based permissions?](./decision-rationale.md#82-are-there-role-based-permissions) | Yes / No |
| 🟢 | 8.3 | [Can multiple developers work simultaneously?](./decision-rationale.md#83-can-multiple-developers-work-simultaneously) | Yes / No |
| 🟢 | 8.4 | [Does it support code review workflows?](./decision-rationale.md#84-does-it-support-code-review-workflows) | Yes / No |
| 🟢 | 8.5 | [Are there live cursors for real-time editing?](./decision-rationale.md#85-are-there-live-cursors-for-real-time-editing) | Yes / No |

### 9. Deployment Automation

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 | 9.1 | [Does it have built-in deployment automation?](./decision-rationale.md#91-does-it-have-built-in-deployment-automation) | Yes / No |
| 🟢 | 9.2 | [Which platforms does it deploy to?](./decision-rationale.md#92-which-platforms-does-it-deploy-to) | List platforms |
| 🟢 | 9.3 | [Does it support CI/CD pipeline integration?](./decision-rationale.md#93-does-it-support-cicd-pipeline-integration) | Yes / No |
| 🟢 | 9.4 | [Can it handle database migrations on deploy?](./decision-rationale.md#94-can-it-handle-database-migrations-on-deploy) | Yes / No |
| 🟢 | 9.5 | [Is deployment configuration customizable?](./decision-rationale.md#95-is-deployment-configuration-customizable) | Yes / Limited / No |

### 10. Local Development Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 | 10.1 | [Can you run projects locally without the tool?](./decision-rationale.md#101-can-you-run-projects-locally-without-the-tool) | Yes / No |
| 🟡 | 10.2 | [Does it work offline?](./decision-rationale.md#102-does-it-work-offline) | Yes / Limited / No |
| 🟡 | 10.3 | [Is local debugging supported?](./decision-rationale.md#103-is-local-debugging-supported) | Yes / No |
| 🟢 | 10.4 | [Are there performance differences local vs cloud?](./decision-rationale.md#104-are-there-performance-differences-local-vs-cloud) | Same / Slower / Faster |
| 🟢 | 10.5 | [Can you use your own dev tools alongside it?](./decision-rationale.md#105-can-you-use-your-own-dev-tools-alongside-it) | Yes / No |

### 11. AI Model Selection

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 11.1 | [Which AI models does it support?](./decision-rationale.md#111-which-ai-models-does-it-support) | List models |
| 🟡 | 11.2 | [Can you switch between models?](./decision-rationale.md#112-can-you-switch-between-models) | Yes / No |
| 🟡 | 11.3 | [Can you use your own API keys?](./decision-rationale.md#113-can-you-use-your-own-api-keys) | Yes / No |
| 🟢 | 11.4 | [Is model selection transparent to users?](./decision-rationale.md#114-is-model-selection-transparent-to-users) | Yes / No |
| 🟢 | 11.5 | [Does it support local/open-source models?](./decision-rationale.md#115-does-it-support-localopen-source-models) | Yes / No |

### 12. IDE Type

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 12.1 | [What is the primary interface?](./decision-rationale.md#121-what-is-the-primary-interface) | Web/Fork/Extension/CLI |
| 🟡 | 12.2 | [Is it based on VS Code?](./decision-rationale.md#122-is-it-based-on-vs-code) | Yes / No |
| 🟢 | 12.3 | [Does it have terminal access?](./decision-rationale.md#123-does-it-have-terminal-access) | Yes / No |
| 🟢 | 12.4 | [Can you customize the IDE?](./decision-rationale.md#124-can-you-customize-the-ide) | Yes / Limited / No |
| 🟢 | 12.5 | [Does it support keyboard shortcuts?](./decision-rationale.md#125-does-it-support-keyboard-shortcuts) | Yes / Limited / No |

### 13. Codebase Scale Limits

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 13.1 | [What is the maximum file count supported?](./decision-rationale.md#131-what-is-the-maximum-file-count-supported) | Number or Unlimited |
| 🟡 | 13.2 | [What is the context window size?](./decision-rationale.md#132-what-is-the-context-window-size) | Tokens/files |
| 🟡 | 13.3 | [Can it handle enterprise-scale codebases?](./decision-rationale.md#133-can-it-handle-enterprise-scale-codebases-100k-loc) | Yes / No |
| 🟢 | 13.4 | [Does it support large monorepos?](./decision-rationale.md#134-does-it-support-large-monorepos) | Yes / Limited / No |
| 🟢 | 13.5 | [Are there performance degradation thresholds?](./decision-rationale.md#135-are-there-performance-degradation-thresholds) | At X files/LOC |

### 14. API/Service Integration

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 14.1 | [Can it scaffold Supabase integration?](./decision-rationale.md#141-can-it-scaffold-supabase-integration) | Yes / Manual / No |
| 🟡 | 14.2 | [Can it generate type-safe API clients?](./decision-rationale.md#142-can-it-generate-type-safe-api-clients) | Yes / No |
| 🟢 | 14.3 | [Does it have templates for auth providers?](./decision-rationale.md#143-does-it-have-templates-for-auth-providers) | Yes / No |
| 🟢 | 14.4 | [Can it integrate payment processors?](./decision-rationale.md#144-can-it-integrate-payment-processors) | Yes / No |
| 🟢 | 14.5 | [Does it support GraphQL code generation?](./decision-rationale.md#145-does-it-support-graphql-code-generation) | Yes / No |

### 15. Code Generation Scope

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 15.1 | [Can it generate full applications from scratch?](./decision-rationale.md#151-can-it-generate-full-applications-from-scratch) | Yes / No |
| 🟡 | 15.2 | [Can it generate complete features/modules?](./decision-rationale.md#152-can-it-generate-complete-featuresmodules) | Yes / No |
| 🟡 | 15.3 | [Does it provide inline code completion?](./decision-rationale.md#153-does-it-provide-inline-code-completion) | Yes / No |
| 🟢 | 15.4 | [Can it generate only UI components?](./decision-rationale.md#154-can-it-generate-only-ui-components) | Yes / No |
| 🟢 | 15.5 | [Can it generate test files?](./decision-rationale.md#155-can-it-generate-test-files) | Yes / No |

### 16. Extension Ecosystem

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 16.1 | [Does it support VS Code extensions?](./decision-rationale.md#161-does-it-support-vs-code-extensions) | Yes / Limited / No |
| 🟢 | 16.2 | [What percentage of VS Code marketplace works?](./decision-rationale.md#162-what-percentage-of-vs-code-marketplace-works) | Percentage |
| 🟢 | 16.3 | [Can you install custom extensions?](./decision-rationale.md#163-can-you-install-custom-extensions) | Yes / No |
| 🟢 | 16.4 | [Does it have its own plugin system?](./decision-rationale.md#164-does-it-have-its-own-plugin-system) | Yes / No |
| 🟢 | 16.5 | [Are popular extensions supported?](./decision-rationale.md#165-are-popular-extensions-eslint-prettier-supported) | Yes / Some / No |

### 17. Pricing Model

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟡 | 17.1 | [Is there a free tier?](./decision-rationale.md#171-is-there-a-free-tier) | Yes / Trial only / No |
| 🟡 | 17.2 | [What is the monthly cost per developer?](./decision-rationale.md#172-what-is-the-monthly-cost-per-developer) | $ amount |
| 🟡 | 17.3 | [Is there enterprise licensing?](./decision-rationale.md#173-is-there-enterprise-licensing) | Yes / No |
| 🟢 | 17.4 | [How is usage measured?](./decision-rationale.md#174-how-is-usage-measured) | Time/Tokens/Seats |
| 🟢 | 17.5 | [Are there usage limits on paid tiers?](./decision-rationale.md#175-are-there-usage-limits-on-paid-tiers) | Yes / No |

### 18. Mobile Support

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 | 18.1 | [Can it generate native mobile apps?](./decision-rationale.md#181-can-it-generate-native-mobile-apps) | iOS+Android/One/No |
| 🟢 | 18.2 | [Does it support React Native?](./decision-rationale.md#182-does-it-support-react-native) | Yes / No |
| 🟢 | 18.3 | [Can it generate responsive web apps?](./decision-rationale.md#183-can-it-generate-responsive-web-apps) | Yes / No |
| 🟢 | 18.4 | [Does it support Flutter?](./decision-rationale.md#184-does-it-support-flutter) | Yes / No |
| 🟢 | 18.5 | [Can it scaffold mobile-specific code?](./decision-rationale.md#185-can-it-scaffold-mobile-specific-code) | Yes / No |

### 19. Performance Optimization

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🟢 | 19.1 | [Does it provide optimization suggestions?](./decision-rationale.md#191-does-it-provide-optimization-suggestions) | Yes / No |
| 🟢 | 19.2 | [Can it analyze bundle sizes?](./decision-rationale.md#192-can-it-analyze-bundle-sizes) | Yes / No |
| 🟢 | 19.3 | [Does it implement lazy loading automatically?](./decision-rationale.md#193-does-it-implement-lazy-loading-automatically) | Yes / No |
| 🟢 | 19.4 | [Does it support code splitting?](./decision-rationale.md#194-does-it-support-code-splitting) | Yes / No |
| 🟢 | 19.5 | [Can it measure performance metrics?](./decision-rationale.md#195-can-it-measure-performance-metrics) | Yes / No |

### 20. Security & Compliance

| Priority | ID | Question | Answer Format |
|----------|----|----|---------------|
| 🔴 | 20.1 | [Can it work in air-gapped environments?](./decision-rationale.md#201-can-it-work-in-air-gappedisolated-environments) | Yes / No |
| 🟡 | 20.2 | [Does it scan for security vulnerabilities?](./decision-rationale.md#202-does-it-scan-for-security-vulnerabilities) | Yes / No |
| 🟡 | 20.3 | [Does it handle authentication scaffolding?](./decision-rationale.md#203-does-it-handle-authentication-scaffolding) | Yes / No |
| 🟢 | 20.4 | [Does it support GDPR compliance features?](./decision-rationale.md#204-does-it-support-gdpr-compliance-features) | Yes / No |
| 🟢 | 20.5 | [Does it have SOC2/ISO certification?](./decision-rationale.md#205-does-it-have-soc2iso-certification) | Yes / No |

---

## Tool Comparison Table Template

Copy this template and fill in answers for each tool you're evaluating.

| Category | Question | Tool 1 | Tool 2 | Tool 3 | Tool 4 |
|----------|----------|--------|--------|--------|--------|
| Deployment Model | Self-hosted? (1.1) | | | | |
| Deployment Model | Air-gapped? (1.2) | | | | |
| Deployment Model | Local desktop? (1.3) | | | | |
| Deployment Model | Processing location? (1.4) | | | | |
| Deployment Model | Web version? (1.5) | | | | |
| Package Management | npm? (2.1) | | | | |
| Package Management | cargo? (2.2) | | | | |
| Package Management | Monorepo? (2.3) | | | | |
| Package Management | pip? (2.4) | | | | |
| Package Management | Package restrictions? (2.5) | | | | |
| Code Ownership | Export 100%? (3.1) | | | | |
| Code Ownership | Platform-independent? (3.2) | | | | |
| Code Ownership | Standard format? (3.3) | | | | |
| Code Ownership | Runs locally? (3.4) | | | | |
| Code Ownership | Export history? (3.5) | | | | |
| Framework Support | TypeScript? (4.1) | | | | |
| Framework Support | Rust LSP? (4.2) | | | | |
| Framework Support | React/Next.js? (4.3) | | | | |
| Framework Support | Python? (4.4) | | | | |
| Framework Support | Go? (4.5) | | | | |
| Framework Support | Vue.js? (4.6) | | | | |
| Framework Support | Angular? (4.7) | | | | |
| Git Integration | Native Git? (5.1) | | | | |
| Git Integration | GitHub/GitLab? (5.2) | | | | |
| Git Integration | PR workflows? (5.3) | | | | |
| Git Integration | Visual UI? (5.4) | | | | |
| Git Integration | Branch management? (5.5) | | | | |
| Multi-file Context | File relationships? (6.1) | | | | |
| Multi-file Context | Multi-file refactor? (6.2) | | | | |
| Multi-file Context | Max context? (6.3) | | | | |
| Multi-file Context | Consistent generation? (6.4) | | | | |
| Multi-file Context | Codebase analysis? (6.5) | | | | |
| Backend | Languages? (7.1) | | | | |
| Backend | DB schemas? (7.2) | | | | |
| Backend | API generation? (7.3) | | | | |
| Backend | Full-stack scaffold? (7.4) | | | | |
| Backend | Seamless integration? (7.5) | | | | |
| Collaboration | Team support? (8.1) | | | | |
| Collaboration | Role permissions? (8.2) | | | | |
| Collaboration | Simultaneous work? (8.3) | | | | |
| Collaboration | Code review? (8.4) | | | | |
| Collaboration | Live cursors? (8.5) | | | | |
| Deployment | Built-in automation? (9.1) | | | | |
| Deployment | Platform support? (9.2) | | | | |
| Deployment | CI/CD integration? (9.3) | | | | |
| Deployment | DB migrations? (9.4) | | | | |
| Deployment | Customizable? (9.5) | | | | |
| Local Development | Run without tool? (10.1) | | | | |
| Local Development | Offline? (10.2) | | | | |
| Local Development | Debugging? (10.3) | | | | |
| Local Development | Performance? (10.4) | | | | |
| Local Development | Own dev tools? (10.5) | | | | |
| AI Models | Supported models? (11.1) | | | | |
| AI Models | Switch models? (11.2) | | | | |
| AI Models | Own API keys? (11.3) | | | | |
| AI Models | Transparent? (11.4) | | | | |
| AI Models | Local models? (11.5) | | | | |
| IDE Type | Interface? (12.1) | | | | |
| IDE Type | VS Code based? (12.2) | | | | |
| IDE Type | Terminal access? (12.3) | | | | |
| IDE Type | Customizable? (12.4) | | | | |
| IDE Type | Keyboard shortcuts? (12.5) | | | | |
| Codebase Scale | Max files? (13.1) | | | | |
| Codebase Scale | Context window? (13.2) | | | | |
| Codebase Scale | Enterprise scale? (13.3) | | | | |
| Codebase Scale | Large monorepos? (13.4) | | | | |
| Codebase Scale | Degradation threshold? (13.5) | | | | |
| API Integration | Supabase? (14.1) | | | | |
| API Integration | Type-safe clients? (14.2) | | | | |
| API Integration | Auth templates? (14.3) | | | | |
| API Integration | Payment processors? (14.4) | | | | |
| API Integration | GraphQL codegen? (14.5) | | | | |
| Code Generation | Full apps? (15.1) | | | | |
| Code Generation | Features? (15.2) | | | | |
| Code Generation | Inline completion? (15.3) | | | | |
| Code Generation | UI components? (15.4) | | | | |
| Code Generation | Test files? (15.5) | | | | |
| Extensions | VS Code extensions? (16.1) | | | | |
| Extensions | Marketplace %? (16.2) | | | | |
| Extensions | Custom extensions? (16.3) | | | | |
| Extensions | Plugin system? (16.4) | | | | |
| Extensions | Popular extensions? (16.5) | | | | |
| Pricing | Free tier? (17.1) | | | | |
| Pricing | Cost/dev/month? (17.2) | | | | |
| Pricing | Enterprise? (17.3) | | | | |
| Pricing | Usage measurement? (17.4) | | | | |
| Pricing | Usage limits? (17.5) | | | | |
| Mobile | Native apps? (18.1) | | | | |
| Mobile | React Native? (18.2) | | | | |
| Mobile | Responsive web? (18.3) | | | | |
| Mobile | Flutter? (18.4) | | | | |
| Mobile | Mobile-specific code? (18.5) | | | | |
| Performance | Optimization suggestions? (19.1) | | | | |
| Performance | Bundle analysis? (19.2) | | | | |
| Performance | Auto lazy loading? (19.3) | | | | |
| Performance | Code splitting? (19.4) | | | | |
| Performance | Metrics? (19.5) | | | | |
| Security | Air-gapped? (20.1) | | | | |
| Security | Vuln scanning? (20.2) | | | | |
| Security | Auth scaffolding? (20.3) | | | | |
| Security | GDPR features? (20.4) | | | | |
| Security | SOC2/ISO cert? (20.5) | | | | |

---

## Scoring System

### Critical Questions (Must Pass All 8)

| Question ID | Requirement |
|-------------|-------------|
| 1.1 | Self-hosted |
| 1.2 | Air-gapped |
| 3.1 | Export 100% |
| 3.2 | Platform-independent |
| 4.1 | TypeScript |
| 4.2 | Rust LSP |
| 10.1 | Run without tool |
| 20.1 | Air-gapped operation |

**Rule**: Fail any critical = ELIMINATED

### Scoring Formula

- **Critical**: 8/8 required (pass/fail)
- **High Priority**: 43 questions × weight 2 = max 86 points
- **Medium Priority**: 49 questions × weight 1 = max 49 points
- **Total Maximum**: 32 + 86 + 49 = 167 points

### Score Calculation

```
Critical Pass = 8/8 ✓ = 32 points (or eliminated)
High Score = (favorable answers / 43) × 86
Medium Score = (favorable answers / 49) × 49
Total = Critical + High + Medium
```

---

## Decision Rules

### Phase 1: Elimination
Eliminate tools that fail ANY critical question (1.1, 1.2, 3.1, 3.2, 4.1, 4.2, 10.1, 20.1)

### Phase 2: Ranking
Rank remaining tools by Total Score (descending)

### Phase 3: Selection
Consider:
- Highest score
- Cost per developer
- Team familiarity
- Vendor stability
- Support quality

---

## Related Documents

- [evaluation-metrics.md](./evaluation-metrics.md) - 20 evaluation categories
- [decision-rationale.md](./decision-rationale.md) - Why each question matters
- [evaluation-template.md](./evaluation-template.md) - Report structure
- [space-instructions.txt](./space-instructions.txt) - Evaluation workflow

---

## Change Log

### v1.0 (2026-02-04)
- Initial release
- 100 questions: 8 Critical, 43 High, 49 Medium
- Comparison table template
- Scoring system and decision rules
