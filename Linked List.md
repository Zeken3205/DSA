# Linked List

A linked list is a linear data structure where elements are stored in separate objects called nodes. Each node consists of two parts: data and a reference (or pointer) to the next node in the sequence. Unlike arrays, linked lists do not have a fixed size and allow efficient insertion and deletion operations at any position, albeit with the trade-off of slower access times.

## Types of Linked Lists

-1. **Singly Linked List**: In this type of linked list, each node contains data and a single pointer to the next node in the sequence.
   
-2. **Doubly Linked List**: Here, each node contains data and two pointers - one pointing to the previous node and one to the next node.
   
-3. **Circular Linked List**: Similar to singly or doubly linked lists, but the last node's pointer points back to the first node, creating a circular structure.

## Operations on Linked List

- **Insertion**: Adding a new node to the list.
- **Deletion**: Removing a node from the list.
- **Traversal**: Accessing each node in the list sequentially.
- **Searching**: Finding a specific node based on its value.
- **Concatenation**: Joining two linked lists together.

## Advantages and Disadvantages

### Advantages:
- Dynamic size: Linked lists can grow or shrink during execution, unlike arrays with a fixed size.
- Efficient insertion and deletion: These operations can be performed with constant time complexity if the position is known.
- No memory wastage: Memory is allocated dynamically as required.

### Disadvantages:
- Slower access time: Accessing an element at a specific position requires traversing the list from the beginning, resulting in linear time complexity.
- Extra memory overhead: Each node in a linked list requires additional memory for storing the pointer to the next node.
- Not cache-friendly: Due to scattered memory allocation, linked lists may not utilize cache efficiently compared to contiguous arrays.

## Implementation

Linked lists can be implemented using various programming languages, such as C++, Java, Python, etc. Below is a simple example of a singly linked list implemented in C++:

```cpp
#include <iostream>

class Node {
public:
    int data;
    Node* next;

    Node(int val) {
        data = val;
        next = nullptr;
    }
};

class LinkedList {
public:
    Node* head;

    LinkedList() {
        head = nullptr;
    }

    void insert(int val) {
        Node* newNode = new Node(val);
        if (!head) {
            head = newNode;
        } else {
            Node* temp = head;
            while (temp->next) {
                temp = temp->next;
            }
            temp->next = newNode;
        }
    }

    void display() {
        Node* temp = head;
        while (temp) {
            std::cout << temp->data << " ";
            temp = temp->next;
        }
        std::cout << std::endl;
    }
};

int main() {
    LinkedList list;
    list.insert(1);
    list.insert(2);
    list.insert(3);
    list.display();
    return 0;
}
```
## Count Nodes of Linked List

Given the head of a singly linked list of integers, the task is to find and return its length.

```cpp
/****************************************************************
Following is the class structure of the Node class:

    class Node
    {
    public:
        int data;
        Node *next;
        Node()
        {
            this->data = 0;
            next = NULL;
        }
        Node(int data)
        {
            this->data = data;
            this->next = NULL;
        }
        Node(int data, Node* next)
        {
            this->data = data;
            this->next = next;
        }
    };
*****************************************************************/

int length(Node *head)
{
    //Write your code here
    int cnt=0;
    Node* temp=head;
    while(temp){
        cnt++;
        temp=temp->next;
    }
    return cnt;
}
```

## Search in a Linked List

Given the head of a singly linked list of integers and a key `k`, the task is to search if the key exists in the linked list.

```cpp
/****************************************************************

Following is the class structure of the Node class:

template <typename T>
class Node
{
public:
    T data;
    Node<T> *next;
    Node()
    {
        this->data = 0;
        this->next = NULL;
    }
    Node(T data)
    {
        this->data = data;
        this->next = NULL;
    }
    Node(T data, T* next)
    {
        this->data = data;
        this->next = next;
    }
};

*****************************************************************/

int searchInLinkedList(Node<int> *head, int k) {
    // Write your code here.
    Node<int>*temp=head;
    while(temp){
        if(temp->data==k) return 1;
        temp=temp->next;
    }
    return 0;
}
```
**Time Complexity: O(n)**

## Introduction to Linked List

Linked lists are a linear data structure consisting of nodes where each node points to the next node in the sequence. They are dynamic in nature, allowing for efficient insertion and deletion operations.

```cpp
/**
 * Definition of linked list
 * class Node {
 *
 * public:
 *     int data;
 *     Node* next;
 *     Node() : data(0), next(nullptr) {}
 *     Node(int x) : data(x), next(nullptr) {}
 *     Node(int x, Node* next) : data(x), next(next) {}
 * };
 */

Node* constructLL(vector<int>& arr) {
    // Write your code here
    Node* head=new Node(arr[0]);
    Node* prev=head;
    for(int i=1;i<arr.size();i++){
        Node* temp=new Node(arr[i]);
        prev->next=temp;
        prev=prev->next;
    }
    return head;
}
```

