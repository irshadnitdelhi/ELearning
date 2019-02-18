

# Stacks (Placements)





#### What is LIFO ? 

> LIFO is a short form of Last In First Out. It refers how data is accessed, stored and retrieved. Using this scheme, data that was stored last should be the one to be extracted first. This also means that in order to gain access to the first data, all the other data that was stored before this first data must first be retrieved and extracted.        

------

#### Differentiate Stack from Array ?

>Stack follows a LIFO pattern. It means that data access follows a sequence wherein the last data to be stored when the first one to be extracted. Arrays, on the other hand, does not follow a particular order and instead can be accessed by referring to the indexed element within the array.​        

------

#### What are the applications of Stack?

>1. Function Call
>2. String Reversal
>3. Parenthesis Checking
>4. Backtracking
>5. Syntax Parsing
>6. Expression Conversion
>7. Graph Teraversal
>
>

------



#### **Design a stack that supports getMin() in O(1) time and O(1) extra space ?**

*Question*

>Design a Data Structure SpecialStack that 
>supports all the stack operations like push(), pop(), isEmpty(), 
>isFull() and an additional operation getMin() which should return 
>minimum element from the SpecialStack.  All these operations of 
>SpecialStack must be O(1). To implement SpecialStack, you should only 
>use standard Stack data structure and no other data structure like 
>arrays, list, .. etc.  
>
>Example
>
>```
>Consider the following SpecialStack
>16  --> TOP
>15
>29
>19
>18
>
>When getMin() is called it should return 15, 
>which is the minimum element in the current stack. 
>
>If we do pop two times on stack, the stack becomes
>29  --> TOP
>19
>18
>
>When getMin() is called, it should return 18 
>which is the minimum in the current stack.
>
>```
>
>

*Answer*

> **Push(x)** : Inserts x at the top of stack.
>
> - If stack is empty, insert x into the stack and make minEle equal to x.
> - If stack is not empty, compare x with minEle. Two cases arise: 
>   - If x is greater than or equal to minEle, simply insert x.
>   - If x is less than minEle, insert (2*x – minEle) into the stack and  make minEle equal to x.  For example, let previous minEle was 3. Now we  want to insert 2.  We update minEle as 2 and insert 2*2 – 3 = 1 into the  stack.
>
> **Pop() :**  Removes an element from top of stack.
>
> - Remove element from top. Let the removed element be y. Two cases arise: 
>   - If y is greater than or equal to minEle, the minimum element in the stack is still minEle.
>   - If y is less than minEle, the minimum element now becomes (2*minEle –  y), so update (minEle = 2*minEle – y). This is where we retrieve  previous minimum from current minimum and its value in stack. For  example, let the element to be removed be 1 and minEle be 2. We remove 1  and update minEle as 2*2 – 1 = 3. 
>
> ```C++
> // C++ program to implement a stack that supports 
> // getMinimum() in O(1) time and O(1) extra space. 
> #include <bits/stdc++.h> 
> using namespace std; 
> 
> // A user defined stack that supports getMin() in 
> // addition to push() and pop() 
> struct MyStack 
> { 
> 	stack<int> s; 
> 	int minEle; 
> 
> 	// Prints minimum element of MyStack 
> 	void getMin() 
> 	{ 
> 		if (s.empty()) 
> 			cout << "Stack is empty\n"; 
> 
> 		// variable minEle stores the minimum element 
> 		// in the stack. 
> 		else
> 			cout <<"Minimum Element in the stack is: "
> 				<< minEle << "\n"; 
> 	} 
> 
> 	// Prints top element of MyStack 
> 	void peek() 
> 	{ 
> 		if (s.empty()) 
> 		{ 
> 			cout << "Stack is empty "; 
> 			return; 
> 		} 
> 
> 		int t = s.top(); // Top element. 
> 
> 		cout << "Top Most Element is: "; 
> 
> 		// If t < minEle means minEle stores 
> 		// value of t. 
> 		(t < minEle)? cout << minEle: cout << t; 
> 	} 
> 
> 	// Remove the top element from MyStack 
> 	void pop() 
> 	{ 
> 		if (s.empty()) 
> 		{ 
> 			cout << "Stack is empty\n"; 
> 			return; 
> 		} 
> 
> 		cout << "Top Most Element Removed: "; 
> 		int t = s.top(); 
> 		s.pop(); 
> 
> 		// Minimum will change as the minimum element 
> 		// of the stack is being removed. 
> 		if (t < minEle) 
> 		{ 
> 			cout << minEle << "\n"; 
> 			minEle = 2*minEle - t; 
> 		} 
> 
> 		else
> 			cout << t << "\n"; 
> 	} 
> 
> 	// Removes top element from MyStack 
> 	void push(int x) 
> 	{ 
> 		// Insert new number into the stack 
> 		if (s.empty()) 
> 		{ 
> 			minEle = x; 
> 			s.push(x); 
> 			cout << "Number Inserted: " << x << "\n"; 
> 			return; 
> 		} 
> 
> 		// If new number is less than minEle 
> 		if (x < minEle) 
> 		{ 
> 			s.push(2*x - minEle); 
> 			minEle = x; 
> 		} 
> 
> 		else
> 		s.push(x); 
> 
> 		cout << "Number Inserted: " << x << "\n"; 
> 	} 
> }; 
> 
> // Driver Code 
> int main() 
> { 
> 	MyStack s; 
> 	s.push(3); 
> 	s.push(5); 
> 	s.getMin(); 
> 	s.push(2); 
> 	s.push(1); 
> 	s.getMin(); 
> 	s.pop(); 
> 	s.getMin(); 
> 	s.pop(); 
> 	s.peek(); 
> 
> 	return 0; 
> } 
> 
> ```
>
> 



