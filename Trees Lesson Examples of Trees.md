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
python ```
def total(tree):
    if tree == None: return 0
    return total(tree.left) + total(tree.right) + tree.cargo
    ```
The base case is the empty tree, which contains no cargo, so the sum is 0. The recursive step makes two recursive calls to find the sum of the child trees. When the recursive calls complete, we add the cargo of the parent and return the total.

21.3. Expression trees
A tree is a natural way to represent the structure of an expression. Unlike other notations, it can represent the computation unambiguously. For example, the infix expression 1 + 2 * 3 is ambiguous unless we know that the multiplication happens before the addition.

This expression tree represents the same computation:

The nodes of an expression tree can be operands like 1 and 2 or operators like + and *. Operands are leaf nodes; operator nodes contain references to their operands. (All of these operators are binary, meaning they have exactly two operands.)

We can build this tree like this:

>>> tree = Tree('+', Tree(1), Tree('*', Tree(2), Tree(3)))
Looking at the figure, there is no question what the order of operations is; the multiplication happens first in order to compute the second operand of the addition.

Expression trees have many uses. The example in this chapter uses trees to translate expressions to postfix, prefix, and infix. Similar trees are used inside compilers to parse, optimize, and translate programs.
