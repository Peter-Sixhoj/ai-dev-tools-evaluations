# Bolt.new Evaluation

Bolt.new is an AI-powered, browser-based full-stack development platform created by StackBlitz that enables users to build complete web and mobile applications through natural language prompts without local environment setup.

## DEPLOYMENT MODEL

Bolt.new operates as a **cloud-hosted, browser-based platform** utilizing WebContainers technology to run Node.js directly in the browser. This eliminates the need for local development environment setup, allowing users to develop, preview, and deploy applications entirely through a web interface. The platform leverages WebAssembly to simulate a Linux-like environment within the browser, though this means it cannot execute native binaries or access system-level resources.

**Limitations**: The WebContainer environment restricts users to browser-native code (JavaScript and WebAssembly only), with no ability to run native system processes or access local file systems directly.

## PACKAGE MANAGEMENT

Bolt.new **fully supports standard package managers** including npm, pip, and other ecosystem-specific dependency managers. The platform automatically handles `npm install` and `npm run dev` commands within its WebContainer environment. Users can install arbitrary third-party dependencies as they would in a traditional development environment, with Bolt handling package resolution and installation through its virtualized Node.js runtime.

**Evidence**: GitHub issues and community discussions confirm that Bolt executes standard npm workflows, though occasionally users report timeout issues with complex dependency trees in the browser environment.

## CODE OWNERSHIP

Users **retain full ownership** of code generated in Bolt.new with multiple export options. The platform provides:

- Direct download via Export > Download functionality from the project interface
- Native GitHub integration allowing users to create repositories and push code directly to their GitHub accounts
- Local import capabilities via StackBlitz for further development

**Evidence**: Official documentation and user guides confirm that exported code can be managed independently outside Bolt's ecosystem, with no vendor lock-in restrictions.

## FRAMEWORK SUPPORT

Bolt.new supports a **comprehensive range of modern web frameworks and languages**:

**Web frameworks**: React, Vue, Angular, Next.js, Vite, and other JavaScript/TypeScript-based frameworks
**Mobile frameworks**: React Native and Expo for cross-platform iOS and Android development (as of February 2025)
**Languages**: JavaScript, TypeScript, HTML, CSS
**Backend**: Node.js-based server environments, Express, and similar Node.js frameworks

**Limitations**: The platform is primarily optimized for JavaScript/TypeScript ecosystems. While Python pip support exists for certain integrations, Bolt is not designed for pure Python, Go, or Rust application development. Native iOS (Swift) and Android (Kotlin) compilation is not supported in-browser.

## GIT INTEGRATION

Bolt.new offers **native GitHub integration** with comprehensive version control capabilities:

- Direct connection to individual GitHub accounts (organizational accounts not supported as of January 2026)
- Repository creation from Bolt projects with automatic main branch initialization
- Full branching and merging support with branch creation/switching directly in the Bolt interface
- Import existing GitHub repositories into Bolt projects
- Commit tracking with every completed AI prompt counting as a commit to the active branch
- Pull request workflows enabling code review and merging back to main branches

**Built-in version history**: Beyond GitHub, Bolt maintains internal version history with bookmark functionality allowing users to save progress snapshots at key milestones.

## MULTI-FILE CONTEXT AWARENESS

Bolt.new demonstrates **strong multi-file context awareness** through its diff feature (available in paid plans). The platform can:

- Understand relationships between files across the entire codebase
- Apply surgical precision modifications to specific code segments without regenerating entire files
- Maintain code coherence by analyzing surrounding context when making changes
- Navigate directly to relevant code sections when given specific file paths and locations

**Best practices**: The diff feature works most effectively when users provide clear file structure, descriptive naming conventions, and explicit location specifications for changes. The system excels with well-organized codebases where separation of concerns is maintained.

## BACKEND CAPABILITIES

Bolt.new supports **full-stack development** including backend logic, databases, and APIs:

