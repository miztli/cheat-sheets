# Dynatrace

Grail: Data lake + Data Warehouse (Is the core of how dynatrace stores data).
- Here, we find the next data sources: logs, traces, entities, events and metrics.
- Designed specially for observability

DQL (Dynatrace Query Language): Is the way in which we access observability data in dynatrace.

##### Recommended command order
`fetch -> filter -> select fields -> process data -> summarize -> static commands / continue filtering -> sort -> limit`

### Logs

##### filtering and sorting

```
fetch logs
| filter
    matchesValue(k8s.container.name, "v1-client-dxl-graphql") AND
    matchesValue(loglevel, "ERROR")
| sort timestamp desc, k8s.pod.name asc
```

##### Setting data limits
_scanLimitGBytes_

`scanLimitGBytes` - The default value is 500GB unless specified otherwise.
`scanLimitGBytes -1` - If set to -1, all data available in the query time range is analyzed.
`scanLimitGBytes -500` - Analyze only 500GB of data

```
fetch logs, scanLimitGBytes -1
```

_limit_

```
fetch logs
| filter
    matchesValue(k8s.container.name, "v1-client-dxl-graphql") AND
    matchesValue(loglevel, "ERROR")
| sort timestamp asc    
| limit 20   
```

##### search
What makes it different from filter is that it can look through all fields or specific ones
```
fetch logs
| search content ~ "Error"
```

##### Expand

##### Dedup

##### summarize
```
fetch logs
| filter
    matchesValue(k8s.container.name, "v1-client-dxl-graphql") AND
    matchesValue(loglevel, "ERROR")
| summarize count(), by:{k8s.node.name}
```

#### Parsing with DPL

### Merging data
Data sources: logs, traces, entities, events and metrics.

##### lookup data
- [How lookup data in Grail works](dynatrace-knowdlege.md)
- [reference docs](https://docs.dynatrace.com/docs/platform/grail/dynatrace-query-language/commands/correlation-and-join-commands#lookup)

Adds fields from a subquery to the source table by finding a match between a field in the source table and the lookup table. Only keeps the first match it finds.

##### join data
Combine multiple records: inner (default join), left join, outer join

### Time Series
In DT metrics are time series data. It's a series of data measured across time.

```
timeseries avg(dt.process.cpu.usage), by:{dt.entity.process_group}
| filter dt.entity.process_group=="PROCESS_GROUP-00DEA159DFA4D9B3"
```
or
```
timeseries avg(dt.process.cpu.usage), by:{dt.entity.process_group}, filter: dt.entity.process_group == "PROCESS_GROUP-00DEA159DFA4D9B3"
```

### Distributed Tracing

### Real User Monitoring (RUM)
- Experience Vitals: It monitors frontend health, performance, error rates, and key business metrics so teams can take action with clarity and speed.
- Error inspector: Helps you discover, prioritize, investigate, and resolve issues directly within your workflow.
- User & sessions: Uncover friction points in the digital experience. Gain insights into user behavior and experience patterns.
- Dashboards
- Notebooks: Detailed investigations and collaborations

### App Function Logs

### Anomaly detection and security monitoring with DQL

### SLO - Service-Level Objectives APP
By applying anomaly detection directly to your DQL-based metrics, you can define thresholds, customize sensitivity, and integrate with alerting profiles to trigger notifications through your preferred channels, like email, Slack, or ServiceNow.

### Anomaly Detector APP

### Distributed tracing

### Dashboards
### Profiling and optimizations
### Services
- Data is collected through OneAgent or Open Telemetry
- Exposes an interface to drill into your service and monitor: performance, health, failures and response time
- Allows observability on:
  - endpoints
  - db queries
  - outbound calls
  - messages (async flows)
  - time-based comparisons
    - response time
### Multidimensional analysis
Investigate custom views: top web requests, db statements, exception analysis
### Notebooks
### Kubernetes