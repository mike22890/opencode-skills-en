---
name: system-design
description: Use for system design/architecture/microservices/databases/caching/distributed systems/CAP/high concurrency/DevOps.
version: 1.0.0
metadata:
  author: mike22890
  tags: system-design architecture microservices distributed devops sre scalability
---

# System Design

## When to trigger

Trigger keywords: system design, architecture, microservices, database, cache, queue, load balancing, distributed, high concurrency, high availability, DevOps, SRE, observability, monitoring, deployment, K8s, containers, scaling, consistency, CAP, BASE.

## 6 rules

1. **CAP**: consistency / availability / partition tolerance — pick two
2. **Horizontal scaling**: more machines beat bigger machines
3. **Async over sync**: decouple with queues
4. **Idempotency**: retryable = safe
5. **Observability**: logs + metrics + traces
6. **Degrade & circuit-break**: fail gracefully

## Self-check

- [ ] Partition tolerance considered?
- [ ] Critical paths decoupled asynchronously?
- [ ] Caching + protection against penetration / avalanche / stampede?
- [ ] Idempotent and retryable?
- [ ] Observability (logs / metrics / traces)?
- [ ] Degradation / circuit-breaking plan?
- [ ] 10x / 100x traffic considered?

## Loading references

| User says | Load |
|---|---|
| CAP / BASE / consistency / partitioning / replication | `reference/principles.md` |
| Microservices / event-driven / CQRS / Saga / rate limiting | `reference/patterns.md` |
| Cache / queues / databases / CDN / monitoring | `reference/scale.md` |
| Masters / anchors to learn | `reference/masters.md` |
