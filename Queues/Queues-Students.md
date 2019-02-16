# Queues

### Introduction

Queue is also an abstract data type or a linear data structure, just like stack data structure, in which the first element is inserted from one end called the REAR(also called tail), and the removal of existing element takes place from the other end called as FRONT(also called head).

This makes queue as FIFO(First in First Out) data structure, which means that element inserted first will be removed first.

### Basic Features

- Like stack, queue is also an ordered list of elements of similar data types.
-  Queue is a FIFO( First in First Out ) structure.
- Once a new element is inserted into the Queue, all the elements inserted before the new element in the queue must be removed, to remove the new element.
- peek() function is oftenly used to return the value of first element without dqueueing it.

### Operations

Queue operations may involve initializing or defining the queue, utilizing it, and then completely erasing it from the memory. Here we shall try to understand the basic operations associated with queues −

- enqueue() − add (store) an item to the queue.
-  dequeue() -- remove ( access ) an item from the queue

### Implementation

Queue can be implemented as an Array and Linked List

### Code

```c++

        #include<iostream>
        
        using namespace std;
        
        #define SIZE 10
        
        class Queue
        {
            int a[SIZE];
            int rear;   //same as tail
            int front;  //same as head
            
            public:
            Queue()
            {
                rear = front = -1;
            }
            
            //declaring enqueue, dequeue and display functions
            void enqueue(int x);     
            int dequeue();
            void display();
        };
        
        // function enqueue - to add data to queue
        void Queue :: enqueue(int x)
        {
            if(front == -1) {
                front++;
            }
            if( rear == SIZE-1)
            {
                cout &lt;&lt; "Queue is full";
            }
            else
            {
                a[++rear] = x;
            }
        }
        
        // function dequeue - to remove data from queue
        int Queue :: dequeue()
        {
            return a[++front];  // following approach [B], explained above
        }
        
        // function to display the queue elements
        void Queue :: display()
        {
            int i;
            for( i = front; i &lt;= rear; i++)
            {
                cout &lt;&lt; a[i] &lt;&lt; endl;
            }
        }
        
        // the main function
        int main()
        {
            Queue q;
            q.enqueue(10);
            q.enqueue(100);
            q.enqueue(1000);
            q.enqueue(1001);
            q.enqueue(1002);
            q.dequeue();
            q.enqueue(1003);
            q.dequeue();
            q.dequeue();
            q.enqueue(1004);
            
            q.display();
            
            return 0;
        }
```



