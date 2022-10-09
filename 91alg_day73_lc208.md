### Idea

### Code

```java
class Trie {
    public class TrieNode{
        HashMap<Character,TrieNode> children = new HashMap<>();
        boolean end;
        public TrieNode(){
            end = false;
        }
    }
    
    TrieNode root;
    public Trie() {
        root = new TrieNode();
    }
    
    public void insert(String word) {
        TrieNode node = root;
        for(char c : word.toCharArray()){
            if(!node.children.containsKey(c)){
                TrieNode newNode = new TrieNode();
                node.children.put(c,newNode);
                node = newNode;
            }else{
                node=node.children.get(c);
            }
        }
        node.end = true;
    }
    
    public boolean search(String word) {
        TrieNode node = root;
        for(char c:word.toCharArray()){
            if(!node.children.containsKey(c)){
                return false;
            }
            node=node.children.get(c);
        }
        return node.end;
    }
    
    public boolean startsWith(String prefix) {
        TrieNode node = root;
        for(char c:prefix.toCharArray()){
            if(!node.children.containsKey(c)){
                return false;
            }
            node = node.children.get(c);
        }
        return true;
    }
}

```

**Complexity Analysis**

- Time Complexity:O(n)
- Space Complexity:
