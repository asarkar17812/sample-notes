# Indexing in Databases: 
- Indexing: 
	- A data structure technique to optimize the performance of a database by minimizing the number of disk accesses required when query is processed
- Searching our index happens in $O(n)$ time. Complex search queries, especially ones containing joins heavily impact performance
- Indexing helps improve performance 
- The key for the index can be any attribute or set of attributes and does not need to be the key for the relation on which the index is built
- RULE OF THUMB: Create an index on the attribute that is used frequently in the search
## Basics: 
- An **index** takes a value for some attribute(s) and finds records with the matching value, containing: 
	- A **search key**, which can be a primary key or a candidate key of the table 
	- A **data reference**, which holds the address of the disk block where the key value can be found 
## Selection of Indexes: 
- An **index on an attribute may speed up the execution of those queries in which a value, or range of values, is specified for that attribute.** This can **speed up join operations involving that attribute**. 
- On the other hand, **every index built for one or more attributes of some relation makes insertions, deletions, and updates to that relation more complex and time-consuming**. 
### Deciding Indexing Techniques: 
- We recognize the following aspects to be important in deciding which is the most optimal indexing technique, such that: 
- **Access Types**: 
	- Finding records with a specified attribute value (search key)
	- Finding records with attribute value based on a specified range 
- **Access Time**: 
	- Time needed to find a particular data item or set of data items 
- **Insertion Time**: 
	- Time to find the place to insert + time to insert a new data item + time to update the index structure 
- **Deletion Time**: 
	- Time to find the data item to be deleted + time to delete the data + time to update the index structure 
- **Space Overhead**: 
	- Space occupied by an index structure 
	- Often we compromise on space for performance or vice versa
## Types of File Organization Mechanisms: 
- **Sequential file organization** (**Order Indexes**):
	- Indices based on sorted ordering of the values
	- Generally fast
	- basic/traditional structure that most DBs utilize 
- **Hash File Organization (Hash Indexes)**: 
	- Indices based on a uniform distribution of values across a range of buckets
	- Hash function determines a value assigned to a bucket 
### Ordered Index Structures: 
- A file may have several indices, based on different search keys 
- **Primary Index (or Clustered Index)**:
	- **Search key defines the sequential order of the file**
		- Fast but can result in unnecessary indices and big space needed
	- The search key of a clustering index is often the primary key, but not always 
- **Secondary Index (or Unclustered Index)**:
	- Search key specifies an **order different from the sequential order of the file** 
		- Improves the performance of queries on non-primary keys but impose overhead
	- Use an extra-level of indirection to implement a secondary index, containing pointers to **all** the records
- Created on the basis of the key of the table 
- Ordered file with fixed, two fields 
- Unique to each record (1:1 mapping)
- Since primary keys are stored in sorted order, the performance of the search operation is quite efficient order
- There are two types of indices: 
	- Dense indices 
	- Sparse indices
### Dense Indices: 
- A record is created for every search key value 
- Need more space to store index records 
	- A search key is a primary key 
- A primary index is dense on a primary-key, ordered table is redundant (requiring unnecessary spaces)
- Supports range queries 
#### Dense Index - Lookup: 
- Given a search key $K$, the index is scanned such that: 
	- When $K$ is found, the associated pointer to the data recorder is followed and the block containing the record is red in main memory 
- When dense indexes are used for non-primary key, the minimum value is located first 
	- Consecutive blocks are loaded in main memory until a search key greater than the maximum value is found
- The index is usually kept in main memory. Thus, one disk I/O has to be performed during lookup. 
- Since the index is sorted, a binary search can be used. 
	- If there are $n$ search keys, at most $\log_{2}(n)$ iterations are required to locate a given search key 
- Query-answering using dense indices is efficient 
### Sparse Indices: 
- Used when **dense indices are too large** 
- **One key-pointer pair per data block**
- Can be used **only if the relation is stored in sorted order of the search key** 
#### Sparse Indices - Lookup: 
- Given a search key $K$:
	- Search the sparse index for the greatest key, $K_{i}\leq K$, using binary search
	- Retrieve the pointed block to main memory to look for the record with search key $K$ (linear search vs binary search)
- The **index is usually kept in main memory**. Thus one disk I/o has to be performed during lookup. 
- Efficient in space, but may require more computational time due to the two binary searchers, such that: 
	1) Search on the sparse index
	2) Search on the retrieved data block 
## Dense vs Sparse Indices: 
- A primary index that is dense on an ordered table is **redundant** 
- Thus, a **primary index on an ordered table is sparse** 
- **Dense** indices are **faster** in general 
- Sparse indices require less space and impose less maintenance for insertions and deletions 
- Try to have a sparse index with one entry per block 
	- We aim to keep the index size small
## Two-Level Sparse Indices: 
- Use **binary search** on outer index 
	- Scan index block until the correct is found 
	- Scan block pointed to for desired record
	- For large files, we add additional levels of indexing to improve search performance 
	- Must update indices at all levels when performing INSERT or DELETE operations
