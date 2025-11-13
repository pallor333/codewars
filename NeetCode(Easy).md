# Contains Duplicate
Given an integer array `nums`, return `true` if any value appears **more than once** in the array, otherwise return `false`.

**Example 1:**

```java
Input: nums = [1, 2, 3, 3]

Output: true
```


**Example 2:**

```java
Input: nums = [1, 2, 3, 4]

Output: false
```
>[!Text]- Recommended Time & Space Complexity
>You should aim for a solution with `O(n)` time and `O(n)` space, where `n` is the size of the input array.

>[!Text]- Hint 1
>A brute force solution would be to check every element against every other element in the array. This would be an `O(n^2)` solution. Can you think of a better way?

>[!Text]- Hint2
>Is there a way to check if an element is a duplicate without comparing it to every other element? Maybe there's a data structure that is useful here.

>[!Text]- Hint3
>We can use a hash data structure like a hash set or hash map to store elements we've already seen. This will allow us to check if an element is a duplicate in constant time.

My answer:
```javascript
class Solution {
    /**
     * @param {number[]} nums
     * @return {boolean}
     */
    hasDuplicate(nums) {
        let setNums = new Set(nums)
        return !(setNums.size === nums.length)
    }
}
```

Slightly more efficient answer:
```javascript
class Solution {
    /**
     * @param {number[]} nums
     * @return {boolean}
     */
    hasDuplicate(nums) {
        return new Set(nums).size < nums.length;
    }
}
```

# Valid Anagram
Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: s = "racecar", t = "carrace"

Output: true
```

**Example 2:**

```java
Input: s = "jar", t = "jam"

Output: false
```

**Constraints:**

- `s` and `t` consist of lowercase English letters.

>[!Text]- Recommended Time & Space Complexity
>You should aim for a solution with `O(n + m)` time and `O(1)` space, where `n` is the length of the string `s` and `m` is the length of the string `t`.

>[!Text]- Hint 1
>A brute force solution would be to sort the given strings and check for their equality. This would be an `O(nlogn + mlogm)` solution. Though this solution is acceptable, can you think of a better way without sorting the given strings?

>[!Text]- Hint 2
>By the definition of the anagram, we can rearrange the characters. Does the order of characters matter in both the strings? Then what matters?

>[!Text]- Hint 3
>We can just consider maintaining the frequency of each character. We can do this by having two separate hash tables for the two strings. Then, we can check whether the frequency of each character in string `s` is equal to that in string `t` and vice versa.

My answer:
```javascript
class Solution {

    /**
     * @param {string} s
     * @param {string} t
     * @return {boolean}
     */

    isAnagram(s, t) {
        if(s.length != t.length) return false

        const stringHash1 = {}, stringHash2 = {}
        s.split('').forEach(ch => stringHash1[ch] = (stringHash1[ch] || 0 ) + 1)
        t.split('').forEach(ch => stringHash2[ch] = (stringHash2[ch] || 0 ) + 1)
  
        const keys1 = Object.keys(stringHash1);
        const keys2 = Object.keys(stringHash2);
        for(const key of keys1){
            if(stringHash1[key] !== stringHash2[key]){
                return false
            }
        }
        return true
    }
}
```
Time Complexity: O(n+m)
Space Complexity: O(n+m)

A more efficient answer:
```javascript
class Solution {
    /**
     * @param {string} s
     * @param {string} t
     * @return {boolean}
     */
    isAnagram(s, t) {
        if (s.length !== t.length) {
            return false;
        }

        const count = new Array(26).fill(0);
        for (let i = 0; i < s.length; i++) {
            count[s.charCodeAt(i) - 'a'.charCodeAt(0)]++;
            count[t.charCodeAt(i) - 'a'.charCodeAt(0)]--;
        }
        return count.every(val => val === 0);
    }
}
```
- Time complexity: O(n+m)O(n+m)
- Space complexity: O(1)O(1) since we have at most 26 different characters.

# Two Sum
Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that _every_ input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

**Example 1:**
```javascript
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]

```
Explanation: `nums[0] + nums[1] == 7`, so we return `[0, 1]`.

**Example 2:**
```javascript
Input: nums = [4,5,6], target = 10

Output: [0,2]
```

**Example 3:**
```javascript
Input: nums = [5,5], target = 10

Output: [0,1]
```

**Constraints:**
- `2 <= nums.length <= 1000`
- `-10,000,000 <= nums[i] <= 10,000,000`
- `-10,000,000 <= target <= 10,000,000`

>[!Text]- Recommended Time & Space Complexity
>You should aim for a solution with `O(n)` time and `O(n)` space, where n is the size of the input array.

>[!Text]- Hint1
>A brute force solution would be to check every pair of numbers in the array. This would be an `O(n^2)` solution. Can you think of a better way? Maybe in terms of mathematical equation?

>[!Text]- Hint2
>Given, We need to find indices `i` and `j` such that `i != j` and `nums[i] + nums[j] == target`. Can you rearrange the equation and try to fix any index to iterate on?

>[!Text]- Hint3
>we can iterate through nums with index `i`. Let `difference = target - nums[i]` and check if `difference` exists in the hash map as we iterate through the array, else store the current element in the hashmap with its index and continue. We use a hashmap for `O(1)` lookups.

My answer: 
```javascript
function twoSum(nums, target) {
    const hash = {};
    for (let i = 0; i < nums.length; i++) {
        const temp = target - nums[i];
        if (temp in hash) {
            return [hash[temp], i];
        }
        hash[nums[i]] = i; // Store the number and its index
    }
}
```
twoSum([1, 3, 4, 2], 6)
Create hash table to hold previous values. Loop over nums array defining the target as the target subtracted by the current element (6-1 = 5). Then check if hash[target] exists, if it does then we can return the indexes of the two nums that add up to the sum, if it doesn't then we add a new value to our array. 
In essence, we loop over our array in one direction while adding to our hash with trailing values, looking backwards in order to see if some value satisfies our target. 
Time efficiency: O(n)
Space efficiency: O(n)

# Valid Palindrome
Given a string `s`, return `true` if it is a **palindrome**, otherwise return `false`.

A **palindrome** is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

**Note:** Alphanumeric characters consist of letters `(A-Z, a-z)` and numbers `(0-9)`.

**Example 1:**

```java
Input: s = "Was it a car or a cat I saw?"

