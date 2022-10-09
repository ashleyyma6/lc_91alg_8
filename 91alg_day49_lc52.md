### Idea
- Put one queen, the next queen:
  - cannot put in the same row -> put Queen row by row
  - cannot put in the same column -> save the column that has Queen, check before put
  - cannot put on the two diagonal -> save the two diagnoal that have Queen\
    - for up diagonal, row+col is unique for every diagnal
    - for down diagonal, row-col is unique ...
    - Use set
  - Put new Queen, check if it works, continue to next row if works, if not, go back, try the next new queen in the current row

### Code

```java
class Solution {
    public int result = 0;
    public int totalNQueens(int n) {
        HashSet<Integer> col = new HashSet<>();
        HashSet<Integer> diag1 = new HashSet<>(); //r+c
        HashSet<Integer> diag2 = new HashSet<>(); //r-c
        int[][] board = new int[n][n];
        backtrack(n,0,board,col,diag1,diag2);
        return result;
    }
    public void backtrack(int n, int r, int[][] board, HashSet<Integer> col, HashSet<Integer> diag1, HashSet<Integer>diag2){
        if(r==n){
            result++;
        }
        
        for(int c=0;c<n;c++){
            if(col.contains(c)||diag1.contains(r+c)||diag2.contains(r-c)){
                continue;
            }
            col.add(c);
            diag1.add(r+c);
            diag2.add(r-c);
            board[r][c] = 1;
            backtrack(n, r+1, board, col, diag1, diag2);
            col.remove(c);
            diag1.remove(r+c);
            diag2.remove(r-c);
            board[r][c]=0;
        }
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n!)
- Space Complexity: O(n)
