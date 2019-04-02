# Name
fescar(Fast & Easy Commit And Rollback)

 ↓

seata (Simple Extensible Autonomous Transaction Architecture)

## 原理和设计

### 前提
- 基于支持本地ACID 事务的关系型数据库
- Java 应用，通过JDBC访问数据库

### 整体机制
- 一阶段：业务数据和回滚日志记录在一个本地事务中提交，释放本地锁和链接资源。
- 二阶段: 
  - 提交异步话(快速完成)
  - 回滚通过一阶段的回滚日志进行反向补偿

### 写隔离
- 一阶段本地事务提交前，需要确保先拿到全局锁
- 拿不到**全局锁**，不能提交本地事务
- 拿 **全局锁** 的尝试被限制在一定范围内，超出范围就放弃，并回滚本地事务，释放本地锁

### 读隔离
- 在数据库本地事务的隔离级别 读已提交(Read Committed) **RC**
- Fescar(AT 模式) 默认全局隔离级别是 读未提交(Read Uncommitted) **RU**
- 特定场景下，必须要求全局的 读已提交，Fescar的方式是通过 SELECT FOR UPDATE 语句进行代理
- SELECT FOR UPDATE 会申请全局锁(但是性能 比较糟糕)，仅仅针对 FOR UPDATE 的语句进行代理
![Seata Tx](seata_tx_at.png)


### MT(Manual Transcation)
- 根据两阶段行为模式不同，我们将分支事务划分为 Automatic Transaction  **AT** 和 **MT**

AT 模式 基于 支持本地ACID事务 的关系型数据库
MT 模式 不依赖底层数据资源的事务支持
自定义prepare/commit/rollback 行为