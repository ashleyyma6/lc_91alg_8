### Idea
- search t in range [grid[0][0], n*n]
- use dfs to check if a t can have a valid path

### Code

```java
class Solution {
    
    public int swimInWater(int[][] grid) {
        int n = grid.length;
        
        int left = grid[0][0];
        int right = n*n;
        while(left<right){
            int mid = left+(right-left)/2;
            if(path_dfs(grid, mid)){
                right = mid;
            }else{
                left = mid+1;
            }
        }
        return left;
    }
    public boolean path_dfs(int[][] grid, int mid){
        int n = grid.length;
        int[][] visited = new int[n][n];
        Stack<int[]> stack = new Stack();
        stack.add(new int[]{0,0});
        int[][] dirs = new int[][]{{0,1},{0,-1},{1,0},{-1,0}};
        while(!stack.empty()){
            int[] curr = stack.pop();
            if(curr[0] == n-1 && curr[1] == n-1){
                  return true;
            }
            for(int[] dir:dirs){
                int row = curr[0]+dir[0];
                int col = curr[1]+dir[1];
                if(row>=0 && row<n && col>=0 && col<n && visited[row][col]==0 && grid[row][col]<=mid){
                    stack.add(new int[]{row,col});
                    visited[row][col] = 1;
                }            
            }
        }
        return false;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n^2logn)
- Space Complexity: O(n)
