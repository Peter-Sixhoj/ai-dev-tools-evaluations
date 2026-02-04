# AI Development Tools Comparison Report

**Report Date**: 2026-02-04  
**Evaluator**: AI Development Tools Evaluator v2.0  
**Tools Evaluated**: 6 platforms  
**Evaluation Framework**: evaluation-metrics.md v2.0 (103 decision questions across 21 metrics)

---

## Executive Summary

This report compares six AI-powered development tools against standardized criteria covering deployment, code ownership, framework support, collaboration, and 17 other dimensions. Each tool was evaluated on 103 decision questions, scored on a 100-point scale with weighted priorities (MUST-HAVE: 40 points, SHOULD-HAVE: 45 points, NICE-TO-HAVE: 15 points).

## Conclusion

For **enterprise teams requiring code portability**, only **Cursor, Windsurf, Bolt.new, and Replit** pass all critical requirements. Cursor and Windsurf lead for large-scale codebases with polyglot support, while Bolt.new and Replit excel at rapid prototyping with zero setup.

**Lovable** offers fast prototyping but creates Supabase dependency. **Base44** provides extreme convenience but severe vendor lock-in makes it unsuitable for teams requiring portable, self-sufficient code.

The choice between top-tier tools (Cursor vs. Windsurf vs. Bolt.new vs. Replit) depends on:
1. **Deployment model preference**: Desktop (Cursor/Windsurf) vs. Cloud (Bolt.new/Replit)
2. **Language requirements**: Polyglot (Cursor/Windsurf/Replit) vs. JavaScript-only (Bolt.new)
3. **Collaboration needs**: Async Git (Cursor/Windsurf) vs. Real-time (Bolt.new/Replit)
4. **Budget constraints**: Windsurf ($15) vs. Cursor ($20) vs. Bolt.new ($20) vs. Replit ($25-40)
5. **Quick prototyping**: Full-stack scaffolding (Bolt.new/Lovable/Replit) vs. Incremental development (Cursor/Windsurf)

All four qualified tools provide enterprise-grade AI development capabilities with zero vendor lock-in—the final choice depends on team-specific priorities.### Overall Rankings

| Rank | Tool | Total Score | MUST-HAVE | SHOULD-HAVE | NICE-TO-HAVE | Status |
|------|------|-------------|-----------|-------------|--------------|--------|
| 1 | **Replit** | 85/100 | 40/40 ✅ | 35.5/45 | 9.5/15 | ✅ All critical passed |
| 2 | **Cursor** | 84/100 | 40/40 ✅ | 36/45 | 8/15 | ✅ All critical passed |
| 3 | **Windsurf** | 84/100 | 40/40 ✅ | 36/45 | 8/15 | ✅ All critical passed |
| 4 | **Bolt.new** | 73/100 | 40/40 ✅ | 25/45 | 8/15 | ✅ All critical passed |
| 5 | **Lovable** | 60/100 | 30/40 ⚠️ | 23/45 | 7/15 | ⚠️ 1 critical failed |
| 6 | **Base44** | 43.5/100 | 10/40 ❌ | 26/45 | 7.5/15 | ❌ 3 critical failed |

### Critical Finding: Only 4 Tools Pass All MUST-HAVE Requirements

**MUST-HAVE Requirements (Deal-Breakers)**:
1. **1.1b**: Applications deployable outside platform
2. **3.1**: Export 100% of code
3. **3.2**: No proprietary runtime dependencies
4. **10.1**: Standard dev commands work (npm start, cargo run)

**❌ DISQUALIFIED**:
- **Base44**: Fails 3/4 (severe vendor lock-in; requires @base44/sdk and platform backend)
- **Lovable**: Fails 1/4 (requires platform for deployment; cannot export independently runnable apps)

**✅ QUALIFIED** (Pass all 4 MUST-HAVE):
- Cursor, Windsurf, Bolt.new, Replit

---

## Detailed Comparison by Metric

### 1. Deployment Model

| Tool | Self-Host IDE<br><sub>🟢 NICE-TO-HAVE</sub> | Deploy Outside Platform<br><sub>🔴 MUST-HAVE</sub> | Air-Gap Support<br><sub>🟢 NICE-TO-HAVE</sub> | Local Desktop App<br><sub>🟡 SHOULD-HAVE</sub> | IDE Location<br><sub>🟡 SHOULD-HAVE</sub> | AI Processing<br><sub>🟡 SHOULD-HAVE</sub> | Web Version<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|-------------|---------------------|----------------|------------------|--------------|----------------|--------------|
| **Cursor** | ❌ No (deprecated) | ✅ Yes | ❌ No | ✅ Desktop | Local | Cloud API | ❌ No |
| **Windsurf** | ❌ No (deprecated) | ✅ Yes | ❌ No | ✅ Desktop | Local | Cloud API | ❌ No |
| **Bolt.new** | ❌ No | ✅ Yes | ❌ No | ❌ No | Cloud (browser) | Cloud API | ✅ Yes |
| **Replit** | ❌ No | ✅ Yes | ❌ No | ❌ No | Cloud (browser) | Cloud API | ✅ Yes |
| **Lovable** | ❌ No | ⚠️ Requires Supabase | ❌ No | ❌ No | Cloud (browser) | Cloud API | ✅ Yes |
| **Base44** | ❌ No | ❌ Requires platform | ❌ No | ❌ No | Cloud (browser) | Cloud API | ✅ Yes |

**Key Insight**: Desktop IDEs (Cursor, Windsurf) offer better performance and offline editing; cloud IDEs (Bolt.new, Replit, Lovable, Base44) enable zero-setup onboarding. No tool supports true air-gapped development—all require internet for AI features. **Base44 fails critical requirement 1.1b** (cannot deploy outside platform).

**Winner**: Cursor, Windsurf (desktop flexibility + cloud AI)

---

### 2. Package Management

