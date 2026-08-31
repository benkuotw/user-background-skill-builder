---
name: user-background-skill-builder
description: >-
  Use this skill when the user wants to create or update a profile of their technical background, preferences, or workflows to give the agent better context.
---

# User Background Skill Builder

This skill helps you (the agent) interview the user to extract their technical background and preferences, and then automatically generate a dedicated "user background" skill based on those answers.

## Workflow

When the user triggers this skill, follow these steps in order:

### 1. Interview Phase
Do not try to guess the user's preferences. Start a conversation and ask them open-ended questions to gather their context. You can ask them all at once or one by one. Good areas to probe:
*   **Tech Stack:** What are their primary programming languages and frameworks?
*   **Experience & Tone:** What is their seniority level? Do they prefer deep technical explanations, or concise code snippets?
*   **Architecture & Design:** Do they have strong preferences for specific design patterns (e.g., functional vs OOP, microservices vs monoliths)?
*   **Workflows:** What are their testing, documentation, and formatting standards?

### 2. Synthesis Phase
Once the user has provided enough information (or says they are done), organize their answers into a well-structured document. Group related concepts logically (e.g., "Communication Preferences", "Coding Standards", "Architecture").

### 3. Generation Phase
Use your file-writing tools to create the new skill in the workspace.
1. Determine a name for the new skill (e.g., `user-profile`, `dev-background`, or ask the user).
2. Write the synthesized profile to `.agents/skills/<skill-name>/SKILL.md`.

**CRITICAL: The generated `SKILL.md` MUST include standard YAML frontmatter.**
Example template for the generated file:
```markdown
---
name: <skill-name>
description: >-
  Context about the user's technical background, preferred frameworks, coding standards, and communication style. Read this when starting a new major task for this user.
---

# User Background Context
[Insert synthesized content here]
```

### 4. Confirmation Phase
Notify the user that the skill has been created successfully. Explain that because it is an agent skill, it will use "progressive disclosure" (the agent will see the description, and read the full details on-demand when it thinks it needs it).
