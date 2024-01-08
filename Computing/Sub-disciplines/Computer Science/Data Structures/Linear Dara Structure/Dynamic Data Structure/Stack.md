# Stack
A **stack** is an [[Data Type#^AbstractDataTypes | abstract data type (ADT)]] that serves as a [[Collection |collection]] of elements, with two main operations and additional:

-   **Push**, which adds an element to the collection, and
-   **Pop**, which removes the most recently added element that was not yet removed.
- Additional:
	-  **peak()** Returns the top element of the stack.
	- **isEmpty()** returns true is stack is empty else false
	- **size()** returns the size of stack
	- **rotate()** or roll() the n topmost elements are moved in rotating fashion  

The order in which an element added to or removed from a stack is described as **last in, first out**, referred to by the acronym **LIFO**. As with a stack of physical objects, this structure makes it easy to take an item off the top of the stack, but accessing a [[Data Type]] deeper in the stack may require taking off multiple other items first.

## **Complexity Analysis:**  
-   **[[Time Complexity]]**

| **Operations** | **Complexity** |
| -------------- | -------------- |
| push()         | O(1)           |
| pop()          | O(1)           |
| peak()         | O(1)           | 
| isEmpty()      | O(1)           |
| size()         | O(1)           |

## **Types of Stacks:**
-   **Register Stack:** This type of stack is also a memory element present in the memory unit and can handle a small amount of data only. The height of the register stack is always limited as the size of the register stack is very small compared to the memory.
-   **Memory Stack:** This type of stack can handle a large amount of memory data. The height of the memory stack is flexible as it occupies a large amount of memory data.

## Implementation
A stack can be implemented either through an [[Array]] or a [[Linked List]].
### Array
An array can be used to implement a (bounded) stack, as follows.
The first element, usually at the zero offset, is the bottom, resulting in `array[0]` being the first element pushed onto the stack and the last element popped off.
The program must keep track of the size (length) of the stack, using a variable *top* that records the number of items pushed so far, therefore pointing to the place in the array where the next element is to be inserted (assuming a zero-based index convention). Thus, the stack itself can be effectively implemented as a three-element structure:
```
procedure initialize(stk : stack, size : integer):
    stk.items ← new array of size items, initially empty
    stk.maxsize ← size
    stk.top ← 0
```
- **Push**
The *push* operation adds an element and increments the *top* index, after checking for overflow:

```
procedure push(stk : stack, x : item):
    if stk.top = stk.maxsize:
        report overflow error
    else:
        stk.items[stk.top] ← x
        stk.top ← stk.top + 1
```
- **Pop**
The *pop* decrements the *top* index after checking for underflow, and returns the item that was previously the top one:

```
procedure pop(stk : stack):
    if stk.top = 0:
        report underflow error
    else:
        stk.top ← stk.top − 1
        r ← stk.items[stk.top]
        return r
```

Using a [[Dynamic Array]], it is possible to implement a stack that can grow or shrink, the size of the stack is the size of the dynamic array. Thus, this is a very efficient implementation of a stack since adding items to or removing items from the end of a dynamic array requires amortized O(1) time.
##### Advantages of array implementation:
-   Easy to implement.
-   Memory is saved as pointers are not involved. 
##### Disadvantages of array implementation:
-   It is not dynamic.
-   It doesn’t grow and shrink depending on needs at runtime.
#### Linked list
Another option for implementing stacks is to use a [[Linked List#Singly Linked List | singly linked list]]. A stack is then a pointer to the "head" of the list, with perhaps a counter to keep track of the size of the list:
```
procedure initialize(stk : stack):
    stk.head ← null
    stk.size ← 0
```
- **Push**
```
procedure push(stk : stack, x : item):
    newhead ← new frame
    newhead.data ← x
    newhead.next ← stk.head
    stk.head ← newhead
    stk.size ← stk.size + 1
```
- **Pop**
```
procedure pop(stk : stack):
    if stk.head = null:
        report underflow error
    r ← stk.head.data
    stk.head ← stk.head.next
    stk.size ← stk.size - 1
    return r
```
##### Advantages of Linked List implementation:
-   The linked list implementation of a stack can grow and shrink according to the needs at runtime.
-   It is used in many virtual machines like JVM.
-   Stacks are more secure and reliable as they do not get corrupted easily.
-   Stack cleans up the objects automatically.
#####  Disadvantages of Linked List implementation:
-   Requires extra memory due to the involvement of pointers.
-   Random accessing is not possible in stack.
-   The total size of the stack must be defined before.
-   If the stack falls outside the memory it can lead to abnormal termination.
## Application of Stack
- [[Backtracking]]
- Compile-time memory management
A number of [[Programming Languages]]'' are stack-oriented, meaning they define most basic operations (adding two numbers, printing a character) as taking their arguments from the stack, and placing any return values back on the stack.
![[Pasted image 20220910160459.png]]