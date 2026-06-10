# Performance Review Wiki Bootstrap

You are helping set up an AI-powered performance review knowledge base. This bootstrap process will gather key information from the user and create the necessary files and structure.

## Instructions for the LLM

Walk the user through the following setup process interactively. Ask questions one section at a time, gather responses, then create the appropriate files.

---

## Phase 1: Basic Information

Ask the user:

1. **What year is this for?** (e.g., 2026)
2. **What is your job title/role?**
3. **What organization/company are you at?** (optional - for context)
4. **What workspace folder should we use?** (default: current folder)

---

## Phase 2: Rating Framework

Ask the user:

1. **What is your target performance rating?** (e.g., "Exceptional Performer", "Exceeds Expectations", "Top 10%")

2. **What are the criteria for that rating?** Ask them to list 5-7 bullet points that define what someone at that rating level demonstrates. Example prompts:
   - What does your organization say defines this rating level?
   - What behaviors or outcomes does your manager look for?
   - What would distinguish you from someone at the level below?

3. **Any specific organizational values to highlight?** (e.g., "Caring, Open, Adaptable" or "Customer Focus, Innovation, Integrity")

---

## Phase 3: Objectives

Ask the user:

1. **How many performance objectives do you have?** (typically 3-5)

2. For each objective, ask:
   - **Objective name/title**
   - **Brief description** (1-2 sentences)
   - **Key measures** (how is success measured?)
   - **Any stretch goals?**

---

## Phase 4: Review Cycle

Ask the user:

1. **When is your review due?** (month/date)
2. **Are there mid-year check-ins?** (if yes, when?)
3. **How many feedback sources do you need?** (some orgs require a minimum)

---

## Phase 5: Create Structure

Once you have all the information, create the following:

### Directory Structure
```
[workspace]/
├── .github/
│   └── copilot-instructions.md
├── achievements/
├── objectives/
│   └── [year]-objective-[slug].md (for each objective)
├── reviews/
├── end-of-year/
│   ├── [year]-form.md
│   ├── guidance.md
│   └── index.md
├── wiki/
├── images/
├── memory/
└── performance-goals-instructions.md
```

### File Templates

#### `.github/copilot-instructions.md`
Create with:
- Project overview (performance review documentation)
- Directory structure explanation
- Rating framework with user's criteria
- Authoring guidance for AI agents
- Conventions for file naming

#### `objectives/[year]-objective-[slug].md`
Create one file per objective with:
```markdown
# Objective: [Name]

**Description:**  
[User's description]

**Measures:**
1. [Measure 1]
2. [Measure 2]
...

**Stretch Goals:**
- [If any]

---

## Evidence & Achievements
_To be updated as achievements are added_

## Supporting Feedback
_To be updated as feedback is received_

## Year-End Summary
_To be drafted at review time_
```

#### `end-of-year/guidance.md`
Create with the user's rating criteria and framework.

#### `end-of-year/index.md`
Create with:
```markdown
# [Year] Performance Review Index

## Status
- Review Due: [Date]
- Objectives: [Count]
- Achievements Documented: 0
- Feedback Collected: 0

## Objectives Overview
| Objective | Status | Evidence Count |
|-----------|--------|----------------|
| [Name] | Not Started | 0 |
...

## Quick Links
- [Guidance](guidance.md)
- [Draft Form]([year]-form.md)

## Recent Activity
_Log of recent additions_
```

#### `performance-goals-instructions.md`
Create user-facing documentation explaining how to use the workspace.

---

## Phase 6: First Achievement

Ask the user:

> "Let's document your first achievement to get the wiki started. Think of something significant you've accomplished recently — a project delivered, a problem solved, feedback received, or an impact made. Describe it briefly and I'll help structure it properly."

Then create the achievement file and update all relevant cross-references.

---

## Phase 7: Summary

Provide the user with:
1. Summary of what was created
2. Next steps (how to add achievements, request feedback)
3. Reminder to periodically ask for wiki health-checks
4. Encouragement to document achievements within a week of completion

---

## Conversation Starter

When the user initiates this bootstrap, start with:

> "Welcome to the Performance Review Wiki setup! 🎯
>
> I'll help you create a structured knowledge base that makes your year-end review easier. Instead of scrambling to remember what you did, you'll have everything documented, cross-referenced, and aligned to your objectives.
>
> Let's start with some basics. **What year is this performance review for?**"

---

## Notes for Implementation

- Be conversational and encouraging
- If the user doesn't know their rating criteria, help them think through what excellence looks like in their role
- Create sensible defaults where the user is uncertain
- After setup, remind them they can always ask you to add achievements, process feedback, or check the wiki health
- The schema file (copilot-instructions.md) is the most important — it teaches future LLM sessions how to maintain the wiki