| Tool | npm Support<br><sub>🟡 SHOULD-HAVE</sub> | cargo (Rust)<br><sub>🟢 NICE-TO-HAVE</sub> | Monorepo Support<br><sub>🟡 SHOULD-HAVE</sub> | pip (Python)<br><sub>🟢 NICE-TO-HAVE</sub> | Package Restrictions<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|------------|----------|----------------|----------|---------------------|
| **Cursor** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ❌ Unrestricted |
| **Windsurf** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ❌ Unrestricted |
| **Bolt.new** | ✅ Yes | ❌ No | ⚠️ Limited | ❌ No | ❌ Unrestricted |
| **Replit** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes (uv) | ❌ Unrestricted |
| **Lovable** | ✅ Yes | ❌ No | ❌ No | ❌ No | ❌ Unrestricted |
| **Base44** | ⚠️ Limited (AI approval) | ❌ No | ❌ No | ❌ No | ✅ Yes (restrictions exist) |

**Key Insight**: Desktop IDEs and Replit support all major package managers. Cloud platforms (Bolt.new, Lovable, Base44) focus on JavaScript/TypeScript only. **Base44 restricts package installation** requiring AI chat approval and CDN workarounds.

**Winner**: Cursor, Windsurf, Replit (full polyglot package management)

---

### 3. Code Ownership & Portability (CRITICAL)

| Tool | Export 100% Code<br><sub>🔴 MUST-HAVE</sub> | No Proprietary SDK<br><sub>🔴 MUST-HAVE</sub> | Standard Format<br><sub>🟡 SHOULD-HAVE</sub> | Runs Standalone<br><sub>🟡 SHOULD-HAVE</sub> | Export Version Control<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|-------------|-------------------|-----------------|-----------------|-----------------------|
| **Cursor** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ npm install only | ✅ Yes |
| **Windsurf** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ npm install only | ✅ Yes |
| **Bolt.new** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ npm install only | ✅ Yes |
| **Replit** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ npm install only | ✅ Yes |
| **Lovable** | ✅ Yes | ⚠️ Partial (Supabase) | ✅ Yes | ⚠️ Requires Supabase | ✅ Yes |
| **Base44** | ✅ Yes | ❌ @base44/sdk required | ✅ Yes | ❌ Requires Base44 backend | ✅ Yes |

**Critical Failures**:
- **Base44**: Cannot run independently; requires @base44/sdk + Base44 backend for database, auth, storage (**FAILS 3.2**)
- **Lovable**: Requires Supabase for backend; cannot deploy to non-Supabase infrastructure (**PARTIAL FAIL 3.2**)

**Winner**: Cursor, Windsurf, Bolt.new, Replit (zero vendor lock-in)

---

### 4. Framework Support

| Tool | TypeScript<br><sub>🟡 SHOULD-HAVE</sub> | Rust + LSP<br><sub>🟢 NICE-TO-HAVE</sub> | React/Next.js<br><sub>🟡 SHOULD-HAVE</sub> | Python<br><sub>🟡 SHOULD-HAVE</sub> | Go<br><sub>🟡 SHOULD-HAVE</sub> | Vue.js<br><sub>🟢 NICE-TO-HAVE</sub> | Angular<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|-----------|------|--------------|--------|----|----|---------|
| **Cursor** | ✅ First-class | ✅ Full LSP | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Windsurf** | ✅ First-class | ✅ Full LSP | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Bolt.new** | ✅ First-class | ❌ No | ✅ Yes | ❌ No | ❌ No | ✅ Yes | ✅ Yes |
| **Replit** | ✅ First-class | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Lovable** | ✅ First-class | ❌ No | ✅ Yes (React) | ❌ No | ❌ No | ❌ No | ❌ No |
| **Base44** | ✅ First-class | ❌ No | ✅ Yes (React) | ❌ No | ❌ No | ❌ No | ❌ No |

**Key Insight**: 
- **Polyglot Champions**: Cursor, Windsurf, Replit (support all target languages)
- **JavaScript-Only**: Bolt.new, Lovable, Base44 (React/Node.js locked)
- **Rust LSP**: Only Cursor, Windsurf, Replit provide full rust-analyzer integration

**Winner**: Cursor, Windsurf (full stack + Rust LSP + Python + Go)

---

### 5. Git Integration

| Tool | Native Git<br><sub>🟡 SHOULD-HAVE</sub> | Push to GitHub/GitLab<br><sub>🟡 SHOULD-HAVE</sub> | PR Workflows<br><sub>🟡 SHOULD-HAVE</sub> | Visual Git UI<br><sub>🟢 NICE-TO-HAVE</sub> | Branch Management<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|------------|----------------------|--------------|--------------|--------------------|
| **Cursor** | ✅ Yes | ✅ GitHub only | ✅ Yes | ✅ Yes | ✅ Yes |
| **Windsurf** | ✅ Yes | ✅ GitHub only | ✅ Yes (PR reviews) | ✅ Yes | ✅ Yes |
| **Bolt.new** | ✅ Yes | ✅ GitHub only | ✅ Yes | ✅ Yes | ✅ Yes |
| **Replit** | ✅ Yes | ✅ GitHub (GitLab CLI) | ✅ Yes | ✅ Yes | ✅ Yes |
| **Lovable** | ✅ Yes | ✅ GitHub only | ✅ Yes | ✅ Yes | ✅ Yes |
| **Base44** | ✅ Yes (Dec 2025) | ✅ GitHub only | ✅ Yes | ❌ No | ✅ Yes (via GitHub) |

**Key Insight**: All tools support GitHub integration with 2-way sync. Only Windsurf has dedicated PR automation features. Replit supports GitLab via CLI (not native).

**Winner (Real-time)**: Replit (GitHub + GitLab CLI)  
**Winner (Enterprise)**: Windsurf (PR automation + RBAC)

---

### 6. Multi-file Context Awareness

