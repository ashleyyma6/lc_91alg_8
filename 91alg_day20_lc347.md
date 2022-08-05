### Idea
- Hash table {k:frequency}, count all numbers
- Push hash table entry to a priority queue, keep the last k elements
- Move queue entries to integer ArrayList, transfer to int array

### Code

```java
public int[] topKFrequent(int[] nums, int k) {
        HashMap<Integer,Integer> map = new HashMap();
        for(int num:nums){
            if(map.containsKey(num)){
                map.put(num, map.get(num)+1);
            }else{
                map.put(num, 1);
            }
        }
        PriorityQueue<Integer> heap = new PriorityQueue<Integer>((n1, n2)->map.get(n1)-map.get(n2));
        for(int n : map.keySet()){
            heap.add(n);
            if(heap.size()>k){
                heap.poll();
            }
        }
        ArrayList<Integer> arr_list = new ArrayList();
        while(!heap.isEmpty()){
            arr_list.add(heap.poll());
        }
        Collections.reverse(arr_list);
        int[] res = arr_list.stream().mapToInt(Integer::intValue).toArray();
        return res;
    }
```

**Complexity Analysis**

- Time Complexity: O(n)+O(nlogn)+O(n) = O(nlogn)
- Space Complexity: O(n)+O(n)+O(n) = O(n)
