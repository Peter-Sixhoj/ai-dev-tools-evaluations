# Bolt.new Evaluation

**Evaluation Date**: 2026-02-03  
**Product Version**: Current (January 2026)  
**Evaluator**: AI Development Tools Evaluator  
**Metrics Version**: evaluation-metrics.md v1.0  
**Template Version**: evaluation-template.md v1.0

## Executive Summary

Bolt.new is a cloud-hosted, browser-based AI development platform built on StackBlitz's WebContainers technology that enables full-stack web application development through natural language prompts. It targets both non-technical users seeking rapid prototyping and experienced developers wanting accelerated iteration cycles, offering complete browser-based development environments with npm package management, Node.js execution, and integrated deployment capabilities. The platform emphasizes AI-driven code generation with minimal setup friction, though it's constrained to JavaScript-based frameworks and browser-compatible environments.

---

## 1. Deployment Model

Bolt.new operates exclusively as a **cloud-hosted, browser-based platform** powered by StackBlitz's WebContainers technology. The entire development environment runs in the browser without requiring local installation or setup. All code execution, including Node.js servers and npm package installations, occurs within the browser environment. Users access projects through bolt.new and work entirely through a web interface, with optional export capabilities for local development continuation.

**Evidence**: Official documentation confirms WebContainers provide "the development environment" enabling users to "install and run npm tools and libraries" and "run Node.js servers" entirely in-browser (P1: Official GitHub repository stackblitz/bolt.new, September 2024). Official support documentation states users can "build, run, edit, and deploy full-stack applications" through the browser interface (P1: support.bolt.new, January 2026).

**Limitations**: No self-hosted or on-premises deployment options exist. All development requires internet connectivity and occurs on Bolt's cloud infrastructure.

---

## 2. Package Management

Bolt.new provides **full npm package management support** through its WebContainers runtime. Users can install any npm-compatible packages including frameworks like Vite, Next.js, and standard Node.js libraries directly within the browser environment. The AI can automatically install dependencies as part of code generation, or users can manually install packages through the integrated terminal.

**Evidence**: Official repository documentation explicitly states the platform can "install and run npm tools and libraries (like Vite, Next.js, and more)" (P1: GitHub stackblitz/bolt.new, September 2024). Multiple user tutorials demonstrate successful integration of third-party packages including Supabase, Stripe, and authentication libraries (P2: YouTube tutorials, November 2024-January 2025).

**Limitations**: Package support is limited to npm ecosystem only—no native support for Python pip, Rust cargo, or Go modules. Packages requiring native binaries or system-level access may not function in the WebContainers environment.

---

## 3. Code Ownership

Bolt.new provides **full code ownership with unrestricted export capabilities**. Users can download complete project source code as a `.zip` file containing all generated files, configurations, and dependencies. Exported code is standard JavaScript/TypeScript with no proprietary dependencies or platform lock-in mechanisms. Additionally, projects can be pushed to GitHub repositories for version control, enabling seamless transition to local development environments.

**Evidence**: Official support documentation describes export functionality: "click its name in the top-left corner. Then, choose 'Export' and 'Download'" resulting in a complete `.zip` file (P1: shipper.now export guide, January 2026). User reports confirm exported code runs immediately in VS Code with `npm install` and standard development commands (P2: verified blog post, August 2025).

**Limitations**: None identified for code ownership. Users maintain full rights to generated code and can freely export, modify, and deploy outside the platform.

---

## 4. Framework Support

Bolt.new supports **JavaScript-based web frameworks exclusively**, with explicit focus on React, Next.js, Vue, and other modern JavaScript/TypeScript frameworks. The platform is optimized for full-stack JavaScript applications including frontend frameworks, Node.js backends, and npm-based tooling. Mobile app development is supported through Expo integration for React Native projects.

**Evidence**: Official introduction states users can build "JavaScript-based full-stack web applications" with "a wide range of JavaScript-based web frameworks" (P1: support.bolt.new, January 2027). Documentation explicitly mentions React, Next.js, Vue support, plus integration with "Expo for mobile application development" (P1: support.bolt.new). User tutorials demonstrate successful Next.js, React, and TypeScript project generation (P2: multiple YouTube tutorials, 2024-2025).

