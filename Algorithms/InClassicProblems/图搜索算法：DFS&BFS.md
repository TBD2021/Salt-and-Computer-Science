# 图搜索算法：DFS and BFS

- [泛洪算法/Flood Fill Algorithms](#Flood_Fill)
- [岛屿问题/the Number of Islands](#岛屿问题)
- [习题和参考资料](#习题和参考资料20230910)

## 泛洪算法/Flood Fill Algorithms <a name="Flood_Fill"></a>

Flood fill, is a flooding algorithm that determines and alters the area connected to a given node in a multi-dimensional array with some matching attribute.

**核心思路**

就是图的遍历，每次访问一个未访问过的节点，将其淹没(染色)。使用DFS、BFS都可以。

|<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/floodfill1_animation_stack.gif" width=200px>|<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/floodfill1_animation_queue.gif" width=200px>|
|---|---|
|4-way flood fill using a stack|4-way flood fill using a queue|

## 岛屿问题/the Number of Islands <a name="岛屿问题"></a>

**问题背景**

Given a matrix of size M x N, where ‘1’ represents land, while ‘0’ represents water. An island is a group of 1’s surrounded either vertically or horizontally.
Return the number of islands present in the matrix.

**【Example 1】**

> **Input:**
>
> <img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/%E5%B2%9B%E5%B1%BF%E9%97%AE%E9%A2%981.jpg" width=200px>
> 
>**Output:** 4

**核心思路**

使用DFS/BFS遍历图并淹没岛屿，也就是泛洪算法。每当将1个岛屿完全淹没时，岛屿数量+1，将所有岛屿淹没后结束，输出计数结果。

**【算法-DFS】**

1. Scan the matrix from (0,0) to (N, M).
2. If the current element is ‘1’, start a DFS.
3. In the DFS traversal, mark every visited node.
4. Count the number of islands as the number of nodes that trigger the DFS.
5. Return count.

- Cost
  - 时间复杂度：O(M * N), where M and N are the size of the matrix.
  - 空间复杂度：O(M * N).

**【算法-BFS】**

1. Scan the matrix from (0,0) till (N, M).
2. If the current element is ‘1’, start a BFS.
3. Consider a queue and put the current node into the queue.
4. Iteratively visit its neighbours vertically and horizontally and mark them as visited.
5. The count is the total number of times the BFS has been invoked.
6. Return count.

- Cost
  - 时间复杂度：O(M * N), where M and N is the size of the matrix.
  - 空间复杂度：O(min(M,N))

### 习题和参考资料 <a name="习题和参考资料20230910">

**习题**

- [算法题解：泛洪算法&岛屿问题](../算法题解/算法题解-Flood_Fill&岛屿问题.md)

**参考资料**

- [Wikipedia: Flood fill](https://en.wikipedia.org/wiki/Flood_fill)
- [Finding The Number of Islands](https://www.interviewbit.com/blog/number-of-islands/)
