### Idea
- Keep visited state, return 0 when cell is visited, out of bounds, not island
- Visit every cell in the grid, use DFS count connected cells, return the island area and get max
### Code

```java
class Solution {
    public int[][] visited;
    public int maxAreaOfIsland(int[][] grid) {
        visited = new int[grid.length][grid[0].length];
        int result = 0;
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[0].length;j++){
                result=Math.max(result, dfs(grid,i,j));
            }
        }
        return result;
    }
    public int dfs(int[][] grid, int row, int col){
        if(row<0||row>=grid.length||col<0||col>=grid[0].length||grid[row][col]==0||visited[row][col]==1){
            return 0;
        }
        visited[row][col]=1;
        int area = 1+dfs(grid,row+1,col)+dfs(grid,row,col+1)+dfs(grid,row-1,col)+dfs(grid,row,col-1);
        return area;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(m*n)
- Space Complexity:O(m*n)