**Database support**:
- Native Bolt databases (unlimited free databases on paid plans, introduced September 2025)
- Full Supabase integration for PostgreSQL databases, authentication services, and edge functions
- Database tables, stored procedures, and SQL operations

**Backend features**:
- Server functions for API endpoints
- Authentication and user management via Supabase or integrated services
- Edge functions for third-party service integration (Stripe, OpenAI, etc.)
- Real-time database operations and API communications

**Evidence**: Official support documentation confirms that both Claude Agent and v1 Agent can generate complete backend architectures, though Claude Agent (introduced with v2) provides more sophisticated database and authentication scaffolding.

## COLLABORATION FEATURES

Bolt.new supports **Git-based collaboration workflows** rather than real-time multiplayer editing:

- Branch-based development allowing multiple developers to work on separate features simultaneously
- Pull request workflows for code review and merge approvals
- Repository sharing via GitHub with collaborator access controls
- No live cursors or simultaneous editing within the Bolt interface itself

**Use case**: Teams can share branches with remote developers or freelancers, who make changes in their own Bolt instances or local environments, then merge back through pull requests.

## DEPLOYMENT AUTOMATION

Bolt.new provides **integrated one-click deployment** to production environments:

**Supported platforms**:
- Netlify (native integration with automatic deployment)
- Vercel and other hosting providers
- Web hosting with automatic URL generation
- Mobile app deployment via Expo Go for testing, with App Store/Google Play deployment requiring additional build steps

**Workflow**: Users can generate applications, have Bolt automatically deploy to Netlify with live URLs, claim ownership by transferring to their Netlify team, and link to GitHub for version control. Manual deployment is also supported via code download and external deployment pipelines.

**Mobile deployment limitation**: While Bolt generates React Native/Expo code that runs in Expo Go for testing, publishing to iOS App Store or Google Play requires external build services (EAS Build) or third-party tools like Natively.dev that wrap the web app in native containers.

## LOCAL DEVELOPMENT SUPPORT

Bolt.new operates **primarily as a cloud-dependent platform** with limited offline capabilities:

**Cloud dependency**: The core Bolt.new experience requires an active internet connection and browser access, as WebContainers run entirely in-browser without local installation.

**Local development option**: Users can export code and continue development locally using:
- Downloaded project files for local IDE work
- GitHub repository clones for standard Git workflows
- Bolt.diy (open-source self-hosted version) for running Bolt locally with custom AI models

**Bolt.diy**: The open-source fork available at github.com/stackblitz/bolt.new allows developers to self-host the platform with their own API keys (Claude, GPT-4, etc.), providing local development capability with Docker, npm, or pnpm installation.

## AI MODEL SELECTION

Bolt.new offers **multi-model support** through two agent systems:

**Claude Agent** (recommended, introduced with v2):
- Claude 4.5 Haiku: Fast, cost-efficient for simple UI/content changes
- Claude 4.5 Sonnet: Balanced performance, default model for everyday building
- Claude 4.5 Opus: Highest reasoning for complex, enterprise-grade architectures

**v1 Agent (legacy)**:
- Single model: Anthropic Claude Sonnet
- Faster but produces lower-quality, incomplete results

**Upcoming models**: LinkedIn announcements indicate OpenAI Codex and additional coding agents are being integrated into Bolt v2.

**Switching**: Users can change models mid-project within Claude Agent without losing chat context, though switching between Claude Agent and v1 Agent clears conversation history.

## IDE TYPE

Bolt.new is a **standalone web-based IDE** built on StackBlitz's WebContainers technology. It is not a VS Code fork or extension, but rather a proprietary browser-based development environment with its own interface, file explorer, terminal emulator, and preview pane.

**Interface components**:
- AI chatbot for natural language instructions
- Code editor with syntax highlighting
- Integrated terminal for command execution
- Live preview pane for real-time application viewing
- File system browser for project navigation

