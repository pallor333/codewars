# Linked List Cycle
Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.
**Example 1:**
![[circularlinkedlist.png]]
**Input:** head = [3,2,0,-4], pos = 1
**Output:** true
**Explanation:** There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

**Example 2:**
![[circularlinkedlist_test2.png]]
**Input:** head = [1,2], pos = 0
**Output:** true
**Explanation:** There is a cycle in the linked list, where the tail connects to the 0th node.

**Example 3:**
![[circularlinkedlist_test3-1.png]]
**Input:** head = [1], pos = -1
**Output:** false
**Explanation:** There is no cycle in the linked list.

**Constraints:**

- The number of the nodes in the list is in the range `[0, 104]`.
- `-105 <= Node.val <= 105`
- `pos` is `-1` or a **valid index** in the linked-list.

**Follow up:** Can you solve it using `O(1)` (i.e. constant) memory?

My answer
```javascript
/**

 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */

var hasCycle = function(head) {
    if(!head) return false
  
    let slow = head //one jump
    let fast = head //two jump
  
    while(fast && fast.next){
        slow = slow.next
        fast = fast.next.next
        if(slow === fast){
            return true
        }
    }
    return false
};
```

# Reverse Linked List
Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.
**Example 1:**
![[rev1ex1.jpg]]
**Input:** head = [1,2,3,4,5]
**Output:** [5,4,3,2,1]

**Example 2:**
![[rev1ex2.jpg]]
**Input:** head = [1,2]
**Output:** [2,1]

**Example 3:**

**Input:** head = []
**Output:** []

**Constraints:**

- The number of nodes in the list is the range `[0, 5000]`.
- `-5000 <= Node.val <= 5000`

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

My answer:
```javascript
/**

 * Definition for singly-linked list.

 * function ListNode(val, next) {

 *     this.val = (val===undefined ? 0 : val)

 *     this.next = (next===undefined ? null : next)

 * }

 */

/**

 * @param {ListNode} head

 * @return {ListNode}

 */

var reverseList = function(head) {
    let current = head, prev = null
    while(current){
        let next = current.next
        current.next = prev
        prev = current
        current = next
    }
    return prev
};
```

# Palindrome Linked List
Given the `head` of a singly linked list, return `true` _if it is a_ _or_ `false` _otherwise_.
**Example 1:**
![[pal1linked-list.jpg]]
**Input:** head = [1,2,2,1]
**Output:** true

**Example 2:**
![[pal2linked-list.jpg]]
**Input:** head = [1,2]
**Output:** false

**Constraints:**

- The number of nodes in the list is in the range `[1, 105]`.
- `0 <= Node.val <= 9`

**Follow up:** Could you do it in `O(n)` time and `O(1)` space?

My answer:
```javascript
var isPalindrome = function(head) {

    //Find middle using 2pointers
    let slow = head, fast = head
    while(fast && fast.next){
        slow = slow.next
        fast = fast.next.next
    }

    //reverse list [1,2] -> [2,1]
    const half = reverseList(slow)
	
	//loop and compare values
    let firstHalf = head, secondHalf = half
    while(secondHalf){
        if(firstHalf.val !== secondHalf.val){
            return false
        }
        firstHalf = firstHalf.next
        secondHalf = secondHalf.next
    }

    return true //all values match = true
};

  
//helper function to reverseList
function reverseList(head){
    let prev = null, current = head
    while(current){
        let next = current.next
        current.next = prev
        prev = current
        current = next
    }

    return prev
}
```