### Idea
- dp array [m][n], set up  base cases [0][0], first row, first column all equals to 1
- Fill the dp array: 
  - cell is filled with the sum of the cell before and above current cell for the previous
  - result is at [m-1][n-1]
### Code

```java
class Solution {
    public int uniquePaths(int m, int n) {
        int[][] grid = new int[m][n];
        grid[0][0] = 1;
        for(int i = 1; i < m;i++){
            grid[i][0]=1;
        }
        for(int j = 1; j < n;j++){
            grid[0][j]=1;
        }
        for(int i  = 1; i< m;i++){
            for(int j = 1; j < n; j++){
                grid[i][j]=grid[i-1][j]+grid[i][j-1];
            }
        }
        return grid[m-1][n-1];
    }
}

```

**Complexity Analysis**

- Time Complexity: O(m*n)
- Space Complexity: O(m*n)
