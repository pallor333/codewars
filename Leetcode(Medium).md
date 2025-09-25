# Add Two Numbers
You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
**Example 1:**
![[addtwonumber1.jpg]]
**Input:** l1 = [2,4,3], l2 = [5,6,4]
**Output:** [7,0,8]
**Explanation:** 342 + 465 = 807.

**Example 2:**

**Input:** l1 = [0], l2 = [0]
**Output:** [0]

**Example 3:**

**Input:** l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
**Output:** [8,9,9,9,0,0,0,1]

**Constraints:**
- The number of nodes in each linked list is in the range `[1, 100]`.
- `0 <= Node.val <= 9`
- It is guaranteed that the list represents a number that does not have leading zeros.

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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */

var addTwoNumbers = function(l1, l2) {
    let num1 = [], num2 = []

    while(l1){
        num1.push(l1.val)
        l1 = l1.next
    }
    while(l2){
        num2.push(l2.val)
        l2 = l2.next
    }

    console.log("linked list values:",num1, num2)
    let numStr1 = num1.reverse().join('') //O(n) * 2
    let numStr2 = num2.reverse().join('') //O(m) * 2
    console.log("numStr:", numStr1, numStr2)
    let sum = (BigInt(numStr1) + BigInt(numStr2)).toString().split('').reverse() // O(n+m) * 4
    console.log("sum:", sum)

  
    let newList = new ListNode(+sum[0])
    let current = newList
    console.log(newList, current)
    for(let i = 1; i < sum.length; i++){
        let newNode = new ListNode(+sum[i])
        console.log(newList, newNode)
        current.next = newNode
        current = current.next
    }

    return newList
};

//given two linked lists, each node with 1 digit
//reverse each list and sum: 243, 563 reversed = 342 + 465 === 807
//output: single linked list with new numbers

  
//iterate over each list, adding number to array [2,4,3] and [5,6,4] //O(n)
//reverse each arr, join('') into str, cast to number to add O(n) * 3
//split string and then reverse()   //O(n) * 2
//Time Complexity: O(n) + O(m) + O(n+m)*2 + O(n+m)*4 + O(n+m) = O(n+m) * 8 => O(n+m)
//Space Complexity: O(n+m) + O(n+m) = O(n+m) * 2 => O(n+m)
```
Removing the console.logs and changing everything to const speeds it up from 43ms to 5ms runtime. Still slow. 

A better answer with only one pass:
```javascript
var addTwoNumbers = function(l1, l2) {
    let dummy = new ListNode()
    let current = dummy
    let total = 0, carry = 0

    while(l1 || l2 || carry){
        total = carry
  
        if(l1){
            total += l1.val
            l1 = l1.next
        }

        if(l2){
            total += l2.val
            l2 = l2.next
        }

  
        let num = total % 10
        carry = Math.floor(total/10)
        dummy.next = new ListNode(num)
        dummy = dummy.next
    }
  

    return current.next
};
```
Step by step algo:
1) Initialization: Initialize the dummy node and result pointer to the dummy node, also set total and carry variables to 0
2) Traversing lists: Traverse through both linked lists while either of them or the carry has a value
3) Calculating Sum: At each iteration, calculate the total sum of digits from l1, l2 and the carry-over
4) Extracting Digit and Carry: Extract the digit by taking the modulo 10 of the total sum and update the carry for the next iteration by dividing the total sum by 10 
5) Creating New Node: Create a new ListNode with the extracted digit and attach it to the resulting linked list
6) Return Result: Finally return the next node of the dummy node which contains the head of the resultant linked list

# Two Sum II - Input Array Is Sorted
Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

**Example 1:**

**Input:** numbers = [2,7,11,15], target = 9
**Output:** [1,2]
**Explanation:** The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].

**Example 2:**

**Input:** numbers = [2,3,4], target = 6
**Output:** [1,3]
**Explanation:** The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].

**Example 3:**

**Input:** numbers = [-1,0], target = -1
**Output:** [1,2]
**Explanation:** The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].

**Constraints:**

- `2 <= numbers.length <= 3 * 104`
- `-1000 <= numbers[i] <= 1000`
- `numbers` is sorted in **non-decreasing order**.
- `-1000 <= target <= 1000`
- The tests are generated such that there is **exactly one solution**.

My answer:
```javascript
var twoSum = function(numbers, target) {
    let l = 0, r = numbers.length-1

    while(l < r){
        let sum = numbers[l] + numbers[r]
        if(sum===target) return [l+1, r+1]
        if(sum < target){
            l++
        }else{
            r--
        }
    }
};
//two pointers, L/R. numbers = [2,7,11,15], target = 18
//2 + 15 = 17 which is less than 18
//l++
```
Two pointer algo solves this easily. 

# 3Sum
Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]
**Explanation:** 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

**Example 2:**

**Input:** nums = [0,1,1]
**Output:** []
**Explanation:** The only possible triplet does not sum up to 0.

**Example 3:**

**Input:** nums = [0,0,0]
**Output:** [[0,0,0]]
**Explanation:** The only possible triplet sums up to 0.

**Constraints:**

- `3 <= nums.length <= 3000`
- `-105 <= nums[i] <= 105`

My answer:
```javascript
threeSum(nums) {
    const result = []
    nums.sort((a,b) => a - b) // 1) Sort the array ascending

    //outerloop 
    for(let i = 0; i < nums.length; i++){
        if(nums[i] > 0) break;  // 2) If current value > 0, stop early
        // 3) Skip duplicate 'i' values
        if(i > 0 && nums[i] === nums[i-1]) continue 
        
        let l = i + 1, r = nums.length-1 // 4) two pointers on the right side
        while(l < r){
            const sum = nums[i] + nums[l] + nums[r]
            if(sum > 0){
                r--  // 5a) sum too big → move right pointer left
            } else if(sum < 0){
                l++  // 5b) sum too small → move left pointer right
            } else{
                result.push([nums[i], nums[l], nums[r]]) // 6) found a triplet
                l++
                r--  // 7) move both pointers inward
                while(l < r && nums[l] === nums[l - 1]){
                    l++ // 8) skip duplicates for left pointer
                }
            }
        }
    }

    return result
}

```