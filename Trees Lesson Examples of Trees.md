# Building trees
The process of assembling a tree is similar to the process of assembling a linked list. 
Each constructor invocation builds a single node.

![image](https://user-images.githubusercontent.com/19671036/60832987-e61d2180-a182-11e9-81b7-14b307ef9d75.png)

The cargo can be any type, but the left and right parameters should be tree nodes. left and right are optional; the default value is None.

To print a node, we just print the cargo.

One way to build a tree is from the bottom up. Allocate the child nodes first:
```
left = Tree(2)
right = Tree(3)
```
Then create the parent node and link it to the children:
```
tree = Tree(1, left, right);
```
We can write this code more concisely by nesting constructor invocations:
```
>>> tree = Tree(1, Tree(2), Tree(3))
```
Either way, the result is the tree at the beginning.
