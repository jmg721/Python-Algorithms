# Lists and Pointer Structures
You will have already seen lists in Python. They are convenient and powerful. Normally, any time you need to store something in a list, you use python's built-in list implementation. In this chapter, however, we are more interested in understanding how lists work. So we are going to study list internals. As you will notice, there are different types of lists.

Python's list implementation is designed to be powerful and to encompass several different use cases. We are going to be a bit more strict in our definition of what a list is. The concept of a node is very important to lists. We shall discuss them in this chapter, but this concept will, in different forms, come back throughout the rest of the book.

## The focus of this Lesson will be the following:
```
-Understand pointers in Python
-Treating the concept of nodes
-Implementing singly, doubly, and circularly linked lists
```
In this lesson, we are going to deal quite a bit with pointers. So it may be useful to remind ourselves what these are. 

To begin with, imagine that you have a house that you want to sell. Lacking time, you contact an agent to find interested buyers. So you pick up your house and take it over to the agent, who will in turn carry the house to anybody who may want to buy it. Ludicrous, you say? Now imagine that you have a few Python functions that work with images. So you pass high-resolution image data between your functions.

Of course, you don't carry your house around. What you would do is write the address of the house down on a piece of scrap paper and hand it over to the agent. The house remains where it is, but the note containing the directions to the house is passed around. You might even write it down on several pieces of paper. Each one is small enough to fit in your wallet, but they all point to the same house.

As it turns out, things are not very different in Python land. Those large image files remain in one single place in memory. What you do is create variables that hold the locations of those images in memory. These variables are small and can easily be passed around between different functions.

That is the big benefit of pointers: they allow you to point to a potentially large segment of memory with just a simple memory address.

Support for pointers exists in your computer's hardware, where it is known as indirect addressing.

In Python, you don't manipulate pointers directly, unlike in some other languages, such as C or Pascal. This has led some people to think that pointers aren't used in Python. Nothing could be further from the truth. Consider this assignment in the Python interactive shell:

```
>>> s = set()
```
	
We would normally say that s is a variable of the type set. That is, s is a set. This is not strictly true, however. The variable s is rather a reference (a "safe" pointer) to a set. The set constructor creates a set somewhere in memory and returns the memory location where that set starts. This is what gets stored in s.

Python hides this complexity from us. We can safely assume that s is a set and that everything works fine.

# Arrays
An array is a sequential list of data. Being sequential means that each element is stored right after the previous one in memory. 
If your array is really big and you are low on memory, it could be impossible to find large enough storage to fit your entire array. 
This will lead to problems.

Of course, the flip side of the coin is that arrays are very fast. 
Since each element follows from the previous one in memory, there is no need to jump around between different memory locations. 
This can be a very important point to take into consideration when choosing between a list and an array in your own real-world applications.

# Pointer structures                                                       
Contrary to arrays, pointer structures are lists of items that can be spread out in memory. 
This is because each item contains one or more links to other items in the structure. 
What type of links these are dependent on the type of structure we have. 
If we are dealing with linked lists, then we will have links to the next (and possibly previous) items in the structure. 
In the case of a tree, we have parent-child links as well as sibling links. 
In a tile-based game where the game map is built up of hexes, each node will have links to up to six adjacent map cells.
There are several benefits with pointer structures. First of all, they don't require sequential storage space. 
Second, they can start small and grow arbitrarily as you add more nodes to the structure.
 
However, this comes at a cost. If you have a list of integers, each node is going to take up the space of an integer, 
as well as an additional integer for storing the pointer to the next node.
