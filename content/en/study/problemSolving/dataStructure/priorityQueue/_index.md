---
title: 📜Priority_Queue September 2022~December 2022
hide_date: true
reading_time: false
date: 2022-09-01
---

- A priority is assigned to the elements in the queue, and a representative case using the heap data structure is the priority queue.
    - A representative case that applies the heap data structure is the Priority Queue.
    - The Priority Queue is a type of queue that is sorted according to the assigned priorities.
    - When an element is pushed, the queue is sorted according to the given priority, and the pop operation happens at the front of the sorted queue. Since it is implemented using a heap data structure, the sorting process that occurs when pushing an element is performed in time complexity of O(log N).
    - **Although a priority queue can be implemented using arrays, linked lists, and other methods, the most efficient structure is the heap.**
    - **A priority queue is divided into a max-priority queue and a min-priority queue, depending on which element gets deleted first during the deletion operation.**
        - In a max-priority queue, the element with the highest priority is deleted first.
        - In a min-priority queue, the element with the lowest priority is deleted first.

- Implementation methods
    - Using arrays:
        - Using an unsorted array:
            
            → If using an unsorted array, insertion is the simplest; just append the new element to the end of the existing elements, so the **time complexity is O(1).** However, for deletion, you have to search through all elements based on priority, so the **time complexity is O(N).** This happens because the array is not sorted.
            
            → Disadvantage: After deleting an element from an arbitrary position, you need to shift the subsequent elements forward.
            
        - Using a sorted array:
            
            → Insertion requires searching for the appropriate position to insert the element. Sequential search or binary search can be used to speed up the search. After finding the position, you need to create space by shifting elements backward, so **the time complexity for insertion is O(N).** For deletion, since the array is sorted, the element at the front or back of the queue is deleted based on priority, so **the time complexity is O(1).**
            
        
    - Using linked lists:
        - Using an unsorted linked list:
            
            → For insertion, it is advantageous to insert at the first node. Unlike arrays, there’s no need to shift other elements, so **the time complexity is O(1).** For deletion, you have to traverse all nodes to find the node based on priority, so **the time complexity is O(N).**
            
        - Using a sorted linked list:
            
            → Insertion at the first node is advantageous. Why? Because reaching the last node has **a time complexity of O(N).** You need to traverse from the head pointer to NULL. Thus, inserting at the first node **has a time complexity of O(1).**
            
            → For deletion, you traverse the nodes and delete based on priority, so **the time complexity is O(N).** **The time complexity does not change based on whether the priority is high or low. It only depends on the sorting criteria, so it’s always O(N). Don’t get confused!**
            
            → Ultimately, there’s no difference in time complexity between this method and the array implementation.
            
        - Using a heap:
            
            → A heap is a type of complete binary tree designed specifically for priority queues. It maintains a semi-sorted state, meaning elements are not fully sorted but are not entirely unsorted either. In a heap, both insertion and deletion have a **time complexity of O(log N), making it much more efficient than other methods.**
            
            →**Note: You must understand the difference between O(N) and O(log N). We always consider the worst-case scenario when evaluating time complexity, not the best or average cases. The difference becomes significant with large numbers like 1024, 2048, etc., rather than small ones like 1, 2, 4, or 8.**
            
- Heap concept:
    
    → A heap is a binary tree where the parent node’s key is greater than or equal to the child node’s key.
    
    ex) **If A is the parent node of B, then key(A) ≥ key(B) is always true.**
    
    ![Figure8](/images/dataStructureImages/image8.jpg)
    
    Figure 10.5 shows examples of max-heaps and min-heaps. In (a), the condition key(parent node) ≥ key(child node) is always true, while in (b), key(parent node) ≤ key(child node) holds.
    
    → Note: The heap tree allows duplicate values, unlike the binary search tree, which does not allow duplicates.
    
    → Also, both types of heap trees share a common characteristic: they are both complete binary trees. **A heap must always maintain the structure of a complete binary tree.**
    
    ![Figure9](/images/dataStructureImages/image9.jpg)
    
- Heap implementation:

    Since the heap takes the form of a complete binary tree, there are no empty nodes in between. **The most effective data structure for storing a heap is an array.** +) To simplify program implementation, we can set the first index to 1 instead of 0. (This is just for convenience.)
    
    ![Figure10](/images/dataStructureImages/image11.jpg)
    
    Referring to the following figure, you can easily calculate the indices. **If the heap contains more nodes than shown in the figure, level traversal may occur for the child nodes, which could result in a time complexity of O(N).** Therefore, we use simple formulas to calculate the indices of the child nodes.
    
    - **Left child’s index = (Parent’s index) * 2**
    - **Right child’s index = (Parent’s index) * 2 + 1**
    - **Parent’s index = (Child’s index) / 2**

- Basic usage
    - You can use it in the same way as the queue by including #include <queue>.
    - priority_queue<Type, Container, Comparator> variable_name
    → Declares a priority queue that sorts elements based on the comparator.
    - priority_queue<Type> variable_name
    → Declares a priority queue that sorts elements in descending order by default.
    → ex) priority_queue<int, vector<int>, greater<int>> pq; (To sort in ascending order, use `greater`.) By default, it sorts in descending order.
    - Other basic functions are the same as in a regular queue.

- Example code:

    ```cpp
    //Descending order

    #include <queue>
    #include <iostream>
    using namespace std;

    int main() {
      // Declare the priority queue using <type, container, comparator>.
      // Without using any comparator, it defaults to sorting integers in descending order.
      priority_queue <int, vector<int>> pq;
      
      pq.push(5);
      pq.push(3);
      pq.push(6);
      pq.push(7);
    
      while(!pq.empty()) {
        int temp = pq.top();
        cout << temp;
        pq.pop();
      }
      // Output
      // 7653
      return 0;
    }
    ```

    ```cpp
    //Ascending order
    #include <queue>
    #include <iostream>
    using namespace std;

    int main() {
      // Declare the priority queue using <type, container, comparator>.
      // Using greater<int> as a comparator to prioritize smaller integers.
      priority_queue <int, vector<int>, greater<int>> pq;
      
      pq.push(5);
      pq.push(3);
      pq.push(6);
      pq.push(7);
    
      while(!pq.empty()) {
        int temp = pq.top();
        cout << temp;
        pq.pop();
      }
      // Output
      // 3567
      return 0;
    }
    ```

    ```cpp
    #include <queue>
    #include <iostream>
    using namespace std;

    // Declare a comparator
    // For int types a and b,
    // Returning a > b prints in ascending order.
    // (Returning a < b prints in descending order.)
    struct cmp {
      bool operator()(int a, int b) {
        return a > b;
      }
    };

    int main() {
      priority_queue <int, vector<int>, cmp> pq;
      
      pq.push(5);
      pq.push(3);
      pq.push(6);
      pq.push(7);
    
      while(!pq.empty()) {
        int temp = pq.top();
        cout << temp;
        pq.pop();
      }
      // Output
      // 3567
      return 0;
    }
    ```
