# 并查集（Disjoint Set/Union-find Forest）

- 基础概念
  - 并查集的定义
- 并查集的表示与底层实现
  - 树型并查集
    - 结构
    - 操作
  - 优化：按秩/大小合并和路径压缩（Path Compression）
    - 按大小合并（Union by Size）
    - 按秩合并（Union by Rank）
    - 路径压缩（Path Compression）
  
## 基础概念

### 并查集的定义

In mathematics, two sets are called disjoint sets if they have no element in common, the intersection of sets is a null set.

In computer science, a disjoint set data structure is defined as one that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It provides near-constant-time operations to add new sets, to merge existing sets, and to determine whether elements are in the same set:

- 新建子集(MakeSet): Add a new element into a new set containing only the new element.
- 合并(Union)：将两个子集合并为一个子集。
- 查询(Find)：查询某元素所属子集的代表元素。这也可以用来判断两个元素是否属于同一个子集。

```
并查集是Union-Find Set的直译。它的核心思想在于，用集合中的一个元素来代表这个集合。
```

## 并查集的表示与底层实现

### 树型并查集（Tree Based Disjoint Set）

- **结构**

并查集最常用的表示方式是森林，其中的每棵树表示一个集合，树中的节点表示对应集合中的元素，而树的根节点则是对应集合的代表元素。

用树来实现并查集，最基本的部件是节点和指向其父节点的指针，可以用一个数组parent[]实现，其中parent\[i\]是节点i的父节点，如果节点i是树的根节点，那么它的父节点设为它自身。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSet1.svg" width=400px>

- **操作**

1. **MakeSet(i)**: Create a set contain only one i.
   
   初始化时，将元素的父节点设为它自身。

2. **Find(i)**: Finding i in a set, return its representatives.

   返回代表元素也就是返回树的根节点。

3. **Union(i,j)**: Merge two sets containing i and j.

   合并操作，就是先找到两个集合的代表元素，然后将前者的父节点设为后者。(当然也可以将后者的父节点设为前者。)

Time Complexity:

|Operation|Tree Based Disjoint Set|
|---|---|
|Union( )|O(1)|
|Find( )|O(depth)|
   
由此可以写出最简单的并查集代码：

```Java
// Tree Based Disjoint Set
public class DisjointSet{
  int[] parent=new int[num];
  public void makeSet(int i){
    parent[i]=i;
  }
  public int find(int i){
    if(parent[i]==i)
      return i;
    else
      return find(parent[i]); 
  }
  public void union(int i, int j){
    parent[i]=find(j);
  }
}
```

### 优化：按秩/大小合并（Union by Rank/Size）和路径压缩（Path Compression）

并查集的查询效率严重依赖于树的高度，worst case，查询操作的时间复杂度可以恶化到O(N)。

并查集的两种优化手段，按秩合并（Union by rank）和按大小合并（Union by size），都是通过在合并操作中控制树的高度，实现在合并操作的时间复杂度维持在O(1)的同时，将查询操作的时间复杂度优化到O(logN)。它们除了记录每个节点的父节点指针，还记录了节点的其他信息，用于在合并操作中决定哪个集合的根节点成为合并后集合的根节点，从而避免树的高度过高。

- **按大小合并（Union by size）**

在按大小合并的算法中，除了用数组parent[ ]来记录每个节点的父节点指针，还用数组size[ ]来记录每个节点所在的树的大小（也就是每个元素所在集合的元素数量）。当合并两个集合时，如果两棵树大小不同，将size较小的树连接到size较大的树的根节点下面；如果两棵树大小相同，则无所谓两棵树的连接方式。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSetUnionBySize1.png" width=800px>

Time complexity: 

O(logN) without Path Compression.

- **按秩合并（Union by rank）**

在按秩合并的算法中，除了用数组parent[ ]来记录每个节点的父节点指针，还用数组rank[ ]来记录每个节点的秩（节点的秩指的是该节点到它最远的后代叶子节点的距离）。初始化时，每个节点的秩设为0。当合并两个集合时，如果两棵树的秩不同，将秩较小的树连接到秩较大的树的根节点下面；如果两棵树的秩相同，则无所谓两棵树的连接方式。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSetUnionBySize2.png" width=800px>

Time complexity: 

O(logN) without Path Compression.

- **路径压缩（Path Compression）**

路径压缩是把树展平为高度只有1的树。要实现路径压缩，只需在查询操作过程中，把沿途的每个节点的父节点都设为根节点。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/DisjointSet4.png" width=400px>

Time complexity: 

路径压缩可以将时间复杂度优化到接近常数时间。

### Time Complexity

Time Complexity (Worst Case):

|Operation|Tree Based Disjoint Set|Union by Rank/Size without Path Compression|Union by Rank/Size with Path Compression|
|---|---|---|---|
|Union( )|O(1)|O(1)|O(1)|
|Find( )|O(N)|O(logN)|O(α(N))|

> α函数为阿克曼函数的反函数，其增长极其缓慢，可以认为是一个很小的常数。
