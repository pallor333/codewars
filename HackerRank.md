# Staircase (Easy)
Its base and height are both equal to

. It is drawn using `#` symbols and spaces. **The last line is not preceded by any spaces.**

Write a program that prints a staircase of size n.

**Function Description**
Complete the staircase function with the following parameter(s):
- int n: an integer

**Print**
Print a staircase as described above. No value should be returned.  
**Note**: The last line is not preceded by spaces. All lines are right-aligned.

**Input Format**
A single integer, n, denoting the size of the staircase.

**Constraints**
0 < n <= 100

**Sample Input**
6
Sample output
```
-      #
-     ##
-    ###
-   ####
-  #####
- ######
```
**Explanation**

The staircase is right-aligned, composed of `#` symbols and spaces, and has a height and width of n = 6.

My answer:
```javascript
//Outer loop prints vertically
//Inner loop prints horizontally
// 0 -> 5 spaces, 1#
// 1 -> 4 spaces, 2#
// 2 -> 3 spaces, 3#
// 3 -> 2 spaces, 4#
// 4 -> 1 space, 5#
// 5 -> 0 space, 6#

function staircase(n) {
    for(let i = 0; i < n; i++){
        let space = ' '.repeat(n - i - 1)
        let stair = '#'.repeat(i + 1)
        console.log(space + stair)
    }
}
```



# Counting Sort 1 (Easy)
**Comparison Sorting**  
Quicksort usually has a running time of , but is there an algorithm that can sort even faster? In general, this is not possible. Most sorting algorithms are _comparison sorts_, i.e. they sort a list just by comparing the elements to one another. A comparison sort algorithm cannot beat (worst-case) running time, since

