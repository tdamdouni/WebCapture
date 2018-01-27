# Big-O Complexity Chart

_Captured: 2017-09-05 at 11:27 from [bigocheatsheet.com](http://bigocheatsheet.com/)_

## Common Data Structure Operations

Data Structure Time Complexity Space Complexity

Average Worst Worst

Access Search Insertion Deletion Access Search Insertion Deletion

[Array](http://en.wikipedia.org/wiki/Array_data_structure)
`Θ(1)`
`Θ(n)`
`Θ(n)`
`Θ(n)`
`O(1)`
`O(n)`
`O(n)`
`O(n)`
`O(n)`

[Stack](http://en.wikipedia.org/wiki/Stack_\(abstract_data_type\))
`Θ(n)`
`Θ(n)`
`Θ(1)`
`Θ(1)`
`O(n)`
`O(n)`
`O(1)`
`O(1)`
`O(n)`

[Queue](http://en.wikipedia.org/wiki/Queue_\(abstract_data_type\))
`Θ(n)`
`Θ(n)`
`Θ(1)`
`Θ(1)`
`O(n)`
`O(n)`
`O(1)`
`O(1)`
`O(n)`

[Singly-Linked List](http://en.wikipedia.org/wiki/Singly_linked_list#Singly_linked_lists)
`Θ(n)`
`Θ(n)`
`Θ(1)`
`Θ(1)`
`O(n)`
`O(n)`
`O(1)`
`O(1)`
`O(n)`

[Doubly-Linked List](http://en.wikipedia.org/wiki/Doubly_linked_list)
`Θ(n)`
`Θ(n)`
`Θ(1)`
`Θ(1)`
`O(n)`
`O(n)`
`O(1)`
`O(1)`
`O(n)`

[Skip List](http://en.wikipedia.org/wiki/Skip_list)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(n)`
`O(n)`
`O(n)`
`O(n)`
`O(n log(n))`

[Hash Table](http://en.wikipedia.org/wiki/Hash_table)
`N/A`
`Θ(1)`
`Θ(1)`
`Θ(1)`
`N/A`
`O(n)`
`O(n)`
`O(n)`
`O(n)`

[Binary Search Tree](http://en.wikipedia.org/wiki/Binary_search_tree)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(n)`
`O(n)`
`O(n)`
`O(n)`
`O(n)`

[Cartesian Tree](https://en.wikipedia.org/wiki/Cartesian_tree)
`N/A`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`N/A`
`O(n)`
`O(n)`
`O(n)`
`O(n)`

[B-Tree](http://en.wikipedia.org/wiki/B_tree)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(n)`

[Red-Black Tree](http://en.wikipedia.org/wiki/Red-black_tree)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(n)`

[Splay Tree](https://en.wikipedia.org/wiki/Splay_tree)
`N/A`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`N/A`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(n)`

[AVL Tree](http://en.wikipedia.org/wiki/AVL_tree)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(log(n))`
`O(n)`

[KD Tree](http://en.wikipedia.org/wiki/K-d_tree)
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`Θ(log(n))`
`O(n)`
`O(n)`
`O(n)`
`O(n)`
`O(n)`

## Array Sorting Algorithms

Algorithm Time Complexity Space Complexity

Best Average Worst Worst

[Quicksort](http://en.wikipedia.org/wiki/Quicksort)
`Ω(n log(n))`
`Θ(n log(n))`
`O(n^2)`
`O(log(n))`

[Mergesort](http://en.wikipedia.org/wiki/Merge_sort)
`Ω(n log(n))`
`Θ(n log(n))`
`O(n log(n))`
`O(n)`

[Timsort](http://en.wikipedia.org/wiki/Timsort)
`Ω(n)`
`Θ(n log(n))`
`O(n log(n))`
`O(n)`

[Heapsort](http://en.wikipedia.org/wiki/Heapsort)
`Ω(n log(n))`
`Θ(n log(n))`
`O(n log(n))`
`O(1)`

[Bubble Sort](http://en.wikipedia.org/wiki/Bubble_sort)
`Ω(n)`
`Θ(n^2)`
`O(n^2)`
`O(1)`

[Insertion Sort](http://en.wikipedia.org/wiki/Insertion_sort)
`Ω(n)`
`Θ(n^2)`
`O(n^2)`
`O(1)`

[Selection Sort](http://en.wikipedia.org/wiki/Selection_sort)
`Ω(n^2)`
`Θ(n^2)`
`O(n^2)`
`O(1)`

[Tree Sort](https://en.wikipedia.org/wiki/Tree_sort)
`Ω(n log(n))`
`Θ(n log(n))`
`O(n^2)`
`O(n)`

[Shell Sort](http://en.wikipedia.org/wiki/Shellsort)
`Ω(n log(n))`
`Θ(n(log(n))^2)`
`O(n(log(n))^2)`
`O(1)`

[Bucket Sort](http://en.wikipedia.org/wiki/Bucket_sort)
`Ω(n+k)`
`Θ(n+k)`
`O(n^2)`
`O(n)`

[Radix Sort](http://en.wikipedia.org/wiki/Radix_sort)
`Ω(nk)`
`Θ(nk)`
`O(nk)`
`O(n+k)`

[Counting Sort](https://en.wikipedia.org/wiki/Counting_sort)
`Ω(n+k)`
`Θ(n+k)`
`O(n+k)`
`O(k)`

[Cubesort](https://en.wikipedia.org/wiki/Cubesort)
`Ω(n)`
`Θ(n log(n))`
`O(n log(n))`
`O(n)`
