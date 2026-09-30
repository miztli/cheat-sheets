# init the project
`/init`

Claude manages 3 memory files to keep the context of the project:
1. Project memory (versioned file checked in at ./CLAUDE.md)
2. Local memory (gitignored file at ./CLAUDE.local.md)
3. User memory (saved in ~./claude/CLAUDE.md)

### Add context to the prompt:
`@[path to file]prompt`

### Exit the current session
`/exit`

### Clear the entire session context and chat history
`/clear`

### Summary of the current chat and context to reduce all conversation and context and just keep meaningful details
`/compact`

### Resume a previous session
`/resume`

### Rename a session
`/rename`

### Planning
`shift + tab`
- Use it for task with wider scope

### Thinking
- Use the planning mode and use the word "Think" at the start of your prompt.
- If you need deeper analysis, use the word "Deep Think" or "Think more" at the start of your prompt.
- Use it for task with narrow scope but requires deep analysis. Each of the previous modes can consume many tokens, so use them wisely.

### IntelliJ integration
- /ide

### Model setup
- [model setup docs](https://code.claude.com/docs/en/model-config)
- During session - Use `/model <alias|name>` to switch models mid-session
- At startup - Launch with `claude --model <alias|name>`
- Environment variable 
  - Set `ANTHROPIC_MODEL=<alias|name>`
- Settings - Configure permanently in your settings file using the `model` field.
- How to apply models:
  - Sonnet: Handle most coding tasks.
  - Opus: Provides stronger reasoning for complex architectural decisions
  
### Extending the code capabilities

Extending the base capabilities: The built-in tools are the foundation. You can extend what Claude knows and add an extra layer of extensions on top of the core agentic loop with:

    - Skills: For workflows.
    - MCP: Connect to external services.
    - Hooks: Automate workflows with hooks.
    - Subagents: Agents to delegate tasks.
    - Claude in chrome for web interaction.