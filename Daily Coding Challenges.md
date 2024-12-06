# The museum of incredibly dull things

The museum of incredibly dull things wants to get rid of some exhibits. Miriam, the interior architect, comes up with a plan to remove the most boring exhibits. She gives them a rating, and then removes the one with the lowest rating.

However, just as she finished rating all exhibits, she's off to an important fair, so she asks you to write a program that tells her the ratings of the exhibits after removing the lowest one. Fair enough.

Given an array of integers, remove the smallest value. **Do not mutate the original array/list.** If there are multiple elements with the same value, remove the one with the lowest index. If you get an empty array/list, return an empty array/list.

Don't change the order of the elements that are left.

### Examples

```
* Input: [1,2,3,4,5], output = [2,3,4,5]
* Input: [5,3,2,1,4], output = [5,3,2,4]
* Input: [2,2,1,2,1], output = [2,2,2,1]
```

Answer:
```
function removeSmallest(numbers) {
  //Empty array end immediately 
  if(numbers.length===0){
    return numbers;
  }
  
  let excitingArr = [];
  let least = numbers[0], idx = 0;
  
  numbers.forEach((num, index) => {
    //Cloning num array
    excitingArr.push(num);
    //Checking for first instance of smallest value
    if(num < least){
      least = num;
      idx = index;
      }
  });
  //Remove smallest value in O(1) time
  excitingArr.splice(idx, 1)
  return excitingArr;
}
```
///////////


# Given a string, you have to return a string in which each character (case-sensitive) is repeated once.

### Examples (Input -> Output):

```
* "String"      -> "SSttrriinngg"
* "Hello World" -> "HHeelllloo  WWoorrlldd"
* "1234!_ "     -> "11223344!!__  "
```

My Answer:
```
function doubleChar(str) {
  let dblStr = "";
  for(let i = 0; i<str.length;i++){
    dblStr+=str[i]+str[i];
  }
  return dblStr;
}
```

Answer:
```
const doubleChar = (str) => str.split("").map(c => c + c).join("");
```

# Remove exclamation marks
Write function RemoveExclamationMarks which removes all exclamation marks from a given string.

Answer:
```
function removeExclamationMarks(s) {
  return s.split('!').join('');
}
```
Another solution:
```
function removeExclamationMarks(s) {
  return s.replace(/!/g, '');
}
```

# Reverse String
Complete the function that accepts a string parameter, and reverses each word in the string. All spaces in the string should be retained.

Examples:
"This is an example!" ==> "sihT si na !elpmaxe"
"double spaces" ==> "elbuod secaps"

Answer:

```
function reverseWords(str) {
	return str.split('').map(word) => {
		return word.split('').reverse().join('');
	}.join('')
```
- str.split(' ') creates an array based on splitting based on each space. "The quick brown fox jumped over the moon." turns into ["The", "quick", "brown", "fox", "jumped", "over", "the", "moon."]

- Map allows us to call a function on each element of the newly formed array. Then on each word in the array, we split by letter, with split(''), reverse the order in the arrays with reverse() and then join the letters back into words with join(''). Finally we add a .join(' ') method after the map() to combine every word in the array into a string, adding a space after each word.

# Convert String to Array
Write a function to split a string and convert it into an array of words.
### Examples (Input ==> Output):

```
"Robin Singh" ==> ["Robin", "Singh"]

"I love arrays they are my favorite" ==> ["I", "love", "arrays", "they", "are", "my", "favorite"]
```
Answer:
```
const stringToArray = string => string.split(" ");
```
# Find the next integral perfect square
You might know some pretty large perfect squares. But what about the NEXT one?

Complete the findNextSquare method that finds the next integral perfect square after the one passed as a parameter. Recall that an integral perfect square is an integer n such that sqrt(n) is also an integer.

If the argument is itself not a perfect square then return either -1 or an empty value like None or null, depending on your language. You may assume the argument is non-negative.

Examples ( Input --> Output )
121 --> 144
625 --> 676
114 --> -1 # because 114 is not a perfect square

Answer:
```
function findNextSquare(sq){
	return math.sqrt(sq)%1 -1 : Math.pow(Math.sqrt(sq)+1, 2);
}
```
Math(sq)%1 is truthy/falsy. When it's not an integer it equals some number (e.g. 32.4893), which is truthy. When it is an integer the remainder is 0 which is falsy. Overall an elegant way to solve this problem. The only issue is that we're calling math.sqrt() twice. Is it more efficient to declare a variable to use?
# Count the smiley faces!
Given an array (arr) as an argument complete the function countSmileys that should return the total number of smiling faces.

Rules for a smiling face:
- Each smiley face must contain a valid pair of eyes. Eyes can be marked as : or ;
- A smiley face can have a nose but it does not have to. Valid characters for a nose are - or ~
- Every smiling face must have a smiling mouth that should be marked with either ) or D
No additional characters are allowed except for those mentioned.

