# Graph

### Concepts

Basic Knowledge about Graph

* Directed Graph
* Un-directed Graph

**Storage of Graph**

* Adjacency Matrix
  * Sparse matrix storage: use [adjacency list\(](https://en.wikipedia.org/wiki/Adjacency_list)key-value pair\)

#### Algorithms

* Typological Sort
* **Shortest Path**
  * [Floyd-Warshall](https://en.wikipedia.org/wiki/Floyd–Warshall_algorithm)
  * [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra's_algorithm)
    * Complexity: O\(N^2\)\), O\(NlogN\) with priority queue
    * O\(Mlog\(N\)\) with adjacency list \(M could be N^2 2 worst\)
  * [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman–Ford_algorithm)
    * Deal with edge with negative weights
    * Complexity and Optimization
      * O\(MN\)
      * early escape loop
      * Queue-optimized Bellman-Ford
* Key Path
  * [**Minimum Spanning Tree**](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
    * [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm)
    * [Prim](https://en.wikipedia.org/wiki/Prim%27s_algorithm)
* Partition
  * [Tarjan](https://en.wikipedia.org/wiki/Tarjan%27s_strongly_connected_components_algorithm)
* [Bipartie Graph](https://en.wikipedia.org/wiki/Bipartite_graph)
  * [Maximum Bipartie Matching](https://www.geeksforgeeks.org/maximum-bipartite-matching/)
  * [Hungarian Algorithm](https://en.wikipedia.org/wiki/Hungarian_algorithm)
* Maximum Flow Problem

---

### Union Find

Count Number of Trees in a forest/connected components in a graph \(Disjoint Set\)

* Init/makeSet
  * Parent notation - use array
    * father\[i\] refers to i's parent
* Find 
  * find the root of a node
  * path compression
* Union
  * father\[root\_A_\] = root\_B_

```py
def init(p): 
    # for i = 0 .. n: p[i] = i; 
    p = [i for i in range(n)] 

def union(self, p, i, j): 
    p1 = self.parent(p, i) 
    p2 = self.parent(p, j) 
    p[p1] = p2 

def parent(self, p, i): 
    root = i 
    while p[root] != root: 
        root = p[root] 
    while p[i] != i: # path compression
        x = i; i = p[i]; p[x] = root 
    return root
```

```java
class UnionFind { 
    private int count = 0; 
    private int[] parent; 
    public UnionFind(int n) { 
        count = n; 
        parent = new int[n]; 
        for (int i = 0; i < n; i++) { 
            parent[i] = i;
        }
    } 
    public int find(int p) { 
        while (p != parent[p]) { 
            parent[p] = parent[parent[p]]; 
            p = parent[p]; 
        }
        return p; 
    }
    public void union(int p, int q) { 
        int rootP = find(p); 
        int rootQ = find(q); 
        if (rootP == rootQ) return; 
        parent[rootP] = rootQ; 
        count--;
    }
}
```



