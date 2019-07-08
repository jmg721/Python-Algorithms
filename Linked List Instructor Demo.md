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

# Singly linked list class
A list is clearly a separate concept from a node. So we start by creating a very simple class to hold our list. We will start with a constructor that holds a reference to the very first node in the list. Since this list is initially empty, we will start by setting this reference to None:
```
    class SinglyLinkedList:
         def __init__(self):
             self.tail = None 
```
# Append operation
The first operation that we need to perform is to append items to the list. This operation is sometimes called an insert operation. Here we get a chance to hide away the Node class. The user of our list class should really never have to interact with Node objects. These are purely for internal use.

A first shot at an append() method may look like this:
```
    class SinglyLinkedList:
         # ...

         def append(self, data):
             # Encapsulate the data in a Node
             node = Node(data)

             if self.tail == None:
                 self.tail = node
             else:
                 current = self.tail
                 while current.next:
                     current = current.next
                 current.next = node 
```
We encapsulate data in a node, so that it now has the next pointer attribute. From here we check if there are any existing nodes in the list (that is, does self.tail point to a Node). If there is none, we make the new node the first node of the list; otherwise, find the insertion point by traversing the list to the last node, updating the next pointer of the last node to the new node.

We can append a few items:
```
>>> words = SinglyLinkedList()
 >>> words.append('egg')
 >>> words.append('ham')
 >>> words.append('spam')
```
List traversal will work more or less like before. You will get the first element of the list from the list itself:
```
>>> current = words.tail
>>> while current:
        print(current.data) 
        current = current.next
```
