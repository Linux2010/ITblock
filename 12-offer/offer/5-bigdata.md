# bigdata
> 大数据

- 问：介绍下RDD？
  - spark的基础的数据抽象，特点是只读，分布存储，可并行操作。
  - 容错性高：rdd有依赖性，可以通过血缘关系，从新计算丢失的分区数据，不必全部重算。
  - 位置优先原则：移动数据不如移动计算。spark调度任务尽可能江计算任务分配到数据存储位置。
- 问：说几个常用的算子，哪些操作会shuffle？
  - map，filter
  - 引起shuffle的操作：groupByKey，reduceByKey，repartition，join，cogroup
- 问：宽窄依赖介绍一下？
  - 窄依赖，父RDD被一个子RDD依赖，算子比如：map，filter
  - 宽依赖，父RDD被多个子RDD依赖，算子比如：groupByKey，reduceByKey