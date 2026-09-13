<!-- 隐式触发：CAP/BASE/一致性/分区/复制/分布式理论/共识算法 -->
# 设计原则（精简版）

## CAP

一致性/可用性/分区容错三选二。P 必选 → CP（ZooKeeper）或 AP（Cassandra）。

## BASE

Basically Available / Soft state / Eventually consistent。CAP 的 AP 实践。

## 一致性模型

强一致 / 弱一致 / 最终一致 / 因果一致 / 读己之写

## 分区+复制

范围/哈希/一致性哈希分区。同步/异步/半同步复制。副本 N=3（quorum=2）。Paxos/Raft 选主。

## 失败应对

网络超时→重试+超时 / 节点崩溃→failover / 慢节点→熔断 / 数据损坏→副本+checksum

## 速查卡

```
CAP 二选一（P必选）/ BASE 最终一致
最终一致=大多数选择 / 副本3 / Raft 易理解
失败：重试/熔断/降级/failover
```