Valid smiley face examples: :) :D ;-D :~)
Invalid smiley faces: ;( :> :} :]

Example:
countSmileys([':)', ';(', ';}', ':-D']);       // should return 2;
countSmileys([';D', ':-(', ':-)', ';~)']);     // should return 3;
countSmileys([';]', ':[', ';*', ':$', ';-D']); // should return 1;

Note:
In case of an empty array return 0. You will not be tested with invalid input (input will always be an array). Order of the face (eyes, nose, mouth) elements will always be the same.

Answer:
```
function countSmileys(arr) { 
  let countSmiles = 0;
  
  arr.forEach(smile =>{
    if(smile[0]  === ':' || smile[0]  === ';'){ //check eyes
      if(smile.length === 2){ //No nose, check mouth only
        smile[1] === ')' || smile[1] === 'D' ? countSmiles++ : null;
       }else{ //Check nose and mouth
          smile[1] === '-' || smile[1] === '~' ? 
          smile[2] === ')' || smile[2] === 'D' ? countSmiles++ : null : null;
       }
    }      
  })
  return countSmiles;
}
```
Program logic: Define counter to return later. Iterate over array looking at valid eyes. If valid eyes found, then check for length to determine if there is a nose. If no nose, check for mouth and if there is a mouth then increment the counter. Else statement is reached when there is a nose. Check for valid nose AND mouth and if this is true then increment counter. 
Ternary conditional operator can be chained to nest if statements to ensure readability and write more concise code. 

Another Answer:
```

const smileyIsValid = smiley => 
  smiley.length === 3 || smiley.length === 2

const smileyHasValidEye = smiley => {
  const maybeEye = smiley.charAt(0)
  return maybeEye === ':' || maybeEye === ';'
}

const smileyHasNose = smiley =>
  smiley.length === 3

const smileyHasValidNose = smiley => {
  const maybeNose = smiley.charAt(1)
  return smileyHasNose(smiley) ? maybeNose === '-' || maybeNose === '~' : true
}

const smileyHasValidMouth = smiley => {
  const maybeMouth = smileyHasNose(smiley) ? smiley.charAt(2) : smiley.charAt(1)
  return maybeMouth === ')' || maybeMouth === 'D'
}

//return the total number of smiling faces in the array
const countSmileys = smileys => 
  smileys.filter(smiley => 
    smileyIsValid(smiley) &&
    smileyHasValidEye(smiley) &&
    smileyHasValidNose(smiley) &&
    smileyHasValidMouth(smiley)
  ).length
```

# Detect Pangram
A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence "The quick brown fox jumps over the lazy dog" is a pangram, because it uses the letters A-Z at least once (case is irrelevant).

Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

Answer:
```
function isPangram(string){
  return new Set(string.toLowerCase().match(/[a-z]/g)).size === 26;
}
```
A set data structure is created. A set can only have one of each character in it at a time. First the string is set to lower case and then it is filtered with regex - /[a-z]/ specifies only lowercase a to z while the 'g' after ensures the string is checked globally. Once all the alphabetical chars are added, the size of the set is compared to 26. If it's 26 then every letter of the alphabet is used and it is a Pangram and will return true.
# Convert num to string
We need a function that can transform a number (integer) into a string.

What ways of achieving this do you know?

#### Examples (input --> output):

```
123  --> "123"
999  --> "999"
-100 --> "-100"
```
Answer:
```
function numberToString(num) {
  return num.toString();
}
```
# Beginner Series #3 Sum of Numbers
Given two integers `a` and `b`, which can be positive or negative, find the sum of all the integers between and including them and return it. If the two numbers are equal return `a` or `b`.
**Note:** `a` and `b` are not ordered!
## Examples (a, b) --> output (explanation)

```
(1, 0) --> 1 (1 + 0 = 1)
(1, 2) --> 3 (1 + 2 = 3)
(0, 1) --> 1 (0 + 1 = 1)
(1, 1) --> 1 (1 since both are same)
(-1, 0) --> -1 (-1 + 0 = -1)
(-1, 2) --> 2 (-1 + 0 + 1 + 2 = 2)
```
Your function should only return a number, not the explanation about how you get that number.

My answer:
```
function getSum(a, b){
  if(a===b){
    return a;
  }
  //Sort a,b and place into new array
  let arr = [a, b].sort((a, b) => a - b);
  //Using array, run a for loop to add all numbers between a,b
  for(let i = arr[0]+1; i < arr[1]; i++){
     arr.push(i);
   }
  //Return the sum of all values
  return arr.reduce((accumulator, item) => accumulator + item, 0);
}
```

