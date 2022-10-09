### Idea

### Code

```java
class Solution {
    public int[] singleNumber(int[] nums) {
        int xor = 0;
        for(int num: nums){
            xor^=num;
        }
        int[] res = new int[2];
        int bit = xor & -1*xor;
        for(int num:nums){
            if((bit & num)==0){
                res[0] ^= num;
            }else{
                res[1] ^= num;
            }
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(n)
- Space Complexity: O(1)
