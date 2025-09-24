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

# Two Sum
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

**Follow-up:** Can you come up with an algorithm that is less than `O(n2)` time complexity?

My answer: 
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */

var twoSum = function(nums, target) {
    const hash = {}
    for(let i = 0; i < nums.length; i++){
        const diff = target - nums[i]
        if(hash[nums[i]] !== undefined){
            return [hash[nums[i]], i]
        }
        hash[diff] = i
    }
};
//create hashmap
//loop over arr, storing {key: value} as {target-nums : index}
//check if val is in hash, if it is then match is found -> return
//loop over nothing found -> return false
```
Remember to use for loops instead of forEach() if you want to 'return' inside of the loop. 

# Merge Sorted Array
You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

**Example 1:**

**Input:** nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
**Output:** [1,2,2,3,5,6]
**Explanation:** The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.

**Example 2:**

**Input:** nums1 = [1], m = 1, nums2 = [], n = 0
**Output:** [1]
**Explanation:** The arrays we are merging are [1] and [].
The result of the merge is [1].

**Example 3:**

**Input:** nums1 = [0], m = 0, nums2 = [1], n = 1
**Output:** [1]
**Explanation:** The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.

**Constraints:**

- `nums1.length == m + n`
- `nums2.length == n`
- `0 <= m, n <= 200`
- `1 <= m + n <= 200`
- `-109 <= nums1[i], nums2[j] <= 109`

**Follow up:** Can you come up with an algorithm that runs in `O(m + n)` time?

My answer:
```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */

var merge = function(nums1, m, nums2, n) {
    let firstPointer = m - 1, secondPointer = n - 1
    let i = m + n - 1

    // Merge while both arrays have elements left
    while(i >= 0 && firstPointer >= 0 && secondPointer >= 0){
        if(nums1[firstPointer] > nums2[secondPointer]){
            nums1[i] = nums1[firstPointer]
            firstPointer--
        }else{
            nums1[i] = nums2[secondPointer]
            secondPointer--
        }
        i--
    }
    
    // Copy any leftovers from nums2
    while (secondPointer >= 0) {
        nums1[i] = nums2[secondPointer];
        secondPointer--;
        i--;
    }
};
```
Use two pointer: we start at the end of the array using two pointers for each array as well as a third pointer to keep track of where we are in nums1. If nums1 = [1, 2, 3, 0, 0, 0] then we have a pointer at the 3 and the last 0. Each loop we compare a real element of nums1 (not the 0 placeholder) and nums2, adding whichever is greater. 
The while loop lasts until i, firstPointer or secondPointer goes below zero. We still may run into issues where the second array isn't totally added to the array. Therefore we do another loop, copying any leftovers from nums2 into num1s. 

Another solution:
```javascript
var merge = function(nums1, m, nums2, n) {
    let firstPointer = m - 1, secondPointer = n - 1, current = m + n - 1

    while(secondPointer >= 0){
        if(firstPointer >= 0 && nums1[firstPointer] > nums2[secondPointer]){
            nums1[current] = nums1[firstPointer]
            firstPointer--
        }else{
            nums1[current] = nums2[secondPointer]
            secondPointer--
        }
        current--
    }
};
```
This solution only requires one loop, using the secondPointer or nums2 as an end condition. The idea is that we loop until the second array is completely empty but with more streamlined logic. The first conditional checks if firstPointer >= 0 and if nums1 > nums2, adding nums1 to the array if true. The idea is that if firstPointer drops below 0, then all we have to do is add elements from num2. 
Step by step algo:
1) Initialize Pointers: firstPointer -> points to last element of nums1, secondPOinter -> points to last element of nums2, current -> points to last index of nums1
2) Iterate while secondPointer is non-negative: Loop continues until all elements from nums2 have been merged into nums1
3) Compare Elements and Merge: If firstPointer is non-negative and the element at nums1 > nums2 then place nums1 at the current index and decrement firstPointer. OTHERWISE place nums2 at the current index and decrement secondPointer
4) Move current index to the left. 
5) Loop ends when all elements from num2 have been placed in nums1. 