**Limitations**: No native support for Rust, Go, Python backend frameworks, or non-JavaScript languages. One user report mentioned using Bolt.new with "Rust + TypeScript" but context suggests TypeScript frontend only (P2: Reddit post, March 2025). The platform's WebContainers architecture fundamentally constrains it to JavaScript/Node.js ecosystems.

---

## 5. Git Integration

Bolt.new provides **native GitHub integration** enabling direct repository creation, branching, and version control operations from the browser interface. Users can create new repositories, import existing ones, create and switch branches, and maintain full Git history without command-line interaction. The platform automatically commits changes and syncs with GitHub, supporting standard Git workflows including pull requests managed through GitHub's interface.

**Evidence**: Official support documentation details complete GitHub integration workflow: "Connect your GitHub account," "Create a new repository from a Bolt project," "Create new branch in Bolt," and "Change branches in Bolt" (P1: support.bolt.new/integrations/git, January 2026). User guides confirm "automatic backups, clean version history" and ability to "use my existing CI, review, and deployment pipelines" (P2: verified blog post, August 2025).

**Limitations**: Currently supports **individual GitHub accounts only**—no organization account support (P1: official documentation). No native GitLab or Bitbucket integration. Advanced Git operations like interactive rebase or cherry-picking require manual command-line work or external tools.

---

## 6. Multi-file Context Awareness

Bolt.new demonstrates **strong multi-file context awareness** through its AI agents that maintain understanding across entire project structures. The platform's Claude Agent and v1 Agent can understand relationships between components, shared state, API routes, and configuration files when generating or modifying code. However, context awareness degrades significantly as project size increases due to AI model token limitations.

**Evidence**: Official repository states "AI models have complete control over the entire environment including the filesystem" enabling coherent multi-file operations (P1: GitHub stackblitz/bolt.new). Claude Agent is described as delivering "more complete results" for "larger development work" (P1: support.bolt.new). User reports indicate the platform successfully handles refactoring across multiple related files (P2: multiple tutorials demonstrating cross-file consistency, 2024-2025).

**Limitations**: Large projects encounter "project too large" errors when total file size exceeds AI context windows. Official documentation advises users to "reduce the size of your projects" for better performance, recommending cleanup of unused files or splitting into smaller components (P1: support.bolt.new troubleshooting). The `node_modules` directory and build output folders should be excluded to prevent context overflow (P2: dev.to guide, June 2025).

---

## 7. Backend Capabilities

Bolt.new supports **full-stack development** including Node.js backend servers, API routes, database integrations, and third-party API connections. Users can build complete applications with frontend, backend logic, database schemas, and authentication—all generated through AI prompts. The platform can run Node.js servers directly in the browser environment and interact with external services like Supabase, PostgreSQL, Firebase, and REST/GraphQL APIs.

**Evidence**: Official repository confirms ability to "run Node.js servers" and "interact with third-party APIs" (P1: GitHub stackblitz/bolt.new). User tutorials demonstrate building full-stack applications with "backend database" integration using Supabase, including authentication and data persistence (P2: YouTube comprehensive guide, January 2025). Multiple sources confirm successful Supabase and PostgreSQL integration patterns (P2: community reports, 2024-2025).

**Limitations**: Backend capabilities constrained to Node.js/JavaScript ecosystems only—no Python FastAPI, Go services, or Rust backend support. Database operations require external managed services (Supabase, hosted PostgreSQL) or Bolt Cloud's integrated database; no local database development environment.

---

## 8. Collaboration Features

Bolt.new introduced **Bolt Teams** in January 2026, providing real-time collaborative editing, role-based permissions, and admin controls for team-based development. Team features include shared project access, member invitation systems, and synchronized editing capabilities designed for small to large cross-functional teams. However, prior to Teams release, collaboration was limited to Git-based workflows only.

