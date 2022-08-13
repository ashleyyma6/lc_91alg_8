### Idea

- Keep a queue to rank element in deceding order, peek is the largest
- When meet a new larger number, poll smaller element, put new larger number
- pop peek when peek is out of the window
- add result when window is full

### Code

```java
public int[] maxSlidingWindow(int[] nums, int k) {
        int[] res = new int[nums.length-k+1];
        Deque<Integer> dq = new LinkedList<>();
        for(int i = 0; i<nums.length;i++){
            while(!dq.isEmpty() && nums[dq.peekLast()]<nums[i]){
                dq.pollLast();
            }
            dq.addLast(i);
            if(dq.peek() <= i-k){
                dq.poll();
            }
            if(i+1>=k){
                res[i+1-k] = nums[dq.peek()];
            }
        }
        return res;
    }

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(k)
