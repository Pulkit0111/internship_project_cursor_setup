---
name: generate
description: Generate a complete set of 20-25 issues for a project from project_ideas.md with guardrails for consistency
---

# Generate Project Issues Command

## Usage

```
/generate <project-number>
```

**Example:**
```
/generate 3
```

This will generate issues for "Project 3: Podcast Chapter Generator" from project_ideas.md.

---

## What This Command Does

When you run `/generate <project-number>`, the system will:

1. **Parse project_ideas.md** and locate the project by number (1-30)
2. **Extract project details**: Name, description, tech stack, features, difficulty
3. **Validate and adjust tech stack** to match ONLY allowed technologies:
   - Python (basics)
   - FastAPI (CRUD only)
   - React (basics)
   - SQLite (data storage, NOT auth)
   - Firebase (authentication ONLY)
   - LangChain (basic usage with LLMs)
4. **Replace disallowed tech automatically**:
   - PostgreSQL/MongoDB → SQLite
   - JWT/OAuth → Firebase Auth
   - OCR libraries → LangChain + LLM
   - Docker → Remove (run locally)
5. **Normalize project name** to folder format (e.g., "Project 3: Podcast Chapter Generator" → "podcast-chapter-generator")
6. **Create project structure**: `<project-name>/issues/` directory
7. **Generate Issue #01**: Project Setup (README format, no template sections)
8. **Generate PROJECT-README.md**: Auto-generated issue flow explanation
9. **Generate Issues #02-24**: Project-specific issues following:
   - Progressive difficulty (Foundation → Firebase Auth → CRUD → Advanced)
   - Guardrails for consistency
   - Firebase authentication (NOT backend auth)
   - SQLite for data (NOT for auth)
   - Time estimates: 60-120 minutes per issue
10. **Apply all guardrails**: Ensures consistent output across any AI model
11. **Map dependencies**: Proper dependency chains with no circular dependencies

---

## Output Structure

After running `/generate 3`, you will have:

```
podcast-chapter-generator/
├── issues/
│   ├── issue-01-project-setup.md                 (README format)
│   ├── issue-02-landing-page-ui.md               (Static UI)
│   ├── issue-03-signup-page-ui.md                (Static form)
│   ├── issue-04-login-page-ui.md                 (Static form)
│   ├── issue-05-firebase-auth-setup.md           (Firebase config)
│   ├── issue-06-integrate-signup-firebase.md     (Firebase integration)
│   ├── issue-07-integrate-login-firebase.md      (Firebase integration)
│   ├── issue-08-dashboard-ui.md                  (Protected route)
│   ├── issue-09-upload-podcast-api.md
│   ├── issue-10-upload-podcast-ui.md
│   ├── issue-11-integrate-upload.md
│   ├── issue-12-process-podcast-llm.md           (LangChain + LLM)
│   ├── issue-13-display-analysis.md
│   ├── issue-14-get-podcasts-api.md
│   ├── issue-15-display-podcasts-dashboard.md
│   ├── issue-16-podcast-detail-ui.md
│   ├── issue-17-get-podcast-detail-api.md
│   ├── issue-18-integrate-detail-page.md
│   ├── issue-19-delete-podcast-api.md
│   ├── issue-20-integrate-delete.md
│   ├── issue-21-export-chapters-api.md
│   └── issue-22-integrate-export.md
└── PROJECT-README.md                              (Issue flow explanation)
```

---

## Key Features

### Guardrails for Consistency

All generated issues follow strict guardrails to ensure consistent output:

1. **Format Guardrails**: Exact 10-section template structure
2. **Content Guardrails**: No code snippets, no schemas, no prescriptive details
3. **Naming Guardrails**: Deterministic file names for first 8 issues
4. **Issue-Specific Guardrails**: Per-issue rules (static UI, Firebase auth, etc.)
5. **Technology Guardrails**: Only allowed tech, auto-replace forbidden tech
6. **Dependency Guardrails**: Logical flow, no circular dependencies
7. **Time Guardrails**: Every issue 60-120 minutes
8. **Abstraction Guardrails**: WHAT to build, not HOW (students decide implementation)
9. **Validation Checkpoints**: Pre/post generation verification
10. **Escape Prevention**: No creative deviations from template

### Firebase Authentication

All projects use Firebase for authentication:
- **Issue #05**: Firebase Auth Setup
- **Issue #06**: Integrate Signup with Firebase (NOT "Connect to Backend")
- **Issue #07**: Integrate Login with Firebase (NOT "Connect to Backend")
- NO backend auth logic
- NO password hashing
- NO session tables

### SQLite for Data Only

SQLite is used ONLY for application data:
- Store todos, notes, files, etc.
- CRUD operations
- NOT for user authentication
- Students design their own schemas (no predefined fields)

### LangChain for AI Features

