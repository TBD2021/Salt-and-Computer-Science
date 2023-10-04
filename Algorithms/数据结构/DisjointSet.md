# 并查集（Disjoint Set/Union-find Forest）

- 基础概念
  - 并查集的定义

## 基础概念

### 并查集的定义

In mathematics, two sets are called disjoint sets if they have no element in common, the intersection of sets is a null set.

In computer science, a disjoint set data structure is defined as one that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It provides near-constant-time operations to add new sets, to merge existing sets, and to determine whether elements are in the same set:

- 新建子集(Add new sets)
- 合并(Union)：将两个子集合并为一个子集。
- 查询(Find)：查询某元素所属子集的代表元素。这也可以用来判断两个元素是否属于同一个子集。

```
并查集的核心思想在于，用集合中的一个元素来代表这个集合。
```

### 并查集的表示与底层实现

- **树型实现**

并查集最常用的表示方式是森林，其中的每棵树表示一个集合，树中的节点表示对应集合中的元素，而树的根节点则是对应集合的代表元素。

用树来实现并查集，最基本的部件是节点和指向其父节点的指针，可以用一个数组parent[]实现，其中parent\[i\]是节点i的父节点，如果节点i是树的根节点，那么它的父节点设为它自身。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSet2.png" width=300px>

由此可以写出最简单的并查集代码：

```Java
public class DisjointSet{
  int[] parent=new int[num];
  public void makeSet(int i){ }
  public int find(int i){ }
  public void union(int i, int j){ }
}
```

1. **MakeSet(i)**: Create a set contain only one i.

初始化时，将元素的父节点设为它自身。

```Java
public void makeSet(int i) {
  parent[i]=i;
}
```

2. **Find(i)**: Finding i in a set, return root index.

```Java
public int find(int i) {
  if(parent[i]==i)
    return i;
  else
    return find(parent[i]); 
}
```

3. **Union(i,j)**: Finding i in a set, return root index.

合并操作，就是先找到两个集合的代表元素，然后将前者的父节点设为后者。(当然也可以将后者的父节点设为前者。)

```Java
public void union(int i, int j) {
  parent[i]=find(j);
}
```
