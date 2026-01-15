---
name: generate
description: Generate a complete set of 15-20 issues from an approved project_details.md file
---

# Generate Project Issues Command

## Usage

```
/generate <path-to-project_details.md>
```

**Example:**
```
/generate personal-voice-journal/project_details.md
```

This will generate issues based on the approved project_details.md file.

---

## What This Command Does

When you run `/generate <path-to-project_details.md>`, the system will:

1. **Read and parse the approved project_details.md file**
   - Extract all project information
   - Get endpoint specifications
   - Get page and component lists
   - Get issue planning details

2. **Validate the planning document**
   - Ensure all required sections are present
   - Verify tech stack uses only allowed technologies
   - Confirm issue count is 15-20

3. **Create issues/ subfolder**
   - Inside the project folder (e.g., `personal-voice-journal/issues/`)

4. **Generate Issue #01** (Project Setup)
   - Copy EXACT content from issue-templates.mdc
   - README format with UV package manager setup
   - No modifications - same for all projects

5. **Generate Issues #02-08** (Foundation + Firebase Auth)
   - Issue #02: Landing Page UI (static)
   - Issue #03: Signup Page UI (static)
   - Issue #04: Login Page UI (static)
   - Issue #05: Firebase Auth Setup
   - Issue #06: Integrate Signup with Firebase
   - Issue #07: Integrate Login with Firebase
   - Issue #08: Dashboard UI (protected route)

6. **Generate Issues #09-onwards** (Project-specific features)
   - Based on project_details.md issue planning
   - Combined frontend+backend issues where appropriate
   - Backend issues start with database/model setup
   - Each issue includes developer flexibility note
   - Progressive difficulty: simple → complex

7. **Generate Final Testing Issue** (Last issue)
   - Complete application flow verification
   - Pages and data mapping
   - User interaction documentation
   - Protected routes verification

8. **Generate PROJECT-README.md**
   - Auto-generated project documentation
   - Issue flow explanation
   - Architecture diagrams
   - API endpoints reference

9. **Apply all guardrails**
   - Check EVERY issue against all guardrails
   - Ensure consistent formatting
   - Verify time estimates (60-120 minutes)
   - Validate dependencies

10. **Map dependencies**
    - Ensure logical flow with no circular dependencies
    - Fixed dependencies for issues 1-8
    - Project-specific dependencies for remaining issues

---

## Output Structure

After running `/generate personal-voice-journal/project_details.md`, you will have:

```
personal-voice-journal/
├── project_details.md                            (Already exists - approved plan)
├── PROJECT-README.md                             (Generated)
└── issues/
    ├── issue-01-project-setup.md                 (README format - exact copy)
    ├── issue-02-landing-page-ui.md               (Static UI)
    ├── issue-03-signup-page-ui.md                (Static form)
    ├── issue-04-login-page-ui.md                 (Static form)
    ├── issue-05-firebase-auth-setup.md           (Firebase config)
    ├── issue-06-integrate-signup-firebase.md     (Firebase integration)
    ├── issue-07-integrate-login-firebase.md      (Firebase integration)
    ├── issue-08-dashboard-ui.md                  (Protected route)
    ├── issue-09-upload-recording.md              (Combined frontend+backend)
    ├── issue-10-process-audio-llm.md             (LangChain + LLM)
    ├── issue-11-display-recordings.md            (Combined frontend+backend)
    ├── issue-12-recording-detail.md              (Combined frontend+backend)
    ├── issue-13-delete-recording.md              (Combined frontend+backend)
    ├── issue-14-tag-management.md                (Combined frontend+backend)
    ├── issue-15-search-recordings.md             (Combined frontend+backend)
    └── issue-16-final-testing.md                 (Complete flow verification)
```

**Total: 15-20 issues** (varies by project complexity)

---

## Key Features

### Two-Phase Workflow

This command is **Phase 2** of the workflow:

```
Phase 1: /projectplan <number>
   ↓
   Creates project_details.md
   ↓
   Team reviews and approves
   ↓
Phase 2: /generate <path-to-project_details.md>
   ↓
   Creates all issues based on approved plan
```

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

### New Issue Guidelines

