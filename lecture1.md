# Serve Type
- 通过总统选举，为整个集群选择leader，保证读写唯一性
- 为zookeeper管理的集群，通过znode, 选择master
- 一般存储集群共享的配置信息：比如微服务的地址

- leader: 集群领导， 对znode进行写操作
- follower: 


# Server Status

- 启动时，处于looking
- 首先， 看有没有leader，然后进入


# zookeeper 端口
- 2888: 用来看leader是否活着
- 3888: 用来询问leader
- :用来连接client


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

# znode
- 信息节点, 类文件系统
- 可设置为 Ephemeral：如果和客户端和zookeeper市区连接，znode会被删除
- 

# master and slave
- sequentail znode是递增的
- sequential znode的另一个显著用途是选择master
- 选择最小znode的作为master














- 
