### Idea
- Find the length of word, as unit
- Left & right pointer, move right pointer
- Hash table {word: start index}
- Move right pointer, If current unit word is in words, update left pointer, right pointer keep move:
  - meet a new word, check if in words & hash table:
    - If in words & not in hash table: add to hash table
      - if the key set size = the size of words, meet all three, push left pointer to result arr, update left to next unit meet
    - If in words & in hash table: word repeat - left update to the next unit of previous one
    - IF not in words: update left to next unit
### Code

```java

public List<Integer> findSubstring(String s, String[] words) {
        int word_unit = words[0].length();
        int left = -1;
        int right =  0;
        for(int right = 0; right<s.length(); right++){
            
        }
    }

```

**Complexity Analysis**

- Time Complexity:
- Space Complexity: