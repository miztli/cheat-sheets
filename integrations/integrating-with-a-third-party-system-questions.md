## Product and business scope

## Technical integration model

### API Style
- REST
- GraphQL
- Sync vs async

### Versioning
- How do you version APIs
- Deprecation policy

## Authentication and security
1. Authentication method
- API Keys
- Oauth2
- Mutual TLS
2. Key/Certificate management
- Rotation policy
- Separate keys per environment
3. PCI compliance
- Are we touching PCI data at any point?
4. IP whitelisting

## State machine

### Retries
- Who retries on failure - retry strategy
- Idempotency guarantees
  - We implement idempotency by:
    - Requiring an idempotency key: The client must send a unique key per logical operation.
    - Persisting the request outcome 
    - Returning the original response for retries 
    - Preventing concurrent execution

### Edge cases
- Double transaction prevention
- Network timeouts

## Error handling and observability
1. Error model
- Error codes vs messages?
- Machine-readable vs human-readable?
2. Common failure scenarios
3. Logs & tracing 
- Do you provide request IDs?
- Can we correlate logs across systems?

## Testing and environments
1. Environments available
- Sandbox / staging / production?
2. Test cards / test accounts
3. Failure simulation?
4. Rate limits
- Sandbox vs production limits? 

## Performance & SLAs
1. Latency expectations

| Percentile   | Use case                        |
| ------------ | ------------------------------- |
| P50 (median) | Typical performance             |
| P75 / P90    | General UX health               |
| **P95**      | Standard production metric      |
| **P99**      | Critical systems, microservices |
| P99.9        | High-scale / hyperscale systems |

2. Availability SLA 
- Uptime guarantees?
3. Throughput
- Max transactions per second? 

## Compliance & Legal
1. Regulatory coverage
2. Local regulations?
3. Data retention
4. Audit & reporting
- Transaction exports?
- Reconciliation reports?

## Support & Escalation

1. Support channels
- Slack / email / ticketing?
2. Incident response
- How are incidents communicated?
- Post-mortems shared?
3. On-call escalation
- Who do we call when payments are down?