**Developer Flexibility:**
- Every issue includes a note that developers can improve structures
- Additions/deletions of files or components are allowed if they improve the project
- Goal is clean, complete project with good UI and validation

**Backend Issues:**
- Always start with database and model setup as first step
- Only essential fields are suggested
- Developers can modify or improve models

**Combined Issues:**
- When features are strongly connected, frontend+backend are combined
- Reduces total issue count to 15-20 (instead of 20-24)
- Gives students full context of complete features
- Helps understand frontend and backend simultaneously

**Final Testing Issue:**
- Always the last issue
- Documents complete application flow
- Includes pages/data mapping, user interactions, protected routes
- Verification checklist for end-to-end testing

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

- **path-to-project_details.md**: Required. Path to the approved project_details.md file
  - Can be relative (e.g., `personal-voice-journal/project_details.md`)
  - Can be absolute (e.g., `/Users/name/Desktop/internship/personal-voice-journal/project_details.md`)

---

## Rules Applied

All issues generated by this command follow the rules defined in multiple rule files:

### 1. technology-constraints.mdc
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

### 2. issue-guardrails.mdc
**Content Rules:**
- No code snippets
- No database schemas or field definitions
- High-level guidance only (WHAT not HOW)
- Students make implementation decisions
- Time estimates: 60-120 minutes per issue
- Developer flexibility notes in every issue
- Backend issues start with DB setup
- Combined frontend+backend when appropriate

### 3. issue-templates.mdc
**Templates:**
- Issue #01: Project Setup (README format - exact copy)
- Standard template: 10 sections for issues #02-onwards
- Final testing template: Last issue with flow verification

### 4. project-types.mdc
**Patterns by project type:**
- Audio projects: LLM-based audio analysis (NO specialized libraries)
- Image projects: Vision LLM (NO OCR libraries)
- NLP projects: LangChain, embeddings, RAG
- Hybrid projects: Multi-modal analysis

---

## Prerequisites

Before running this command:

1. **Run /projectplan first**
   - Example: `/projectplan 1`
   - This creates the project_details.md file

2. **Review and approve the plan**
   - Open the generated project_details.md
   - Review all sections (endpoints, pages, components, issues)
   - Make any necessary edits
   - Get team approval

3. **Then run /generate**
   - Example: `/generate personal-voice-journal/project_details.md`
   - Issues are generated based on the approved plan

## Project Source

All projects originate from `project_ideas.md` which contains 30 full-stack agentic AI projects organized in 4 categories:

1. **Audio Processing + NLP** (Projects 1-8)
2. **Image Processing + Vision** (Projects 9-16)
3. **NLP + Database Query** (Projects 17-23)
4. **Hybrid Multi-Modal** (Projects 24-30)

The `/projectplan` command reads from project_ideas.md and creates project_details.md.
The `/generate` command reads from project_details.md and creates issues.

---

## Examples

Complete workflow for different project types:

### Example 1: Audio Project
```bash
# Step 1: Create planning document
/projectplan 1

# Step 2: Review and approve
# Open: personal-voice-journal/project_details.md
# Review, edit if needed, get approval

# Step 3: Generate issues
/generate personal-voice-journal/project_details.md

# Result: 15-20 issues created in personal-voice-journal/issues/
```

### Example 2: Image Project
```bash
# Step 1: Create planning document
/projectplan 9

# Step 2: Review and approve
# Open: receipt-scanner/project_details.md

# Step 3: Generate issues
/generate receipt-scanner/project_details.md
```

### Example 3: NLP Project
```bash
# Step 1: Create planning document
/projectplan 17

# Step 2: Review and approve
# Open: personal-knowledge-base/project_details.md

# Step 3: Generate issues
/generate personal-knowledge-base/project_details.md
```

### Example 4: Hybrid Project
```bash
# Step 1: Create planning document
/projectplan 24

# Step 2: Review and approve
# Open: ai-resume-reviewer/project_details.md

# Step 3: Generate issues
/generate ai-resume-reviewer/project_details.md
```

---

## What Gets Auto-Generated

For each project, the system generates:

1. **Issue #01**: Project Setup README (exact copy from template, no modifications)
2. **PROJECT-README.md**: Project documentation with architecture and API reference
3. **Issues #02-08**: Foundation + Firebase auth (fixed pattern for all projects)
4. **Issues #09-onwards**: Project-specific features (based on project_details.md)
5. **Final Issue**: Complete testing and flow verification

