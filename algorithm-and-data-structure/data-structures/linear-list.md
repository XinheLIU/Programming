# Linear List

- [Linear List](#linear-list)
  - [Array](#array)
  - [Linked List](#linked-list)
    - [Linked List vs. Array](#linked-list-vs-array)
  - [Skip List](#skip-list)
  - [Hash Table](#hash-table)
    - [Hash Collision)](#hash-collision)
  - [Stack](#stack)
    - [Use Stack In Engineering](#use-stack-in-engineering)
  - [Queue](#queue)
    - [Use Queue In Engineering](#use-queue-in-engineering)
  - [Bloom Filter](#bloom-filter)
  - [Cache](#cache)

## Array

Features

- continuous storage
  - CPU cache friendly
- fixed storage
  - out of memory error
    - e.g. C/C++ needs boundary check
  - dynamic allocation is expansive

Time Complexity

- Random Access O\(1\)
- Insert/Delete O\(n\)

Common Operations

- Construct
- Destruct/Clear
- Insert
- Append
- Delete
- Change
- Sort
- Search
  - getPos, getValue
- Merge two sorted array

Container Implementations

- **Dynamic Memory Allocation** could be slow
- Encapsulate common operations
- [ArrayList](http://developer.classpath.org/doc/java/util/ArrayList-source.html)\(Java\) and vector\(C++\)
  - Limit Checking
  - Implement an array with dynamic storage
  - implement a fixed memory array with dynamic insert and delete
- list in Python
  
Pros and Cons

- Pro-different storage type
  - Java ArrayList con only store _Integer, Long, not atomic types\(primitive types\) like \_int, long_
- Con-performance
  - **container is slower**
    - auto-boxing, unboxing in Java

## Linked List

[LinkedList Example](http://www.cs.cmu.edu/~adamchik/15-121/lectures/Linked%20Lists/code/LinkedList.java)

Features

Time Complexity

Singly-linked List

- Prepend O\(1\)
- Append O\(1\)
- Lookup O\(n\)
- Insert/Delete O\(1\)

Double Linked List

- Can find prev node in O\(1\)
- Insert before in O\(1\)
- [LinkedHashMap](https://github.com/openjdk-mirror/jdk7u-jdk/blob/master/src/share/classes/java/util/LinkedHashMap.java) in Java

Cyclical Linked List

- [Joseph's problem](https://en.wikipedia.org/wiki/Josephus_problem)

Implementation

Operations

- Search by index or value
- Insert a node
- Delete a node
- Reverse Linked List

Common Techniques

- **Boundary Condition** Handling careful
  - head pointer, tail pointer to NULL, back to head for circular linked list
  - empty list
  - do not lose node
- Use Prev/Dummy node to avoid special handling
  - \(Use a **sentinel** for special situation handling\)
- Special Situation Handling
  - empty linked list
  - one node
  - two node
  - head and tail

Container Implementations

[Java](http://developer.classpath.org/doc/java/util/LinkedList-source.html)

Use In Engineering

- [Cache Replacement](https://en.wikipedia.org/wiki/Cache_replacement_policies)
  - Least Frequently Used\(LFU\)
  - Least Recent Used\(LRU\)
  - FIFO

### Linked List vs. Array

Pros

- Dynamic Memory Allocation easier, Array is easier to go out of memory
- Can frequently insert in the middle
- Visibility and flexibility - do not require to know the size, can be building blocks for other data types
- Being able to model the linked based relationship directly.
  
Cons

- Random Access is hard
- Array can take advantage of CPU Cache, be visited faster
- Hard memory management, more expensive in memory
  - frequent Garbage Collection in Java
  - not friendly to cache, more memory pieces

## Skip List

[Skip List](https://en.wikipedia.org/wiki/Skip_list)

Features

Time Complexity

- Search/Look up **O\(logn\)**
- Insert/Delete O\(1\)

Implementation

[Redis](https://stackoverflow.com/questions/45115047/why-redis-sortedset-uses-skip-list-instead-of-balanced-tree)

## [Hash Table](https://en.wikipedia.org/wiki/Hash_table)

### [Hash Collision](https://en.wikipedia.org/wiki/Collision_(computer_science))

Collision resolution

- open addressing 
  - linear probing
    - the problem of clustering
  - quadratic probing
- chainging

Time Complexity

- Search O\(1\)
  - worst be O\(n\)
  - Hash Collsion
    - open hashing - use Linked list
    - closed hashing
    - other methods
- Insertion/Deletion O\(1\)
  - sometimes needs to allocate memory dynamically

Implementations

Set

- [Java](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/util/Set.html)
  - Python
  - C++
    - unordered_set

Map

- [Java](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/util/Map.html) 
- Python
  - dict
  - [collecitons](https://docs.python.org/2/library/collections.html)
- C++
  - unordered\_map

Set and Map might be implemented in non-linear forms\(Red-Black Tree, AVL Tree\)

Use In Engineering

- Associative array
- Database indexing
- cache
- set

## Stack

Last In First Out\(LIFO\) Array - Restricted Linear List

Time Complexity

- O\(1\) insert/delete
- O\(n\) Access Search

Need dynamic allocation - push operation could become O\(n\) \(Average still O\(1\) \)

Implementation

with array or with linked list

Common Operations

- Push
- Pop
- peek

Container Implementations

In production, always choose **Deque** for both stack and queue

- [Java](http://fuseyism.com/classpath/doc/java/util/Queue-source.html)
- [Python](https://docs.python.org/2/library/collections.html)

### Use Stack In Engineering

- Browser, go back, go forward
- function call stack
- Parser
  - expression calculate value

## Queue

First In First Out\(FIFO\) Array

Time Complexity

- O\(1\) insert/delete
- O\(n\) Access/Search

Implementation

- Sequence Queue-Array
  - head and tail pointer
- **Circular Queue**
  - head = tail : empty
  - \(tail + 1\)% n == head: full
- Use Linked List or Array

Operations

- enqueue
- dequeue

Container Implementation

In production, always choose **Deque** for both stack and queue

- [Java](http://fuseyism.com/classpath/doc/java/util/Queue-source.html)
- [Python](https://docs.python.org/2/library/collections.html)

### Use Queue In Engineering

Widely used in system, middleware, and frameworks

- Message Queue
- High performance queue - Disruptor
- Blocking Queue
  - a consumer - producer model
    - take will be blocked if empty
- Concurrent Queue
  - add lock on enqueue\(\), dequeue\(\) methods
  - performance - use array circular queue
    - CAS \(compare and set \) atomic operation
- Examples
  - Linux Cycle Memory
  - Java Concurrent Parallel
    - ArrayBlockingQueue

## Bloom Filter

[Bloom Filter](https://en.wikipedia.org/wiki/Bloom_filter)

- More space efficient than hashtable
- in exchange of some false positive
- no false negative

In Engineering

- Email content recognition \(SPAM, content filter\)
- Bitcoin Network
- Mapreduce
- Cache in Redis

```py
from bitarray import bitarray
import mmh3
class BloomFilter:
    def init(self, size, hash_num):
        self.size = size
        self.hash_num = hash_num
        self.bit_array = bitarray(size)
        self.bit_array.setall(0)

def add(self, s): 
    for seed in range(self.hash_num): 
        result = mmh3.hash(s, seed) % self.size 
        self.bit_array[result] = 1 

def lookup(self, s): 
    for seed in range(self.hash_num): 
        result = mmh3.hash(s, seed) % self.size 
        if self.bit_array[result] == 0: 
            return "Nope" 
    return "Probably"
```

## Cache

[Cache Replacement Policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)

Usually implemented with linear structures combinations \(eg. Linked List + HashTable\), Common forms includes

- FIFO, LIFO
- LRU Cache
- LFU Cache
- Smart Caches
  - eg. with Recommendation intelligence

```py
class LRUCache(object): 

    def __init__(self, capacity): 
        self.dic = collections.OrderedDict() 
        self.remain = capacity

    def get(self, key): 
        if key not in self.dic: 
            return -1 
        v = self.dic.pop(key) 
        self.dic[key] = v   # key as the newest one 
        return v 

    def put(self, key, value): 
        if key in self.dic: 
            self.dic.pop(key) 
        else: 
            if self.remain > 0: 
                self.remain -= 1 
            else:   # self.dic is full
                self.dic.popitem(last=False) 
        self.dic[key] = value
```