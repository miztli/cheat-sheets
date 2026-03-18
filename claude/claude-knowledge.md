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

### Planning
`shift + tab`
- Use it for task with wider scope

### Thinking
- Use the planning mode and use the word "Think" at the start of your prompt.
- If you need deeper analysis, use the word "Deep Think" or "Think more" at the start of your prompt.
- Use it for task with narrow scope but requires deep analysis. Each of the previous modes can consume many tokens, so use them wisely.

### IntelliJ integration
- /ide