# Breadth First Traversal

Breadth First Search (BFS) algorithm traverses a graph in a breadthward motion and uses a queue to remember to get the next vertex to start a search, when a dead end occurs in any iteration.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/breadth_first_traversal.jpg)

As in the example given above, BFS algorithm traverses from A to B to E to F first then to C and G lastly to D. It employs the following rules.

* **Rule 1** − Visit the adjacent unvisited vertex. Mark it as visited. Display it. Insert it * in a queue.
* **Rule 2** − If no adjacent vertex is found, remove the first vertex from the queue.
* **Rule 3** − Repeat Rule 1 and Rule 2 until the queue is empty.

# Algorithms

| Step | Traversal                                                                         | Description                                                                                                                                                                                                  |
|------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_one.jpg) | Initialize the stack.                                                                                                                                                                                        |
| 2.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_two.jpg) | Mark S as visited and put it onto the stack. Explore any unvisited adjacent node from S. We have three nodes and we can pick any of them. For this example, we shall take the node in an alphabetical order. |
| 3.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_three.jpg) | Mark A as visited and put it onto the stack. Explore any unvisited adjacent node from A. Both Sand D are adjacent to A but we are concerned for unvisited nodes only.                                        |
| 4.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_four.jpg) | Visit D and mark it as visited and put onto the stack. Here, we have B and C nodes, which are adjacent to D and both are unvisited. However, we shall again choose in an alphabetical order.                 |
| 5.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_five.jpg) | We choose B, mark it as visited and put onto the stack. Here Bdoes not have any unvisited adjacent node. So, we pop Bfrom the stack.                                                                         |
| 6.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_six.jpg) | We check the stack top for return to the previous node and check if it has any unvisited nodes. Here, we find D to be on the top of the stack.                                                               |
| 7.   | ![](https://www.tutorialspoint.com/data_structures_algorithms/images/dfs_seven.jpg) | Only unvisited adjacent node is from D is C now. So we visit C, mark it as visited and put it onto the stack.                                                                                                |

At this stage, we are left with no unmarked (unvisited) nodes. But as per the algorithm we keep on dequeuing in order to get all unvisited nodes. When the queue gets emptied, the program is over.