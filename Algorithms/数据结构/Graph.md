# 图（Graph）
<details>
<summary> Later Updates </summary>

- Shortest Path in Graph
- Minimum Spanning Tree

- 图的连通性
- Maximum Flow

</details>

- 基础概念
  - 图的定义
  - 图的类型
    - 有向图与无向图；有权图与无权图；
    - 简单图与多重图；稠密图与稀疏图
- 图的表示
  - 邻接矩阵与邻接表
  - 对比：邻接矩阵与邻接表
- 图搜索算法：DFS和BFS
  - 图的深度优先遍历：用栈存储次序信息
  - 图的宽度优先遍历：用队列存储次序信息
  - DFS和BFS的遍历路径
  - 对比：DFS和BFS
- 拓扑排序与环检测
  - 有向图的环检测
  - 拓扑排序
  - 无向图的环检测
- 习题和参考资料
  
## 基础概念

### 图的定义

A Graph denoted by *G=(V, E)*, is a non-linear data structure defined by a finite set of vertices *V*, and a set of edges *E* consisting of ordered or unordered pairs of vertices from *V*. 

- **顶点与边**
  - 顶点(Vertices)
  - 边(Edges)
  - 顶点的度(Degree of a Vertex): The degree of a vertex is the number of edges incident with that vertex.

- **路径**
  - 路径(Path): A path is a sequence of vertices with the property that each vertex in the sequence is adjacent to the vertex next to it. A path that does not repeat vertices is called a simple path.

- **环**
  - 环(Cycle): A Cycle in graph is a path in which **only** the first and last vertices are equal.
  - 回路(Circuit): A circuit is a path in graph in which the first and last vertices are equal.
  
- **自环与重边**
  - 自环(Loop): A loop is an edge that connects a vertex to itself.
  - 重边(Multiple Edges): Multiple edges are two or more edges connecting the same two vertices. 

### 图的类型

- **有向图与无向图**
  - 有向图(Directed Graph): A graph in which edge has direction. That is the nodes are ordered pairs in the definition of every edge.
  - 无向图(Undirected Graph): A graph in which edges do not have any direction. That is the nodes are unordered pairs in the definition of every edge. 

- **有权图与无权图**
  - 有权图(Weighted Graph): A graph in which the edges are already specified with suitable weight is known as a weighted graph. 
  - 无权图(Unweighted Graph): An unweighted graph is a graph in which the edges do not have weights or costs associated with them. Instead, they simply represent the presence of a connection between two vertices.

- **简单图与多重图**
  - 简单图(Simple Graph): A simple graph is a graph that does not allow for loops or multiple edges.
  - 多重图(Multigraph,or Pseudograph): A multigraph is a graph which is permitted to have multiple edges.

- **稠密图与稀疏图**
  - 稠密图(Dense Graph): A graph with many edges compared to the number of vertices.
  - 稀疏图(Sparse Graphs): A graph with relatively few edges compared to the number of vertices.

## 图的表示

### 邻接矩阵与邻接表

  Assume the graph *G=(V, E)* contains *|V|* vertices and *|E|* edges.  
  - 邻接矩阵(Adjacency Matrix)：一个 *V×V* 二维数组（矩阵），在二维数组中保存每两个节点间的联通关系。
  - 邻接表(Adjaceny List)：一个长度为 *V* 的哈希表，其中每个数据对的Key值存储节点，Value值存储从该节点出发的所有相邻节点。

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/Graph1.png" width=600px>

在图的邻接表表示中，如果G是一个有向图，则所有链表的长度之和为 *|E|*；如果G是一个无向图，则所有链表的长度之和为*2|E|*。

### 对比：邻接矩阵与邻接表

时间复杂度:

|Operation|Adijacency Matrix|Adjacency List|
|:---:|:---:|:---:|
|Store graph|O(V<sup>2</sup>)|O(V+E)|
|Add vertex|O(V<sup>2</sup>)|O(1)|
|Add edge|O(1)|O(1)|
|Remove vertex|O(V<sup>2</sup>)|O(E)|
|Remove Edge|O(1)|O(V)|
|判断已知位置的<br>两个节点是否邻接|O(1)|O(V)|

结论：

      - 大多数情况下，邻接表都优于邻接矩阵（不过，邻接表和邻接矩阵在渐进意义下至少是一样有效的）。
      - 稀疏图更适合使用邻接表，但是当遇到稠密图或必须很快判断两个给定顶点是否存在连接边时，更适合使用邻接矩阵。

## 图搜索算法：DFS和BFS

图搜索算法（或者说图遍历算法）(Graph Search (or Graph Traversal) Algorithms)，主要用于在图中进行搜索或者发现。它们会访问算法能够到达的所有节点，但是不会对搜索路径有优化需求。而路径规划算法(Pathfinding Algorithms)则用于在图中寻找给定的起点与终点之间符合特定要求的路径。

