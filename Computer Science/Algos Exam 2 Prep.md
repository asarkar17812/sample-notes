# Coverage: 
- ### Data Types: 
	1) Priority Queue ADT
	2) Heap-order trees
	3) Min and max heaps 
		1) Understand the operations and properties of implicit n-nary min/max heaps 
	4) Dictionaries 
	5) Ordered Dictionary (Dynamic Set)
		1) Binary Search Trees: 
			1) How all the operations of BSTs work and how fast they are, both in best and worst-case scenarios
				1) Worst case specifically means the BST is NOT balanced. We cannot assume an unbalanced BST, unless evidence proves otherwise. 
		2) Balanced Binary Search Trees (BBSTs) and Red-Black Trees: 
			1) How are they defined and what properties they have.
			2) What is black height?
			3) How fast each operation works and their best/worst case performance. Understand how each operation works (except Delete)
			4) The mechanics of RB-Insertion:
				1) Rotations and recoloring, etc.
	6) Augmented Red-Black Trees:
		1) Dynamic order statistics 
		2) What attributes are reasonable to add due to their efficiency in being updated. 
		3) 1D Range Trees 
		4) Interval Trees
- ### Hashing: 
	1) General principles 
	2) Understand insertion and search works for the following variants: 
- ### Dynamic Programming: 
	- Understanding of the structure:
		- Overlapping subproblems 
		- Optimal subproblems
	- Steps of solving a problem via dynamic programming
	- Recognize, recreate, and know the runtimes of:
		- Rod cutting
		- Path counting
		- Treasure hunting
		- Walking up the stairs 
		- Longest Common Subsequence (LCS)
		- Longest Increasing Subsequence (LIS)
		- Putting parenthesis into an arithmetic expression to get the largest number 
---
# Sorting: 
- ### Stable vs Unstable Sorting:
	- Given an input of a list of tuples, such that: 
		```python 
		[("Alice", 30), ("Bob", 25), 
         ("Charlie", 30)]
       ```
	- **Stable** sorting preserves the natural order of the elements, such that:
		```python
			[("Bob", 25), ("Alice", 30), 
	         ("Charlie", 30)]
		```
	- Unstable sorting does NOT preserve the natural order of the elements, such that: 
	```python
 	[("Bob", 25), ("Charlie", 30), ("Alice", 
      30)]
    ```
### Counting Sort: 
- We begin by assuming our input is the form of $n$ integers within a range of size $k$. This allows us to use an array with $k$ indices matching the range. 
	- The importance of using an array is that it will allow us to keep track of how many times integers each integer appears
	- Using only a single array to sort is considered unstable, since we are NOT preserving the ordering of our input. 
	- This is considered to run in: $$\Theta(n)+\Theta(k)$$
- Using a second array of size $k$, we can achieve stable sorting. The second array will store how many integers are less than or equal to each value. To accomplish this, we proceed, such that: 
	1) Iterate over the input list containing the $n$ integers. As we iterate over, we count the occurrences of specific integers in our first array of size $k$. 
	2) Then, after we finish iterating over the input list and have counted the occurrences of each element, we iterate over our first array and count the number of elements less than or equal to the current element. 
	3) Finally, we iterate over our input list and begin to sort it. Taking an element of the input, we go to its associated index in our second array. Using the element stored at the retrieved index, which represents the number of occurrences of the element, we copy the data into our sorted list.
	4) We end by decrementing the number of occurrences of our element in the second array. 
	- This is still considered to run in: $$\Theta(n)+\Theta(k)$$
## Radix Sort:
- Our input contains $n$ elements, with $\ell$ max length of each element, and $r$, or radix, which represents the number of symbols available at each digit (eg, binary, decimal, hex, etc.)
	- There are many implementations of Radix Sort. One of these implementations involves grouping the elements according to their most significant digit and then recursively grouping each group into subgroups according to the subsequent significant digits.
	- For our implementation, we will focus on the least significant digit first and then move towards the most significant digit. For every column of digits, we can use specifically a *stable* counting sort such that the time-complexity to sort each column is given by: $$\Theta(n+r)$$
		- Since we iterate from the least significant digit to the most significant, this corresponds to iterating over the length, $\ell$, of an integer. Thus, according to the cost per column above, the total time-complexity of our Radix sort operation is such that: $$\Theta(\ell(n+r))$$
---
# Hashing:
- ### Basics: 
	- Hashing operations are often expected to be $O(1)$, under specific assumptions, and include: 
		1) Search 
		2) Insert 
		3) Delete
		- For some hashing methods, some operations can be $O(1)$ worst-case. 
- ### Direct Access Tables Example:
	- We begin by assuming our keys are distinct and come from a small set of possible values, $U$. Often $U$ is larger than the available space, $m$, but we only need to deal with a subset of $S$ of $U$, such that, $|S|\leq m$. We also define our hash function, $h$, to map the elements of $S$ to our hash table, $T$. 
	- Problems:
		1) There will be permanently empty slots 
		2) There will be collisions in mapping the elements of $S$ to $T$. 
	- To solve these problems, we can use a more complicated hashing function to reduce collisions and the number of empty slots. Consequently, this will increase the cost of processing and will also need to be repeated for changes in $S$. 
