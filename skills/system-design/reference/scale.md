# Scalability

## Cache trio

- **Penetration**: querying non-existent data → bloom filter / cache null values
- **Avalanche**: mass key expiration at once → randomized TTL / multi-level cache
- **Stampede**: hot key expires suddenly → mutex lock / logical expiration

**Patterns**: Cache-Aside (most common) / Read-Through / Write-Through / Write-Behind

## Queues

Decoupling / peak shaving / async. Kafka (high throughput + Streams) / RabbitMQ (routing) / Redis Streams (lightweight)

**Watch**: idempotent consumption / ordering guarantees / retries + DLQ

## Databases

- Indexes: B+Tree / Hash / GIN / BRIN
- Optimization: slow queries / covering indexes / avoid SELECT * / batching
- Isolation: read committed / repeatable read (MySQL default) / serializable

## CDN

Static asset distribution. CloudFlare / Akamai / CloudFront

## Async

Sync → async: free threads / shave peaks / raise throughput. Message queues / callbacks / Futures / coroutines

## Monitoring

- Metrics: CPU/memory/QPS/latency/error rate
- Logs: structured
- Traces: distributed tracing
- Tools: Prometheus+Grafana / ELK / Jaeger

## Elasticity

Horizontal scaling (more machines) > vertical. Triggers: CPU/QPS/schedule/prediction. Watch startup latency + scale-in jitter

## Canary / A-B

Canary release (small % → monitor → full) / A-B (two versions + statistical significance)

## Degradation

Circuit-breaker degrade / rate-limit degrade / manual degrade. Sentinel / Hystrix / Resilience4j

## Quick card

```
Cache: penetration/avalanche/stampede / Queues: decouple/shave peaks/async
DB: indexes + slow queries + transactions / CDN: static assets / Async: free threads
Monitoring: metrics+logs+traces / Elasticity: horizontal + warmup / Canary + A/B
```
