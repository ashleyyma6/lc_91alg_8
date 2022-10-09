### Idea
- count & save character frequency of string p in an array
- left, right pointer, update the character frequency between left and right, compare to string p 
### Code

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        int[] countP = new int[26];
        char[] pArr = p.toCharArray();
        for(char c:pArr){
            countP[c-'a']++;
        }
        int[] countS = new int[26];
        char[] sArr = s.toCharArray();
        int left = 0;
        int right = 0;
        List<Integer> result = new ArrayList<>();
        while(right<s.length()){
            countS[sArr[right]-'a']++;
            if(right-left+1>p.length()){
                countS[sArr[left]-'a']--;
                left++;
            }
            if(right-left+1==p.length() && isEqual(countP, countS)){
               result.add(left);
            }
            right++;
        }
        return result;
    }
    public boolean isEqual(int[] p, int[] s){
         for(int i =0;i<26;i++){
            if(p[i]!=s[i]){
                return false;
            }
         }
        return true;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(s+p) // s = s.length. p = p.length
- Space Complexity:O(s+p)