## Delete Head of a Given Linked List

This function deletes the head node of a given linked list and returns the new head.

```cpp
/*
Following is the class structure of the Node class:

class Node
{
public:
    int data;
    Node *next;
    Node()
    {
        this->data = 0;
        next = NULL;
    }
    Node(int data)
    {
        this->data = data; 
        this->next = NULL;
    }
    Node(int data, Node* next)
    {
        this->data = data;
        this->next = next;
    }
};
*/

Node * deleteHead(Node *head) {
    // Write your code here.
    if (head == NULL) {
        // If there's no element, return NULL
        return NULL;
    }
    if (head->next == NULL) {
        // If there's only one element, delete it and return NULL
        delete head;
        return NULL;
    }

    Node* temp=head;
    head=head->next;
    delete temp;
    return head;
}
```

## Delete Last Node of a Linked List

This function deletes the last node of a given linked list and returns the modified list.

```cpp
/**
 * Definition for singly-linked list.
 * class Node {
 * public:
 *     int data;
 *     Node *next;
 *     Node() : data(0), next(nullptr) {}
 *     Node(int x) : data(x), next(nullptr) {}
 *     Node(int x, Node *next) : data(x), next(next) {}
 * };
 */

Node *deleteLast(Node *list){
    // Write your code here
    Node *temp=list;
    while(temp->next->next!=nullptr){
        temp=temp->next;
    }
    delete temp->next;
    temp->next=nullptr;
    return list;
}
```
**Time Complexity: O(n)**

## Delete the kth Element of a Linked List

This function deletes the kth element (0-based index) of a given linked list and returns the modified list.

```cpp
/****************************************************************
 
Following is the class structure of the Node class:

    class Node
    {
    public:
        int data;
        Node *next;
        Node(int data)
        {
            this->data = data;
            this->next = NULL;
        }
    };

*****************************************************************/

Node *deleteNode(Node *head, int pos)
{
    // Write your code here.
    if(head == NULL) return head;

    if (pos == 0)
    {
        Node *temp = head;
        head = head->next;
        delete temp;
    }
    else
    {
        Node* temp = deleteNode(head->next, pos - 1);
        head->next = temp;
    }
    return head;
}
```
**Time Complexity: O(n)**

## Insert Node at the Beginning of a Linked List

This function inserts a new node with the given value at the beginning of the linked list and returns the modified list.

```cpp
Node* insertAtFirst(Node* list, int newValue) {
    // Write your code here
    Node* temp = new Node(newValue, list);
    list = temp;
    return list;
}
```
**Time Complexity: O(1)**

## Insert at the Tail of a Linked List

This function inserts a new node with the given value at the tail (end) of the linked list and returns the modified list.

```cpp
/************************************************************

Following is the linkedList class structure:

class Node {
public:
    int data;
    Node *next;

    Node(int val) {
        this->data = val;
        next = NULL;
    }
};

************************************************************/

Node* insertEnd(Node* head, int k) {
    // Write your code here.
    if (head == nullptr) {
        head = new Node(k);
        return head;
    } 
    
    Node* curr=head;
    while(curr->next!=nullptr) curr=curr->next;
    Node* temp= new Node(k);
    curr->next=temp;
    return head;
}
```
**Time Complexity: O(n)**

## Insert Node Before a Given Value in a Linked List

This function inserts a new node with the given value `x` before the first occurrence of the value `val` in the linked list and returns the modified list.

```cpp
/****************************************************************
Following is the Linked list node structure already written

class Node
{
public:
    int data;
    Node* next;
    Node(int data)
    { 
        this->data = data;
        next = NULL;
    }
};
*****************************************************************/

Node* insertBeforeValue(Node* head, int x, int val){
    // Write your code here.
    
    if (head == nullptr)
        return nullptr;
    
    if(head->data==val){
        Node *temp= new Node(x);
        temp->next=head;
        head=temp;
        return head;
    }
    Node* prev=nullptr;
    Node* current=head;
    while(current!=nullptr&&current->data!=val){
        prev=current;
        current=current->next;
    }
    if(current==nullptr) return head;
    Node* newNode = new Node(x);
    prev->next = newNode;
    newNode->next = current;
    return head;
}
```

**Time Complexity: O(n)**

## Middle of the Linked List

This function returns the middle node of a singly linked list. If there are two middle nodes, it returns the second middle node.

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        int cmt=0;
        ListNode *temp=head;
        while(temp){
            cmt++;
            temp=temp->next;
        }
        ListNode *current=head;
        for(int i=1;i<(cmt/2)+1;i++){
            current=current->next;
        }
        head=current;
        return head;
    }
};
```
**Time Complexity: O(n)**


## Another method(Tortoise hare Floyd's Tortoise and Hare algorithm /Fast Slow Method)

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode *slow=head,*fast=head;
        while(fast!=NULL&&fast->next!=NULL){
            slow=slow->next;
            fast=fast->next->next;
        }
        return slow;
    }
};
```
**Approach:** Floyd's Tortoise and Hare algorithm


