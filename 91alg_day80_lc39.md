### Idea

### Code

```cpp
class Solution {
public:
    vector<int> nums;
    vector<vector<int>> result;
    vector<int> list;
    int t;
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        this->t = target;
        this->nums = candidates;
        dfs(0,0);
        return result;
    }
    
    void dfs(int curr_sum, int start){
        if(curr_sum == t){
            result.push_back(list);
        }else if(curr_sum<t){
            for(int i = start; i<nums.size();i++){
                if((curr_sum+nums[i])<=t){
                    list.push_back(nums[i]);
                    dfs(curr_sum+nums[i],i);
                    list.pop_back();
                }else{
                    break;
                }
            }
        }
    }
};

```

**Complexity Analysis**

- Time Complexity: O(n) // num of nodes
- Space Complexity: O(m) // height of decision tree