**Evidence**: Official blog announcement states "You can now unlock seamless collaboration with your team using Bolt for Teams" with "real-time editing, role-based permissions, admin controls" (P1: bolt.new/blog/bolt-teams, January 2026). The Teams plan is available at $40/month per user with "collaboration features, higher usage limits, and team project management" (P1: pricing analysis, November 2025). Community discussions from June 2025 requested team features prior to the January 2026 release (P2: Reddit boltnewbuilders).

**Limitations**: Real-time collaboration requires paid Teams subscription ($40/month per user minimum). Free and individual Pro users must rely solely on GitHub-based collaboration workflows without simultaneous editing capabilities. No mention of live cursors or conflict resolution features in available documentation.

---

## 9. Deployment Automation

Bolt.new offers **integrated one-click deployment** through built-in Bolt Cloud hosting, providing automatic deployment to `.bolt.host` subdomains for all users. Paid users can connect custom domains. The platform also integrates with external deployment services including Netlify and Cloudflare for production deployments. Deployment can be triggered directly from the chat interface with AI assistance.

**Evidence**: Official documentation states "Deploy your project to the web in seconds. Every project comes with a free bolt.host subdomain" and users can "publish to a live URL in seconds, with a free `.bolt.host` domain included" (P1: support.bolt.new). User tutorials demonstrate "deploying the app live using Bolt's seamless Netlify integration" (P2: YouTube guide, January 2025). Official repository confirms capability to "deploy to production from chat" (P1: GitHub stackblitz/bolt.new).

**Limitations**: Custom domains restricted to Pro tier subscribers only. CI/CD pipeline integration requires external setup through GitHub Actions or deployment platform webhooks. No built-in support for containerized deployments, Kubernetes, or enterprise deployment patterns.

---

## 10. Local Development Support

Bolt.new provides **code export for local development continuation** but requires cloud connectivity for the primary development experience. Users can download complete project source code and continue development in local IDEs like VS Code or Cursor after export. However, the platform itself operates exclusively in the browser with no offline mode or local-first architecture.

**Evidence**: Export documentation confirms users can download projects as `.zip` files containing "all the HTML/CSS documents related to the app you've built" and "then you can take them in Cursor, VS Code or any other app" (P1: shipper.now export guide, January 2026). User workflows demonstrate exporting Bolt projects, importing to GitHub, then continuing development in Cursor with local debugging (P2: Reddit user report, June 2025).

**Limitations**: No offline development capability—all work in Bolt.new requires active internet connection. No local installation option or desktop application. WebContainers run in browser only, requiring cloud infrastructure. Once exported, users lose AI-assisted development unless using separate local AI tools.

---

## 11. AI Model Selection

Bolt.new offers **multi-model support** with user-selectable AI agents powered by different large language models. As of December 2025, the platform partnered with Anthropic to provide Claude Sonnet 4 access to all users. Users can choose between "Claude Agent" (powered by Claude 4.5 models including Opus and Sonnet) and "v1 Agent" (legacy, faster but less capable). When using Claude Agent, users can further select specific Claude 4.5 model variants to prioritize speed, capability, or token efficiency.

**Evidence**: Official introduction states "Bolt gives you the choice of which LLM, or agent, powers your builds" with current options being "Claude Agent" (with selectable Claude 4.5 models) and "v1 Agent" (P1: support.bolt.new). Official blog confirms "We've partnered with Anthropic to bring Claude Sonnet 4 to all Bolt users" (P1: bolt.new/blog, December 2025). Claude 4 announcement confirms Claude Opus 4 and Sonnet 4 availability with extended thinking capabilities (P1: anthropic.com, May 2025).

**Limitations**: Model selection appears limited to Anthropic's Claude family and proprietary v1 agent. No explicit mention of GPT-4, GPT-4o, or Google Gemini integration in current documentation. Users cannot bring their own API keys for alternative models.

---

## 12. IDE Type

