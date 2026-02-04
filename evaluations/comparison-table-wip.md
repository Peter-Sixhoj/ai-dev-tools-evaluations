# AI Development Tools Comparison Table (Work in Progress)

**Status**: Phase 1 - Data extraction from existing evaluations  
**Date Started**: 2026-02-04  
**Tools Being Compared**: Cursor, Windsurf, Bolt.new, Lovable, Replit, Base44

---

## Progress Tracker

- [x] Cursor - Data extracted
- [ ] Windsurf - Pending
- [ ] Bolt.new - Pending
- [ ] Lovable - Pending
- [ ] Replit - Pending
- [ ] Base44 - Pending

---

## CRITICAL QUESTIONS (Must Pass All 8)

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **1.1: Self-hosted?** | No | | | | | |
| **1.2: Air-gapped?** | No | | | | | |
| **3.1: Export 100%?** | Yes | | | | | |
| **3.2: Platform-independent?** | Yes | | | | | |
| **4.1: TypeScript?** | Yes | | | | | |
| **4.2: Rust LSP?** | No (syntax only) | | | | | |
| **10.1: Run without tool?** | Yes | | | | | |
| **20.1: Air-gapped operation?** | No | | | | | |

**Critical Analysis - Cursor**:  
❌ **FAILS** critical questions 1.1, 1.2, 4.2, 20.1  
✅ **PASSES** critical questions 3.1, 3.2, 4.1, 10.1

**Result**: Cursor would be **ELIMINATED** in strict evaluation (4 critical failures)

---

## HIGH PRIORITY QUESTIONS (43 total)

### Deployment Model

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **1.3: Local desktop?** | Yes (Win/Mac/Linux) | | | | | |
| **1.4: Processing location?** | Hybrid (local IDE, cloud AI) | | | | | |

### Package Management

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **2.1: npm?** | Yes | | | | | |
| **2.2: cargo?** | Yes | | | | | |
| **2.3: Monorepo?** | Yes (with workarounds) | | | | | |

### Code Ownership

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **3.3: Standard format?** | Yes | | | | | |
| **3.4: Runs locally?** | Yes (immediately) | | | | | |

### Framework Support

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **4.3: React/Next.js?** | Yes | | | | | |
| **4.4: Python?** | Yes (FastAPI, Django) | | | | | |
| **4.5: Go?** | Limited | | | | | |

### Git Integration

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **5.1: Native Git?** | Yes | | | | | |
| **5.2: GitHub/GitLab?** | GitHub only | | | | | |
| **5.3: PR workflows?** | Yes | | | | | |

### Multi-file Context

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **6.1: File relationships?** | Yes (semantic search) | | | | | |
| **6.2: Multi-file refactor?** | Yes | | | | | |
| **6.3: Max context?** | 8,000 lines | | | | | |

### Backend Capabilities

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **7.1: Backend languages?** | Node.js, Python, Go (limited) | | | | | |
| **7.2: DB schemas?** | Yes | | | | | |
| **7.3: API generation?** | REST & GraphQL | | | | | |

### Collaboration

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **8.1: Team support?** | Git-based (no real-time) | | | | | |

### Local Development

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **10.2: Offline?** | Limited (AI requires cloud) | | | | | |
| **10.3: Debugging?** | Yes | | | | | |

### AI Models

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **11.1: Supported models?** | Claude 3.5, GPT-4/4o/5, Gemini, xAI, Composer | | | | | |
| **11.2: Switch models?** | Yes | | | | | |
| **11.3: Own API keys?** | Yes (Pro+/Ultra) | | | | | |

### IDE Type

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **12.1: Interface?** | Desktop (VS Code fork) + Web PWA | | | | | |
| **12.2: VS Code based?** | Yes | | | | | |

### Codebase Scale

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **13.1: Max files?** | 100,000 (with workarounds) | | | | | |
| **13.2: Context window?** | 8,000 lines | | | | | |
| **13.3: Enterprise scale?** | Limited (100k+ requires workarounds) | | | | | |

### API Integration

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **14.1: Supabase?** | Yes | | | | | |
| **14.2: Type-safe clients?** | Yes (inferred) | | | | | |

### Code Generation

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **15.1: Full apps?** | Yes (Composer) | | | | | |
| **15.2: Features?** | Yes | | | | | |
| **15.3: Inline completion?** | Yes (Tab - Supermaven) | | | | | |

### Extensions

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **16.1: VS Code extensions?** | Yes (~90%) | | | | | |

### Pricing

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **17.1: Free tier?** | Yes (Hobby - permanent) | | | | | |
| **17.2: Cost/dev/month?** | $20 (Pro), $40 (Teams) | | | | | |
| **17.3: Enterprise?** | Yes (custom pricing) | | | | | |

### Security

| Question | Cursor | Windsurf | Bolt.new | Lovable | Replit | Base44 |
|----------|--------|----------|----------|---------|--------|--------|
| **20.2: Vuln scanning?** | Not mentioned | | | | | |
| **20.3: Auth scaffolding?** | Yes (Auth0, Supabase, Clerk, Firebase) | | | | | |

---

## CURSOR SCORING SUMMARY

### Critical Questions: 4/8 PASS ❌
- ✅ Export 100% (3.1)
- ✅ Platform-independent (3.2)
- ✅ TypeScript support (4.1)
- ✅ Run without tool (10.1)
- ❌ Self-hosted (1.1)
- ❌ Air-gapped (1.2)
- ❌ Rust LSP (4.2)
- ❌ Air-gapped operation (20.1)

**Result**: **ELIMINATED** (fails 4 critical questions)

### High Priority Questions: 36/43 estimated

**Strong Areas**:
- Package management (npm, cargo, monorepo)
- Code ownership (standard format, runs locally)
- Framework support (React/Next.js, Python)
- Git integration (native, PR workflows)
- Multi-file context (semantic search, refactoring)
- Backend capabilities (Node.js, Python, DB schemas, APIs)
- AI models (multiple models, switching, BYOK)
- IDE type (VS Code fork, familiar interface)
- Code generation (full apps, features, inline)
- Pricing (free tier, reasonable cost)

**Weak Areas**:
- Deployment model (not self-hosted, not air-gapped)
- Framework support (Rust syntax only, Go limited)
- Collaboration (Git-based only, no real-time)
- Offline (AI requires cloud)
- Codebase scale (100k limit, 8k context)
- Security (no explicit vuln scanning, GDPR gaps)

### If Critical Questions Were Relaxed

**Estimated Score**: ~142/167 (85%)
- Critical: 32 points (if passed)
- High: ~72/86 points (84%)
- Medium: ~38/49 points (estimated 78%)

---

## NOTES FOR NEXT TOOLS

### Data Extraction Checklist
For each remaining tool, extract:
1. ✅ 8 Critical questions first (determines elimination)
2. ✅ 43 High Priority questions
3. ⏭️ 49 Medium Priority questions (if not eliminated)

### Key Questions to Watch
- **Self-hosting capability**: Most cloud tools will fail this
- **Air-gapped operation**: Most tools require internet for AI
- **Rust LSP**: Specialty support, many tools lack this
- **Code ownership**: Critical differentiator
- **Codebase scale**: Enterprise scalability
- **Context window size**: Major capability differentiator

---

## Next Steps

1. Extract Windsurf data
2. Extract Bolt.new data
3. Extract Lovable data
4. Extract Replit data
5. Extract Base44 data
6. Calculate scores for all non-eliminated tools
7. Identify top 2-3 finalists
8. Deep dive research on finalists with updated 2026 data
