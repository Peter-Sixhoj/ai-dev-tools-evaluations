# Framework Refinement Worksheet v1.0

**Date**: 2026-02-04  
**Purpose**: Identify ambiguous questions and propose clarifications before re-evaluating tools  
**Status**: Draft for Review  

---

## Introduction

This worksheet identifies questions in `decision-criteria.md` that may be ambiguous, overlapping, or unclear. For each issue, we propose a refinement.

**How to use this**:
1. Review each ambiguity
2. Decide: Accept proposed fix / Modify / Remove question
3. Mark your decision in the "Your Decision" column
4. We'll create Decision Framework v2.0 based on your feedback

---

## Critical Ambiguities (Must Fix - These are 🔴 CRITICAL questions)

### 🔴 AMBIGUITY #1: Question 1.1 - Self-Hosted Interpretation

**Current Question**: "Can the tool be fully self-hosted on-premises?"

**Ambiguity**: Which "tool" are we asking about?
- **Interpretation A**: Can the **development environment** (IDE + AI) run on your servers?
- **Interpretation B**: Can the **application you build** be deployed on-premises?

**Why This Matters**: 
- If Interpretation A: Windsurf YES, others NO (only Windsurf offers self-hosted IDE)
- If Interpretation B: All tools YES (all export standard code deployable anywhere)

**Current Rationale Says**: 
> "Self-hosting provides complete data control... Cloud-only tools send your code to external servers"

This clearly indicates **Interpretation A** (about the development tool).

**Proposed Fix**: Split into two questions:

| New ID | Question | Priority | Answer Format |
|--------|----------|----------|---------------|
| 1.1a | Can the **development environment** (IDE + AI) be fully self-hosted on your infrastructure? | 🔴 CRITICAL | Yes / Partial / No |
| 1.1b | Can **applications you build** be deployed to any on-premises infrastructure? | 🟡 HIGH | Yes / Requires platform / No |

**Your Decision**: [ ] Accept / [ ] Modify / [ ] Other: ________________

---

### 🔴 AMBIGUITY #2: Questions 1.2 & 20.1 - Duplicate Air-Gapped

**Current Questions**:
- **1.2**: "Does it work in air-gapped environments without internet?"
- **20.1**: "Can it work in air-gapped/isolated environments?"

**Ambiguity**: These appear to be asking the exact same thing.

**Why This Matters**: 
- Having two identical critical questions artificially inflates their importance
- Scoring becomes confusing (fail once or twice?)

**Proposed Fix**: Combine into single question with clearer sub-aspects:

| New ID | Question | Priority | Answer Format |
|--------|----------|----------|---------------|
| 1.2 | Can the tool operate in **completely air-gapped environments** (no internet access for development or AI features)? | 🔴 CRITICAL | Yes / Partial (internet for AI only) / No |

**Remove**: Question 20.1 (duplicate)

**Your Decision**: [ ] Accept / [ ] Modify / [ ] Keep both: ________________

---

### 🔴 AMBIGUITY #3: Question 4.2 - Rust LSP as CRITICAL?

**Current Question**: "Does it support Rust with LSP integration?" (🔴 CRITICAL)

**Ambiguity**: Is Rust LSP truly a **must-have deal-breaker** for your use case?

**Why This Matters**:
- **ALL 6 tools fail this question** (or have very limited support)
- If truly critical, all tools should be eliminated
- Current scoring: This question eliminates all viable options

**Evidence**:
- Windsurf: Limited (syntax only)
- Cursor: No (syntax only)
- Replit: No (50+ languages but limited Rust)
- Bolt.new: No (JavaScript only)
- Lovable: No (JavaScript only)
- Base44: N/A (React only)

**Proposed Fix**: Downgrade from CRITICAL to HIGH priority

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 4.2 | Does it support Rust with LSP integration (rust-analyzer)? | 🟡 HIGH | Yes / Syntax only / No |

**Alternative**: Remove question entirely if Rust is not actively used today

**Your Decision**: [ ] Downgrade to HIGH / [ ] Remove / [ ] Keep CRITICAL: ________________

---

### 🔴 AMBIGUITY #4: Question 3.2 - Platform Dependencies

**Current Question**: "Is exported code dependency-free from the platform?"

**Ambiguity**: What counts as a "platform dependency"?
- **Interpretation A**: Code requires proprietary runtime/SDK (like AWS Amplify SDK)
- **Interpretation B**: Code uses standard third-party services (like Supabase client)

**Why This Matters**:
- Lovable uses Supabase heavily - is this a "platform dependency"?
- Bolt.new uses standard npm packages - are these "dependencies"?

**Proposed Fix**: Clarify what we're looking for:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 3.2 | Does exported code avoid **proprietary runtime dependencies** (code runs with standard npm/cargo/pip, no vendor-specific SDK required)? | 🔴 CRITICAL | Yes / Requires vendor SDK / No |

