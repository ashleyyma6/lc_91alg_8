### Idea
- make an dp array, check all possible step changes, fill thge array with the possibliity when start at a row, a column, k step to walk. Sum up all k step possibility. 
### Code

```java
class Solution {
    public double knightProbability(int n, int k, int row, int column) {
        if(k==0){
            return 1.0d;  
        }
        int[][] moves = new int[][]{{2,1},{2,-1},{-2,1},{-2,-1},{1,2},{1,-2},{-1,-2},{-1,2}};
        double[][][] dp = new double[k+1][n][n];
        dp[0][row][column] = 1.0;
        for(int i = 0 ;i < k;i++){
            for(int j = 0;j < n;j++){
                for(int m = 0;m < n;m++){
                    for(int[] move:moves){
                        if((j+move[0]<n) && (j+move[0]>-1) && (m+move[1]<n) && (m+move[1]>-1)){
                            dp[i+1][j+move[0]][m+move[1]] += dp[i][j][m]/8.0d;
                        }
                    }
                }
            }
        }
        double res = 0;
        for(int i = 0;i < n;i++){
            for(int j = 0;j < n;j++){
                res+=dp[k][i][j];
            }
        }
        //return dfs(n,k,row,column);
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(nnk)
- Space Complexity:O(nnk)
