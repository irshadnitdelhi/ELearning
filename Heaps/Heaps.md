# Binary Heaps

------

### Introduction

A Heap is a special Tree-based data structure in which the tree is a complete binary tree. Generally Heaps can be of two types :

1. **Max Heap** : The key present at the root node must be greatest among the keys present at all of it's children. The same property must be recursively true for all sub-trees in that Binary Tree.
2. **Min - Heap : ** The key present at the root node must be minimum among the keys present at all of its children. The same property must be recursively true for all sub-trees in that Binary Tree

------

### Video

<iframe width="419" height="374" src="https://www.youtube.com/embed/uZj0hetLFHU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



------



### Representation 

It's a complete tree ( All levels are completely filled except possibly the last level and the last level has all keys as left as possible). This property makes them suitable to be stored in an array.

- The root element will be at Arr[0]

- node.parent()  -->  returns Arr[(i-1)/2]

- node.leftChild() --> returns Arr[ (2*i )+1 ]

- node.rightChild() --> return Arr[ (2*i)+2 ]

  

![](https://www.geeksforgeeks.org/wp-content/uploads/binaryheap.png)

------

### Operations

1. **getMin()  ** : It returns the root element of Min Heap. The time complexity is *O(1)*
2. **extractMin() ** : Removes the minimum element (root element) from Min Heap. The time complexity is O(*log n*) as this operation needs to maintain the heap property by calling heapify() after removing the root
3. **decreaseKey() ** : Decreases the value of key. The time complexity of this operation is O(*log n*).
4. **insert() ** : Inserting a new key takes O(*log n*) time. We add a new key at the end of the tree and call heapify() to maintain the heap property.
5. **delete()** : Deleting a key also takes O(*log n*) time. We replace the key to be deleted with minimum infinite by calling decreaseKey(). After decreaseKey(), the minus infinite value must reach root, so we call extractMin() to remove the key.

-------

### Code

```C++
// A C++ program to demonstrate common Binary Heap Operations 
#include<iostream> 
#include<climits> 
using namespace std; 

// Prototype of a utility function to swap two integers 
void swap(int *x, int *y); 

// A class for Min Heap 
class MinHeap 
{ 
	int *harr; // pointer to array of elements in heap 
	int capacity; // maximum possible size of min heap 
	int heap_size; // Current number of elements in min heap 
public: 
	// Constructor 
	MinHeap(int capacity); 

	// to heapify a subtree with the root at given index 
	void MinHeapify(int ); 

	int parent(int i) { return (i-1)/2; } 

	// to get index of left child of node at index i 
	int left(int i) { return (2*i + 1); } 

	// to get index of right child of node at index i 
	int right(int i) { return (2*i + 2); } 

	// to extract the root which is the minimum element 
	int extractMin(); 

	// Decreases key value of key at index i to new_val 
	void decreaseKey(int i, int new_val); 

	// Returns the minimum key (key at root) from min heap 
	int getMin() { return harr[0]; } 

	// Deletes a key stored at index i 
	void deleteKey(int i); 

	// Inserts a new key 'k' 
	void insertKey(int k); 
}; 

// Constructor: Builds a heap from a given array a[] of given size 
MinHeap::MinHeap(int cap) 
{ 
	heap_size = 0; 
	capacity = cap; 
	harr = new int[cap]; 
} 

// Inserts a new key 'k' 
void MinHeap::insertKey(int k) 
{ 
	if (heap_size == capacity) 
	{ 
		cout << "\nOverflow: Could not insertKey\n"; 
		return; 
	} 

	// First insert the new key at the end 
	heap_size++; 
	int i = heap_size - 1; 
	harr[i] = k; 

	// Fix the min heap property if it is violated 
	while (i != 0 && harr[parent(i)] > harr[i]) 
	{ 
	swap(&harr[i], &harr[parent(i)]); 
	i = parent(i); 
	} 
} 

// Decreases value of key at index 'i' to new_val. It is assumed that 
// new_val is smaller than harr[i]. 
void MinHeap::decreaseKey(int i, int new_val) 
{ 
	harr[i] = new_val; 
	while (i != 0 && harr[parent(i)] > harr[i]) 
	{ 
	swap(&harr[i], &harr[parent(i)]); 
	i = parent(i); 
	} 
} 

// Method to remove minimum element (or root) from min heap 
int MinHeap::extractMin() 
{ 
	if (heap_size <= 0) 
		return INT_MAX; 
	if (heap_size == 1) 
	{ 
		heap_size--; 
		return harr[0]; 
	} 

	// Store the minimum value, and remove it from heap 
	int root = harr[0]; 
	harr[0] = harr[heap_size-1]; 
	heap_size--; 
	MinHeapify(0); 

	return root; 
} 


// This function deletes key at index i. It first reduced value to minus 
// infinite, then calls extractMin() 
void MinHeap::deleteKey(int i) 
{ 
	decreaseKey(i, INT_MIN); 
	extractMin(); 
} 

// A recursive method to heapify a subtree with the root at given index 
// This method assumes that the subtrees are already heapified 
void MinHeap::MinHeapify(int i) 
{ 
	int l = left(i); 
	int r = right(i); 
	int smallest = i; 
	if (l < heap_size && harr[l] < harr[i]) 
		smallest = l; 
	if (r < heap_size && harr[r] < harr[smallest]) 
		smallest = r; 
	if (smallest != i) 
	{ 
		swap(&harr[i], &harr[smallest]); 
		MinHeapify(smallest); 
	} 
} 

// A utility function to swap two elements 
void swap(int *x, int *y) 
{ 
	int temp = *x; 
	*x = *y; 
	*y = temp; 
} 

// Driver program to test above functions 
int main() 
{ 
	MinHeap h(11); 
	h.insertKey(3); 
	h.insertKey(2); 
	h.deleteKey(1); 
	h.insertKey(15); 
	h.insertKey(5); 
	h.insertKey(4); 
	h.insertKey(45); 
	cout << h.extractMin() << " "; 
	cout << h.getMin() << " "; 
	h.decreaseKey(2, 1); 
	cout << h.getMin(); 
	return 0; 
} 

```

------

### Applications

1. **Heap Sort ** : Heap sort uses Binary Heap to sort an array in O(*n log(n)*) time
2. **Priority Queue ** : Priority Queues can be efficiently implemented using Binary Heap because it supports insert(), delete(), and extractMin(),decreaseKey() operations in *O(log n)* time. Binomial Heap and Fibonacci Heap are the other variants that uses further optimization.
3. **Graph Algorithms** :  The priority queues are especially used in Graph Algorithms like Dijkstra's Shortest Path and Prim's Minimum Spanning Tree.
4. **Miscellaneous Problems** : 
   1. K'th Largest Element in an array
   2. Sort an almost sorted arry
   3. Marge K Sorted Arrays





