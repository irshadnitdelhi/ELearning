# Queue 

------

#### What is a Queue, how it is different from stack and how is it implemented?

>  Queue is a linear structure which follows the order is First In First Out (FIFO) to access elements.   Mainly the following are basic operations on queue: Enqueue, Dequeue, Front, Rear
>
> The difference between stacks and queues is in removing. In a stack we remove the item the most recently added; in a queue, we remove the item the least recently added. Both Queues and Stacks can be implemented using Arrays and Linked Lists.
>
> ​                  

------

#### Which data structures are used for BFS and DFS of a graph?

>Queue is used for BFS
>
>Stack is used for DFS. DFS can also be implemented using recursion (Note that recursion also uses function call stack).​                    

​                                      

------

#### ​How to implement Stack using queue

> A stack can be implemented using two queues. Let stack to be implemented be ‘s’ and queues used to implement be ‘q1’ and ‘q2’. Stack ‘s’ can be implemented in two ways:
>
> **Method 1 (By making push operation costly)**
>
> ```c++
> /* Program to implement a stack using 
> two queue */
> #include<bits/stdc++.h> 
> 
> using namespace std; 
> 
> class Stack 
> { 
> 	// Two inbuilt queues 
> 	queue<int> q1, q2; 
> 	
> 	// To maintain current number of 
> 	// elements 
> 	int curr_size; 
> 
> 	public: 
> 	Stack() 
> 	{ 
> 		curr_size = 0; 
> 	} 
> 
> 	void push(int x) 
> 	{ 
> 		curr_size++; 
> 
> 		// Push x first in empty q2 
> 		q2.push(x); 
> 
> 		// Push all the remaining 
> 		// elements in q1 to q2. 
> 		while (!q1.empty()) 
> 		{ 
> 			q2.push(q1.front()); 
> 			q1.pop(); 
> 		} 
> 
> 		// swap the names of two queues 
> 		queue<int> q = q1; 
> 		q1 = q2; 
> 		q2 = q; 
> 	} 
> 
> 	void pop(){ 
> 
> 		// if no elements are there in q1 
> 		if (q1.empty()) 
> 			return ; 
> 		q1.pop(); 
> 		curr_size--; 
> 	} 
> 
> 	int top() 
> 	{ 
> 		if (q1.empty()) 
> 			return -1; 
> 		return q1.front(); 
> 	} 
> 
> 	int size() 
> 	{ 
> 		return curr_size; 
> 	} 
> }; 
> 
> // driver code 
> int main() 
> { 
> 	Stack s; 
> 	s.push(1); 
> 	s.push(2); 
> 	s.push(3); 
> 
> 	cout << "current size: " << s.size() 
> 		<< endl; 
> 	cout << s.top() << endl; 
> 	s.pop(); 
> 	cout << s.top() << endl; 
> 	s.pop(); 
> 	cout << s.top() << endl; 
> 
> 	cout << "current size: " << s.size() 
> 		<< endl; 
> 	return 0; 
> } 
> // This code is contributed by Chhavi 
> 
> ```
>
> **Method 2 (By making pop operation costly)**
>
> ```c++
> /* Program to implement a stack 
> using two queue */
> #include<bits/stdc++.h> 
> using namespace std; 
> 
> class Stack 
> { 
> 	queue<int> q1, q2; 
> 	int curr_size; 
> 
> 	public: 
> 	Stack() 
> 	{ 
> 		curr_size = 0; 
> 	} 
> 
> 	void pop() 
> 	{ 
> 		if (q1.empty()) 
> 			return; 
> 
> 		// Leave one element in q1 and 
> 		// push others in q2. 
> 		while (q1.size() != 1) 
> 		{ 
> 			q2.push(q1.front()); 
> 			q1.pop(); 
> 		} 
> 
> 		// Pop the only left element 
> 		// from q1 
> 		q1.pop(); 
> 		curr_size--; 
> 
> 		// swap the names of two queues 
> 		queue<int> q = q1; 
> 		q1 = q2; 
> 		q2 = q; 
> 	} 
> 
> 	void push(int x) 
> 	{ 
> 		q1.push(x); 
> 		curr_size++; 
> 	} 
> 
> 	int top() 
> 	{ 
> 		if (q1.empty()) 
> 			return -1; 
> 
> 		while( q1.size() != 1 ) 
> 		{ 
> 		q2.push(q1.front()); 
> 		q1.pop(); 
> 		} 
> 		
> 		// last pushed element 
> 		int temp = q1.front(); 
> 		
> 		// to empty the auxiliary queue after 
> 		// last operation 
> 		q1.pop(); 
> 	
> 		// push last element to q2 
> 		q2.push(temp); 
> 
> 		// swap the two queues names 
> 		queue<int> q = q1; 
> 		q1 = q2; 
> 		q2 = q; 
> 		return temp; 
> 	} 
> 
> 	int size() 
> 	{ 
> 		return curr_size; 
> 	} 
> }; 
> 
> // Driver code 
> int main() 
> { 
> 	Stack s; 
> 	s.push(1); 
> 	s.push(2); 
> 	s.push(3); 
> 	s.push(4); 
> 
> 	cout << "current size: " << s.size() 
> 		<< endl; 
> 	cout << s.top() << endl; 
> 	s.pop(); 
> 	cout << s.top() << endl; 
> 	s.pop(); 
> 	cout << s.top() << endl; 
> 	cout << "current size: " << s.size() 
> 		<< endl; 
> 	return 0; 
> } 
> // This code is contributed by Chhavi 
> 
> ```