Output: true
```

Explanation: After considering only alphanumerical characters we have "wasitacaroracatisaw", which is a palindrome.

**Example 2:**

```java
Input: s = "tab a cat"

Output: false
```

Explanation: "tabacat" is not a palindrome.

**Constraints:**

- `1 <= s.length <= 1000`
- `s` is made up of only printable ASCII characters.

  
  
>[!Text]- Recommended Time & Space Complexity
>You should aim for a solution with `O(n)` time and `O(n)` space, where n is the size of the input array.
  
>[!Text]- Hint 1
>A brute force solution would be to create a copy of the string, reverse it, and then check for equality. This would be an `O(n)` solution with extra space. Can you think of a way to do this without `O(n)` space?
  
>[!Text]- Hint 2
>Can you find the logic by observing the definition of pallindrome or from the brute force solution?
  
>[!Text]- Hint 3
>A palindrome string is a string that is read the same from the start as well as from the end. This means the character at the start should match the character at the end at the same index. We can use the two pointer algorithm to do this efficiently.

My answer:
```javascript
class Solution {
    /**
     * @param {string} s
     * @return {boolean}
     */
    isAlphanumeric(c){
        return (
            c >= 'a' && c <= 'z' ||
            c >= 'A' && c <= 'Z' ||
            c >= '0' && c <= '9'
        )
    }

    isLetter(c){
        return (
            c >= 'a' && c <= 'z' ||
            c >= 'A' && c <= 'Z'
        )
    }
    //Loop over s with two pointers: starting at 0 and length-1
    //if(!isAlphanumeric(c)) l++ or r--
    isPalindrome(s) {
        let l = 0, r = s.length-1
        while(l < r){
            while(l < r && !this.isAlphanumeric(s[l])){ l++ }
            while(l < r && !this.isAlphanumeric(s[r])){ r-- }
  
            let forward = s[l], backward = s[r]
            if(this.isLetter(forward)) { forward = forward.toLowerCase() }
            if(this.isLetter(backward)) { backward = backward.toLowerCase() }
            if(forward !== backward) return false
            l++
            r--
        }
        return true
    }

}
```
# Best Time to Buy and Sell Stock
You are given an integer array `prices` where `prices[i]` is the price of NeetCoin on the `ith` day.

You may choose a **single day** to buy one NeetCoin and choose a **different day in the future** to sell it.

Return the maximum profit you can achieve. You may choose to **not make any transactions**, in which case the profit would be `0`.

**Example 1:**

```java
Input: prices = [10,1,5,6,7,1]

Output: 6
```

Explanation: Buy `prices[1]` and sell `prices[4]`, `profit = 7 - 1 = 6`.

**Example 2:**

```java
Input: prices = [10,8,7,5,2]

Output: 0
```

Explanation: No profitable transactions can be made, thus the max profit is 0.

**Constraints:**

- `1 <= prices.length <= 100`

My answer:
```javascript
class Solution {
    /**
     * @param {number[]} prices
     * @return {number}
     */

    maxProfit(prices) {
        let min = prices[0], maxProfit = 0
        for(let price of prices){
            min = Math.min(min, price)
            maxProfit = Math.max(maxProfit, price - min)
        }

        return maxProfit
    }
}

//input: array of numbers, output: one number of max profit
//loop over arr
//keep track of min
//keep track of current - min => max
//return max or 0
```
# Linked List Cycle Detection
Given the beginning of a linked list `head`, return `true` if there is a cycle in the linked list. Otherwise, return `false`.

There is a cycle in a linked list if at least one node in the list can be visited again by following the `next` pointer.

Internally, `index` determines the index of the beginning of the cycle, if it exists. The tail node of the list will set it's `next` pointer to the `index-th` node. If `index = -1`, then the tail node points to `null` and no cycle exists.

**Note:** `index` is **not** given to you as a parameter.

**Example 1:**
```javascript
Input: head = [1,2,3,4], index = 1
Output: true
```
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

**Example 2:**
```javascript
Input: head = [1,2], index = -1
Output: false
```

**Constraints:**
- `1 <= Length of the list <= 1000`.
- `-1000 <= Node.val <= 1000`
- `index` is `-1` or a valid index in the linked list.

My answer:
```javascript
class Solution {
    /**
     * @param {ListNode} head
     * @return {boolean}
     */
    hasCycle(head) {
        if(!head) return false
        let slow = head, fast = head
        while(fast && fast.next){
            slow = slow.next
            fast = fast.next.next
            if(slow === fast) return true
        }
        return false
    }
}
//input: head, output: true/false
//two pointers at head, slow and fast
//while(fast != null), set slow to next and fast to next+next
//if slow is ever === fast, return false
//outside of while loop return true
```