## Updating Indices: 
- **All associated indices must be updated when a record is inserted into or deleted from a file** 
- Insertion: 
	- Find a place to insert 
	- For a dense index: 
		- Insert search key value if its not present already
	- For a sparse index: 
		- No changes are made unless a new block is created
		- If the first search key value appears in the new block, insert the search key value into the index
- Deletion: 
	- Find the record 
	- If the recovered record is the last record, delete it's search key value from the index
	- For a dense index: 
		- Delete the search key value
	- For a sparse index: 
		- Delete the search key value
		- Replace the key value's entry index with the next search key value if not already present 
# Implementation of Indices and Updates:
- We begin by recognizing that as the DB and it's index file grows, performance degrades; reorganization is also costly. 
- To solve this issue, we can use the $B+$ tree data structure to maintain indices. This is similar to balance sorted trees, which allows fast search and maintenance without overflow pages. 
### Clustered vs Unclustered Indices: 
- Clustered Index: 
	- When records that are close index are close in data 
	- Indices and data are sorted the same way 
## B+ Trees:
### Basics: 
- $B+$ are **tree-like file structures** 
	- Links nodes with pointers 
	- Has **exactly one root** and is **bounded by leaves at the bottom-most level**
	- Has **unique paths from root to each leaf**; **each path must be of equal length**
	- **Stores keys only at leaves**, references in other/internal nodes 
	- Guides **key search via the reference values, from root to leaves** 
- **Maintains the tree balance** 
- Allows **extensibility**:
	- We can **specify the number of pointers at any given node**
### Nodes: 
- **Includes** the **root**, **internal** nodes (nodes between the root and leaves), and **leaf** nodes
- Each **node is exactly one disk page** ("page" is synonymous with "node")
- Any tree, $T$, will contain $n$ pointers and $n-1$ key values 
#### Leaf Nodes: 
- Each leaf contains a **key value** and a **pointer to the storage location of data matching the key**  
- Leaf nodes are organized into a linked list pages, chaining the leaf nodes 
- The **number of keys = the number of values** 
- If there is an $n-$order $B+$ tree, the leaf nodes: 
	- **Can hold up to $n-1$ key values** 
	- **Must contain at least $\left\lceil  \frac{n-1}{2}  \right\rceil$ key values**
	- Thus we conclude that the **leaf nodes must be such that:** $$\left\lceil  \frac{n-1}{2}  \right\rceil \leq L_{n}\leq(n-1)$$
#### Internal Nodes: 
- Each entry consists of a reference value (key) and a pointer to leaf nodes 
- The data that is being pointed to is less than or equal to the corresponding reference key-value
- If there is a $n$-order $B+$ tree, then the leaf nodes: 
	- Can hold $n-1$ keys
	- Can hold up to $n$ pointers
	- Must contain at least $l\left\lceil  \frac{n}{2}  \right\rceil$
#### Root Node: 
- A root node **consists of one or more reference values (keys) and pointers to the leaf nodes and/or internal nodes**
- If there is an $n$-order $B+$ tree, then leaf nodes
	- Can hold fewer than $\left\lceil  \frac{n}{2}  \right\rceil$ pointers
	- **Must have at least two pointers, if the root points to internal nodes** 
	- Must have at least one entry, if the root is the only node in the tree
#### Number of Indices: 
- For an $n$-order $B+$ tree with height $h$: 
	- The maximum number of records indexed is $r_{\text{max}}=n^h - n^{h-1}$
	- The minimum number of records indexed is $r_{\text{min}}=2 \left\lceil  \frac{n}{2}  \right\rceil^{h-1}$
#### Low n vs High n: 
- Small $n$:
	- Produces a tall and thin $B+$ tree 
	- *Advantage*: Good consistent performance
		- Equal depth of tree $\to$ constant search
	- *Disadvantage*: High overhead when inserting/deleting 
	- We typically use $B+$ trees with small $n$ for **read-heavy DB applications**,  since we'd like to have consistent search runtimes
- Large $n$:
	- Produces a short and wide $B+$ tree
	- *Advantage*: Low overhead 
	- *Disadvantage*: Inconsistent performance
	- We typically use $B+$ trees with large $n$ for read/write-mix DB applications, because of the low overhead for INSERT and DELETE operations 
## Advantages and Disadvantages for Index Data Structures: 
### Index-Sequential Files: 
- Disadvantages: 
	- Performance degrades as the sequential file grows because multiple overflow blocks are being created 
	- Periodic reorganization of entire file is required; increases overhead 
### B+ Tree Index File: 
- Advantage: 
	- Automatically reorganizes itself with small, local changes (when inserting or deleting data)
	- Range queries on indexed attributes are fast 
- Disadvantage: 
	- Extra insertion deletion overhead, space overhead
### Cost of Disk I/O Operations: 
- If we do not utilize an indexing method, we must sequentially scan an entire disk block. Thus, the **estimated cost is the product of the selectivity estimate and the number of blocks/tuples** we must iterate through. 
	- The **selectivity estimate** is the proportion of tuples matching the selection of a given query 
- We recognize that when using an unclustered index in the wrong scenario can lead to low performance. A **full sequential scan may be a better option when**: 
	- **Selectivity is high** (many tuples match the selection)
	- The **ratio between the number of tuples to the number of blocks is high** 
- 