------

#### How to implement Queue using Stack

> A queue can be implemented using two stacks. Let queue to be implemented be q and stacks used to implement q be stack1 and stack2. q can be implemented in two ways:
>
>**Method 1 (By making enQueue operation costly)**
>
>```C++
>// CPP program to implement Queue using 
>// two stacks with costly enQueue() 
>#include <bits/stdc++.h> 
>using namespace std; 
>
>struct Queue { 
>	stack<int> s1, s2; 
>
>	void enQueue(int x) 
>	{ 
>		// Move all elements from s1 to s2 
>		while (!s1.empty()) { 
>			s2.push(s1.top()); 
>			s1.pop(); 
>		} 
>
>		// Push item into s1 
>		s1.push(x); 
>
>		// Push everything back to s1 
>		while (!s2.empty()) { 
>			s1.push(s2.top()); 
>			s2.pop(); 
>		} 
>	} 
>
>	// Dequeue an item from the queue 
>	int deQueue() 
>	{ 
>		// if first stack is empty 
>		if (s1.empty()) { 
>			cout << "Q is Empty"; 
>			exit(0); 
>		} 
>
>		// Return top of s1 
>		int x = s1.top(); 
>		s1.pop(); 
>		return x; 
>	} 
>}; 
>
>// Driver code 
>int main() 
>{ 
>	Queue q; 
>	q.enQueue(1); 
>	q.enQueue(2); 
>	q.enQueue(3); 
>
>	cout << q.deQueue() << '\n'; 
>	cout << q.deQueue() << '\n'; 
>	cout << q.deQueue() << '\n'; 
>
>	return 0; 
>} 
>
>```
>
>
>
>**Method 2 (By making deQueue operation costly)  **
>
>         ```
>// CPP program to implement Queue using 
>// two stacks with costly deQueue() 
>#include <bits/stdc++.h> 
>using namespace std; 
>
>struct Queue { 
>	stack<int> s1, s2; 
>
>	// Enqueue an item to the queue 
>	void enQueue(int x) 
>	{ 
>		// Push item into the first stack 
>		s1.push(x); 
>	} 
>
>	// Dequeue an item from the queue 
>	int deQueue() 
>	{ 
>		// if both stacks are empty 
>		if (s1.empty() && s2.empty()) { 
>			cout << "Q is empty"; 
>			exit(0); 
>		} 
>
>		// if s2 is empty, move 
>		// elements from s1 
>		if (s2.empty()) { 
>			while (!s1.empty()) { 
>				s2.push(s1.top()); 
>				s1.pop(); 
>			} 
>		} 
>
>		// return the top item from s2 
>		int x = s2.top(); 
>		s2.pop(); 
>		return x; 
>	} 
>}; 
>
>// Driver code 
>int main() 
>{ 
>	Queue q; 
>	q.enQueue(1); 
>	q.enQueue(2); 
>	q.enQueue(3); 
>
>	cout << q.deQueue() << '\n'; 
>	cout << q.deQueue() << '\n'; 
>	cout << q.deQueue() << '\n'; 
>
>	return 0; 
>} 
>
>         ```
>
>

------



#### Which Data Structure should be used for implementing LRU Cache ?

> Queue which is implemented using a doubly linked list. The maximum size of the queue will be equal to the total number of frames available (cache size).The most recently used pages will be near rear end and least recently pages will be near front end.

------



