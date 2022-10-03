### Idea

### Code

```java

class Solution {

    public int[] parent;
    public int[] rank;

    public int findCircleNum(int[][] isConnected) {
        parent = new int[isConnected.length];
        for(int i = 0;i<parent.length;i++){
            parent[i]=i;
        }
        int[] rank = new int[isConnected.length];
        Arrays.fill(rank,1);c

        int res = isConnected.length;
        for(int i = 0;i<isConnected.length;i++){
            for(int j = i; j<isConnected.length;j++){
                if(isConnected[i][j]==1){
                    res-=union(rank, parent, i, j);
                }
            }
        }
        return res;
    }
    public int findRoot(int[] parent, int node){
        int root = node;
        while(root!=parent[root]){
            parent[root] = parent[parent[root]];
            root = parent[root];
        }
        return root;
    }
    public int union(int[] rank, int[] parent, int node1, int node2){
        int parent1 = findRoot(parent, node1);
        int parent2 = findRoot(parent, node2);
        if(parent1 == parent2){
            return 0;
        }
        if(rank[parent2]>rank[parent1]){
            parent[parent1] = parent2;
            rank[parent2]+=rank[parent1];
        }else{
            parent[parent2] = parent1;
            rank[parent1]+=rank[parent2];
        }
        return 1;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n^2) // n = number of edges
- Space Complexity: O(m) // m = number of nodes
