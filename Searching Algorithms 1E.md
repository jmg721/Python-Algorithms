Searching Algorithms

Searching is a very basic necessity when you store data in different data structures. The simplest approach is to go across every element in the data structure and match it with the value you are searching for. This is known as Linear search. It is inefficient and rarely used, but creating a program for it gives an idea about how we can implement some advanced search algorithms.

##
# Linear Search

In this type of search, a sequential search is made over all items one by one. Every item is checked and if a match is found then that particular item is returned, otherwise the search continues till the end of the data structure.

def linear\_search(values, search\_for):

    search\_at =0

    search\_res =False

# Match the value with each data element

    while search\_at \&lt; len(values)and search\_res isFalse:

        if values[search\_at]== search\_for:

            search\_res =True

        else:

            search\_at = search\_at +1

    return search\_res

l =[64,34,25,12,22,11,90]

print(linear\_search(l,12))

print(linear\_search(l,91))

When the above code is executed, it produces the following result −

True

False

##
# Interpolation Search

This search algorithm works on the probing position of the required value. For this algorithm to work properly, the data collection should be in a sorted form and equally distributed. Initially, the probe position is the position of the middle most item of the collection.If a match occurs, then the index of the item is returned. If the middle item is greater than the item, then the probe position is again calculated in the sub-array to the right of the middle item. Otherwise, the item is searched in the subarray to the left of the middle item. This process continues on the sub-array as well until the size of subarray reduces to zero.

There is a specific formula to calculate the middle position which is indicated in the program below.

def intpolsearch(values,x ):

    idx0 =0

    idxn =(len(values)-1)

    while idx0 \&lt;= idxn and x \&gt;= values[idx0]and x \&lt;= values[idxn]:

# Find the mid point

        mid = idx0 +\

               int(((float(idxn - idx0)/( values[idxn]- values[idx0]))

                    \*( x - values[idx0])))

# Compare the value at mid point with search value

        if values[mid]== x:

            return&quot;Found &quot;+str(x)+&quot; at index &quot;+str(mid)

        if values[mid]\&lt; x:

            idx0 = mid +1

    return&quot;Searched element not in the list&quot;

l =[2,6,11,19,27,31,45,121]

print(intpolsearch(l,2))

When the above code is executed, it produces the following result −

Found2 at index 0

SEARCH TREE

A Binary Search Tree (BST) is a tree in which all the nodes follow the below-mentioned properties − The left sub-tree of a node has a key less than or equal to its parent node&#39;s key. The right sub-tree of a node has a key greater than to its parent node&#39;s key. Thus, BST divides all its sub-trees into two segments; the left sub-tree and the right sub-tree and can be defined as –

left\_subtree (keys)  ≤  node (key)  ≤  right\_subtree (keys)

### **Search for a value in a B-tree**

Searching for a value in a tree involves comparing the incoming value with the value exiting nodes. Here also we traverse the nodes from left to right and then finally with the parent. If the searched for value does not match any of the exiting value, then we return not found message else the found message is returned.

classNode:

    def \_\_init\_\_(self, data):

        self.left =None

        self.right =None

        self.data = data

# Insert method to create nodes

    def insert(self, data):

        ifself.data:

            if data \&lt;self.data:

                ifself.left isNone:

                    self.left =Node(data)

                else:

                    self.left.insert(data)

            elif data \&gt;self.data:

                ifself.right isNone:

                    self.right =Node(data)

                else:

                    self.right.insert(data)

        else:

            self.data = data

# findval method to compare the value with nodes

    def findval(self, lkpval):

        if lkpval \&lt;self.data:

            ifself.left isNone:

                return str(lkpval)+&quot; Not Found&quot;

            returnself.left.findval(lkpval)

        elif lkpval \&gt;self.data:

            ifself.right isNone:

                return str(lkpval)+&quot; Not Found&quot;

            returnself.right.findval(lkpval)

        else:

            print(str(self.data)+&#39; is found&#39;)

# Print the tree

    defPrintTree(self):

        ifself.left:

            self.left.PrintTree()

        print(self.data),

        ifself.right:

            self.right.PrintTree()

root =Node(12)

root.insert(6)

root.insert(14)

root.insert(3)

print(root.findval(7))

print(root.findval(14))

When the above code is executed, it produces the following result −

7NotFound

14is found



BINARY TREE

Tree represents the nodes connected by edges. It is a non-linear data structure. It has the following properties.

- One node is marked as Root node.
- Every node other than the root is associated with one parent node.
- Each node can have an arbitrary number of child node.

We create a tree data structure in python by using the concept os node discussed earlier. We designate one node as root node and then add more nodes as child nodes. Below is program to create the root node.

### **Create Root**

We just create a Node class and add assign a value to the node. This becomes tree with only a root node.

classNode:

    def \_\_init\_\_(self, data):

        self.left =None

        self.right =None

        self.data = data

    defPrintTree(self):

        print(self.data)

root =Node(10)

root.PrintTree()

When the above code is executed, it produces the following result −

10

### **Inserting into a Tree**

To insert into a tree we use the same node class created above and add a insert class to it. The insert class compares the value of the node to the parent node and decides to add it as a left node or a right node. Finally the Print Tree class is used to print the tree.

classNode:

    def \_\_init\_\_(self, data):

        self.left =None

        self.right =None

        self.data = data

    def insert(self, data):

# Compare the new value with the parent node

        ifself.data:

            if data \&lt;self.data:

                ifself.left isNone:

                    self.left =Node(data)

                else:

                    self.left.insert(data)

            elif data \&gt;self.data:

                ifself.right isNone:

                    self.right =Node(data)

                else:

                    self.right.insert(data)

        else:

            self.data = data

# Print the tree

    defPrintTree(self):

        ifself.left:

            self.left.PrintTree()

        print(self.data),

        ifself.right:

            self.right.PrintTree()

# Use the insert method to add nodes

root =Node(12)

root.insert(6)

root.insert(14)

root.insert(3)

root.PrintTree()

When the above code is executed, it produces the following result −

361214

##
# Traversing a Tree

The tree can be traversed by deciding on a sequence to visit each node. As we can clearly see we can start at a node then visit the left sub-tree first and right sub-tree next. Or we can also visit the right sub-tree first and left sub-tree next. Accordingly there are different names for these tree traversal methods. We study them in detail in the chapter implementing the tree traversal algorithms here.