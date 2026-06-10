# AI-Powered Performance Review System

A pattern for building personal performance review knowledge bases using LLMs.

This is an idea file, designed to be shared with your LLM Agent (Claude Code, GitHub Copilot, Cursor, or any AI coding assistant). Its goal is to communicate the high-level idea — your agent will build out the specifics in collaboration with you.

---

## The Core Idea

Most people's approach to annual performance reviews looks like scrambling: you dig through old emails, chat logs, and calendar invites the week before your review is due, trying to reconstruct what you accomplished over the past year. You ask colleagues for feedback at the last minute. You forget achievements, undersell your impact, and the process feels painful.

The idea here is different. Instead of reconstructing your year from scattered sources at review time, the LLM incrementally builds and maintains a persistent performance wiki — a structured, interlinked collection of markdown files that sits between you and the raw events of your work year.

When you complete a significant piece of work, receive feedback, or achieve a goal, you (or the LLM) don't just file it away. The achievement is documented with context, aligned to your objectives, linked to relevant feedback, and integrated into your evolving performance narrative. The evidence is compiled once and kept current, not re-derived when reviews are due.

**This is the key difference**: the wiki is a persistent, compounding artifact. The cross-references are already there. The feedback is already tied to achievements. The synthesis already reflects everything you've done. The wiki keeps getting richer with every accomplishment you add and every piece of feedback you receive.

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of capturing events as they happen, directing the analysis, and asking the right questions. The LLM does all the grunt work — the summarizing, cross-referencing, filing, and narrative-building that makes a performance case actually compelling at year-end.

### Why This Works for Performance Reviews

Performance reviews have unique challenges that make them ideal for this pattern:

- **Recency bias**: Without documentation, you only remember recent work. The wiki captures everything.
- **Evidence gathering**: Claims need proof. The wiki maintains links between achievements and supporting feedback.
- **Narrative building**: Reviews need a coherent story. The wiki synthesizes patterns across your year.
- **Rating alignment**: You need to demonstrate you meet criteria. The wiki explicitly maps evidence to rating requirements.
- **Feedback collection**: Good reviews need diverse perspectives. The wiki tracks feedback requests and responses.

---

## Architecture

There are three layers:

### 1. Raw Sources
Your curated collection of evidence as it happens. Achievement descriptions, feedback received, objectives set, presentations delivered, kudos received. These are immutable once captured — the LLM reads from them but structures them into the wiki. This is your source of truth.

**Directory**: `achievements/`, `reviews/`, `objectives/`

### 2. The Wiki
A directory of LLM-generated and maintained markdown files. Summaries, objective write-ups, cross-referenced feedback, an index, a synthesis. The LLM owns this layer. It creates pages, updates them when new achievements arrive, maintains cross-references between feedback and accomplishments, and keeps everything aligned with your target rating criteria.

**Directory**: `end-of-year/`, `wiki/`

### 3. The Schema
A document (`.github/copilot-instructions.md` for GitHub Copilot, `CLAUDE.md` for Claude Code, or `AGENTS.md` for Codex) that tells the LLM how the wiki is structured, what conventions to follow, and what workflows to use when ingesting achievements, processing feedback, or synthesizing your year. This is the key configuration file — it's what makes the LLM a disciplined performance review assistant rather than a generic chatbot.

**File**: `.github/copilot-instructions.md` or equivalent

---

## Directory Structure

