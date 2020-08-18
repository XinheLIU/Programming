/

p* ```py
  def recursion(level, param1, param2, ...): 
      # recursion terminator 
      if level > MAX_LEVEL: 
         process_result 
         return 

      # process logic in current level 
      process(level, data...) 

      # drill down 
      self.recursion(level + 1, p1, ...) 

      # reverse the current level status if needed
  ```

# Divide and Counquer

```py
def divide_conquer(problem, param1, param2, ...): 
  # recursion terminator 
  if problem is None: 
    print_result 
    return 

  # prepare data 
  data = prepare_data(problem) 
  subproblems = split_problem(problem, data) 

  # conquer subproblems 
  subresult1 = self.divide_conquer(subproblems[0], p1, ...) 
  subresult2 = self.divide_conquer(subproblems[1], p1, ...) 
  subresult3 = self.divide_conquer(subproblems[2], p1, ...) 
  …

  # process and generate the final result 
  result = process_result(subresult1, subresult2, subresult3, …)

  # revert the current level states
```

---

# Back Tracking

* Recursion
* Depth-First, Breath-First

Can combine with Dynamic Programming

---

# Greedy Algorithm

[Greedy Algorithm ](https://en.wikipedia.org/wiki/Greedy_algorithm)is useful in solving optimization problems when a local optimum in each stage is useful in finding a global optimum. \(usually, not path dependency\)

### Typical problems

* backpack problem
* coin change 
* [Huffman coding](https://en.wikipedia.org/wiki/Huffman_coding)

---

# Dynamic Programing

[Knapsack Problem](https://en.wikipedia.org/wiki/Knapsack_problem)

* Cut problem into **Sub-problems** \( same calculation, smaller size\)
* Clarify **State Variables**: the solution is determined by a set of variables
  * must have two characteristics
    * optimized sub-structure: the optimal solution contains the optimal solutions of sub-problems
    * Markov Process: no after-effect property: only related to state variable at t, not t-1,...,t-n
* Find State-Transfer formula



