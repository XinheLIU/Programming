# Algorithm Complexity

## Time Complexity

- Best Case Time Compexity - $$\Omega(n)$$
  - upper lower bound
  - f\(n\) &gt;= cg\(n\)
- Worst Case Time Complexity - O\(n\)
  - f\(n\) &lt;= cg\(n\)
  - f\(n\) is in set O\(g\(n\)\)
- Average Case Time Complexity - $$\Theta(n)$$
  - When best case meets the worst case
  - probability weighted average
- [Amortized Time Complexity](https://en.wikipedia.org/wiki/Amortized_analysis)

Examples

- O\(1\) &lt; O\(logn\) &lt; O\(n\) &lt; O\(nlogn\) &lt; O\(n^2\) &lt; O\(n^c\)  
  &lt; O\(c^n\) &lt; O\(n!\) &lt; \infty

- f\(n\) - n is the data size , dictated by its highest order term.

#### Example-Time Complexity for Recursion

eg. F\(n\) = F\(n-1\) + F\(n-2\)

- Use recursion Tree 
  - Complexity = Height x Width
- Mathematical Solution
  - Find out recurrence formula, substitute to the first term
  - Mathematical Induction
- Master's Theorem

### Master's Theorem

[Master's Theorem](https://en.wikipedia.org/wiki/Master_theorem_%28analysis_of_algorithms%29)

For


$$
T(n) = aT(n/b) + f(n)
$$


1. $$f(n) = O(n^{log_b a - \epsilon}), T(n) = \theta(n^{log_b a})$$
2. $$f(n) = \theta(n^{log_b a}), T(n) = \theta(n^{log_b a}log n)$$
3. $$f(n) = \Omega(n^{log_b a + \epsilon}), c < 1, a(f(n)/b) \leq cf(n), T(n) = \theta(f(n))$$

eg.

- Binary Search T\(n\) = T\(n/2\) + O\(1\), c = log\_b a, O\(lgn\)
- Binary Tree Traversal T\(n\) = 2T\(n/2\) + O\(1\), c &lt; logb \_a , O\(n\)
- Merge Sort T\(n\) = 2（T/2\)+ O\(n\), c = log\_b a, O\(n log n\)
- Optimal Sorted Matrix : Akra\_Bazzi Theorem 

## Strategies to Improve time Complexity

- return to filter out unsuccessful results
- select good data structure
- cache calculation results
- Tradeoff between time and space compexity