------

#### Tower of Hanoi

*Question*

>Tower of Hanoi is a mathematical puzzle where we have three rods and n 
>disks. The objective of the puzzle is to move the entire stack to 
>another rod, obeying the following simple rules:
>
>​	1) Only one disk can be moved at a time.
>​	2) Each move consists of taking the upper disk from one of the stacks 
>​	     and placing it on top of another stack i.e. a disk can only be moved if 
>​             it is the uppermost disk on a stack.
>​	3) No disk may be placed on top of a smaller disk.

*Answer*

>```c
>#include <stdio.h> 
>
>// C recursive function to solve tower of hanoi puzzle 
>void towerOfHanoi(int n, char from_rod, char to_rod, char aux_rod) 
>{ 
>	if (n == 1) 
>	{ 
>		printf("\n Move disk 1 from rod %c to rod %c", from_rod, to_rod); 
>		return; 
>	} 
>	towerOfHanoi(n-1, from_rod, aux_rod, to_rod); 
>	printf("\n Move disk %d from rod %c to rod %c", n, from_rod, to_rod); 
>	towerOfHanoi(n-1, aux_rod, to_rod, from_rod); 
>} 
>
>int main() 
>{ 
>	int n = 4; // Number of disks 
>	towerOfHanoi(n, 'A', 'C', 'B'); // A, B and C are names of rods 
>	return 0; 
>} 
>
>```
>
>
>
>

------

#### Implement two stacks in an array ? 

*Question*

>Create a data structure *twoStacks* that represents two stacks. Implementation of *twoStacks* should use only one array, i.e., both stacks should use the same array for storing elements. Following functions must be supported by *twoStacks*.
>
>1. push1(int x) : Pushes x to First stack
>2. push2(int x) : Pushes x to Second Stack
>3. pop1() : pops the element from the First Stack
>4. pop2() : Pops the element from the Second Stack

