# KT

### Concepts

`Ramp-up period time: ` The ramp-up period in JMeter is the time it takes to start all the virtual users (threads) specified in a Thread Group. It prevents the system from being overwhelmed by an instant, unnatural spike in traffic. The delay between starting each successive thread is calculated using the formula: Delay = Ramp-up Period / Number of Threads

`Latency: ` The amount of time it takes to the request from client to server and back again (point A to B). It doesn't include processing time once the request reaches the server.
`Response time: ` The overall amount it takes the request to complete. Including latency and server processing time.