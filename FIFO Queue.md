# FIFO Queue
The python Queue class implements a basic first-in, first-out collection. 
Items can be added to the end of the container using put(), and removed from the head using get().

The constructor for a FIFO queue is as follows:

> class Queue.Queue(maxsize=0)

The parameter maxsize is an integer used to limit the items that can be added into the queue.

Insertion will be blocked once the queue is full, until items are consumed.  The queue size is infinite if maxsize <= 0.

See the following example for how to use the FIFO queue:

![image](https://user-images.githubusercontent.com/19671036/60819695-aa279380-a165-11e9-9eb4-8fd943d6214d.png)

