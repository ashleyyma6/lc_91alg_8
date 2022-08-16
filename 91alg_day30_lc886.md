### Idea
<<<<<<< HEAD
- BFS
- A dictionary to put person and a list of people dislikes
- Traverse 2D array dislikes to fill the dictionary, create a relationship enrty for everyone
- A queue to save person that have not check yet
- A color array contains: 1, -1 to mark people in different group. A dislikes B, A must have different mark with B
- Traverse the dictionary, mark person different color, add the unchecked person into a queue. If meet mark confict, return false. If all checked, return true. 
- https://www.youtube.com/watch?v=0ACfAqs8mm0

### Code

```java
    public boolean possibleBipartition(int n, int[][] dislikes) {
        Map<Integer, List<Integer>> graph = new HashMap<>();
        for(int[] disklike:dislikes){
            List<Integer> curr_list;
            if(graph.containsKey(disklike[0])){
                curr_list = graph.get(disklike[0]);
            }else{
                curr_list = new ArrayList<>();
            }
            curr_list.add(disklike[1]);
            graph.put(disklike[0],curr_list);
            if(graph.containsKey(disklike[1])){
                curr_list = graph.get(disklike[1]);
            }else{
                curr_list = new ArrayList<>();
            }
            curr_list.add(disklike[0]);
            graph.put(disklike[1],curr_list);
        }
        Queue<Integer> queue = new LinkedList<>();
        int[] colors = new int[n+1];
        for(int i = 0;i<n;i++){
            if(colors[i]==0){
                colors[i] = 1;
                queue.add(i);
                while(!queue.isEmpty()){
                    int curr = queue.poll();
                    List<Integer> curr_list = graph.get(curr);
                    if(curr_list!=null){
                        for(Integer check:curr_list){
                            if(colors[curr]==colors[check]){
                                return false;
                            }
                            if(colors[check]==0){
                                colors[check] = -colors[curr];
                                queue.add(check);
                            }
                        }
                    }
                }
            }
        }
        return true;
        
    }

```

**Complexity Analysis**

- Time Complexity:O(e+n) // e = pairs in dislikes
- Space Complexity: O(e+n)
