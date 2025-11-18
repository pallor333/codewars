# Group Anagrams
Given an array of strings `strs`, group all _anagrams_ together into sublists. You may return the output in **any order**.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

**Example 2:**

```java
Input: strs = ["x"]

Output: [["x"]]
```

**Example 3:**

```java
Input: strs = [""]

Output: [[""]]
```

**Constraints:**

- `1 <= strs.length <= 1000`.
- `0 <= strs[i].length <= 100`
- `strs[i]` is made up of lowercase English letters.

My answer:
```javascript
class Solution {
    /**
     * @param {string[]} strs
     * @return {string[][]}
     */
    groupAnagrams(strs){
        let result = []
        while(strs.length > 0){
            const word = strs[0]
            const sublist = [word], anagramIdx = [0]

            //check for anagram
            for(let i = 1; i < strs.length; i++){
                if(this.checkAnagram(word, strs[i])) {
                    sublist.push(strs[i])
                    anagramIdx.push(i)
                }
            }

            //push temp arr to result arr
            if(sublist.length > 0) { result.push(sublist) }

            //remove matching anagram from strs by idx
            for(let i = anagramIdx.length -1 ; i >= 0; i--){
                strs.splice(anagramIdx[i], 1)
            }
        }

        return result
    }

    checkAnagram(s, t){
        if(s.length !== t.length) return false
        let letterCount = {}
  
        for(let char of s){
            letterCount[char] = (letterCount[char] || 0) + 1
        }
  

        for(let char of t){
            if(!letterCount[char]) return false
            letterCount[char]--
        }

        return true
    }
}
```
Time complexity: O(n^2  ** k). Loop over every string (iterate n times) and compare to to every other string (iterate n times). Check anagram compares the characters in each string (iterate k times). Potential O(n) from .splice()
Space complexity: O(n + k) => O(k). LetterCount = O(k), sublist = O(n), result = O(n)

Better answer:
```javascript
class Solution {
  /**
   * @param {string[]} strs
   * @return {string[][]}
   */
  groupAnagrams(strs) {
    const map = new Map();

    for (const word of strs) {
      // Build frequency count for 26 lowercase letters
      const freq = new Array(26).fill(0);
      for (const char of word) {
        freq[char.charCodeAt(0) - 97]++;
      }

      // Use frequency array as a unique signature key
      const key = freq.join('#');
	  
	  // Add to map and push
      if (!map.has(key)) map.set(key, []);
      map.get(key).push(word);
    }

    return [...(map.values()];
  }
}
```
Pseudocode: 
Create an array of 26 buckets corresponding to each letter of the alphabet, 'freq'
1) Loop over each word in the array.
2) Loop over each character in the word, incrementing the corresponding bucket in 'freq'
3) Create 'key' by joining 'freq' with a signature key ('#') for uniqueness 
4) Add the 'key' to map if it doesn't exist and then push the word to the key as a value.
5) Once the loop over each word in array is done, return the map.values() in array format

**Time Complexity:** O(n * k): Outer loop once per string = O(n). Inner loop once per char = O(k). Key construction walks over 26 elements = O(26) = O(1) => n ** (k + 1) = O(n * k)
**Space Complexity**: O(n * k): array = O(1), map storage is every char of every string stored once = O(n * k). 

# 