| Tool | Understand Relationships<br><sub>🟡 SHOULD-HAVE</sub> | Cross-file Refactor<br><sub>🟡 SHOULD-HAVE</sub> | Max Context Size<br><sub>🟡 SHOULD-HAVE</sub> | Consistency<br><sub>🟢 NICE-TO-HAVE</sub> | Codebase Analysis<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------------------|-------------------|------------------|-------------|---------------------|
| **Cursor** | ✅ Yes | ✅ Yes | 200K tokens | ✅ Yes | ✅ Yes (RAG indexing) |
| **Windsurf** | ✅ Yes | ✅ Yes (Cascade) | 200K tokens | ✅ Yes | ✅ Yes (RAG indexing) |
| **Bolt.new** | ✅ Yes | ✅ Yes | 200K-500K tokens | ✅ Yes | ⚠️ Limited |
| **Replit** | ✅ Yes | ✅ Yes | 128K tokens | ✅ Yes | ⚠️ Limited |
| **Lovable** | ✅ Yes | ✅ Yes | Not documented | ✅ Yes | ⚠️ Limited |
| **Base44** | ✅ Yes | ✅ Yes | Not documented | ✅ Yes | ⚠️ Limited |

**Key Insight**: Cursor & Windsurf use RAG-based indexing for unlimited file awareness. Cloud platforms rely on context windows (128K-500K tokens). Bolt.new can hit "Project too large" errors requiring .boltignore.

**Winner**: Cursor, Windsurf (RAG indexing + 200K context)

---

### 7. Backend Capabilities

| Tool | Backend Languages<br><sub>🟡 SHOULD-HAVE</sub> | Database Schemas<br><sub>🟡 SHOULD-HAVE</sub> | API Generation<br><sub>🟡 SHOULD-HAVE</sub> | Full-Stack Scaffold<br><sub>🟢 NICE-TO-HAVE</sub> | Frontend/Backend Integration<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|------------------|-----------------|----------------|---------------------|----------------------------|
| **Cursor** | All (manual coding) | ✅ Yes | ✅ Both (REST/GraphQL) | ✅ Yes | ✅ Yes |
| **Windsurf** | All (manual coding) | ✅ Yes | ✅ Both (REST/GraphQL) | ✅ Yes | ✅ Yes |
| **Bolt.new** | Node.js only | ✅ Yes (Supabase/Prisma) | ✅ Both | ✅ Yes | ✅ Yes |
| **Replit** | Node.js, Python, Go, Rust | ✅ Yes (PostgreSQL) | ✅ Both | ✅ Yes | ✅ Yes |
| **Lovable** | Node.js serverless | ✅ Yes (Supabase) | ✅ REST | ✅ Yes | ✅ Yes |
| **Base44** | TypeScript only | ✅ Yes | ✅ REST | ✅ Yes | ✅ Yes |

**Key Insight**: All tools generate full-stack applications. Desktop IDEs support all languages (user codes manually with AI assistance). Cloud platforms auto-generate but limit backend languages.

**Winner**: Replit (automatic generation + 4 backend languages), Cursor/Windsurf (manual but unlimited)

---

### 8. Collaboration Features

| Tool | Real-time Multiplayer<br><sub>🟢 NICE-TO-HAVE</sub> | Git Workflows<br><sub>🟡 SHOULD-HAVE</sub> | Role-based Permissions<br><sub>🟢 NICE-TO-HAVE</sub> | Multiple Devs Simultaneously<br><sub>🟢 NICE-TO-HAVE</sub> | Code Review<br><sub>🟢 NICE-TO-HAVE</sub> | Live Cursors<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------------------|---------------------|---------------------|----------------------------|--------------|-------------|
| **Cursor** | ❌ No | ✅ Yes (GitHub) | ❌ No | ❌ No | ⚠️ Limited | ❌ No |
| **Windsurf** | ❌ No | ✅ Yes (GitHub PR) | ✅ Teams+ | ❌ No | ✅ Yes (PR automation) | ❌ No |
| **Bolt.new** | ✅ Yes (Teams) | ✅ Yes (GitHub) | ✅ Teams | ✅ Yes | ❌ No | ✅ Yes |
| **Replit** | ✅ Yes | ✅ Yes (GitHub/GitLab) | ✅ Yes | ✅ Yes | ✅ Yes (via GitHub) | ✅ Yes |
| **Lovable** | ✅ Yes | ✅ Yes (GitHub) | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes |
| **Base44** | ✅ Yes | ✅ Yes (GitHub Dec 2025) | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes |

**Key Insight**: Cloud platforms excel at real-time collaboration (Google Docs-style). Desktop IDEs rely on async Git workflows. Only Windsurf has dedicated PR review automation.

**Winner (Real-time)**: Replit (multiplayer + Git workflows + RBAC)  
**Winner (Enterprise)**: Windsurf (PR automation + RBAC)

---

### 9. Deployment Automation

| Tool | Built-in Deploy<br><sub>🟢 NICE-TO-HAVE</sub> | Platforms<br><sub>🟢 NICE-TO-HAVE</sub> | CI/CD Integration<br><sub>🟢 NICE-TO-HAVE</sub> | DB Migrations<br><sub>🟢 NICE-TO-HAVE</sub> | Deploy Config<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------------|-----------|-------------------|---------------|----------------|
| **Cursor** | ❌ No | Manual | ✅ Via GitHub Actions | ❌ No | N/A |
| **Windsurf** | ✅ Yes | Netlify | ✅ GitHub Actions | ❌ No | ⚠️ Limited |
| **Bolt.new** | ✅ Yes | Netlify | ✅ GitHub Actions | ⚠️ Supabase only | ⚠️ Limited |
| **Replit** | ✅ Yes | Replit cloud | ✅ Via GitHub Actions | ✅ Yes (automatic) | ⚠️ Limited |
| **Lovable** | ✅ Yes | Lovable hosting | ❌ No | ✅ Supabase | ⚠️ Limited |
| **Base44** | ✅ Yes | Base44 hosting | ❌ No | ✅ Automatic | ⚠️ Limited |

