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

Another solution:
```javascript
var twoSum = function(nums, target) {
    const complement = {}
    for(let i = 0; i < nums.length; i++){
        let diff = target - nums[i]
        if(complement[diff] !== undefined){
            return [complement[diff], i]
        }
        complement[nums[i]] = i
    }
};
```
This one is more efficient that the previous, using 0ms of runtime compared to 3ms of runtime. 

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

# Merge Strings Alternately
You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._
**Example 1:**

**Input:** word1 = "abc", word2 = "pqr"
**Output:** "apbqcr"
**Explanation:** The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r

**Example 2:**

**Input:** word1 = "ab", word2 = "pqrs"
**Output:** "apbqrs"
**Explanation:** Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s

**Example 3:**

**Input:** word1 = "abcd", word2 = "pq"
**Output:** "apbqcd"
**Explanation:** Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d

**Constraints:**
- `1 <= word1.length, word2.length <= 100`
- `word1` and `word2` consist of lowercase English letters.

My answer:
```javascript
/**
 * @param {string} word1
 * @param {string} word2
 * @return {string}
 */

var mergeAlternately = function(word1, word2) {
    const result = []
    for(let i = 0; i < word1.length; i++){
        result[i * 2] = word1[i]
    }

    for(let i = 0; i < word2.length; i++){
        result[(i*2)+1] = word2[i]
    }
    return result.join('')
};

//initialize two pointers, first and second
//loop over each letter
//str1 = [0, 2, 4]
//str2 = [1, 3, 5]

//time complexity: O(n) + O(m) + O(n + m) = 2 O(n+m) => O(n+m)
//space complexity: O(n+m)
```

Another solution that utilizes only one loop:
```javascript
var mergeAlternately = function(word1, word2) {
	let merged = []; 
	
	for (let i = 0; i < Math.max(word1.length, word2.length); i++) { 
		if (i < word1.length) { merged.push(word1[i]); } 
		if (i < word2.length) { merged.push(word2[i]); } 
	} 
	
	return merged.join(""); 
};
```

# Best Time to Buy and Sell Stock
You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

**Example 1:**

**Input:** prices = [7,1,5,3,6,4]
**Output:** 5
**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

**Example 2:**

**Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** In this case, no transactions are done and the max profit = 0.

**Constraints:**

- `1 <= prices.length <= 105`
- `0 <= prices[i] <= 104`

My answer:
```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */

var maxProfit = function(prices) {
    let lowestPrice = prices[0]
    let maxProfit = 0

    for(let i = 1; i < prices.length; i++){
        if(prices[i] < lowestPrice){
            lowestPrice = prices[i]
        }
        if( (prices[i] - lowestPrice) > maxProfit){
            maxProfit = prices[i] - lowestPrice
        }
    }

    return maxProfit
};
//Time complexity: O(n)
//Space complexity: O(1)
```
Using greedy algo. Create two variables, one to keep track of the lowest price and one to keep track of the max profit. Scan from left to right, updating both lowest price seen and maximum profit gained from selling. 

# Palindrome Number
Given an integer `x`, return `true` _if_ `x` _is a palindrome_, and_ `false` _otherwise_.

**Example 1:**

**Input:** x = 121
**Output:** true
**Explanation:** 121 reads as 121 from left to right and from right to left.

**Example 2:**

**Input:** x = -121
**Output:** false
**Explanation:** From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

**Example 3:**

**Input:** x = 10
**Output:** false
**Explanation:** Reads 01 from right to left. Therefore it is not a palindrome.

**Constraints:**

- `-231 <= x <= 231 - 1`

**Follow up:** Could you solve it without converting the integer to a string?

My answer:
```javascript
var isPalindrome = function(x) {
	if(x < 0) return false
	
    let arr = x.toString().split('')
    let i = 0, j = arr.length - 1
    while(i <= j){
        if(arr[i] !== arr[j]) return false
        i++
        j--
    }
    return true
};
//Time Complexity: O(n) + O(n) + O(logn) => O(nlogn)
//Space Complexity: O(n)
```
It's faster to omit the .split('') because string indexing is fast and efficient in JavaScript. 

Better approach
```javascript
var isPalindrome = function(x) {
    if (x < 0 || (x % 10 === 0 && x !== 0)) return false;
    
    let reversed = 0;
    let original = x;
    
    while (x > 0) {
        reversed = reversed * 10 + (x % 10);
        x = Math.floor(x / 10);
    }
    
    return original === reversed;
};
//Time Complexity: O(logn)
//Space Complexity: O(1)
```
## Step-by-Step Algorithm

**Input:** An integer `x`  
**Output:** Boolean indicating if `x` is a palindrome

