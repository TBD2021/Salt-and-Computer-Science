# 图/Graph
<details>
- 基础
  - 图的定义与特性
  - 图的表示与底层实现
  - Transpose graph??????
- 图的遍历
  - 深度优先遍历/DFS：用栈存储次序信息
  - 宽度优先遍历/BFS：用队列存储次序信息
  - Trade-off Between DFS and BFS
- 图的环
  - Detect Cycle in a Directed Graph/Undirected Graph/........
- Shortest Path in Graph
- Minimum Spanning Tree
- 拓扑排序
- 图的连通性
- Maximum Flow
- 习题和参考资料
</details>

## 基础

A graph *G=(V, E)* is defined by a finite set of *vertices V*, and a set of *edges E* consisting of ordered or unordered pairs of vertices from *V*. 

**特性**

- Directed vs. Undirected Graphs
- Weighted vs. Unweighted Graphs
- Simple vs. Non-Simple Graphs
- Sparse vs. Dense Graphs

## 图的底层实现

Assume the graph *G=(V, E)* contains *|V|* vertices and *|E|* edges.
- 邻接矩阵/Adjacency Matrix：一个 *V×V* 二维数组（矩阵），在二维数组中保存每两个节点间的联通关系
- 邻接表/Adjaceny list：一个长度为 *V* 的哈希表，其中每个数据对的Key值存储节点，Value值存储从该节点出发的所有相邻节点

**Trade-off between Adijacency List and Adjaacency Matrix**

|Time Complexity Cost|
|   |Adijacency List|Adjacency Matrix|
|---|---|---|
|Store graph|O(V+E)|O(V<sup>2</sup>)|
|Add vertex|O(1)|O(V<sup>2</sup>)|
|Add edge|O(1)|O(1)|
|Remove vertex|O(E)|O(V<sup>2</sup>)|
|Remove Edge|O(V)|O(1)|
|判断已知位置的两个节点是否邻接|O(V)|O(1)|

- 大多数情况，邻接表都优于邻接矩阵
- 稀疏图(节点较多，边较少)适合用邻接表存储，稠密图(节点较少，边较多)适合用邻接矩阵存储

## 图的遍历

**I. 深度优先遍历/Depth First Traversal**

图的DFS算法与树的DFS算法相近。关键的不同在于，由于图中可能有环，图的DFS需要记录一个节点是否已经被访问过（Visted/Not visted），以避免对一个节点反复访问。

图的DFS结果不唯一。

- **算法**-非递归实现

1. 从源节点开始，把相邻节点依次放入栈。
2. 弹出一个节点，把该节点下一个**没有进过栈**的邻接节点放入栈。
3. 重复步骤1、2，直到栈变成空栈。

**II. 宽度优先遍历/Breadth First Traversal**

图的BFS算法与树的BFS算法相近。关键的不同在于，由于图中可能有环，图的BFS需要记录一个节点是否已经被访问过（Visted/Not visted），以避免对一个节点反复访问。

- **算法**-非递归实现

1. 从源节点开始，把相邻节点依次放入队列。
2. 弹出一个节点，把该节点下一个**没有进过队列**的邻接节点放入队列。
3. 重复步骤1、2，直到队列变成空队列。

**III. Trade-off between DFS and BFS***

首先分析图的DFS和BFS的优缺点。

- 正确性
  - 如果解存在，那么BFS一定能找到该解
  - DFS不保证能找到该解
  - 如果存在多个解，那么BFS可以找那个最小解（需求步数最小的解）
  - DFS不能保证找到最小解
- 时间复杂度
  - DFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix 
  - BFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix
- 空间复杂度
  假设图的深度为d，宽度(所有顶点的最大出度)为b
  - DFS：由于仅需记录一条路径上的点，需求的额外空间较少，为O(d)
  - BFS: 要记录访问到的每一层的层次信息，需求的额外空间较多，为O(b×d）
- 实现
  - DFS可能会陷入永远沿着一条路径走的循环，解决方法之一是对DFS设置一个截止深度（Cut-off Depth）
  - BFS不会陷入循环
  - DFS的递归写法可读性非常好
  - BFS的递归写法，实质上是借用DFS的递归，在每次访问一个节点时，记录下该节点所属的level，然后按level的次序返回节点

**总结**

- 搜索的目标节点距离起点较近的情况，如求最短路径，用BFS速度更快
- General Case，用DFS可以节省空间

## 拓扑排序/Topological Sort



### 习题和参考资料

**参考资料**
- [Difference between BFS and DFS](https://www.geeksforgeeks.org/difference-between-bfs-and-dfs/?ref=lbp)