**Key Insight**: Cursor has no deployment features (IDE only). Windsurf & Bolt.new integrate with Netlify (external platform). Replit, Lovable, Base44 deploy to proprietary hosting.

**Winner**: Windsurf, Bolt.new (Netlify flexibility), Replit (one-click + custom domains)

---

### 10. Local Development Support (CRITICAL)

| Tool | Export Runs Standalone<br><sub>🔴 MUST-HAVE</sub> | Offline Work<br><sub>🟡 SHOULD-HAVE</sub> | Local Debugging<br><sub>🟡 SHOULD-HAVE</sub> | Performance<br><sub>🟢 NICE-TO-HAVE</sub> | Use Own Dev Tools<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|---------------------|--------------|-----------------|----------------|-------------------|
| **Cursor** | ✅ Yes | ⚠️ Limited (editing only) | ✅ Yes | Same | ✅ Yes |
| **Windsurf** | ✅ Yes | ⚠️ Limited (editing only) | ✅ Yes | Same | ✅ Yes |
| **Bolt.new** | ✅ npm install only | ❌ No | ⚠️ Limited | Faster local | ✅ Yes (after export) |
| **Replit** | ✅ npm install only | ❌ No | ✅ Yes | Depends on plan | ✅ Yes (after export) |
| **Lovable** | ⚠️ Requires Supabase | ❌ No | ⚠️ Limited | Faster local | ✅ Yes (with Supabase) |
| **Base44** | ❌ Requires platform | ❌ No | ❌ No | N/A | ❌ No |

**Critical Failures**:
- **Base44**: Exported code cannot run standalone; requires Base44 backend infrastructure (**FAILS 10.1**)
- **Lovable**: Requires Supabase infrastructure; not fully standalone (**PARTIAL FAIL 10.1**)

**Winner**: Cursor, Windsurf (desktop IDEs with local flexibility)

---

### 11. AI Model Selection

| Tool | Supported Models<br><sub>🟡 SHOULD-HAVE</sub> | Model Switching<br><sub>🟡 SHOULD-HAVE</sub> | BYOK<br><sub>🟡 SHOULD-HAVE</sub> | Transparency<br><sub>🟢 NICE-TO-HAVE</sub> | Local Models<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------------|-----------------|------|---------------|-------------|
| **Cursor** | 8+ (Claude, GPT-4, etc.) | ✅ Yes | ✅ Yes | ✅ Yes | ❌ No |
| **Windsurf** | Claude, GPT-4, SWE-1 | ✅ Yes | ✅ Yes | ✅ Yes | ❌ No |
| **Bolt.new** | Claude 3.5 Sonnet | ⚠️ Agent versions only | ❌ No | ✅ Yes | ❌ No |
| **Replit** | GPT-5, Claude 3.5, Replit Code | ❌ No (automatic) | ✅ Yes | ✅ Yes | ❌ No |
| **Lovable** | Claude 3.5 Sonnet | ❌ No | ❌ No | ❌ No | ❌ No |
| **Base44** | Not disclosed | ❌ No | ❌ No | ❌ No | ❌ No |

**Key Insight**: Cursor offers most flexibility (8+ models, BYOK). Windsurf provides strong diversity with SWE-1. Cloud platforms lock users to vendor-managed models.

**Winner**: Cursor (most model options + BYOK), Windsurf (BYOK + SWE-1)

---

### 12. IDE Type

| Tool | Primary Interface<br><sub>🟡 SHOULD-HAVE</sub> | VS Code-based<br><sub>🟡 SHOULD-HAVE</sub> | Terminal Access<br><sub>🟢 NICE-TO-HAVE</sub> | Customization<br><sub>🟢 NICE-TO-HAVE</sub> | Keyboard Shortcuts<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|------------------|-------------|---------------|---------------|---------------------|
| **Cursor** | Desktop IDE | ✅ Yes (fork) | ✅ Yes | ✅ Full VS Code | ✅ Yes |
| **Windsurf** | Desktop IDE | ✅ Yes (fork) | ✅ Yes | ✅ Full VS Code | ✅ Yes |
| **Bolt.new** | Web IDE | ❌ No | ✅ Yes | ⚠️ Limited | ✅ Yes |
| **Replit** | Web IDE | ❌ No | ✅ Yes | ⚠️ Limited | ✅ Yes |
| **Lovable** | Web IDE | ❌ No | ✅ Yes | ⚠️ Limited | ✅ Yes |
| **Base44** | Web IDE | ❌ No | ❌ No | ⚠️ Limited | ✅ Yes |

**Key Insight**: Cursor & Windsurf are VS Code forks (full compatibility). Cloud platforms use proprietary web IDEs with varying customization levels.

**Winner**: Cursor, Windsurf (VS Code ecosystem + desktop performance)

---

### 13. Codebase Scale Limits

| Tool | Max File Count<br><sub>🟡 SHOULD-HAVE</sub> | AI Context Window<br><sub>🟡 SHOULD-HAVE</sub> | Proven 100K+ LOC<br><sub>🟡 SHOULD-HAVE</sub> | Monorepo Support<br><sub>🟢 NICE-TO-HAVE</sub> | Performance Thresholds<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------------|-------------------|------------------|------------------|-----------------------|
| **Cursor** | Unlimited (10k+ tested) | 200K tokens | ✅ Yes (evidence) | ✅ Yes | None documented |
| **Windsurf** | Unlimited (10k+ tested) | 200K tokens | ✅ Yes (Fortune 500) | ✅ Yes | None documented |
| **Bolt.new** | Context-limited | 200K-500K tokens | ⚠️ Limited (errors) | ⚠️ Limited | Context window |
| **Replit** | 2 GiB storage | 128K tokens | ✅ Yes (300K LOC) | ⚠️ Limited (config needed) | 2 GiB / 128K tokens |
| **Lovable** | Context-limited | Not documented | ❌ No (prototypes) | ❌ No | Context window |
| **Base44** | Not documented | Not documented | ❌ No (MVPs) | ❌ No | Not documented |