```
performance-wiki/
├── .github/
│   └── copilot-instructions.md    # Schema: tells the LLM how to maintain the wiki
├── achievements/                   # Raw: individual accomplishments
│   ├── 2026-achievement-project-x-delivery.md
│   ├── 2026-achievement-team-mentoring.md
│   └── ...
├── objectives/                     # Raw: yearly performance objectives
│   ├── 2026-objective-delivery.md
│   ├── 2026-objective-collaboration.md
│   └── ...
├── reviews/                        # Raw: feedback from colleagues
│   ├── feedback-colleague-a.md
│   ├── feedback-manager-b.md
│   └── ...
├── end-of-year/                    # Wiki: synthesized review materials
│   ├── 2026-form.md               # Final review form content
│   ├── guidance.md                # Rating criteria and framework
│   └── index.md                   # Navigation and synthesis
├── wiki/                          # Wiki: additional documentation
│   └── ...
├── images/                        # Supporting visual evidence
├── memory/                        # Session memory for the LLM
└── performance-goals-instructions.md  # User-facing documentation
```

---

## Operations

### Ingest Achievement
You complete significant work and tell the LLM to document it. An example flow:

1. You describe what you accomplished
2. The LLM asks clarifying questions about impact, alignment to objectives, supporting evidence
3. The LLM creates an achievement file with structured content
4. The LLM updates relevant objective files to reference the new achievement
5. The LLM updates the index/synthesis with the new entry
6. Optionally, the LLM identifies which colleagues could provide supporting feedback

A single achievement might touch 3-5 wiki pages. The key insight: the LLM maintains the cross-references so you don't have to.

### Ingest Feedback
You receive feedback from a colleague. The flow:

1. You share the raw feedback (copy/paste from email, Slack, etc.)
2. The LLM creates or updates a feedback file for that reviewer
3. The LLM extracts key quotes and tags them as positive, developmental, or actionable
4. The LLM links relevant feedback to specific achievements
5. The LLM updates your objective write-ups with supporting quotes
6. The LLM identifies if the feedback reveals gaps or new achievements to document

### Query
You ask questions against the wiki:

- "What evidence do I have for the 'Exceptional Performer' rating?"
- "Which objectives am I weakest on?"
- "What feedback have I received about leadership?"
- "How many people have I gotten feedback from this year?"
- "Draft my year-end summary for Objective 2"

The LLM synthesizes answers with citations to specific files and quotes.

### Synthesize
At review time, ask the LLM to generate:

- Complete objective write-ups with embedded evidence and feedback quotes
- Self-assessment summaries aligned to rating criteria
- Gap analysis: what's missing, what additional evidence would strengthen the case
- Counter-narrative: what a skeptical reviewer might say, and how to address it

### Lint
Periodically, ask the LLM to health-check the wiki:

- Objectives without sufficient supporting achievements
- Achievements without linked feedback
- Feedback files that haven't been integrated into objectives
- Rating criteria without mapped evidence
- Stale or outdated information
- Missing dates or context

---

## Rating Framework

The schema should include your organization's rating criteria. The LLM uses these to:

1. **Tag achievements** with which criteria they demonstrate
2. **Identify gaps** where you lack evidence for specific criteria
3. **Frame language** in write-ups to match the rating vocabulary
4. **Build the case** by explicitly mapping evidence to each criterion

Example criteria structure (customize for your organization):

```markdown
## Target Rating: [Rating Name]

### Criteria:
- **Criterion 1**: Delivers and exceeds objectives within role
- **Criterion 2**: Makes substantial contributions beyond immediate role  
- **Criterion 3**: Consistently recognized for outstanding results
- **Criterion 4**: Role model for organizational values
- **Criterion 5**: Builds capability in others
- **Criterion 6**: Proactive in innovation and new solutions
- **Criterion 7**: Resilient and organizationally aware

### How the LLM Applies These:
- When synthesizing evidence, explicitly map examples to criteria
- Highlight where contributions go beyond role expectations
- Surface feedback quotes that demonstrate external recognition
- Frame achievements using aligned language ("significant impact", "outstanding results")
```

---

## Indexing and Logging

Two special files help the LLM (and you) navigate the wiki:

### index.md
Content-oriented catalog of everything in the wiki. Each achievement, objective, and feedback file listed with a one-line summary, date, and linked objectives/criteria. The LLM updates it on every ingest. When answering a query, the LLM reads the index first to find relevant content.

