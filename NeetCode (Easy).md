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