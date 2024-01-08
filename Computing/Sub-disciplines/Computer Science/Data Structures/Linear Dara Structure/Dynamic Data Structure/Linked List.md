# Linked List
A Linked List is a linear [[Data Structure]] that is used to store a collection of data with the help of nodes. A linked list is made up of two items that are data and a reference to the next node. A reference to the next node is given with the help of [[pointers]] and data is the value of a node.

## Basic Concepts
Each record of a linked list is often called an 'element' or **'node'**.
The **Head** of the list is its first element.
The **Tail** of the list is its last element.

### Declaration
For singly linked, node data structure have two parts. Fields with data, and pointer to next node. 
```
record Node
{
    data; // The data being stored in the node
    Node next // A reference to the next node, null for last node
}
```
For doubly linked list
```
record Node
{
    data; // The data being stored in the node
    Node next // A reference to the next node, null for last node
    Node prev // A reference to the prev node, null for last node
}
```
List have a variable *firstNode* which always points to the first node in the list, or is *null* for an empty list.
```
record List
{
    Node firstNode // points to first node of list; null for empty list
}
```

![[Linked List.svg]]

- The consecutive elements are connected by pointers.
- The size of a linked list is not fixed.
- The last node of the linked list points to null.
- Memory is not wasted but extra memory is consumed as it also uses pointers to keep track of the next successive node.

## Usage
Linked list is one of most common data structure, used to implement several other common [[Data Type#Abstract Data Types| abstract data types]], including [[lists]], [[stacks]], [[queues]], though it is not uncommon to implement those data structures directly without using linked list as the basis.

## Advantages of Linked Lists over arrays:
-   Dynamic Array.
-   Ease of Insertion/Deletion.

## Drawbacks of Linked Lists:
-   Random access is not allowed. We have to access elements sequentially starting from the first node(head node). So we cannot do a [[binary search with linked lists]] efficiently with its default implementation. 
-   Extra memory space for a pointer is required with each element of the list. 
-   Not cache friendly. Since array elements are contiguous locations, there is locality of reference which is not there in case of linked lists.

## Types of linked list
### Singly Linked List
Singly linked lists contain nodes which have a value field as well as pointer to next node.
![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200922124319/Singly-Linked-List1.png)
**[[Time Complexity]]:** O(N)  
**Auxiliary Space:** O(N)

### Doubly Linked List
Doubly linked list contain nodes which have a 'value' field as well as pointers to next and previous node
![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200922124412/Doubly-Linked-List.png)

### Circular Linked List 
The last node of a list, contains link to the first/head node of the linked list in its next pointer. 
This list is said to be *circular* or *circularly linked*; otherwise, it is said to be *open* or *linear*.
![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200922124456/Circular-Linked-List.png)

### Doubly Circular Linked List
Circular double linked list contains nodes that have pointers for next and previous node and head and tail is connected
![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200922124527/Doubly-Circular-Linked-List.png)

## Operations
-This section gives [[Pseudocode]] for adding or removing nodes from singly, doubly, and circularly linked lists in-place.

### Traversal
**Traversal** of a singly linked list is simple, beginning at the first node and following each _next_ link until we come to the end:

```
node := list.firstNode
while node not null
    (do something with node.data)
    node := node.next
```

### Insertion
A new node can be added in three ways:
#### At the front of linked list
Inserting at the front of the list requires a separate function. This requires updating *Head*.
```
function insertAtTheFront(List list, Node newNode) // insert node before current first node
    newNode.next   := list.firstNode
    list.firstNode := newNode
```
![[adding at the front of linked list.svg]]
**Complexity Analysis:**
- **[[Time Complexity]]:** O(1), We have a pointer to the head and we can directly attach a node and change the pointer. So the Time complexity of inserting a node at the head position is O(1) as it does a constant amount of work.
- **Auxiliary Space:** O(1)

#### After given node (5 Step Process)
Follow the steps to add a node after a given node:
- Firstly, check if the given previous node is NULL or not.
- Then, allocate a new node and
- Assign the data to the new node
- And then make the next of new node as the next of previous node. 
- Finally, move the next of the previous node as a new node.
```
function insertAfter(Node node, Node newNode) // insert newNode after node
    newNode.next := node.next
    node.next    := newNode
```
![[adding after node.svg]]
**Complexity Analysis:** 
- **[[Time Complexity]]:** O(N), where N is the size of the linked list  
- **Auxiliary Space:** O(1) since using constant space to modify pointers
#### Add a node at the end: (6 steps process)
- The new node is always added after the last node of the given Linked List.
- Since a Linked List is typically represented by the head of it, we have to traverse the list till the end and then change the next to last node to a new node.
![[adding in the end.svg]]
**Complexity Analysis:**
- **[[Time Complexity]]:** O(N), where N is the number of nodes in the linked list. Since there is a loop from head to end, the function does O(n) work. 
    - This method can also be optimized to work in O(1) by keeping an extra pointer to the tail of the linked list/
- **Auxiliary Space:** O(1)
- 
### Deletion
An elemeчnt can deleted in a list from:

#### Beginning
```
function removeBeginning(List list) // remove first node
    obsoleteNode := list.firstNode
    list.firstNode := list.firstNode.next // point past deleted node
    destroy obsoleteNode
```
Notice that `removeBeginning()` sets `list.firstNode` to `null` when removing the last node in the list.

Since we *can't iterate backwards*, efficient `insertBefore` or `removeBefore` *operations are not possible*. Inserting to a list before a specific node requires traversing the list, which would have *a worst case running time of* **O(n)**.

####   Middle
``` 
function removeAfter(Node node) // remove node past this one
    obsoleteNode := node.next
    node.next := node.next.next
    destroy obsoleteNode
```
The diagram demonstrates the former. To find and remove a particular node, one must again keep track of the previous element.
![[removing node.svg]]

#### End
```
function removeEnd() // remove last node
	while(node has next)
	{
		prevnode = node
		node := node.next
	}
	prevnode.next := NULL
	destry node
```

## Iterative Method to delete an element from the linked list:
To delete a node from the linked list, we need to do the following steps:
-   Find the previous node of the node to be deleted. 
-   Change the **next** of the previous node. 
-   Free memory for the node to be deleted.

## Recursive Method to delete a node from linked list:
To delete a node of a linked list recursively we need to do the following steps:
-   We pass node* (node pointer) as a reference to the function (as in node* &head)
-   Now since the current node pointer is derived from the previous node’s next (which is passed by reference) so now if the value of the current node pointer is changed, the previous next node’s value also gets changed which is the required operation while deleting a node (i.e points previous node’s next to current node’s (containing key) next).
-   Find the node containing the given value.
-   Store this node to deallocate it later using the free() function.
-   Change this node pointer so that it points to its next and by performing this previous node’s next also gets properly linked.

**Complexity Analysis:**
- **[[Time Complexity]]:** O(n)  
- **Auxiliary Space:** O(n) _(due to recursion call stack)_

## Efficiency
|                    | Peek      | Beginning | End            | Middle    | Excess space, average |
| ------------------ | --------- | --------- | -------------- | --------- | --------------------- |
| **Linked List**    | **Θ(n)**  | **Θ()**   | **Θ()**        | **Θ()**   | **Θ(n)**              |
| Array              | Θ(1)      | ---       | ---            | ---       | 0                     |
| Dynamic Array      | Θ(1)      | Θ(n)      | Θ(1) amortized | Θ(n)      | Θ(n)                  |
| Balanced Tree      | Θ(log(n)) | Θ(log(n)) | Θ(log(n))      | Θ(log(n)) | Θ(n)                  |
| Random-Access List | Θ(log(n)) | Θ(1)      | ---            | ---       | Θ(n)                  |
| Hashed Array Tree  | Θ(1)      | Θ(n)      | Θ(1) amortized | Θ(n)      | Θ(n)                  |


## Doubly linked vs. singly linked
Double-linked lists require more space per node (unless one uses XOR-linking), and their elementary operations are more expensive; but they are often easier to manipulate because they allow fast and easy sequential access to the list in both directions. In a doubly linked list, one can insert or delete a node in a constant number of operations given only that node's address. To do the same in a singly linked list, one must have the _address of the pointer_ to that node, which is either the handle for the whole list (in case of the first node) or the link field in the _previous_ node. Some algorithms require access in both directions. On the other hand, doubly linked lists do not allow tail-sharing and cannot be used as persistent data structures.

## Length of Linked List
### Iterative
1) Initialize count as 0 
2) Initialize a node pointer, current = head.
3) Do following while current is not NULL
     a) current = current -> next
     b) count++;
4) Return count

**Complexity:**
- **[[Time Complexity]]**: O(n) Where n is the size of the linked list, and we have to traverse the list only once.
- **Auxiliary Space:** O(1) As constant extra space is used.

### Recursive
**int getCount(head)**
1) If head is NULL, return 0.
2) Else return 1 + getCount(head->next)

**Complexity:**
- **[[Time Complexity]]:** O(n) As we are traversing the linked list only once.
- **Auxiliary Space:** O(n)
Extra space is used in recursion call stack.

#### Tail recursion
The above **recursive** approach can be modified to make it a **tail recursive function** and thus our auxiliary space will become O(1).

**[[Time Complexity]]:** O(n) As we are traversing the list only once.
**Auxiliary Space:** O(1) As we are using tail recursive function, no extra space is used in function call stack .