1. **Handle edge cases:**
    
    - If `x < 0`, return `false` (negative numbers can't be palindromes)
        
    - If `x` ends with 0 and `x ≠ 0`, return `false` (numbers ending with 0 can't be palindromes except 0 itself)
        
2. **Initialize variables:**
    
    - `original = x` (store original value for comparison)
        
    - `reversed = 0` (will store the reversed number)
        
3. **Reverse the number digit by digit:**
    
    text
    

While x > 0:
    a. Extract last digit: lastDigit = x % 10
    b. Append to reversed: reversed = reversed × 10 + lastDigit  
    c. Remove last digit: x = floor(x / 10)

- **Compare and return result:**
    
    - Return `true` if `original == reversed`, otherwise `false`

# Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

**Input:** strs = ["flower","flow","flight"]
**Output:** "fl"

**Example 2:**

**Input:** strs = ["dog","racecar","car"]
**Output:** ""
**Explanation:** There is no common prefix among the input strings.

**Constraints:**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters if it is non-empty.

My answer:
```javascript
var longestCommonPrefix = function(strs) {
    let check=strs[0]

    for(let i = 1; i < strs.length; i++){
        const word = strs[i]
  
        for(let j = 0; j < word.length; j++){
            if(word[j] !== check[j]){
                check = check.slice(0, j)
                break;
            }
        }

        if(word.length < check.length){
            check = check.slice(0, word.length)
        }
    }

    return check
};
//define check as first element in arr
//loop over arr, checking each char
//cut off the loop once characters stop matching
//in cases where word < check, slice it after inner loop
//Time Complexity: O(n*m)
//Space Complexity: O(1)
```

# Majority Element
Given an array `nums` of size `n`, return _the majority element_.
The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

**Example 1:**
**Input:** nums = [3,2,3]
**Output:** 3

**Example 2:**
**Input:** nums = [2,2,1,1,1,2,2]
**Output:** 2

**Constraints:**
- `n == nums.length`
- `1 <= n <= 5 * 104`
- `-109 <= nums[i] <= 109`

**Follow-up:** Could you solve the problem in linear time and in `O(1)` space?

My answer:
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    let candidate = null, count = 0
    for(let i = 0; i < nums.length; i++){
        if(count===0){
            candidate = nums[i]
        }
        nums[i] === candidate ? count++ : count--
    }

    return candidate
};
//var to store majority element and a counter
//each loop, increment or decrement based on element comparison
//if count is zero then set the current element to candidate
```

# Valid Parentheses
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

**Input:** s = "()"

**Output:** true

**Example 2:**

**Input:** s = "()[]{}"

**Output:** true

**Example 3:**

**Input:** s = "(]"

**Output:** false

**Example 4:**

**Input:** s = "([])"

**Output:** true

**Example 5:**

**Input:** s = "([)]"

**Output:** false

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of parentheses only `'()[]{}'`.

My answer:
```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const stack = []
    const openBrackets = new Set(['(', '[', '{'])
    const closedBrackets = new Set([')', ']', '}'])
    const match = {
        ')' : '(',
        ']' : '[', 
        '}' : '{'
    }
    for(let c of s){
        if(openBrackets.has(c)){
            stack.push(c)
        }else if(closedBrackets.has(c)){
            if(stack.length===0 || stack.pop() !== match[c]){
                return false
            }
        }
    }

    return stack.length === 0 
};
//const stack = []
//define variables for closed brackets, open brackets and a matching obj
//loop over str
//check if open or closed bracket
//open = add to stack
//closed = check stack and compare, if doesn't match return false
//loop ends -> return true if stack length is zero, false otherwise
```

# Remove Element
Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm). The order of the elements may be changed. Then return _the number of elements in_ `nums` _which are not equal to_ `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}

If all assertions pass, then your solution will be **accepted**.

**Example 1:**

**Input:** nums = [3,2,2,3], val = 3
**Output:** 2, nums = [2,2,_,_]
**Explanation:** Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).

**Example 2:**

**Input:** nums = [0,1,2,2,3,0,4,2], val = 2
**Output:** 5, nums = [0,1,4,0,3,_,_,_]
**Explanation:** Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).

**Constraints:**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

My Answer:
```javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */

var removeElement = function(nums, val) {
    let last = nums.length - 1
    let count = 0
    for(let i = 0; i < nums.length; i++){
        if(nums[i] === val){
            while(nums[last] === val){ last-- }
            nums[i] = nums[last]
            last--
            count++
        }
    }

    return nums.length - count
};
```
Pointer looking at last value in the array. When the current value === val, ensure that the pointer at the end is not equal to the val and then place it in the current slot. We have a 'count' variable for the end when we return k where k is equal to the first k elements of the nums array. 
[3, 2, 2, 3], val = 3

A more efficient answer using the same two pointer concept:
```javascript
var removeElement = function(nums, val) {
    let k = 0; // Pointer for next position to place non-val elements
    
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== val) {
            nums[k] = nums[i];
            k++;
        }
    }
    
    return k;
};
```

For `nums = [3,2,2,3]`, `val = 3`:
```javascript
i=0: nums[0]=3 (val) → skip, k=0, nums=[3,2,2,3]
i=1: nums[1]=2 (!val) → nums[0]=2, k=1, nums=[2,2,2,3]  
i=2: nums[2]=2 (!val) → nums[1]=2, k=2, nums=[2,2,2,3]
i=3: nums[3]=3 (val) → skip, k=2, nums=[2,2,2,3]
```


# Search Insert Position
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

**Input:** nums = [1,3,5,6], target = 5
**Output:** 2

**Example 2:**

**Input:** nums = [1,3,5,6], target = 2
**Output:** 1

**Example 3:**

**Input:** nums = [1,3,5,6], target = 7
**Output:** 4

**Constraints:**

- `1 <= nums.length <= 104`
- `-104 <= nums[i] <= 104`
- `nums` contains **distinct** values sorted in **ascending** order.
- `-104 <= target <= 104`
My Answer:
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */

var searchInsert = function(nums, target) {
    let l = 0, r = nums.length-1
    while(l <= r){
        let m = Math.floor((l+r)/2)
        if(target === nums[m]) return m
        target < nums[m] ? r = m - 1 : l = m + 1
    }

    return l
};
```