图搜索算法包含深度优先搜索（Depth First Traversal, DFS）和宽度优先搜索(Breadth First Traversal, BFS)。DFS和BFS做为两个最基础的图搜索算法，通常是其他路径规划算法的基础部件。

### 深度优先搜索

图的DFS算法与树的DFS算法相近，两者的关键不同在于，由于图中可能有环，图的DFS算法需要额外记录每个个节点是否已经被访问过（Visted/Not visted），以避免对某个节点的反复访问。

图的DFS结果不唯一。

**【算法-非递归实现】**

0. 创建一个栈。
1. 从源节点开始，把源节点的所有相邻节点依次放入栈。
2. 弹出一个节点，把该节点下的所有**没有进过栈**的相邻节点放入栈。
3. 重复步骤1、2，直到栈变成空栈。

### 宽度优先搜索

图的BFS算法与树的BFS算法相近，两者的关键不同在于，由于图中可能有环，图的BFS算法需要额外记录每个节点是否已经被访问过（Visted/Not visted），以避免对某个节点的反复访问。

**【算法-非递归实现】**

0. 创建一个队列。
1. 从源节点开始，把源节点的所有相邻节点依次放入队列。
2. 弹出一个节点，把该节点下的所有**没有进过队列**的相邻节点放入队列。
3. 重复步骤1、2，直到队列变成空队列。

### DFS和BFS的遍历路径

在DFS和BFS的遍历过程中，节点有3种标记状态：已访问过（Visited Nodes），未访问过(Not Visited Nodes)，以及还在递归栈中的（Unfinished/ On Path Nodes）。

