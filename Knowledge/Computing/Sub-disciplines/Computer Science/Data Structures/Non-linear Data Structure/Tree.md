# Tree
A **tree** is a widely used [[Data Type#^AbstractDataTypes | abstract data type (ADT)]] that represents a hierarchical [[tree structure]] with a set of connected nodes. Each node in the tree can be connected to many children (depending on the type of tree), but must be connected to exactly one parent, except for the *root* node, which has no parent.

## Basic Concepts
- *Path* − Path refers to the sequence of nodes along the edges of a tree.
- *Root* − The node at the top of the tree is called root. There is only one root per tree and one path from the root node to any node.
- *Parent* − Any node except the root node has one edge upward to a node called parent.
- *Child* − The node below a given node connected by its edge downward is called its child node.
- *Neighbor* - Parent or child.
- *Siblings* - are the children of vertex.
- *Visiting* − Visiting refers to checking the value of a node when control is on the node.
- *Leaf* − The node which does not have any child node is called the leaf node.
- *Breadth* - The number of leaves.
- *Internal Vertices* - The nodes which are not Leaves
- *Level* - The level of a node is the number of edges along the unique path between it and the root node. This is the same as depth when using zero-based counting.
- *Width* - The number of nodes in a level.
- *Ancestor* - A node reachable by repeated proceeding from child to parent.
- *Descendant* - A node reachable by repeated proceeding from parent to child. Also known as _subchild_.
- *Subtree* − Subtree represents the descendants of a node.
- *Forest* - A set of one or more disjoint trees.
- *Traversing* − Traversing means passing through nodes in a specific order.
- *Degree* - For a given node, its number of children. A leaf has necessarily degree zero.
- *Degree of tree* - The degree of a tree is the maximum degree of a node in the tree.
- *Distance* - The number of edges along the shortest path between two nodes.
- *Size of a tree* - Number of nodes in the tree.

## Tree Traversals
Stepping through the items of a tree, by means of the connections between parents and children, is called **walking the tree**, and the action is a _walk_ of the tree. Often, an operation might be performed when a pointer arrives at a particular node.

- A walk in which each parent node is traversed before its children is called a **pre-order** walk.
- A walk in which the children are traversed before their respective parents are traversed is called a **post-order** walk.
- A a walk in which a node's left subtree, then the node itself, and finally its right subtree are traversed is called an **in-order** traversal. (This last scenario, referring to exactly two subtrees, a left subtree and a right subtree, assumes specifically a [[Binary Tree]].) A **level-order** walk effectively performs a [[Breadth-First Search]] over the entirety of a tree; nodes are traversed level by level, where the root node is visited first, followed by its direct child nodes and their siblings, followed by its grandchild nodes and their siblings, etc., until all nodes in the tree have been traversed.