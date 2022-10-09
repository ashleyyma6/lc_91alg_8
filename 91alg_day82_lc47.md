### Idea

### Code

```cpp
class Solution {
public:
    
    vector<int> curr_list;
    vector<vector<int>> result;
    
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<int> visited(nums.size(), 0);
        dfs(nums, visited);
        return result;
    }

    void dfs(vector<int>& nums, vector<int>& visited){
        if(curr_list.size()==nums.size()){
            result.push_back(curr_list);
        }else{
            for(int i = 0;i<nums.size();i++){
                if(visited[i]){
                    continue;
                }else if(i>0 && nums[i]==nums[i-1] && visited[i-1]==0){
                    continue;
                }else{
                    curr_list.push_back(nums[i]);
                    visited[i]=1;
                    dfs(nums, visited);
                    curr_list.pop_back();
                    visited[i]=0;
                }  
            }
        }
    }
};

```

**Complexity Analysis**

- Time Complexity: O(n!)
- Space Complexity: O(n)
