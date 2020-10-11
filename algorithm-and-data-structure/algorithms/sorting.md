# Sorting

## Internal Sorting

* O\(n^2\)
  * Bubble Sort
    * Stable
  * Insertion Sort
    * Shell Sort: split into sub groups then do a final sweep
      * Hibbard Gap Sequence \(O\(n^3/2\)\)
    * Stable
  * Selection Sort
    * not stable
* O\(nlogn\)
  * Merge Sort
    * optimization
      * selection sort at smaller list
      * R.Sedgewick optimization: flip the right array, simplify the boundary check, when merge, left and right are "back to back"
      * Complexity T\(n\) = 2T\(n/2\) + cn
  * Quick Sort
    * divide and conquer : pivoting
    * randomized quick sort\(RQS\): select pivoting randomly to improve efficiency
    * Complexity T\(n\) = T\(i\) + T\(n-1-i\) + cn
      * worst case O\(n^2\)
      * average O\(nlogn\)
    * not stable
  * Heap Sort
* O\(n\)
  * Distribution Sort/Bucket Sort
    * Radix Sort
    * need knowledge about the sequence \(range\)

## External Sorting

Large object sorting finished in external storage

## Sample Questions

1. If index in internal memory and data in external memory, swap data is very expensive, which sort to use?
   1. Selection Sort
2. A library has many shelves, some books are misreplaced \(not far\), which sort to use
   1. Insertion Sort
3. Why O\(nlogn\) is the lower bound of comparison based algo
   1. n! possible orders, for x!=y half x &gt;y, half x &lt; y, O\(log\(n!\)\) = O\(nlog\(n\)\) -&gt; Sterling's formula
4. What algo to use when you have 1MB/1GB/1TB data
   1. external sort - external merge sort
5. Maximum number of comparison in selection sort
   1. n\(n-1\)/2
6. Optimize
   1. insertion sort - binary search