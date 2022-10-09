### Idea
- brute force
- Check every time, count their bits, add match to result list.  
### Code

```java
class Solution {
    public List<String> readBinaryWatch(int turnedOn) {
        List<String> result = new ArrayList<>();
        for(int hour = 0; hour<12;hour++){
            for(int min = 0; min<60;min++){
                if(Integer.bitCount(min)+Integer.bitCount(hour)==turnedOn){
                    if(min<10){
                        result.add(Integer.toString(hour)+":"+"0"+Integer.toString(min));
                    }else{
                        result.add(Integer.toString(hour)+":"+Integer.toString(min));
                    }
                }
            }
        }
        return result;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(60+12)xO(1) = O(1)
- Space Complexity: O(1)
