<!-- 隐式触发：微服务/事件驱动/CQRS/Saga/限流/架构模式/服务拆分 -->
# 架构模式（精简版）

## 微服务

独立部署/独立数据库/API 通信。大团队大流量用，小项目别用。

## 事件驱动

事件产生→总线→消费者。Kafka/RabbitMQ/Redis Streams。解耦/异步/可重放。

## CQRS

写模型（优化写入）+ 读模型（优化读取），可不同存储。读写比例悬殊用。

## Saga

大事务拆小事务+补偿。Choreography（无中心）/ Orchestration（中央协调器）。

## 限流

令牌桶/漏桶/滑动窗口/计数器。Sentinel/Resilience4j/nginx limit_req。

## 熔断

Closed→Open→Half-Open→Closed。失败阈值+降级。

## 读写分离

主写从读，binlog/CDC 同步。读多写少用。延迟问题→强一致读主库。

## 分库分表

单表>1亿/单库QPS>10000。垂直（按业务）/水平（hash/range）。ShardingSphere/Vitess/TiDB。

## 速查卡

```
微服务=大团队 / 事件驱动=解耦 / CQRS=读写分离
Saga=分布式事务 / 限流=令牌桶 / 熔断=失败降级
读写分离=读多写少 / 分库分表=单表过亿
```