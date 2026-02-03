# Bolt.new Evaluation

Bolt.new is an AI-powered full-stack web application builder that runs entirely in the browser using WebContainers technology, enabling developers to prompt, code, and deploy applications without local setup [web:1][web:2]. Built by StackBlitz, it combines large language models with an in-browser Node.js environment for rapid prototyping and production deployment [web:25][web:28].

## DEPLOYMENT MODEL

Cloud-hosted browser-based platform [web:4][web:5]. Bolt.new runs entirely within Chromium-based browsers (Chrome, Edge, Brave, Vivaldi, Opera) on desktop [page:1]. The WebContainers technology executes a Node.js runtime compiled to WebAssembly directly in the browser tab, not on remote servers [web:25][web:28]. Mobile browsers are not fully supported [page:1].

The platform operates online by default but supports offline development after initial load, allowing continued work without internet connectivity [web:25]. However, AI code generation requires active connection to cloud-based LLM services.

## PACKAGE MANAGEMENT

Full npm support with notable limitations [web:10][page:1]. Bolt.new allows installation of arbitrary npm packages through standard `npm install` commands in the integrated terminal [web:10]. The platform supports npm, and users have reported using `--force` and `--legacy-peer-deps` flags for dependency resolution [web:29].

**Limitations**: Dependency installation can hang or fail, particularly for large packages, with errors requiring browser refresh or manual `package-lock.json` deletion [web:26]. Installation times can extend up to 15 minutes for complex dependency trees [web:26]. The WebContainer environment's memory constraints directly impact package installation success rates [web:22][web:26].

## CODE OWNERSHIP

Full code export and ownership [web:16][web:19]. Users can download complete source code as a zip file containing all frontend and backend files by clicking the project name, selecting "Export," then "Download" [web:16][web:19]. The exported code is standard Node.js application structure that can be run locally or deployed to any hosting provider [web:9].

Projects can be opened in StackBlitz IDE for further editing and pushed to GitHub repositories for version control [web:9]. No vendor lock-in exists for the generated codebase itself.

## FRAMEWORK SUPPORT

JavaScript/TypeScript-based web frameworks only [page:1][web:18]. Supported frameworks include:

- Frontend: React, Next.js, Vue, Angular, Svelte, Remix [web:12][web:15][web:18]
- Backend: Node.js, Express, NestJS [web:18][page:1]
- Mobile: Expo for React Native applications (iOS/Android) [web:37][web:40][page:1]
- Languages: JavaScript, TypeScript [page:1][web:11]

**Not supported**: Python (FastAPI, Django, Flask), PHP, Ruby, Go, Rust, or any non-JavaScript backend frameworks [web:18][page:1]. The platform explicitly operates in a Node.js-only environment due to WebContainer constraints.

## GIT INTEGRATION

Native GitHub integration with full version control [web:6][web:9]. Bolt.new connects directly to GitHub accounts (requires authorizing StackBlitz) and supports:

- Creating new GitHub repositories from within Bolt [web:6]
- Branching and merging operations [web:6]
- Switching between branches in the Bolt interface [web:6]
- Automatic commit and push workflows [web:9]

Users can also open projects in StackBlitz IDE to access more granular Git operations before pushing to GitHub [web:9]. The GitHub integration enables continuous deployment workflows with Netlify, where commits automatically trigger redeployment [web:9].

## MULTI-FILE CONTEXT AWARENESS

Advanced multi-file context with AI-driven consistency [web:1][page:0]. The Claude Agent (primary AI) handles projects "1,000 times larger than before" with improved built-in context management [web:1]. The platform maintains awareness across entire codebases, understanding file relationships and dependencies.

**Context window limitations**: Projects exceeding AI context capacity trigger "project size exceeded" errors [web:32][web:35]. The AI's context window defines processing limits—typically manageable for standard web applications but problematic for enterprise-scale codebases with extensive files [web:32][web:35]. Users can mitigate this using `.bolt/ignore` files to exclude large datasets, logs, or non-essential assets, potentially reducing project size by 10-30% [web:35].

## BACKEND CAPABILITIES

Full-stack development with integrated database support [web:3][web:8][page:0]. Bolt.new generates complete backend implementations including:

- RESTful APIs and backend services [web:8][web:25]
- Authentication systems (user sign-up, login, session management) [web:8][web:37]
- Database integration with built-in Bolt Databases or external Supabase/PostgreSQL connections [web:3][web:8][page:0]
- CRUD operations and data persistence [web:8]

The Claude Agent specifically supports creating Bolt Databases directly or connecting to user-owned Supabase accounts [page:0]. Backend code runs in the browser's Node.js environment during development [web:28].

## COLLABORATION FEATURES

