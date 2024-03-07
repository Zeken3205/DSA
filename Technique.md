# Floyd's Tortoise and Hare algorithm (Slow Fast Loop Detection)

Floyd's Tortoise and Hare algorithm, also known as Floyd's cycle-finding algorithm or the "slow and fast pointers" algorithm, is a popular technique used to detect cycles in a linked list or any cyclic structure. It was devised by Robert W. Floyd in 1967.

## Algorithm Steps:

### Initialization:
Start with two pointers, often referred to as the "tortoise" and the "hare", both initially pointing to the head of the linked list.

### Movement:
Move the tortoise pointer one step at a time and the hare pointer two steps at a time through the linked list.

### Detection of a Cycle:
- If there is no cycle, the hare will reach the end of the list (null pointer) before or at the same time as the tortoise.
- If there is a cycle, however, the hare will eventually catch up to the tortoise within the cycle.

### Cycle Detection:
If the hare ever equals the tortoise (i.e., they meet at the same node), then there is a cycle in the linked list.

### Finding the Start of the Cycle:
Once a cycle is detected, move one of the pointers back to the head of the linked list while keeping the other pointer at the meeting point. Then move both pointers one step at a time until they meet again. The meeting point is the start of the cycle.

This algorithm is very efficient, with a time complexity of O(n), where n is the number of nodes in the linked list. It's also space-efficient as it only requires two pointers regardless of the size of the linked list.

## C++ Implementation:

```cpp
#include <iostream>

struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(nullptr) {}
};

bool hasCycle(ListNode *head) {
    if (head == nullptr || head->next == nullptr)
        return false;
    
    ListNode *tortoise = head;
    ListNode *hare = head;
    
    while (hare != nullptr && hare->next != nullptr) {
        tortoise = tortoise->next;
        hare = hare->next->next;
        
        if (tortoise == hare)
            return true; // Cycle detected
    }
    
    return false; // No cycle found
}

int main() {
    // Create a sample linked list with a cycle
    ListNode *head = new ListNode(1);
    head->next = new ListNode(2);
    head->next->next = new ListNode(3);
    head->next->next->next = new ListNode(4);
    head->next->next->next->next = head->next; // Create a cycle from node 4 to node 2
    
    // Check if the linked list has a cycle
    if (hasCycle(head))
        std::cout << "The linked list contains a cycle.\n";
    else
        std::cout << "The linked list does not contain a cycle.\n";
    
    // Clean up memory
    ListNode *current = head;
    while (current != nullptr) {
        ListNode *temp = current;
        current = current->next;
        delete temp;
    }
    
    return 0;
}
```