**Key Insight**: Cursor & Windsurf are enterprise-proven on 100K+ LOC codebases with RAG indexing. Bolt.new hits context limits ("Project too large"). Lovable & Base44 optimize for MVPs.

**Winner**: Cursor, Windsurf (proven Fortune 500 adoption + unlimited indexing)

---

### 14. API/Service Integration

| Tool | Supabase Scaffold<br><sub>🟡 SHOULD-HAVE</sub> | Type-safe Clients<br><sub>🟡 SHOULD-HAVE</sub> | Auth Templates<br><sub>🟢 NICE-TO-HAVE</sub> | Payment Integration<br><sub>🟢 NICE-TO-HAVE</sub> | GraphQL Codegen<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|-----------------|-------------------|---------------|---------------------|------------------|
| **Cursor** | ✅ Yes (manual) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Windsurf** | ✅ Yes (manual) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Bolt.new** | ✅ Yes (automatic) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Replit** | ✅ Yes (automatic) | ✅ Yes | ✅ Yes | ✅ Yes (Stripe) | ✅ Yes |
| **Lovable** | ✅ Yes (native) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Base44** | ❌ No | ⚠️ Limited | ✅ Yes | ⚠️ Limited | ❌ No |

**Key Insight**: All qualified tools support Supabase integration. Lovable has native Supabase support (but creates dependency). Desktop IDEs code manually; cloud platforms auto-generate.

**Winner**: Lovable (native Supabase), Bolt.new/Replit (auto-scaffolding)

---

### 15. Code Generation Scope

| Tool | Full Apps<br><sub>🟡 SHOULD-HAVE</sub> | Complete Features<br><sub>🟡 SHOULD-HAVE</sub> | Inline Completion<br><sub>🟡 SHOULD-HAVE</sub> | UI Components<br><sub>🟢 NICE-TO-HAVE</sub> | Test Files<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------|------------------|-------------------|--------------|-----------|
| **Cursor** | ✅ Yes (with guidance) | ✅ Yes | ✅ Yes (Tab) | ✅ Yes | ✅ Yes |
| **Windsurf** | ✅ Yes (Cascade) | ✅ Yes (Cascade) | ✅ Yes (Flow) | ✅ Yes | ✅ Yes |
| **Bolt.new** | ✅ Yes (automatic) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Replit** | ✅ Yes (Agent 2.0) | ✅ Yes | ✅ Yes (Ghostwriter) | ✅ Yes (screenshot-to-code) | ✅ Yes |
| **Lovable** | ✅ Yes (automatic) | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Base44** | ✅ Yes (automatic) | ✅ Yes | ✅ Yes | ✅ Yes | ⚠️ Limited |

**Key Insight**: All tools generate full applications. Windsurf's Cascade mode is most autonomous. Replit's Agent 2.0 has screenshot-to-code (multimodal). Desktop IDEs require more guidance; cloud platforms fully autonomous.

**Winner**: Windsurf (Cascade autonomy), Replit (multimodal generation)

---

### 16. Extension Ecosystem

| Tool | VS Code Extensions<br><sub>🟡 SHOULD-HAVE</sub> | Marketplace Coverage<br><sub>🟢 NICE-TO-HAVE</sub> | Custom Extensions<br><sub>🟢 NICE-TO-HAVE</sub> | Own Plugin System<br><sub>🟢 NICE-TO-HAVE</sub> | Popular Tools Support<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|---------------------|---------------------|-------------------|------------------|----------------------|
| **Cursor** | ✅ Yes | 90%+ marketplace | ✅ Yes | ✅ Yes | ✅ Yes |
| **Windsurf** | ✅ Yes | 50-70% (Open VSX) | ✅ Yes | ✅ Yes | ✅ Yes |
| **Bolt.new** | ❌ No | N/A | ❌ No | ❌ No | ✅ Via config |
| **Replit** | ❌ No | N/A | ✅ Yes (2026) | ✅ Yes | ✅ Via config |
| **Lovable** | ❌ No | N/A | ❌ No | ❌ No | ✅ Via config |
| **Base44** | ❌ No | N/A | ❌ No | ❌ No | ⚠️ Limited |

**Key Insight**: Only Cursor & Windsurf support VS Code extensions. Cursor has full marketplace access; Windsurf limited to Open VSX. Cloud platforms use config files (not extensions).

**Winner**: Cursor (90%+ VS Code marketplace), Windsurf (Open VSX subset)

---

### 17. Pricing Model

| Tool | Free Tier<br><sub>🟡 SHOULD-HAVE</sub> | Monthly Cost<br><sub>🟡 SHOULD-HAVE</sub> | Enterprise<br><sub>🟡 SHOULD-HAVE</sub> | Usage Measurement<br><sub>🟢 NICE-TO-HAVE</sub> | Usage Limits<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|----------|-------------|-----------|------------------|--------------|
| **Cursor** | ✅ 2000 completions | $20 Pro | ✅ Custom | Completions/requests | Premium models limited |
| **Windsurf** | ✅ 25 credits | $15 Pro | ✅ $60/user | Credits | Credit-based |
| **Bolt.new** | ✅ 300K tokens/day | $20-200 | N/A | Tokens | Token-based |
| **Replit** | ✅ Limited | $20 Core / $40 Agent | ✅ Custom | Effort-based (Agent) | 2 GiB storage |
| **Lovable** | ✅ Limited | $30-100 | ✅ Custom | Project-based | Not specified |
| **Base44** | ✅ Limited | $20-200 | ✅ Custom | Not specified | Not specified |

