# General Trees
Productivity experts say that breakthroughs come by thinking “nonlinearly.” In this chapter, we discuss one of the most important nonlinear data structures in computing—trees. Tree structures are indeed a breakthrough in data organization, for they allow us to implement a host of algorithms much faster than when using linear data structures, such as array-based lists or linked lists. Trees also provide a natural organization for data, and consequently have become ubiquitous structures in file systems, graphical user interfaces, databases, Web sites, and other computer systems.

It is not always clear what productivity experts mean by “nonlinear” thinking, but when we say that trees are “nonlinear,” we are referring to an organizational relationship that is richer than the simple “before” and “after” relationships between objects in sequences. The relationships in a tree are hierarchical, with some objects being “above” and some “below” others. Actually, the main terminology for tree data structures comes from family trees, with the terms “parent,” “child,” “ancestor,” and “descendant” being the most common words used to describe relationships. We show an example of a family tree in Figure
![image](https://user-images.githubusercontent.com/19671036/60832293-24194600-a181-11e9-9c92-16a5d9a24f1f.png)
TREE DEFINITIONS AND PROPERTIES
A tree is an abstract data type that stores elements hierarchically. With the exception of the top element, each element in a tree has a parent element and zero or more children elements. A tree is usually visualized by placing elements inside ovals or rectangles, and by drawing the connections between parents and children with straight lines. (See Figure below) We typically call the top element the root of the tree, but it is drawn as the highest element, with the other elements being connected below (just the opposite of a botanical tree).

![image](https://user-images.githubusercontent.com/19671036/60832389-5f1b7980-a181-11e9-8768-a16521ea9166.png)

 A tree with 17 nodes representing the organization of a fictitious corporation. The root stores Electronics R'Us. The children of the root store R & D, Sales, Purchasing, and Manufacturing. The internal nodes store Sales, International, Overseas, Electronics R'Us, and Manufacturing.
 
# Formal Tree Definition
Formally, we define a tree T as a set of nodes storing elements such that the nodes have a parent-child relationship that satisfies the following properties:

If T is nonempty, it has a special node, called the root of T, that has no parent.
Each node v of T different from the root has a unique parent node w; every node with parent w is a child of w.
Note that according to our definition, a tree can be empty, meaning that it does not have any nodes. This convention also allows us to define a tree recursively such that a tree T is either empty or consists of a node r, called the root of T, and a (possibly empty) set of subtrees whose roots are the children of r.

Other Node Relationships
Two nodes that are children of the same parent are siblings. A node v is external if v has no children. A node v is internal if it has one or more children. External nodes are also known as leaves.

# Example: 
Earlier, we discussed the hierarchical relationship between files and directories in a computer's ile system, although at the time we did not emphasize the nomenclature of a ile system as a tree. In Figure below, we revisit an earlier example. We see that the internal nodes of the tree are associated with directories and the leaves are associated with regular iles. In the UNIX and Linux operating systems, the root of the tree is appropriately called the “root directory” and is represented by the symbol “/.”

![image](https://user-images.githubusercontent.com/19671036/60832576-d5b87700-a181-11e9-861b-ff33f200af38.png)
Tree representing a portion of a file system.

A node u is an ancestor of a node v if u = v or u is an ancestor of the parent of v. Conversely, we say that a node v is a descendant of a node u if u is an ancestor of v. For example, in Figure above, cs252/ is an ancestor of papers/, and pr3 is a descendant of cs016/. The subtree of T rooted at a node v is the tree consisting of all the descendants of v in T (including v itself). In Figure above, the subtree rooted at cs016/ consists of the nodes cs016/, grades, homeworks/, programs/, hw1, hw2, hw3, pr1, pr2, and pr3.

Edges and Paths in Trees
An edge of tree T is a pair of nodes (u, v) such that u is the parent of v, or vice versa. A path of T is a sequence of nodes such that any two consecutive nodes in the sequence form an edge. For example, the tree in Figure 8.3 contains the path (cs252/, projects/, demos/, market).

Example: The inheritance relation between classes in a Python program forms a tree when single inheritance is used. For example, in Section 2.4 we provided a summary of the hierarchy for Python's exception types, as portrayed in Figure below. The BaseException class is the root of that hierarchy, while all user-defined exception classes should conventionally be declared as descendants of the more specific Exception class. 

![image](https://user-images.githubusercontent.com/19671036/60832694-229c4d80-a182-11e9-8482-05af5ca26673.png)

 A portion of Python's hierarchy of exception types.
 
 In Python, all classes are organized into a single hierarchy, as there exists a built-in class named object as the ultimate base class. It is a direct or indirect base class of all other types in Python (even if not declared as such when defining a new class). Therefore, the hierarchy pictured in Figure above is only a portion of Python's complete class hierarchy.
 
 
 
 




