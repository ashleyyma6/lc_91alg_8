### Idea
- Count character frequency of t, and number of unique characters in t
- Move right pointer, reduce the frequency by one, and reduce the unique character number by one when frequency is cleared. 
- Move left pointer when the left pointer character is cleared. 
- return the substring when all character frequency is cleared, or the current window is smaller than the previous
### Code

```java
class Solution {
    public String minWindow(String s, String t) {
        if(t.length()==0){
            return "";
        }
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();
        int[] countT = new int[256];
        
        int countTchars = 0;
        for(char c: tArr){
            countT[c]++;
        }
        for(int i:countT){
            if(i!=0){
                countTchars++;
            }
        }
        
        String res = "";
        int left = 0;
        int right = 0;
        for(right=0;right<s.length();right++){
            if(countT[sArr[right]]==1){
                countTchars--;
            }
            countT[sArr[right]]--;
                   
            while(left<s.length() && countT[sArr[left]]<0){
                countT[sArr[left]]++;
                left++;
            }
            if(countTchars==0){
                if(res == "" || res.length()>right-left+1){
                    res = s.substring(left,right+1);
                }
            }
        }
        return res;
    }
}
```

**Complexity Analysis**

- Time Complexity: O(m+n)
- Space Complexity: O(m+n)
