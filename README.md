# AI Coding Skills

A collection of AI coding assistant skills and rules for use with Cursor IDE and other AI-powered development environments.

## Skills

### 1. RIPER-5

A strict behavioral protocol and workflow framework designed for advanced AI assistants. It constrains AI behavior through a mandatory, phased process with five modes:

- **RESEARCH** - Information gathering and deep understanding
- **INNOVATE** - Brainstorming potential approaches  
- **PLAN** - Creating exhaustive technical specifications
- **EXECUTE** - Implementing exactly what was planned
- **REVIEW** - Validating implementation against the plan

[View RIPER-5 Skill](./riper-5/SKILL.md)

### 2. Simple Execution

A lightweight rule for straightforward task execution. Use when tasks are simple, well-defined, and low-risk.

[View Simple Execution Skill](./simple-execution/SKILL.md)

### 3. Markdown Style

Google Markdown style guide principles for creating clean, readable, and maintainable documentation. Based on Google's official style guide.

[View Markdown Style Skill](./markdown-style/SKILL.md)

### 4. Compact

A context compression tool to solve LLM context window overload. It stops current tasks to review, prune, and summarize the session history into a high-density "State Snapshot" for seamless migration to a new chat.

[View Compact Skill](./compact/SKILL.md)

### 5. Wrap Up

A delivery management skill for the final phase of a session. It checks code hygiene (cleaning up print statements, TODOs), reminds about documentation updates, and generates standard Git commit messages.

[View Wrap Up Skill](./wrapup/SKILL.md)

## Usage

Copy the content of the desired skill into your AI assistant's system prompt or rules configuration.

For Cursor IDE:
1. Open Settings
2. Navigate to Rules
3. Paste the skill content into User Rules or Workspace Rules

## Credits

- RIPER-5 is based on [robotlovehuman's original work](https://forum.cursor.com/t/i-created-an-amazing-mode-called-riper-5-mode-fixes-claude-3-7-drastically/65516)

## License

MIT
