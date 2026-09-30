# TMUX

### Panes

##### Split into panes

Vertically
`ctrl+b` + `%`

Horizontally
`ctrl+b` + `"`

##### Move between panes

`ctrl+b` + `arrow` 

### Sessions

##### Create new window in session

`ctrl+b` + `c`

Navigate between windows

`ctrl+b` + `[index]` 

##### List available sessions

`tmux ls`

##### Rename session
`tmux rename [session-name]`

##### Detach session
`ctrl+b` + `d`

##### Attach session
`tmux attach -t [session-name]`

##### Delete session
`tmux kill-session -t [session-name]`