Real-time multiplayer editing with enterprise team features [web:30][web:25]. Bolt Teams (released January 2026) provides:

- Real-time collaborative editing with live cursors [web:30]
- Role-based permissions and admin controls [web:30]
- Shared project workspaces [web:10]
- Team-level resource management [web:10]

The collaboration model resembles "Google Docs for coding" [web:25], enabling multiple developers to edit simultaneously. This differs from traditional Git-based workflows, though GitHub integration remains available for version control [web:6].

## DEPLOYMENT AUTOMATION

One-click deployment to production [web:3][web:5][web:8]. Bolt.new includes native integration with Netlify for instant deployment:

- Click "Deploy" or "Publish" button for automated hosting setup [web:3][web:5]
- Generates live URLs immediately (free Bolt URL or custom Netlify domain) [web:3][web:5]
- Handles hosting configuration automatically—no manual pipeline setup required [web:5][web:8]
- Supports continuous deployment when paired with GitHub integration [web:9]

Users can also deploy to other platforms manually by exporting source code [web:14][web:16]. Vercel support has been requested but is not natively integrated [web:14].

## LOCAL DEVELOPMENT SUPPORT

Hybrid browser-local execution model [web:25][web:28]. The WebContainers technology runs Node.js locally within the browser tab rather than on remote servers, providing faster performance and enhanced security [web:25]. Code executes on local device resources (CPU, RAM) [web:22].

**Offline capability**: After initial load, developers can work offline for coding and testing [web:25]. However, AI code generation requires internet connectivity to access cloud-based LLM services [web:24]. The platform does not support traditional local IDE workflows—development occurs in the browser environment.

Users can export code to continue development in local environments outside Bolt [web:16][web:19].

## AI MODEL SELECTION

Multi-model support with granular selection [page:0][web:7]. Bolt.new offers two AI agent systems:

**Claude Agent** (recommended for production):
- Haiku 4.5: Fast, cost-efficient for simple edits and styling [page:0]
- Sonnet 4.5: Balanced default for everyday building [page:0]
- Opus 4.5: Highest reasoning for complex, enterprise-grade architecture [page:0]

**v1 Agent (legacy)**: Uses Claude Sonnet, faster but produces incomplete apps requiring more fixes [page:0]. Not recommended for production work.

Additional models available through pricing tiers include GPT-4 and other LLMs [web:7][web:10]. Users can switch models mid-project within Claude Agent without losing context [page:0].

## IDE TYPE

Standalone web IDE with integrated tooling [web:25][web:28]. Bolt.new provides a complete browser-based development environment featuring:

- Code editor (VS Code-like interface) [web:25]
- File tree and project structure navigator [web:28]
- Integrated terminal with full shell access [web:25]
- Live preview pane for real-time application testing [web:28]
- AI chat interface for prompt-driven development [web:2]

The platform is built on StackBlitz's WebContainers technology but operates as an independent product [web:6]. It is not a VS Code extension or fork—it's a purpose-built web application.

## CODEBASE SCALE LIMITS

Optimized for small-to-medium projects with explicit size constraints [web:1][web:32][web:35]. While Bolt.new claims to handle projects "1,000 times larger than before" [web:1], practical limitations exist:

**Constraints**: AI context window limits trigger "project size exceeded" errors for large codebases [web:32][web:35]. Projects with extensive datasets, complex logic, or heavy media assets struggle within these constraints [web:35]. WebContainer memory demands increase with project size, requiring sufficient browser RAM [web:22][web:26].

**Mitigation strategies**: Use `.bolt/ignore` files to exclude non-essential files (10-30% size reduction), clean unused dependencies regularly, and adopt modular architecture [web:35].

**Best suited for**: Rapid prototypes, MVPs, small production applications, and learning projects [web:28]. Enterprise-scale repositories with thousands of files may exceed practical limits [web:35].

## API/SERVICE INTEGRATION

Strong third-party integration support [web:8][web:37][page:0]. Bolt.new facilitates integration with:

- Databases: Native Bolt Databases, Supabase, PostgreSQL [web:8][page:0]
- Authentication: Supabase Auth for user management [web:8][web:37]
- External APIs: Any REST or GraphQL API accessible from Node.js [web:18]
- Mobile platforms: Expo for iOS/Android deployment [web:37][web:40][page:1]

Integration setup is AI-assisted—developers can prompt for "add Supabase authentication" and the Claude Agent generates configuration code [web:8]. Third-party security scanners exist specifically for Bolt.new apps to verify database security rules and exposed credentials [web:36][web:39].

## CODE GENERATION SCOPE

Complete application scaffolding including full-stack architecture [web:2][web:8]. Bolt.new generates:

