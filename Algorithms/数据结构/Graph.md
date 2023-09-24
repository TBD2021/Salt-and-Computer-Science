# 图/Graph
<details>
<summary> Later Updates </summary>
√- 基础概念
  √- 图的定义
  √- 图的表示与底层实现
√- 图的遍历
  √- 深度优先遍历/DFS：用栈存储次序信息
  √- 宽度优先遍历/BFS：用队列存储次序信息
  √- Trade-off Between DFS and BFS
√- 拓扑排序
  
  - 图的环
  - Detect Cycle in a Directed Graph/Undirected Graph/........
- Shortest Path in Graph
- Minimum Spanning Tree

- 图的连通性
- Maximum Flow
- 习题和参考资料
</details>

- 基础概念
  - 图的定义与相关概念
  - 图的类型
    - 有向图与无向图、
    - 有权图与无权图
    - 简单图与多重图
    - 稠密图与稀疏图
  - 图的表示与底层实现
    - 邻接矩阵
    - 邻接表
    - 对比：Adijacency List and Adijacency Matrix
- 图的遍历和图搜索算法
  - 图的深度优先遍历：用栈存储次序信息
  - 图的宽度优先遍历：用队列存储次序信息
  - 图搜索算法：DFS和BFS
    - 图搜索算法和路径规划算法概述
    - 对比：DFS and BFS
- 拓扑排序

## 基础概念

### 图的定义与相关概念

A Graph denoted by *G=(V, E)*, is a non-linear data structure defined by a finite set of vertices *V*, and a set of edges *E* consisting of ordered or unordered pairs of vertices from *V*. 

**顶点与边**

- 顶点/Vertices
- 边/Edges
- 顶点的度/Degree of a Vertex: The degree of a vertex is the number of edges incident with that vertex.

**路径**

- 路径/Path: A path is a sequence of vertices with the property that each vertex in the sequence is adjacent to the vertex next to it. A path that does not repeat vertices is called a simple path.

**环**

- 环/Cycle: A Cycle in graph is a path in which **only** the first and last vertices are equal.
- 回路/Circuit: A circuit is a path in graph in which the first and last vertices are equal.
  
**自环与重边**

- 自环/Loop: A loop is an edge that connects a vertex to itself.
- 重边/Multiple Edges: Multiple edges are two or more edges connecting the same two vertices. 

### 图的类型

**有向图与无向图**

- 有向图/Directed Graph: A graph in which edge has direction. That is the nodes are ordered pairs in the definition of every edge.
- 无向图/Undirected Graph: A graph in which edges do not have any direction. That is the nodes are unordered pairs in the definition of every edge. 

**有权图与无权图**

- 有权图/Weighted Graph: A graph in which the edges are already specified with suitable weight is known as a weighted graph. 
- 无权图/Unweighted Graph: An unweighted graph is a graph in which the edges do not have weights or costs associated with them. Instead, they simply represent the presence of a connection between two vertices.

**简单图与多重图**

- 简单图/Simple Graph: A simple graph is a graph that does not allow for loops or multiple edges.
- 多重图/Multigraph(or Pseudograph): A multigraph is a graph which is permitted to have multiple edges.

**稠密图与稀疏图**

- 稠密图/Dense Graph: A graph with many edges compared to the number of vertices.
- 稀疏图/Sparse Graphs: A graph with relatively few edges compared to the number of vertices.

### 图的表示与底层实现

Assume the graph *G=(V, E)* contains *|V|* vertices and *|E|* edges.
- 邻接矩阵/Adjacency Matrix：一个 *V×V* 二维数组（矩阵），在二维数组中保存每两个节点间的联通关系。
- 邻接表/Adjaceny List：一个长度为 *V* 的哈希表，其中每个数据对的Key值存储节点，Value值存储从该节点出发的所有相邻节点。

**对比：Adijacency List and Adjaacency Matrix**

Time Complexity Cost:

|Action|Adijacency Matrix|Adjacency List|
|---|---|---|
|Store graph|O(V<sup>2</sup>)|O(V+E)|
|Add vertex|O(V<sup>2</sup>)|O(1)|
|Add edge|O(1)|O(1)|
|Remove vertex|O(V<sup>2</sup>)|O(E)|
|Remove Edge|O(1)|O(V)|
|判断已知位置的两个节点是否邻接|O(1)|O(V)|

- 大多数情况下，邻接表都优于邻接矩阵。
- 稀疏图适合用邻接表存储，稠密图适合用邻接矩阵存储。

## 图的遍历

### 深度优先遍历/Depth First Traversal

