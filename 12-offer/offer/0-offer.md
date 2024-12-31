# offer
> 记录和整理涉及的问答知识点，包含：技术问题，项目问题，细节点问题，业务问题，发展规划问题等。

- [1-java](./1-java.md)




> 未分类

- 问：分布式锁介绍一下，常用的分布式锁有什么？
  - 答：
- 问：red-lock了解吗？它的原理是什么？
  - 答：

> 2024-10-25
- 问：实时数仓与离线数仓发生不一致的情况，你们如何处理？
  - 答：实时和离线本身技术架构是不一致的，实时特点是快速响应，发生差异原因主要是：数据延迟，数据丢失，性能问题。
  - 离线数仓的特点是可追溯，数据质量高，数据有延迟。离线数仓在计算时有足够的时间校验数据的完整性，以及对数据进行清洗加工。
  - 所以，离线更准确更稳定，实时更加敏捷稳定性差。
> 2024-10-27
- 问：流量暴涨你如何处理？
  - 答：
- 问：模型平台的建设，你如何建设？
  - 答：
> 2024-10-29
- 问：你们项目中选择使用grovvy，为什么没有使用aviator？
  - 答：1，aviator是轻量级、高性能的java语言实现的表达式引擎。
  - 2，grovvy是一个完整的动态编程语言，也是基于java平台的。
  - 3，区别：grovvy可以处理复杂的逻辑，aviator专注与简单的表达式；我们项目中针对标准变量的加工，会有复杂的逻辑和代码处理过程，所以选型为grovvy。
> 2024-10-31
- 问：外数响应慢，同步改异步，接口响应如何做？
  - 答：首先同步改为异步，发起端不再等返回，最好是在核心最开始近件儿时就能发起对外数请求，然后外数平台进行数据请求拿到结果后推kafka，实时加工处理后，推给风控决策系统使用。


