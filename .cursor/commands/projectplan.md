---
name: projectplan
description: Create project_details.md planning document for a project from project_ideas.md
---

# Project Plan Command

## Usage

```
/projectplan <project-number>
```

**Example:**
```
/projectplan 1
```

This will create a planning document for "Project 1: Personal Voice Journal with Audio Summarization" from project_ideas.md.

---

## What This Command Does

When you run `/projectplan <project-number>`, the system will:

1. **Parse project_ideas.md** and locate the project by number (1-30)
2. **Extract project details**: Name, description, tech stack, features, difficulty
3. **Validate and adjust tech stack** to match ONLY allowed technologies:
   - Replace PostgreSQL/MongoDB → SQLite
   - Replace JWT/OAuth → Firebase Auth
   - Replace OCR libraries → LangChain + LLM
   - Remove Docker, Redis, Celery, etc.
4. **Normalize project name** to folder format (e.g., "Personal Voice Journal" → "personal-voice-journal")
5. **Create project folder** at workspace root: `<project-name>/`
6. **Generate project_details.md** with all required sections:
   - Project overview and description
   - Complete feature list with implementation approach
   - Technology stack specification
   - Possible challenges and solutions
   - All backend API endpoints (with protection status and LLM requirements)
   - All frontend pages (with routes and protection status)
   - All components (with usage mapping)
   - Component-to-page mapping
   - Issue planning overview (15-20 issues)
   - Issue-to-responsibility mapping
7. **DO NOT create issues folder** - that comes after approval

---

## Output Structure

After running `/projectplan 1`, you will have:

```
personal-voice-journal/
└── project_details.md
```

**The project_details.md file contains:**
- Complete project blueprint
- All endpoints, pages, and components
- Issue planning with clear mapping
- Technology stack (validated against allowed tech)
- Implementation approach for each feature
- Challenges and solutions

---

## Next Steps After Generation

1. **Review the project_details.md file**
   - Check that all features are included
   - Verify endpoints are complete
   - Ensure pages and components are listed
   - Confirm issue planning makes sense

2. **Request changes if needed**
   - Edit the project_details.md file directly
   - Add missing features or endpoints
   - Adjust component structure
   - Modify issue planning

3. **Get team approval**
   - Share with team for review
   - Incorporate feedback
   - Finalize the document

4. **Generate issues**
   - Once approved, run: `/generate <path-to-project_details.md>`
   - Example: `/generate personal-voice-journal/project_details.md`
   - This creates all issues based on the approved plan

---

## Key Features

### Two-Phase Workflow

This command implements a two-phase workflow:

```
Phase 1: Planning
/projectplan 1 → Creates project_details.md → Team reviews → Approval

Phase 2: Issue Generation
/generate path → Creates all issues based on approved plan
```

### Comprehensive Planning

The generated project_details.md includes:

**Technical Specifications:**
- All backend endpoints with full details
- All frontend pages with routes
- All components with usage mapping
- Database schema (high-level)
- Technology stack

**Project Planning:**
- Issue count estimate (15-20)
- Issue-to-responsibility mapping
- Which issue builds which page
- Which issue creates which component
- Which issue implements which endpoint

**Implementation Guidance:**
- How each feature will be implemented
- What technologies will be used
- Possible challenges and solutions
- Success criteria

### Technology Validation

All technologies are automatically validated:
- **Allowed:** Python, FastAPI, React, SQLite, Firebase, LangChain, Tailwind
- **Replaced:** PostgreSQL→SQLite, JWT→Firebase, OCR→LLM, Docker→Remove
- **Prohibited:** CrewAI, Next.js, MongoDB, Redis, Celery, etc.

### Project Type Patterns

The command uses project type patterns to generate appropriate structure:

**Audio Projects:**
- Upload audio endpoints
- LLM-based audio analysis (NO specialized libraries)
- Transcription and summary features
- Audio player components

**Image Projects:**
- Upload image endpoints
- Vision LLM analysis (NO OCR libraries)
- Image viewer components
- Analysis results display

**NLP + Database Projects:**
- Document upload endpoints
- LangChain semantic search
- RAG implementation
- Search interface components

**Hybrid Projects:**
- Multiple input types
- Multi-modal analysis
- Complex workflows
- Rich data visualization

---

## Arguments

- **project-number**: Required. Integer between 1-30 corresponding to projects in project_ideas.md

---

## Rules Applied

This command follows rules defined in:

1. **technology-constraints.mdc** - Allowed/prohibited technologies
2. **project-planning.mdc** - project_details.md template and guidelines
3. **project-types.mdc** - Patterns for different project types

---

## Project Ideas Source

All projects come from `project_ideas.md` which contains 30 full-stack agentic AI projects organized in 4 categories:

1. **Audio Processing + NLP** (Projects 1-8)
   - Personal Voice Journal
   - Meeting Note Taker
   - Podcast Chapter Generator
   - Voice Command Todo Manager
   - Audio Emotion Detector
   - Language Learning Audio Quiz
   - Customer Support Audio Analyzer
   - Sleep Meditation Generator

2. **Image Processing + Vision** (Projects 9-16)
   - Receipt Scanner and Expense Tracker
   - Plant Disease Identifier
   - Document Scanner and Organizer
   - Fashion Style Recommender
   - Handwriting Recognition Note App
   - Real Estate Property Analyzer
   - Art Style Transfer and Analysis
   - Quality Control Inspector

3. **NLP + Database Query** (Projects 17-23)
   - Personal Knowledge Base
   - SQL Query Generator
   - Customer Support Chatbot
   - Research Paper Summarizer
   - Job Recommendation Engine
   - Email Smart Assistant
   - Content Recommendation System

4. **Hybrid Multi-Modal** (Projects 24-30)
   - AI Resume Reviewer
   - Automated Invoice Processing
   - Food Recognition and Nutrition Analyzer
   - Event Planning Assistant
   - Medical Report Analyzer
   - Real Estate Listing Generator
   - Interview Preparation Coach

---

## Examples

Create planning documents for different project types:

```
/projectplan 1    # Audio: Personal Voice Journal
/projectplan 9    # Image: Receipt Scanner
/projectplan 17   # NLP: Personal Knowledge Base
/projectplan 24   # Hybrid: AI Resume Reviewer
```

---

## What Gets Generated

For each project, the system generates a comprehensive `project_details.md` with:

### 1. Project Overview
- Detailed description
- Target users
- Core value proposition

### 2. Features
- Complete feature list
- Implementation approach for each feature
- Technology mapping

### 3. Technology Stack
- Frontend: React, Vite, Tailwind, Router
- Backend: Python, FastAPI, Uvicorn
- Database: SQLite (data only)
- Auth: Firebase (authentication only)
- AI: LangChain + LLM

### 4. API Endpoints
Table with:
- Method (GET, POST, PUT, DELETE)
- Endpoint path
- Protected status (Yes/No)
- Purpose
- LLM integration required (Yes/No)
- Request/Response format

### 5. Frontend Structure
- All pages with routes and protection status
- All components with usage details
- Component-to-page mapping

### 6. Issue Planning
- Estimated issue count (15-20)
- Issue categories (Foundation, Core, Advanced, Testing)
- Issue-to-responsibility mapping
- Which issue builds what

### 7. Challenges and Solutions
- Technical challenges
- Learning curve challenges
- Proposed solutions

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
| "Whisper API" | LangChain + LLM | Use LLM for audio |
| "PyTesseract OCR" | Vision LLM | Use LLM for images |

---

## Validation

Before completing generation, the system verifies:

□ Project exists in project_ideas.md
□ All features are extracted
□ Tech stack uses only allowed technologies
□ Disallowed tech is replaced or removed
□ Project name is normalized correctly
□ All required sections are included
□ Endpoints are clearly defined
□ Pages and components are listed
□ Issue planning is complete
□ Issue count is 15-20
□ Final testing issue is included

---

## Important Notes

- This command creates the **planning document only**
- No issues are generated yet
- The document is meant to be **reviewed and approved**
- You can **edit the document** after generation
- Only after approval should you run `/generate`
- The document serves as **single source of truth**
- All issue generation will be based on this document

---

## Workflow Example

```bash
# Step 1: Create planning document
/projectplan 1

# Step 2: Review the generated file
# Open: personal-voice-journal/project_details.md
# Review all sections, endpoints, pages, components

# Step 3: Make changes if needed
# Edit the file directly to add/remove/modify anything

# Step 4: Get team approval
# Share with team, incorporate feedback

# Step 5: Generate issues (only after approval)
/generate personal-voice-journal/project_details.md

# Step 6: Issues are created
# Now you have: personal-voice-journal/issues/issue-01-project-setup.md, etc.
```

---

## Benefits of This Approach

1. **Review Before Generation** - Catch issues early
2. **Single Source of Truth** - All info in one place
3. **Easy to Modify** - Edit the planning document
4. **Team Alignment** - Everyone sees the plan
5. **Better Issues** - Generated from approved blueprint
6. **Less Rework** - Get it right before creating issues
7. **Clear Scope** - Know exactly what will be built
8. **Predictable Output** - Issues match the plan

---

## Remember

- This is **Phase 1** of the two-phase workflow
- The output is a **planning document**, not issues
- The document should be **reviewed and approved**
- Only after approval should you run `/generate`
- The planning document can be **edited** as needed
- This ensures **quality and alignment** before issue generation
