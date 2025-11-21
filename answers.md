# CMPS 2200 Assignment 4
## Answers

**Name:** Daron Lebaredian





- **1a.**

The maximum depth of a d-nary heap -- where n is the total number of nodes in the heap, d is the number of nodes per internal node, and i is the depth of the tree (starting at i=0) -- is:

$i=\lfloor log_d(n)\rfloor$

This is because if we assign each node a cost, c, and assume this said to be equal to one we can use this equation,

$\frac{n}{d^i}=c$

This equation is how one can calculate the cost per node in a tree. We already know there, usually, is d^i nodes per level i and we also know the total number of nodes, n. After we subsitute c with 1 and solve for i we get.

$i = log_d(n)$

We now just need wrap the left side with the floor function to avoid decimals in the outputs and finally get a function which shows the maximum depth of our d-nary heaps:

$i=\lfloor log_d(n)\rfloor$


- **1b.**

The work of `insert` operation in a d -ary heap is:

$W(n) \in O(log_d(n))$

This is because the maximum number of swaping operations needed to keep the heap property intact is equal to the depth of the heap, any additional swaps of nodes is unnecessary. 

The work of `delete` operation in a d -ary heap is:

$W(n) \in O(dlog_d(n))$

While the `insert` operator only needs to check the parent node of the inserted node for each level, the `delete` operation must look for the mimimum node for each level. Basically the `insert` operator node will have to look at only one node per level while the `delete` operator must look, at most all of the orginally swaped node's children, or d nodes. This is why the work of the `delete` operator much at most look at d nodes log_d(n) times, or d nodes for each level.

- **1c.**

We already know the `insert` operation will be called $|E|$ times, for each edge, and the `delete` operation will be caled |V| times, for each node. This means the work of this algorithmn will be, based on previously calculated work of these operations:

$W(n) \in O(|E|log_d(n)+|V|dlog_d(n))$

- **1d.**

A d value must be is

$d=\frac{|E|}{|V|}$

We can find this d value by doing the following

$|E|log_d(|V|)+|V|dlog_d(|V|)=|E|$

$|V|dlog_d(n)=|E|(1-log_d(n))$

$\frac{|V|dlog_d(n)}{|E|}=1-log_d(n)$

$\frac{|V|}{|E|}=\frac{1-log_d(n)}{dlog_d(n)}$

$\frac{|V|}{|E|}=\frac{1-log_d(n)}{dlog_d(n)}$

$\frac{|E|}{|V|}=d\frac{log_d(n)}{1-log_d(n)}$

Then after removing log term we can estimate the needed d value:

$d=\frac{|E|}{|V|}$

- **2a.**

Each column and rows correspond to i and j. Each element in the matrices below represents a output from $APSP(i,j,k) $

k = 2:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | 0        | -2       | -1       |
| 1 | -2       | 0        | 0        |
| 2 | -1       | 0        | 0        |

k = 1:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | 0    | -2       | -1 |
| 1 | -2    | 0        | 1 |
| 2 | -1 | 1 | 0   |

k = 0:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | 0   | -2 | 2 |
| 1 | -2 | 0 | 1 |
| 2 | 2 | 1 | 0  |

- **2b.**



- **2c.**

- **2d.**

- **2e.**



- **3a.**


- **3b.**


- **3c.**
