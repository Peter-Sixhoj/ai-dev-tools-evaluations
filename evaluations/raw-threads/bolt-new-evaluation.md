# Bolt.new Evaluation

Bolt.new is an AI-powered, browser-based full-stack development platform created by StackBlitz that enables users to build complete web and mobile applications through natural language prompts without local environment setup[web:44][web:28].

## DEPLOYMENT MODEL

Bolt.new operates as a **cloud-hosted, browser-based platform** utilizing WebContainers technology to run Node.js directly in the browser[web:74]. This eliminates the need for local development environment setup, allowing users to develop, preview, and deploy applications entirely through a web interface[web:28]. The platform leverages WebAssembly to simulate a Linux-like environment within the browser, though this means it cannot execute native binaries or access system-level resources[web:75].

**Limitations**: The WebContainer environment restricts users to browser-native code (JavaScript and WebAssembly only), with no ability to run native system processes or access local file systems directly[web:75].

## PACKAGE MANAGEMENT

Bolt.new **fully supports standard package managers** including npm, pip, and other ecosystem-specific dependency managers[web:59]. The platform automatically handles `npm install` and `npm run dev` commands within its WebContainer environment[web:59]. Users can install arbitrary third-party dependencies as they would in a traditional development environment, with Bolt handling package resolution and installation through its virtualized Node.js runtime[web:28].

**Evidence**: GitHub issues and community discussions confirm that Bolt executes standard npm workflows, though occasionally users report timeout issues with complex dependency trees in the browser environment[web:59].

## CODE OWNERSHIP

Users **retain full ownership** of code generated in Bolt.new with multiple export options[web:53][web:55]. The platform provides:

- Direct download via Export > Download functionality from the project interface[web:55]
- Native GitHub integration allowing users to create repositories and push code directly to their GitHub accounts[web:51]
- Local import capabilities via StackBlitz for further development[web:66]

**Evidence**: Official documentation and user guides confirm that exported code can be managed independently outside Bolt's ecosystem, with no vendor lock-in restrictions[web:53][web:55].

## FRAMEWORK SUPPORT

Bolt.new supports a **comprehensive range of modern web frameworks and languages**[web:5][web:28]:

**Web frameworks**: React, Vue, Angular, Next.js, Vite, and other JavaScript/TypeScript-based frameworks
**Mobile frameworks**: React Native and Expo for cross-platform iOS and Android development (as of February 2025)[web:71][web:72]
**Languages**: JavaScript, TypeScript, HTML, CSS
**Backend**: Node.js-based server environments, Express, and similar Node.js frameworks

**Limitations**: The platform is primarily optimized for JavaScript/TypeScript ecosystems. While Python pip support exists for certain integrations, Bolt is not designed for pure Python, Go, or Rust application development[web:28]. Native iOS (Swift) and Android (Kotlin) compilation is not supported in-browser[web:74].

## GIT INTEGRATION

Bolt.new offers **native GitHub integration** with comprehensive version control capabilities[web:51][web:54]:

- Direct connection to individual GitHub accounts (organizational accounts not supported as of January 2026)[web:51]
- Repository creation from Bolt projects with automatic main branch initialization[web:51]
- Full branching and merging support with branch creation/switching directly in the Bolt interface[web:51]
- Import existing GitHub repositories into Bolt projects[web:51]
- Commit tracking with every completed AI prompt counting as a commit to the active branch[web:58]
- Pull request workflows enabling code review and merging back to main branches[web:58]

**Built-in version history**: Beyond GitHub, Bolt maintains internal version history with bookmark functionality allowing users to save progress snapshots at key milestones[web:58].

## MULTI-FILE CONTEXT AWARENESS

Bolt.new demonstrates **strong multi-file context awareness** through its diff feature (available in paid plans)[web:57][web:60]. The platform can:

- Understand relationships between files across the entire codebase[web:57]
- Apply surgical precision modifications to specific code segments without regenerating entire files[web:60]
- Maintain code coherence by analyzing surrounding context when making changes[web:57]
- Navigate directly to relevant code sections when given specific file paths and locations[web:57]

**Best practices**: The diff feature works most effectively when users provide clear file structure, descriptive naming conventions, and explicit location specifications for changes[web:57]. The system excels with well-organized codebases where separation of concerns is maintained[web:60].

## BACKEND CAPABILITIES

