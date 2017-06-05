# yarn

- 代替map reduce
1. map: 将文件切片 (就近分配）
2. combine: (map-side reduce) 得到一个比较小的输出结果，节约计算
3. shuffle: map 输出作为reduce的输入就是shuffle
4. reduce: 合并


# Shuffle:
- map 输出的时候不可能把所有文件都放到内存操作，就会spill到硬盘， 默认如果内存到80%就会spill
- 每个partition是reducer的输出

# 就近原则
- job tracker 装在 name node上
- task tracker 装在data node上

# Yarn
- 把jobTracker分成了Resource Manager 和 Application Manager
- name node上管理resource Manager, data node 上管理 application manager
- 用容器执行，管理task
- 


