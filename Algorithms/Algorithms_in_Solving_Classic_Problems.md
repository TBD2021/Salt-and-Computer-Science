# Algorithms in Solving Classic Problems

## 目录

 [图](#图)

- [岛屿问题/Number of Islands](#岛屿问题)

## 图<a name="图"></a>

### 岛屿问题/Number of Islands <a name="岛屿问题"></a>

**核心思路**

  - 使用BFS/DFS遍历二维数组，这种方法也被称为Flood Fill Algorithm

**问题背景**

Given a matrix of size M x N, where ‘1’ represents land, while ‘0’ represents water. An island is a group of 1’s surrounded either vertically or horizontally.
Return the number of islands present in the matrix.

**Example 1**

> **Input:**
>
> <img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Algorithms/img/%E5%B2%9B%E5%B1%BF%E9%97%AE%E9%A2%981.jpg" width=200px>
> 
>**Output:** 4

**方法 1: DFS**

- **算法:**

  - Scan the matrix from (0,0) to (N, M).
  - If the current element is ‘1’, start a DFS.
  - In the DFS traversal, mark every visited node.
  - Count the number of islands as the number of nodes that trigger the DFS.
  - Return count.

- **复杂度:**
  - Time Complexity: O(M * N), where M and N are the size of the matrix
  - Space Complexity: O(M * N).

**方法 2: BFS**

- **算法:**
  - Scan the matrix from (0,0) till (N, M).
  - If the current element is ‘1’, start a BFS.
  - Consider a queue and put the current node into the queue.
  - Iteratively visit its neighbours vertically and horizontally and mark them as visited.
  - The count is the total number of times the BFS has been invoked.
  - Return count.

- **复杂度:**
  - Time Complexity:O(M * N), where M and N is the size of the matrix
  - Space Complexity:O(min(M,N)).

**习题**

[算法题解：岛屿问题](算法题解.md)
