# Architecture Patterns

## Microservices

Independent deployment / independent databases / API communication. For large teams and traffic; skip for small projects.

## Event-driven

Event produced → bus → consumers. Kafka/RabbitMQ/Redis Streams. Decoupling / async / replayability.

## CQRS

Write model (optimized for writes) + read model (optimized for reads), can use different stores. For skewed read/write ratios.

## Saga

Split large transactions into small ones + compensations. Choreography (no center) / Orchestration (central coordinator).

## Rate limiting

Token bucket / leaky bucket / sliding window / counter. Sentinel / Resilience4j / nginx limit_req.

## Circuit breaking

Closed → Open → Half-Open → Closed. Failure thresholds + degradation.

## Read-write splitting

Primary writes, replicas read; binlog/CDC sync. For read-heavy workloads. Latency issues → read from primary for strong consistency.

## Sharding

Single table > 100M rows / single DB QPS > 10,000. Vertical (by business) / horizontal (hash/range). ShardingSphere / Vitess / TiDB.

## Quick card

```
Microservices = big teams / Event-driven = decoupling / CQRS = read-write split
Saga = distributed transactions / Rate limit = token bucket / Circuit break = graceful failure
Read-write split = read-heavy / Sharding = 100M+ rows
```