- ### Chaining: 
	- To solve the issue of collisions, we can use chaining to make a linked list, connecting keys that map to the same slot. 
		- Consequently, for when $|S|=n$, the **Search and Delete operations become $O(n)$**. **Insertion still remains constant time, such that its time-complexity is $\Theta(1)$**. 
	- We can recognize that: If our hash function maps $S$ to $T$ uniformly, we can minimize the max chain size. This then minimizes worst-case time-complexity. 
		- A random hashing map could accomplish this, but we need our map to be consistent/deterministic, meaning a specific element of $S$ must be mapped to a specific slot in $T$. 
	- When utilizing chaining for a hash table, we sacrifice space-complexity for time-complexity. This is a consequence of space cost of the pointers used to connect keys in a specific slot of the hash table. In 64-bit and 32-bit systems, the space cost of a pointer is 8 and 4 bytes respectively. The cost of storing an individual entry in the table is the sum of size of the key and the size of the value in bytes, plus every additional pointer. When $\alpha < 1$, we do not require chaining. 
	- #### Simple Uniform Hashing: 
		- We assume that our hashing map uniformly distributes data like a random function, even though our hashing map is consistent/deterministic. 
		- Then probability two given keys collide: $\frac{1}{m}$
			- Our hash table, $T$ is of size $m$. 
		- The expected list size, also called **load factor**, is: $\frac{n}{m}=\alpha$ 
			- This comes from the ratio of the number of elements, $n$, of the set $S$ that we are hashing, to the size, $m$, of the hash table, $T$. 
			- We call this the load factor, since it describes the average load, or amount, of keys mapped to one slot in the hash table, $T$. 
		- Our expected **time-complexity is of search and delete** are such that: $$\Theta(\alpha)+\Theta(1)$$
			- $\Theta(1)$ comes from the operation of mapping an element of $S$ to $T$. This is also the cost to evaluate our hashing function $h$, which we assume to be constant time. 
			- $\Theta(\alpha)$ comes from the operation of iterating through the linked list of keys at a position in the hash table, $T$. This is in average time is half the list length. 
				- Our search and delete operations will approach constant time when our load factor is also constant time, such that $\alpha=O(1)$. 
## Open Addressing: 
- Requires $n\leq m = \alpha< 1$
	- We are requiring the average load factor per slot, $\alpha$, to be less than one. This guarantees that there cannot not be collisions. 
- To solve the sacrifice of space-complexity for improved time-complexity made by chaining, we can avoid using pointers in linked lists and use that space for a larger hash table, $T$.
	- To be clear, for the same number of keys, chaining uses extra pointers and thus more space than necessary. 
- We begin by using a probe sequence, which is a permutation, $P$, of the indices of all slots in the hast table, $T$. This permutation determines the order in which our Search/Delete/Insert operations iterate over the hash table to find an element or empty slot.  
	- We could use special "deleted" markers to indicate slots that are known to be empty.  
- ### Linear Probing: 
	- We define linear probing in terms of our hash function, such that: $$h(k,i)=(h(k,0)+i)\text{mod}m \sim h(k) + \Theta (\alpha)$$
		- $h(k,i)$ represents our hash function. 
			- $k$ represents the input element of $S$ that we are hashing
			- $i$ represents the current element of $P$ that we are using as the index of $T$. 
		- $\text{mod}m$ represents the necessary wrapping of the elements of hash table, so that way the probe doesn't extend beyond the boundaries of the contiguous array.
- ### Clustering: 
	- When using linear probing, hash tables can develop continuous "clusters" of filled slots. 
		- The probability of extending a cluster is such that: $$\frac{|\text{cluster}|}{m}\gg \frac{1}{m}$$
			- As the probability of extending a cluster increases, the search/delete operations become slower. This is because the more occupied slots in the table, the deeper we have iterate through the $P$. The more iterations of $P$, the slower and slower our operations become. 
	- Generates $m$ probe sequences, or in other words, $m$ iterations of the indices stored in $P$. 
- ### Typical Probing Sequences: 
	- #### Quadratic Probing:$$h(k,i)=(h(k,0)+ci+di^2)\text{mod}m$$
		- As a consequence of adding a higher order term, $di^2$, we encourage more random probe sequences and start to address the clustering issue. 
		- Also generates $m$ probe sequences
	- #### Double Hashing: $$h(k,i)=(h_{1}(k)+ih_{2}(k))\text{mod}m$$
		- Using the sum of two unique hash functions and the periodic nature of $\text{mod}m$, we can use $h_{2}$ so that each $k$ has its own "random" offset
		- Can generate $m^2$ probe sequences, which improves the navigational capacity of our probing solution. 
## Analysis of Open Addressing: 
 - We begin by making the assumption **Uniform Hashing** (*not to be confused with simple uniform hashing*), such that
	1) Every key is equally likely to have any of the $m!$ permutations as a probe sequence
	2) All probe sequences are independent of each other 
	- The common probing methodologies seen above do not come close to this assumption. 
- When, $n<m$, the load factor is $\alpha<1$. Then, we claim that the **expected number of probes** when searching is such that: $$\begin{align} \\
\mathbb{E}[\#\text{ of Probes}] &\leq \left( \frac{m}{m-n} \right) \\ \\
&= \left(\frac{1}{1-\alpha}\right)
\end{align}$$
	- If our claim is true, then when $n\ll m$, we conclude: $$\mathbb{E}[\# \text{ of Probes}] = O(1)$$
- #### Proof: 
	- Suppose: $$\mathbb{E}[\# \text{ of Probes}]\leq \left( 
        \frac{1}{1-\alpha}\right)$$
    - We can begin by using a sequence to describe the probability that a probe collides and causes an unsuccessful search, such that: $$\begin{align}\mathbb{P}[\text{1st probe collides}] &= \frac{n}{m} \\ \\
\mathbb{P}[\text{2nd probe collides}] &= \frac{n-1}{m-1} \\
\vdots \\ \\
\mathbb{P}[i\text{th probe collides}] &= \frac{n-i}{m-i} < \frac{n}{m} = \alpha
\end{align}$$
		- Expanding our expectation in terms of our sequence, we have: $$\mathbb{E}[\#\text{ of probes}] = 1 + \frac{n}{m}(\dots)$$
			- The $1$ term comes from the initial probe having to be deployed. 
			- The $\frac{n}{m}$ term represents the probability of needing to probe more 
		- Further expansion shows us: $$\begin{align}
\mathbb{E}[\#\text{ of probes}] &= 1 + \frac{n}{m}\left( 1+ \frac{n-1}{m-1}  \left(\dots\left(1+  \frac{0}{m-n}  \right)\right)\right) \\ \\
&\leq 1+\alpha(1+\alpha(\dots)) \sim n\text{ terms} \\ \\
&\leq 1 + \alpha + \alpha^2 \dots \\ \\
&= \sum^\infty_{i=1}\alpha^i \\ \\
&= \frac{1}{1-\alpha}
\end{align}$$
---
# Deterministic Selection: 
- ## Method of Partitions: 
	- Given a iterable, sequential ADT input, like an array or linked list, we can use the method of partitions to help sort the ADT in $O(n)$, such that: 
		1) We choose an element in the ADT to be our **pivot**, either randomly or as a given input. WLOG, we assume the pivot to be the leftmost element of our ADT, at index $0$.
		2) We then iterate both from the beginning and ending sides of the ADT, one position at a time. 
		3) After iterating, we check if the new elements are greater than or less than the pivot. Depending on the relationship between the pivot and the compared elements, we proceed by sending elements less than the median to the LHS and elements greater than the median to the RHS. 
			1) If the LHS element is less than the median, we continue iterating. 
			2) If the RHS element is greater than the median, we continue iterating. 
			3) If the LHS element is greater than the median and the RHS element is less than the median, we swap the elements at their current indices. 
			4) If the LHS & RHS elements are both greater than the median, we continue iterating only on the RHS, until we find an element that is less than the median. We then swap the LHS and RHS elements and then continue traversing otherwise. This also applies vice versa for when the LHS & RHS elements are both less than the median. 
			5) After the LHS and RHS meet at the same index, $i=k$, we  swap our pivot element, at $i=0$, and the element at $i=k$. 
	- The time-complexity of the partitioning method is: $$\Theta(n+1)$$
		- The $+1$ comes from the operation of swapping the pivot element with the element at $i=k$.
		- The $n$ term is from the RHS and LHS iterations towards the meeting position at $i=k$.
	- We also recognize that the **partition swap was done IN-PLACE**, but the method of partitions in general is **NOT stable**, because it doesn't preserve the order of elements in the ADT. 
	- Stable and in-place variants cannot be done in $O(n)$.
- ## Method of Pruning and Searching: 
	- We begin by identifying some ways to get $O(n)$ algorithms through other methodologies first, including: 
		- ### Iteration: 
			- Iterate through an input, $k$ times with each iteration having a cost of $O(1)$
			- Good for sequential tasks, like verifying sorted order, retrieving a specific element, or partitions.
		- ### Divide and Conquer: 
			- $T(n) = bT\left(  \frac{n}{b}  \right) + O(n^{1-\epsilon})$, where $\epsilon=\Theta(1)$
			- The variant of divide and conquer algorithm above specifies that leaf level dominates polynomially for the recombination step. 
		- ### Master's Theorem Divide and Conquer: 
			- $T(n)=aT\left(  \frac{n}{b}  \right)+\Theta(n)$ 
			- This variant is more similar to the standard master's theorem, where $c=1$, $d=1$, and $a<b$.
			- If we must access all the data in our ADT, our lower bound becomes $\Omega(n)$, since iteration will not be enough. 
	- ### Pruning and Searching: 
		- We begin by recognizing the recurrence relationship: $$T(n)=T \left(  \frac{n}{b}  \right) + \Theta(n)=\Theta(n)$$
			- The first term, $T\left(  \frac{n}{b}  \right)$, eliminates a constant fraction of the data
			- We also do $\Theta(n)$ non-recursive work. 
		- We then modify the recurrence relationship to be: $$T(n) = \Theta(n) + T\left(  \frac{n}{x}  \right) + T\left(  \frac{n}{b}  \right) \iff \left[\left(\frac{1}{x} +  \frac{1}{b}\right) = \frac{1}{c}\ \text{, }\ c>1\right]$$
			- We still perform $\Theta(n)$ non-recursive work 
			- We now perform$T\left(  \frac{n}{x}  \right)$ recursive work per recurrence 
			- We also eliminate a constant fraction,  $T\left(  \frac{n}{b}  \right)$, of the data. 
		- #### Proof: 
		- Suppose we have the following recurrence relation: $$T(n)=T\left( \frac{n}{x}  \right) + T\left( \frac{n}{b}  \right) + pn$$
			- Where $p$ is a constant related to the scaling of non-recursive work. 
		- Suppose: $$\begin{align}
1) \ &T(n)\leq d \left(\frac{n}{x}\right) + d\left(\frac{n}{b} \right) + pn, \  \forall k<n, T(k)\leq dk 
\end{align} $$
		- Then we proceed with our recurrence relation above, such that:
$$\begin{align}  \\1)\ T(n)&\leq d \left(\frac{n}{x}\right) + d\left(\frac{n}{b} \right) + pn \\ \\
&= dn \left( \frac{1}{x} + \frac{1}{b} \right) + pn \\
&= dn\left(\frac{1}{c} \right) + pn \\
&= dn - \left( \frac{c-1}{c}dn - pn \right) \\
&\leq dn, \text{ if } d\geq p \left( \frac{c}{c-1}  \right)
\end{align}$$

- ## Deterministic Selection Algorithms: 
	- Given $n$ values in an array or linked list, find the $k$th **smallest element**, which is otherwise called element of **rank**=$k$. 
		- Think of the idea of **rank** as where the element places in a ladder in terms of magnitude. Where the ladder touches the ground is the smallest element, or where rank=1. The other end of the ladder is the supremum of the set of values. 
		- There does exist a naive approach, such that: 
			1) We sort using MergeSort in $O(n\log n)$
			2) Selecting the $k$th smallest element. This is easy and fast when we select the smallest element, $k=O(1)$, or when we are selecting the largest element, $k=n-O(1) \to O(n)$. This gets increasingly hard as we get closer to selecting the median, such that $k \to \frac{n}{2}$. 
		- This causes an upper-bound where, after performing the MergeSort, we select the first element, such that, $O(n\log n) + O(1) = O(n\log n)$. The lower bound is when we select the largest element such that, $O(n\log n) + O(n)$. 
	- Not using the approach above, we begin by proposing a new selection algorithm, such that: 
		- We pick a random input value, $x$, as our pivot for the method of partitions.
		- We assign $A$ to be the LHS of the median and to contain the values smaller than our pivot, $x$, such that $\{0,\dots,x-1\} \in A$. 
		- Similarly, we assign $B$ to RHS of the median and to contain the values larger than our pivot, such that $\{x+1,\dots,n\}\in B$. 
		- Assuming our values are already sorted, then $\text{size}(A)+1=\text{rank}(x) =r$:
			- This is because the number of elements before the pivot, plus the position of the pivot itself, represent the number of elements smaller than our pivot. 
		- Then we proceed by dividing our selection conditions to be the following: 
			- If $\text{rank}(x)=k, \text{return } x$
			- If $k< \text{rank}(x)$, then we recurse on A to find values with $\text{rank}(k)$. 
			- If $k>\text{rank}(x)$, then we recurse on B to find values with $\text{rank}(k-r)$.
			- **Worst Case:** $T(n)=\Theta(n)+T(n-1)=O(n^2)$
	- To improve the selection algorithm proposed above, we can optimize how we pick our median element, specifically by using the Deterministic Selection Algorithm, such that: 
		1) First, we split our $n$ values into blocks of size $b$, and then we find the $a$th smallest value of each block, which costs: $$\frac{n}{b} \cdot \Theta(1)=\Theta(n)$$
			- If $n$ is not a multiple of $b$, we may need to recurse on a few more elements or spend extra $O(n)$ work dealing with the extraneous elements that don't fill a block. 
		2) Second, we copy those "representatives" of each block to a new list, which costs: $$\Theta(n)$$
		3) Then, we find the median, $x$, of that new list, effectively recursively applying the splitting and selection process to our values, which costs: $$T\left( \frac{n}{b} \right)$$
		4) Using the pivot we generated, we then partition the input, which will cost: $$\Theta(n)$$
		5) Finally, we recurse left or right if necessary, such that: $$T(f(n))$$
		- This provides us with the improved recurrence relation, such that: $$T(n)\leq T\left(  \frac{n}{b}  \right)+ T\left(  f(n) \right) + dn$$
			- We assume that: $T(k)\leq ck, \forall k<n$
			- Let $f(n)$
---
# Indicator Random Variables:
- We begin by defining the random variable, $x$. For our purposes, we can imagine these random variables as  functions that map the sample space of the random variable, $x$, to $\mathbb{R}$ or $\mathbb{N}$, depending on the if the variable is discretized or continuous. 
- These indicator random variables follow many of the same properties that discrete random variables take on, including the linearity of expectation. 
--- 
# Binary Search Trees:
## Basics of BSTs:
- We begin by defining the BST ADT as having a root node and two children nodes per node. This structure allows us navigate data by either traversing left or right, which can correlate to characteristics in the data, like less than or greater than the current node's element. 
	- Our **search** operation will depend on the depth of the tree that we have to traverse to find our element, such that: $O(h)$, where $h$ is the height of the tree
	- Our **insertion** operation must inherently search the tree in order to find where the element being inserted belongs. This is a necessary consequence to preserve the structure of the tree and has time-complexity, $O(h)+O(1)$, from the search operation and the cost of insertion. 
	- Our **delete** operation can be constant time, such that $O(1)$. Despite that, it's not that simple to delete a node in the BST, since the node may or may not have children. 
		- If the current node, $x$, is a leaf we can delete the node without worry 
		- If the current node, $x$, has one child node, we can shift the sub-tree attached to $x$ up, so that the child of $x$ takes it's spot. 
		- If the current node, $x$, is the root with one child, $x$ is either or minimum or maximum element 
		- If the current node, $x$, is the root node and has two children with their own subtrees, we must find a successor node, $y$, to replace the root. We then must search for the smallest element greater than $x$, which is guaranteed to exist because the root has two children. This is also the last node visited on a path from the right-child of the root. Consequently, because of the worst-case scenario requiring traversal of the tree, we maintain $O(h)$.
	- Thus, we denote that the insertion, deletion, and search operations are of time-complexity, $O(h)$, where $h$ is depth/height of the tree. 
## Random BSTs:
### Time Complexity: 
- Given an array, $A$, containing $n$ elements, we can begin by inserting the elements into a BST in order of their indices. In the case of BSTs, this insertion of elements proceeds according to the comparison of the element being inserted to the value of the current node that we have traversed to. If the compared element is less than the current node, then we traverse the left-child of the current node. If the compared element is greater than the current node, then we traverse the right-child of the current node. 
	- What is the worst-case time complexity and why?
		- $\Theta(h^2)$, since we must iterate over the whole array and also insert into the BST. $h$ is the depth/height, or the number of levels between the root and the furthest leaf of our tree.
	- How unbalanced can the tree be?
		- If the input array is already sorted, reverse-sorted, or nearly sorted, each iteration of the array will return an element less than or greater than the current element. This will cause a tree where every node has only a left or right child, respective to how the array is sorted. 
- To solve the problems acknowledged above, we ask new questions, such that: 
	- What would be ideal for reducing time-complexity?
		- If we produced a balanced partition every time, we can  choose the median and split the elements of the array so that the height of the tree isn't tipped overly one way or the other. 
	- What is the improved worst time-complexity? 
		- Naively, $\Omega (n\log n)$, since constructing a BST essentially sorts data, the sorting lower bound applies. 
		- In a balanced tree $\sim \frac{n}{2}$ nodes have depth of $\sim \log n$ so they take $\Omega(n\log n)$ time to insert. 
		- In any other tree, we can find $\geq \frac{n}{2}$ nodes with depth of $\geq \log(n)$, meaning that every algorithm requires $\Omega(n\log(n))$ time to construct any BST 
	- From the behavior that we discussed above, we can conclude that depending on our choice of median element, our time-complexity of constructing a BST is between $\Theta(n\log(n))$ and $\Theta(n^2)$, which is similar to the stable QuickSort algorithm. 
### Height/Depth of BSTs:
- What is the expected height, $H()$, of a randomly constructed BST that contains $n$ elements?$$H(n)=1+\text{max}\{H(k),H(n-k-1)\}, k \in [0,n-1]$$
	- The $1$ term comes from the root node
	- $\text{max}\{H(k), H(n-k-1)\}$ represents choosing the height of the larger sub-tree. 
		- $H(k)$ represents the left sub-tree of the root. 
		- $H(n-k-1)$ represents the right sub-tree of the root. We recognize $n-k-1$ to be the number of elements in the tree, minus the root node and all $k$ elements of the left sub-tree. 
	- $k$ is a random chosen element in the domain, $[0,n-1]$. 
		- If $\frac{n}{4} \leq k \leq \frac{{3n}}{4}$:
			- $H(n)\leq 1 + H\left( \frac{3n}{4} \right)$
		- else: 
			- $H(n)\leq 1 + H(n-1) < 1 + H(n)$ 
	- Then our expected height will be: $$\begin{align}
H(n)&\leq 1 + \frac{1}{2}H\left(  \frac{3n}{4}  \right) + \frac{1}{2} H(n) \\
\frac{1}{2}H(n) &\leq 1 + \frac{1}{2}H\left(  \frac{3n}{4}  \right) \\
H(n) &\leq 2 + H \left(  \frac{3n}{4}  \right) \\
&= O(\log n)
\end{align}$$
		- The 1/2 coefficients come from the probability that $k$ falls within a specific range of $n$. The inner two quartiles, from 25% to 75%, are included in the first "if" statement. The outer two quartiles, from 0% to 25% and 75% to 100%, are included in the "else" statement. 
