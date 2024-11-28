# leetcode
> 算法知识

- 问： 介绍一下布隆过滤器，手动实现一个布隆过滤器伪代码？
  - 布隆过滤器是为了解决海量数据的存在性问题。适用于海量数据去重，解决缓存穿透这些场景。
  - 原理是算hash值，数据量太大的情况下，单个hash很容易重复，所以算一组hash，只有一组hash全命中才认为存在，否则不存在，但是还会有一组hash全重复的情况，所以有小概率不准确的情况。
  - https://javaguide.cn/cs-basics/data-structure/bloom-filter.html