Better answer:
```
const GetSum = (a, b) => {
  let min = Math.min(a, b),
      max = Math.max(a, b);
  return (max - min + 1) * (min + max) / 2;
}
```
Uses Gauss Summation: n(n+1)/2 where n is the largest number of the values you want to sum. 

Even better answer:
```
function GetSum(a,b)
{
  return (Math.abs(a - b) + 1) * (a+b) / 2;
}
```
This gets around having to figure out the min/max by using Math.abs(). 
# Beginner Series #4 Cockroach
The cockroach is one of the fastest insects. Write a function which takes its speed in km per hour and returns it in cm per second, rounded down to the integer (= floored).

For example:

```
1.08 --> 30
```

Note! The input is a Real number (actual type is language dependent) and is >= 0. The result should be an Integer.

Answer: 
```
function cockroachSpeed(s) {
  const secsInHour = 3600;
  const centimetersInKilometers = 100000;
  
  return Math.floor((s*centimetersInKilometers)/secsInHour);
}
```
# Transportation on vacation
After a hard quarter in the office you decide to get some rest on a vacation. So you will book a flight for you and your girlfriend and try to leave all the mess behind you.

You will need a rental car in order for you to get around in your vacation. The manager of the car rental makes you some good offers.

Every day you rent the car costs $40. If you rent the car for 7 or more days, you get $50 off your total. Alternatively, if you rent the car for 3 or more days, you get $20 off your total.

Write a code that gives out the total amount for different days(d).

Answer:
```
function rentalCarCost(d) {
  const dailyFee = 40;
  const threeOrMoreDiscount = 20;
  const sevenOrMoreDiscount = 50;
  return d < 7 && d >= 3 ? d*dailyFee - threeOrMoreDiscount : 
  d >= 7 ? d*dailyFee - sevenOrMoreDiscount : d*dailyFee
}
```
# Removing Elements
Take an array and remove every second element from the array. Always keep the first element and start removing with the next element.
### Example:

`["Keep", "Remove", "Keep", "Remove", "Keep", ...]` --> `["Keep", "Keep", "Keep", ...]`

None of the arrays will be empty, so you don't have to worry about that!

Answer:
```
function removeEveryOther(arr){
  return arr.filter(function(elem, index) {
    return index % 2 === 0;
  });
}
```

Filter will iterate over the array and return values that make it true. We include the index as a way to check for every other element to return.

Refactored answer:
```
function removeEveryOther(arr){
  return arr.filter((element, index) => index % 2 === 0);
}
```
# Counting Duplicates
### Count the number of Duplicates

Write a function that will return the count of **distinct case-insensitive** alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

### Example

"abcde" -> 0 `# no characters repeats more than once`  
"aabbcde" -> 2 `# 'a' and 'b'`  
"aabBcde" -> 2 ``# 'a' occurs twice and 'b' twice (`b` and `B`)``  
"indivisibility" -> 1 `# 'i' occurs six times`  
"Indivisibilities" -> 2 `# 'i' occurs seven times and 's' occurs twice`  
"aA11" -> 2 `# 'a' and '1'`  
"ABBA" -> 2 `# 'A' and 'B' each occur twice`

My Answer:
```
function duplicateCount(text){
  //Put all lowercase into array and then sort 
  let textArr = text.toLowerCase().split("").sort();
  //Variable to hold previous element during looping
  let prev = null;
  //Array to hold all duplicate values
  let dupesArr = []
  //Filter over characters, add if previous value same AND it is not already in dupe array
  textArr.filter(element => {
    element === prev && !dupesArr.includes(element) ? dupesArr.push(element): null;
    prev = element;
    });
  
  return dupesArr.length;
}
```

# Two Sum
Write a function that takes an array of numbers (integers for the tests) and a target number. It should find two different items in the array that, when added together, give the target value. The indices of these items should then be returned in a tuple / list (depending on your language) like so: `(index1, index2)`.

For the purposes of this kata, some tests may have multiple answers; any valid solutions will be accepted.

The input will always be valid (numbers will be an array of length 2 or greater, and all of the items will be numbers; target will always be the sum of two different items from that array).

