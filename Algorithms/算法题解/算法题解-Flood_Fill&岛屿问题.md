# 算法题解-Flood Fill&岛屿问题
- [Flood Fill Algorithms](#Flood_Fill20230910)
  - [Flood Fill: LeetCode-733](#LeetCode-733)

## Flood Fill Algorithms <a name ="Flood_Fill20230910">

### Flood Fill <a name ="LeetCode-733">
[LeetCode-733. Flood Fill (Easy)](https://leetcode.com/problems/flood-fill/)

**解析**图的遍历，DFS，BFS都可以。

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
