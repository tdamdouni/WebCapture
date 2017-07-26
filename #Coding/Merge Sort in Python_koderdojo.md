# Merge Sort in Python

_Captured: 2016-10-19 at 15:57 from [www.koderdojo.com](http://www.koderdojo.com/blog/merge-sort-in-python-using-pythonista-3-on-ipad-pro)_

[Koder Dojo](/)

____

# Merge Sort in Python Using Pythonista 3 on iPad Pro

In one of my algorithms courses I just started learning **divide and conquer
algorithms** and the first example provided by my instructor is **Merge
Sort**. My instructor describes Merge Sort using pseudo code, but
unapologetically leaves out a lot of details like merging, etc. This is
perfect for me since in addition to algorithms I am also learning Python and
this gives me a chance to write a Merge Sort using Python for the first time.

## Merge Sort in Python

Merge Sort breaks the problem of sorting a list into smaller, similar
subproblems. It recursively breaks the list in half, sorts those smaller
lists, and merges them together to eventually form the original list in sorted
order.

This sounds like a pretty cool algorithm to tackle so I open up Pythonista 3
on my iPad Pro and begin creating a function that takes as its only input, a
list. To make this simple, I am going to assume this list is made up of
integers only.

Here is my initial solution for Merge Sort in Python. The spacing is a bit off
due to copy and paste.

    
    
    def merge_sort(integers):
    	""" Returns a sorted list of integers
    	
    	>>> merge_sort([])
    	[]
    	>>> merge_sort([1])
    	[1]
    	>>> merge_sort([2, 1])
    	[1, 2]
    	>>> merge_sort([2, 1, 4])
    	[1, 2, 4]
    	>>> merge_sort([2, 1, 4, 3])
    	[1, 2, 3, 4]
    	>>> merge_sort([2, 15, 89, 27, 16, 34, 120, 65, 51, 1, 54, 72, 210, 27])
    	[1, 2, 15, 16, 27, 27, 34, 51, 54, 65, 72, 89, 120, 210]
    	"""
    
    
    	length = len(integers)
    	
    	# base case
    	if (length < 2):
    		return integers
    
            # split the list in half and sort each half
    	midpoint = length // 2
    	left = merge_sort(integers[:midpoint])
    	right = merge_sort(integers[midpoint:])
    
            # merge the two sorted lists into 1 larger list
    	merged_integers = []
    
            # keep track of position in left and right lists
    	left_index = 0
    	right_index = 0
    	
            # perform merge. take smaller of left-most
            # integer in each list and place in merged list.
            # stop when either list is empty and append
            # the remaining items from the non-empty list
    	while True:
    		if left[left_index] <= right[right_index]:
    			merged_integers.append(left[left_index])
    			left_index += 1
    		else:
    			merged_integers.append(right[right_index])
    			right_index += 1
    			
    		if left_index > len(left) - 1:
    			merged_integers += right[right_index:]
    			break
    			
    		if right_index > len(right) - 1:
    			merged_integers += left[left_index:]
    			break
    			
    	return merged_integers
    

Once I confirmed my solution worked, I did a bit of searching to see if I was
even close and if there were some obvious optimizations. I found a post on
[stackoverflow](http://stackoverflow.com/questions/18761766/mergesort-python)
that offered a more elegant solution to ending the **while** loop and merging
the remaining integers once one of the lists became empty. I changed the
**while** loop and the bit of code at the end. This provides a more meaningful
finish to the **while** loop, less comparisons in the loop, and a simple merge
at the end that merges both lists, even the empty one. I hadn't thought about
merging the empty list as well, which is unnecessary, but not problematic.

    
    
    	# perform merge. take smaller of left-most
    	# integer in each list and place in merged list.
    	# stop when finished adding integers from either list.
    	while left_index < len(left) and right_index < len(right):
    		if left[left_index] <= right[right_index]:
    			merged_integers.append(left[left_index])
    			left_index += 1
    		else:
    			merged_integers.append(right[right_index])
    			right_index += 1
    	
    	# add any remaining items from the non-empty list
    	merged_integers += left[left_index:]
    	merged_integers += right[right_index:]

Here is the final result of programming Merge Sort in Python with a tad bit of
help from the Internet.

    
    
    def merge_sort(integers):
    	""" Returns a sorted list of numbers
    	
    	>>> merge_sort([])
    	[]
    	>>> merge_sort([1])
    	[1]
    	>>> merge_sort([2, 1])
    	[1, 2]
    	>>> merge_sort([2, 1, 4])
    	[1, 2, 4]
    	>>> merge_sort([2, 1, 4, 3])
    	[1, 2, 3, 4]
    	>>> merge_sort([2, 15, 89, 27, 16, 34, 120, 65, 51, 1, 54, 72, 210, 27])
    	[1, 2, 15, 16, 27, 27, 34, 51, 54, 65, 72, 89, 120, 210]
    	"""
    
    
    	length = len(integers)
    	
    	# base case
    	if (length < 2):
    		return integers
    	
    	# split the list in half and sort each half
    	midpoint = length // 2
    	left = merge_sort(integers[:midpoint])
    	right = merge_sort(integers[midpoint:])
    
    	# merge the two sorted lists into 1 larger list
    	merged_integers = []
    	
    	# keep track of position in left and right lists
    	left_index = 0
    	right_index = 0
    
    	# perform merge. take smaller of left-most
    	# integer in each list and place in merged list.
    	# stop when finished adding integers from either list.
    	while left_index < len(left) and right_index < len(right):
    		if left[left_index] <= right[right_index]:
    			merged_integers.append(left[left_index])
    			left_index += 1
    		else:
    			merged_integers.append(right[right_index])
    			right_index += 1
    	
    	# add any remaining items from the non-empty list
    	merged_integers += left[left_index:]
    	merged_integers += right[right_index:]
    			
    	return merged_integers
    

## Python Optimizations Leave Me Wondering

I am not so sure about the performance of re-calculating the length of the
left and right lists in the while loop over and over.

    
    
    while left_index < len(left) and right_index < len(right):

It seems like it would better to set those values to variables ahead of time
so one is not calling the **len** function over and over. I tried searching
for information on this, but didn't find anything yet. If I do, I will update
this article.

As an FYI, I had already thought about this optimization in my original code.
Notice at the beginning of the function that I set the length of **integers**
to a variable to avoid calling it twice.

    
    
    	**length** = len(integers)
    	
    	# base case
    	if (**length** < 2):
    		return integers
    
            # split the list in half and sort each half
    	midpoint = **length** // 2

This may be unnecessary and perhaps even worse. I am not sure at the moment. I
do know that it is definitely inconistent with calling the **len** functions
over and over in the **while** loop, but I am leaving it for now I until I
learn more about Python and if/how it optimizes code.

## Pythonista 3 on iPad Pro

I haven't mentioned this before, but I wrote this Merge Sort using Pythonista
3 on my 12.9" iPad Pro. I absolutely love Pythonista 3. Here is a screenshot
of me re-running the Doctests on the Merge Sort algorithm just after making
that change to the **while** loop and code at the end. I particularly love
that Pythonista 3 supports split screen.

![Writing Merge Sort in Python Using Pythonista 3 on iPad Pro
](/media/default/articles/merge-sort-python-pythonista3-ipad-pro.png)

## Python Doctests

I plan to start adding Doctests to all my code samples using Python. I realize
they are not a replacement for unit tests, but I find Doctests extremely
useful for my simple coding exercises and Pythonista 3 fully supports running
them. They came in really handy after I made a change to the Merge Sort
algorithm. I made the changes and re-ran the Doctests and all 6 passed, which
provided me re-assurance that the code still worked (at least as good as the
Doctests).

    
    
    	>>> merge_sort([])
    	[]
    	>>> merge_sort([1])
    	[1]
    	>>> merge_sort([2, 1])
    	[1, 2]
    	>>> merge_sort([2, 1, 4])
    	[1, 2, 4]
    	>>> merge_sort([2, 1, 4, 3])
    	[1, 2, 3, 4]
    	>>> merge_sort([2, 15, 89, 27, 16, 34, 120, 65, 51, 1, 54, 72, 210, 27])
    	[1, 2, 15, 16, 27, 27, 34, 51, 54, 65, 72, 89, 120, 210]
    

The Doctests mainly test for the edge cases. The empty list and one item list
test the base case. The 2 item list tests right at the edge of the base case (
length < 2 ). The 3 item list tests an odd number of integers. The 4 item list
tests an even number of integers. Finally, I just threw in a bigger list,
which also contains duplicates. I could include a test with 0, which is a
unique integer, and that would be a really good test. Including a really big
number would be a reasonable test as well.

Doctests are awesome, and I will continue to use them. I need to start
including unit tests as well.

## Merge Sort Array Optimizations

I am writing this section several weeks after I wrote the original article on
Merge Sort in Python. A new course I am taking on Algorithms and a recent
HackerRank Cracking the Coding Interview programming challenge has me re-
thinking the way I handled arrays in the previous algorithm. I realize now
there are a couple of obvious performance improvements that can be made in my
original code.

This bit of code is not performance friendly:

    
    
    # split the list in half and sort each half
    midpoint = length // 2
    left = merge_sort(integers[:midpoint])
    right = merge_sort(integers[midpoint:])
    
    # merge the two sorted lists into 1 larger list
    merged_integers = []
    

I am creating 3 new arrays with every recursive call to `merge_sort`. A new
array is being created for the left half of the original array
(`integers[:midpoint]`), and a new array is being created for the right half
of the original array(`integers[midpoint:]`). In addition, I am creating a new
temporary array, called `merged_integers`, for the merge. The algorithm works,
but it is slower than it needs to be.

Here is another version of Merge Sort I just wrote in Python that fixes all
those problems by passing in `lo` and `hi` values of the indexes of the array
that need to be sorted as well as a single temporary array, `tmp`. This avoids
all the array creation occurring recursively in the original code. This is an
in-place sort.

    
    
    def merge_sort(arr):
    
        def sort(arr, tmp, lo, hi):
            if lo >= hi:
                return
    
            mid = (lo + hi) // 2
    
            sort(arr, tmp, lo, mid)
            sort(arr, tmp, mid + 1, hi)
    
            merge(arr, tmp, lo, hi)
    
        def merge(arr, tmp, lo, hi):
            mid = (lo + hi) // 2
            left_index = lo
            right_index = mid + 1
            index = lo
    
            while left_index <= mid and right_index <= hi:
                if arr[left_index] <= arr[right_index]:
                    tmp[index] = arr[left_index]
                    left_index += 1
                else:
                    tmp[index] = arr[right_index]
                    right_index += 1
    
                index += 1
    
            if left_index <= mid:
                tmp[index:hi + 1] = arr[left_index:mid + 1]
            else:
                tmp[index:hi + 1] = arr[right_index:hi + 1]
    
            arr[lo:hi + 1] = tmp[lo:hi + 1]
    
        if len(arr) < 2:
            return
    
        tmp = [None]*len(arr)
    
        sort(arr, tmp, 0, len(arr) - 1)

I hope you found this article useful!

[python](/Tags/python)[algorithms](/Tags/algorithms)

⇐ [Inorder Traversal of Binary Search Tree in Python](/blog/inorder-traversal-
of-binary-search-tree-in-python)



### Posted by Koder Dojo

I am a C# ASP.NET MVC Developer learning Python as well as a number of topics
on computer science, algorithms, data structures, and cryptography. I am
documenting my adventures to help and inspire other developers to learn these
topics as well.

#### Related Posts:

#### [Python Training - Selection Sort with Sample Unit Tests](/blog/python-
training-selection-sort-with-sample-unit-tests)

I am learning Python and taking several online courses on computer science and
algorithms. One of my assigments is to write **Selection Sort** in Python. I
wrote this sample code on my iPad Pro using Pythonista and included unit
tests.

#### [Insertion Sort Using Python](/blog/insertion-sort-using-python)

A solution to insertion sort using Python that I wrote with Pythonista on my
iPad Pro. I have also included several Doctests to verify it is sorting a list
of integers correctly using insertion sort. If you are attending computer
science and algorithms courses like myself, I hope you find the code useful!

Copyright (C) 2016 All Rights Reserved by Koder Dojo.

[ __ __ ](https://twitter.com/koderdojo) [ __ __
](https://github.com/KoderDojo)