**Examples**:
- ✅ YES: Uses Supabase client (standard npm package, can swap for other backend)
- ✅ YES: Uses React, Express, PostgreSQL (all standard open-source)
- ❌ NO: Requires proprietary Base44 runtime to function
- ⚠️ PARTIAL: Requires specific cloud provider SDK (AWS Amplify, Firebase)

**Your Decision**: [ ] Accept clarification / [ ] Modify: ________________

---

## High Priority Ambiguities (Should Fix)

### 🟡 AMBIGUITY #5: Questions 13.1, 13.2, 13.3 - Scale Measurement Overlap

**Current Questions**:
- **13.1**: "What is the maximum file count supported?"
- **13.2**: "What is the context window size?"
- **13.3**: "Can it handle enterprise-scale codebases (100k+ LOC)?"

**Ambiguity**: These three questions measure overlapping concepts:
- File count = storage/indexing capacity
- Context window = how much code AI can see at once
- Enterprise scale = combination of both + performance

**Why This Matters**: 
- Answering 13.3 requires data from 13.1 and 13.2
- Scoring gives 3x weight to essentially one capability

**Proposed Fix**: Keep all three but clarify what each measures:

| ID | Question | What It Measures | Answer Format |
|----|----------|------------------|---------------|
| 13.1 | What is the maximum **total file count** the tool can index/navigate? | Storage & indexing capacity | Number (e.g., "100,000 files") or "Unlimited" |
| 13.2 | What is the **AI context window** (how much code can AI consider at once)? | AI comprehension scope | Tokens (e.g., "200K tokens") or files (e.g., "50 files") |
| 13.3 | Has the tool been **proven on enterprise-scale codebases** (100K+ LOC)? | Real-world validation | Yes (with evidence) / Likely / No |

**Your Decision**: [ ] Accept clarification / [ ] Merge questions / [ ] Modify: ________________

---

### 🟡 AMBIGUITY #6: Question 8.1 - Collaboration Types

**Current Question**: "Does it support team collaboration?"
**Answer Format**: Real-time / Git-based / No

**Ambiguity**: The answer format implies Real-time is "better" than Git-based, but they serve different workflows:
- **Real-time**: Google Docs style (Replit, Lovable, Bolt.new)
- **Git-based**: Professional PR workflow (Cursor, Windsurf)

**Why This Matters**: 
- These are different collaboration philosophies, not quality rankings
- Your team may prefer one or the other

**Proposed Fix**: Split into two questions:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 8.1a | Does it support **real-time multiplayer** collaboration (simultaneous editing)? | 🟢 MEDIUM | Yes / No |
| 8.1b | Does it support **Git-based** collaboration workflows (branches, PRs, code review)? | 🟡 HIGH | Yes / Limited / No |

**Rationale**: Git workflows are higher priority for professional teams; real-time is nice-to-have.

**Your Decision**: [ ] Accept split / [ ] Keep as-is / [ ] Modify: ________________

---

### 🟡 AMBIGUITY #7: Question 10.1 - Running Projects

**Current Question**: "Can you run projects locally without the tool?"

**Ambiguity**: What does "without the tool" mean?
- **Interpretation A**: Can exported projects run using standard commands (npm start) outside the tool's IDE?
- **Interpretation B**: Can projects run without any vendor infrastructure/backend?

**Why This Matters**:
- Interpretation A: All tools except Base44 score YES
- Interpretation B: Only tools with no proprietary backend score YES

**Current Rationale Says**:
> "Running projects without the tool means you're not locked in. If you can only run projects inside the tool, you lose access if vendor shuts down."

This indicates **Interpretation A** (about IDE lock-in, not backend lock-in).

**Proposed Fix**: Clarify the question:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 10.1 | Can exported projects **run using standard dev commands** (npm start, cargo run) in any IDE/terminal, without requiring the tool's IDE? | 🔴 CRITICAL | Yes / Requires tool IDE / No |

**Your Decision**: [ ] Accept clarification / [ ] Modify: ________________

---

### 🟡 AMBIGUITY #8: Question 1.4 - Code Processing Location

**Current Question**: "Where is code processed? (local vs cloud)"
**Answer Format**: Local / Cloud / Hybrid

**Ambiguity**: What does "code processing" mean?
- **Interpretation A**: Where does the IDE run? (local vs browser)
- **Interpretation B**: Where do AI features process code? (local AI vs cloud API)
- **Interpretation C**: Both?

**Why This Matters**:
- Cursor: IDE local + AI cloud = "Hybrid"
- Windsurf: IDE local + AI cloud (but can be self-hosted) = "Hybrid" or "Local"?
- Replit: IDE cloud + AI cloud = "Cloud"

**Proposed Fix**: Split into two questions:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 1.4a | Where does the **IDE/editor** run? | 🟡 HIGH | Local (desktop) / Cloud (browser) / Both |
| 1.4b | Where are **AI features processed**? | 🟡 HIGH | Local / Cloud API / Self-hosted option / Hybrid |

**Your Decision**: [ ] Accept split / [ ] Keep as-is / [ ] Modify: ________________

---

## Medium Priority Ambiguities (Nice to Fix)

### 🟢 AMBIGUITY #9: Question 7.1 - Backend Languages

**Current Question**: "Can it generate backend code (Node.js/Python/Go/Rust)?"
**Answer Format**: All / Some / None

**Ambiguity**: "All" means all 4 languages? Or just "multiple languages"?

**Proposed Fix**: More granular answer:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 7.1 | Which backend languages can it generate? | 🟡 HIGH | List: Node.js, Python, Go, Rust, Other |

**Your Decision**: [ ] Accept / [ ] Keep as-is

---

### 🟢 AMBIGUITY #10: Question 11.3 - Own API Keys

**Current Question**: "Can you use your own API keys?"

**Ambiguity**: What does this enable?
- **Interpretation A**: Cost control (pay OpenAI/Anthropic directly)
- **Interpretation B**: Data residency (API calls go to your account)
- **Interpretation C**: Unlimited usage (bypass vendor limits)

**Proposed Fix**: Clarify the benefit:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 11.3 | Can you **bring your own API keys (BYOK)** for AI providers (OpenAI, Anthropic, etc.)? | 🟡 HIGH | Yes / Enterprise only / No |

**Your Decision**: [ ] Accept / [ ] Keep as-is

---

### 🟢 AMBIGUITY #11: Questions 6.3 - Context Size Units

**Current Question**: "What is the maximum file context size?"
**Answer Format**: Number of files

**Ambiguity**: Should this be measured in:
- Files (e.g., "50 files")
- Tokens (e.g., "200K tokens")
- Lines of code (e.g., "8,000 lines")
- All three?

**Proposed Fix**: Accept any measurement unit, document which:

| ID | Question | Priority | Answer Format |
|----|----------|----------|---------------|
| 6.3 | What is the maximum **AI context size**? | 🟡 HIGH | Specify unit: tokens / files / LOC / characters (e.g., "200K tokens" or "50 files") |

**Your Decision**: [ ] Accept / [ ] Standardize to one unit: ________________

---

## Redundancy Issues

### REDUNDANCY #1: Questions 1.2 and 20.1
**Status**: Already covered in AMBIGUITY #2
**Recommendation**: Merge into single question

---

### REDUNDANCY #2: Questions 3.3 and 3.4 Overlap?

**Current Questions**:
- **3.3**: "Is code export in standard project format?"
- **3.4**: "Can exported code run immediately in local environment?"

**Are these asking the same thing?**
- Standard format → runs immediately?
- Or can format be standard but require setup?

**Proposed Fix**: Keep both, but clarify:

| ID | Question | What It Checks |
|----|----------|----------------|
| 3.3 | Is exported code in **standard project format** (package.json, Cargo.toml, standard directories)? | Format/structure |
| 3.4 | Can exported code **run with zero modifications** (npm start works immediately)? | Immediate usability |

**Example Difference**:
- Tool exports standard package.json (3.3 = YES)
- But you need to run `npm install` first (3.4 = "Requires setup")

**Your Decision**: [ ] Keep both with clarification / [ ] Merge / [ ] Other: ________________

---

## Priority Classification Questions

These questions help determine if current priority levels match YOUR needs:

### PRIORITY QUESTION #1: Air-Gapped Requirements

**Current Status**: 🔴 CRITICAL (questions 1.2 and 20.1)

**Ask Yourself**: 
- Do you work with classified/highly sensitive data?
- Do you have regulatory requirements for air-gapped development?
- Is this a hard requirement or future-proofing?

**Options**:
- [ ] Keep as 🔴 CRITICAL (deal-breaker)
- [ ] Downgrade to 🟡 HIGH (strongly prefer but not required)
- [ ] Downgrade to 🟢 MEDIUM (nice-to-have for flexibility)

**Your Decision**: ________________

---

### PRIORITY QUESTION #2: Self-Hosted Development Environment

**Current Status**: 🔴 CRITICAL (question 1.1)

**Ask Yourself**:
- Do you have data sovereignty requirements?
- Do you need to control where code is processed during development?
- Is this regulatory or preference?

**Options**:
- [ ] Keep as 🔴 CRITICAL (must be self-hostable)
- [ ] Downgrade to 🟡 HIGH (prefer but can accept cloud IDE)
- [ ] Split: Self-hosted AI is critical, IDE location flexible

