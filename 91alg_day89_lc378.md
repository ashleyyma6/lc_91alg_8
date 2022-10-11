### Idea
- a max heap of size k
### Code

```cpp

class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        priority_queue<int, vector<int>, less<int>> heap;
        for(vector<int> v:matrix){
           for(int i:v){
               if(heap.size()<k){
                   heap.push(i);
               }else if(heap.top()>i){
                   heap.pop();
                   heap.push(i);
               }
           }
        }
        return heap.top();
    }
};

```

**Complexity Analysis**

- Time Complexity:O(n^2)
- Space Complexity: O(k)
