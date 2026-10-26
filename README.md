# User Background Skill Builder

An agent skill that interviews you and turns your background into a new skill. When the generated skill is invoked, the conversation is more precise and tailored to you.

It works with any agent that reads `SKILL.md` skills, including Claude Code and Google Antigravity.

## Installation

1. Go to the skills folder of your agent:

   | Agent | Skills folder |
   | --- | --- |
   | Claude Code (all projects) | `~/.claude/skills` |
   | Claude Code (one project) | `<project>/.claude/skills` |
   | Antigravity (one project) | `<project>/.agents/skills` |
   | Antigravity (all projects) | `~/.gemini/antigravity/skills` (check your version's docs) |

   ```bash
   cd ~/.claude/skills
   ```

2. Clone this repository into a folder named `user-background-skill-builder`:

   ```bash
   git clone https://github.com/benkuotw/user-background-skill-builder.git
   ```

The new background skill is created next to `user-background-skill-builder`, in the same skills folder, so your agent picks it up without any moving.

## Usage

Ask your agent to build a skill based on your background:

> **/user-background-skill-builder** Build a skill based on my background and name it `my-name`