Bolt.new is a **standalone web-based IDE** built on StackBlitz's WebContainers technology, featuring a chat-driven interface with integrated code editor, terminal, and live preview panel. The development environment provides code editing capabilities, file navigation, terminal access, and real-time preview of running applications, all within the browser. The interface combines conversational AI prompting with traditional code editing for hybrid workflows.

**Evidence**: Official documentation describes it as an "AI-powered builder" where users "type your idea into the chat" and work in a browser-based environment (P1: support.bolt.new). The platform uses "StackBlitz's WebContainers to provide the development environment" (P1: support.bolt.new). User tutorials show a chat interface alongside code editor and live preview panels (P2: multiple YouTube demonstrations).

**Limitations**: Not a VS Code fork or extension—no access to VS Code marketplace extensions. No desktop application or local IDE option. Limited customization compared to traditional IDEs. Users requiring specific IDE features must export code to local development environments.

---

## 13. Codebase Scale Limits

Bolt.new experiences **significant performance degradation and context limitations** with larger codebases, with users reporting "project size exceeded" errors when total file content exceeds AI model context windows. The platform is optimized for small to medium projects (prototypes, single-page applications, small full-stack apps) rather than enterprise-scale monorepos. Official documentation recommends cleanup strategies and project splitting for larger applications.

**Evidence**: User reports document "Project size exceeded. Looks like you've hit the size limit" errors during development (P2: Reddit boltnewbuilders, June 2025). Official troubleshooting guide states "As your project becomes larger it becomes more difficult to keep Bolt aligned with your code" and recommends running cleanup commands or "separating your project into smaller components" (P1: support.bolt.new/troubleshooting). Technical explanation confirms AI models have "finite input capacities, often referred to as 'context windows'" that limit project size (P2: dev.to guide, June 2025).

**Limitations**: Not suitable for enterprise-scale codebases (100k+ LOC) or large monorepos. No published hard limits on file counts, but practical limits appear around medium-sized applications before context degradation. Token consumption increases with project size, impacting pricing. The `node_modules` directory and build artifacts must be excluded to preserve context budget.

---

## 14. API/Service Integration

Bolt.new provides **strong integration capabilities** for third-party APIs and services through AI-assisted scaffolding and direct code generation. The platform officially integrates with Figma (design), GitHub (version control), Expo (mobile), and Stripe (payments). Users report successful integrations with authentication providers (Supabase Auth, Firebase Auth, Auth0, Clerk), databases (Supabase, PostgreSQL), and various REST/GraphQL APIs.

**Evidence**: Official documentation lists native integrations: "Figma for design, GitHub for version control, backups, and collaboration, Expo for mobile application development, Stripe for payment handling" (P1: support.bolt.new). User tutorials demonstrate building applications with "Supabase" for "user authentication" and "dynamic recipe database" (P2: YouTube comprehensive guide, January 2025). Authentication tutorial covers "Firebase authentication, Supabase, or Auth0 via REST APIs" (P2: digiqt.com guide, December 2025).

**Limitations**: Integration quality depends on AI model knowledge and API documentation availability. Complex authentication flows or enterprise-specific APIs may require manual configuration. Type-safe API client generation not explicitly documented. Integration typically requires providing API credentials and endpoints through prompts or manual configuration.

---

## 15. Code Generation Scope

Bolt.new generates **complete full-stack applications from natural language prompts**, including frontend UI, backend logic, database schemas, API routes, authentication flows, and deployment configurations. The platform can scaffold entire projects from scratch or iteratively add features to existing code through conversational prompts. Code generation spans from single components to multi-page applications with complex data flows.

**Evidence**: Official introduction states users can build "stunning websites like landing pages, personal and corporate websites, e-commerce shops," "powerful web apps such as project management tools, job boards, CRMs, SaaS platforms," and "versatile mobile apps" (P1: support.bolt.new). Repository documentation confirms ability to handle "the entire app lifecycle—from creation to deployment" (P1: GitHub stackblitz/bolt.new). User tutorial demonstrates building a complete "recipe tracking app" with "user authentication, dynamic recipe database, search, filter, and sorting functionality" from prompts (P2: YouTube guide, January 2025).

