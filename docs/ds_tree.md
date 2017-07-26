## Tree

## Binary Tree

Fundamentally, a binary tree is composed of nodes connected by edges (with further restrictions discussed below). Some binary tree, \(t\), is either empty or consists of a single root element with two distinct binary tree child elements known as the *left subtree* and the *right subtree* of \(t\). As the name *binary* suggests, a node in a binary tree has a *maximum* of \(2\) children.

The following diagrams depict two different binary trees: 

![](https://s3.amazonaws.com/hr-challenge-images/17175/1459921033-f6c1c3af16-BinaryTrees.png) 

Here are the basic facts and terms to know about binary trees:

1. The convention for binary tree diagrams is that the *root* is at the top, and the subtrees branch down from it.
2. A node's *left* and *right* subtrees are referred to as *children*, and that node can be referred to as the *parent* of those subtrees.
3. A non-root node with no children is called a *leaf*.
4. Some node \(a\) is an ancestor of some node \(b\) if \(b\) is located in a left or right subtree whose root node is \(a\). This means that the root node of binary tree \(t\) is the ancestor of all other nodes in the tree.
5. If some node \(a\) is an ancestor of some node \(b\), then the path from \(a\) to \(b\) is the sequence of nodes starting with \(a\), moving down the ancestral chain of children, and ending with bb.
6. The depth (or level) of some node \(a\) is its distance (i.e., number of edges) from the tree's root node.
7. Simply put, the height of a tree is the number of edges between the root node and its furthest leaf.
    * More technically put, it's \(1+max(height(leftSubtree), height(rightSubtree))\) ) (i.e., one more than the maximum of the heights of its left and right subtrees).
    * Any node has a height of \(1\), and the height of an empty subtree is \( - 1 \).
    * Because the height of each node is \(1 + \) the maximum height of its subtrees and an empty subtree's height is \( - 1 \), the height of a single-element tree or leaf node is \(0\).

Let's apply some of the terms we learned above to the binary tree on the right:

1. The root node is \(A\).

2. The respective left and right children of \(A\) are \(B\) and \(E\). The left child of \(B\) is \(C\). The respective left and right children of \(E\) are \(F\) and \(D\).

3. Nodes \(C\), \(F\), and \(D\) are leaves (i.e., each node is a leaf).

4. The root is the ancestor of all other nodes, \(B\) is an ancestor of \(C\), and \(E\) is an ancestor of \(F\) and \(D\).

5. The path between \(A\) and \(C\) is \( A \rightarrow B \rightarrow C \). The path between \(A\) and \(F\) is \( A \rightarrow E \rightarrow F \). The path between \(A\) and \(D\) is A \( \rightarrow E \rightarrow D \).

6. The depth of root node \(A\) is \(0\). The depth of nodes \(B\) and \(E\) is \(1\). The depth of nodes \(C\), \(F\), and \(D\), is \(2\).

7. The height of the tree, \( height(t) \), is \(2\). We calculate this recursively as \( height(t)=1+(max(height(root.leftChild),height(root.rightChild))) \).

Because this is long and complicated when expanded, we'll break it down using an image of a slightly simpler version of \(t\) whose height is still \(2\): 

![](https://s3.amazonaws.com/hr-challenge-images/17175/1459925609-5a2f70951f-BTHeight.png) 
    
## Binary Search Tree

A Binary Search Tree (BST), \(t\), is a binary tree that is either empty or satisfies the following three conditions:

1. Each element in the left subtree of \(t\) is less than or equal to the root element of \(t\) (i.e., \( max(leftTree(t).value) \leq t.valuemax(leftTree(t).value) \leq t.value \)).

2. Each element in the right subtree of \(t\) is greater than the root element of \(t\) (i.e., \( max(rightTree(t).value) \ge t.valuemax(rightTree(t).value) \ge t.value\)).

3. Both \( leftTree(t) \) and \( rightTree(t) \) are BSTs.

You can essentially think of it as a regular binary tree where for each node parent having a \( leftChild \) and \( rightChild \), \( leftChild.value \leq parent.value \le rightChild.value \). In the first diagram at the top of this article, the binary tree of integers on the left side is a binary search tree.

### Advantages and Drawbacks 

* *Searching for elements is very fast.*

We know that each node has a maximum of two children and we know that the \( \leq \) items are always in the left subtree and the \( > \) items are always in the right subtree. To search for an element, we simply need to compare the value we want against the value stored in the root node of the current subtree and work our way down the appropriate child subtrees until we either find the value we're looking for or we hit *null* (i.e., an empty subtree) which indicates the item is not in the BST. Inserting or searching for a node in a balanced tree is \( O(\log n) \) because you're discarding half of the possible values each time you go left or right.

* *It can easily become unbalanced.*

Depending on the insertion order, the tree can very easily become unbalanced (which makes for longer search times). For example, if we create a new tree where the sequence of inserted nodes is \( 2 \rightarrow 1 \rightarrow 3 \rightarrow 4 \rightarrow 5 \rightarrow 6 \), we end up with the following unbalanced tree: 

![](https://s3.amazonaws.com/hr-challenge-images/24100/1473289501-fe15119ffb-UnbalancedBST.png)

Observe that the root's left subtree only has one node, whereas the root's right subtree has four nodes. For this reason, inserting or searching for a node in an unbalanced tree is \( O(n) \).

## Challenges

* ["Trees: Is This a Binary Search Tree?". *hackerrank*. 2016](https://www.hackerrank.com/challenges/ctci-is-binary-search-tree)

## References

* ["Binary Trees and Binary Search Trees". *AllisonP, hackerrank*. 2016](https://www.hackerrank.com/topics/binary-trees-and-binary-search-trees)
