# Stacks

#### Introduction

Stack is an abstract data type with a bounded(predefined) capacity. It is a simple data structure that allows adding and removing elements in a particular order. Every time an element is added, it goes on the top of the stack and the only element that can be removed is the element that is at the top of the stack, just like a pile of objects.

#### Basic Features of the Stack

- Stack is an ordered list of similar data type.

- Stack is a LIFO(Last in First out) structure or we can say FILO(First in Last out).

- Stack is said to be in Overflow state when it is completely full and is said to be in Underflow state if it is completely empty.



#### Operations

- **Push**: Adds an item in the stack. If the stack is full, then it is said to be an Overflow condition.

- **Pop:** Removes an item from the stack. The items are  popped in the reversed order in which they are pushed. If the stack is  empty, then it is said to be an Underflow condition.

- **Peek or Top:** Returns top element of stack. 

- **isEmpty:**  Returns true if stack is empty, else false.

  

#### Algorithm for Push Operation

```

1. Check if the stack is full or not.
2. If the stack is full, then print error of overflow and exit the program.
3. If the stack is not full, then increment the top and add the element.
```



#### Algorithm for Pop Operation

```

1.Check if the stack is empty or not.
2.If the stack is empty, then print error of underflow and exit the program.
3.If the stack is not empty, then print the element at the top and decrement the top.
```



#### Code

```
/* C++ program to implement basic stack 
operations */
#include<bits/stdc++.h> 

using namespace std; 

#define MAX 1000 

class Stack 
{ 
	int top; 
public: 
	int a[MAX]; //Maximum size of Stack 

	Stack() { top = -1; } 
	bool push(int x); 
	int pop(); 
	bool isEmpty(); 
}; 

bool Stack::push(int x) 
{ 
	if (top >= (MAX-1)) 
	{ 
		cout << "Stack Overflow"; 
		return false; 
	} 
	else
	{ 
		a[++top] = x; 
		cout<<x <<" pushed into stack\n"; 
		return true; 
	} 
} 

int Stack::pop() 
{ 
	if (top < 0) 
	{ 
		cout << "Stack Underflow"; 
		return 0; 
	} 
	else
	{ 
		int x = a[top--]; 
		return x; 
	} 
} 

bool Stack::isEmpty() 
{ 
	return (top < 0); 
} 

// Driver program to test above functions 
int main() 
{ 
	class Stack s; 
	s.push(10); 
	s.push(20); 
	s.push(30); 
	cout<<s.pop() << " Popped from stack\n"; 

	return 0; 
} 

```



#### Applications of Stack

-  The simplest application of a stack is to reverse a word. You push a given word to stack - letter by   letter - and then pop letters from the stack.
- Expression Conversion : Infix to Postfix , Postfix to Prefix etc



​            