## Reverse a Linked List (Iterative)

This function reverses a given singly linked list iteratively and returns the head of the reversed list.

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev=NULL;
        ListNode* curr=head;
        while(curr!=NULL){
            ListNode* f =curr->next;
            curr->next=prev;
            prev=curr;
            curr=f;
        }
        return prev;
    }
};
```
**Aproach:**

- 1. Initialize two pointers `prev` and `curr` to `NULL` and `head` respectively.
- 2. Traverse the list until `curr` becomes `NULL`.
- 3. Inside the loop, store the next node of `curr` in a temporary variable `f`.
- 4. Set the next pointer of `curr` to `prev`.
- 5. Move `prev` to `curr` and `curr` to `f`.
- 6. After the loop, `prev` will point to the new head of the reversed list. Return `prev`.

### Time Complexity:
The time complexity of reversing a linked list iteratively is O(n), where 'n' is the number of nodes in the list, as it requires traversing the entire list once.


## Detect a Cycle in a Linked List

This function detects if a given singly linked list contains a cycle (i.e., a loop) or not.
Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

### Algorithm: Floyd's Tortoise and Hare algorithm

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (!head || !head->next || !head->next->next) 
            return false;
        ListNode *slow = head;
        ListNode *fast = head;
        while (fast != NULL && fast->next != NULL) { // if fast->next is null then fast->next->next will mean null->next which produces error.
            fast = fast->next->next;
            slow = slow->next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
};
```
**Aproach:**
- The solution uses the Floyd's Tortoise and Hare algorithm to detect a cycle in a linked list.
- Two pointers, slow and fast, are initialized to the head of the list.
- In each iteration, the slow pointer moves one step ahead while the fast pointer moves two steps ahead.
- If there is a cycle, eventually the fast pointer will catch up with or overtake the slow pointer.
- If at any point during the traversal, the slow and fast pointers meet, it indicates the presence of a cycle, and the function returns true.
- If the fast pointer reaches the end of the list (i.e., becomes NULL), it means there is no cycle, and the function returns false.


## Find the Starting Point of a Cycle in a Linked List

This function finds the starting point of a cycle in a given singly linked list.

### Algorithm: Floyd's Tortoise and Hare algorithm

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *slow = head, *fast = head;
        int s = 0;
        if (!(fast && fast->next && fast->next->next)) return NULL;
        while (fast != nullptr && fast->next != nullptr) {
            fast = fast->next->next;
            slow = slow->next;
            if (slow == fast) {
                s = 1;
                break;
            }
        }
        if (s == 0) return NULL;
        while (head != slow) {
            slow = slow->next;
            head = head->next;
        }
        return head;
    }
};
```
**Aproach:**
- Initialize two pointers, slow and fast, to the head of the linked list.
- Traverse the list with the fast pointer moving two steps at a time and the slow pointer moving one step at a time.
- If the pointers meet (i.e., there's a cycle), set a flag s to indicate it.
- If there's no cycle (s remains 0), return NULL.
- Once a cycle is detected, reset one of the pointers to the head of the list and move both pointers one step at a time until they meet again. The meeting point is the starting point of the cycle.

Time Complexity:
The time complexity of finding the starting point of a cycle in a linked list using Floyd's Tortoise and Hare algorithm is O(n), where 'n' is the number of nodes in the list. This algorithm involves traversing the list at most twice, making it efficient.


## Palindrome Linked List

This function checks whether a given singly linked list is a palindrome or not.

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> n;
        ListNode* temp = head;
        while (temp != NULL) {
            n.push_back(temp->val);
            temp = temp->next;
        }
        int start = 0, end = n.size() - 1;
        while (start <= end) {
            if (n[start] != n[end]) return false;
            start++;
            end--;
        }
        return true;
    }
};
```
**Approach:**
- Traverse the given linked list and store the values of each node in a vector.
- Use two pointers (start and end) initialized to the beginning and end of the vector, respectively.
- Compare elements at start and end positions of the vector.
- If the elements are not equal, return false (indicating the list is not a palindrome).
- Move the start pointer towards the end of the vector and the end pointer towards the beginning of the vector.
- Repeat this process until start crosses end or until the entire vector is checked.
- If all elements are equal, return true (indicating the list is a palindrome).
  
**Time Complexity:**
The time complexity of checking whether a linked list is a palindrome using this approach is O(n), where 'n' is the number of nodes in the list. This is because the algorithm traverses the entire list once to store the values in the vector and then compares the elements in the vector, which also takes linear time.

