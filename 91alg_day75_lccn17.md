### Idea

### Code

```java
class Solution {
    public class Trie{
        public class TrieNode{
            String end;
            HashMap<Character, TrieNode> children;
            TrieNode(){
                children = new HashMap<>();
                end = null;
            }
        }
        TrieNode root;
        public Trie(String[] words){
            root = new TrieNode();
            for(String word: words){
                TrieNode node = root;
                for(char c: word.toCharArray()){
                    if(!node.children.containsKey(c)){
                        node.children.put(c, new TrieNode());
                    }
                    node=node.children.get(c);
                }
                node.end = word;
            }
        }
        public List<String> search(String str){
            TrieNode node = root;
            List<String> res = new ArrayList<>();
            for(char c:str.toCharArray()){
                if(!node.children.containsKey(c)){
                    break;
                }
                node = node.children.get(c);
                if(node.end!=null){
                    res.add(node.end);
                }   
            }
            return res;
        }
    }

    public int[][] multiSearch(String big, String[] smalls) {
        Trie t = new Trie(smalls);
        Map<String, List<Integer>> find = new HashMap<>();
        for(int i = 0; i < big.length();i++){
            List<String> matches = t.search(big.substring(i));
            for(String word:matches){
                if(!find.containsKey(word)){
                    find.put(word, new ArrayList<>());
                }
                find.get(word).add(i);
            }
        }
        int[][] res = new int[smalls.length][];
        for(int i = 0;i<smalls.length;i++){
            List<Integer> list = find.get(smalls[i]);
            if(list==null){
                res[i]=new int[0];
                continue;
            }
            int size = list.size();
            res[i] = new int[size];
            for(int j = 0;j<size;j++){
                res[i][j] = list.get(j);
            }
        }
        return res;
    }
}

```

**Complexity Analysis**

- Time Complexity: O(m*n) // m = big.length, n = smalls.length()
- Space Complexity: O(n*k) //k is the longest string length in smalls
