# 算法题解-Flood Fill Algorithms&岛屿问题
- [Flood Fill Algorithms](#Flood_Fill20230910)
  - [Flood Fill: LeetCode-733](#LeetCode-733)
- [岛屿问题/the Number of Islands](#the_Number_of_Islands20230923)
  - [Number of Islands: LeetCode-200](#LeetCode-200)

## Flood Fill Algorithms <a name ="Flood_Fill20230910">

### Flood Fill <a name ="LeetCode-733">
[LeetCode-733. Flood Fill (Easy)](https://leetcode.com/problems/flood-fill/)

**【解析】** 图的遍历，DFS，BFS都可以。

```Java
//4-direction Flood Fill Method
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        graphDFS(image,sr,sc,color);
        return image;      
    }

//Graph DFS, Recursive Implementation
    public void graphDFS(int[][] image, int sr, int sc, int color) {
        int rowNum=image[0].length;
        int columnNum=image.length;
        int preColor=preColor=image[sr][sc];

        if(preColor==color)         //Important: 如果不做这个判定，会反复擦写同一个位置，导致死循环
            return;
        else{
            image[sr][sc]=color;
            if(sr-1>=0&&image[sr-1][sc]==preColor){
                graphDFS(image,sr-1,sc,color);
            }
            if(sr+1<columnNum&&image[sr+1][sc]==preColor){
                graphDFS(image,sr+1,sc,color);
            }
            if(sc-1>=0&&image[sr][sc-1]==preColor){
                graphDFS(image,sr,sc-1,color);
            }
            if(sc+1<rowNum&&image[sr][sc+1]==preColor){
                graphDFS(image,sr,sc+1,color);
            }
        }
        return;  
    }
```
## 岛屿问题/the Number of Islands <a name ="the_Number_of_Islands20230923">

### Number of Islands <a name ="LeetCode-200">
[LeetCode-200. Number of Islands (Medium)](https://leetcode.com/problems/number-of-islands/)

**【解析】** 每次用DFS/BFS遍历，将1个岛涂色。扫描整个矩阵，计数总共涂了几个岛。

```Java
    public int rSize;   //row size
    public int cSize;   //column size

    public int numIslands(char[][] grid) {
        int res=0;
        rSize=grid.length;
        cSize=grid[0].length;

        int i=0;
        int j=0;
        while(i<rSize){
            while(j<cSize){
                if(grid[i][j]=='1'){
                    dfsGraph(grid, i, j, '1','0');
                    res++;
                }
                j++;
            }
            j=0;
            i++;
        }
        return res;        
    }

//Graph DFS, Recursive Implementation
    public void dfsGraph(char[][]grid, int rNum, int cNum, char pre, char cur){
        if(rNum-1>=0&&grid[rNum-1][cNum]==pre){
            grid[rNum-1][cNum]=cur;
            dfsGraph(grid, rNum-1, cNum, pre,cur);
        }
        if(rNum+1<rSize&&grid[rNum+1][cNum]==pre){
            grid[rNum+1][cNum]=cur;
            dfsGraph(grid, rNum+1, cNum, pre,cur);
        }
        if(cNum-1>=0&&grid[rNum][cNum-1]==pre){
            grid[rNum][cNum-1]=cur;
            dfsGraph(grid, rNum, cNum-1, pre,cur);
        }
        if(cNum+1<cSize&&grid[rNum][cNum+1]==pre){
            grid[rNum][cNum+1]=cur;
            dfsGraph(grid, rNum, cNum+1, pre,cur);
        }
        return;
    }
```