**Limitations**: Limited to JavaScript/TypeScript ecosystems only. Cannot generate native iOS/Android apps (only React Native via Expo). Code quality and architectural decisions depend on AI model capabilities and prompt clarity. Large feature requests may require iterative refinement through multiple prompts.

---

## 16. Extension Ecosystem

Bolt.new has **no native extension ecosystem** as it is a standalone web IDE rather than a VS Code fork. Users cannot install VS Code marketplace extensions or third-party plugins within the Bolt.new environment. The platform provides a fixed feature set determined by StackBlitz's WebContainers and Bolt's interface design.

**Evidence**: Official documentation makes no mention of extension support or plugin systems. Documentation confirms Bolt "uses StackBlitz's WebContainers to provide the development environment" (P1: support.bolt.new). The platform's web-based architecture and distinct interface design differ fundamentally from VS Code's extension architecture (P3: Inference from platform design).

**Limitations**: No extensibility through plugins. Users requiring specific extensions or tools must export code to local IDEs that support extensions. Limited customization options beyond platform-provided features. No community-contributed enhancements or specialized tooling integration beyond official integrations.

---

## 17. Pricing Model

Bolt.new uses **token-based pricing** with free, Pro, Teams, and Enterprise tiers. The Free tier provides limited access with basic capabilities. Pro plans start at $25/month for 10M tokens, scaling to $2,400/month for 1,200M tokens, with usage-based increments. Teams costs $40/month per user with collaboration features and higher limits. Enterprise offers custom pricing with priority support and compliance features.

**Evidence**: Pricing analysis documents current Pro tier structure: "10M tokens for $25, 26M for $50, 55M for $100" scaling up to "1200M for $2400" (P1: shipper.now pricing guide, November 2025). Same source confirms "Team, $40/month per user: Adds collaboration features, higher usage limits, and team project management" and "Enterprise, custom pricing: Everything in Team plus priority support, usage scaling, and security compliance" (P1: shipper.now). Official blog confirms Teams availability (P1: bolt.new/blog, January 2026).

**Limitations**: Token-based pricing creates unpredictable costs for heavy users. Large codebases consume more tokens per operation. Custom domains and advanced features require paid tiers. Free tier capabilities not explicitly documented in available sources. No published token consumption benchmarks for typical operations.

---

## 18. Mobile Support

Bolt.new supports **mobile web application development** and **React Native app generation through Expo integration**. Users can build responsive web applications that function on mobile browsers and generate native mobile apps using React Native framework with Expo tooling. The official documentation explicitly lists mobile app creation as a core capability.

**Evidence**: Official introduction states users can build "versatile mobile apps including games, productivity tools, social apps, workout planners" and explicitly mentions "Expo for mobile application development" as an official integration (P1: support.bolt.new). Documentation confirms users can "build websites and JavaScript-based full-stack web applications" plus mobile apps (P1: support.bolt.new).

**Limitations**: Mobile support limited to React Native via Expo—no native Swift/Kotlin development. No Flutter, Xamarin, or other cross-platform frameworks. App Store and Google Play deployment requires external configuration beyond Bolt's scope. Mobile preview and testing capabilities within Bolt environment not documented; likely requires export and external testing tools.

---

## 19. Performance Optimization

Bolt.new provides **AI-assisted performance optimization** through prompt-driven implementation of best practices, but lacks built-in automated performance analysis or monitoring tools. Users can request optimizations like code splitting, lazy loading, image optimization, and caching strategies through natural language prompts, leveraging the AI's knowledge of framework-specific optimization techniques. The platform generates code following modern performance patterns when properly prompted.

**Evidence**: User guide documents optimization techniques achievable in Bolt: "Request bolt.new to implement Next.js Image component for automatic optimization," "Request dynamic imports for components," "Use Static Site Generation (SSG)" and other performance patterns (P2: boltnewexperts.com optimization guide, December 2023). The guide confirms users can "request bolt.new to use appropriate rendering methods" and "implement proper caching headers" (P2: community guide).

