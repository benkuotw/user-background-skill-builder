---
name: user-background-skill-builder
description: >-
  Use this skill when the user wants to create or update a profile of their technical background, preferences, or workflows to give the agent better context.
---

# User Background Skill Builder

This skill helps you (the agent) interview the user to extract their deep technical background, psychological motivations, and career trajectory, and then automatically generate a highly organized "user background" skill based on those answers.

## The Methodology: The Chronological Deep-Dive

Do not settle for superficial questions like "what is your tech stack?" To truly assist a user, agents need to understand their **resilience, their career crucibles, and their problem-solving philosophy.**

When the user triggers this skill, follow these steps in order:

### 1. The Interview Phase (The "Grill Me" Approach)
Start an interactive interview with the user. Go chronologically if they have a long career. Extract both the technical achievements and the psychological "why":
*   **The Origin Story:** How did they get into tech? What did they study?
*   **Job-by-Job Breakdown:** For each major role, extract:
    *   What they actually built (not just their HR title).
    *   The environment (Was it toxic? Was it a greenfield opportunity? Was it legacy tech?)
    *   The exit (Why did they leave? What did they learn?)
*   **Pivots and Crucibles:** Ask about moments of burnout, major career pivots (e.g., trying a different industry, dropping out of a program), and how they overcame them.
*   **Current Goals:** What is their ultimate career goal (e.g., Global Remote SRE) and current study plan?

### 2. The Synthesis Phase (Multi-File Architecture)
Once you have the full story, do **not** dump it all into a single massive `SKILL.md` file. That overwhelms the agent context window. Instead, organize it into a Multi-File Reference Architecture.

Separate the content into logical, chronological narrative documents (e.g., `origin_story.md`, `job_journey.md`, `roadmaps.md`). 

### 3. The Generation Phase
Use your file-writing tools to create the new skill **next to this skill**, in the same skills folder. That is the parent folder of the folder containing this `SKILL.md` (for example `~/.claude/skills/` for Claude Code, or `.agents/skills/` for Antigravity), so the agent can load the new skill without any moving. Use a different location only if the user asks for one.

1. Create a `references/` subdirectory inside the new skill folder: `<skills folder>/<skill-name>/references/`.
2. Write the detailed chronological narratives as markdown files into the `references/` directory.
3. Write the main `SKILL.md` file at the root of the skill folder.

**CRITICAL: The main `SKILL.md` MUST include standard YAML frontmatter and act as an Executive Summary.**

Example template for the generated `SKILL.md`:
```markdown
---
name: <skill-name>
description: >-
  Context about the user's technical background, career history, and current goals. Read this when starting a new major task for this user.
---

# User Background Context

## Executive Profile
* **Background:** High-level summary of their years of experience and domain.
* **Current Goal:** What they are trying to achieve right now.
* **Engineering Philosophy:** How they approach problem solving (e.g., First-principles, AI Multiplier).

## Detailed References
For deep psychological context, chronological job history, and exact study roadmaps, refer to the following markdown files:
* **[Origin Story](./references/origin_story.md):** How the user entered the industry.
* **[Job Journey](./references/job_journey.md):** Chronological breakdown of their major roles and technical achievements.
* **[Current Roadmaps](./references/roadmaps.md):** Their active study plans or career transition strategies.
```

### 4. Confirmation Phase
Notify the user that the skill has been created successfully, and that it can be used in new conversations (some agents only load skills when a conversation starts). Explain how the multi-file architecture works (progressive disclosure: agents read the executive summary first, and click into the narrative references only when deep psychological or historical context is needed).