Total: 15-20 issues + 1 project README

**Issue count is flexible:**
- Simpler projects: 15-16 issues
- Complex projects: 18-20 issues
- Combined frontend+backend issues reduce count
- Always includes final testing issue

---

## Input: project_details.md

The generate command reads from the approved project_details.md file which contains:

**Project Information:**
- Project name and description
- Complete feature list
- Technology stack (already validated)
- Implementation approach

**Technical Specifications:**
- All backend API endpoints (with protection status and LLM requirements)
- All frontend pages (with routes and components)
- All components (with usage mapping)
- Database schema (high-level)

**Issue Planning:**
- Estimated issue count (15-20)
- Issue categories and progression
- Issue-to-responsibility mapping
- Which issue builds what

**This ensures:**
- Issues match the approved plan
- No surprises in generated issues
- Team alignment on scope
- Predictable output

---

## Issue Format

### Issue #01 (Project Setup)
README format with:
- Project structure
- Clone instructions (Windows & macOS)
- Prerequisites (Python 3.12+, UV, Node.js 18+, Google API Key)
- Backend setup with UV package manager
- Frontend setup with npm
- Testing instructions
- Development commands
- Technologies used
- Next steps

**EXACT copy from template - no modifications**

### Issues #02-onwards (Standard Template)
Each issue follows this structure:

```
# Issue Title                           (H1, not H2)

## Summary                               (What and why)
## Learning goals                        (3-4 objectives)
## Requirements / Acceptance criteria   (5+ checkboxes)
## Step-by-step guide                   (5-7 steps with Action/Where/Goal/Reference)
## Time estimate                         (60-120 minutes)
## Constraints                           (Tech stack, prohibitions, developer flexibility note)
## Dependencies                          (Blocked by / Unblocks)
## Definition of Done                    (5+ checkboxes)
## Raise PR                              (8 checkboxes)
```

### Final Testing Issue
Special template with:
- Complete application flow documentation
- Pages and routes table
- API endpoints table
- User interaction flow table
- Protected routes list
- Error scenarios tested
- Testing documentation template

---

## Consistency Guarantees

With the guardrails system, issues generated will be:

✅ **Structurally identical** - Same 10 sections in same order
✅ **Technologically consistent** - Only allowed tech used
✅ **Properly abstracted** - High-level guidance, no code
✅ **Correctly timed** - All issues 60-120 minutes
✅ **Logically ordered** - Proper dependencies
✅ **Beginner-friendly** - Students make decisions, learn by doing
✅ **Developer flexibility** - Can improve structures as needed
✅ **Combined when appropriate** - Frontend+backend together for related features
✅ **Complete flow** - Final testing issue documents entire application

This ensures consistent output whether Claude, GPT-4, Gemini, or any other model generates the issues.

## Benefits of Two-Phase Approach

**Phase 1 (Planning):**
- Review before generation
- Catch issues early
- Team alignment
- Easy to modify
- Single source of truth

**Phase 2 (Generation):**
- Issues match approved plan
- No surprises
- Predictable output
- Less rework
- Quality assurance

---

## Notes

- Each project generates 15-20 issues (flexible based on complexity)
- Issue #01 is always "Project Setup" (README format - exact copy)
- Issues #02-08 follow fixed pattern (foundation + Firebase auth)
- Issues #09-onwards are project-specific (based on project_details.md)
- Final issue is always testing and flow verification
- All issues follow strict guardrails for consistency
- Combined frontend+backend issues reduce total count
- Backend issues start with database/model setup
- Every issue includes developer flexibility note
- Time estimates scale with complexity (60-120 minutes)
- Firebase handles ALL authentication
- SQLite handles ALL data storage
- LangChain + LLMs handle ALL AI features
- Students design their own database schemas
- No code snippets in any issue

## Important Reminders

- **Always run /projectplan first** before /generate
- **Review and approve** project_details.md before generating issues
- **The planning document can be edited** to adjust scope or details
- **Issues are generated from the approved plan** not from project_ideas.md
- **This ensures quality and team alignment** before issue creation
