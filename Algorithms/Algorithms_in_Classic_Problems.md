# Algorithms in Classic Problems

- [图](#图)
  - [Flood Fill Algorithms](#Flood_Fill)
  - [岛屿问题/the Number of Islands](#岛屿问题)
  - [习题和参考资料](#习题和参考资料20230910)

## 图<a name="图"></a>

### Flood Fill Algorithms <a name="Flood_Fill"></a>

Flood fill, is a flooding algorithm that determines and alters the area connected to a given node in a multi-dimensional array with some matching attribute.

**核心思路**

- 就是图的遍历，使用DFS、BFS都可以

|<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/floodfill1_animation_stack.gif" width=200px>|<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/floodfill1_animation_queue.gif" width=200px>|
|---|---|
|Four-way flood fill using a stack|Four-way flood fill using a queue|

### 岛屿问题/the Number of Islands <a name="岛屿问题"></a>

**问题背景**

Given a matrix of size M x N, where ‘1’ represents land, while ‘0’ represents water. An island is a group of 1’s surrounded either vertically or horizontally.
Return the number of islands present in the matrix.

**Example 1**

> **Input:**
>
> <img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/%E5%B2%9B%E5%B1%BF%E9%97%AE%E9%A2%981.jpg" width=200px>
> 
>**Output:** 4

**核心思路**

- 使用BFS/DFS遍历二维数组，也就是Flood Fill Algorithm

**方法 1：DFS**

- **算法**

1. Scan the matrix from (0,0) to (N, M).
2. If the current element is ‘1’, start a DFS.
3. In the DFS traversal, mark every visited node.
4. Count the number of islands as the number of nodes that trigger the DFS.
5. Return count.

- **复杂度**

  Time Complexity: O(M * N), where M and N are the size of the matrix
  
  Space Complexity: O(M * N)

**方法 2：BFS**

- **算法**

1. Scan the matrix from (0,0) till (N, M).
2. If the current element is ‘1’, start a BFS.
3. Consider a queue and put the current node into the queue.
4. Iteratively visit its neighbours vertically and horizontally and mark them as visited.
5. The count is the total number of times the BFS has been invoked.
6. Return count.

- **复杂度**
  
  Time Complexity: O(M * N), where M and N is the size of the matrix

  Space Complexity: O(min(M,N))

### 习题和参考资料 <a name="习题和参考资料20230910">

**习题**

- [算法题解：Flood_Fill&岛屿问题](算法题解/算法题解-Flood_Fill&岛屿问题.md)

**参考资料**

- [Wikipedia: Flood fill](https://en.wikipedia.org/wiki/Flood_fill)
- [Finding The Number of Islands](https://www.interviewbit.com/blog/number-of-islands/)