**Relationship to VS Code**: While not based on VS Code, Bolt projects can be exported and opened in VS Code or other local IDEs through GitHub integration or direct download.

## CODEBASE SCALE LIMITS

Bolt.new exhibits **practical limitations for enterprise-scale repositories**:

**Strengths**:
- Diff feature enables efficient handling of large codebases by modifying only relevant segments rather than regenerating entire files
- Multi-file context awareness supports complex project structures with proper organization
- Claude 4.5 Opus specifically designed for enterprise architectures and large refactors spanning many files

**Limitations**:
- WebContainer environment constraints limit resource-intensive operations
- Token consumption increases significantly with larger codebases, impacting cost on paid plans
- Performance degradation reported for extremely complex dependency trees during npm install operations

**Optimal use case**: Bolt excels at building production-quality applications from scratch and handling medium-sized projects, but may struggle with massive monorepo architectures or projects with hundreds of interdependent files.

## API/SERVICE INTEGRATION

Bolt.new demonstrates **strong third-party integration capabilities**:

**Native integrations**:
- Supabase: Full support for PostgreSQL databases, authentication, edge functions, and storage
- Stripe: Payment processing via edge functions
- Clerk: Authentication services (as alternative to Supabase auth)

**Custom integrations**: Edge functions enable developers to integrate any third-party API requiring server-side logic, including:
- OpenAI and other LLM APIs via secure server functions
- REST and GraphQL APIs through backend endpoints
- Webhook receivers and external service communications

**Database options**:
- Built-in Bolt databases (unlimited on paid plans)
- Supabase PostgreSQL with full SQL access
- Connection to external database services via environment variables

**Configuration**: Secrets management through Bolt's settings interface allows secure storage of API keys and credentials for external service integration.

## CODE GENERATION SCOPE

Bolt.new generates **complete full-stack applications** rather than isolated components:

**Scope includes**:
- Complete UI scaffolding with multiple pages and navigation
- Backend logic including server functions and API endpoints
- Database schema creation with tables and relationships
- Authentication flows with signup, login, and user management
- Deployment configuration for production environments
- Mobile app scaffolding with React Native/Expo (cross-platform iOS/Android)

**Not an inline code completion tool**: Unlike GitHub Copilot or Cursor's Tab completion, Bolt focuses on generating entire project structures from natural language descriptions rather than line-by-line autocomplete.

**Plan Mode**: Claude Agent includes Plan Mode, which develops detailed build strategies before execution, ensuring architectural coherence across generated code.

## EXTENSION ECOSYSTEM

Bolt.new **does not support traditional IDE extensions** like VS Code marketplace plugins. As a standalone browser-based IDE, it operates within a closed ecosystem without extension APIs for third-party plugins.

**Alternatives**:
- Users can export code to VS Code for extension-based workflows
- `claude.md` files can be uploaded to provide project-specific instructions and context, offering some customization capability
- Bolt.diy open-source version may offer more extensibility for self-hosted deployments

**Limitation**: This represents a significant constraint for developers who rely heavily on linting tools, custom formatters, or specialized development extensions in their daily workflows.

## PRICING MODEL

Bolt.new operates on a **freemium subscription model** with multiple tiers:

**Free tier**: Available with limited functionality and token usage
**Paid plans**: Starting at approximately $20/month (as of January 2025)

**Features by tier**:
- **Free**: Basic project creation, limited AI interactions
- **Paid**: Unlimited Bolt databases, diff feature, Plan Mode, Claude 4.5 model selection (Haiku/Sonnet/Opus), enhanced token limits, GitHub integration, Supabase connectivity

**Token economics**: Claude Agent uses more tokens per request but typically results in fewer overall tokens spent due to higher-quality output requiring less iteration. Users can manage costs by selecting appropriate models (Haiku for simple tasks, Opus for complex work).

**Enterprise**: Pricing information for enterprise-scale deployments not publicly detailed in available sources.

## MOBILE SUPPORT