**Key Insight**: Windsurf offers best value ($15 Pro + BYOK). Most expensive: Lovable Pro Max ($100), Base44 Elite ($200). BYOK available only on Cursor & Windsurf.

**Winner (Value)**: Windsurf ($15 Pro + BYOK option)

---

### 18. Mobile Support

| Tool | Native Mobile Apps<br><sub>🟢 NICE-TO-HAVE</sub> | React Native<br><sub>🟢 NICE-TO-HAVE</sub> | Responsive Web<br><sub>🟢 NICE-TO-HAVE</sub> | Flutter<br><sub>🟢 NICE-TO-HAVE</sub> | Mobile Scaffolding<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|-------------------|-------------|--------------|--------|-------------------|
| **Cursor** | ❌ No | ✅ Yes (manual) | ✅ Yes | ✅ Yes (manual) | ✅ Yes |
| **Windsurf** | ❌ No | ✅ Yes (manual) | ✅ Yes | ✅ Yes (manual) | ✅ Yes |
| **Bolt.new** | ❌ No | ✅ Yes (Jan 2026) | ✅ Yes | ❌ No | ✅ Yes |
| **Replit** | ❌ No (preview only) | ✅ Yes (Expo) | ✅ Yes | ✅ Yes | ✅ Yes |
| **Lovable** | ❌ No | ❌ No | ✅ Yes | ❌ No | ✅ Yes (web) |
| **Base44** | ❌ No | ❌ No | ✅ Yes | ❌ No | ✅ Yes (web) |

**Key Insight**: No tool compiles native mobile binaries directly. Cursor, Windsurf, Replit support React Native and Flutter (manual coding). Bolt.new added React Native in Jan 2026. All generate responsive web apps.

**Winner**: Replit (React Native + Flutter templates), Cursor/Windsurf (full manual control)

---

### 19. Performance Optimization

| Tool | Optimization Suggestions<br><sub>🟢 NICE-TO-HAVE</sub> | Bundle Analysis<br><sub>🟢 NICE-TO-HAVE</sub> | Auto Lazy Loading<br><sub>🟢 NICE-TO-HAVE</sub> | Code Splitting<br><sub>🟢 NICE-TO-HAVE</sub> | Performance Metrics<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|------------------------|---------------|------------------|--------------|---------------------|
| **Cursor** | ✅ Yes (AI-suggested) | ⚠️ Via extensions | ❌ No | ✅ Framework-native | ⚠️ Via extensions |
| **Windsurf** | ✅ Yes (AI-suggested) | ⚠️ Via extensions | ❌ No | ✅ Framework-native | ⚠️ Via extensions |
| **Bolt.new** | ✅ Yes (AI-suggested) | ❌ No | ❌ No | ✅ Framework-native | ❌ No |
| **Replit** | ✅ Yes (on prompt) | ❌ No | ❌ No | ✅ Framework-native | ⚠️ Via generated code |
| **Lovable** | ✅ Yes (AI-suggested) | ❌ No | ❌ No | ✅ Framework-native | ❌ No |
| **Base44** | ⚠️ Limited | ❌ No | ❌ No | ✅ Framework-native | ❌ No |

**Key Insight**: All tools rely on AI suggestions for optimization (not automatic). Desktop IDEs leverage extensions for bundle analysis. Framework-native code splitting (Next.js, Vite) available in all modern stacks.

**Winner**: Cursor, Windsurf (extension ecosystem for profiling)

---

### 20. Security & Compliance

| Tool | Vulnerability Scanning<br><sub>🟡 SHOULD-HAVE</sub> | Auth Scaffolding<br><sub>🟡 SHOULD-HAVE</sub> | GDPR Features<br><sub>🟢 NICE-TO-HAVE</sub> | SOC2/ISO Certification<br><sub>🟢 NICE-TO-HAVE</sub> |
|------|---------------------|------------------|-------------|----------------------|
| **Cursor** | ⚠️ Via extensions | ✅ Yes | ⚠️ User responsibility | ⚠️ Infrastructure only |
| **Windsurf** | ⚠️ Via extensions | ✅ Yes | ⚠️ User responsibility | ⚠️ Infrastructure only |
| **Bolt.new** | ❌ No | ✅ Yes (Supabase) | ⚠️ User responsibility | ⚠️ Via hosting |
| **Replit** | ✅ Yes (Enterprise) | ✅ Yes | ✅ Yes (Enterprise) | ✅ Yes (Enterprise) |
| **Lovable** | ❌ No | ✅ Yes (Supabase) | ⚠️ Via Supabase | ⚠️ Via Supabase |
| **Base44** | ✅ Yes (Security scan) | ✅ Yes | ⚠️ Limited | ⚠️ Via platform |

**Key Insight**: Replit Enterprise offers comprehensive compliance (SOC2, SBOM, vulnerability scanning). Base44 has security scan feature. Desktop IDEs rely on extensions. Auth scaffolding available in all tools.

**Winner**: Replit (Enterprise compliance suite), Base44 (built-in security scan)

---

### 21. Team & Adoption

| Tool | Team Sizes<br><sub>🟡 SHOULD-HAVE</sub> | Learning Curve<br><sub>🟢 NICE-TO-HAVE</sub> | Vendor Stability<br><sub>🟡 SHOULD-HAVE</sub> |
|------|------------|---------------|-----------------|
| **Cursor** | Solo / Small / Medium / Enterprise | Minimal (VS Code users) | Series B+ (well-funded) |
| **Windsurf** | Solo / Small / Medium / Enterprise | Minimal (VS Code users) | Series B+ (Codeium) |
| **Bolt.new** | Solo / Small / Medium | Easy (1 day) | Series A (StackBlitz) |
| **Replit** | Solo / Small / Medium / Enterprise | Moderate (1-3 days) | Series B+ (established) |
| **Lovable** | Solo / Small | Easy (1 day) | Early-stage (funded) |
| **Base44** | Solo / Small | Easy (1 day) | Acquired by Wix ($80M) |