---
# Dynamic, Balanced, and Non-Random BSTs: 
- We want to create a binary tree that has $O(\log n)$ search, insert, and delete operations. To accomplish this, we need to always maintain $\Theta(\log n)$ height & update in $O(\log n)$ time. 
- ## Red-Black Trees:
	- ### Structure: 
		1) Nodes are colored either red or black 
		2) The root is always black 
		3) We add black "dummy" leaves so every "real" node has 2 children. (think of padding for tokenizers)  
		4) **Every red node has a black parent** 
		5) **For any node, $x$: all paths down to leaves must contain numbers of black nodes, not including $x$.** 
			- If any path is $>2$ times longer than another, we cannot make a tree into red-black tree. 
	- ### Updating RB Trees:
		- #### Insertion: 
			- We insert the node, $x$, containing our data as a red **leaf**
			- We cannot violate the black height specification 
			- If we have a red-red violation, where a red node has a red child, we start **fixing**, locally and upward. 
		- #### Fixing: 
			- Stop Conditions: We want to either create a new RB tree or redefine an ancestor as $x$ (aka fixing upward)
			- Continue Conditions: When our inserted element, $x$, and its parent node, $p$, are both red
			- We define $r$ to be the root node and $y$ to be the node on the opposite side to $p$. 
				- There are 4 possible shapes, including inserting $x$ either to the left or right of $p$. We also include the mirror image of those shapes, such that they're reflected about the node. 
			- Then, we deal with the scenarios such that: 
				1) Recoloring: $y$ is red 
					- We proceed by **recoloring**, $p, g,\& \ y$.
					- We also want to preserve black-height invariance
					- We eliminate the $p$ and $x$ violation, by 
				2) Rotation:
					- 
---

# Augmenting Data Structures: 
## Dynamic Selection and Dynamic Rank:
- We can begin by introducing our array, $A$, with $n$ elements. To find the rank of an element, $i$, in the set of values stored in $A$, we can try two naive solutions, such that: 
	1) We use the method of partitions to find specifically the position of $i$ in $A$. This will be done in $\Theta(n)$ time, but also is $\Theta(n)$ for all subsequent queries of $\text{rank}(k)$, where $k$ is an arbitrary element of $A$.
	2) If we sort $A$, we will take $O(n\log(n))$ time for the initial sorting, and then $O(1)$ for all subsequent queries. 
- The problem that we have with the methodologies above is that they become increasingly unoptimal as we insert/delete entries from $A$. This leads us to rely on (1) more than (2), which then causes $O(n)$ time complexity. 
### Dynamic Sets: 
- In order to improve the insert and delete operations, we use a RB tree. Once we sort the elements of $A$, we can insert them into our RB tree, where the RHS is greater than the root and the LHS is less than the root. Then, for an element, $i$, we can count the number of nodes in a subtree, including the root node, to find the rank of that element. Then, starting at $i$, we traverse up and sum the count of smaller ancestors than element $i$ (until we reach the root) and the sizes of the subtrees containing smaller numbers than $i$. Thus, the time complexity to find the $\text{rank}(i)$ is $O(\log n)$, while the initial time cost to build the RB tree is $\Theta(n\log(n))$ time. 
- To compute the sizes of subtrees after constructing our RB tree, we can use a **postorder walk**, such that: 
	1) We begin at the root node and then traverse all the way down our LHS to the leaf of the left-most subtree. We mark any leaf nodes as having a subtree length of 1. 
	2) We then move to the nearest leaf directly to the right, which we continue until we have traversed all the leaves on the LHS. 
	3) Then, we traverse up a level of the right-most leaf of the LHS of the tree, until we reach the level below the root of the tree. For every level we go up, we add the lengths of the subtrees below and the current node. 
	4) Once we are at the level below the root, we traverse to the left-most leaf of the RHS and begin numbering the leaves as having subtree lengths of 1. 
	5) After we reach the right-most leaf of the RHS, we begin going up the tree and adding the lengths of the subtrees plus the current node. We do this until we reach the level below the root. 
	6) Now that we have the sub-lengths of both the RHS & LHS of the root, we can add them and the root itself to find the number of elements in our RB tree. 
- The issue with using postorder walks is that we may need to rebalance the RB tree in order to maintain its $\Theta(n\log(n))$ operation time-complexity. The process of rebalancing may cause the leaf nodes to change entirely, which then leads us to investigate when subtree sizes in RB trees are affected by update operations:
	- Rotations: Our runtime per search/insertion/deletion operation becomes $O(\log(n))$, since we may need to rotate a subtree in order to maintain the ordering rules of the RB tree. 
- Then we offer two solutions for dynamic selection (aka finding the $ith$ smallest element), such that: 
	1) Static: $\Theta(n)$ time, from utilizing the method of partitions to select the $i$th element 
	2) Dynamic: $O(n\log(n))$ time for sorting and creating the RB tree and its subtree sizes. Then $O(\log n)$ time for finding the $i$th smallest element and for all query/insert/deletion operations. 
## Range Counting: 
- We want to enumerate the set of elements, $S$, that exist within a certain interval, $L$, of the domain, $Q$. We will call the elements of $S\in L$, $k$, so that we can track the amount of elements appearing in our interval.  
- We can naively use an array, $A$, with markers $l$ and $r$ for left and right respectively. Using binary search on $A$ with markers, $l$ & $r$, we have $O(\log n + k)$ time, since we need to count AND enumerate/report the number of elements, $k$, appearing in the interval. 
	- This static approach will break down though, since the insert/delete operations are in $O(n)$ time. 