Bolt.new supports **full-stack development** including backend logic, databases, and APIs[web:41][web:28]:

**Database support**:
- Native Bolt databases (unlimited free databases on paid plans, introduced September 2025)[web:67]
- Full Supabase integration for PostgreSQL databases, authentication services, and edge functions[web:67]
- Database tables, stored procedures, and SQL operations[web:70]

**Backend features**:
- Server functions for API endpoints[web:67]
- Authentication and user management via Supabase or integrated services[web:67]
- Edge functions for third-party service integration (Stripe, OpenAI, etc.)[web:67]
- Real-time database operations and API communications[web:70]

**Evidence**: Official support documentation confirms that both Claude Agent and v1 Agent can generate complete backend architectures, though Claude Agent (introduced with v2) provides more sophisticated database and authentication scaffolding[web:61].

## COLLABORATION FEATURES

Bolt.new supports **Git-based collaboration workflows** rather than real-time multiplayer editing[web:58]:

- Branch-based development allowing multiple developers to work on separate features simultaneously[web:51]
- Pull request workflows for code review and merge approvals[web:58]
- Repository sharing via GitHub with collaborator access controls[web:58]
- No live cursors or simultaneous editing within the Bolt interface itself

**Use case**: Teams can share branches with remote developers or freelancers, who make changes in their own Bolt instances or local environments, then merge back through pull requests[web:58].

## DEPLOYMENT AUTOMATION

Bolt.new provides **integrated one-click deployment** to production environments[web:66][web:63]:

**Supported platforms**:
- Netlify (native integration with automatic deployment)[web:66]
- Vercel and other hosting providers
- Web hosting with automatic URL generation[web:66]
- Mobile app deployment via Expo Go for testing, with App Store/Google Play deployment requiring additional build steps[web:71][web:73]

**Workflow**: Users can generate applications, have Bolt automatically deploy to Netlify with live URLs, claim ownership by transferring to their Netlify team, and link to GitHub for version control[web:66]. Manual deployment is also supported via code download and external deployment pipelines[web:69].

**Mobile deployment limitation**: While Bolt generates React Native/Expo code that runs in Expo Go for testing, publishing to iOS App Store or Google Play requires external build services (EAS Build) or third-party tools like Natively.dev that wrap the web app in native containers[web:74].

## LOCAL DEVELOPMENT SUPPORT

Bolt.new operates **primarily as a cloud-dependent platform** with limited offline capabilities[web:28][web:44]:

**Cloud dependency**: The core Bolt.new experience requires an active internet connection and browser access, as WebContainers run entirely in-browser without local installation[web:28].

**Local development option**: Users can export code and continue development locally using:
- Downloaded project files for local IDE work[web:55]
- GitHub repository clones for standard Git workflows[web:51]
- Bolt.diy (open-source self-hosted version) for running Bolt locally with custom AI models[web:56][web:68]

**Bolt.diy**: The open-source fork available at github.com/stackblitz/bolt.new allows developers to self-host the platform with their own API keys (Claude, GPT-4, etc.), providing local development capability with Docker, npm, or pnpm installation[web:44][web:56][web:68].

## AI MODEL SELECTION

Bolt.new offers **multi-model support** through two agent systems[web:61]:

**Claude Agent** (recommended, introduced with v2):
- Claude 4.5 Haiku: Fast, cost-efficient for simple UI/content changes[web:61]
- Claude 4.5 Sonnet: Balanced performance, default model for everyday building[web:61]
- Claude 4.5 Opus: Highest reasoning for complex, enterprise-grade architectures[web:61]

**v1 Agent (legacy)**:
- Single model: Anthropic Claude Sonnet[web:61]
- Faster but produces lower-quality, incomplete results[web:61]

**Upcoming models**: LinkedIn announcements indicate OpenAI Codex and additional coding agents are being integrated into Bolt v2[web:65].

**Switching**: Users can change models mid-project within Claude Agent without losing chat context, though switching between Claude Agent and v1 Agent clears conversation history[web:61].

## IDE TYPE

Bolt.new is a **standalone web-based IDE** built on StackBlitz's WebContainers technology[web:28][web:44]. It is not a VS Code fork or extension, but rather a proprietary browser-based development environment with its own interface, file explorer, terminal emulator, and preview pane[web:28].

