# Design Principles

## CAP

Consistency / Availability / Partition tolerance — pick two. P is mandatory → CP (ZooKeeper) or AP (Cassandra).

## BASE

Basically Available / Soft state / Eventually consistent. The AP practice of CAP.

## Consistency models

Strong / weak / eventual / causal / read-your-writes

## Partitioning + replication

Range / hash / consistent-hash partitioning. Sync / async / semi-sync replication. Replicas N=3 (quorum=2). Paxos/Raft for leader election.

## Failure responses

Network timeout → retry + timeout / node crash → failover / slow node → circuit break / data corruption → replicas + checksum

## Quick card

```
CAP pick two (P mandatory) / BASE eventual consistency
Eventual consistency = most common choice / 3 replicas / Raft is easiest to understand
Failures: retry / circuit break / degrade / failover
```