**Key Insight**: Desktop IDEs (Cursor, Windsurf) have minimal learning curve for VS Code users. Cloud platforms optimize for beginners. All vendors are funded/stable except Lovable (early-stage).

**Winner**: Cursor, Windsurf (enterprise-ready + stable), Replit (education market leader)

---

## Use Case Recommendations

### For Enterprise Teams (10K+ files, 100K+ LOC)

**🏆 Top Choice: Cursor or Windsurf**

**Why**:
- ✅ Proven on Fortune 500 codebases (Windsurf: 59% adoption)
- ✅ Unlimited file indexing with RAG-based context
- ✅ Full polyglot support (TypeScript, Rust, Python, Go)
- ✅ Zero vendor lock-in (standard npm/cargo projects)
- ✅ VS Code-based familiarity (minimal learning curve)

**Choose Cursor if**: Team prioritizes model flexibility (8+ models, BYOK)  
**Choose Windsurf if**: Team needs PR automation and agentic coding (Cascade)

---

### For Full-Stack TypeScript/React Teams

**🏆 Top Choice: Bolt.new or Replit**

**Why**:
- ✅ Zero setup (browser-based, instant onboarding)
- ✅ Full-stack generation (React + Node.js + database)
- ✅ Real-time collaboration
- ✅ One-click deployment (Netlify/Replit)
- ✅ Zero vendor lock-in (standard exports)

**Choose Bolt.new if**: Team needs Netlify deployment and Supabase integration  
**Choose Replit if**: Team needs 50+ language support and platform hosting

---

### For Rapid Prototyping / MVPs (Non-Technical Founders)

**🏆 Top Choice: Lovable or Replit**

**Why**:
- ✅ Natural language prompts (no coding required)
- ✅ Full-stack generation in minutes
- ✅ Built-in hosting and database
- ✅ Real-time collaboration
- ✅ Visual editor for tweaks

**Choose Lovable if**: Supabase backend acceptable, focus on speed  
**Choose Replit if**: Need broader language support and educational resources

**⚠️ Avoid Base44**: Severe vendor lock-in (apps cannot run outside platform)

---

### For Polyglot Teams (Rust + Python + Go + TypeScript)

**🏆 Top Choice: Cursor or Windsurf**

**Why**:
- ✅ First-class Rust LSP (rust-analyzer)
- ✅ Full Python, Go, TypeScript support
- ✅ Multi-file refactoring across languages
- ✅ Local debugging for all languages

**Not Recommended**: Bolt.new, Lovable, Base44 (JavaScript-only)

---

### For Teams Requiring Code Portability (CRITICAL)

**🏆 Top Choice: Cursor, Windsurf, Bolt.new, or Replit**

**Why**:
- ✅ Pass all 4 MUST-HAVE requirements
- ✅ Zero proprietary runtime dependencies
- ✅ Standard npm/cargo/pip projects
- ✅ Deploy anywhere (AWS, Vercel, self-hosted)

**❌ DISQUALIFIED**:
- **Base44**: Requires @base44/sdk + platform backend (severe lock-in)
- **Lovable**: Requires Supabase (moderate lock-in)

---

## Critical Decision Framework

### Step 1: Check MUST-HAVE Requirements

Does your project require:
1. ✅ Deploy to infrastructure outside platform?
2. ✅ Export 100% of code?
3. ✅ No proprietary runtime dependencies?
4. ✅ Run with standard dev commands (npm start)?

**If YES to all** → Cursor, Windsurf, Bolt.new, Replit  
**If YES to 3/4** → Lovable (Supabase acceptable?)  
**If NO** → Base44 (accept platform lock-in)

### Step 2: Choose by Primary Need

**Need: Enterprise-scale codebase support (100K+ LOC)**
→ **Cursor** or **Windsurf**

**Need: Fastest time-to-prototype (non-technical founders)**
→ **Lovable** or **Replit** (avoid Base44)

**Need: Full-stack TypeScript + zero setup**
→ **Bolt.new** or **Replit**

**Need: Polyglot support (Rust + Python + Go)**
→ **Cursor** or **Windsurf**

**Need: Real-time collaboration + multiplayer**
→ **Replit** or **Bolt.new**

**Need: AI model flexibility + BYOK**
→ **Cursor** (8+ models) or **Windsurf** (BYOK)

### Step 3: Evaluate Budget

**Free tier sufficient?**
- Windsurf: 25 credits/month
- Cursor: 2000 completions
- Bolt.new: 300K tokens/day
- Replit: Limited Agent access

**Budget <$20/month/user?**
→ Windsurf ($15 Pro) or Cursor ($20 Pro)

**Budget $30-40/month/user?**
→ Replit Agent ($40) or Cursor Team ($40)

**Budget >$50/month/user?**
→ Consider BYOK (Cursor/Windsurf) to reduce costs

---

## Strengths & Weaknesses Summary

### Cursor
**Strengths**:
- ✅ 8+ AI models with full BYOK support
- ✅ VS Code-native (zero learning curve)
- ✅ Enterprise-proven (100K+ LOC codebases)
- ✅ Full polyglot support (Rust LSP, Python, Go)
- ✅ Zero vendor lock-in

**Weaknesses**:
- ❌ No deployment automation
- ❌ No real-time collaboration
- ❌ Self-hosted deprecated (cloud-only AI)
- ⚠️ Premium models expensive without BYOK

**Best for**: Enterprise teams, polyglot developers, model flexibility seekers

---

### Windsurf
**Strengths**:
- ✅ Agentic Cascade mode (autonomous multi-file edits)
- ✅ Fortune 500 proven (59% adoption claim)
- ✅ Netlify one-click deployment
- ✅ PR automation with AI reviews
- ✅ Affordable ($15 Pro + BYOK)

