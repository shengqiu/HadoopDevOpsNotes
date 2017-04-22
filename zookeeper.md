#zookeeper是一个分布式协调服务，主要用来处理分布式系统中各系统之间的协作问题的。
- 主要体现在仲裁，选取master
- 同步配置文件


# Serve Type
- 通过总统选举，为整个集群选择leader，保证读写唯一性
- 为zookeeper管理的集群，通过znode, 选择master
- 一般存储集群共享的配置信息：比如微服务的地址
- 只有leader可以写，正如数据库，原子操作，这样只有一个线程访问数据

- leader: 集群领导， 对znode进行写操作
- follower: 


# Server Status

- 启动时，处于looking
- 首先， 看有没有leader，然后进入


# zookeeper 端口
- 2888: 用来看leader是否活着
- 3888: 用来询问leader
- 2181:用来连接client


# leader election
1. 启动: 进入looking
2. 询问: 其他的服务器3888端口
3. 如果有leader，变成follower
4. 如果没有，选transaction_ID最大的

# NTP服务
- 每个机器启动都会有网络授时服务
- 或使用全球服务器授时，或者企业内部授时
- 

# Brain split and quorum
- quorum: 集群的主机数量, zookeeper数量一半是基数
- brain split 发生在集群分开的情况

# data model: znode
- 信息节点, 类文件系统
- znode可设置为 Ephemeral：也就是临时节点，它是session有效的，当session结束之后，这个node自动删除，所以我们可以用这种node来实现对服务的监控。譬如一个服务启动之后就向zk挂载一个ephemeral node，如果这个服务崩溃了，那么连接断开，session无效了，这个node就删除了，我们也就知道该服务出了问题
- znode 还有一种Sequence Node，用来实现序列化的唯一节点，我们可以通过这个功能来实现一个简单地leader服务选举，譬如每个服务启动的时候都向zk注册一个sequence node，谁最先注册，zk给的sequence最小，这个最小的就是leader了，如果leader当掉了，那么具有第二小sequence node的节点就成为新的leader。
- 另一种是persistense

# master and slave
- sequentail znode是递增的
- sequential znode的另一个显著用途是选择master
- 选择最小znode的作为master




# 如何部署：
- 设置 binary位置
- 设置 数据位置
- 设置 quorum
- 设置 log位置, 在bin event下面
- 机器号 在data/myid里
- getAcl 看权限
- java.env 里要打开kerbros， 要配置好指向jaas.conf
- 在java.env 里可以关闭Acl，用skipAcl
- jaas.conf 用来配置kerbros的信息











- 
