# 并查集（Disjoint Set/Union-find Forest）

- 基础概念
  - 并查集的定义

## 基础概念

### 并查集的定义

In mathematics, two sets are called disjoint sets if they have no element in common, the intersection of sets is a null set.

In computer science, a disjoint set data structure is defined as one that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. 

并查集的核心思想在于，用集合中的一个元素来代表这个集合。It provides near-constant-time operations to add new sets, to merge existing sets, and to determine whether elements are in the same set:

- 新建子集(Add new sets)
- 合并(Union)：将两个子集合并为一个子集。
- 查询(Find)：查询某元素所属子集的代表元素。这也可以用来判断两个元素是否属于同一个子集。

### 并查集的表示与底层实现

- **树型实现**

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSet1.png" width=600px>

并查集最常用的表示方式是森林，其中的每棵树表示一个集合，树中的节点表示对应集合中的元素，而树的根节点则是对应集合的代表元素。