> The idea is to start two stacks from two extreme corners of arr[].  stack1 starts from the 
> leftmost element, the first element in stack1 is pushed at index 0.  The stack2 starts from the rightmost corner, the first element in stack2 is pushed at index (n-1).  Both stacks grow (or shrink) in opposite  direction.  To check for overflow, all we need to check is for space between top elements of both stacks. This check is highlighted in the below code.	
>
> ```
> #include<iostream> 
> #include<stdlib.h> 
> 
> using namespace std; 
> 
> class twoStacks 
> { 
> 	int *arr; 
> 	int size; 
> 	int top1, top2; 
> public: 
> twoStacks(int n) // constructor 
> { 
> 	size = n; 
> 	arr = new int[n]; 
> 	top1 = -1; 
> 	top2 = size; 
> } 
> 
> // Method to push an element x to stack1 
> void push1(int x) 
> { 
> 	// There is at least one empty space for new element 
> 	if (top1 < top2 - 1) 
> 	{ 
> 		top1++; 
> 		arr[top1] = x; 
> 	} 
> 	else
> 	{ 
> 		cout << "Stack Overflow"; 
> 		exit(1); 
> 	} 
> } 
> 
> // Method to push an element x to stack2 
> void push2(int x) 
> { 
> 	// There is at least one empty space for new element 
> 	if (top1 < top2 - 1) 
> 	{ 
> 		top2--; 
> 		arr[top2] = x; 
> 	} 
> 	else
> 	{ 
> 		cout << "Stack Overflow"; 
> 		exit(1); 
> 	} 
> } 
> 
> // Method to pop an element from first stack 
> int pop1() 
> { 
> 	if (top1 >= 0 ) 
> 	{ 
> 		int x = arr[top1]; 
> 		top1--; 
> 		return x; 
> 	} 
> 	else
> 	{ 
> 		cout << "Stack UnderFlow"; 
> 		exit(1); 
> 	} 
> } 
> 
> // Method to pop an element from second stack 
> int pop2() 
> { 
> 	if (top2 < size) 
> 	{ 
> 		int x = arr[top2]; 
> 		top2++; 
> 		return x; 
> 	} 
> 	else
> 	{ 
> 		cout << "Stack UnderFlow"; 
> 		exit(1); 
> 	} 
> } 
> }; 
> 
> 
> /* Driver program to test twStacks class */
> int main() 
> { 
> 	twoStacks ts(5); 
> 	ts.push1(5); 
> 	ts.push2(10); 
> 	ts.push2(15); 
> 	ts.push1(11); 
> 	ts.push2(7); 
> 	cout << "Popped element from stack1 is " << ts.pop1(); 
> 	ts.push2(40); 
> 	cout << "\nPopped element from stack2 is " << ts.pop2(); 
> 	return 0; 
> } 
> 
> ```

------

#### Design a stack with operations on middle element?

*Question*

> How to implement a stack which will support following operations in O(1) time complexity?
>
> 1.  push()  : which adds an element to the top of stack.
> 2. pop()     : which removes an element from the top of stack
> 3. findMiddle() : which will return middle element of the stack 
> 4. deleteMiddle() : which will delete the middle element.

*Answer*

> ```C++
> /* Program to implement a stack that supports findMiddle() and deleteMiddle 
> in O(1) time */
> #include <stdio.h> 
> #include <stdlib.h> 
> 
> /* A Doubly Linked List Node */
> struct DLLNode 
> { 
> 	struct DLLNode *prev; 
> 	int data; 
> 	struct DLLNode *next; 
> }; 
> 
> /* Representation of the stack data structure that supports findMiddle() 
> in O(1) time. The Stack is implemented using Doubly Linked List. It 
> maintains pointer to head node, pointer to middle node and count of 
> nodes */
> struct myStack 
> { 
> 	struct DLLNode *head; 
> 	struct DLLNode *mid; 
> 	int count; 
> }; 
> 
> /* Function to create the stack data structure */
> struct myStack *createMyStack() 
> { 
> 	struct myStack *ms = 
> 			(struct myStack*) malloc(sizeof(struct myStack)); 
> 	ms->count = 0; 
> 	return ms; 
> }; 
> 
> /* Function to push an element to the stack */
> void push(struct myStack *ms, int new_data) 
> { 
> 	/* allocate DLLNode and put in data */
> 	struct DLLNode* new_DLLNode = 
> 			(struct DLLNode*) malloc(sizeof(struct DLLNode)); 
> 	new_DLLNode->data = new_data; 
> 
> 	/* Since we are adding at the begining, 
> 	prev is always NULL */
> 	new_DLLNode->prev = NULL; 
> 
> 	/* link the old list off the new DLLNode */
> 	new_DLLNode->next = ms->head; 
> 
> 	/* Increment count of items in stack */
> 	ms->count += 1; 
> 
> 	/* Change mid pointer in two cases 
> 	1) Linked List is empty 
> 	2) Number of nodes in linked list is odd */
> 	if (ms->count == 1) 
> 	{ 
> 		ms->mid = new_DLLNode; 
> 	} 
> 	else
> 	{ 
> 		ms->head->prev = new_DLLNode; 
> 
> 		if (ms->count & 1) // Update mid if ms->count is odd 
> 		ms->mid = ms->mid->prev; 
> 	} 
> 
> 	/* move head to point to the new DLLNode */
> 	ms->head = new_DLLNode; 
> } 
> 
> /* Function to pop an element from stack */
> int pop(struct myStack *ms) 
> { 
> 	/* Stack underflow */
> 	if (ms->count == 0) 
> 	{ 
> 		printf("Stack is empty\n"); 
> 		return -1; 
> 	} 
> 
> 	struct DLLNode *head = ms->head; 
> 	int item = head->data; 
> 	ms->head = head->next; 
> 
> 	// If linked list doesn't become empty, update prev 
> 	// of new head as NULL 
> 	if (ms->head != NULL) 
> 		ms->head->prev = NULL; 
> 
> 	ms->count -= 1; 
> 
> 	// update the mid pointer when we have even number of 
> 	// elements in the stack, i,e move down the mid pointer. 
> 	if (!((ms->count) & 1 )) 
> 		ms->mid = ms->mid->next; 
> 
> 	free(head); 
> 
> 	return item; 
> } 
> 
> // Function for finding middle of the stack 
> int findMiddle(struct myStack *ms) 
> { 
> 	if (ms->count == 0) 
> 	{ 
> 		printf("Stack is empty now\n"); 
> 		return -1; 
> 	} 
> 
> 	return ms->mid->data; 
> } 
> 
> // Driver program to test functions of myStack 
> int main() 
> { 
> 	/* Let us create a stack using push() operation*/
> 	struct myStack *ms = createMyStack(); 
> 	push(ms, 11); 
> 	push(ms, 22); 
> 	push(ms, 33); 
> 	push(ms, 44); 
> 	push(ms, 55); 
> 	push(ms, 66); 
> 	push(ms, 77); 
> 
> 	printf("Item popped is %d\n", pop(ms)); 
> 	printf("Item popped is %d\n", pop(ms)); 
> 	printf("Middle Element is %d\n", findMiddle(ms)); 
> 	return 0; 
> } 
> 
> ```
>
> ​	
>
> 

