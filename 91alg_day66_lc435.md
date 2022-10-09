### Idea
- sort the intervals based on the start
- go through the intervals, check if the current start is smaller than the last interval's end time
  - Yes, overlap, the interval whose end is bigger should be removed
  - No, update and check the next interval
### Code

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if(intervals.length<2){
            return 0;
        }
        Arrays.sort(intervals, new Comparator<int[]>(){
           @Override
            public int compare(final int[] arr1, final int[] arr2){
                return Integer.compare(arr1[0],arr2[0]);
            }
        });
        int lastEnd = intervals[0][1];
        int res = 0;
        for(int i = 1; i < intervals.length; i++){
            if(intervals[i][0]<lastEnd){
                res+=1;
                if(lastEnd>intervals[i][1]){
                    lastEnd = intervals[i][1];
                }
            }else{
                lastEnd = intervals[i][1];
            }
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(nlogn)
- Space Complexity: O(1)