**Limitations**: No built-in performance profiling, bundle analysis tools, or Core Web Vitals monitoring within the Bolt interface. Performance optimization entirely depends on user's knowledge to request appropriate optimizations through prompts. No automatic detection of performance issues or suggestion system. Users must manually monitor deployed applications with external tools like Lighthouse or PageSpeed Insights.

---

## 20. Security & Compliance

Bolt.new provides **authentication scaffolding capabilities** through integration with third-party authentication providers (Supabase Auth, Firebase Auth, Auth0, Clerk) but lacks built-in security scanning or compliance automation features. Users can implement secure authentication workflows, but security implementation quality depends on AI-generated code and user review. The platform includes database security settings for Bolt Cloud databases.

**Evidence**: Authentication guide confirms support for "Firebase authentication, Supabase, or Auth0 via REST APIs" with workflows for "sessions, roles, and access control" (P2: digiqt.com guide, December 2025). Best practices guide recommends "Always Use HTTPS," "Block Repeated Login Attempts," "Enable Two-Factor Authentication (2FA)," and "Store Tokens in Secure Context" (P2: digiqt.com security guide). Database documentation mentions "Security Audit" feature for Bolt Cloud databases (P1: support.bolt.new/cloud/database/security).

**Limitations**: No automated security vulnerability scanning or static analysis within the platform. No GDPR, eIDAS, or NIS2 compliance automation features documented. Security depends on AI model's knowledge of security best practices and user's security expertise to review generated code. No air-gapped or on-premises deployment options for sensitive environments. Teams and Enterprise tiers mention "security compliance" but specific features not detailed in available documentation.

---

## Key Differentiators

**Unique Strengths**:
- **Zero-setup full-stack development**: Complete Node.js environment with npm package management running entirely in browser without local installation requirements
- **AI-first architecture**: Deep integration between AI models and development environment, with AI controlling filesystem, terminal, package manager, and deployment
- **Instant prototyping to production**: Single platform handling development, database, hosting, and domain management with one-click deployment
- **Accessibility for non-developers**: Natural language interface enabling product managers, designers, and beginners to build functional applications

**Critical Limitations**:
- **JavaScript-only constraint**: No support for TypeScript-first, Rust, Python, or Go backend development—fundamentally limited to Node.js ecosystem
- **Codebase scale limitations**: Performance degradation and context errors with enterprise-scale applications (100k+ LOC) or large monorepos
- **Cloud-dependent architecture**: No offline development, self-hosted options, or air-gapped deployment for security-sensitive environments
- **Limited customization**: No extension ecosystem, fixed feature set, and restricted IDE customization compared to VS Code or JetBrains products

**Best Suited For**: 
- Rapid prototyping and MVP development for web applications
- Non-technical founders and product managers building initial versions
- Small teams (2-10 developers) working on JavaScript-based full-stack projects under 50k LOC
- Agencies building client websites and small SaaS applications with quick turnaround requirements
- Educational contexts teaching web development concepts

**Not Recommended For**: 
- Enterprise applications requiring Rust, Go, or Python backends
- Large monorepos (100k+ LOC) or organizations with complex existing codebases
- Teams requiring air-gapped development or strict data sovereignty
- Projects demanding VS Code extension ecosystem (language servers, specialized debuggers, custom tools)
- Organizations with established local-first development workflows and offline requirements
- Applications requiring native mobile development (Swift/Kotlin) or non-JavaScript frameworks

---

## Export Metadata

**File Path**: `/evaluations/raw-threads/bolt-new-evaluation.md`  
**Evaluation Date**: 2026-02-03  
**Evaluator**: AI Development Tools Evaluator  
**Metrics Version**: evaluation-metrics.md v1.0 (SHA: 7cc9030ec7e428a46b69e5845f630cb47edc89c2)  
**Template Version**: evaluation-template.md v1.0 (SHA: 1ab46125f20c606da9d42b98ac8c394d3154dcf3)  

**Status**: Ready for synthesis via GitHub Actions