**Weaknesses**:
- ❌ No real-time collaboration
- ❌ Self-hosted deprecated (cloud-only AI)
- ⚠️ Extension ecosystem limited (Open VSX ~50-70%)
- ❌ No mobile app generation

**Best for**: Enterprise teams, agentic coding workflows, budget-conscious teams

---

### Bolt.new
**Strengths**:
- ✅ Zero setup (browser-based)
- ✅ Full-stack React + Node.js generation
- ✅ Netlify deployment integration
- ✅ Real-time Teams collaboration
- ✅ Zero vendor lock-in (standard exports)

**Weaknesses**:
- ❌ JavaScript-only (no Rust, Python, Go backends)
- ⚠️ Context window limits ("Project too large" errors)
- ❌ No BYOK (locked to Claude)
- ❌ No mobile app generation (React Native added, but limited)

**Best for**: TypeScript/React teams, rapid web app prototyping, zero-setup onboarding

---

### Replit
**Strengths**:
- ✅ 50+ languages supported
- ✅ Real-time multiplayer collaboration
- ✅ Built-in hosting + deployments
- ✅ Educational resources (great for learning)
- ✅ Zero vendor lock-in

**Weaknesses**:
- ⚠️ Context window (128K tokens) smaller than competitors
- ⚠️ AI model selection automatic (no manual switching)
- ❌ Deployment locked to Replit platform (less flexibility)
- ⚠️ 2 GiB storage limit per app

**Best for**: Educators, polyglot teams, learners, teams needing multiplayer

---

### Lovable
**Strengths**:
- ✅ Extremely fast prototyping
- ✅ Real-time collaboration
- ✅ Supabase integration (type-safe)
- ✅ Natural language-first development
- ✅ Visual editor for non-developers

**Weaknesses**:
- ⚠️ **Fails 1 MUST-HAVE**: Requires Supabase (moderate vendor lock-in)
- ❌ JavaScript-only (no Rust, Python, Go)
- ❌ No BYOK or model selection
- ⚠️ Optimized for MVPs, not enterprise scale
- ⚠️ Expensive ($30-100/month)

**Best for**: Non-technical founders, rapid MVPs, Supabase-first projects

---

### Base44
**Strengths**:
- ✅ Extremely fast prototyping for non-developers
- ✅ All-in-one platform (database, auth, hosting)
- ✅ Real-time collaboration
- ✅ Wix acquisition (financial stability)
- ✅ Security scan feature

**Weaknesses**:
- ❌ **Fails 3 MUST-HAVE**: Severe vendor lock-in (requires @base44/sdk + backend)
- ❌ Apps cannot run independently outside platform
- ❌ JavaScript-only (no Rust, Python, Go)
- ❌ npm package restrictions (CDN workarounds needed)
- ❌ No model selection or BYOK
- ❌ Optimized for MVPs only, not enterprise scale

**Best for**: Non-technical users accepting platform lock-in for convenience  
**Avoid if**: Code portability or vendor independence required

---

## Final Recommendation by Scenario

### Scenario 1: Enterprise Development (Large Teams, 100K+ LOC)
**Winner**: **Cursor** or **Windsurf**
- Both pass all MUST-HAVE requirements
- Proven on Fortune 500 codebases
- Full polyglot support
- Choose Cursor for model flexibility, Windsurf for agentic coding

### Scenario 2: Startup MVP (Fast Prototyping, Small Team)
**Winner**: **Bolt.new** or **Replit**
- Zero setup, instant collaboration
- Full-stack generation
- Zero vendor lock-in (unlike Lovable/Base44)
- Choose Bolt.new for React focus, Replit for language diversity

### Scenario 3: Non-Technical Founder (No Coding Knowledge)
**Winner**: **Lovable** (acceptable Supabase lock-in) or **Replit**
- Natural language development
- Visual editing
- **Avoid Base44** (severe lock-in)

### Scenario 4: Polyglot Team (Rust + Python + TypeScript)
**Winner**: **Cursor** or **Windsurf**
- Only tools with full Rust LSP + Python + Go + TypeScript
- Bolt.new, Lovable, Base44 are JavaScript-only

### Scenario 5: Budget-Conscious Team
**Winner**: **Windsurf** ($15 Pro + BYOK)
- Lowest monthly cost with full enterprise features
- BYOK saves on AI costs

---

## Disqualified Tools

### ❌ Base44 (CRITICAL FAILURES)
**Reason**: Fails 3 of 4 MUST-HAVE requirements
- Cannot deploy outside platform
- Requires proprietary @base44/sdk runtime
- Cannot run with standard dev commands

**Impact**: Severe vendor lock-in eliminates from consideration for any team requiring code portability.

### ⚠️ Lovable (PARTIAL FAILURE)
**Reason**: Fails 1 of 4 MUST-HAVE requirements
- Requires Supabase for backend

**Impact**: Acceptable for teams already using Supabase, but creates moderate vendor dependency.

---

## Evaluation Methodology Notes

### Scoring System
- **MUST-HAVE (40 points)**: Deal-breaker requirements (10 points each, 4 questions)
- **SHOULD-HAVE (45 points)**: High-priority features (1 point each, 45 questions)
- **NICE-TO-HAVE (15 points)**: Bonus features (0.28 points each, 54 questions)

### Evidence Levels
- **P1 (Primary)**: Official documentation, vendor statements, published roadmaps
- **P2 (Secondary)**: Verified user reports (within 6 months), technical reviews
- **P3 (Tertiary)**: Reasonable inferences (clearly marked)

### Evaluation Date
All evaluations completed: 2026-02-04

### Version References
- **Metrics**: evaluation-metrics.md v2.0
- **Template**: evaluation-template.md v2.0
- **Criteria**: decision-criteria.md v2.0

---


