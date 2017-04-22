# hdfs是最基础的组件

- hbase
- yarn/mr
- hive 可以独立工作于hdfs,或者之于yarn 或者 hbase之上。
- spark 工作于hdfs, yarn, hbase, hive之上

# 为什么需要新的文件系统
- 久的文件系统无法支持TB级别的大文件
- 是一个逻辑文件系统，是建立在物理文件系统上的，
- 允许在逻辑上将多个物理文件合并成超大文件
- 尽可能利用廉价资源， 将硬件失效当作常态来考虑。
- hdfs倾向于优化读取的文件系统，
- 基于块状存储 和流式存储
- 大的block size 便于流式存储，也便于存储更大的文件metadata

# 如何支持高效率访问 
- 采用Raid0, HDFS自带备份, 完全同步读写，所以性能提升和服务器数量提升是线性关系
- 厚置备模式, thick
- hdfs三个拷贝同时写入，（一读三写，三写一读）
- 本地缓存（先写入本地缓存，达到一定大小后才会被写入data node)

# hdfs核心组件

## name node
- 本身就是一个数据库(fsimage)
- edits 存储日志
- 控制对data node的访问
- posix 文件风格
- Federation 模式

## data node
- 实现hdfs文件系统
- 存储数据

## name node HA
- 至少一台standby name node (由zookeeper决定）
- 三台以上的journalNode提供edit log （由zookeeper调度）

## data node HA
- 邻近访问 rack awareness（位置感知）：一般来说两份拷贝在同一台机器上实现快速访问，第三份拷贝放在另一台机上预防第一台机器出问题
- 



