Based on: [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

```javascript
twoSum([1, 2, 3], 4) // returns [0, 2] or [2, 0]
twoSum([3, 2, 4], 6) // returns [1, 2] or [2, 1]
```

My Answer:
```
function twoSum(numbers, target) {
    for(let i = 0; i < numbers.length-1; i++){
      for(let j = i+1; j < numbers.length; j++){
        if(numbers[i] + numbers[j] === target){
          return [i, j];
        }
      }
    }
}
```
Not very efficient. O(n^2) run time.

**A better answer using Map():**
```
function twoSum(numbers, target) {
  let seen = new Map();
  for (let i = 0; i < numbers.length; i++) {
    let x = numbers[i], y = target - x;
    if (seen.has(y))
      return [seen.get(y), i];
    seen.set(x, i);
  }
}
```
A Map allows for faster lookups and insertions. We can check if a number has been seen before in constant time, O(1). We loop over the number array, defining the current element as x and the target - current element as y. That complement, y, is checked for in the Map() data structure. If it's not found then we add the current element, along with it's index into the Map(). If it's found, then we return current index along with the stored index in the Map().

The genius lies in the searching for a complement. For example, given [3, 2, 4] with 6 being the target. The first element 3 is added to the map. Then we move onto 2. Quick maffs: 6 - 2 = 4, which is not found in the map. Then we move onto 4. Subtracting 4 from 6 yields two, which we look for in the map. It's there, along with the correct index which is promptly returned with the current index: [2, 1]. This solution is O(n) runtime, a much more efficient solution than my double loop O(n^2 solution.)

A better answer using Hashing:
```
function twoSum(numbers, target) {
  var tmp, hash = {};
  numbers.forEach(function(a, i){ hash[a] = i; })
  
  for (var i = 0; i < numbers.length; i++){
    tmp = target - numbers[i];
    if (typeof hash[tmp] !== 'undefined') return [i, hash[tmp]]
  }
}
```
A hashtable object is created to hold key-pair values of 'element: index'. This looks something like:  
```
{ 2: 0, // index 0, value 2 
7: 1, // index 1, value 7 
11: 2, // index 2, value 11 
15: 3 // index 3, value 15 }
```
Once that's out of the way, we loop over the number array, defining the complement - the total sum minus the current element - as 'tmp'. We look for tmp in the hashtable, returning the index of the current element and the index in the hashtable if a match is found. 

# Jade Casing Strings
Jaden Smith, the son of Will Smith, is the star of films such as The Karate Kid (2010) and After Earth (2013). Jaden is also known for [some of his philosophy that he delivers via Twitter](https://twitter.com/jaden). When writing on Twitter, he is known for almost always capitalizing every word. For simplicity, you'll have to capitalize each word, check out how contractions are expected to be in the example below.

Your task is to convert strings to how they would be written by Jaden Smith. The strings are actual quotes from Jaden Smith, but they are not capitalized in the same way he originally typed them.

Example:

```
Not Jaden-Cased: "How can mirrors be real if our eyes aren't real"
Jaden-Cased:     "How Can Mirrors Be Real If Our Eyes Aren't Real"
```

[Link to Jaden's former Twitter account @officialjaden via archive.org](https://web.archive.org/web/20190624190255/https://twitter.com/officialjaden)

My Answer:
```
String.prototype.toJadenCase = function () {
  return this.split(" ").map(str => str.charAt(0).toUpperCase() + str.slice(1)).join(" ")
};
```
The keyword 'this' is required to call the string. It is first split by space, each word being an element in an array. Then the map method is called to create a new array populated with the capitalized first letter as well as the rest of the string. str.charAt(0) is not completely necessary as strings are indexed and str[0] would suffice. We must use str.slice(1) - slice is inclusive at the start but exclusive at the end - to append the rest of the string into each element of our new array. Then the array elements are joined together in a single string which is returned back.

# Exes and Ohs
Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

Examples input/output:

```
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```

My answer:
```
function XO(str) {
  let xoCounter = 0;
  let str = str.toLowerCase();
  for(let i = 0; i < str.length; i++){
    str[i] === 'x' ? xoCounter++ : 
    str[i] === 'o' ? xoCounter-- : xoCounter + 0;
  }
  return xoCounter === 0;
}
```
Time complexity is O(n), space complexity is O(n) + 2. 

Another answer:
```
const XO = str => {
  str = str.toLowerCase().split('');
  //DRY
  const filter_len = (ch) => str.filter(x => x === ch).length
  return filter_len('x') ===  filter_len('o');
} 
```
This one is less efficient in terms of memory (creating a new array) as well as iterating over the array twice. 
This solution converts everything to lowercase and then puts it all into an array. A function is defined based on the parameter 'ch' and using the filter() array method to return the length of the array found via filter(). Finally we call the filter_len function to compare the 'x' and 'o'. 
It's a solution worth keeping in mind, even if it's not best practice.
# Square(n) Sum
Complete the square sum function so that it squares each number passed into it and then sums the results together.

For example, for `[1, 2, 2]` it should return `9` because 12+22+22=91^2 + 2^2 + 2^2 = 912+22+22=9.

Arrays

Lists

Fundamentals

Answer: 
```
function squareSum(numbers){
  return numbers.reduce((sum, n) => sum + n*n, 0);
}
```
# Sum of the first nth term of Series
## Task

Your task is to write a function which returns the `n`-th term of the following series, which is the sum of the first `n` terms of the sequence (`n` is the input parameter).

Series:1+14+17+110+113+116+…\mathrm{Series:}\quad 1 + \frac14 + \frac17 + \frac1{10} + \frac1{13} + \frac1{16} + \dotsSeries:1+41​+71​+101​+131​+161​+…

You will need to figure out the rule of the series to complete this.

## Rules

- You need to round the answer to 2 decimal places and return it as String.
    
- If the given value is `0` then it should return `"0.00"`.
    
- You will only be given Natural Numbers as arguments.
    

## Examples (Input --> Output)

```
n
1 --> 1 --> "1.00"
2 --> 1 + 1/4 --> "1.25"
5 --> 1 + 1/4 + 1/7 + 1/10 + 1/13 --> "1.57"
```

Answer:
```
function SeriesSum(n) {
  let sum = 0;
  for(let i = 0; i < n; i++) {
    sum += 1 / (3 * i + 1);
  }
  return sum.toFixed(2);
}
```
# The Supermarket Queue (6kyu)
There is a queue for the self-checkout tills at the supermarket. Your task is write a function to calculate the total time required for all the customers to check out!
### input

- customers: an array of positive integers representing the queue. Each integer represents a customer, and its value is the amount of time they require to check out.
- n: a positive integer, the number of checkout tills.

### output

The function should return an integer, the total time required.

---
## Important

**Please look at the examples and clarifications below, to ensure you understand the task correctly :)**

---
### Examples

```javascript
queueTime([5,3,4], 1)
// should return 12
// because when there is 1 till, the total time is just the sum of the times

queueTime([10,2,3,3], 2)
// should return 10
// because here n=2 and the 2nd, 3rd, and 4th people in the 
// queue finish before the 1st person has finished.

queueTime([2,3,10], 2)
// should return 12
```
### Clarifications

- There is only ONE queue serving many tills, and
- The order of the queue NEVER changes, and
- The front person in the queue (i.e. the first element in the array/list) proceeds to a till as soon as it becomes free.
- You should assume that all the test input will be valid, as specified above.
- The situation in this kata can be likened to the more-computer-science-related idea of a thread pool, with relation to running multiple processes at the same time: [https://en.wikipedia.org/wiki/Thread_pool](https://en.wikipedia.org/wiki/Thread_pool)

Answer:
```
function queueTime(customers, n) {
  let tills = new Array(n).fill(0);
  for (let time of customers) {
    let idx = tills.indexOf(Math.min(...tills)); 
    tills[idx] += time;
  }
  
  return Math.max(...tills);
}
```
Create an array of length n (number of tills), fill with zeroes. Loop through each customer and find the till with the shortest wait time. At first each till will have zero wait time so the customer goes to the empty till. Once all lanes are filled, customers go to the till with the minimum time.  Increment till element for the time it takes for checkout. Return the largest cumulative till time to get the answer. 

Time Complexity: The Math.min(...w) and indexOf() operations both involve scanning the entire w array, making each customer addition take O(n) time.
Therefore, the time complexity of this solution is O(m * n), where m is the number of customers and n is the number of tills. For smaller numbers of tills and customers, this approach works fine, but for larger values, optimizations like using a priority queue or min-heap could improve the performance.

Overall this solution uses an array of tills to hold values, not bothering to subtract but to add.

# Switch It Up (8kyu)
When provided with a number between `0-9`, return it in words. Note that the input is guaranteed to be within the range of `0-9`.

Input: `1`

Output: `"One"`.

If your language supports it, try using a [switch statement](https://en.wikipedia.org/wiki/Switch_statement).

Answer:
```
switchItUp=n=>["Zero","One","Two","Three","Four","Five","Six","Seven","Eight","Nine"][n]
```
A more readable version:
```
function switchItUp (n) {
	const numbersAsWords = ['Zero', 'One', 'Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten'];
	return numbersAsWords[n];
```
Uses the indexing of an array to call the corresponding number in the array. "If I were going to bring something like this into everyday use, I’d add a `Number.isInteger(n)` check and I’d probably make sure the array contains the index being passed so there’s no question that we’ll get the number we want."
# All Star Coding Challenge #18 (8kyu)
Create a function that accepts a string and a single character, and returns an integer of the count of occurrences the 2nd argument is found in the first one.

If no occurrences can be found, a count of `0` should be returned.

```js
("Hello", 'o')  =>  1
("Hello", 'l')  =>  2
("", 'z')       =>  0
```

### Notes

- The first argument can be an empty string
- In languages with no distinct character data type, the second argument will be a string of length `1`

Answer:
```
function strCount(str, letter){  
  return str.split(letter).length-1
}
```
We split the string based on the letter into separate elements in an array.  
("Hello", 'o')  =>  ['Hell' , ''] = 2 -1 => 1
("Hello", 'l')  =>  ['He', '', 'o] = 3 - 1 => 2
("", 'z')       =>  [''] =1 -1 => 0 
# Minimize Sum Of Array (Array Series #1) (7kyu)

Task:
**_Given_** an **_array of integers_** , **_Find the minimum sum_** which is obtained _from summing each Two integers product_ .

 Notes:

- **_Array/list_** _will contain_ **_positives only_** .
- **_Array/list_** _will always have_ **_even size_**
- ---
 Input >> Output Examples

```
minSum({5,4,2,3}) ==> return (22) 
```

**_Explanation_**:

- **_The minimum sum_** _obtained from summing each two integers product_ , `5*2 + 3*4 = 22`

```
minSum({12,6,10,26,3,24}) ==> return (342)
```

**_Explanation_**:

- **_The minimum sum_** _obtained from summing each two integers product_ , `26*3 + 24*6 + 12*10 = 342`

```
minSum({9,2,8,7,5,4,0,6}) ==> return (74)
```

**_Explanation_**:

- **_The minimum sum_** _obtained from summing each two integers product_ , `9*0 + 8*2 +7*4 +6*5 = 74`

---
My answer:
```
function minSum(arr) {
  arr = arr.sort((a, b) => a - b);
  let value = 0;
  while(arr.length !== 0){
  	value += ( arr.pop() * arr.shift() );
  }
  return value;
}
```

Another answer:
```
const minSum = arr =>
  arr.sort((a, b) => a - b).reduce((pre, val) => pre + val * arr.pop(), 0);
```
This is what I initially conceived of but inclusion of shift() rendered the reduce() function worthless as it would skip elements. This is a good execution of it. 

# Product of Maximums Of Array (Array Series #2) (7kyu)
## Task

**_Given_** an _array/list [] of integers_ , **_Find the product of the k maximal_** numbers.

---
### Notes

- **_Array/list_** size is _at least 3_ .
    
- **_Array/list's numbers_** _Will be_ **_mixture of positives , negatives and zeros_**
    
- **_Repetition_** of numbers in _the array/list could occur_.

### Input >> Output Examples

```
maxProduct ({4, 3, 5}, 2) ==>  return (20)
```

#### _Explanation_:

- **_Since_** _the size (k) equal 2_ , then **_the subsequence of size 2_** _whose gives_ **_product of maxima_** is `5 * 4 = 20` .
```
maxProduct ({8, 10 , 9, 7}, 3) ==>  return (720)
```

#### _Explanation_:

- **_Since_** _the size (k) equal 3_ , then **_the subsequence of size 3_** _whose gives_ **_product of maxima_** is `8 * 9 * 10 = 720` .
```
maxProduct ({10, 8, 3, 2, 1, 4, 10}, 5) ==> return (9600)
```

#### _Explanation_:

- **_Since_** _the size (k) equal 5_ , then **_the subsequence of size 5_** _whose gives_ **_product of maxima_** is `10 * 10 * 8 * 4 * 3 = 9600` .
```
maxProduct ({-4, -27, -15, -6, -1}, 2) ==> return (4)
```

#### _Explanation_:

- **_Since_** _the size (k) equal 2_ , then **_the subsequence of size 2_** _whose gives_ **_product of maxima_** is `-4 * -1 = 4` .

```
maxProduct ({10, 3, -1, -27} , 3)  return (-30)
```

#### _Explanation_:

- **_Since_** _the size (k) equal 3_ , then **_the subsequence of size 3_** _whose gives_ **_product of maxima_** is `10 * 3 * -1 = -30` .
Answer:
```
function maxProduct(numbers, size){
  return numbers
  .sort((a, b) => b - a)
  .slice(0, size)
  .reduce((product, x) => product * x, 1);
}
```
Sort from greatest to least. Slice into the array size elements where size is the number of maximal numbers wanted. Call reduce to multiply all the numbers and return a produt.
# Array Leaders (Array Series #3) (7kyu)
 Definition/Task:

An **_element is leader_** _if it is greater than The Sum all the elements to its right side_.
**_Given_** an _array/list [] of integers_ , **_Find_** _all the **_LEADERS_** in the array_.

---
Notes

- **_Array/list_** size is _at least 3_ .
- **_Array/list's numbers_** Will be **_mixture of positives , negatives and zeros_**
- **_Repetition_** of numbers in _the array/list could occur_.
- **_Returned Array/list_** _should store the leading numbers **_in the same order_** in the original array/list

 Input >> Output Examples
```
arrayLeaders ({1, 2, 3, 4, 0}) ==> return {4}
```

 **_Explanation_**:
- `4` _is greater than the sum all the elements to its right side_
- **_Note_** : **_The last element_** `0` _is equal to right sum of its elements (abstract zero)_.
```
arrayLeaders ({16, 17, 4, 3, 5, 2}) ==> return {17, 5, 2}
```

**_Explanation_**:
- `17` _is greater than the sum all the elements to its right side_
- `5` _is greater than the sum all the elements to its right side_
- **_Note_** : **_The last element_** `2` _is greater than the sum of its right elements (abstract zero)_.
```
arrayLeaders ({5, 2, -1}) ==> return {5, 2}
```

 **_Explanation_**:
- `5` _is greater than the sum all the elements to its right side_
- `2` _is greater than the sum all the elements to its right side
- **_Note_** : **_The last element_** `-1` _is less than the sum of its right elements (abstract zero)_.
```
arrayLeaders ({0, -1, -29, 3, 2}) ==> return {0, -1, 3, 2}
```

**_Explanation_**:
- `0` _is greater than the sum all the elements to its right side_
- `-1` _is greater than the sum all the elements to its right side
- `3` _is greater than the sum all the elements to its right side_
- **_Note_** : **_The last element_** `2` _is greater than the sum of its right elements (abstract zero)_.

My Answer:
```
function arrayLeaders(numbers){
  let total = numbers.reduce((sum, n) => sum + n, 0);
  return numbers.filter(num =>{
    total -= num;
    return num > total
  });
}
```
Sum up the entire array and then go from left to right, subtracting current element from the total and then checking if the current value is greater than the sum. O(n^2) run time.

Better answer:
```
var arrayLeaders = numbers => {

  let total = 0, res = []
  for (let i = numbers.length - 1; i >= 0; i--) {
    if (numbers[i] > total) res.unshift(numbers[i]);
    total += numbers[i];
  }

  return res;
}
```
This solution goes from right to left, decrementing in index. This approach is a bit more intuitive, checking if the current element is greater than the total and adding to the front of the new array if so. After it then adds the current element to the new total. O(n) run time.

# Maximum Gap (Array Series #4) (7kyu)
## Task

**_Given_** an _array/list [] of integers_ , **_Find_** **_The maximum difference_** _between the successive elements in its sorted form_.
## Notes

- **_Array/list_** size is _at least 3_ .
- **_Array/list's numbers_** Will be **mixture of positives and negatives also zeros_**
- **_Repetition_** of numbers in _the array/list could occur_.
- **_The Maximum Gap_** is _computed Regardless the sign_.
---
## Input >> Output Examples

```
maxGap ({13,10,5,2,9}) ==> return (4)
```

## **_Explanation_**:

- **_The Maximum Gap_** _after sorting the array is_ `4` , _The difference between_ `9 - 5 = 4` .
```
maxGap ({-3,-27,-4,-2}) ==> return (23)
```

## **_Explanation_**:

- **_The Maximum Gap_** _after sorting the array is_ `23` , _The difference between_ `|-4- (-27) | = 23` .
- **_Note_** : _Regardless the sign of negativity_ .
```
maxGap ({-7,-42,-809,-14,-12}) ==> return (767)  
```

## **_Explanation_**:

- **_The Maximum Gap_** _after sorting the array is_ `767` , _The difference between_ `| -809- (-42) | = 767` .
- **_Note_** : _Regardless the sign of negativity_ .

```
maxGap ({-54,37,0,64,640,0,-15}) //return (576)
```

## **_Explanation_**:

- **_The Maximum Gap_** _after sorting the array is_ `576` , _The difference between_ `| 64 - 640 | = 576` .
- **_Note_** : _Regardless the sign of negativity_ .

Answer:
```
function maxGap (numbers){
  numbers.sort((a, b) => a - b);
  let max = numbers[1] - numbers[0];
  for(let i = 2; i < numbers.length; i++){
    if(numbers[i] - numbers[i-1] > max) max = numbers[i] - numbers[i-1];
  }
  return max;
}
```
Sort array and then compare each pair's difference, returning the largest number, max. Sorting is O(n log n) while iterating over the array is O(n) therefore the time complexity is O(n log n).

Answer with methods:
```
function maxGap(numbers) {
  return numbers
    .sort((a, b) => a - b) // Sort the array
    .reduce((max, n, i, arr) => { // Include 'arr' for the array reference
      if (i < arr.length - 1) { // Only access arr[i + 1] if we're not at the last index
        let gap = arr[i + 1] - n;
        if (max < gap) {
          max = gap;
        }
      }
      return max;
    }, 0);
}

```
Time complexity is same as above, O(n log n).

# Product Array (Array Series #5) (7kyu)
## Task

**_Given_** an _array/list [] of integers_ , **_Construct_** a _product array **_Of same size_** Such That prod[i] is equal to The Product of all the elements of Arr[] except Arr[i]_.
## Notes

- **_Array/list_** size is _at least 2_ .
- **_Array/list's numbers_** Will be **_only Positives
- **_Repetition_** of numbers in _the array/list could occur_.
---
## Input >> Output Examples

```
productArray ({12,20}) ==>  return {20,12}
```
## **_Explanation_**:

- **_The first element_** _in prod [] array_ **_20_** _is the product of all array's elements except the first element
- **_The second element_** **_12_** _is the product of all array's elements except the second element_ .

```
productArray ({1,5,2}) ==> return {10,2,5}
```
## **_Explanation_**:

- **_The first element_** **_10_** _is the product of all array's elements_ **_except_** _the first element **_1_**
- **_The second element_** **_2_** _is the product of all array's elements_ **_except_** _the second element_ **_5
- **_The Third element_** **_5_** _is the product of all array's elements_ **_except_** _the Third element_ **_2_**.

```
productArray ({10,3,5,6,2}) return ==> {180,600,360,300,900}
```
## **_Explanation_**:

- **_The first element_** **_180_** _is the product of all array's elements_ **_except_** _the first element_ **_10
- **_The second element_** **_600_** _is the product of all array's elements_ **_except_** _the second element_ **_3
- **_The Third element_** **_360_** _is the product of all array's elements_ **_except_** _the third element_ **_5
- **_The Fourth element_** **_300_** _is the product of all array's elements_ **_except_** _the fourth element_ **_6
- _Finally_ ,**_The Fifth element_** **_900_** _is the product of all array's elements_ **_except_** _the fifth element_ **_2_**

My Answer:
```
function productArray(numbers){
  let maxProd = numbers.reduce((product, num) => product * num, 1);
  return numbers.map(num => maxProd / num);
}
```
O(n) is spent on calculating the total product with reduce(). O(n) is spent on the map() method to compute the final array. O(n) + O(n) = O(2n). Since O(2n) simplifies to O(n) - constant factors are dropped when expressing time complexity - the overall time complexity is O(n). 

A more unclear answer: 
```
const mul = (v, w) => v * w;
const product = a => a.reduce(mul, 1);

function productArray(a) {
  const p = product(a); //Get the product of all elements in the array
  return a.map(v => p / v); //Return new array where each element is p/v
}
```
This solution uses two helper functions with runtime as O(n).

# Maximum Triplet Sum (Array Series #7) (7kyu)
## Task

**_Given_** an _array/list [] of n integers_ , _find maximum triplet sum in the array_ **_Without duplications_** .
## Notes :

- **_Array/list_** size is _at least 3_ .
- **_Array/list_** numbers could be a _mixture of positives , negatives and zeros_ .
- **_Repetition_** of numbers in _the array/list could occur_ , So **_(duplications are not included when summing)_**.
## Input >> Output Examples
```cpp
maxTriSum ({3,2,6,8,2,3}) ==> return (17)
```
## **_Explanation_**:

- As the **_triplet_** that _maximize the sum_ **_{6,8,3}_** in order , **_their sum is (17)
- _Note_ : **_duplications_** _are not included when summing_ , **(i.e) the numbers added only once** .
```
maxTriSum ({2,1,8,0,6,4,8,6,2,4}) ==> return (18)
```

## **_Explanation_**:
- As the **_triplet_** that _maximize the sum_ **_{8, 6, 4}_** in order , **_their sum is (18)_** ,
- _Note_ : **_duplications_** _are not included when summing_ , **(i.e) the numbers added only once** .
    ```cpp
maxTriSum ({-7,12,-7,29,-5,0,-7,0,0,29}) ==> return (41)
    ```
## **_Explanation_**:
- As the **_triplet_** that _maximize the sum_ **_{12 , 29 , 0}_** in order , **_their sum is (41)_** ,
- _Note_ : **_duplications_** _are not included when summing_ , **(i.e) the numbers added only once** .

Answer:
```
function maxTriSum(numbers){
  numbers.sort((a, b) => b - a)
  return Array.from(new Set(numbers)).slice(0, 3).reduce((sum,n) => sum + n, 0);
}
```
Sort the array from greatest to least. Then use a set to remove duplicate elements, convert it back to an array so we can use array methods on it. Slice into the array, returning only the first three (greatest) elements and then sum them with reduce before returning the total sum. Time complexity is O(n).

Another answer, similar but cleaner:
```
function maxTriSum(numbers){
  return [...new Set(numbers)]
    .sort( (a,b) => a - b)
    .slice(-3)
    .reduce( (acc, n) => acc + n, 0);
}
```
Using brackets and the spread operator (...) avoids having to use the .from() method and removing duplicates before sorting makes the code slightly more efficient. This sorts from least to greatest and slice(-3) returns the 3 elements at the end.