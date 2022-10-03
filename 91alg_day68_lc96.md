### Idea

- Have an array to save the number of unique trees of given number of nodes.
- Go through 1-n, multiply the unique trees numbers of left subtree and right subtree, and add together will get the number of unique trees of given number of nodes.

### Code

```java
class Solution {
    public int numTrees(int n) {
        int[] trees = new int[n+1];
        Arrays.fill(trees, 1);
        for(int i = 2;i<n+1;i++){
            int tree = 0;
            for(int j = 1;j<i+1;j++){
                int left = j-1;
                int right = i-j;
                tree += (trees[left]*trees[right]);
            }
            trees[i] = tree;
        }
        return trees[n];
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n^2)
- Space Complexity: O(n)