- Our dynamic approach will involve using a 
---
# Dynamic Programming: 
## Counting Paths:
- We begin by define a $2D$, rectangular grid, $G$, to be of dimensions $n \times m$.
- Starting at the the top-left corner, $(0,0)$, we can only traverse by moving down or to the right. 
- According to the rules above, how many unique sequences exist to reach the opposite corner, $(n,m)$?
#### Recursion as Motivation:
- Naively, we can attempt using recursion to navigate the different possible path choices, such that:$$A[r,c]=A[r-1,c]+A[r,c-1]$$
	- $A[r,c]:=$ A recursive function that takes in the parameters for the starting row, $r$, and column, $c$.
	- We traverse from the bottom-right and go up and to the left instead. This is logically equivalent to starting from the top-left and traverse down and to the right. 
- **Visualizing** the different paths the function call can take, we can imagine a binary tree where the root is the function call at the top of the recursion stack. The left child is traversing up and the right child is traversing left. Extending this fully until $[0,c]$ and $[r,0]$ are the left and right most leaves of the tree, 
- Using our structure provided above, we can **identify the unique sequences of traversal** by counting the number of nodes that contain: $\text{min}\{r,c\}$.  
- Naturally, since we only iteratively move either up or to the left at a time, we will have identical function calls at every level of the tree greater than the children of the root. Thus, for an $n\times n$ grid, the number of identical function calls, aka **repetitive subproblems**, that occur is given, $\Omega (2^n)$.
	- Then, we must ask: how many times will we recurse in a unique way?
		- There exist $r \cdot c$ **distinct subproblems**. Starting at the root node, for every right child node we visit, the left sub-tree of that child will me entirely duplication function calls. The left-only and right-only traversals of the tree are of length $r$ and $c$ respectively. 
### Memoization: 
- We define memoization as the ability to store recursive function calls and re-use them in the even that a recursive function call is identical to one that has already appeared in our decision tree. 
- This results in $\Theta(n \cdot m)$ time and space complexity. 
### Dynamic Programming: 
- We recognize dynamic programming as a "bottom-up:base cases first" approach. Instead of recursion, we then fill any cell as long as the entries directly above and to the left of the element are also already filled. We define the left and top edges of our grid as our base cases, where each entry is $1$. Using **binomial theorem** (aka Pascals Triangle), we can determine the pattern of each newly traversed node. Therefore, since we are summing the number of paths to reach the cells above and to the left of the current entry, when we reach the opposite corner, that is the total amount of paths to reach the bottom right. 
- If we were to insert obstacles into our grid, we can update the base cases to include $0$ at blocked positions. Utilizing the rule of determining the current entry by summing the entries directly above and to the left of the current entry, we still are able to navigate our grid. 
## Longest Common Subsequence(LCS):
#### Brute Force:
- We can naively use brute force methods to find the LCS of two strings, $X$, of length $n$, and $Y$, of length $m$, such that:
	- The size of $X$ is greater than or equal to $Y$, such that: $m\leq n$
	```pseudo
	 for every subsequence of Y: 
		 check if it exists in X 
	```
	- Iterating over every subsequence of $Y$ costs $\Theta(2^m)$ time. Checking if the current subsequence of $Y$ is in $X$ costs $O(n)$ time. 
	- Thus our total time-complexity is such that: $O(n \cdot 2^m)$. 
#### Recursion: 
```c++
## We define our recursive function to be passed in our 
## strings, A & B, and their indices, i & j, respectively
int LCS(A,B,i,j){
	## Base Case: 
	## Check if our strings are empty 
	if (A[i]=='\0' or B[j]=='\0'){ 
		return 0;
		}
		## Successful Recursive Condition: 
		## Call the LCS function again, but iterate one 
		## position forward in both, and add one to the 
		## total length of the matching subsequence

	else if (A[i]==B[j]){
		return 1+LCS(A,B,i+1,j+1);
		}
	## Unsuccessful Recursive Condition: 
	## Call the LCS function again, but only iterate 
	## forward once in either string. Returning the max
	## allows us to continue matching subsequences 
	else{
		return max(LCS(i+1,j),LCS(i,j+1));
	}
};```
- The runtime of the recursive version of the LCS problem is $\Omega(2^n)$, if $m \sim n$.
	- The worst case is that we find no common subsequence between either strings at all 
- Memoization allows us to reduce the runtime of this algorithm to $\Theta(n \cdot m)$, but will also take up $\Theta(n \cdot m)$ space. 
- The number of distinct subproblems $m \cdot n$
- The number of full levels is greater than $\text{min}\{m,n\}$
#### Dynamic Programming: 
- The space and time cost of the dynamic programming approach is $\Theta(n\cdot m)+\Theta(1)$. We do save $\text{min}\{m,n\}$ space, but we also are only given the size of the longest common subsequence and not the subsequence itself. 
	- To find the subsequence itself, we have to trace from $c_{m,n}$ to $c_{1,1}$
		- We begin at $c_{m,n}$ and traverse left, following the greatest value. If we reach the end of our chain of values of the same size, we move up and to the left. We repeat this until we reach $c_{1,1}$. The letters that we consider part of our subsequence include the elements at which we made our diagonal jump. 
