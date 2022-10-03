### Idea

### Code

```cpp
class Solution {
public:
    int t;
    vector<int> curr_list;
    vector<int> nums;
    vector<vector<int>> result;

    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(),candidates.end());
        this->nums=candidates;
        this->t = target;
        dfs(0,0);
        return result;
    }
    void dfs(int curr, int start){
        if(curr==t){
            result.push_back(curr_list);
        }else if(curr<t){
            for(int i = start;i<nums.size();i++){
                if(i>start && nums[i]==nums[i-1]){
                    continue;
                }
                if(curr+nums[i]<=t){
                    curr_list.push_back(nums[i]);
                    dfs(curr+nums[i],i+1);
                    curr_list.pop_back();
                }else{
                    break;
                }

            }
        }else{
            return;
        }
    }
};

```

**Complexity Analysis**

- Time Complexity:O(2^n)
- Space Complexity: O(n)