------

#### How to implement k stacks using a single array

*Question*

> Create a data structure kStacks that represents k stacks. Implementation of kStacks should use only one array, i.e., k stacks should use the same array for storing elements. Following functions must be supported by kStacks.
>
> 1. push(int x, int sn) –> pushes x to stack number ‘sn’ where sn is from 0 to k-1
> 2. pop(int sn) –> pops an element from stack number ‘sn’ where sn is from 0 to k-1​        

*Answer*

> **Method 1 (Divide the array in slots of size n/k)** 
>  A simple way to implement k stacks is to divide the array in k slots of  size n/k each, and fix the slots for different stacks, i.e., use arr[0]  to arr[n/k-1] for first stack, and arr[n/k] to arr[2n/k-1] for stack2  where arr[] is the array to be used to implement two stacks and size of  array be n.
>
> The problem with this method is inefficient use of array space. A  stack push operation may result in stack overflow even if there is space  available in arr[]. For example, say the k is 2 and array size (n) is 6  and we push 3 elements to first and do not push anything to second  second stack. When we push 4th element to first, there will be overflow  even if we have space for 3 more elements in array.
>
> **Method 2 (A space efficient implementation)**
> The idea is to use two extra arrays for efficient implementation of k  stacks in an array.  This may not make much sense for integer stacks,  but stack items can be large for example stacks of employees, students,  etc where every item is of hundreds of bytes.  For such large stacks,  the extra space used is comparatively very less as we use two *integer* arrays as extra space.
>
> Following are the two extra arrays are used:
>  **1) top[]:**  This is of size k and stores indexes of top elements in all stacks.
>  **2) next[]:** This is of size n and stores  indexes of next item for the items in array arr[].   Here arr[] is  actual array that stores k stacks.
>  Together with k stacks, a stack of free slots in arr[] is also maintained. The top of this stack is stored in a variable ‘free’.
>
> All entries in top[] are initialized as -1 to indicate that all  stacks are empty.  All entries next[i] are initialized as i+1 because  all slots are free initially and pointing to next slot. Top of free  stack, ‘free’ is initialized as 0.
>
> ```c++
> // A C++ program to demonstrate implementation of k stacks in a single 
> // array in time and space efficient way 
> #include<iostream> 
> #include<climits> 
> using namespace std; 
> 
> // A C++ class to represent k stacks in a single array of size n 
> class kStacks 
> { 
> 	int *arr; // Array of size n to store actual content to be stored in stacks 
> 	int *top; // Array of size k to store indexes of top elements of stacks 
> 	int *next; // Array of size n to store next entry in all stacks 
> 				// and free list 
> 	int n, k; 
> 	int free; // To store beginning index of free list 
> public: 
> 	//constructor to create k stacks in an array of size n 
> 	kStacks(int k, int n); 
> 
> 	// A utility function to check if there is space available 
> 	bool isFull() { return (free == -1); } 
> 
> 	// To push an item in stack number 'sn' where sn is from 0 to k-1 
> 	void push(int item, int sn); 
> 
> 	// To pop an from stack number 'sn' where sn is from 0 to k-1 
> 	int pop(int sn); 
> 
> 	// To check whether stack number 'sn' is empty or not 
> 	bool isEmpty(int sn) { return (top[sn] == -1); } 
> }; 
> 
> //constructor to create k stacks in an array of size n 
> kStacks::kStacks(int k1, int n1) 
> { 
> 	// Initialize n and k, and allocate memory for all arrays 
> 	k = k1, n = n1; 
> 	arr = new int[n]; 
> 	top = new int[k]; 
> 	next = new int[n]; 
> 
> 	// Initialize all stacks as empty 
> 	for (int i = 0; i < k; i++) 
> 		top[i] = -1; 
> 
> 	// Initialize all spaces as free 
> 	free = 0; 
> 	for (int i=0; i<n-1; i++) 
> 		next[i] = i+1; 
> 	next[n-1] = -1; // -1 is used to indicate end of free list 
> } 
> 
> // To push an item in stack number 'sn' where sn is from 0 to k-1 
> void kStacks::push(int item, int sn) 
> { 
> 	// Overflow check 
> 	if (isFull()) 
> 	{ 
> 		cout << "\nStack Overflow\n"; 
> 		return; 
> 	} 
> 
> 	int i = free;	 // Store index of first free slot 
> 
> 	// Update index of free slot to index of next slot in free list 
> 	free = next[i]; 
> 
> 	// Update next of top and then top for stack number 'sn' 
> 	next[i] = top[sn]; 
> 	top[sn] = i; 
> 
> 	// Put the item in array 
> 	arr[i] = item; 
> } 
> 
> // To pop an from stack number 'sn' where sn is from 0 to k-1 
> int kStacks::pop(int sn) 
> { 
> 	// Underflow check 
> 	if (isEmpty(sn)) 
> 	{ 
> 		cout << "\nStack Underflow\n"; 
> 		return INT_MAX; 
> 	} 
> 
> 
> 	// Find index of top item in stack number 'sn' 
> 	int i = top[sn]; 
> 
> 	top[sn] = next[i]; // Change top to store next of previous top 
> 
> 	// Attach the previous top to the beginning of free list 
> 	next[i] = free; 
> 	free = i; 
> 
> 	// Return the previous top item 
> 	return arr[i]; 
> } 
> 
> /* Driver program to test twStacks class */
> int main() 
> { 
> 	// Let us create 3 stacks in an array of size 10 
> 	int k = 3, n = 10; 
> 	kStacks ks(k, n); 
> 
> 	// Let us put some items in stack number 2 
> 	ks.push(15, 2); 
> 	ks.push(45, 2); 
> 
> 	// Let us put some items in stack number 1 
> 	ks.push(17, 1); 
> 	ks.push(49, 1); 
> 	ks.push(39, 1); 
> 
> 	// Let us put some items in stack number 0 
> 	ks.push(11, 0); 
> 	ks.push(9, 0); 
> 	ks.push(7, 0); 
> 
> 	cout << "Popped element from stack 2 is " << ks.pop(2) << endl; 
> 	cout << "Popped element from stack 1 is " << ks.pop(1) << endl; 
> 	cout << "Popped element from stack 0 is " << ks.pop(0) << endl; 
> 
> 	return 0; 
> } 
> 
> ```

