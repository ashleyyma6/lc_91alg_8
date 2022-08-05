### Idea
- Left, right pointer, Hash table save index of a character
- Move right pointer, if character exists in table, update left pointer forward, update new index for right pointer character, update max length
### Code

```java
 public int lengthOfLongestSubstring(String s) {
        if(s.length()<2){
            return s.length();
        }
        HashMap<Character,Integer> map = new HashMap<>();
        int left=-1;
        int result = 0;
        for(int i = 0;i<s.length();i++){
            char current  = s.charAt(i);
            if(map.containsKey(current)){
                left = Math.max(map.get(current),left);
            }
            map.put(current,i);
            result = Math.max(result,i-left);
        }
        return result;
    }

```

**Complexity Analysis**

- Time Complexity:O(n)
- Space Complexity:O(n)
