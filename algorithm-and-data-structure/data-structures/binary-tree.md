# Binary Tree

- [Binary Tree](#binary-tree)
  - [Basic Concept](#basic-concept)
    - [Properties](#properties)
    - [Time Complexity](#time-complexity)
    - [Implementation](#implementation)
    - [In Engineering](#in-engineering)
      - [Huffman Tree](#huffman-tree)
  - [Binary Search Tree](#binary-search-tree)
    - [Concept](#concept)
  - [Self-Balancing Binary Search Tree](#self-balancing-binary-search-tree)
  - [Heap/Priority Queue](#heappriority-queue)
    - [Common Forms](#common-forms)

most important recursively defined data structure

## Basic Concept

- node, parent, ancestor, brother, left-most, right-most
- leaf and branch
- edge, path
- degree: number of connections
- level: root is level 1
- depth: the depth of deepest leaf \(root is level 0\)
- height: longest path \(leaves are level 0\)
  - height of tree = height of root
- **full binary tree**
  - every node either be leaf or has two children
- **complete binary tree**
  - the bottom two layers can have nodes with less than 2 degree \(all levels filled except last\)
  - the bottom layer leafs fill from left to right
- perfect binary tree
  - all internal nodes have to children and all leaves at same level
- balanced binary tree
  - depth of left and right subtree differ by 1 or less
- extended tree
  - empty child fill by an "empty leaf"
  - E = I + 2n : E is external path sum, I is internal nodes

### Properties

- 2^i nodes on level i
- depth of k has at most 2^\(k+1\) - 1 nodes
- n0 = n2 + 1, n0 is terminal, n2 is the 2-degree node
- **Full Binary Tree Theorem**: Non empty binary tree leafs = brach nodes + 1
  - Non-empty tree subtree numbers = n + 1, n is number of nodes
- n&gt;0 nodes complete tree height roundup\( log2\(n+1\) \)\(depth -1\)

### Time Complexity

- Search, Access, Insertion, Deletion average O\(log\(N\)\)
  - worst case O\(N\)
  - to improve worst case complexity, we have
    - Red-black tree
    - Splay Tree
    - AVL Tree
    - KD Tree

### Implementation

Operations

- Traversal
  - pre-order, in-order, post-order - using stack
  - level order
  - **Morris Traversal**

### In Engineering

#### Huffman Tree

[Huffman Coding](https://en.wikipedia.org/wiki/Huffman_coding)

- prefix coding of characters - not equal length for every char
- weighted by usage frequency
  - larger the weight, closer to root
- can be implemented like a max heap

## Binary Search Tree

### Concept

- Binary Tree that
  - left child value less than node
  - right value larger than node
- be a sorted array with inorder traversal
- Search, Access, Insertion, Deletion average O\(log\(N\)\)
  - worst case O\(N\)
  - to improve worst case complexity, we have 
    - Red-black tree
    - Splay Tree
    - AVL Tree
    - KD Tree

Implementation

Operations

- Search
- Insert - maintain property
  - if find, not insert
  - when allowing duplicates - always insert under right sub-tree
    - when search, search not stop but goes down to the right
- **Delete**
  - swap with the **min in right **\(left most\) or max in left \(right most\)
  - keep as balanced as possible

Engineering Usage

- Automatic sorted data structure \(ordered map\)
- BST that support duplicates \(duplicate key values\)
  - put same data under right subtree
  - when search, continue to right till all found
- Memory index
  - external memory usually use B/B+ Tree

## Self-Balancing Binary Search Tree

[Self-Balancing Binary Search Tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)

- [AVL Tree](https://en.wikipedia.org/wiki/AVL_tree)
  - balance factor = left height - right height
  - left rotation, right rotation, left right rotation, right left rotation
- [Red-Black Tree](https://en.wikipedia.org/wiki/Red–black_tree)
  - properties
    - every node is red or black
    - root is black
    - leaves are black empty nodes\(NIL\)
    - no adjacent red nodes
    - from any node to leaves, path has equal black nodes
  - the taller subtree is less than twice the height of the other subtree
  - insert rebalance
    - left right rotate
    - change color
  - delete reblance
    - one child case
    - two children
      - child has child or not
- B/B+ Tree
- Other Self-Balancing Binary Search Tree
  - Treap
  - Splay Tree


## Heap/Priority Queue

Features

- Heap is a tree structure \(conceptually\) with ordering rule
  - if the ordered direct children &gt;= \(&lt;=\) parent, it called min \(max\) heap
  - In a binary heap, each node has at most 2 direct children. Usually modeled at a complete binary tree with 2^N -1 nodes
  - label properties: Node **i** has left child **2i**, right child **2i + 1,** parent 2 // i
- usually implemented as a **priority queue**
  - other implementations include max tree, HBLT, WBLT, MaxWBLT

### Common Forms

- Min heap
- Max Heap
- Priority Queue
- Fibonacci Heap
- Binary Heap

Implementation

Operations

- **Insert**: insert value to the next leaf, swap to the place **\(ShiftUp\) - O\(logn\)**
- **Delete**: Move the last labelled node to deleted position, Swap Down to the right order **\(ShiftDown\) - O\(logn\)**
- Construct heap - O\(n\)
  - from the first branching node, bottom up, \(i = n // 2 - 1, i-=1\) Shiftdown each element

```py
class BinHeap:
    def __init__(self):
      self.heapList = [0]
      self.currentSize = 0

    def __minChild(self,i):
      if i - 2 + 1 > self.currentSize:
        return i - 2
      else:
        if self.heapList[i-2] < self.heapList[i-2+1]:
          return i - 2
        else:
          return i - 2 + 1

    def shiftDown(self,i):
      while (i - 2) <= self.currentSize:
        mc = self.__minChild(i)
        if self.heapList[i] > self.heapList[mc]:
          self.heapList[mc], self.heapList[i] = self.heapList[i], self.heapList[mc]
        i = mc

    def shiftUp(self,i):
      while i // 2 > 0:
        if self.heapList[i] < self.heapList[i // 2]:
          self.heapList[i // 2], self.heapList[i]  = self.heapList[i], self.heapList[i // 2]
        i = i // 2

    def insert(self,k):
      self.heapList.append(k)
      self.currentSize = self.currentSize + 1
      self.shiftUp(self.currentSize)

    def delMin(self):
      retval = self.heapList[1]
      self.heapList[1] = self.heapList[self.currentSize]
      self.currentSize = self.currentSize - 1
      self.heapList.pop()
      self.shiftDown(1)
      return retval

    def buildHeap(self,alist):
      i = len(alist) // 2
      self.currentSize = len(alist)
      self.heapList = [0] + alist[:]
      while (i > 0):
        self.shiftDown(i)
        i = i - 1
```

Container Implementation

[Python](https://docs.python.org/2/library/heapq.html)