**Your Decision**: ________________

---

### PRIORITY QUESTION #3: Rust LSP Support

**Current Status**: 🔴 CRITICAL (question 4.2)

**Ask Yourself**:
- Are you actively developing Rust applications today?
- How much Rust code do you write (% of total development)?
- Would "syntax highlighting only" be acceptable?

**Options**:
- [ ] Keep as 🔴 CRITICAL (must have full LSP)
- [ ] Downgrade to 🟡 HIGH (want good Rust support)
- [ ] Downgrade to 🟢 MEDIUM (nice-to-have for future)
- [ ] Remove (not using Rust)

**Your Decision**: ________________

---

### PRIORITY QUESTION #4: TypeScript Support

**Current Status**: 🔴 CRITICAL (question 4.1)

**Ask Yourself**:
- Is TypeScript your team's primary language?
- Would JavaScript-only be acceptable?
- How important is full type inference?

**Options**:
- [ ] Keep as 🔴 CRITICAL (TypeScript is primary language)
- [ ] Downgrade to 🟡 HIGH (prefer TS but JS acceptable)

**Your Decision**: ________________

---

### PRIORITY QUESTION #5: Code Export & Portability

**Current Status**: 🔴 CRITICAL (questions 3.1, 3.2, 10.1)

**Ask Yourself**:
- How important is avoiding vendor lock-in?
- Do you need to migrate away from tools easily?
- Is this regulatory or practical?

**Options**:
- [ ] Keep as 🔴 CRITICAL (zero lock-in tolerance)
- [ ] Downgrade to 🟡 HIGH (prefer portability but can accept some dependencies)

**Your Decision**: ________________

---

## Missing Questions?

Are there important questions we should ADD?

### SUGGESTED ADDITION #1: Team Size Support

**Proposed Question**: "What team sizes does it support well?"
- Solo developers
- Small teams (2-10)
- Medium teams (10-50)
- Enterprise teams (50+)

**Add this question?**: [ ] Yes / [ ] No

---

### SUGGESTED ADDITION #2: Learning Curve

**Proposed Question**: "What is the learning curve for developers familiar with VS Code?"
- Minimal (< 1 day)
- Moderate (1-3 days)
- Significant (1+ weeks)

**Add this question?**: [ ] Yes / [ ] No

---

### SUGGESTED ADDITION #3: Vendor Stability

**Proposed Question**: "What is the vendor's funding/stability status?"
- Public company
- Well-funded startup (Series B+)
- Early-stage startup
- Open source project

**Add this question?**: [ ] Yes / [ ] No

---

### YOUR ADDITIONS:

Any questions you think are missing?

1. ___________________________________________
2. ___________________________________________
3. ___________________________________________

---

## Summary of Required Decisions

Before we can proceed with re-evaluation, please provide decisions on:

### CRITICAL (Must Decide)
1. ✅ **AMBIGUITY #1** (Question 1.1 - Self-hosted): Split into dev tool vs app deployment?
2. ✅ **AMBIGUITY #2** (Questions 1.2 & 20.1): Merge duplicate air-gapped questions?
3. ✅ **AMBIGUITY #3** (Question 4.2 - Rust): Keep CRITICAL, downgrade, or remove?
4. ✅ **AMBIGUITY #4** (Question 3.2 - Dependencies): Accept clarification?

### HIGH PRIORITY (Should Decide)
5. ⚠️ **AMBIGUITY #5** (Questions 13.1-13.3): Accept clarification on scale metrics?
6. ⚠️ **AMBIGUITY #6** (Question 8.1): Split real-time vs Git collaboration?
7. ⚠️ **AMBIGUITY #7** (Question 10.1): Accept clarification on "without tool"?
8. ⚠️ **AMBIGUITY #8** (Question 1.4): Split IDE location vs AI processing?

### PRIORITY CLASSIFICATIONS (Critical for Framework)
9. 🎯 **Air-gapped priority**: Keep CRITICAL or downgrade?
10. 🎯 **Self-hosted priority**: Keep CRITICAL or downgrade?
11. 🎯 **Rust LSP priority**: Keep CRITICAL, downgrade, or remove?

---

## Next Steps

**After you complete this worksheet**:

1. I'll create **Decision Framework v2.0** with:
   - Refined questions (clear, unambiguous)
   - Adjusted priorities based on your decisions
   - Updated rationale documentation
   - Example answers for clarity

2. You review and approve v2.0

3. I systematically re-evaluate all 6 tools against v2.0

4. We produce accurate comparison with confidence

---

**Estimated Time**:
- Your decisions: 30-45 minutes
- Framework v2.0 creation: 2-3 hours
- Re-evaluation: 4-6 hours
- **Total: ~8 hours to final accurate recommendation**

---

**Status**: ⏳ Awaiting your review and decisions