Use LangChain + LLMs for AI tasks:
- NO OCR libraries (PyTesseract, etc.)
- Use vision-enabled LLMs to understand images
- Use LLMs to analyze audio/documents
- Keep analysis conceptual, not prescriptive

### Progressive Difficulty

```
Phase 1 (Issues 01-05): Foundation
- Project setup, static UI pages, Firebase setup

Phase 2 (Issues 06-07): Firebase Authentication
- Integrate signup and login with Firebase

Phase 3 (Issue 08): Dashboard
- Protected route, user-specific content

Phase 4 (Issues 09-18): CRUD Operations
- Create, Read, Update, Delete for main features

Phase 5 (Issues 19-24): Advanced Features
- AI features with LangChain, export, additional functionality
```

---

## Arguments

- **project-number**: Required. Integer between 1-30 corresponding to projects in project_ideas.md

---

## Rules Applied

All issues generated by this command follow the rules defined in `.cursor/rules/issue-generation.mdc`:

**Allowed Technologies:**
- Python (basics)
- FastAPI (CRUD only)
- React (basics with hooks and router)
- SQLite (data storage only, NOT auth)
- Firebase (authentication only)
- LangChain (basic LLM usage)
- Tailwind CSS

**Prohibited Technologies:**
- JWT, OAuth, backend auth
- OCR libraries
- Docker, Kubernetes
- PostgreSQL, MongoDB, Redis
- Celery, background workers
- Complex agents, CrewAI

**Content Rules:**
- No code snippets
- No database schemas or field definitions
- High-level guidance only (WHAT not HOW)
- Students make implementation decisions
- Time estimates: 60-120 minutes per issue

---

## Project Ideas Source

All projects come from `project_ideas.md` which contains 30 full-stack agentic AI projects organized in 4 categories:

1. **Audio Processing + NLP** (Projects 1-8)
2. **Image Processing + Vision** (Projects 9-16)
3. **NLP + Database Query** (Projects 17-23)
4. **Hybrid Multi-Modal** (Projects 24-30)

---

## Examples

Generate issues for different project types:

```
/generate 1    # Personal Voice Journal (Audio + NLP)
/generate 9    # Receipt Scanner (Image → LLM analysis, NOT OCR)
/generate 17   # Personal Knowledge Base (NLP + Database + RAG)
/generate 24   # AI Resume Reviewer (Hybrid with LLM analysis)
```

---

## What Gets Auto-Generated

For each project, the system generates:

1. **Issue #01**: Project Setup README (setup instructions, no template sections)
2. **PROJECT-README.md**: Explains issue progression and learning journey
3. **Issues #02-08**: Foundation + Firebase auth (fixed pattern for all projects)
4. **Issues #09-24**: Project-specific CRUD and features

Total: 20-24 issues + 1 project README

---

## Tech Stack Adjustments

The system automatically adjusts tech stacks to match what students know:

| Project Mentions | System Uses | Reason |
|------------------|-------------|--------|
| "PostgreSQL database" | SQLite | Students only know SQLite |
| "JWT authentication" | Firebase Auth | Only allowed auth method |
| "OCR text extraction" | LangChain + LLM | Use LLMs to understand content |
| "Docker deployment" | Local setup | No containerization |
| "CrewAI agents" | Basic LangChain | Simple chains only |

---

## Issue Format

Each issue (except #01) follows this structure:

```
# Issue Title                           (H1, not H2)

## Summary                               (What and why)
## Learning goals                        (3-4 objectives)
## Requirements / Acceptance criteria   (5+ checkboxes)
## Step-by-step guide                   (5-7 steps with Action/Where/Goal/Reference)
## Time estimate                         (60-120 minutes)
## Constraints                           (Tech stack, prohibitions, notes)
## Dependencies                          (Blocked by / Unblocks)
## Definition of Done                    (5+ checkboxes)
## Raise PR                              (8 checkboxes)
```

**Issue #01 is different**: README format only, no template sections

---

## Consistency Guarantees

With the guardrails system, issues generated will be:

✅ **Structurally identical** - Same 10 sections in same order
✅ **Technologically consistent** - Only allowed tech used
✅ **Properly abstracted** - High-level guidance, no code
✅ **Correctly timed** - All issues 60-120 minutes
✅ **Logically ordered** - Proper dependencies
✅ **Beginner-friendly** - Students make decisions, learn by doing

This ensures consistent output whether Claude, GPT-4, Gemini, or any other model generates the issues.

---

## Notes

- Each project generates exactly 20-24 issues
- Issue #01 is always "Project Setup" (README format)
- Issues #02-08 follow fixed pattern (foundation + Firebase auth)
- Issues #09-24 are project-specific
- All issues follow strict guardrails for consistency
- Tech stack is automatically validated and adjusted
- Time estimates scale with complexity (60-120 minutes)
- Firebase handles ALL authentication
- SQLite handles ALL data storage
- LangChain + LLMs handle ALL AI features
- Students design their own database schemas
- No code snippets in any issue