[Animation of Graph DFS(Video)](https://www.youtube.com/watch?v=NUgMa5coCoE)

[Animation of Graph BFS(Video)](https://www.youtube.com/watch?v=x-VTfcmrLEQ)

### 对比：DFS和BFS

1. 正确性: 
    - 如果解存在，那么BFS一定能找到该解；而DFS不保证能找到该解。
    - 如果存在多个解，那么BFS可以找最短路径解；而DFS不能保证找到最短路径解。
2. 实现
    - DFS可能会陷入永远沿着一条路径走的循环，解决方法之一是对DFS设置一个截止深度(Cut-off Depth)；BFS不会陷入循环。
    - DFS的递归写法可读性非常好；BFS的递归写法实质上是借用了DFS的递归，在每次访问一个节点时，记录下该节点所属的level，然后按level的次序返回节点
    - DFS可以回溯；BFS不能回溯。
3. Cost
    - BFS在时间和空间上的花销都比DFS大。 
    - 时间复杂度
      - DFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix 
      - BFS：O(V+E) for Adjacency List, O(V<sup>2</sup>) for Adjacency Matrix
    - 空间复杂度：假设图的深度为d，宽度(所有顶点的最大出度)为b
      - DFS：由于仅需记录一条路径上的点，需求的额外空间较少，为O(d)
      - BFS: 要记录访问到的每一层的层次信息，需求的额外空间较多，为O(b×d）

结论：

    - 大多数情况下，DFS算法可以节省时间、空间开销。
    - 搜索的目标节点距离起点较近的情况，例如求最短路径，用BFS速度更快。
    - DFS算法能够记录回溯信息。

## 拓扑排序与环检测

拓扑排序(Topological Sort): Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge *(u, v)*, vertex *u* comes before *v* in the ordering.

拓扑排序算法是图的DFS/BFS算法的一个应用，用于寻找一个符合活动先后依赖关系的线性序列。

在处理依赖性问题时，首先用有向图表示项目，用顶点表示项目中的活动，用有向边表示活动之间的先后依赖关系。那么，检测这个有向图中是否存在环，就等于检测该项目是否存在循环依赖；如果这个有向图中没有环，也就是说这是一个有向无环图，那么它一定存在至少一个拓扑序列，也就等于该项目中存在一个符合依赖关系的线性序列。因此，有向图的环检测和拓扑排序算法这两个问题本质上是一致的，区别仅在于，有向图的环检测仅仅需要一个判断结果，而拓扑排序算法需要输出一个符合依赖关系的结果序列。

### 有向图的环检测

**【算法-基于DFS】**

如果一个图中有环，那么它一定有一条后向边(back edge)。 要检测后向边，就要对遍历过程进行tracking。前面提到，在DFS的遍历过程中，节点有3种标记状态：已访问过（Visited Nodes），未访问过（Not Visited Nodes），以及还在递归栈中的（Unfinished Nodes）。 因此，如果在DFS的递归过程中，当前到达的节点仍然还在于递归栈中，说明这个有向边指向了同一条路径中的过去访问过的节点，也就是说图中存在环。

**【算法-基于BFS】**

0. 创建一个数组，用于记录图中所有节点的入度；创建一个队列，将入度为0的点放入队列中。
1. 将队列中的头节点出队并输出到结果队列，再将它及它的影响删除(发出的边删除，后继节点的入度-1)，将后继邻接节点中所有入度变为0的节点放入队列。
2. 重复步骤1，直到队列清空。
3. 如果结果队列中的节点数等于有向图的节点数，说明该有向图中不存在环。否则，说明有向图中存在环。

> 如果有向图中有环，那么就会有节点的入度永远不会被减到0，也就永远不会进入结果队列。

- Cost
  - 时间复杂度：O(*V*+*E*)
  - 空间复杂度：O(*V*) 

### 拓扑排序

拓扑排序的适用范围是有入度为0节点的有向无环图(DAG)。有向无环图和存在拓扑序列是互为充分必要条件的：
  - 如果一个图不是有向无环图，那么它就没有拓扑序列。
  - 如果一个图是有向无环图，那么它至少有一个拓扑序列。
  - 反之，如果一个图存在一个拓扑序列，那么这个图必定是有向无环图。

**【应用范例】**
  
  - 项目的依赖性问题：建立一个有向无环图，用顶点表示活动，用边表示活动之间的先后依赖关系，找出该图中的拓扑序列。
  - 判断一个图是不是有向无环图：判断用拓扑排序得到的拓扑序列所包含的节点数量是否与图的节点数量相等。

**【算法-基于DFS】**

当到达一个节点时，并不立即输出这个节点，而是先对该节点的所有相邻节点先递归地调用拓扑排序算法，然后将这个节点压入结果栈。当所有节点都访问过以后，将结果栈输出（拓扑排序中的节点顺序与他们从递归栈中出栈的顺序相反，因此需要额外创建一个结果栈来实现反序输出）。

0. 创建一个栈来存放结果；创建一个数组来标记每个节点是Visited还是Not Visited，并初始化。创建一个数组来标记每个节点是否在递归栈中。
1. 从任意一个节点A开始，如果节点A是Visited，不用执行任何操作。如果节点A是Not Visited，将节点A放入递归栈中。 
   1. 访问节点A的所有相邻节点。       
      1. 如果这些相邻节点中有存在于递归栈中的节点，说明该DAG有环，不能进行拓扑排序。
      2. 否则，对A的所有相邻节点递归地调用拓扑排序算法，直到节点A的没有Not visited的相邻节点。
   2. 将节点A标记为Visited，并压入结果栈。
2. 重复步骤1，直到所有节点都是Visited，并被压入结果栈。
3. 将结果栈输出。 

**Example: Topological Sort using DFS**

<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/TopologicalSortDFS1.png" width=600px>

**【算法-基于BFS】**

> 这种利用节点入度的拓扑排序算法即为Kahn's Algorithm。

0. 创建一个数组，用于记录图中所有节点的入度；创建一个队列，将入度为0的点放入队列中。
1. 将队列中的头节点出队并放入结果序列，再将它及它的影响删除(发出的边删除，后继节点的入度-1)，将后继邻接节点中所有入度变为0的节点放入队列。
2. 重复步骤1，直到队列清空。
3. 如果结果序列中的节点数不等于图的节点数，说明该有向图中存在环。如果结果序列中的节点数等于图的节点数，说明该有向图中不存在环，这个结果序列就是该有向图的拓扑序列。

- Cost
  - 时间复杂度：O(*V*+*E*)
  - 空间复杂度：O(*V*)

### 无向图的环检测

在有向图的环检测中使用的算法适当修改即可用于无向图中。

**【算法-基于DFS】**

如果一个图中有环，那么它一定有一条后向边(back edge)。在DFS的遍历过程中，如果发现某个节点有一条边指向已访问过的节点，并且这个已访问过的节点不是上一步访问的节点（由于是无向边，一个节点肯定会回指上一步的节点，把这种情况排除），那么图中就存在环。

**【算法-基于BFS】**

0. 创建一个数组，用于记录图中所有节点的度；创建一个队列，将度≤1的点放入队列中。
1. 将队列中的头节点出队并放入结果序列，再将它及它的影响删除(邻接节点的度-1)，将邻接节点中所有度变为1的节点放入队列。
2. 重复步骤1，直到队列清空。
3. 如果结果序列中的节点数不等于图的节点数，说明该无向图中存在环。如果结果序列中的节点数等于图的节点数，说明该无向图中不存在环。
   
## 习题和参考资料

**参考资料**

- [Difference between BFS and DFS](https://www.geeksforgeeks.org/difference-between-bfs-and-dfs/?ref=lbp)
- [Topological Sorting](https://www.geeksforgeeks.org/topological-sorting/)
