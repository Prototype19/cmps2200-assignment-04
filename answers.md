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

Each column and rows correspond to i and j. Each element in the matrices below represents a output from $APSP(i,j,k)$. k shows the number of verticles that can be intermediate vericles in a APSP (0, 1, ..., k).

k = -1:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | 0   | -2 | 2 |
| 1 | -2 | 0 | 1 |
| 2 | 2 | 1 | 0  |

k = 0:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | 0   | -2 | 2 |
| 1 | -2 | -4 | 0 |
| 2 | 2 | 0 | 0  |


k = 1:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | -4   | -6 | -2 |
| 1 | -6 | -8 | -4 |
| 2 | -2 | -4 | 0  |

k = 2:

| i/j | 0 | 1  | 2 |
| :------: | :------: | :------: | :------: |
| 0 | -4   | -6 | -2 |
| 1 | -6 | -8 | -4 |
| 2 | -2 | -4 | 0  |



- **2b.**

I realized APSP(i,j,1) and APSP(i,j,2) share this relation:

$APSP(i,j,2) = min(APSP(i,j,1),APSP(2,j,1)+APSP(i,2,1))$

Therefore i can write APSP(i,j,2) in terms of APSP(i,j,1) and APSP(i,j,0) like this by subsitution the recursion relation about with different, i,j and k values:

$APSP(i,j,2) = min(APSP(i,j,1),min(APSP(i,2,0),APSP(i,1,0)+APSP(1,2,0))+min(APSP(2,j,0),APSP(2,1,0)+APSP(1,j,0))$

- **2c.**

Suppose there is a vertex A, there are two possible cases:

The first case is when vertex A is not in the optimial solution, or path P, so the weight if P remains APSP(i,j,k-1).

The second case is when the vertex is in path P. This means APSP(i,j,k-1) is the sum of APSP(i,A,k-1) and APSP(A,j,k-1) as the algorithmn must find the most optimial paths from i and j to A, as we know vertex A is in P already.

Therefore the Optimial substructure property for APSP(i,j,k-1) is:

$APSP(i,j,k-1)=min(APSP(i,j,k-1),APSP(i,A,k-1)+APSP(A,j,k-1)$

- **2d.**

An algorithm for APSP which used memorization would need to create a 3d table with n lengths on each side. This is because there is n possible i, j and k values. This also means the table with have n^3 sub problems needed to be calculated. Since the work for each look up of the created table is $O(1)$ we can say the work for this algorithm is:

$W(n) \in O(n^3)$

- **2e.**

The work of Johnson's algorithmn is:

$O(|V|^2log(|V|) + |V||E|)$

This algorithmn is only better then ours:

$W(n) \in O(|V|^3)$

When the graph isn't very dense

$|E| < |V|^2$ 

Otherwise johnson's algorithmn is worse than ours


- **3a.**

A solution of MST is guaranteed to be a solution of MMET.

Let's say there are two tree, T and T', and T is the MST and T' is the MMET. Let's say there is are edges E and E' which correspond to T and T' but E and E' are different. However if they are different values this is a contradiction. If E > E', as then T is not really the MST because then if another tree used E' instead of E, then it would have a lower total weight compaired to tree T, meaning T would actually need edge E' meaning E = E' and MST must be a solution to MMET.

- **3b.**

First compute MST, call the resulting tree T with total weight W.

Then cycle through each edge, E, of the graph not in T

If E can be put into T and creates a cycle, delete the heavest edge, besides the new node created. This results in tree T'. Then calculate a new total weight W' for tree T'

Compare all these new trees can pick the one with the minimum W'.



- **3c.**

The work of this algorithmn will be

$W(g) \in O(|E|log(|E|)+|E|-|V|-1)$

or

$W(g) \in O(|E|(log(|E|)-|V|))$

g is a inputed graph, because it has both verticles and edges.

this is because the work to create a MST tree is: 

$O(|E|log|E|)$

And the number of edges in MST tree will be |V|-1, as that's the defintion of a tree due to the fact edges can't be selected twice and you onyl need that many edges to create said tree. So the number of edges selected in the loop will be |E|-|V|-1 as edges already in the MST tree is not selected.

 

