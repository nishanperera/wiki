# Performance Review Wiki Schema Template

This is a template for the schema file that configures how LLM agents interact with your performance review wiki. Copy this to `.github/copilot-instructions.md` (for GitHub Copilot) or `CLAUDE.md` (for Claude Code) and customize for your needs.

---

```markdown
# Copilot Instructions for Performance Review Workspace

## Project Overview
This workspace is a structured knowledge repository for annual performance review documentation. It tracks achievements, objectives, peer feedback, and synthesizes evidence for year-end reviews. This is not a codebase — it's a documentation and evidence-tracking system maintained by AI.

## Directory Structure
- `achievements/`: Individual achievement write-ups, each as a separate markdown file
- `objectives/`: Yearly performance objectives, one file per objective
- `reviews/`: Peer and manager feedback, organized by reviewer
- `end-of-year/`: Synthesized review materials, forms, and guidance
- `wiki/`: Documentation and setup files
- `images/`: Supporting visual evidence (screenshots, diagrams)
- `memory/`: Session memory and context for the LLM

## File Naming Conventions
- Achievements: `[YEAR]-achievement-[descriptive-slug].md`
- Objectives: `[YEAR]-objective-[descriptive-slug].md`
- Feedback: `feedback-[reviewer-name].md`
- Use lowercase with hyphens, no spaces

## Key Patterns
- Each achievement links to one or more objectives
- Feedback files contain direct quotes from reviewers
- Cross-references between achievements, objectives, and feedback are maintained by the LLM
- All evidence synthesis draws only from documented files — never invent evidence

## Target Rating Framework

### Target: [YOUR TARGET RATING]

### Criteria (customize these):
1. **[Criterion 1]**: [Description of what this looks like]
2. **[Criterion 2]**: [Description]
3. **[Criterion 3]**: [Description]
4. **[Criterion 4]**: [Description]
5. **[Criterion 5]**: [Description]

### Organizational Values (customize):
- **[Value 1]**: [What this means in practice]
- **[Value 2]**: [What this means]
- **[Value 3]**: [What this means]

### How to Apply These Criteria
When synthesizing evidence from achievements, objectives, and feedback:
- Explicitly map examples to the criteria above
- Highlight where contributions go beyond role expectations
- Surface peer feedback quotes that demonstrate recognition
- Use language aligned with the rating criteria ("significant impact", "outstanding results")
- Frame achievements to demonstrate the criteria

## Authoring Guidance for AI Agents

### When Adding Achievements
1. Create file in `achievements/` with proper naming convention
2. Include: what was done, impact/outcome, alignment to objectives
3. Update relevant objective files to reference the new achievement
4. Update `end-of-year/index.md` with the new entry
5. Identify which rating criteria the achievement demonstrates

### When Processing Feedback
1. Create or update file in `reviews/feedback-[name].md`
2. Preserve exact quotes using blockquote format (> "quote")
3. Categorize feedback as: positive, developmental, or actionable
4. Link relevant quotes to specific achievements
5. Update objective write-ups with supporting quotes

### When Synthesizing
1. Draw only from documented evidence — never invent
2. Use direct quotes to support claims
3. Map evidence explicitly to rating criteria
4. Identify gaps where evidence is weak
5. Use professional, impact-focused language

### Writing Style
- Use clear, active language focused on outcomes
- Quantify impact where possible
- Include context: what was the situation, what did you do, what was the result
- Be specific rather than vague ("reduced deployment time by 40%" not "improved efficiency")

## Operations

### Adding an Achievement
User says something like: "I just finished [project/task]" or "Document this achievement: [description]"
- Ask clarifying questions about impact and alignment
- Create the achievement file
- Update cross-references

### Processing Feedback
User shares feedback or says: "I got this feedback from [name]"
- Extract and preserve quotes
- Create/update feedback file
- Link to relevant achievements

### Health Check
User asks: "Check my wiki health" or "What am I missing?"
- Review objectives for evidence coverage
- Check achievements for linked feedback
- Identify gaps in rating criteria evidence
- Suggest what to document or who to ask for feedback

### Synthesize for Review
User asks: "Draft my year-end summary" or "Summarize objective X"
- Synthesize across all relevant files
- Include embedded quotes and evidence
- Align to rating criteria
- Identify any remaining gaps

## Important Reminders
- **Never invent evidence** — only reference what's in the files
- **Preserve exact quotes** — direct quotes are powerful evidence
- **Maintain cross-references** — every achievement should link to objectives
- **Think about gaps** — proactively identify what's missing
- **Encourage regular capture** — achievements documented fresh are more detailed
```

---

## Customization Guide

1. **Replace `[YOUR TARGET RATING]`** with your organization's rating level (e.g., "Exceptional Performer", "Exceeds Expectations")

2. **Fill in the criteria** from your organization's rating framework. These typically come from:
   - Your performance review form
   - Your manager's expectations
   - HR documentation on what defines each rating level

3. **Add organizational values** if your company emphasizes specific values in reviews

4. **Adjust the directory structure** if you prefer a different organization

5. **Add role-specific guidance** if certain achievements are particularly valued in your field

---

## Example: Tech Industry Criteria

```markdown
### Target: Exceeds Expectations

### Criteria:
1. **Delivery**: Consistently delivers high-quality work ahead of schedule
2. **Technical Excellence**: Demonstrates deep expertise and raises team standards
3. **Impact**: Work has measurable business impact beyond immediate scope
4. **Collaboration**: Actively helps others succeed, shares knowledge
5. **Leadership**: Takes initiative, drives improvements without being asked
6. **Growth**: Continuously learns and applies new skills

### Values:
- **Customer Focus**: Decisions prioritize customer outcomes
- **Innovation**: Finds better ways to solve problems
- **Ownership**: Takes responsibility for outcomes, not just tasks
```

---

## Example: Generic Corporate Criteria

```markdown
### Target: High Performer

### Criteria:
1. **Results**: Achieves or exceeds all objectives
2. **Behaviors**: Consistently demonstrates company values
3. **Teamwork**: Contributes positively to team success
4. **Development**: Shows growth in skills and capabilities
5. **Initiative**: Proactively identifies and solves problems
6. **Communication**: Effectively shares information and ideas

### Values:
- **Integrity**: Acts ethically and honestly
- **Respect**: Treats others with dignity
- **Excellence**: Strives for high quality in all work
```
