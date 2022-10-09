### Idea
- max heap

### Code

```cpp
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        priority_queue<int> heap(nums.begin(), nums.end());
        for(int i = 0;i<k-1;i++){
            heap.pop();
        }
        return heap.top();      
    }
};
```

**Complexity Analysis**

- Time Complexity: O(logn+k)
- Space Complexity: O(n)
