<!-- 隐式触发：缓存/队列/数据库/CDN/监控/性能优化/扩展/高并发 -->
# 可扩展性（精简版）

## 缓存三剑客

- **穿透**：查不存在数据→布隆过滤器/缓存空值
- **雪崩**：大量 key 同时过期→随机过期/多级缓存
- **击穿**：热门 key 过期瞬间→互斥锁/逻辑过期

**模式**：Cache-Aside（最常用）/ Read-Through / Write-Through / Write-Behind

## 队列

解耦/削峰/异步。Kafka（高吞吐+Stream）/ RabbitMQ（路由）/ Redis Streams（轻量）

**注意**：幂等消费 / 顺序保证 / 失败重试+DLQ

## 数据库

- 索引：B+Tree / Hash / GIN / BRIN
- 优化：慢查 / 索引覆盖 / 避免 SELECT * / 批量
- 事务隔离：读已提交 / 可重复读（MySQL 默认）/ 串行化

## CDN

静态资源分发。CloudFlare / Akamai / 阿里云/腾讯云

## 异步

同步→异步：释放线程/削峰/提升吞吐。消息队列/回调/Future/协程

## 监控

- Metrics（指标）：CPU/内存/QPS/延迟/错误率
- Logs（日志）：结构化
- Traces（链路）：分布式追踪
- 工具：Prometheus+Grafana / ELK / Jaeger

## 弹性

水平扩展（加机器）> 垂直扩展。触发：CPU/QPS/定时/预测。注意启动延迟+缩容抖动

## 灰度/A/B

金丝雀发布（小比例试用→监控→全量）/ A/B（两版本对比+统计显著性）

## 降级/兜底

熔断降级 / 限流降级 / 手动降级。Sentinel / Hystrix / Resilience4j

## 速查卡

```
缓存：防穿透/雪崩/击穿 / 队列：解耦/削峰/异步
数据库：索引+慢查+事务 / CDN：静态资源 / 异步：释放线程
监控：Metrics+Logs+Traces / 弹性：水平扩展+预热 / 灰度：金丝雀+A/B
```