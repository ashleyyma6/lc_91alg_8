### Idea

- Find the length of word, as unit, the length of the string composed of words
- Two Hash tables {word: frequency}
- Count the word in words and its appearance times
- One pointer to mark the start of the string, an inner pointer to check words in the string, count appearance times
  - Break when meet word not in words, when appearance time exceeds
  - Add result when the substring length match target length

### Code

```java

 HashMap<String, Integer> count_words = new HashMap<>();
        for(String word:words){
            if(count_words.containsKey(word)){
                count_words.replace(word, count_words.get(word)+1);
            }else{
                count_words.put(word,1);
            }
        }

        int word_unit = words[0].length();
        int string_length = word_unit * words.length;

        ArrayList<Integer> result = new ArrayList<>();

        for(int i = 0; i<s.length()-string_length+1;i++){
            HashMap<String, Integer> count = new HashMap<>();
            for(int j = i; j<i+string_length;j+=word_unit){
                String current_word = s.substring(j,j+word_unit);
                if(!count_words.containsKey(current_word)){
                    break;
                }else{
                     if(count.containsKey(current_word)){
                        count.replace(current_word, count.get(current_word)+1);
                        if(count.get(current_word) > count_words.get(current_word)){
                            break;
                        }
                    }else{
                        count.put(current_word,1);
                    }
                    if((j-i)==(string_length-word_unit)){
                        result.add(i);
                    }
                }
            }
        }
        return result;
    }

```

**Complexity Analysis**

- Time Complexity: O(mn) // m = s.length, n = words.length
- Space Complexity: O(n)
