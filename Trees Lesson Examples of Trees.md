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

# Traversing trees
Any time you see a new data structure, your first question should be, How do I traverse it? The most natural way to traverse a tree is recursively. For example, if the tree contains integers as cargo, this function returns their sum:
 ```python
def total(tree):
    if tree == None: return 0
    return total(tree.left) + total(tree.right) + tree.cargo
```

The base case is the empty tree, which contains no cargo, so the sum is 0. The recursive step makes two recursive calls to find the sum of the child trees. When the recursive calls complete, we add the cargo of the parent and return the total.

# Expression trees
A tree is a natural way to represent the structure of an expression. Unlike other notations, it can represent the computation unambiguously. For example, the infix expression 1 + 2 * 3 is ambiguous unless we know that the multiplication happens before the addition.

This expression tree represents the same computation:

The nodes of an expression tree can be operands like 1 and 2 or operators like + and *. Operands are leaf nodes; operator nodes contain references to their operands. (All of these operators are binary, meaning they have exactly two operands.)

We can build this tree like this:

```
>>> tree = Tree('+', Tree(1), Tree('*', Tree(2), Tree(3)))
```
Looking at the figure, there is no question what the order of operations is; the multiplication happens first in order to compute the second operand of the addition.

Expression trees have many uses. The example in this chapter uses trees to translate expressions to postfix, prefix, and infix. Similar trees are used inside compilers to parse, optimize, and translate programs.

# Tree traversal¶
We can traverse an expression tree and print the contents like this:
```python
def print_tree(tree):
    if tree == None: return
    print tree.cargo,
    print_tree(tree.left)
    print_tree(tree.right)
```
In other words, to print a tree, first print the contents of the root, then print the entire left subtree, and then print the entire right subtree. This way of traversing a tree is called a preorder, because the contents of the root appear before the contents of the children. For the previous example, the output is:
```
>>> tree = Tree('+', Tree(1), Tree('*', Tree(2), Tree(3)))
>>> print_tree(tree)
+ 1 * 2 3
```
This format is different from both postfix and infix; it is another notation called prefix, in which the operators appear before their operands.

You might suspect that if you traverse the tree in a different order, you will get the expression in a different notation. For example, if you print the subtrees first and then the root node, you get:
```python
def print_tree_postorder(tree):
    if tree == None: return
    print_tree_postorder(tree.left)
    print_tree_postorder(tree.right)
    print tree.cargo,
```
The result, 1 2 3 * +, is in postfix! This order of traversal is called postorder.

Finally, to traverse a tree inorder, you print the left tree, then the root, and then the right tree:
```python
def print_tree_inorder(tree):
    if tree == None: return
    print_tree_inorder(tree.left)
    print tree.cargo,
    print_tree_inorder(tree.right)
```
The result is 1 + 2 * 3, which is the expression in infix.

To be fair, we should point out that we have omitted an important complication. Sometimes when we write an expression in infix, we have to use parentheses to preserve the order of operations. So an inorder traversal is not quite sufficient to generate an infix expression.

Nevertheless, with a few improvements, the expression tree and the three recursive traversals provide a general way to translate expressions from one format to another.

If we do an inorder traversal and keep track of what level in the tree we are on, we can generate a graphical representation of a tree:
```python
def print_tree_indented(tree, level=0):
    if tree == None: return
    print_tree_indented(tree.right, level+1)
    print '  ' * level + str(tree.cargo)
    print_tree_indented(tree.left, level+1)
```
The parameter level keeps track of where we are in the tree. By default, it is initially 0. Each time we make a recursive call, we pass level+1 because the child’s level is always one greater than the parent’s. Each item is indented by two spaces per level. The result for the example tree is:
```
>>> print_tree_indented(tree)
    3
  *
    2
+
  1
```
If you look at the output sideways, you see a simplified version of the original figure.
