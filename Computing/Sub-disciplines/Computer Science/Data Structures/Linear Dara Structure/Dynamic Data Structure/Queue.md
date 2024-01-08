# Queue
A **queue** is a [[Collection | collection]] of entities that are maintained in a sequence and can be modified by the addition of entities at one end of the sequence and the removal of entities from the other end of the sequence.
The end of the sequence at which elements are *added* is called the *back, tail, or rear* of the queue
The end at which elements are *removed* is called the *head or front* of the queue

> Like Real Life Queue

- **The operations of a queue make it a [[first-in-first-out (FIFO) data structure]].**
In a FIFO data structure, the first element added to the queue will be the first one to be removed

## **Characteristics of Queue:**
- Queue can handle multiple data.
- Both ends are accessible.
- Fast and Flexible.

## Basic Operations
Queue operations may involve initializing or defining the queue, utilizing it, and then completely erasing it from the memory. Here we shall try to understand the basic operations associated with queues −
- **enqueue()** − add (store) an item to the queue.
- **dequeue()** − remove (access) an item from the queue.
- Additional:
	- **peek()** − Gets the element at the front of the queue without removing it.
	- **isFull()** − Checks if the queue is full.  
	- **isEmpty()** − Checks if the queue is empty.

- **Enqueue:**
Queues maintain two data pointers, **front** and **rear**. Therefore, its operations are comparatively difficult to implement than that of stacks.
```
procedure enqueue(data)      
   if queue is full
      return overflow
   endif
   rear ← rear + 1
   queue[rear] ← data
   return true
end procedure
```
- **Dequeue:**
Accessing data from the queue is a process of two tasks − access the data where **front** is pointing and remove the data after access.
```
procedure dequeue
   if queue is empty
      return underflow
   end if
   data = queue[front]
   front ← front + 1
   return true
end procedure
```

## Implementation
A queue can be implemented either through an [[Array]] or a [[Linked List]].