**Interface components**:
- AI chatbot for natural language instructions
- Code editor with syntax highlighting
- Integrated terminal for command execution
- Live preview pane for real-time application viewing
- File system browser for project navigation

**Relationship to VS Code**: While not based on VS Code, Bolt projects can be exported and opened in VS Code or other local IDEs through GitHub integration or direct download[web:51][web:55].

## CODEBASE SCALE LIMITS

Bolt.new exhibits **practical limitations for enterprise-scale repositories**[web:60][web:61]:

**Strengths**:
- Diff feature enables efficient handling of large codebases by modifying only relevant segments rather than regenerating entire files[web:60]
- Multi-file context awareness supports complex project structures with proper organization[web:57]
- Claude 4.5 Opus specifically designed for enterprise architectures and large refactors spanning many files[web:61]

**Limitations**:
- WebContainer environment constraints limit resource-intensive operations[web:75]
- Token consumption increases significantly with larger codebases, impacting cost on paid plans[web:60]
- Performance degradation reported for extremely complex dependency trees during npm install operations[web:59]

**Optimal use case**: Bolt excels at building production-quality applications from scratch and handling medium-sized projects, but may struggle with massive monorepo architectures or projects with hundreds of interdependent files[web:61].

## API/SERVICE INTEGRATION

Bolt.new demonstrates **strong third-party integration capabilities**[web:67][web:70]:

**Native integrations**:
- Supabase: Full support for PostgreSQL databases, authentication, edge functions, and storage[web:67]
- Stripe: Payment processing via edge functions[web:67]
- Clerk: Authentication services (as alternative to Supabase auth)[web:70]

**Custom integrations**: Edge functions enable developers to integrate any third-party API requiring server-side logic, including:
- OpenAI and other LLM APIs via secure server functions[web:67]
- REST and GraphQL APIs through backend endpoints
- Webhook receivers and external service communications

**Database options**:
- Built-in Bolt databases (unlimited on paid plans)[web:67]
- Supabase PostgreSQL with full SQL access[web:67]
- Connection to external database services via environment variables

**Configuration**: Secrets management through Bolt's settings interface allows secure storage of API keys and credentials for external service integration[web:67].

## CODE GENERATION SCOPE

Bolt.new generates **complete full-stack applications** rather than isolated components[web:28][web:63]:

**Scope includes**:
- Complete UI scaffolding with multiple pages and navigation[web:28]
- Backend logic including server functions and API endpoints[web:67]
- Database schema creation with tables and relationships[web:67][web:70]
- Authentication flows with signup, login, and user management[web:67]
- Deployment configuration for production environments[web:66]
- Mobile app scaffolding with React Native/Expo (cross-platform iOS/Android)[web:71][web:72]

**Not an inline code completion tool**: Unlike GitHub Copilot or Cursor's Tab completion, Bolt focuses on generating entire project structures from natural language descriptions rather than line-by-line autocomplete[web:28].

**Plan Mode**: Claude Agent includes Plan Mode, which develops detailed build strategies before execution, ensuring architectural coherence across generated code[web:61].

## EXTENSION ECOSYSTEM

Bolt.new **does not support traditional IDE extensions** like VS Code marketplace plugins[web:28]. As a standalone browser-based IDE, it operates within a closed ecosystem without extension APIs for third-party plugins.

**Alternatives**:
- Users can export code to VS Code for extension-based workflows[web:51][web:55]
- `claude.md` files can be uploaded to provide project-specific instructions and context, offering some customization capability[web:61]
- Bolt.diy open-source version may offer more extensibility for self-hosted deployments[web:56]

**Limitation**: This represents a significant constraint for developers who rely heavily on linting tools, custom formatters, or specialized development extensions in their daily workflows.

## PRICING MODEL

Bolt.new operates on a **freemium subscription model** with multiple tiers[web:7][web:10][web:46]:

**Free tier**: Available with limited functionality and token usage
**Paid plans**: Starting at approximately $20/month (as of January 2025)[web:48]

**Features by tier**:
- **Free**: Basic project creation, limited AI interactions
- **Paid**: Unlimited Bolt databases, diff feature, Plan Mode, Claude 4.5 model selection (Haiku/Sonnet/Opus), enhanced token limits, GitHub integration, Supabase connectivity[web:61][web:60]

**Token economics**: Claude Agent uses more tokens per request but typically results in fewer overall tokens spent due to higher-quality output requiring less iteration[web:61]. Users can manage costs by selecting appropriate models (Haiku for simple tasks, Opus for complex work)[web:61].

