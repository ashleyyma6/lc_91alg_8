### Idea

### Code

```java
class Solution {
    public boolean canIWin(int maxChoosableInteger, int desiredTotal) {
        if(maxChoosableInteger>=desiredTotal){
            return true;
        }
        int choose_sum = maxChoosableInteger*(maxChoosableInteger+1)/2;
        if(choose_sum < desiredTotal){
            return false;
        }

        HashMap<Integer, Boolean> seen = new HashMap<>();
        return canwin(maxChoosableInteger,desiredTotal,0,seen);
    }
    public boolean canwin(int maxChoosable, int remainder, int current, HashMap<Integer, Boolean> seen){
        if(seen.containsKey(current)){
            return seen.get(current);
        }
        
        for(int i = 0;i < maxChoosable; i++){
            int curr = (1<<i);
            if((curr&current)==0){
                int nextChoice = curr|current;
                if(remainder<=i+1||!canwin(maxChoosable,remainder-(i+1), nextChoice,seen)){
                    seen.put(current, true);
                    return true;
                }
            }

        }
        seen.put(current,false);
        return false;
        
    }
}

```

**Complexity Analysis**

- Time Complexity:O(n^n)
- Space Complexity: O(n)