```c++
if(A[i]==B[j]){
	return LCS[i,j]=1+LCS[i-1,j-1];
} else {
	return LCS[i,j]=max(LCS[i-1,j],LCS[i,j-1]);
};
```
## Longest Increasing Subsequence(LIS):
 - We begin by considering our sequence, $S$, that contains, $n$, unordered elements. 
 - We want to find the longest subsequence of elements of $S$ that is ordered from least to greatest. 
### Brute Force: 
- We try all possible subsequences and see if they are increasing. 
- The runtime of this is $O(2^n)$, as we can try including/excluding every element of $S$
### Recursion as Motivation: 
- We can naively try a recursive approach, such that we traverse $S$ from left to right and find the length of the LIS. 
- This has a runtime of $O(2^n)$ and a space complexity of $O(n)$
```C++
# A helper function that identifies where the LIS ends
def LISEndingAtIdx(S, i):
    # Base case
    if i == 0:
        return 1
    # Consider all elements on the left of i,
    # recursively compute LISs ending with 
    # them and consider the largest
    mx = 1
    for prev in range(i):
        if S[i] < S[i]:
            mx = max(mx, lisEndingAtIdx(S, prev) + 1)
    return mx
# Our recursive function 
def LIS(S):
    n = len(S)
    res = 1
    for idx in range(1, n):
        res = max(res, lisEndingAtIdx(S, i))
    return res
```
- We can use memoization to help address the overlapping subproblems and to attempt to reduce the complexity of our recursive function. While this may have improvements, our algorithm maintains having $O(n^2)$ time and $O(n)$ space complexities. 
### Dynamic Programming: 
- Our dynamic programming approach requires creating a parallel array, $A$, also of size $n$. In $A$, we fill the array with our base case, which is values of 1. We use two iterates, $i$ and $j$ to navigate $S$, such that $S[i=0]$ and $S[j=1]$. When $j \neq i+1$, we also increment $i$ until it reaches $j-1$, to check if there exists an even longer subsequence including element $S[j]$. After we compare the values $S[i]$ and $S[j]$: 
	1) If $S[i]<S[j]$, then we increment the value stored in $A[j]$ and also increment $j$, and proceed to compare again. 
	2) If $S[i]>S[j]$, then we increment $i$ until $i=j-1$. 
```C++
# LIS returns length of the longest increasing subsequence # in arr of size n
def LIS(S):
    n = len(S)
    # Declare the list (array) for LIS and
    # initialize LIS values for all indexes
    lis = [1] * n
    
    # Compute optimized LIS values in bottom-up manner
    for i in range(1, n):
        for prev in range(0, i):
            if S[i] > S[prev]:
                S[i] = max(lis[i], lis[prev] + 1)
    # Return the maximum of all LIS values
    return max(lis)
```
- Our solution will run in $O(n^2)$ time and take up $O(n)$ space. 
- We also recognize that the dynamic programming approach will return the length of the LIS. If we want to retrieve the actual sequence itself, we can use our parallel array $A$ and recognize the elements marked as the base case and the largest value in stored in $A$. These elements represent the infimum and supremum of our LIS, while the elements preceding the supremum (until $A[k]=2$, where $k$ is the index preceding the supremum) are the rest of sequence. 
## Rod Cutting:
- Suppose we have a rod, $R$, of length $n$ with specific prices per length. We want to find the maximum amount of money you can get by cutting the rod into pieces and selling it.
### Recursion as Motivation: 
```c++
int RodCutting(length, Price[]){
	# Base Case: When the rod DNE
	if length==0{
		return 0;
	} 
	max=-infinity;
	## Recursive Case: For the length of the rod, we can 
	## split the rod into  the price of a piece of length 
	## i, and the rest of the rod 
	for (i=1;i<=length;i++){
		temp = Price[i] + RodCutting(length-i, Price);
		if (temp>max){
			max = temp;
			}
		}
	return max;
}
```
- The runtime of our recursive algorithm above is $\omega(2^n)$
- Since we only have one changing variable, which is our sub-length we cut, $i$, our space complexity will be linear. We also know that we will have repeating, identical function calls, which suggests that we can use memoization to reduce the amount of function calls.  
### Dynamic Programming: 
```c++
int RodCutting(n,Price[]){
	allocate Table[0,...,n];
	Table[0,...,n]=0;
	for (length=1; length<=n;length++){
		for (i=1;i<=length;i++){
			temp = Price[i] + Table[length-i]
			if (temp>Table[length]){
				Table[length]=temp;
			}
	return Table[n];
		}
	}
}
```
- The runtime of the dynamic programming approach, either iteratively or through memoization, is $\Theta(n^2)$. 
- Our spacetime complexity, either iteratively or memoized, $\Theta(n)$. 
- Since our dynamic programming approach only returns the max price, we should need to make a parallel array, $A$, to store the number of cuts per length $i$, so we can find the which lengths to sell at. We can retrieve $A[L]=j_{0}$ so that we can find the first cut to make; after we make our first cut, we move to $A[L-j_{0}]=j_{1}$. We continue this process until we get to $A[0]$.
---