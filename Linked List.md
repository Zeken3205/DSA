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

**Time Complexity: O(n)**

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
### Approach:

-1. Initialize two pointers `prev` and `curr` to `NULL` and `head` respectively.
-2. Traverse the list until `curr` becomes `NULL`.
-3. Inside the loop, store the next node of `curr` in a temporary variable `f`.
-4. Set the next pointer of `curr` to `prev`.
-5. Move `prev` to `curr` and `curr` to `f`.
-6. After the loop, `prev` will point to the new head of the reversed list. Return `prev`.

### Time Complexity:
The time complexity of reversing a linked list iteratively is O(n), where 'n' is the number of nodes in the list, as it requires traversing the entire list once.
