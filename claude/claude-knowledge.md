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
