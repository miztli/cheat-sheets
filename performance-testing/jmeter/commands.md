# Useful commands

### Help
`./jmeter -h`

### Controllers

- `Samplers:` Tell JMeter to send request to a server and wait for the response. Ex: FTP Request, HTTP Request, JDBC Request, etc. 
- `Logical:` Let you customize the logic JMeter uses to decide when to send requests. Ex: Once Only Controller, Interleave Controller, Loop Controller, Throughput Controller, Runtime Controller, Module Controller, etc.

### Timers
A timer will tell JMeter to delay a certain amount of time before each sampler which is in it's scope.

### Listeners
They provide means to view, save and read the test results. By default, these results will be stored in .jtl file but they can also be saved in CSV, though less details will be provided. Ex: Summary Report, View Results Tree, Aggregate Report, etc.

### Recording
- HTTP(S) Test Script Recorder: Allows JMeter to intercept and record your actions while you navigate your web application with your browser.

### Run in terminal
`./jmeter -n -t ~/Documents/ulta/performance-tests/file.jmx -l ~/Documents/performance-tests/tests_27_mar/results.csv`

`-n` non-gui mode
`-l` location and name of generated results file (csv / jtl)
`-t` test file (.jmx generated in UI mode)
`-j` log file dir and name
