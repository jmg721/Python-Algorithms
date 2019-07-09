# Create a Program to Check whether a Singly Linked List is a Palindrome
This is a Python program to check whether a singly linked list is a palindrome.

## Problem Description
The program creates a linked list using data items input from the user and determines whether it is a palindrome.

## Problem Solution
1. Create a class Node with instance variables data and next.
2. Create a class LinkedList with instance variables head and last_node.
3. The variable head points to the first element in the linked list while last_node points to the last.
4. Define methods append and display inside the class LinkedList to append data and display the linked list respectively.
5. Define method get_prev_node which takes a reference node as argument and returns the node before it.
6. Define a function is_palindrome which returns True if the linked list passed to it is a palindrome.
7. The function is_palindrome iterates through the linked list from the start and the last node towards the middle to check if the list is a palindrome.
8. Create an instance of LinkedList, append data to it and determine whether it is a palindrome.
