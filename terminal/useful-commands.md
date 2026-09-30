# Useful commands for unix-based terminals

##### watch

Execute command every 5 seconds until `ctrl+c`
`watch -n 5 ls`

##### display open TCP ports (lsof)

`lsof -i -P | grep LISTEN | grep 63140`