1、HashMap 和 Hashtable 区别 
2、Java 垃圾回收机制和生命周期 
3、怎么解决 Kafka 数据丢失的问题 
4、zookeeper 是如何保证数据一致性的 
5、hadoop 和 spark 在处理数据时，处理出现内存溢出的方法有哪些？
6、java 实现快速排序 
7、设计微信群发红包数据库表结构（包含表名称、字段名称、类型） 
8、如何选型：业务场景、性能要求、维护和扩展性、成本、开源活跃度 
9、Spark如何调优 
10、Flink和spark的通信框架有什么异同 
11、Java的代理 
12、Java的内存溢出和内存泄漏 
13、hadoop 的组件有哪些？Yarn的调度器有哪些？
14、hadoop 的 shuffle 过程 
15、简述Spark集群运行的几种模式 
16、RDD 中的 reducebyKey 与 groupByKey 哪个性能高？
17、简述 HBase 的读写过程 
18、在 2.5亿个整数中，找出不重复的整数，注意：内存不足以容纳 2.5亿个整数。
19、CDH 和 HDP 的区别 
20、Java原子操作 
21、Java封装、继承和多态 
22、JVM 模型 
23、Flume taildirSorce 重复读取数据解决方法 
24、Flume 如何保证数据不丢 
25、Java 类加载过程 
26、Spark Task 运行原理 
27、手写一个线程安全的单例 
28、设计模式 
29、impala 和 kudu 的适用场景，读写性能如何 
30、Kafka ack原理 
31、phoenix 创建索引的方式及区别 
32、Flink TaskManager 和 Job Manager 通信 
33、Flink 双流 join方式 
34、Flink state 管理和 checkpoint 的流程 
35、Flink 分层架构 
36、Flink 窗口 
37、Flink watermark 如何处理乱序数据 
38、Flink time 
39、Flink支持exactly-once 的 sink 和 source 
40、Flink 提交作业的流程 
41、Flink connect 和 join 区别 
42、重启 task 的策略 
43、hive 的锁 
44、hive sql 优化方式 
45、hadoop shuffle 过程和架构 
46、如何优化 shuffle过程 
47、冒泡排序和快速排序 
48、讲讲Spark的stage 
49、spark mkrdd和Parrallilaze函数区别 
50、Spark checkpoint 过程 
51、二次排序 
52、如何注册 hive udf 
53、SQL去重方法 
54、Hive分析和窗口函数 
55、Hadoop 容错，一个节点挂掉然后又上线 
56、掌握 JVM 原理 
57、Java 并发原理 
58、多线程的实现方法 
59、RocksDBStatebackend实现（源码级别） 
60、HashMap、ConcurrentMap和 Hashtable 区别 
61、Flink Checkpoint 是怎么做的，作用到算子还是chain 
62、Checkpoint失败了的监控 
63、String、StringBuffer和 StringBuilder的区别 
64、Kafka存储流程，为什么高吞吐？
65、Spark优化方法举例 
66、keyby的最大并行度 
67、Flink 优化方法 
68、Kafka ISR 机制 
69、Kafka partition的4个状态 
70、Kafka 副本的7个状态 
71、Flink taskmanager的数量 
72、if 和 switch 的性能及 switch 支持的参数 
73、kafka 零拷贝 
74、hadoop 节点容错机制 
75、HDFS 的副本分布策略 
76、Hadoop面试题汇总，大概都在这里(https://www.cnblogs.com/gala1021/p/8552850.html) 
77、Kudu 和Impala 权限控制 
78、Time_wait状态？当server处理完client的请求后立刻closesocket此时会出现time_wait状态
79、三次握手交换了什么？(SYN,ACK,SEQ,窗口大小) 3次握手建立链接，4次握手断开链接。
80、hashmap 1.7和1.8 的区别 
81、concurrenthashmap 1.7和1.8？
82、Kafka 的ack 
83、sql 去重方法(group by 、distinct、窗口函数) 
84、哪些 Hive sql 不能在 Spark sql 上运行，看这里：https://spark.apache.org/docs/2.2.0/sql-programming-guide.html#unsupported-hive-functionality 
85、什么情况下发生死锁 
86、事务隔离级别？可重复读、不可重复读、读未提交、串行化 
87、Spark shuffle 和 Hadoop shuffle的异同 
88、Spark静态内存和动态内存 
89、mysql btree 和 hash tree 的区别。btree 需要唯一主键，hash tree 适合>= 等，精确匹配，不适合范围检索 
90、udf、udtf和 udaf 的区别 
91、hive sql 的执行过程 
92、spark sql 的执行过程 
93、找出数组中最长的top10字符串 
94、Flink 数据处理流程 
95、Flink 与 Spark streaming 对比 
96、Flink watermark 使用 
97、窗口与流的结合 
98、Flink 实时告警设计 
99、Java：面向对象、容器、多线程、单例 
100、Flink：部署、API、状态、checkpoint、savepoint、watermark、重启策略、datastream 算子和优化、job和task状态 
101、Spark：原理、部署、优化 
102、Kafka：读写原理、使用、优化 
103、hive的外部表 
104、spark的函数式编程 
105、线性数据结构和数据结构 
106、Spark映射，RDD
107、java的内存溢出和内存泄漏
108、多线程的实现方法 
109、HashMap、ConcurrentMap和 Hashtable 区别 
110、Flink Checkpoint 是怎么做的，作用到算子还是chain 
111、Checkpoint失败了的监控 
112、String、StringBuffer和 StringBuilder的区别 
113、Kafka存储流程，为什么高吞吐 
114、Spark 优化方法举例 
115、keyby 的最大并行度 
116、Flink 优化方法 
117、Kafka ISR 机制 
118、kafka partition 的状态 
119、kafka 副本的状态 
120、taskmanager 的数量 
121、if 和switch的性能区别
122、Hdfs读写流程（结合cap理论讲） 
123、技术选型原则 
124、Kafka组件介绍 
125、g1和cms的区别 
126、讲讲最熟悉的数据结构 
127、spark oom处理方法 
128、看了哪些源码 
129、Spark task原理 
130、解决过的最有挑战的问题 
131、Hbase读写流程