------

#### How to create a megeable stack ?

*Question*

>Design a stack with following operations.
>
>1.  push(Stack s, x):  Adds an item x to stack s
>2. pop(Stack s): Removes the top item from stack s
>3. merge(Stack s1, Stack s2): Merge contents of s2 into s1.
>
>Time Complexity of all above operations should be O(1). 

*Answer*

>If we **use array** implementation of stack, then merge is not possible to do in O(1) time as we have to do following steps.
>
>1. Delete old arrays
>2. Create a new array for s1 with  size equal to size of old array for s1 plus size of s2.
>3. Copy old contents of s1 and s2 to new array for s1
>    The above operations take O(n) time.
>
>We can **use a linked list**  with two pointers, one pointer to first node (also used as top when  elements are added and removed from beginning). The other pointer is  needed for last node so that we can quickly link the linked list of s2  at the end of s1. Following are all operations.
>
>1.   push(): Adds the new item at the beginning of linked list using first pointer.
>2.   pop():  Removes an item from beginning using first pointer.
>3.   merge(): Links the first pointer second stack as next of last pointer of first list.
>
>*Can we do it if we are not allowed to use extra pointer?*
> We can do it with [**circular linked list**](http://quiz.geeksforgeeks.org/circular-linked-list/).  The idea is to keep track of last node in linked list. The next of last node indicates top of stack.
>
>1.   push(): Adds the new item as next of last node.
>
>2.   pop(): Removes next of last node.
>
>3.   merge(): Links the top (next of last) of second list to the top (next  of last) of first list.  And  makes last of second list as last of whole  list.
>
>   

------

#### Design a Data Structure SpecialStack as described as given below 

*Question*

>1. push() 
>2. pop()
>3. isEmpty()
>4. isFull()
>5. getMin() : Tot get the minimum element from the stack
>
>All of these operations of SpecialStack must be O(1). Do not use any other data structures like arrays, Linked List etc ..

*Answer*

>Use two stacks: one to store actual stack elements and other as an auxiliary stack to store minimum values. The idea is to do push() and pop() operations in such a way that the top of auxiliary stack is always the minimum. Let us see how push() and pop() operations work.
>
>```
>void Push(int x)
>1. Push x to the first stack
>2. Compare x with the to element of the second stack( auxilary stack)
>   Let the top element be y , then
>   a) If x is smaller than y, push x to the auxilary stack
>   b) If x is greater than y, push y to the auxilary stack
>```
>
>```
>int Pop()
>1. Pop the top element from the auxilary stack
>2. Pop the top element from the actual stack and return it.
>```
>
>```
>int getMin()
>1. Return the top element of auxilary stack
>```
>
>#### Code
>
>````c++
>#include<iostream> 
>#include<stdlib.h> 
>
>using namespace std; 
>
>/* A simple stack class with basic stack funtionalities */
>class Stack 
>{ 
>private: 
>	static const int max = 100; 
>	int arr[max]; 
>	int top; 
>public: 
>	Stack() { top = -1; } 
>	bool isEmpty(); 
>	bool isFull(); 
>	int pop(); 
>	void push(int x); 
>}; 
>
>/* Stack's member method to check if the stack is iempty */
>bool Stack::isEmpty() 
>{ 
>	if(top == -1) 
>		return true; 
>	return false; 
>} 
>
>/* Stack's member method to check if the stack is full */
>bool Stack::isFull() 
>{ 
>	if(top == max - 1) 
>		return true; 
>	return false; 
>} 
>
>/* Stack's member method to remove an element from it */
>int Stack::pop() 
>{ 
>	if(isEmpty()) 
>	{ 
>		cout<<"Stack Underflow"; 
>		abort(); 
>	} 
>	int x = arr[top]; 
>	top--; 
>	return x; 
>} 
>
>/* Stack's member method to insert an element to it */
>void Stack::push(int x) 
>{ 
>	if(isFull()) 
>	{ 
>		cout<<"Stack Overflow"; 
>		abort(); 
>	} 
>	top++; 
>	arr[top] = x; 
>} 
>
>/* A class that supports all the stack operations and one additional 
>operation getMin() that returns the minimum element from stack at 
>any time. This class inherits from the stack class and uses an 
>auxiliarry stack that holds minimum elements */
>class SpecialStack: public Stack 
>{ 
>	Stack min; 
>public: 
>	int pop(); 
>	void push(int x); 
>	int getMin(); 
>}; 
>
>/* SpecialStack's member method to insert an element to it. This method 
>makes sure that the min stack is also updated with appropriate minimum 
>values */
>void SpecialStack::push(int x) 
>{ 
>	if(isEmpty()==true) 
>	{ 
>		Stack::push(x); 
>		min.push(x); 
>	} 
>	else
>	{ 
>		Stack::push(x); 
>		int y = min.pop(); 
>		min.push(y); 
>		if( x < y ) 
>		min.push(x); 
>		else
>		min.push(y); 
>	} 
>} 
>
>/* SpecialStack's member method to remove an element from it. This method 
>removes top element from min stack also. */
>int SpecialStack::pop() 
>{ 
>	int x = Stack::pop(); 
>	min.pop(); 
>	return x; 
>} 
>
>/* SpecialStack's member method to get minimum element from it. */
>int SpecialStack::getMin() 
>{ 
>	int x = min.pop(); 
>	min.push(x); 
>	return x; 
>} 
>
>/* Driver program to test SpecialStack methods */
>int main() 
>{ 
>	SpecialStack s; 
>	s.push(10); 
>	s.push(20); 
>	s.push(30); 
>	cout<<s.getMin()<<endl; 
>	s.push(5); 
>	cout<<s.getMin(); 
>	return 0; 
>} 
>
>````
>
>

------

