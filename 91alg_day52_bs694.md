### Idea
- BFS start from the target node in the graph, check current levelnodes' connected nodes 
- put the new nodes into the list for next level check, return when reach the target node again
- The level depth of the first time reach target node again is the result
### Code

```java
class Solution {
    public int solve(int[][] graph, int target) {

        if(graph.length<target || graph[target].length==0){
            return -1;
        }
        Queue<Integer> list = new ArrayDeque<>();
        Set<Integer> visited = new HashSet<>();
        list.add(target);
        int result = 0;
        while(!list.isEmpty()){
            result+=1;
            Queue<Integer> newList = new ArrayDeque<>();
            int n = list.size();
            for(int i =0; i<n;i++){
                int curr = list.poll().intValue();
                for(int j:graph[curr]){
                    if(j==target){
                        return result;
                    }
                    if(visited.contains(j)){
                        continue;
                    }
                    visited.add(j);
                    newList.add(j);
                }
            }
            list = newList;
        }
        return -1;

    }
}

```

**Complexity Analysis**

- Time Complexity: O(m*n)
- Space Complexity: O(m*n)