### log.md (optional)
Chronological record of what happened and when — achievements documented, feedback received, objectives updated. Useful tip: if each entry starts with a consistent prefix (e.g., `## [2026-03-15] achievement | Project X Delivery`), the log becomes parseable and gives you a timeline of your year.

---

## Feedback Collection Strategy

Good performance reviews need diverse, specific feedback. The wiki helps you:

### Plan Feedback Requests
- After significant events (presentations, project completions, collaborations)
- From diverse sources (peers, manager, stakeholders, cross-functional partners)
- With specific, tailored questions (not just "how am I doing?")

### Template for Feedback Requests
```markdown
## [Event Name] - [Date]

### Context
[Brief description of what happened and your role]

### Questions
1. What went well?
2. What could I improve on?
3. [Specific question related to the event]
4. Any additional comments?
```

### Track Feedback Status
The LLM can maintain a view of:
- Who you've requested feedback from
- Who has responded
- What events are missing feedback coverage
- Gaps in feedback diversity (e.g., all from same team)

---

## Tips and Tricks

- **Capture early, capture often**: Document achievements within a week of completion. Details fade fast.

- **Include the "why"**: Not just what you did, but why it mattered and what impact it had.

- **Quantify where possible**: Numbers make achievements concrete. "Improved deployment time" vs "Reduced deployment time by 40%".

- **Save the quotes**: When someone says something positive in chat or email, capture the exact quote. Direct quotes are powerful evidence.

- **Request developmental feedback**: Not all feedback should be positive. Showing you sought and acted on constructive feedback demonstrates growth mindset.

- **Link everything**: Every achievement should link to an objective. Every piece of feedback should link to an achievement or behavior it validates.

- **Review quarterly**: Don't wait for year-end. Ask the LLM to do a quarterly health-check of your wiki.

- **The wiki is git-tracked**: You get version history for free. You can see how your narrative evolved.

---

## The Schema Template

Your schema file (e.g., `.github/copilot-instructions.md`) should include:

```markdown
# Performance Review Wiki Instructions

## Project Overview
[What this workspace is for]

## Directory Structure  
[Explain each folder's purpose]

## Conventions
[File naming, date formats, required fields]

## Rating Framework
[Your organization's criteria]

## Authoring Guidance
[How the LLM should write, what voice to use, how to handle evidence]

## Operations
[Standard workflows for ingest, query, synthesize]
```

---

## Why This Works

The tedious part of performance reviews is not the reflecting or the thinking — it's the evidence gathering, the cross-referencing, the narrative building, the ensuring you haven't forgotten anything, the aligning every claim to supporting proof. Humans procrastinate on this because the maintenance burden is painful. LLMs don't get tired, don't forget to link an achievement to its supporting feedback, and can touch 10 files in one pass to keep everything consistent.

The human's job is to capture achievements as they happen, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.

Most people undersell themselves in reviews not because they lack accomplishments, but because they lack evidence and narrative. The wiki solves both: evidence is captured systematically, narrative is synthesized continuously.

---

## Getting Started

1. **Run the Bootstrap Prompt**: Share `BOOTSTRAP.prompt.md` with your LLM to set up your workspace interactively
2. **Set Your Objectives**: Document your yearly objectives at the start of the year (or now, if mid-year)
3. **Configure Your Rating Framework**: Add your organization's criteria to the schema
4. **Start Capturing**: Document your first achievement and request your first feedback
5. **Let It Compound**: The wiki gets more valuable with every addition

---

## Note

This document is intentionally abstract. It describes the pattern, not a specific implementation. The exact directory structure, the schema conventions, the file formats — all of that will depend on your organization, your role, and your LLM of choice. The right way to use this is to share it with your LLM agent and work together to instantiate a version that fits your needs. The document's only job is to communicate the pattern. Your LLM can figure out the rest.

---

*Inspired by [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)*