Bolt.new provides **native mobile app generation** through React Native and Expo integration (launched February 2025):

**Capabilities**:
- Cross-platform iOS and Android app generation from prompts
- React Native framework with Expo for development and testing
- Expo Go mobile app for real-device testing during development
- Full authentication, database, and backend integration for mobile apps

**Deployment workflow**:
1. Generate mobile app in Bolt using React Native/Expo
2. Test on multiple device previews (iPhone, Pixel) in browser
3. Test on physical devices via Expo Go app
4. Deploy to web instantly via Bolt's hosting
5. For App Store/Google Play: Export to EAS Build or use third-party wrapper services like Natively.dev

**Native build limitation**: iOS and Android apps cannot be compiled to native binaries within the browser due to WebContainer constraints (requires Xcode and Android Studio). Users must use external build services for app store submission.

## PERFORMANCE OPTIMIZATION

Bolt.new includes **automated performance features** with varying levels of sophistication:

**Built-in optimizations**:
- Diff-based code modifications reduce token consumption and processing overhead by avoiding full file regeneration
- WebContainer technology provides optimized browser-based runtime for Node.js applications
- Automatic build process optimization via `npm run build` commands

**Model-based optimization**: Claude 4.5 Opus specifically designed for handling complex refactors that require system-wide optimization decisions.

**Limitations**: Bolt does not provide dedicated bundle analysis tools, performance profiling dashboards, or automated code splitting beyond what the chosen framework (Vite, Next.js, etc.) provides by default. Users must export projects and use external tools like Lighthouse or Webpack Bundle Analyzer for detailed performance auditing.

## SECURITY AND COMPLIANCE

Bolt.new has introduced **automated security scanning capabilities** (as of November 2025):

**Security features**:
- Automated security audits during the publishing process
- Vulnerability detection with developer alerts
- "Ask Bolt to fix" button for automated vulnerability remediation
- Google SSO integration for reduced authentication friction
- Secrets management for secure API key storage

**Authentication**:
- Built-in user authentication via Supabase integration
- Support for third-party auth providers like Clerk
- Google Single Sign-On for end-user access

**Compliance**: No specific compliance certifications (SOC 2, ISO 27001, GDPR) documented for the Bolt.new platform itself in available sources. Applications built with Bolt can implement compliance requirements through Supabase's security features and proper architectural patterns, but this is developer-managed rather than platform-enforced.

**Limitation**: Enterprise-grade compliance features and audit trails are not explicitly documented in official Bolt.new materials as of February 2026.

## Key Differentiators

**Browser-native full-stack development**: Bolt.new's WebContainers technology uniquely enables complete Node.js runtime execution directly in the browser without local environment setup, distinguishing it from traditional IDEs and even other AI coding tools like Cursor or GitHub Copilot that require local installations.

**Multi-model AI flexibility**: Unlike single-model platforms, Bolt offers three Claude 4.5 variants (Haiku, Sonnet, Opus) allowing developers to optimize for speed, capability, or cost depending on task complexity—a granularity uncommon in AI coding platforms.

**Integrated production pipeline**: The seamless flow from natural language prompt to deployed production URL (via Netlify/Vercel) with built-in database provisioning, authentication, and GitHub version control creates an end-to-end development experience that minimizes context switching.

**Diff-based intelligent editing**: The surgical code modification approach that changes only relevant segments rather than regenerating entire files significantly reduces token waste and maintains code stability, particularly valuable for iterative development on larger projects.

**True full-stack scope**: While many AI coding tools focus on frontend or require separate backend setup, Bolt generates complete applications including database schemas, server functions, authentication flows, and API integrations in a unified workflow.

---

**Evaluation completed**: February 3, 2026
**Repository**: [Peter-Sixhoj/ai-dev-tools-evaluations](https://github.com/Peter-Sixhoj/ai-dev-tools-evaluations)
**File path**: `/evaluations/raw-threads/bolt-new-evaluation.md`