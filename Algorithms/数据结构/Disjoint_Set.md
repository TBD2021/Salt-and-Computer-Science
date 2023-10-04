# 并查集（Disjoint Set/Union-find Forest）

- 基础概念
  - 并查集的定义

## 基础概念

### 并查集的定义

Disjoint set is a data structure defined as one that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It provides near-constant-time operations to add new sets, to merge existing sets, and to determine whether elements are in the same set:

- 新建子集(Add new sets)
- 合并(Union)：将两个子集合并为一个子集。
- 查询(Find)：查询某元素所属子集的代表元素。这也可以用来判断两个元素是否属于同一个子集。

### 并查集的表示与底层实现