图的DFS算法与树的DFS算法相近。关键的不同在于，由于图中可能有环，图的DFS算法需要记录一个节点是否已经被访问过（Visted/Not visted），以避免对一个节点反复访问。

图的DFS结果不唯一。

**【算法-非递归实现】**

1. 从源节点开始，把相邻节点依次放入栈。
2. 弹出一个节点，把该节点下一个**没有进过栈**的邻接节点放入栈。
3. 重复步骤1、2，直到栈变成空栈。

### 宽度优先遍历/Breadth First Traversal

图的BFS算法与树的BFS算法相近。关键的不同在于，由于图中可能有环，图的BFS需要记录一个节点是否已经被访问过（Visted/Not visted），以避免对一个节点反复访问。

**【算法-非递归实现】**

1. 从源节点开始，把相邻节点依次放入队列。
2. 弹出一个节点，把该节点下一个**没有进过队列**的邻接节点放入队列。
3. 重复步骤1、2，直到队列变成空队列。

### 图搜索算法：DFS和BFS

**图搜索算法与路径规划算法概述**

图搜索算法/Graph Search (or Graph Traversal) Algorithms: 图搜索算法，或者说图遍历算法，主要用于在图中进行搜索或者发现。它们会访问所有算法能够到达的节点，但是不会对搜索路径有优化需求。图搜索算法包含深度优先搜索DFS和宽度优先搜索BFS，它们往往是其他路径规划算法的基础。

-DFS: 从给定的起点在图中做深度优先遍历。

-BFS: 从给定的起点在图中做宽度优先遍历。

路径规划算法/Pathfinding Algorithms: 路径规划算法用于在图中寻找给定的起点与终点之间符合要求的路径。

**对比：DFS and BFS**

DFS和BFS做为两个最基础的图搜索算法，通常是其他路径规划算法的基础部件：
- 正确性: 
  - 如果解存在，那么BFS一定能找到该解；而DFS不保证能找到该解。
  - 如果存在多个解，那么BFS可以找最短路径解；而DFS不能保证找到最短路径解。
- 实现
  - DFS可能会陷入永远沿着一条路径走的循环，解决方法之一是对DFS设置一个截止深度(Cut-off Depth)；BFS不会陷入循环。
  - DFS的递归写法可读性非常好；BFS的递归写法实质上是借用了DFS的递归，在每次访问一个节点时，记录下该节点所属的level，然后按level的次序返回节点
- Cost
  - BFS在时间和空间上的花销都比DFS大。 
  - 时间复杂度
     - DFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix 
     - BFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix
  - 空间复杂度：假设图的深度为d，宽度(所有顶点的最大出度)为b
    - DFS：由于仅需记录一条路径上的点，需求的额外空间较少，为O(d)
    - BFS: 要记录访问到的每一层的层次信息，需求的额外空间较多，为O(b×d）

结论：

- 大多数情况下，用DFS可以节省时间、空间
- 搜索的目标节点距离起点较近的情况，如求最短路径，用BFS速度更快

## 拓扑排序算法/Topological Sort

拓扑排序/Topological Sort: Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge *(u, v)*, vertex *u* comes before *v* in the ordering.

- 拓扑排序用于寻找一个符合依赖关系的线性序列。
- 拓扑排序的适用范围是有向无环图(DAG)，且有入度为0的节点。有向无环图和存在拓扑序列是互为充分必要条件：
  - 如果一个图不是有向无环图，那么它就没有拓扑序列。
  - 如果一个图是有向无环图，那么它至少有一个拓扑序列。
  - 反之，如果一个图存在一个拓扑序列，那么这个图必定是有向无环图。

**【应用范例】**
  
  - 项目之间的依赖性问题：建立一个有向无环图，用顶点表示项目，用边表示依赖关系，找出该图中的拓扑序列。
  - 判断一个图是不是有向无环图：判断用拓扑排序得到的拓扑序列所包含的节点数量是否与图的节点数量相等。 

**【算法-基于BFS】**

1. 计算图中所有节点的入度。将入度为0的点放入一个队列中。
2. 将队列中的头节点出队并输出，再将它及它的影响删除(发出的边删除，后继节点的入度-1)，将后继节点中所有入度变为0的节点放入队列。
3. 重复步骤2，直到队列清空。

- Cost
  - 时间复杂度：O(*V*+*E*)
  - 空间复杂度：O(*V*) 

## 习题和参考资料

**参考资料**
- [Difference between BFS and DFS](https://www.geeksforgeeks.org/difference-between-bfs-and-dfs/?ref=lbp)