**Enterprise**: Pricing information for enterprise-scale deployments not publicly detailed in available sources.

## MOBILE SUPPORT

Bolt.new provides **native mobile app generation** through React Native and Expo integration (launched February 2025)[web:71][web:72][web:73]:

**Capabilities**:
- Cross-platform iOS and Android app generation from prompts[web:71][web:72]
- React Native framework with Expo for development and testing[web:71]
- Expo Go mobile app for real-device testing during development[web:73]
- Full authentication, database, and backend integration for mobile apps[web:71][web:73]

**Deployment workflow**:
1. Generate mobile app in Bolt using React Native/Expo[web:72]
2. Test on multiple device previews (iPhone, Pixel) in browser[web:73]
3. Test on physical devices via Expo Go app[web:73]
4. Deploy to web instantly via Bolt's hosting[web:73]
5. For App Store/Google Play: Export to EAS Build or use third-party wrapper services like Natively.dev[web:74]

**Native build limitation**: iOS and Android apps cannot be compiled to native binaries within the browser due to WebContainer constraints (requires Xcode and Android Studio)[web:74]. Users must use external build services for app store submission[web:74].

## PERFORMANCE OPTIMIZATION

Bolt.new includes **automated performance features** with varying levels of sophistication[web:60][web:61]:

**Built-in optimizations**:
- Diff-based code modifications reduce token consumption and processing overhead by avoiding full file regeneration[web:60]
- WebContainer technology provides optimized browser-based runtime for Node.js applications[web:28]
- Automatic build process optimization via `npm run build` commands[web:69]

**Model-based optimization**: Claude 4.5 Opus specifically designed for handling complex refactors that require system-wide optimization decisions[web:61].

**Limitations**: Bolt does not provide dedicated bundle analysis tools, performance profiling dashboards, or automated code splitting beyond what the chosen framework (Vite, Next.js, etc.) provides by default. Users must export projects and use external tools like Lighthouse or Webpack Bundle Analyzer for detailed performance auditing.

## SECURITY AND COMPLIANCE

Bolt.new has introduced **automated security scanning capabilities** (as of November 2025)[web:76]:

**Security features**:
- Automated security audits during the publishing process[web:76]
- Vulnerability detection with developer alerts[web:76]
- "Ask Bolt to fix" button for automated vulnerability remediation[web:76]
- Google SSO integration for reduced authentication friction[web:76]
- Secrets management for secure API key storage[web:67]

**Authentication**:
- Built-in user authentication via Supabase integration[web:67]
- Support for third-party auth providers like Clerk[web:70]
- Google Single Sign-On for end-user access[web:76]

**Compliance**: No specific compliance certifications (SOC 2, ISO 27001, GDPR) documented for the Bolt.new platform itself in available sources. Applications built with Bolt can implement compliance requirements through Supabase's security features and proper architectural patterns, but this is developer-managed rather than platform-enforced[web:79].

**Limitation**: Enterprise-grade compliance features and audit trails are not explicitly documented in official Bolt.new materials as of February 2026.

## Key Differentiators

**Browser-native full-stack development**: Bolt.new's WebContainers technology uniquely enables complete Node.js runtime execution directly in the browser without local environment setup, distinguishing it from traditional IDEs and even other AI coding tools like Cursor or GitHub Copilot that require local installations[web:28][web:74].

**Multi-model AI flexibility**: Unlike single-model platforms, Bolt offers three Claude 4.5 variants (Haiku, Sonnet, Opus) allowing developers to optimize for speed, capability, or cost depending on task complexity—a granularity uncommon in AI coding platforms[web:61].

**Integrated production pipeline**: The seamless flow from natural language prompt to deployed production URL (via Netlify/Vercel) with built-in database provisioning, authentication, and GitHub version control creates an end-to-end development experience that minimizes context switching[web:66][web:67].

**Diff-based intelligent editing**: The surgical code modification approach that changes only relevant segments rather than regenerating entire files significantly reduces token waste and maintains code stability, particularly valuable for iterative development on larger projects[web:60].

**True full-stack scope**: While many AI coding tools focus on frontend or require separate backend setup, Bolt generates complete applications including database schemas, server functions, authentication flows, and API integrations in a unified workflow[web:67][web:70].