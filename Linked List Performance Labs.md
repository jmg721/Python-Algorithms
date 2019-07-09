# Create a  Program to utilize a Doubly Linked List and involve Insertion, Deletion & Display Operations

This is a Python program to create a doubly linked list and implement insertion, deletion and display operations on the list.

##  Problem Description
The program creates a doubly linked list and presents the user with a menu to perform various operations on the list.

## Problem Solution
1. Create a class Node with instance variables data and next.
2. Create a class DoublyLinkedList with instance variables first and last.
3. The variable first points to the first element in the doubly linked list while last points to the last element.
4. Define methods get_node, insert_after, insert_before, insert_at_beg, insert_at_end, remove and display.
5. get_node takes an index as argument and traverses the list from the first node that many times to return the node at that index.
6. The methods insert_after and insert_before insert a node after or before some reference node in the list.
7. The methods insert_at_beg and insert_at_end insert a node at the first or last position of the list.
8. The method remove takes a node as argument and removes it from the list.
9. The method display traverses the list from the first node and prints the data of each node.
10. Create an instance of DoublyLinkedList and present the user with a menu to perform operations on the list.
