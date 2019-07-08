# Singly linked lists
A singly linked list is a list with only one pointer between two successive nodes. It can only be traversed in a single direction, that is, you can go from the first node in the list to the last node, but you cannot move from the last node to the first node.

We can actually use the node class that we created earlier to implement a very simple singly linked list:
```
    >>> n1 = Node('eggs')
    >>> n2 = Node('ham')
    >>> n3 = Node('spam')
```
Next we link the nodes together so that they form a chain:
```
    >>> n1.next = n2
    >>> n2.next = n3
```
To traverse the list, you could do something like the following. We start by setting the variable current to the first item in the list:
```
    current = n1
    while current:
        print(current.data)
        current = current.next 
```
In the loop we print out the current element after which we set current to point to the next element in the list. We keep doing this until we have reached the end of the list.

There are, however, several problems with this simplistic list implementation:

It requires too much manual work by the programmer
It is too error-prone (this is a consequence of the first point)
Too much of the inner workings of the list is exposed to the programmer
We are going to address all these issues in the following sections.
