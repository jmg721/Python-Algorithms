# Stacks
A stack is a data structure that is often likened to a stack of plates. 
If you have just washed a plate, you put it on top of the stack. When you need a plate, 
you take it off the top of the stack. 
So the last plate to be added to the stack will be the first to be removed from the stack. 
Thus, a stack is a last in, first out (LIFO) structure:

![image](https://user-images.githubusercontent.com/19671036/60811535-19e15280-a155-11e9-8e9a-2687644e3152.png)

The preceding figure depicts a stack of plates. Adding a plate to the pile is only possible by leaving that plate on top of the pile. To remove a plate from the pile of plates means to remove the plate that is on top of the pile.There are two primary operations that are done on stacks: push and pop. When an element is added to the top of the stack, it is pushed onto the stack. When an element is taken off the top of the stack, it is popped off the stack. Another operation which is used sometimes is peek, which makes it possible to see the element on the stack without popping it off.Stacks are used for a number of things. One very common usage for stacks is to keep track of the return address during function calls. Let's imagine that we have the following little program:

![image](https://user-images.githubusercontent.com/19671036/60811393-c2db7d80-a154-11e9-83dd-571ac8836a8b.png)

When the program execution gets to the call to a(), it first pushes the address of the following instruction onto the stack, then jumps to a. Inside a, b() is called, but before that, the return address is pushed onto the stack. Once in b() and the function is done, the return address is popped off the stack, which takes us back to a(). When a has completed, the return address is popped off the stack, which takes us back to the print statement.

Stacks are actually also used to pass data between functions. Say you have the following function call somewhere in your code:

![image](https://user-images.githubusercontent.com/19671036/60811613-46956a00-a155-11e9-9527-49bc84a2c520.png)

What is going to happen is that 14, 'eggs', 'ham' and 'spam' will be pushed onto the stack, one at a time:

![image](https://user-images.githubusercontent.com/19671036/60811669-66c52900-a155-11e9-9e19-34dc6f30f5e2.png)

When the code jumps into the function, the values for a, b, c, d will be popped off the stack. The spam element will be popped off first and assigned to d, then "ham" will be assigned to c, and so on:

![image](https://user-images.githubusercontent.com/19671036/60811834-b73c8680-a155-11e9-8842-f0a8b5bcbcd0.png)

# Stack implementation
Now let us study an implementation of a stack in Python. We start off by creating a node class, just as we did in the previous chapter with lists:

![image](https://user-images.githubusercontent.com/19671036/60815909-30d87280-a15e-11e9-9da0-105f5b9a96e5.png)

This should be familiar to you by now: a node holds data and a reference to the next item in a list. We are going to implement a stack instead of a list, but the same principle of nodes linked together still applies.

Now let us look at the stack class. It starts off similar to a singly linked list. We need to know the node at the top of the stack. We would also like to keep track of the number of nodes in the stack. So we will add these fields to

![image](https://user-images.githubusercontent.com/19671036/60815974-49e12380-a15e-11e9-8441-90d82d5d0c18.png)

# Push operation
The push operation is used to add an element to the top of the stack. Here is an implementation:

![image](https://user-images.githubusercontent.com/19671036/60816065-78f79500-a15e-11e9-9987-6ec1a8ebb331.png)

In the following figure, there is no existing node after creating our new node. Thus self.top will point to this new node. The else part of the if statement guarantees that this happens:

![image](https://user-images.githubusercontent.com/19671036/60816105-97f62700-a15e-11e9-86e1-38afda93ba2f.png)

In a scenario where we have an existing stack, we move self.top so that it points to the newly created node. The newly created node must have its next pointer, pointing to the node that used to be the top node on the stack:

![image](https://user-images.githubusercontent.com/19671036/60816155-b4925f00-a15e-11e9-92d5-193260da1302.png)


# Pop operation
Now we need a pop method to remove the top element from the stack. As we do so, we need to return the topmost element as well. We will make the stack return None if there are no more elements:


![image](https://user-images.githubusercontent.com/19671036/60816517-81040480-a15f-11e9-9a6f-097cddda73d5.png)

The thing to pay attention to here is the inner if statement. If the top node has its next attribute pointing to another node, then we must set the top of the stack to now point to that node:

![image](https://user-images.githubusercontent.com/19671036/60816827-2323ec80-a160-11e9-8fa3-79790ed7c9e0.png)

When there is only one node in the stack, the pop operation will proceed as follows:

![image](https://user-images.githubusercontent.com/19671036/60816870-3a62da00-a160-11e9-8481-e3e5ea91987a.png)

Removing such a node results in self.top pointing to None:

![image](https://user-images.githubusercontent.com/19671036/60816906-4a7ab980-a160-11e9-97df-ed602a2735a5.png)

# Peek
As we said earlier, we could also add a peek method. This will just return the top of the stack without removing it from the stack, allowing us to look at the top element without changing the stack itself. This operation is very straightforward. If there is a top element, return its data, otherwise return None (so that the behavior of peek matches that of pop):

![image](https://user-images.githubusercontent.com/19671036/60817002-71d18680-a160-11e9-821e-282f24e57f95.png)