represents the minimum number of comparisons needed to know where to place each element. For more details, you can see [these notes](http://www.cs.cmu.edu/~avrim/451f11/lectures/lect0913.pdf) (PDF).

**Alternative Sorting**  
Another sorting method, the _counting sort_, does not require comparison. Instead, you create an integer array whose index range covers the entire range of values in your array to sort. Each time a value occurs in the original array, you increment the counter at that index. At the end, run through your counting array, printing the value of each non-zero valued index that number of times.

**Example**  

arr = [1,1,3,2,1]
All of the values are in the range [0...3] , so create an array of zeros, result =[0,0,0,0]. The results of each iteration follow:

i	arr[i]	result
0	1	[0, 1, 0, 0]
1	1	[0, 2, 0, 0]
2	3	[0, 2, 0, 1]
3	2	[0, 2, 1, 1]
4	1	[0, 3, 1, 1]

The frequency array is [0,3,1,1]. These values can be used to create the sorted array as well: sorted = [1,1,1,2,3]

**Note**  
For this exercise, always return a frequency array with 100 elements. The example above shows only the first 4 elements, the remainder being zeros.

**Challenge**  
Given a list of integers, count and return the number of times each value appears as an array of integers.

**Function Description**

Complete the _countingSort_ function in the editor below.

countingSort has the following parameter(s):

- _arr[n]:_ an array of integers

**Returns**

- int[100]: a frequency array

**Input Format**

The first line contains an integer n, the number of items in arr.  
Each of the next n lines contains an integer arr[i] where 0 <= i < n.

**Constraints**
100 <= n <= 10^6
0 <= arr[i] < 100

  

**Sample Input**

100
63 25 73 1 98 73 56 84 86 57 16 83 8 25 81 56 9 53 98 67 99 12 83 89 80 91 39 86 76 85 74 39 25 90 59 10 94 32 44 3 89 30 27 79 46 96 27 32 18 21 92 69 81 40 40 34 68 78 24 87 42 69 23 41 78 22 6 90 99 89 50 30 20 1 43 3 70 95 33 46 44 9 69 48 33 60 65 16 82 67 61 32 21 79 75 75 13 87 70 33  

**Sample Output**

0 2 0 2 0 0 1 0 1 2 1 0 1 1 0 0 2 0 1 0 1 2 1 1 1 3 0 2 0 0 2 0 3 3 1 0 0 0 0 2 2 1 1 1 2 0 2 0 1 0 1 0 0 1 0 0 2 1 0 1 1 1 0 1 0 1 0 2 1 3 2 0 0 2 1 2 1 0 2 2 1 2 1 2 1 1 2 2 0 3 2 1 1 0 1 1 1 0 2 2 

**Explanation**

Each of the resulting values result[i] represents the number of times i appeared in arr.


# The Full Counting Sort (Medium)
Use the counting sort to order a list of strings associated with integers. If two strings are associated with the same integer, they must be printed in their original order, i.e. your sorting algorithm should be _stable_. There is one other twist: strings in the first half of the array are to be replaced with the character `-` (dash, ascii 45 decimal).

Insertion Sort and the simple version of Quicksort are stable, but the faster in-place version of Quicksort is not since it scrambles around elements while sorting.

Design your counting sort to be stable.

**Example**
```
arr = [[0, 'a], [1, 'b'], [0, 'c'], [1, 'd']]
```
The first two strings are replaced with '-'. Since the maximum associated integer is 1, set up a helper array with at least two empty arrays as elements. The following shows the insertions into an array of three empty arrays.
```
i	string	converted	list
0				[[],[],[]]
1 	a 	-		[[-],[],[]]
2	b	-		[[-],[-],[]]
3	c			[[-,c],[-],[]]
4	d			[[-,c],[-,d],[]]
```
The result is then printed: - c - d.

**Function Description**
Complete the _countSort_ function in the editor below. It should construct and print the sorted strings.

countSort has the following parameter(s):
```- string arr[n][2]: each arr[i] is comprised of two strings, x and s```

**Returns**  
- Print the finished array with each element separated by a single space.

**Note**: The first element of each arr[i].  x must be cast as an integer to perform the sort.

**Input Format**
The first line contains n, the number of integer/string pairs in the array arr.  
Each of the next n contains x[i] and s[i], the integers (as strings) with their associated strings.

**Constraints**
```
1 <= n <= 1000000
n is even
1 <= |s| <= 10
0 <= x < 100, x ar
s[i] consists of characters in the range ascii[a-z]
```

**Output Format**
Print the strings in their correct order, space-separated on one line.

**Sample Input**
```
20
0 ab
6 cd
0 ef
6 gh
4 ij
0 ab
6 cd
0 ef
6 gh
0 ij
4 that
3 be
0 to
1 be
5 question
1 or
2 not
4 is
2 to
4 the
```

**Sample Output**
```
- - - - - to be or not to be - that is the question - - - -
```

**Explanation**
The correct order is shown below. In the array at the bottom, strings from the first half of the original array were replaced with dashes.
```
0 ab
0 ef
0 ab
0 ef
0 ij
0 to
1 be
1 or
2 not
2 to
3 be
4 ij
4 that
4 is
4 the
5 question
6 cd
6 gh
6 cd
6 gh
```

```
sorted = [['-', '-', '-', '-', '-', 'to'], ['be', 'or'], ['not', 'to'], ['be'], ['-', 'that', 'is', 'the'], ['question'], ['-', '-', '-', '-'], [], [], [], []]
```

My answer:
```javascript
function countSort(arr) {
    const count = [], sorted = []
    for (let i = 0; i < arr.length; i++) {
        count.push([])
    }
  
    arr.forEach((pair,idx) => {
        const str = idx < arr.length / 2 ? "-" : pair[1]
        count[pair[0]].push(str)
    })

    count.forEach(n => {
        if(n.length!==0) {sorted.push(n.join(' '))}
    })
    
    console.log(sorted.join(' '))
}
//create array of arrays to store ordered strings plus '-'
//loop over given arr, using num in element to push to another arr
//indexes < arr.length / 2 become '-', otherwise push the str
//loop AGAIN over array of arrays, pushing to sorted arr if it's not an empty arr
//console log with a .join()
```

A better answer:
```javascript
function countSort(arr) {
  const count = Array.from({ length: arr.length }, () => [])

  arr.forEach((pair, idx) => {
    const str = idx < arr.length / 2 ? "-" : pair[1]
    count[pair[0]].push(str)
  })

  // Directly flatten and join
  console.log(count.flat().join(" "))
}
```
- `count.flat()` takes all the arrays inside `count` and smashes them into a single array (skips empties automatically).
- No need to check `if (n.length !== 0)` anymore.
- No extra `sorted` array — you build the final output in one shot.
This gets rid of the 'sorted' array with array.flat()