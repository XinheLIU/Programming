# [tree](https://en.wikipedia.org/wiki/Tree_%28data_structure%29)

- Heap
- Muti-way Search Tree
  - B Tree, B+ Tree
  - 2-3 Tree, 2-3-4 Tree
- Binary Indexed Tree
- Segment Tree
- Trie

Binary Tree is **not** a tree strictly\(delete a left child, right child does not become left child\)

- [Convert tree to binary tree](http://examradar.com/converting-m-ary-tree-general-tree-binary-tree/)

## Trie

[Trie](https://en.wikipedia.org/wiki/Trie)

- Stores words in a file using common prefix
  - using space complexity to exchange time complexity
- Efficient in searching strings in a file

Common Operations

- Insert word
- Search word 
- Search prefix\(start with\)

```py
class Trie(object):

    def __init__(self): 
        self.root = {} 
        self.end_of_word = "#" 

    def insert(self, word): 
        node = self.root 
        for char in word: 
            node = node.setdefault(char, {}) 
        node[self.end_of_word] = self.end_of_word 

    def search(self, word): 
        node = self.root 
        for char in word: 
            if char not in node: 
                return False 
            node = node[char] 
        return self.end_of_word in node 

    def startsWith(self, prefix): 
        node = self.root 
        for char in prefix: 
            if char not in node: 
                return False 
            node = node[char] 
        return True
```