- Complete UI components and layouts [web:3]
- Multi-page application structures [web:25]
- Backend APIs and server logic [web:8][web:25]
- Database schemas and CRUD operations [web:8]
- Authentication flows and user management [web:8][web:37]
- Mobile app configurations via Expo [web:37][web:40]

The scope extends far beyond inline code completion or UI-only generation—it produces production-ready full-stack applications from natural language prompts [web:3][web:8]. The Claude Agent includes "Plan Mode" for detailed build strategy development before code execution [page:0].

## EXTENSION ECOSYSTEM

No traditional extension marketplace [web:25][page:1]. Bolt.new does not support VS Code marketplace extensions or third-party plugins. The platform provides a curated, integrated development environment with fixed tooling.

**Customization options**: Users can upload `claude.md` files to provide project-specific instructions and context to AI agents [page:0]. This serves as a project knowledge base but differs from traditional IDE extensions.

For developers requiring specific extensions, code can be exported and opened in local IDEs with full extension support [web:16][web:19].

## PRICING MODEL

Freemium with token-based subscription tiers [web:7][web:10]. Pricing structure (as of 2025):

- **Free tier**: Basic AI prompt usage (150,000 tokens/day, 1M tokens/month), basic deployment options [web:10]
- **Pro ($20/month)**: Enhanced token limits, npm package installation, private projects, backend/database integration [web:7][web:10]
- **Pro 50 ($50/month)**: Higher token allocation for part-time builders and freelancers [web:7]
- **Pro 100 ($100/month)**: 10M+ tokens/month for daily development work across multiple projects [web:7][web:10]
- **Pro 200 ($200/month)**: Maximum token allowance for full-time AI-assisted development [web:7]
- **Teams ($30/user/month)**: Team collaboration features, shared resources, priority support, centralized management [web:10][web:30]

Token consumption varies by AI model selection (Opus uses more than Haiku) [page:0]. The platform charges for AI code generation usage rather than deployment or hosting.

## MOBILE SUPPORT

Native mobile app generation via Expo integration [web:37][web:40][page:1]. Bolt.new supports building cross-platform mobile applications for iOS and Android using Expo framework [web:37][web:40].

**Capabilities**:
- Generate React Native mobile apps from text prompts [web:40]
- Device preview for iPhone and Android devices within Bolt interface [web:37]
- Testing on physical devices via Expo Go mobile app [web:37]
- Authentication and backend integration for mobile apps [web:37]
- Deployment options to web and app stores [web:37]

The Expo integration (announced February 2025) transforms Bolt.new from web-only to universal app builder [web:40]. However, this remains focused on React Native—native Swift/Kotlin development is not supported [page:1].

## PERFORMANCE OPTIMIZATION

Limited built-in optimization tooling [web:26][web:35]. Bolt.new does not include dedicated performance monitoring, bundle analysis tools, or automated code optimization features in the traditional sense.

**Performance considerations**: The WebContainer environment's efficiency depends on local device resources (RAM, CPU) [web:22][web:26]. Projects consuming excessive memory or having large dependency trees experience slower performance [web:26][web:35]. Regular cleanup of unused files and dependencies improves responsiveness [web:35].

Developers requiring advanced performance optimization must export code and use external tools (Lighthouse, webpack-bundle-analyzer, etc.) [web:16].

## SECURITY AND COMPLIANCE

No built-in security scanning or compliance features [web:36][web:39]. Bolt.new prioritizes rapid functionality generation over security hardening. AI-generated code often ships with:

- Exposed API keys and credentials in frontend bundles [web:36][web:39]
- Missing database Row Level Security (RLS) policies [web:39]
- Absent HTTP security headers (XSS, clickjacking protection) [web:36][web:39]
- Weak authentication implementations [web:36][web:39]

**Third-party solutions**: External security scanners like VibeAppScanner specifically target Bolt.new applications, detecting exposed secrets, database misconfigurations, and authentication issues [web:36][web:39]. These services report finding 4,100+ issues across 500+ scanned Bolt apps [web:39].

Developers must manually implement security best practices or use external scanning tools before production deployment.

## Key Differentiators

Bolt.new uniquely combines WebContainers' browser-native Node.js execution with multi-model AI selection (Haiku/Sonnet/Opus) for granular control over speed versus capability tradeoffs [page:0][web:25][web:28]. Unlike traditional cloud IDEs running on remote servers, all code execution occurs locally in the browser tab for enhanced security and performance [web:25]. The platform's one-click Netlify deployment with automated continuous delivery via GitHub integration creates a complete development-to-production loop without manual DevOps configuration [web:5][web:9]. The recent Expo integration extends capabilities beyond web to native iOS/Android mobile apps, positioning Bolt.new as a universal application builder rather than web-only tool [web:37][web:40].