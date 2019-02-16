

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

