
# Searching Algorithms

- [Searching Algorithms](#searching-algorithms)
  - [Binary Search](#binary-search)
    - [key points](#key-points)
  - [Breath-First Search\(BFS\) and Depth-First-Search\(DFS\)](#breath-first-searchbfs-and-depth-first-searchdfs)
    - [Double-direction BFS\(DBFS\) : expand from start point and end point](#double-direction-bfsdbfs--expand-from-start-point-and-end-point)
  - [Depth-First Search(DFS)](#depth-first-searchdfs)
    - [Heuristic Seach](#heuristic-seach)

## Binary Search

```py
# Template 1
left, right = 0, len(array) - 1 
while left <= right: 
      mid = (left + right) / 2 
      if array[mid] == target: 
            # find the target!! 
            break or return result 
      elif array[mid] < target: 
            left = mid + 1 
      else: 
            right = mid - 1

# Template 2
if len(A) == 0 or A == None:
    return -1

start,end = 0, len(A) - 1

if target < A[start] or target > A[end]:
    return -1

while start + 1 < end:
    mid = start + (end - start) >> 1
    if target == A[mid]:
        return mid
    elif target > A[mid]:
        start = mid
    else:
        end = mid

if target == A[end]:
    return end
elif target == A[start]:
    return start
else:
    return -1
```

### key points

* while loop condition
  * l &lt;= r: always return in the loop
  * l + 1 &lt;r: needs post-processing, left an right do not meet
* mid
  * use l + \(r-l\) &gt;&gt; 1 to be faster and avoid overflow in common languages
* update left and right pointer
  * l &lt;= r: use +1, -1 to avoid dead loop

  * l + 1 &lt; r: use l = mid, r = mid

Assumptions

* only works for array\(storage supports random access and consecutive\)
* data is sorted
* data is bounded\(usually\)

Use In Engineering

The existence of sorted data structures\(tree, hash tables\) with fast search make binary search become most useful in searching approximation values \(eg. first/last occurrence of a value/in a range\)

- search location range of IP adrress


## Breath-First Search\(BFS\) and Depth-First-Search\(DFS\)

Search on a graph

```py
def BFS(graph, start, end):

    queue = [] 
    queue.append([start]) 
    visited.add(start)

    while queue: 
        node = queue.pop() 
        visited.add(node)

        process(node) 
        nodes = generate_related_nodes(node) 
        queue.push(nodes)

    # other processing work
```

- Complete: can guarantee the solution to be found
- Storage cost high

Imprmprovements

### Double-direction BFS\(DBFS\) : expand from start point and end point

  ```py
  def BFS(graph, start, end):
      front, back = [start],[end]
      visited.add(start)

      while front and back: 
          # choose the short one to sarch
          queue = front if len(front) < back else back

          node = queue.pop() 
          visited.add(node)

          process(node) 
          nodes = generate_related_nodes(node) 
          queue.push(nodes)
  ```

* Preprocess and store

## Depth-First Search(DFS)

```py
# recursive
visited = set() 

def dfs(node, visited):
    if node in visited: # terminator
        # already visited 
        return 

        visited.add(node) 

        # process current node here. 
        ...
        for next_node in node.children(): 
            if not next_node in visited: 
                dfs(next_node, visited)

# iterative

def DFS(self, tree): 

    if tree.root is None: 
        return [] 

    visited, stack = [], [tree.root]

    while stack: 
        node = stack.pop() 
        visited.add(node)

        process (node) 
        nodes = generate_related_nodes(node) 
        stack.push(nodes) 

    # other processing work
```

* Applicable to most any problems
* storage cost low

Applications

* [Flood Fill](https://en.wikipedia.org/wiki/Flood_fill)

Improvements

### Heuristic Seach

A\* algorithm: use Priority Queue

```py
def AstarSearch(graph, start, end):
    pq = collections.priority_queue() # Valuation function: key for performance
    pq.append([start]) 
    visited.add(start)

    while pq: 
        node = pq.pop() # can we add more intelligence here ?
        visited.add(node)

        process(node) 
        nodes = generate_related_nodes(node) 
        unvisited = [node for node in nodes if node not in visited]
        pq.push(unvisited)
```

* key is [similarity measures](https://dataaspirant.com/2015/04/11/five-most-popular-similarity-measures-implementation-in-python/)