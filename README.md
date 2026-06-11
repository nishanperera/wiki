# AI-Powered Performance Review System

Build a personal knowledge base that makes year-end reviews easy.

## The Problem

Performance reviews are painful because you're reconstructing your year from memory at the last minute. You forget achievements, undersell your impact, and scramble for evidence.

## The Solution

Let an LLM maintain a structured wiki of your achievements, feedback, and objectives throughout the year. When review time comes, everything is documented, cross-referenced, and ready to synthesize.

## Quick Start

### Option 1: Bootstrap (Recommended)

1. Open your AI assistant (GitHub Copilot, Claude, Cursor, etc.)
2. Share the contents of `BOOTSTRAP.prompt.md`
3. Answer the questions — the LLM will create your workspace

### Option 2: Manual Setup

1. Create this folder structure:
   ```
   performance-wiki/
   ├── .github/
   │   └── copilot-instructions.md
   ├── achievements/
   ├── objectives/
   ├── reviews/
   ├── end-of-year/
   └── wiki/
   ```

2. Customize the rating criteria for your organization

## Daily Usage

### Document an Achievement
Tell your LLM: *"I just completed [project/task]. Document this achievement."*

### Process Feedback
Share feedback you received: *"I got this feedback from [colleague]: [paste feedback]"*

### Check Progress
Ask: *"What evidence do I have for each objective?"* or *"Run a wiki health check"*

### Prepare for Review
Ask: *"Draft my year-end summary for Objective X"* or *"What gaps do I have?"*

## Tips

- **Document achievements within a week** — details fade fast
- **Request feedback after events** — not just at year-end
- **Include exact quotes** — direct quotes are powerful evidence
- **Quantify impact** — "reduced time by 40%" beats "improved efficiency"
- **Review quarterly** — don't wait until December

## Credits

Inspired by [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).
