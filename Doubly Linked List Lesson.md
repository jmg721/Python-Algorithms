# Python program to create and display a doubly linked list.
In this program, we will create a doubly linked list and print all the nodes present in the list.

Doubly Linked List:
Doubly Linked List is a variation of the linked list. The linked list is a linear data structure which can be described as the collection of nodes. Nodes are connected through pointers. Each node contains two fields: data and pointer to the next field. The first node of the linked list is called the head, and the last node of the list is called the tail of the list.

One of the limitations of the singly linked list is that it can be traversed in only one direction that is forward. The doubly linked list has overcome this limitation by providing an additional pointer that points to the previous node. With the help of the previous pointer, the doubly linked list can be traversed in a backward direction thus making insertion and deletion operation easier to perform. So, a typical node in the doubly linked list consists of three fields:

Data represents the data value stored in the node.
Previous represents a pointer that points to the previous node.
Next represents a pointer that points to the next node in the list.

![image](https://user-images.githubusercontent.com/19671036/60900225-77e36800-a231-11e9-8dce-7eb53a15459d.png)

The above picture represents a doubly linked list in which each node has two pointers to point to previous and next node respectively. Here, node 1 represents the head of the list. The previous pointer of the head node will always point to NULL. Next pointer of node one will point to node 2. Node 5 represents the tail of the list whose previous pointer will point to node 4, and the next will point to NULL.

## ALGORITHM:
```
Define a Node class which represents a node in the list. It will have three properties: data, 
previous which will point to the previous node and next which will point to the next node.

Define another class for creating a doubly linked list, and it has two nodes: head and tail. 
Initially, head and tail will point to null.
addNode() will add node to the list:

It first checks whether the head is null, then it will insert the node as the head.
Both head and tail will point to a newly added node.
Head's previous pointer will point to null and tail's next pointer will point to null.
If the head is not null, the new node will be inserted at the end of the list 
such that new node's previous pointer will point to tail.
The new node will become the new tail. Tail's next pointer will point to null.

a. display() will show all the nodes present in the list.

Define a new node 'current' that will point to the head.
Print current.data till current points to null.
Current will point to the next node in the list in each iteration.
```
## PROGRAM

![image](https://user-images.githubusercontent.com/19671036/60900424-c3961180-a231-11e9-8b98-aa471d129489.png)
![image](https://user-images.githubusercontent.com/19671036/60900478-db6d9580-a231-11e9-8d52-cc9716d9060e.png)

![image](https://user-images.githubusercontent.com/19671036/60901446-98142680-a233-11e9-8139-3be70f7eb6fc.png)

Output:
```
Nodes of doubly linked list: 
1 2 3 4 5
```
