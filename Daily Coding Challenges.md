//Last added # Beginner Series #4 Cockroach
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

 Examples (Input -> Output):

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
```javascript
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
```javascript
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
```javascript
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
```javascript
{ 
	2: 0, // index 0, value 2 
	7: 1, // index 1, value 7 
	11: 2, // index 2, value 11 
	15: 3 // index 3, value 15 
}
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
# Row Weights (7kyu)
Several people are standing in a row divided into two teams. The first person goes into team 1, the second goes into team 2, the third goes into team 1, and so on.
### Task

Given an **array of positive integers** (the weights of the people), return a new array / tuple of two integers (depending on your language), whereby the first one is the total weight of team 1, and the second one is the total weight of team 2. Note that the **array will never be empty**.
### Examples

- `[13, 27, 49]` returns `[62, 27]` or `(62, 27)` (depending on your language) because the total weight of team 1 is 13+49=62 13 + 49 = 62 13+49=62 and the total weight of team 2 is 27 27 27.
- `[50, 60, 70, 80]` returns `[120, 140]` or `(120, 140)` (depending on your language) because the total weight of team 1 is 50+70=120 50 + 70 = 120 50+70=120 and the total weight of team 2 is 60+80=140 60 + 80 = 140 60+80=140.
- `[80]` returns `[80, 0]` or `(80, 0)` (depending on your language) because the total weight of team 1 is 80 80 80 and the total weight of team 2 is 0 0 0.

My answer:
```
function rowWeights(array){
  let teamWeights = [0, 0]
  array.filter((person, idx) =>{
    idx % 2 ? teamWeights[1] += person: teamWeights[0] += person;
  })
  return teamWeights;
}
```

One liner using .reduce():
```
// rowWeights=arr=>arr.reduce((a,b,i)=>(a[i%2]+=b,a),[0,0])

rowWeights= arr =>
	arr.reduce((sum, person, idx) => (sum[idx % 2] += person, sum) ,[0,0])
```
The code sum[idx % 2] will always return 0 or 1, adding the value of person to the correct array index. The comma operator (,) returns the value of the last operand. Equivalent to 
```
sum[idx%2]+=person; return sum;
```
or a return statement. If there is no return statement then the values are not updated in the array and we get a 'NaN'. Great way to use .reduce() to return a two length array.

A refactored answer based on what I learned above:
```
function rowWeights(array){
  let teamWeights = [0, 0]
  array.filter((person, idx) => teamWeights[idx % 2] += person)
  return teamWeights;
}
```
# Form the Minimum (7kyu)
### Task

Given a list of digits, return the **smallest number** that could be formed from these digits, using the digits only once (ignore duplicates). **Only positive integers** in the range of 1 to 9 will be passed to the function.

### Examples

```
[1, 3, 1] ==> 13
[5, 7, 5, 9, 7] ==> 579
[1, 9, 3, 1, 7, 4, 6, 6, 7]  ==> 134679
```
My Answer:
```
function minValue(values){
  //Convert to set to get rid of duplicate values
  //Convert back to array to sort from min -> max
  //Convert to String to create a single number from digits
  //Convert back to number to return value
  return Number([...new Set(values)].sort((a, b) => a - b).join(""))
}
```

Another answer without Set:
```
function minValue(values){
  const n = values
    .filter((e, i, arr) => arr.indexOf(e) === i)
    .sort()
    .join('');
  return Number(n);
}
```
Not only is it formatting cleanly, making it easy to read but it avoids creating a Set, and thus saving us from having to convert to a set and then back to an array. arr.indexOf(e) returns the first occurrence of e and thus filter will not add duplicates to the filtered array. From there we sort -default is by string-equivalent and min->max but since we are only using values 1-9 we do not have to bother with (a,b) => a-b saving us keystrokes. Join converts an array into a string, and then we return the string converted to a integer.

# Minimum Steps (Array Series #6)
## Task

**_Given_** _an array of N integers, you have to find_ **_how many times_** _you have to_ **_add up the smallest numbers_** _in the array until_ **_their Sum_** _becomes greater or equal to_ **_K_**.
## Notes:

- **_List size_** is _at least 3_.
- **_All numbers_** _will be_ **_positive_**.
- **_Numbers_** could _occur more than once_ , **_(Duplications may exist)_**.
- Threshold **_K_** will _always be reachable_.
    ## Input >> Output Examples

```
minimumSteps({1, 10, 12, 9, 2, 3}, 6)  ==>  return (2)
```
## **_Explanation_**:

- We _add two smallest elements_ **_(1 + 2)_**, _their sum is 3_ .
- **_Then_** we **_add the next smallest number to it (3 + 3)_** , so _the sum becomes 6_ .
- **_Now_** the result is greater or equal to **_6_** , _Hence the output is (2) i.e (2) operations are required to do this_ .
    ```
    minimumSteps({8, 9, 4, 2}, 23)  ==> return (3)
    ```
    ## **_Explanation_**:
- We _add two smallest elements_ **_(4 + 2)_**, _their sum is 6_ .
- **_Then_** we **_add the next smallest number to it (6 + 8)_** , so _the sum becomes 14_ .
- **_Now_** we **_add the next smallest number (14 + 9)_** , so _the sum becomes 23_ 
- **_Now_** the result is greater or equal to **_23_** , _Hence the output is (3) i.e (3) operations are required to do this_ .
    ```
    minimumSteps({19,98,69,28,75,45,17,98,67}, 464)  ==>  return (8)
    ```
    ## **_Explanation_**:
- We _add two smallest elements_ **_(19 + 17)_**, _their sum is 36_ .
- **_Then_** we **_add the next smallest number to it (36 + 28)_** , so _the sum becomes 64_ .
- We need to **_keep doing this_** _until **_the sum_** becomes greater or equal to **_K_** (464 in this case)_, which will require **8_** Steps .

My Answer:
```
function minimumSteps(numbers, value){
  //Sort numbers array ascending
  numbers.sort((a, b) => a - b);
  
  //Special case for first num bigger than value. 
  if(numbers[0] > value) return 0;
  
  //Count steps and keep track of sum
  let counter = 1, sum = numbers[0] + numbers[1];
  
  //Pop numbers out of array as we use them
  numbers.shift();
  numbers.shift();
  
  //Stop adding when sum >= value
  while(sum < value){
    sum += numbers[0];
    counter++;
    numbers.shift();
  }
  return counter;
}
```
Very scuffed. Not at all optimal.

A better answer:
```
function minimumSteps(numbers, value){
   return numbers.sort((a, b) => a - b).filter(e => (value -= e) > 0).length;
}
```
Sort array ascending and then call filter. The conditional subtracts the current element from the value and checks if it is greater than zero. Covers the edge case where smallest element is greater than the value while checking to see if the sum of the added elements are greater or equal to the desired target value. Once a shallow copy of the array ft. those elements are found, we return the length as the minimum steps. 
# Maximum Product (7kyu)
### Task
Given an array of integers , Find **the maximum product** obtained from multiplying 2 adjacent numbers in the array. Note that the array size is at least 2 and consists a mixture of positive, negative integers and also zeroes.

### Examples
- `[1, 2, 3]` returns `6` because the maximum product is obtained from multiplying  2∗3=6\ 2 * 3 = 6  2∗3=6
- `[9, 5, 10, 2, 24, -1, -48]` returns `50` because the maximum product is obtained from multiplying  5∗10=50\ 5 * 10 = 50  5∗10=50
- `[-23, 4, -5, 99, -27, 329, -2, 7, -921]` returns `-14` because the maximum product is obtained from multiplying  −2∗7=−14\ -2 * 7 = -14  −2∗7=−14

Answer: 
```
function adjacentElementsProduct(array) {
  return array.reduce((product, element, idx)=> {
  if(array[idx+1] != undefined){
    let localProduct = element * array[idx+1] 
    if(localProduct > product){
      product = localProduct;
      }
    }
    return product;
  },-Infinity)
}
```
Iterate over the array, comparing each element with the next one. We do an 'undefined' comparison with the next element to avoid going out of bounds. If the current product is greater than the max product then we reassign. Time complexity O(n), space complexity O(1). 

Another answer using a for loop instead:
```
function adjacentElementsProduct(array) {
  let maxProduct = -Infinity;

  for (let i = 0; i < array.length - 1; i++) {
    let currentProduct = array[i] * array[i + 1];
    if (currentProduct > maxProduct) {
      maxProduct = currentProduct;
    }
  }

  return maxProduct;
}
```

Another answer:
```
const adjacentElementsProduct = (array) => array.slice(1).reduce(
  (max, cur, i) => Math.max(array[i] * cur, max), -Infinity
);
```
Slice(1) skips the first element. During the reduce function call, we multiply the previous element (array[i]) with the current element (cur). Math.max then compares the product with the current value of max - which starts out as -Infinity. 

My answer using reduce() the next day:
```
function adjacentElementsProduct(array) {
  return array.slice(1).reduce((maxProduct, n, idx) =>{
    let localProduct = n * array[idx];
    if(localProduct > maxProduct) maxProduct = localProduct;
    return maxProduct;
  }, -Infinity);
}
```

# Nth Smallest Element (Array Series #4) (7kyu)
### Task
Given an array/list of integers, find the Nth smallest element in the array.
### Notes
- Array/list size is at least 3.
- Array/list's numbers could be a mixture of positives , negatives and zeros.
- Repetition in array/list's numbers could occur, so don't remove duplications.

### Input >> Output Examples
```
arr=[3,1,2]            n=2    ==> return 2 
arr=[15,20,7,10,4,3]   n=3    ==> return 7 
arr=[2,169,13,-5,0,-1] n=4    ==> return 2 
arr=[2,1,3,3,1,2],     n=3    ==> return 2 
```

My answer:
```
function nthSmallest(arr, pos){
  return arr.sort((a,b)=>a-b)[pos-1]
}
```
Sort the array and then use position variable (minus one) to give the smallest nth element in the array. It modifies the original array so it is not the best practice.

Another answer using recursion but O(n) runtime:
```
const prepend = (v,a) => [v].concat(a) ;
const insert = (a,v) => a.length ? v<=a[0] ? prepend(v,a.slice(0,-1)) : prepend(a[0],insert(a.slice(1),v)) : [] ;
const nthSmallest = (a,n) => a.reduce(insert,Array.from( { length: n }, () => Infinity ))[n-1] ;
```
The `prepend` function adds a value to the beginning of an array, while the `insert` function recursively inserts a value into a sorted array to maintain order. The `nthSmallest` function uses `reduce` to accumulate the smallest `n` elements from the input array, inserting each element in sorted order, starting with an array of `n` `Infinity` values. After processing all elements, it returns the nth smallest element by accessing the `n-1` index of the sorted array. This approach efficiently finds the nth smallest element without fully sorting the entire array.

Insert:
a.length ? ... : []; -> Check if array is empty, if empty then return empty array []. This is the base case of the recursive function.


# Transform to Prime (6kyu)
## Task :

**_Given_** _a List [] of n integers_, **_find minimum number_** to be **inserted** in a _list_, so that **_sum of all elements of list_** should _equal the closest prime number_ .

---

## Notes

- **_List size_** is _at least 2_ .
- **_List's numbers_** will only **_positives_** (n > 0) .
- **_Repetition_** of numbers in the list **_could occur_** .
- **_The newer list's sum_** should _equal the closest prime number_ .
## Input >> Output Examples

```cpp
minimumNumber ({3,1,2}) ==> return (1)
```
## **_Explanation_**:

- **_Since_** **the sum** of the list's elements equal to **_(6)_** , _the minimum number to be inserted to transform the sum to prime number_ is **_(1)_** , _which will make **_the sum of the List_** equal the closest prime number **_(7)_** .


```cpp
minimumNumber ({2,12,8,4,6}) ==> return (5)
```
## **_Explanation_**:

- **_Since_** **the sum** of the list's elements equal to **_(32)_** , _the minimum number to be inserted to transform the sum to prime number_ is **_(5)_** , _which will make **_the sum of the List_** equal the closest prime number **_(37)_** .


```cpp
minimumNumber ({50,39,49,6,17,28}) ==> return (2)
```
## **_Explanation_**:

- **_Since_** , **the sum** of the list's elements equal to **_(189)_** , _the minimum number to be inserted to transform the sum to prime number_ is **_(2)_** , _which will make **_the sum of the List_** equal the closest prime number **_(191)_** .

My Answer:
```
function minimumNumber(numbers){
  // Sum the array
  let total = numbers.reduce((total, n) => total + n, 0);
  // Check total for prime number, incrementing by one until found
  for(let i = total; ; i++){
    if(prime(i)) return i - total;
  }
}

// Helper function to check for primes
function prime(num){
  if(num <= 1) return false;
  if(num <= 3) return true;
  if(num % 2 === 0 || num % 3 === 0) return false;
    
  // Check for factors from 5 to sqrt(num)
  for (let i = 5; i * i <= num; i += 6) {
    if (num % i === 0 || num % (i + 2) === 0) {
      return false;
    }
  }
  return true;
}
```

Another answer:
```
function minimumNumber(numbers){
  let sum = numbers.reduce((a,b) => a + b)
  for(let i = sum; ; i++) {
    if(prime(i)) return i - sum
  }
  function prime(a) {
    if(a < 2) return false
    if(a % 2 === 0) return a === 2
    for(let i = 3; i * i <= a; i += 2) {
      if(a % i === 0) return false
    }
    return true
  }
}
```

String Katas

# Dot Calculator (7kyu)
You have to write a calculator that receives strings for input. The dots will represent the number in the equation. There will be dots on one side, an operator, and dots again after the operator. The dots and the operator will be separated by one space.

Here are the following valid operators :

- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `//` Integer Division

## Your Work (Task)

You'll have to return a string that contains dots, as many the equation returns. If the result is 0, return the empty string. When it comes to subtraction, the first number will always be greater than or equal to the second number.

### Examples (Input => Output)

```
* "..... + ..............." => "...................."
* "..... - ..."             => ".."
* "..... - ."               => "...."
* "..... * ..."             => "..............."
* "..... * .."              => ".........."
* "..... // .."             => ".."
* "..... // ."              => "....."
* ". // .."                 => ""
* ".. - .."                 => ""
```

My Answer:
```
function dotCalculator (equation) {
  let arr = equation.split(" ");
  if(arr[1] === "+"){
    return ".".repeat(arr[0].length + arr[2].length);
  }else if(arr[1] === "-"){
    return ".".repeat(arr[0].length - arr[2].length);
  }else if(arr[1] === "*"){
    return ".".repeat(arr[0].length * arr[2].length);
  }else{ //implicit divide
    return ".".repeat(arr[0].length / arr[2].length);
  }
}
```
```
function dotCalculator (equation) {
  let arr = equation.split(" ");
  return arr[1] === "+" ? ".".repeat(arr[0].length + arr[2].length) :
          arr[1] === "-" ? ".".repeat(arr[0].length - arr[2].length) :
            arr[1] === "*" ? ".".repeat(arr[0].length * arr[2].length) :
              ".".repeat(arr[0].length / arr[2].length);
}
```
Solution refactored several times to clean it up. It has good performance and readability but suspect maintainability. An object-oriented solution would be better. 

An answer using objects:
```
const dotCalculator = (equation) => {
  const operations = {
    '+' : (a, b) => a + b,
    '-' : (a, b) => a - b,
    '*' : (a, b) => a * b,
    '//': (a, b) => a / b,
  };
  const [left, operator, right] = equation.split(' ');
  return '.'.repeat(operations[operator](left.length, right.length));
}
```
An object allows us define each different operation. Then we use destructuring assignment (syntax that makes it possible to unpack values from arrays or properties from objects into distinct variables) into a left value, an operator and a right value. Then we call upon the object and plug in the values into the repeat string function to return the correct amount of dots. 

An answer using a switch statement:
```
function dotCalculator (equation) {
  const arr = equation.split(' ');
  switch ( arr[1] ){
      case '+':
      return '.'.repeat( arr[0].length + arr[2].length )
      case '-':
      return '.'.repeat( arr[0].length - arr[2].length )
      case '*':
      return '.'.repeat( arr[0].length * arr[2].length )
      default:
      return '.'.repeat( arr[0].length / arr[2].length )
  }
}
```
# Correct the mistakes of the character recognition software (8 kyu)
Character recognition software is widely used to digitise printed texts. Thus the texts can be edited, searched and stored on a computer.

When documents (especially pretty old ones written with a typewriter), are digitised character recognition softwares often make mistakes.

Your task is correct the errors in the digitised text. You only have to handle the following mistakes:

- `S` is misinterpreted as `5`
- `O` is misinterpreted as `0`
- `I` is misinterpreted as `1`

The test cases contain numbers only by mistake.

An answer using an Object:
```
const corrections = {
	'5': 'S',
	'0': 'O',
  '1': 'I',
};

const correct = string => (
	string.replace(/[501]/g, character => corrections[character])
);
```

My answer:
```
function correct(string){
//   let newString = ""
//   for(let i = 0; i < string.length;i++){
//     if(string[i]==="5"){
//       newString += "S";
//     }else if(string[i]==="0"){
//        newString += "O";    
//     }else if(string[i]==="1"){
//        newString += "I";    
//     }else{
//       newString += string[i];
//     }
//   }
//   return newString
	return string.replaceAll("0", "O").replaceAll("1", "I").replaceAll("5", "S")
}
```
Top solution doesn't feature any methods but isn't very maintainable. The second one loops over the array three times. Neither is ideal

# Cat years, Dog years (8kyu)
I have a cat and a dog.

I got them at the same time as kitten/puppy. That was `humanYears` years ago.

Return their respective ages now as [`humanYears`,`catYears`,`dogYears`]

NOTES:

- `humanYears` >= 1
- `humanYears` are whole numbers only

## Cat Years

- `15` cat years for first year
- `+9` cat years for second year
- `+4` cat years for each year after that

## Dog Years

- `15` dog years for first year
- `+9` dog years for second year
- `+5` dog years for each year after that

My answer:
```
var humanYearsCatYearsDogYears = function(humanYears) {
  let catYears = 0;
  let dogYears = 0;
  if(humanYears === 1){
    catYears = 15;
    dogYears = 15;
  }else if(humanYears === 2){
    catYears = 24;
    dogYears = 24;
  }else{
    catYears = 24 + (humanYears-2) * 4;
    dogYears = 24 + (humanYears-2) * 5;
  }
  
  return [humanYears,catYears,dogYears];
}
```

A better answer:
```
var humanYearsCatYearsDogYears = function(y) {
  if (y == 1) return [1, 15, 15]
  if (y == 2) return [2, 24, 24]
  return [y, (y-2) * 4 + 24, (y-2) * 5 + 24]
}
```
# Ones and Zeros (7kyu)
Given an array of ones and zeroes, convert the equivalent binary value to an integer.

Eg: `[0, 0, 0, 1]` is treated as `0001` which is the binary representation of `1`.

Examples:

```
Testing: [0, 0, 0, 1] ==> 1
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 0, 1] ==> 5
Testing: [1, 0, 0, 1] ==> 9
Testing: [0, 0, 1, 0] ==> 2
Testing: [0, 1, 1, 0] ==> 6
Testing: [1, 1, 1, 1] ==> 15
Testing: [1, 0, 1, 1] ==> 11
```

However, the arrays can have varying lengths, not just limited to `4`.

Answer:
```
const binaryArrayToNumber = arr => {
  return parseInt(arr.join(""), 2)
};
```
The **`parseInt()`** function parses a string argument and returns an integer of the specified [radix](https://en.wikipedia.org/wiki/Radix) (the base in mathematical numeral systems). Arr.join("") creates a string from the array. By calling parseInt and 2, we convert the string into a number using binary. 

# Asterisk counting (7kyu)
You receive the name of a city as a string, and you need to return a string that shows how many times each letter shows up in the string by using asterisks (`*`).

For example:

```
"Chicago"  -->  "c:**,h:*,i:*,a:*,g:*,o:*"
```

As you can see, the letter `c` is shown only once, but with 2 asterisks.

The return string should include **only the letters** (not the dashes, spaces, apostrophes, etc). There should be no spaces in the output, and the different letters are separated by a comma (`,`) as seen in the example above.

Note that the return string must list the letters in order of their first appearance in the original string.

More examples:

```
"Bangkok"    -->  "b:*,a:*,n:*,g:*,k:**,o:*"
"Las Vegas"  -->  "l:*,a:**,s:**,v:*,e:*,g:*"
```

My answer:
```
function isLetter(char){ //Helper function to determine letter
  return char.toUpperCase() != char.toLowerCase();
}

function getStrings(city){
  let strCount = {};
  let cityStr = [];
  
  //Loop over string to populate Object
  for(let i = 0; i < city.length; i++){
    let char = city[i].toLowerCase();
    if(isLetter(city[i])){
      if(strCount.hasOwnProperty(char)){
      	strCount[char] += 1;
      }else{
      	strCount[char] = 1;
      }
    }
  }
  //Loop over Object to fill an array for return
  for(let key in strCount){
  	cityStr.push(`${key}:${"*".repeat(strCount[key])}`)
  }
  
  return cityStr.join(',');
}
```
Helper function is a solution stolen from stackoverflow. The logic is that only a letter will morph when comparing it's uppercase value to lowercase. A number or punctuation will remain the same. We iterate through the string, incrementing the object if it's there or setting the object to one if it's not. Then we use another loop to push the value of "key:value" to the array where value is asterisks repeated with the repeat() string function. The join() method is called upon to add commas between each array value and returned as a string.

```
function getStrings(city) {
    city = city.toLowerCase();
    let obj = {};
    let str = '';

    for (let elem of city) {
	    if(elem.toUpperCase() != elem.toLowerCase()){
	        if (!(elem in obj)) {
	            obj[elem] = '*';
	        } else {
	            obj[elem] += '*';
	        }
	    }
    }

    for (let key in obj) {
        if (key !== ' ') {
            str += key + ':' + obj[key] + ',';
        }
    }

    return str.substring(0, str.length - 1);
}
```
This solution is slightly modified, using my code to check for letter. It has the same blueprint but is slightly more efficient. For one the object is incremented with asterisks directly, circumventing any need for the repeat() method. In the second loop, hasOwnProperty() is not called either, instead just checking if there exists another key. And instead of an array, a string is used, manually adding commas to the end. When we finally return the string, we cut off the very last character of the string using a substring() method call. 
# The Office I - Outed (7kyu)
Your colleagues have been looking over your shoulder. When you should have been doing your boring real job, you've been using the work computers to smash in endless hours of codewars.

In a team meeting, a terrible, awful person declares to the group that you aren't working. You're in trouble. You quickly have to gauge the feeling in the room to decide whether or not you should gather your things and leave.

Given an object ( `meet` ) containing team member names as keys, and their happiness rating out of 10 as the value, you need to assess the overall happiness rating of the group. If <= 5, return 'Get Out Now!'. Else return 'Nice Work Champ!'.

Happiness rating will be total score / number of people in the room.

Note that your boss is in the room ( `boss` ). Their score is worth double its face value (but they are still just one person!).

My Answer:
```
function outed(meet, boss){
  let happiness = 0;
  let totalCoworkers = 0;
  for (const [human, value] of Object.entries(meet)) {
    totalCoworkers++;
    human === boss ? happiness += value*2 : happiness += value;
  }
  return (happiness/totalCoworkers) <= 5 ? 'Get Out Now!' : 'Nice Work Champ!'
}
```
Another answer:
```
function outed(meet, boss) {
  let names = Object.keys(meet)
  let score = names.reduce((s,v) => s + meet[v], 0) + meet[boss]
  return score / names.length > 5 ? 'Nice Work Champ!' : 'Get Out Now!'
}
```
Save keys in an array and use that array to call the reduce() method. We don't need to do a comparison for boss, just add it on as extra after. meet[v] calls the value. Then we return the score divided by number of employees and return the corresponding string.
# The Office II - Boredom Score (7kyu)
Every now and then people in the office moves teams or departments. Depending what people are doing with their time they can become more or less boring. Time to assess the current team.

You will be provided with an object(staff) containing the staff names as keys, and the department they work in as values.

Each department has a different boredom assessment score, as follows:

accounts = 1  
finance = 2  
canteen = 10  
regulation = 3  
trading = 6  
change = 6  
IS = 8  
retail = 5  
cleaning = 4  
pissing about = 25  

Depending on the cumulative score of the team, return the appropriate sentiment:

<=80: 'kill me now'  
< 100 & > 80: 'i can handle this'  
100 or over: 'party time!!'

My Answer:
```
let boredomScores = {
  'accounts': 1,
  'finance': 2, 
  'canteen': 10,
  'regulation': 3,
  'trading': 6,
  'change': 6,
  'IS': 8,
  'retail': 5,
  'cleaning': 4,
  'pissing about': 25,
}

function boredom(staff){
  let people = Object.keys(staff);
  let score = people.reduce((sum, n) => sum + boredomScores[staff[n]], 0);
  return score > 80 && score < 100 ? 'i can handle this' :
         score <= 80 ? 'kill me now' : 'party time!!'
}
```
Define values in boredomScore. Place names in people array. Call reduce() method on people array, using each current value go into staff for the corresponding thing and then using the boredeomScore obj to return a numerical value. Once everything is added up, we return a different string based on the score. 

Another ans:
```
function boredom(staff){
   var map = {...}; //same as my boredomScores
   var score = Object.keys(staff).reduce(
     function(a,b){       
       return a+map[staff[b]]
    },0); 
   
   return score <= 80 ? 'kill me now': score < 100 && score > 80 ? 'i can handle this' : 'party time!!';
}
```
This answer differs slightly. Instead of having a separate variable for the Object.keys(staff), instead reduce is called directly upon it. I rate this solution as slightly more efficient.

# The Office III - Broken Photocopier (7kyu)
The bloody photocopier is broken... Just as you were sneaking around the office to print off your favorite binary code!

Instead of copying the original, it reverses it: '1' becomes '0' and vice versa.

Given a string of binary, return the version the photocopier gives you as a string.

My answer:
```
function broken(x){
  return x.split('').map(ch => ch === "1" ? "0" : "1").join(''); 
}
```
# The Office IV - Find a Meeting Room (7kyu)
Your job at E-Corp is both boring and difficult. It isn't made any easier by the fact that everyone constantly wants to have a meeting with you, and that the meeting rooms are always taken!

In this kata, you will be given an array. Each value represents a meeting room. Your job? Find the **first** empty one and return its index (N.B. There may be more than one empty room in some test cases).

```
'X' --> busy
'O' --> empty
```

If all rooms are busy, return `"None available!"`

My Answer:
```
function meeting(x){
  let room = x.findIndex(n => n ==='O');
  return room !== -1 ? room : 'None available!';
}
```

# The Office V - Find a Chair
So you've found a meeting room - phew! You arrive there ready to present, and find that someone has taken one or more of the chairs!! You need to find some quick.... check all the other meeting rooms to see if all of the chairs are in use.

Your meeting room can take up to `8` chairs. `need` will tell you how many have been taken. You need to find that many.

Find the spare chairs from the array of meeting rooms. Each meeting room tuple will have the number of occupants as a string. Each occupant is represented by `'X'`. The room tuple will also have an integer telling you how many chairs there are in the room.

You should return an array of integers that shows how many chairs you take from each room in order, up until you have the required amount.

example:

`[['XXX', 3], ['XXXXX', 6], ['XXXXXX', 9], ['XXX',2]]` when you need `4` chairs:

`result -> [0, 1, 3]` no chairs free in room 0, take `1` from room 1, take `3` from room 2. no need to consider room 3 as you have your `4` chairs already.

If you need no chairs, return `"Game On"`. If there aren't enough spare chairs available, return `"Not enough!"`.

My answer:
```
function meeting(x, need){
  if(need === 0){
    return "Game On";
  }
  
  let chairsTaken = [];
  
  for(let i = 0; i < x.length; i++){
    let openChairs = x[i][1] - x[i][0].length;
    if(openChairs <= 0){
      chairsTaken.push(0);
    }else{
      need -= openChairs;
      chairsTaken.push(openChairs);    
      if(need < 0){
        chairsTaken[chairsTaken.length-1] += need;
        break;
      }else if(need === 0){
        break;
      }
    }
  }
  
  
  return need > 0 ? "Not enough!" : chairsTaken;
}
```
Start off by checking if we need any chairs. If we don't we can end the function and return 'Game On' immediately. We have a counter variable to keep track of all the chairs taken from each room.  We loop over each room. If open chairs is <= 0, we push 0 to the array. Else we subtract the number of free chairs from the need variable given to the function and push the value to the array. Within this statement we also check if need is < 0. If it is we do some correction, adding the value of need to last element of the array and then ending the loop. Another check after for need equaling exactly zero to break out of the loop. Kind of poor solution imho. Finally we return the chairsTaken array or a string if a solution could not be found

A better soln:
```
function meeting(rooms, need) {
  if (need <= 0) {
    return 'Game On';
  }
  const taken = [];
  for (const [{ length: chairs }, people] of rooms) {
    const take = Math.min(Math.max(people - chairs, 0), need);
    taken.push(take)
    need -= take;
    if (need <= 0) {
      return taken;
    }
  }
  return 'Not enough!';
}
```
Much better solution. Starts out the same as mine with the quick return statement if no need of chairs and a variable to hold the array of chairs. Uses destructuring assignment -> [{ length: chairs }, people] <- where we are unpacking values from arrays into distinct variables.  Object destructuring is used to yield the length of chairs as a variable. Once we have these two values, iterating is far easier. Math.min and and Math.max are used to find the max chairs we can take and Math.min to return 0 or how many chairs we need. Need is appropriately decremented and then there is one check to see if we have met our need - returning the taken array. If by the end the need array is not 0, we return the string. 

# Next Palindromic Number
There were and still are many problem in CW about palindrome numbers and palindrome strings. We suposse that you know which kind of numbers they are. If not, you may search about them using your favourite search engine.

In this kata you will be given a positive integer, `val` and you have to create the function `next_pal()`(`nextPal` Javascript) that will output the smallest palindrome number higher than `val`.

Let's see:

```javascript
For Javascript
nextPal(11) == 22

nextPal(188) == 191

nextPal(191) == 202

nextPal(2541) == 2552
```

You will be receiving values higher than 10, all valid.

My answer:
```
function nextPal(val) {
    for(let i = val + 1; i < Infinity; i++){
        let str = i.toString();
        if(checkPalindrome(str)) return i;
    }
}

// Helper function to check palindrome
function checkPalindrome(str){
    for(let i = 0; i < str.length/2; i++){
        if(str.charAt(i) !== str.charAt(str.length - 1 - i)) return false;
    }
    return true;
}
```
Converts num to string, and then throws it to helper function. The funcction checkPalindrome() loops over half the string, comparing the first letter to the last letter. If they are ever not the same then it throws a false. If it's done looping and it never returns false then it must be a palindrome and it returns true.

Another ans:
```
function nextPal(val) {
  do {
    val++;
  } while(!isPalindrome(val))
  return val;
}

function isPalindrome(num) {
  return num === reverseNum(num);
}

function reverseNum(num) {
  return parseInt(num.toString().split('').reverse().join(''));
}
```
Uses two helper functions. The real meat is reverseNum() which converts to a string, splits it to an array, reverses the array, joins the array and then converts it back to a number to return. The number is then compared to the original number in isPalindrome() which returns a true/false to the main function.

Another ans, refactored
```
const nextPal = val => {
  while (++val != [...`${val}`].reverse().join(``)) ;
  return val;
};
```
This solution is the same one as above but far more concise. `++val` is a pre-increment, adding one, evaluating and then storing the value. ++val increments by one, starting it at the number greater than val. First, it converts the number val to a string using template literal syntax (`${val}`). The string is then converted into an array of its characters using [...]. Then the array methods reverse() and join() are called to turn it back into a string. We don't have to convert it back to a number because JS attempts to convert the string to a number.

# Invalid Input - Error Handling #1 (7kyu)
Error Handling is very important in coding and seems to be overlooked or not implemented properly.

## Task

Your task is to implement a function which takes a string as input and return an object containing the properties vowels and consonants. The vowels property must contain the total count of vowels {a,e,i,o,u}, and the total count of consonants {a,..,z} - {a,e,i,o,u}. Handle invalid input and don't forget to return valid ones.

## Input

The input is any random string. You must then discern what are vowels and what are consonants and sum for each category their total occurrences in an object. However you could also receive inputs that are not strings. If this happens then you must return an object with a vowels and consonants total of 0 because the input was NOT a string. Refer to the Example section for a more visual representation of which inputs you could receive and the outputs expected. :)

## Example:

```javascript
Input: getCount('test')
Output: {vowels:1,consonants:3}

Input: getCount('tEst')
Output: {vowels:1,consonants:3}

Input getCount('    ')
Output: {vowels:0,consonants:0}

Input getCount()
Output: {vowels:0,consonants:0}
```
My answer:
```
function getCount(words) {
  let vowelConsonants = {
    'vowels': 0, 
    'consonants' : 0,
  }
  if(typeof words !== 'string') return vowelConsonants
  
  //97 - 122 = a-z in ASCII
  words.toLowerCase().split('').forEach(ch => {
    //check for aeiou
    'aeiou'.includes(ch) ? vowelConsonants['vowels']++ :
    //check for any letter
    ch.charCodeAt() >= 97 && ch.charCodeAt() <= 122 ?  vowelConsonants['consonants']++ : null;
  })
  
  return vowelConsonants;
}
```
Define object to hold variables, then a line to ensure we are only checking strings. Once we are sure that we are dealing with a string, it is then okay to convert everything to lowercase, split into an array and then iterate over with forEach(). The logic if/if else/else structure is leveraged here, first checking for a vowel. If a vowel is found then the second if statement is not reached, allowing us to check for any letter (a consonant). The object is incremented accordingly. 

Another ans:
```
function getCount(words) {
  let f = typeof words === 'string';
  return {
    vowels: f ? words.replace(/[^aeiou]/gi,'').length : 0,
    consonants: f ? words.replace(/[^bcdfghjklmnpqrstvwxyz]/gi,'').length : 0
  }
}
```
f is a string check. We return an object with vowels and consonants, using the f to choose to return either 0 or the proper number of letters. The structure ensures that we are only calling string methods on a string. 
words.replace(/[^aeiou]/gi,'') 
- replace(target, new) returns a new string with one, some, or all matches of a `pattern` replaced by a `replacement`
- `/[^aeiou]/` is a regular expression that matches any character that is **not** a lowercase or uppercase vowel (a, e, i, o, u).
- The `^` inside the square brackets means "negate" the character class, so it matches any character **except** vowels.
- The `gi` flags mean:
	- `g`: Global search (replace all occurrences).
	- `i`: Case-insensitive search.
- `.replace(..., '')` replaces all matched characters (non-vowels) with an empty string, effectively removing them.
Therefore, this replace() returns ONLY vowels. 

The same is repeated for consonants, and by returning the length we get the proper num of vowels/consonants.

# Genetic Algorithm Series - #1 Generate (7kyu)
A genetic algorithm is based in groups of chromosomes, called populations. To start our population of chromosomes we need to generate random binary strings with a specified length.

In this kata you have to implement a function `generate` that receives a `length` and has to return a random binary string with `length` characters.
## Example:

Generate a chromosome with length of 4 `generate(4)` could return the chromosome `0010`, `1110`, `1111`... or any of `2^4` possibilities.

_**Note:**_ _Some tests are random. If you think your algorithm is correct but the result fails, trying again should work._

My ans:
```
const generate = length => {
  let binaryStr = "";
  for(let i = 0; i < length; i++){
    binaryStr += Math.round(Math.random() * 1).toString();
  }
  return binaryStr;
};
```

Another set of solutions:
```
const generate = length => {
  return Array.from(Array(length) , x => Math.floor(Math.random() * 2)).join('');
};
```
This one uses an array.from() -- method that creates a new shallow array from an iterable/array-like object -- defining a new object of 

```
const generate = length =>
  [...Array(length)].map(val => Math.random() * 2 ^ 0).join(``);
```
Spreading the array turns otherwise empty slots into 'undefined', allowing map() to properly iterate over every element and fill them with the function expression. Generating the random 0/1 in this way also uses one less method call.

# Genetic Algorithm Series - #2 Mutation (7kyu)
Mutation is a genetic operator used to maintain genetic diversity from one generation of a population of genetic algorithm chromosomes to the next.

![Mutation](http://i.imgur.com/HngmxNN.gif)

A mutation here may happen on zero or more positions in a chromosome. It is going to check every position and by a given probability it will decide if a mutation will occur.

A mutation is the change from `0` to `1` or from `1` to `0`.

My answer:
```
const mutate = (chromosome, p) => {
  return chromosome.split('').map(n => {
    if(Math.random() <= p){
      return n === '0' ? '1' : '0';
    }
    return n;
  }).join('')
};
```

Another solution:
```
const mutate = (chromosome,p) => Array.from( chromosome, bit => Math.random()<p ? bit^1 : bit ).join("") ;
```
- **`Array.from(chromosome)`**: This takes the string `chromosome` and converts it into an array of characters (or bits, in this case). For example, if `chromosome = '10101'`, it will become `['1', '0', '1', '0', '1']`.
- **`bit => Math.random() < p ? bit ^ 1 : bit`**: This is a **mapping function** that will be applied to each `bit` in the array. The mapping function does the following:
    - **`Math.random() < p`**: This generates a random number between 0 and 1. If the random number is **less than `p`**, the bit has a chance to be mutated.
    - **`bit ^ 1`**: This operation is the **XOR** (exclusive OR) operation. The XOR of a bit and `1` will flip the bit:
        - `0 ^ 1 = 1` (flip `0` to `1`)
        - `1 ^ 1 = 0` (flip `1` to `0`)
    - **`bit`**: If the random number is **greater than or equal to `p`**, the bit is **not mutated** and remains unchanged.

# Error Throwing - Error Handling #2 (7kyu) 
Error Handling is very important in coding. Most error handling seems to be overlooked or not implemented properly.

## Task

In this kata you are provided to evaluate a string, you must check for any HTML code (i.e. if any HTML tags are found), if any code is found you must return false, If the input is not a string you must throw a `TypeError`, if the string is over 255 characters long or contains 0 characters you must throw a `RangeError` and last of all if the string entered is null throw a `ReferenceError`.

## Error Messages

ReferenceError

```javascript
new ReferenceError('Message is null!')
```

TypeError

```javascript
new TypeError(`Message should be of type string but was of type ${typeof msg}!`)
```

RangeError

```javascript
new RangeError(`Message contains ${msg.length} characters!`)
```

My answer:
```
function validateMessage(msg) {
  
  if(msg === null){
    throw new ReferenceError('Message is null!')
  }else if(typeof(msg) !== 'string'){
    throw new TypeError(`Message should be of type string but was of type ${typeof msg}!`)
  }else if(msg.includes('<') && msg.includes('>')){
    return false;
  }else if(msg.length > 255 || msg.length === 0){
    throw new RangeError(`Message contains ${msg.length} characters!`)
  }
  
  return true;
  
}
```


A soln involving regex:
```
const validateMessage = msg => {
  if (msg === null) throw ReferenceError('Message is null!');
  if (typeof msg != 'string') throw TypeError(`Message should be of type string but was of type ${typeof msg}!`);
  if (!msg.length || msg.length > 255) throw RangeError(`Message contains ${msg.length} characters!`);
  if (/<.*>/.test(msg)) return false;
  return true;
}
```

# Genetic Algorithm Series - #3 Crossover (7 kyu)
In genetic algorithms, crossover is a genetic operator used to vary the programming of chromosomes from one generation to the next.

The one-point crossover consists in swapping one's cromosome part with another in a specific given point. The image bellow shows the crossover being applied on chromosomes `1011011001111` and `1011100100110` with the cut point (index) `4`:

![](http://i.imgur.com/nZ4hgnS.gif)

In this kata you have to implement a function `crossover` that receives two chromosomes `chromosome1`, `chromosome2` and a zero-based `index` and it has to return an array with the crossover result on both chromosomes `[chromosome1, chromosome2]`.

## Example:

`crossover('111000', '000110', 3)` should return `['111110', 000000']`

My answer:
```
const crossover = (chromosome1, chromosome2, index) => {
  let strandOneFront = "", strandOneBack = "", strandTwoFront = "", strandTwoBack = "";
  chromosome1.split('').filter((n, idx) => idx < index ? strandOneFront+= n : strandOneBack+= n);
  chromosome2.split('').filter((n, idx) => idx < index ? strandTwoFront+= n : strandTwoBack+= n);
  
  return [strandOneFront.concat(strandTwoBack), strandTwoFront.concat(strandOneBack)];
};
```

A more efficient answer:
```
const crossover = (chromosome1, chromosome2, index) => {
  return [
    chromosome1.substring(0, index) + chromosome2.substring(index),
    chromosome2.substring(0, index) + chromosome1.substring(index)
  ]
};
```

substring(start, end) returns part of the string from the start (inclusive) to the end(exclusive). If no end is specified then it will return until the end of string.

# Genetic Algorithm Series - #4 Get population and fitnesses (7kyu)
In a genetic algorithm, a population is a collection of candidates that may evolve toward a better solution.

We determine how close a chromosome is to a ideal solution by calculating its fitness. You are given two parameters, the `population` containing all individuals and a function `fitness` that determines how close to the solution a chromosome is.

Your task is to return a collection containing an object with the chromosome and the calculated fitness.

```
[
  { chromosome: c, fitness: f },
  { chromosome: c, fitness: f },
  ...
]
```

Answer:
```
const mapPopulationFit = (population, fitness) => {
  return population.map(chromosome => ({ chromosome, fitness: fitness(chromosome) }))
}
```
Uses ES6 syntax shorthand. Instead of var test = 1; and {test: test}, you may instead just do {test}.

Another answer, but without the shorthand:
```
const mapPopulationFit = (population, fitness) =>
  population.map(chromosome => ({
    fitness: fitness(chromosome),
    chromosome,
  }))
```

```
const mapPopulationFit = (population, fitness) => population.map(chromosome => ({chromosome, fitness:fitness(chromosome)}))
```

# Pull your words together, man! (7kyu)
Your friend Robbie has successfully created an AI that is capable of communicating in English!

Robbie's almost done with the project, however the machine's output isn't working as expected. Here's a sample of a sentence that it outputs:

```
["this","is","a","sentence"]
```

Every time that it tries to say a sentence, instead of formatting it in normal English orthography, it just outputs a list of words.

Robbie has pulled multiple all-nighters to get this project finished, and he needs some beauty sleep. So, he wants you to write the last part of his code, a `sentencify` function, which takes the output that the machine gives, and formats it into proper English orthography.

Your function should:

1. Capitalize the first letter of the first word.
2. Add a period (`.`) to the end of the sentence.
3. Join the words into a complete string, with spaces.
4. Do _no other manipulation_ on the words.

My answer:
```
function sentencify(words) {
  let sentence = words.map((word, idx) =>{
    if(idx === 0){
      word = word[0].toUpperCase() + word.slice(1);
    }
    if (idx === words.length-1){
      word += '.'
    }
    return word;
  })
  return sentence.join(' ');
}

```

Better answer:
```
const sentencify = words =>
  `${words[0][0].toUpperCase()}${words.join(` `).slice(1)}.`;
```
The first letter (""words [0]  [0] ") of the first word ("words[0]")  is capitalized using toUpperCase(). Using the template string, we then combine it with the rest of the array using words.  We call upon the words array again, joining them into a single string so we may slice into it, return everything but the first character. -- join(' ').slice(1). If we do it the opposite way, it will instead join all elements but the first one, and thus the return string will be missing the end characters of the first element.  Finally a period is placed at the end of the template string. 
# Bouncing Balls (6kyu)
A child is playing with a ball on the nth floor of a tall building. The height of this floor above ground level, _h_, is known.

He drops the ball out of the window. The ball bounces (for example), to two-thirds of its height (a bounce of 0.66).

His mother looks out of a window 1.5 meters from the ground.

How many times will the mother see the ball pass in front of her window (including when it's falling _and_ bouncing)?

#### Three conditions must be met for a valid experiment:

- Float parameter "h" in meters must be greater than 0
- Float parameter "bounce" must be greater than 0 and less than 1
- Float parameter "window" must be less than h.

**If all three conditions above are fulfilled, return a positive integer, otherwise return -1.**

#### Note:

The ball can only be seen if the height of the rebounding ball is strictly _greater_ than the window parameter.

#### Examples:

```
- h = 3, bounce = 0.66, window = 1.5, result is 3

- h = 3, bounce = 1, window = 1.5, result is -1 

(Condition 2) not fulfilled).
```

My answer:
```
function bouncingBall(h,  bounce,  window) {
  if(h < 0 || bounce < 0 || bounce >= 1 || h <= window) return -1;
  
  let count = 0;
  while(h > window){
    count++; //falling down
    h *= bounce;
    if(h > window) count++; // bouncing up
  }
  return count;
  
} 
```

A recursive solution: 
```
const bouncingBall = (h, b, w) => (h <= 0 || b <= 0 || b >= 1 || w >= h) ? -1 : 2 + bouncingBall(h*b, b, w);
```

Another soln in O(log(n)) time:
```
function bouncingBall(h,  bounce,  window) {
  if (h <= 0 || bounce <= 0 || bounce >= 1 || window >= h) return -1

  let bounces = (Math.log(window/h) / Math.log(bounce))
  if (bounces - Math.floor(bounces) != 0) {
    bounces *= 2
  }
  
  bounces = Math.floor(bounces)
  if (bounces % 2 == 0) return bounces + 1
  
  return bounces
}
```

# Two to One (7 kyu)
Take 2 strings `s1` and `s2` including only letters from `a` to `z`. Return a new **sorted** string (alphabetical ascending), the longest possible, containing distinct letters - each taken only once - coming from s1 or s2.

#### Examples:

```
a = "xyaabbbccccdefww"
b = "xxxxyyyyabklmopq"
longest(a, b) -> "abcdefklmopqwxy"

a = "abcdefghijklmnopqrstuvwxyz"
longest(a, a) -> "abcdefghijklmnopqrstuvwxyz"
```

My answer: 
```
function longest(s1, s2) {
  return [...new Set(s1 + s2)].sort().join('');
}
```
[...] or spreading a set will do the same as Array.from()
# Sum without highest and lowest number (8kyu)
Sum all the numbers of a given array ( cq. list ), except the highest and the lowest element ( by value, not by index! ).

The highest or lowest element respectively is a single element at each edge, even if there are more than one with the same value.

Mind the input validation.

## Example

```
{ 6, 2, 1, 8, 10 } => 16
{ 1, 1, 11, 2, 3 } => 6
```

## Input validation

If an empty value ( `null`, `None`, `Nothing`, `nil` etc. ) is given instead of an array, or the given array is an empty list or a list with only `1` element, return `0`.

My answer:
```
function sumArray(array) {
 return array === null || array === undefined || array.length <= 2 ? 0 : 
      array.sort((a,b) => a - b).slice(1, array.length-1).reduce((sum, n) => sum + n, 0);
  
}
```

A solution with a better runtime:
```
function sumArray(array) {
  return Array.isArray(array) && array.length > 1
    ? array.reduce((s, n) => s + n, 0) - Math.min(...array) - Math.max(...array)
    : 0
}
```

# Calculating with Functions (5kyu)
This time we want to write calculations using functions and get the results. Let's have a look at some examples:

```javascript
seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3
```

Requirements:

- There must be a function for each number from 0 ("zero") to 9 ("nine")
- There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy
- Each calculation consist of exactly one operation and two numbers
- The most outer function represents the left operand, the most inner function represents the right operand
- Division should be **integer division**. For example, this should return `2`, not `2.666666...`:

```javascript
eight(dividedBy(three()));
```

Answer:
```
const zero = a => a ? a(0) : 0
const one = a => a ? a(1) : 1
const two = a => a ? a(2) : 2
const three = a => a ? a(3) : 3
const four = a => a ? a(4) : 4
const five = a => a ? a(5) : 5
const six = a => a ? a(6) : 6
const seven = a => a ? a(7) : 7
const eight = a => a ? a(8) : 8
const nine = a => a ? a(9) : 9

const plus = a => b => a + b
const minus = a => b => b - a
const dividedBy = a => b => Math.floor(b / a)
const times = a => b => a * b
```
The function checks if `a` is truthy using the conditional (ternary) operator: `a ? a(7) : 7`. If you pass a function as `a`, the expression `a(7)` is evaluated, which means the function `a` will be called with the argument `7`. In this case, `7` is the number passed into the function. If you do **not** provide an argument to `seven` (or you pass a falsy value like `null`, `undefined`, `false`, etc.), the expression `a ? a(7) : 7` will evaluate to `7` (the default value).

`const plus = a => b => a + b` defines a **curried function** in JavaScript. `a => b => a + b` is an **arrow function** with two parts:

- The outer function takes an argument `a` (the first operand).
- The inner function takes an argument `b` (the second operand).
- The result of the inner function is `a + b`, which is the sum of `a` and `b`.

The `plus` function is a **curried** function, which means it returns another function. The curried pattern allows you to call the function in multiple stages:

1. **First, you call `plus` with a value for `a`**.
2. **Then, the returned function takes a second argument `b`**, and when you call that function, it returns the result of `a + b`.
```
seven(times(five())); // must return 35
```


 Using a generator to get rid of all the duplicate functions. (And with readable variable names):
 ```
const zero = a => a ? a(0) : 0
const one = a => a ? a(1) : 1
const two = a => a ? a(2) : 2
const three = a => a ? a(3) : 3
const four = a => a ? a(4) : 4
const five = a => a ? a(5) : 5
const six = a => a ? a(6) : 6
const seven = a => a ? a(7) : 7
const eight = a => a ? a(8) : 8
const nine = a => a ? a(9) : 9

const plus = a => b => a + b
const minus = a => b => b - a
const dividedBy = a => b => Math.floor(b / a)
const times = a => b => a * b
```

A concise answer:
```
const [zero, one, two, three, four, five, six, seven, eight, nine] = [...Array(10)].map((_, idx) => fn => fn ? fn(idx) : idx);

const [plus, minus, times, dividedBy] = [`+`, `-`, `*`, `/`].map(val => new Function(`b`, `return a => a ${val} b ^ 0`));
```

The first part creates an array of 10 elements, where each element represents a digit (0 through 9). Here's how it works:

1. `Array(10)` creates an empty array of length 10, which looks like `[ <10 empty items> ]`.
2. `[...Array(10)]` spreads this array into a new array, making it a fully instantiated array of length 10, but the values inside are still `undefined` (like `[undefined, undefined, ..., undefined]`).
3. `.map((_, idx) => fn => fn ? fn(idx) : idx)` transforms this array into an array of functions. Each element in this array is now a function that takes another function `fn` as an argument:
    - If `fn` is provided, the function calls `fn(idx)`, where `idx` is the current index of the digit (0 for `zero`, 1 for `one`, etc.).
    - If `fn` is not provided, it simply returns `idx` itself (the digit).

So, when you access an element like `zero`, it’s actually a function that will return `0` if you call it without any arguments, or you can pass a function to it, and it will apply that function to `0`.

For example:```
zero()  // Returns 0
zero(x => x + 5)  // Returns 5 (because 0 + 5 = 5)```

# Build Tower (6kyu)
Build a pyramid-shaped tower, as an array/list of strings, given a positive integer `number of floors`. A tower block is represented with `"*"` character.

For example, a tower with `3` floors looks like this:

```
[
  "  *  ",
  " *** ", 
  "*****"
]
```

And a tower with `6` floors looks like this:

```
[
  "     *     ", // 5 space, 1 star, 5 space
  "    ***    ", // 4 space, 3 star, 4 space
  "   *****   ", // 3 space, 5 star, 3 space
  "  *******  ", // 2 space, 7 star, 2 space
  " ********* ", // 1 space, 9 star, 1 space
  "***********"  // 0 space, 11 star, 0 space
]
```

My answer:
```
function towerBuilder(nFloors) {
  let totalStars = 2 * (nFloors - 1) + 1
  return new Array(nFloors).fill("").map((element, idx) => {
    let currentStars = 2 * idx + 1;
    let currentSpace = (totalStars - currentStars) / 2
    
    return " ".repeat(currentSpace)+"*".repeat(currentStars)+" ".repeat(currentSpace);
  });
}
```
Refactored answer:
```
function towerBuilder(nFloors) {
  return new Array(nFloors)
    .fill("")
    .map((element, idx) => 
         " ".repeat(nFloors - idx - 1)+"*".repeat((idx * 2) + 1)+" ".repeat(nFloors - idx - 1));
}
```

An answer without function calls:
```
function towerBuilder(nFloors) {
  let tower = [];
  for (let i = 0; i < nFloors; i++) {
    tower.push(" ".repeat(nFloors - i - 1)
             + "*".repeat((i * 2)+ 1)
             + " ".repeat(nFloors - i - 1));
  }
  return tower;
}
```

A concise answer:
```
const towerBuilder = nFloors =>
  [...Array(nFloors)]
  .map((_, idx) => `${`*`.repeat(2 * idx + 1)}`
  .padStart(nFloors + idx, ` `)
  .padEnd(2 * nFloors - 1, ` `));
```

# I need more speed! (6kyu)
Write a function that will take in any `array` and reverse it.  

Sounds simple doesn't it?  

**NOTES:**

- Array should be reversed in place! (no need to return it)
- Usual builtins have been deactivated. Don't count on them.
- You'll have to do it fast enough, so think about performances

My answer:
```
function reverse(arr) {
  let temp, length = arr.length;
  for(let i = 0; i < length/2; i++){
    temp = arr[i];
    arr[i] = arr[length - 1 - i];
    arr[length - 1 - i] = temp;
   }
}
```
Picture a mirror set on the middle element, we swap values in the array based on that midpoint. Iterate over half of the array, using a temp variable to store the current value. Then set the current element to the corresponding array value on the other side of the array and then set that element to temp. 

Another answer:
```
const reverse = (arr, l = arr.length - 1) => {
  for (let i = 0; i < l; i++, l--) {
    const tmp = arr[i];
    arr[i] = arr[l];
    arr[l] = tmp;
  }
  return arr;
};
```

# Fake Binary (8 kyu)
Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'. Return the resulting string.

**Note: input will never be an empty string**

My answer:
```
function fakeBin(x){
  return x.replaceAll(/[1234]/g, '0')
          .replaceAll(/[56789]/g, '1');
}
```
Using regex, we specify using a character class [] inside the expression call to replace the values of 1, 2, 3, and 4 with 0 and also 5, 6, 7, 8, 9 with 1. The g specifies it to be a global replacement. This is perhaps not the most efficient code.

Alternate answer that's a bit more concise:
```
function fakeBin(x){
  return x.replace( /[0-4]/g, "0" ).replace( /[5-9]/g, "1" )
}
```
Instead of writing out all the numbers, we use a range to specify.

An answer using regex and logic:
```
function fakeBin(x) {
  return x.replace(/\d/g, d => d < 5 ? 0 : 1);
}
```
/\d/g matches all digit characters (0-9), syntactic sugar same as `/[0-9]/g`. In JavaScript, `String.prototype.replace()` allows a **replacement string** or a **replacement function** as the second argument:

- If you provide a string, it will be used directly as the replacement.
- If you provide a function, that function is invoked for each match, and the return value of the function will be used as the replacement.

Another answer using arrays:
```
function fakeBin(x) {
    return x.split('').map(n => n < 5 ? 0 : 1).join('');
}
```
Split the string into an array of each character and then create a new one, replacing each character with a 1 or 0 based on the element being less than 5. 

# Grasshopper - Check for factor (8kyu)
This function should test if the `factor` is a factor of `base`.

Return `true` if it is a factor or `false` if it is not.

## About factors

Factors are numbers you can multiply together to get another number.

2 and 3 are factors of 6 because: `2 * 3 = 6`

- You can find a factor by dividing numbers. If the remainder is 0 then the number is a factor.
- You can use the mod operator (`%`) in most languages to check for a remainder

For example 2 is not a factor of 7 because: `7 % 2 = 1`

Note: `base` is a non-negative number, `factor` is a positive number.

My answer:
```
function checkForFactor (base, factor) {
  return base % factor === 0
}
```

Another ans:
```
const checkForFactor = (base, factor) => !(base % factor);
```

# Mumbling (7kyu)
#### Examples:

```
accum("abcd") -> "A-Bb-Ccc-Dddd"
accum("RqaEzty") -> "R-Qq-Aaa-Eeee-Zzzzz-Tttttt-Yyyyyyy"
accum("cwAt") -> "C-Ww-Aaa-Tttt"
```

The parameter of accum is a string which includes only letters from `a..z` and `A..Z`.

My answer:
<<<<<<< HEAD
```
function accum(s) {
	return s.toLowerCase().split('').map((ch,idx) => ch.toUpperCase()+ch.repeat(idx)).join('-');
}
```

=======
# Get the Middle Character (7kyu)
You are going to be given a **non-empty** string. Your job is to return the middle character(s) of the string.

- If the string's length is odd, return the middle character.
- If the string's length is even, return the middle 2 characters.

### Examples:

```javascript
"test" --> "es"
"testing" --> "t"
"middle" --> "dd"
"A" --> "A"
```

My answer:
```
function getMiddle(s) {
  return s.length % 2 === 0 ? s[s.length/2 - 1] + s[s.length/2] :  s[Math.floor(s.length/2)];
}
```

A more elegant answer:
```
function getMiddle(s){
  return s.slice((s.length-1)/2, s.length/2+1);
}
```

# Duplicate Encoder (6kyu)
The goal of this exercise is to convert a string to a new string where each character in the new string is `"("` if that character appears only once in the original string, or `")"` if that character appears more than once in the original string. Ignore capitalization when determining if a character is a duplicate.

### Examples

```
"din"      =>  "((("
"recede"   =>  "()()()"
"Success"  =>  ")())())"
"(( @"     =>  "))((" 
```

### Notes

Assertion messages may be unclear about what they display in some languages. If you read `"...It Should encode XXX"`, the `"XXX"` is the expected result, not the input!

My answer:
```
function duplicateEncode(word){
    let dictionary = {}
    //fill dictionary in or increment
     word.toLowerCase().split('').forEach(ch => 
		dictionary[ch] = (dictionary[ch]+1) || 1);
  
    return word
      .toLowerCase()
      .split('')
      .map(ch => dictionary[ch] === 1 ? "(" : ")")
      .join('');
}
```

Big O notation of O(2n). Loops over the string once to populate the dictionary with 1 or increment value. Loops again to build the string for return, checking the dictionary and returning "(" if the value is 1 or ")" if the value is greater.

Another answer:
```
function countCharacters(chars) {
  return chars
    .reduce( function(memo, char){
      memo[char] = memo[char] ? memo[char] + 1 : 1;
      return memo;
    }, {});
}

function duplicateEncode(word){
  const chars = word.toLowerCase().split('');
  const charsCount = countCharacters(chars);
  return chars
    .map( ch => charsCount[ch] > 1 ? ')' : '(' )
    .join('');
}
```
Not necessarily better but uses a function to create the dictionary, similar in logic to mine.

# You can't code under pressure #2
You need to make a constructor function with two methods (and only these two methods) to return and increment a counter, but the counter should not be directly accessible from outside the function.

Answer:
```
function Counter() {
  let _count = 0;

  this.check = function() {
    return _count;
  }
  this.increment = function() {
    _count++;
  }
};
```
# Welcome! (8 kyu)
### The Task

- Think of a way to store the languages as a database. The languages are listed below so you can copy and paste!
- Write a 'welcome' function that takes a parameter 'language', with a type `String`, and returns a greeting - if you have it in your database. It should default to English if the language is not in the database, or in the event of an invalid input.

### The Database

Please modify this as appropriate for your language.

```haskell
[ ("english", "Welcome")
, ("czech", "Vitejte")
, ("danish", "Velkomst")
, ("dutch", "Welkom")
, ("estonian", "Tere tulemast")
, ("finnish", "Tervetuloa")
, ("flemish", "Welgekomen")
, ("french", "Bienvenue")
, ("german", "Willkommen")
, ("irish", "Failte")
, ("italian", "Benvenuto")
, ("latvian", "Gaidits")
, ("lithuanian", "Laukiamas")
, ("polish", "Witamy")
, ("spanish", "Bienvenido")
, ("swedish", "Valkommen")
, ("welsh", "Croeso")
]
```

Possible invalid inputs include:

```
IP_ADDRESS_INVALID - not a valid ipv4 or ipv6 ip address
IP_ADDRESS_NOT_FOUND - ip address not in the database
IP_ADDRESS_REQUIRED - no ip address was supplied
```

My answer:
```
function greet(language) {
  const database = {
"english": 'Welcome',
"czech": 'Vitejte',
"danish": 'Velkomst',
"dutch": 'Welkom',
"estonian": 'Tere tulemast',
"finnish": 'Tervetuloa',
"flemish": 'Welgekomen',
"french": 'Bienvenue',
"german": 'Willkommen',
"irish": 'Failte',
"italian": 'Benvenuto',
"latvian": 'Gaidits',
"lithuanian": 'Laukiamas',
"polish": 'Witamy',
"spanish": 'Bienvenido',
"swedish": 'Valkommen',
"welsh": 'Croeso'
    }
  return database[language] ? database[language] : database["english"]
}
```

Another ans:
```
function greet(language) {
	var GreetingsDB = {
    english: 'Welcome',
    czech: 'Vitejte',
    danish: 'Velkomst',
    dutch: 'Welkom',
    estonian: 'Tere tulemast',
    finnish: 'Tervetuloa',
    flemish: 'Welgekomen',
    french: 'Bienvenue',
    german: 'Willkommen',
    irish: 'Failte',
    italian: 'Benvenuto',
    latvian: 'Gaidits',
    lithuanian: 'Laukiamas',
    polish: 'Witamy',
    spanish: 'Bienvenido',
    swedish: 'Valkommen',
    welsh: 'Croeso'
  }, 
  defaultLanguage = 'english';
  return GreetingsDB[language] || GreetingsDB[defaultLanguage];
}
```

# Genetic Algorithm Series - #5 Roulette wheel selection (6kyu)
The "Roulette wheel selection", also known as "Fitness proportionate selection", is a genetic operator used in genetic algorithms for selecting potentially useful solutions for recombination.

Your task is to implement it.

![roulette](http://i.imgur.com/K5VSzVT.png)

You throw a coin in and has a chance to fall in one of the slots, the higher the fitness the higher the chance the element has to be selected.

Given the `population` and `fitnesses`, your task is to run the roulette to return one element.

_**Note:**_ _Some tests are random. If you think your algorithm is correct but the result fails, trying again should work.

My answer:
```
const select = (population, fitnesses) => {
  let totalSlots = 1/Math.min(...fitnesses), fitnessWheel = "";
  
  population.filter((gene, idx)=> fitnessWheel += gene
                    .toString()
                    .repeat(fitnesses[idx] * totalSlots)
  );
  return fitnessWheel[Math.floor(Math.random() * fitnessWheel.length)]
};
```
It doesn't work on strings that are too large for the JavaScript engine to handle. Thus another answer is required.

My solution using Cumulative Probability:
```
const select = (population, fitnesses) => {
  let pick = Math.random(), cumulativeProbability = 0;
  
  for(let i = 0; i < population.length; i++){
    cumulativeProbability += fitnesses[i];
    if(pick <= cumulativeProbability){
      return population[i];
    }
  }
  
};
```

Another soln using weighted random selection
```
const select = (population, fitnesses) => {
    const wheel = fitnesses.reduce((a,b) => a + b);
    let spin = Math.random() * wheel;
    return population.find((e,i) => (spin-= fitnesses[i]) <= 0);
};
```
First two lines reduce add up the probability generates a random value within the bounds of the total fitness. Then .find() is called on the population array, subtracting the corresponding fitness from the spin until the value is less than zero. 
- The idea is that the larger the fitness value of an individual, the later the `spin` value will reach zero, giving the individual a higher chance of being selected.
- For example, if `fitnesses = [10, 20, 30]` and `spin = 45`:
    - For the first individual (fitness 10), `spin -= 10` gives `spin = 35`.
    - For the second individual (fitness 20), `spin -= 20` gives `spin = 15`.
    - For the third individual (fitness 30), `spin -= 30` gives `spin = -15`, which is less than 0, so this individual is selected.

# List Filtering (7kyu)
In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

### Example

```python
filter_list([1,2,'a','b']) == [1,2]
filter_list([1,'a','b',0,15]) == [1,0,15]
filter_list([1,2,'aasf','1','123',123]) == [1,2,123]
```

My answer:
```
function filter_list(l) {
  let arr = []
  for(let i = 0;i < l.length;i++){
    if(Number.isInteger(l[i])){
      arr.push(l[i])
    }
  }
  return arr
}
```

Better answer:
```
function filter_list(l) {
  return l.filter(e => Number.isInteger(e));
}
```
Another answer:
```
function filter_list(l) {
 return l.filter(v => typeof v == "number")
}
```

# Rocks Paper Scissors (8kyu)
Let's play! You have to return which player won! In case of a draw return `Draw!`.

**Examples(Input1, Input2 --> Output):**

```
"scissors", "paper" --> "Player 1 won!"
"scissors", "rock" --> "Player 2 won!"
"paper", "paper" --> "Draw!"
```

My answer:
```
const rps = (p1, p2) => {
  let chart = {
    'rock': 'scissors',
    'scissors': 'paper',
    'paper': 'rock'
  }
  
  return p1 === p2 ? "Draw!" : "Player " + (chart[p1] === p2 ? 1 : 2) + " won!"
  
};
```
Another answer:
```
const rps = (p1, p2) =>
  p1 === p2 ? `Draw!` : `Player ${/ps|rp|sr/.test(p1[0] + p2[0]) + 1} won!`;
```

# Product of consecutive Fib numbers (5kyu)
The Fibonacci numbers are the numbers in the following integer sequence (`Fn`): `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, ...`

such that:

F(0)=1F(1)=1F(n)=F(n−1)+F(n−2)F(0) = 1\\F(1) = 1\\F(n) = F(n-1) + F(n-2)F(0)=1F(1)=1F(n)=F(n−1)+F(n−2)

Given a number, say `prod` (for product), we search two Fibonacci numbers `F(n)` and `F(n+1)` verifying:

F(n)∗F(n+1)=prodF(n) * F(n+1) = prodF(n)∗F(n+1)=prod

---

Your function takes an integer (`prod`) and returns an array/tuple (check the function signature/sample tests for the return type in your language):

- if `F(n) * F(n+1) = prod`:
    
    ```
    (F(n), F(n+1), true)
    ```
    
- If you do not find two consecutive `F(n)` verifying `F(n) * F(n+1) = prod`:
    
    ```
    (F(n), F(n+1), false)
    ```
    
    where `F(n)` is the smallest one such as `F(n) * F(n+1) > prod`.

#### Examples:

```javascript
714 ---> (21, 34, true)
--> since F(8) = 21, F(9) = 34 and 714 = 21 * 34

800 --->  (34, 55, false)
--> since F(8) = 21, F(9) = 34, F(10) = 55 and 21 * 34 < 800 < 34 * 55
```
My answer:
```
function productFib(prod){
  let arr = [1, 1, false], nextSum = arr[0] + arr[1], fiboProd = arr[0] * arr[1];
  
  while(fiboProd <= prod){
    if(prod === fiboProd){
      arr[2] = true;
      return arr;
    }else{
      arr[0] = arr[1];
      arr[1] = nextSum;
      nextSum = arr[0] + arr[1];
      fiboProd = arr[0] * arr[1];
    }
  }
  
  
  return arr
}
```
Variables to hold the array, the sum and product of the two numbers. While the fibonacci product is smaller or equal to that of the product given two steps occur. First a check is made to see if the product equals the fibonacci product. If so, declare the false to be true in the array and return the array. ELSE we move the value in the 2nd element to the 1st, the sum of the two elements into the 2nd element slot and re-multiply the value of the two array elements. If we get to a point where the fibonacci product is greater than the product given then we can return the array knowing that it's false

A more concise answer:
```
function productFib(prod){
  let [a, b] = [0, 1];
  while(a * b < prod) [a, b] = [b, a + b];
  return [a, b, a * b === prod];
}
```
Similar to my code but far more concise. An array is used but only uses two elements. A while statement is used but very succinctly defines the code, using a very simple [a, b] = [b, a + b] if the fibonacci product is smaller than the given product. There's a lack of equals comparison, for that part is done in the return statement implicitly. If two numbers equal each other than one is NOT less than the other. The last part of the array - True/False is found via comparison a * b === prod.

# Count characters in your string (6kyu)
The main idea is to count all the occurring characters in a string. If you have a string like `aba`, then the result should be `{'a': 2, 'b': 1}`.

What if the string is empty? Then the result should be empty object literal, `{}`.

My answer:
```
function count(string) {
  let chars = {}
  for(let i = 0; i < string.length; i++){
    chars.hasOwnProperty(string[i]) ? chars[string[i]]++ : chars[string[i]] = 1;
  }
```
x.hasOwnProperty(y) is the proper way to check if a key exists inside an object. 

Answer using split() and forEach():
```
function count (string) {  
  var count = {};
  string.split('').forEach(function(s) {
     count[s] ? count[s]++ : count[s] = 1;
  });
  return count;
}
```

Another answer using reduce()
```
function count (string) {
  return string.split('').reduce(function(counts,char){
    counts[char] = (counts[char]||0) + 1;
    return counts;
  },{});
}
```

Another answer:
```
const count = string =>
  [...string].reduce((pre, val) => (pre[val] = -~pre[val], pre), {});
```
"Finally, it is worth noting that, although the spread operator is just three little dots in your code, it can represent a substantial amount of work to the JavaScript interpreter. If an object has n properties, the process of spreading those properties into another object is likely to be an O(n) operation. This means that if you find yourself using ... within a loop or recursive function as a way to accumulate data into one large object, you may be writing an inefficient O(n2) algorithm that will not scale well as n gets larger." - David Flanagan, JavaScript: The Definitive Guide, Seventh Edition

# Testing 1-2-3(7kyu)
Your team is writing a fancy new text editor and you've been tasked with implementing the line numbering.

Write a function which takes a list of strings and returns each line prepended by the correct number.

The numbering starts at 1. The format is `n: string`. Notice the colon and space in between.

**Examples: (Input --> Output)**

```
[] --> []
["a", "b", "c"] --> ["1: a", "2: b", "3: c"]
```

My answer:
```
var number=function(array){
  return array.map((n, idx) => `${idx+1}: ${n}`)
}
```

# Convert number to reversed array of digits (8kyu)
Given a random non-negative number, you have to return the digits of this number within an array in reverse order.

## Example(Input => Output):

```
35231 => [1,3,2,5,3]
0 => [0]
```
My answer:
```
function digitize(n) {
  return n.toString().split('').map(n => Number(n)).reverse()
}
```

Another answer:
```
const digitize = num =>
  [...`${num}`].reverse().map(Number);
```

# The highest profit wins! (7kyu)
### Task

Write a function that returns both the minimum and maximum number of the given list/array.

### Examples (Input --> Output)

```
[1,2,3,4,5] --> [1,5]
[2334454,5] --> [5,2334454]
[1]         --> [1,1]
```

### Remarks

All arrays or lists will always have at least one element, so you don't need to check the length. Also, your function will always get an array or a list, you don't have to check for `null`, `undefined` or similar.

My answer:
```
function minMax(arr){
  return [Math.min(...arr), Math.max(...arr)];
}
```

# Growth of a Population (7kyu)
In a small town the population is `p0 = 1000` at the beginning of a year. The population regularly increases by `2 percent` per year and moreover `50` new inhabitants per year come to live in the town. How many years does the town need to see its population greater than or equal to `p = 1200` inhabitants?

```
At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (** number of inhabitants is an integer **)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years.
```

More generally given parameters:

`p0, percent, aug (inhabitants coming or leaving each year), p (population to equal or surpass)`

the function `nb_year` should return `n` number of entire years needed to get a population greater or equal to `p`.

aug is an integer, percent a positive or null floating number, p0 and p are positive integers (> 0)

```
Examples:
nb_year(1500, 5, 100, 5000) -> 15
nb_year(1500000, 2.5, 10000, 2000000) -> 10
```

#### Note:

- Don't forget to convert the percent parameter as a percentage in the body of your function: if the parameter percent is 2 you have to convert it to 0.02.
    
- There are no fractions of people. At the end of each year, the population count is an integer: `252.8` people round down to `252` persons.

My answer:
```
function nbYear(p0, percent, aug, p) {
    let years = 0;
    while(p0 < p){
      p0 = Math.floor(p0 + (p0*percent/100) + aug);
      years++;
    }
  return years
}
```
Another answer using for loop:
```
function nbYear(p0, percent, aug, p) {
  for (var years = 0; p0 < p; years++) {
    p0 = Math.floor(p0 + p0 * percent / 100 + aug);
  }
  return years
}
```
Recursive answer:
```
function nbYear(p0, percent, aug, p, years = 0) {
  if (p0 < p) {
    return nbYear(p0 + Math.floor(p0 * percent / 100) + aug, percent, aug, p, ++years);
  }
  return years;
}
```

# Is the string uppercase? (8kyu)
## Task

Create a method to see whether the string is ALL CAPS.

### Examples (input -> output)

```
"c" -> False
"C" -> True
"hello I AM DONALD" -> False
"HELLO I AM DONALD" -> True
"ACSKLDFJSgSKLDFJSKLDFJ" -> False
"ACSKLDFJSGSKLDFJSKLDFJ" -> True
```

In this Kata, a string is said to be in ALL CAPS whenever it does not contain any lowercase letter so any string containing no letters at all is trivially considered to be in ALL CAPS.

My answer:
```
String.prototype.isUpperCase = function() {
  return String(this) === this.toUpperCase();
}
```

Alternate ans:
```
String.prototype.isUpperCase = function() {
  return this.toUpperCase() === this;
}
```

More efficient for large strings:
```
String.prototype.isUpperCase = function() {
  for (let ch of this) {
    if (ch !== ch.toUpperCase()) {
      return false;
    }
  }
  return true;
}
```

# Delete occurrences of an element if it occurs more than n times (6kyu)
## Enough is enough!

Alice and Bob were on a holiday. Both of them took many pictures of the places they've been, and now they want to show Charlie their entire collection. However, Charlie doesn't like these sessions, since the motif usually repeats. He isn't fond of seeing the Eiffel tower 40 times.  
He tells them that he will only sit for the session if they show the same motif at most `N` times. Luckily, Alice and Bob are able to encode the motif as a number. Can you help them to remove numbers such that their list contains each number only up to `N` times, without changing the order?

## Task

Given a list and a number, create a new list that contains each number of `list` at most `N` times, without reordering.  
For example if the input number is `2`, and the input list is `[1,2,3,1,2,1,2,3]`, you take `[1,2,3,1,2]`, drop the next `[1,2]` since this would lead to `1` and `2` being in the result `3` times, and then take `3`, which leads to `[1,2,3,1,2,3]`.  
With list `[20,37,20,21]` and number `1`, the result would be `[20,37,21]`.

My answer:
```
function deleteNth(arr,n){
  let obj = {};
  return arr.filter(num => {
    obj[num] = (obj[num] || 0) + 1;
    return obj[num] <= n;
  })
}
```
The line obj[num] = (obj[num] || 0) + 1; initializes the property of num to 0 if it hasn't been seen before, otherwise it increments it by one. Then the value is checked against n, returning it as long as it's less than or equal to n. It's a clever way to make use of arr.filter()'s true/false keep the value/discard the value decision making. 

Another answer:
```
function deleteNth(arr,x){
  var obj = {}
  return arr.filter(function(number){
    obj[number] = obj[number] ? obj[number] + 1 : 1
    return obj[number] <= x
  })
}
```

# Money, Money, Money (7kyu)
Mr. Scrooge has a sum of money 'P' that he wants to invest. Before he does, he wants to know how many years 'Y' this sum 'P' has to be kept in the bank in order for it to amount to a desired sum of money 'D'.

The sum is kept for 'Y' years in the bank where interest 'I' is paid yearly. After paying taxes 'T' for the year the new sum is re-invested.

Note to Tax: not the invested principal is taxed, but only the year's accrued interest

Example:

```
  Let P be the Principal = 1000.00      
  Let I be the Interest Rate = 0.05      
  Let T be the Tax Rate = 0.18      
  Let D be the Desired Sum = 1100.00


After 1st Year -->
  P = 1041.00
After 2nd Year -->
  P = 1083.86
After 3rd Year -->
  P = 1128.30
```

Thus Mr. Scrooge has to wait for 3 years for the initial principal to amount to the desired sum.

Your task is to complete the method provided and return the number of years 'Y' as a whole in order for Mr. Scrooge to get the desired sum.

Assumption: Assume that Desired Principal 'D' is always greater than the initial principal. However it is best to take into consideration that if Desired Principal 'D' is equal to Principal 'P' this should return 0 Years.

My Answer:
```
function calculateYears(principal, interest, tax, desired) {
  let years = 0;
    while(principal < desired){
      principal += principal * interest * (1-tax)
      years++;
    }
  return years
}
```

Another answer:
```
function calculateYears(principal, interest, tax, desired) {
  return Math.ceil(
    Math.log(desired / principal) / 
    Math.log(1 + interest * (1 - tax))
  );
}
```

# L1: Set Alarm (8kyu)
The function should return true if you are employed and not on vacation (because these are the circumstances under which you need to set an alarm). It should return false otherwise. Examples:

```
employed | vacation 
true     | true     => false
true     | false    => true
false    | true     => false
false    | false    => false
```
My answer:
```
function setAlarm(employed, vacation){
  return vacation===true && employed===true ? false : employed;
}
```

A better answer:
```
function setAlarm(employed, vacation){
  return employed && !vacation;
}
```

A funny solution that isn't recommended:
```
function setAlarm(employed, vacation){
  return employed > vacation
}
```

# Replace With Alphabet Position (6kyu)
In this kata you are required to, given a string, replace every letter with its position in the alphabet.

If anything in the text isn't a letter, ignore it and don't return it.

`"a" = 1`, `"b" = 2`, etc.

## Example

```
Input = "The sunset sets at twelve o' clock."
Output = "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"
```

My answer:
```
function alphabetPosition(text) {
  return text.toLowerCase().split('')
    .reduce((arr, ch) => {
      if(ch.charCodeAt(0) >= 97 && ch.charCodeAt(0) <= 122){
        arr.push(ch.charCodeAt(0) - 96)
      }
      return arr
    }, [])
    .join(' ');
}
```

Answer using regex:
```
function alphabetPosition(text) {
  const matches = text.toLowerCase().match(/[a-z]/g);
  return matches ? matches.map(ch => ch.charCodeAt(0) - 96).join(' ') : "";
}
```
Answer filters for cases in which match returns null. The `match()` method returns `null` if no matches are found in the input string. When `null` is returned, calling `.map()` on it results in a `TypeError`. Therefore by using the ternary operator, we can check if matches is null and return an empty string if so. Else we can safely call .map() on it.

# Count the Digit
Take an integer `n (n >= 0)` and a digit `d (0 <= d <= 9)` as an integer.

Square all numbers `k (0 <= k <= n)` between 0 and n.

Count the numbers of digits `d` used in the writing of all the `k**2`.

Implement the function taking `n` and `d` as parameters and returning this count.

#### Examples:

```
n = 10, d = 1 
the k*k are 0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100
We are using the digit 1 in: 1, 16, 81, 100. The total count is then 4.

The function, when given n = 25 and d = 1 as argument, should return 11 since
the k*k that contain the digit 1 are:
1, 16, 81, 100, 121, 144, 169, 196, 361, 441.
So there are 11 digits 1 for the squares of numbers between 0 and 25.
```

Note that `121` has twice the digit 1.

My answer:
```
function nbDig(n, d) {
  const arr = Array(n+1).fill(0);
  d = d.toString();
  return arr.reduce((sum, _, idx) =>{
    let power = (idx**2).toString();
    for(let i = 0; i < power.length; i++){
      power[i] === d ? sum++ : null
    }
    return sum;
  }, 0);
}
```
Define a new array with size n+1 to iterate over (the range is 0 to n inclusive). We fill so reduce doesn't skip over elements but don't care too much about what value is inside of them. The variable 'd' is casted into a string before we use it for comparison. We use arr.reduce, using the current index to find the power of the current number and then loop over the string version of it. When we find matches to d we increment the sum and then we return the sum after every iteration. 

A more efficient answer without methods:
```
function nbDig(n, d) {
  let count = 0;
  const digitStr = d.toString(); // Convert the digit `d` to a string for comparison

  for (let k = 0; k <= n; k++) {
    const square = (k * k).toString(); // Square the number and convert to string
    for (let i = 0; i < square.length; i++) {
      if (square[i] === digitStr) {
        count++; // Increment count for each occurrence of `d`
      }
    }
  }

  return count;
}
```
An answer with methods:
```
function nbDig(n, d) {
  let count = 0;
  const digitStr = d.toString();

  for (let k = 0; k <= n; k++) {
    const square = (k * k).toString();
    count += square.split(digitStr).length - 1; // Count occurrences of `d`
  }

  return count;
}
```
The length of this array minus 1 (`square.split(digitStr).length - 1`) gives the number of occurrences of `d`.
One liner answer:
```
const nbDig = (n, d) =>
  [...Array(++n)].map((_, idx) => idx ** 2).join(``).split(d).length - 1;
```
`Array(++n)` creates an array of length `n + 1` (since `n` was incremented). The spread operator (`...`) converts the sparse array created by `Array(++n)` into a dense array. This ensures that `map()` can iterate over all elements. The map() method iterates over every element in the array, calculating the square. Once done all the elements are joined into a string which is split based upon d and then the length of it is found by subtracting one. For example 0149, d = 1 => [0, 49]. Length === 2. Subtract 1 and we get the occurances of 1 which is 1. Or 121 and d=1 => ["". "2". "']. Length is 3, 3-1 = 2 which is how many times we see the number 1.

# Consecutive strings (6kyu)
You are given an array(list) `strarr` of strings and an integer `k`. Your task is to return the **first** longest string consisting of k **consecutive** strings taken in the array.

#### Examples:

```
strarr = ["tree", "foling", "trashy", "blue", "abcdef", "uvwxyz"], k = 2

Concatenate the consecutive strings of strarr by 2, we get:

treefoling   (length 10)  concatenation of strarr[0] and strarr[1]
folingtrashy ("      12)  concatenation of strarr[1] and strarr[2]
trashyblue   ("      10)  concatenation of strarr[2] and strarr[3]
blueabcdef   ("      10)  concatenation of strarr[3] and strarr[4]
abcdefuvwxyz ("      12)  concatenation of strarr[4] and strarr[5]

Two strings are the longest: "folingtrashy" and "abcdefuvwxyz".
The first that came is "folingtrashy" so 
longest_consec(strarr, 2) should return "folingtrashy".

In the same way:
longest_consec(["zone", "abigail", "theta", "form", "libe", "zas", "theta", "abigail"], 2) --> "abigailtheta"
```

n being the length of the string array, if `n = 0` or `k > n` or `k <= 0` return "" (return `Nothing` in Elm, "nothing" in Erlang).

#### Note

consecutive strings : follow one after another without an interruption

My answer:
```function longestConsec(strArr, k) {
  let longest= "";
  
  for(let i = 0; i <= strArr.length-k; i++){
    let temp = "";
    for(let j = i; j < i + k; j++){
      temp += strArr[j]
    }
    if(temp.length > longest.length){
      longest = temp
    }
  }

  return longest;
}
```

A more efficient answer:
```function longestConsec(strarr, k) {
  const n = strarr.length;

  // Handle edge cases
  if (n === 0 || k > n || k <= 0) {
    return "";
  }

  let longest = "";

  // Iterate through the array
  for (let i = 0; i <= n - k; i++) {
    // Concatenate k consecutive strings
    const current = strarr.slice(i, i + k).join("");

    // Update longest if the current concatenation is longer
    if (current.length > longest.length) {
      longest = current;
    }
  }

  return longest;
}
```
Differences from my code: adds edge cases where the array is empty, k is greater than the number of elements in the array or k is negative. There's iteration through the array but the slice() method is used to concat subsections i through i+k. In the same for loop, the length of the subslice is compared against the current longest string. This logic implicitly redefines the current/temp variable so I don't have to clear it before every single for loop. 

# Return pyramids (7kyu)
The task is very simple.

You must to return pyramids. Given a number `n` you print a pyramid with `n` floors

For example , given a `n=4` you must to print this pyramid:

```
   /\
  /  \
 /    \
/______\ 
   
```

Other example, given a `n=6` you must to print this pyramid:

```
     /\
    /  \
   /    \
  /      \
 /        \
/__________\
```

Another example, given a `n=10`, you must to print this pyramid:

```
         /\
        /  \
       /    \
      /      \
     /        \
    /          \
   /            \
  /              \
 /                \
/__________________\
```

Note: a line feed character is needed at the end of the string. Case `n=0` should so return `"\n"`.

An answer:
```
function pyramid(n){
  var r = '';
  for(var i = 0; i<n; i++){
    r += ' '.repeat(n-i-1);
    r += '/';
    r += (i<n-1)?' '.repeat(2*i):'_'.repeat(2*i);
    r += '\\';
    r += '\n';
  }
  return r;
}
```

A more concise answer:
```
const pyramid = n =>
  [...Array(n)].map((_, idx) => `${` `.repeat(n - idx - 1)}/${(n === idx + 1 ? `__` : `  `).repeat(idx)}\\\n`).join(``);
```

# Sort Numbers (7 kyu)
Finish the solution so that it sorts the passed in array of numbers. If the function passes in an empty array or null/nil value then it should return an empty array.

For example:

```javascript
solution([1, 2, 10, 50, 5]); // should return [1,2,5,10,50]
solution(null); // should return []
```

My answer:
```
function solution(nums){
  return nums ? nums.sort((a, b) => a - b) : []
}
```

# Rot13 (5kyu)
ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

My answer:
```function rot13(message){
  const A = 65, Z = 90, a = 97, z = 122, ROT13 = 13;
  return String.fromCharCode(...message
    .split('')
    .map(c => {
      let char = c.charCodeAt(0);
      // Return non-letter characters unchanged
      if(char < A || (char > Z && char < a) || char > z) return char;
      // Apply ROT13 cipher
      let charCipher = char + ROT13 
      return char <= Z 
        ? charCipher > Z ? char = charCipher - 26 : charCipher  // Uppercase
        : charCipher > z ? char = charCipher - 26 : charCipher; // lowercase
      }) 
  );
}
```
The message is split into an array and then the map function is called on each element, checking first if it's a non-letter. If it is then it's returned unchanged. Apply the cipher on the character, using an intermediary cipher-applied char to check against if it's out of bounds. If the charCipher is, then we simply subtract 26 to get the proper value and return that. Finally we use the method String.fromCharCode() and the spread operator to return a string from our array of numbers. 

Another answer using regex:
```
function rot13(message) {
  var a = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
  var b = "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"
  return message.replace(/[a-z]/gi, c => b[a.indexOf(c)])
}
```
A second answer using regex:
```
const rot13 = str => str.replace(/[a-z]/gi, letter => String.fromCharCode(letter.charCodeAt(0) + (letter.toLowerCase() <= 'm' ? 13: -13)));
```

# Convert Boolean to a String (8kyu)
Implement a function which convert the given boolean value into its string representation.

Note: Only valid inputs will be given.

Answer:
```function booleanToString(b){
  return b.toString()
}
```

# Beginner Series #2 Clock (8kyu)
Clock shows `h` hours, `m` minutes and `s` seconds after midnight.

Your task is to write a function which returns the time since midnight in milliseconds.

## Example:

```
h = 0
m = 1
s = 1

result = 61000
```

Input constraints:

- `0 <= h <= 23`
- `0 <= m <= 59`
- `0 <= s <= 59`

Answer:
```function past(h, m, s){
  return (h*3600000) + (m*60000) + (s*1000)
}
```
Clearer answers:
```function past(h, m, s){
  return (h*3600000) + (m*60000) + (s*1000)
}
```

Best practice:
```function past(h, m, s){
  var hoursInMillseconds = h * 60 * 60 * 1000;
  var minutesInMillseconds = m * 60 * 1000;
  var secondsInMillseconds = s * 1000;
  
  return hoursInMillseconds + minutesInMillseconds + secondsInMillseconds;
}
```

# Is it a palindrome? (8 kyu)
Write a function that checks if a given string (case insensitive) is a [palindrome](https://en.wikipedia.org/wiki/Palindrome).

A palindrome is a word, number, phrase, or other sequence of symbols that reads the same backwards as forwards, such as `madam` or `racecar`.

Answer:
```
function isPalindrome(x) {
  return x.toLowerCase() === x.toLowerCase().split('').reverse().join('')
}
```

# Categorize New Member (7kyu)
The Western Suburbs Croquet Club has two categories of membership, Senior and Open. They would like your help with an application form that will tell prospective members which category they will be placed.

To be a senior, a member must be at least 55 years old and have a handicap greater than 7. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.

## Input

Input will consist of a list of pairs. Each pair contains information for a single potential member. Information consists of an integer for the person's age and an integer for the person's handicap.

## Output

Output will consist of a list of string values (in Haskell and C: `Open` or `Senior`) stating whether the respective member is to be placed in the senior or open category.

### Example

```
input =  [[18, 20], [45, 2], [61, 12], [37, 6], [21, 21], [78, 9]]
output = ["Open", "Open", "Senior", "Open", "Open", "Senior"]
```

My answer:
```function openOrSenior(data){
  return data.map(member => member[0] >= 55 && member[1] > 7 ? "Senior" : "Open")
}
```

A more readable answer:
```
function openOrSenior(data){
  return data.map(([age, handicap]) => (age > 54 && handicap > 7) ? 'Senior' : 'Open');
}
```

# Count of positive/sum of negatives (8kyu)
Given an array of integers.

Return an array, where the first element is the count of positives numbers and the second element is sum of negative numbers. 0 is neither positive nor negative.

If the input is an empty array or is null, return an empty array.

## Example

For input `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, -11, -12, -13, -14, -15]`, you should return `[10, -65]`.

My answer:
```
function countPositivesSumNegatives(input) {
  if(!Array.isArray(input) || !input.length) return [];
  
  let arr = [0, 0];
  for(let i = 0; i < input.length; i++){
    if(input[i] > 0) arr[0]++;
    if(input[i] < 0) arr[1] += input[i];
  }
  
  return arr;
}
```

A more succinct answer:
```function countPositivesSumNegatives(input) {
  return !input || !input.length ? [] : input.reduce(([pos, neg], num) => [
    pos + (num > 0 ? 1 : 0),
    neg + (num < 0 ? num : 0)
  ], [0, 0]);
}
```
1. **Destructuring in the `reduce` function**: Instead of using `sum[0]` and `sum[1]`, we directly destructure the accumulator into `[pos, neg]` for better readability.

2. **Inline conditional updates**: The positive count (`pos`) and negative sum (`neg`) are updated inline using ternary operators, making the code more concise.

3. **Implicit return**: The `reduce` callback implicitly returns the updated `[pos, neg]` array.

# Powers of 2 (8kyu)
Complete the function that takes a non-negative integer `n` as input, and returns a list of all the powers of `2` with the exponent ranging from `0` to `n` ( inclusive ).

## Examples

```python
n = 0  ==> [1]        # [2^0]
n = 1  ==> [1, 2]     # [2^0, 2^1]
n = 2  ==> [1, 2, 4]  # [2^0, 2^1, 2^2]
```

My answer:
```function powersOfTwo(n){
  return Array(n+1).fill(2).map((num,idx) => Math.pow(num,idx))
}
```

Another answer:
```
function powersOfTwo(n) {
  return Array.from({length: n + 1}, (v, k) => 2 ** k);
}
```

# Break camelCase (6 kyu)
Complete the solution so that the function will break up camel casing, using a space between words.

### Example

```
"camelCasing"  =>  "camel Casing"
"identifier"   =>  "identifier"
""             =>  ""
```

My answer:
```function solution(string) {
  let brokenStr = '';
  
  for (let i = 0; i < string.length; i++) {
    if( string[i] === string[i].toUpperCase() ) brokenStr += ' '; 
    brokenStr += string[i];
  }
  
  return brokenStr;
}
```
Iterate over the string, checking if it's uppercase via comparison to it's upperCase version. If one is found, add a space to the new string before adding the original character. 

A solution using methods:
```
const solution = string => {
  return [...string].map((char) => {
    return (char === char.toUpperCase()) ? ` ${char}` : char;
  }).join('');
}
```

# Simple Encryption #1 - Alternating Split (6kyu)
Implement a pseudo-encryption algorithm which given a string `S` and an integer `N` concatenates all the odd-indexed characters of `S` with all the even-indexed characters of `S`, this process should be repeated `N` times.

Examples:

```
encrypt("012345", 1)  =>  "135024"
encrypt("012345", 2)  =>  "135024"  ->  "304152"
encrypt("012345", 3)  =>  "135024"  ->  "304152"  ->  "012345"

encrypt("01234", 1)  =>  "13024"
encrypt("01234", 2)  =>  "13024"  ->  "32104"
encrypt("01234", 3)  =>  "13024"  ->  "32104"  ->  "20314"
```

Together with the encryption function, you should also implement a decryption function which reverses the process.

If the string `S` is an empty value or the integer `N` is not positive, return the first argument without changes.

My answer:
```
function encrypt(text, n) {
  if(text === null) return null;
  if(!text || n <= 0) return text;
  
  let secretTxt = text;
  while(n > 0){
    let even = "", odd = "";
    for(let i = 0; i < secretTxt.length; i++){
      i % 2 === 0 ? even += secretTxt[i] : odd += secretTxt[i];
    }
    secretTxt = odd+even;
    n--;
  }
  
  return secretTxt;
}

function decrypt(encryptedText, n) {
  if(encryptedText === null) return null;
  if(!encryptedText || n <= 0) return encryptedText;
  
  let secretTxt = encryptedText, txtLength = encryptedText.length;
  while(n > 0){
    let tmp = [], halfLength = Math.floor(txtLength/2), 
    firstHalf = secretTxt.slice(halfLength), 
    secondHalf = secretTxt.slice(0, halfLength);
    
    for (let i = 0, j = 0, k = 0; i < txtLength; i++) {
      if (i % 2 === 0) {
        tmp[i] = firstHalf[j++];
      } else {
        tmp[i] = secondHalf[k++];
      }
    }
    secretTxt = tmp.join('');
    n--;
  }
  
  return secretTxt;
}
```

My code optimized/refactored:
```
function encrypt(text, n) {
    if (text === null) return null;
    if (!text || n <= 0) return text;

    let secret = text;
    for (let i = 0; i < n; i++) {
        const [even, odd] = [[], []];
        for (let j = 0; j < secret.length; j++) {
            (j % 2 ? odd : even).push(secret[j]);
        }
        secret = odd.concat(even).join('');
    }
    return secret;
}
```
For encrypt(), even and odd are set as an array for easier viewing as well as efficiency. Strings are immutable in JS causing O(n^2) time complexity whenever you append a string. `const [even, odd] = [[], []];` is a **destructuring assignment** - a concise way to define and initialize two arrays in a single line. It also removes the while loop, instead nesting a for loop inside another, allowing us to write less code. 

```
function decrypt(encryptedText, n) {
    if (encryptedText === null) return null;
    if (!encryptedText || n <= 0) return encryptedText;

    const length = encryptedText.length;
    let secret = encryptedText;
    
    for (let i = 0; i < n; i++) {
        const mid = Math.floor(length / 2);
        const first = secret.slice(mid);
        const second = secret.slice(0, mid);
        
        secret = Array.from({length}, (_, idx) => 
            idx % 2 ? second[(idx - 1) >> 1] : first[idx >> 1]
        ).join('');
    }
    return secret;
}
```
While loop is replaced with a for() loop. Redundant counter variables eliminated and calculates indices directly using  bitwise operations (>> 1). The for() loop is replaced with Array.from(). The method array.from() creates a new, shallow-copied array instance from another array. 
### Array.from() explanation
**1. `Array.from({ length }, callback)`**

- **Purpose:** Creates a new array of a specified length and populates it using a callback function.
    
- **`{ length }`:** This creates an array-like object with a `length` property. For example, if `length = 10`, it behaves like an array with 10 empty slots.
    
- **Callback Function:** The second argument is a mapping function that determines the value of each element in the new array.
    

---

**2. Callback Function: `(_, idx) => ...`**

- **Parameters:**
    
    - `_`: A placeholder for the current element (not used in this case).
        
    - `idx`: The index of the current element being processed.
        
- **Purpose:** For each index `idx` in the new array, the callback decides which character to place at that position.
    

---

 **3. Ternary Operator: `idx % 2 ? ... : ...`**

- **Purpose:** Determines whether the current index `idx` is odd or even.
    
    - If `idx` is **odd** (`idx % 2 === 1`), take a character from `second`.
        
    - If `idx` is **even** (`idx % 2 === 0`), take a character from `first`.
        

---

 **4. Bitwise Operations: `>> 1`**

- **Purpose:** Efficiently calculates the index in the `first` or `second` array.
    
    - `idx >> 1`: Equivalent to `Math.floor(idx / 2)`. Used for even indices.
        
    - `(idx - 1) >> 1`: Equivalent to `Math.floor((idx - 1) / 2)`. Used for odd indices.
        
- **Why Bitwise?** Bitwise operations are faster than division and floor operations.
    

---

 **5. Accessing `first` and `second` Arrays**

- **`first[idx >> 1]`:** For even indices, take the character from `first` at the calculated index.
    
- **`second[(idx - 1) >> 1]`:** For odd indices, take the character from `second` at the calculated index.
    

---

 **6. `join('')`**

- **Purpose:** Converts the array of characters into a single string.
    
- **Why?** After reconstructing the array, we need to join its elements into a string to get the final result.
# What is between? (8kyu)
Complete the function that takes two integers (`a, b`, where `a < b`) and return an array of all integers between the input parameters, **including** them.

For example:

```
a = 1
b = 4
--> [1, 2, 3, 4]
```

My answer:
```function between(a, b) {
  let arr = []
  for(i = a; i <= b; i++) arr.push(i);
  return arr
}
```

Answer using array.from()
```
const between = (a, b) => 
	Array.from(new Array(b-a+1), (_, i) => a + i);
```
Create a new array of (b-a+1) size. The second parameter calls a map() function on the newly formed array, using the index + smallest number to populate the array with the proper values.

Another answer:
```
const between = (a, b) =>
  [...Array(b - a + 1)].map((_, idx) => idx + a);
```
Using the spread operator is required, else it will return an array of [undefined]

# Grasshopper - personalized message (8 kyu)
Create a function that gives a personalized greeting. This function takes two parameters: `name` and `owner`.

Use conditionals to return the proper message:

|case|return|
|---|---|
|name equals owner|'Hello boss'|
|otherwise|'Hello guest'|
My answer:
```
function greet (name, owner) {
  return name === owner ? 'Hello boss' : 'Hello guest';
}
```

Another answer:
```
function greet (name, owner) {
  return `Hello ${name==owner?'boss':'guest'}`
}
```
Use of string literals.

# Make a function that does arithmetic (7kyu)
Given two numbers and an arithmetic operator (the name of it, as a string), return the result of the two numbers having that operator used on them.

`a` and `b` will both be positive integers, and `a` will always be the first number in the operation, and `b` always the second.

The four operators are "add", "subtract", "divide", "multiply".

A few **examples:(Input1, Input2, Input3 --> Output)**

```
5, 2, "add"      --> 7
5, 2, "subtract" --> 3
5, 2, "multiply" --> 10
5, 2, "divide"   --> 2.5
```

Try to do it without using if statements!

My answer:
```
function arithmetic(a, b, operator){
  if(operator === "add"){
    return a + b 
  } else if(operator === "subtract"){
    return a - b
  } else if(operator === "multiply"){
    return a * b      
  } else if(operator === "divide"){
    return a / b 
  } 
}
```
Another answer:
```
const arithmetic = (a, b, operator) => {
 return  ( 
   operator === "add" ? a + b : operator === "subtract" ? a - b : operator === "multiply" ? a * b : a / b
 )
}
```
Another answer:
```
const arithmetic = (a, b, operator) => ({
  'add'     : a + b,
  'subtract': a - b,
  'multiply': a * b,
  'divide'  : a / b
}[operator]);
```

# Give me a Diamond (6kyu)
## Task

You need to return a string that looks like a diamond shape when printed on the screen, using asterisk (`*`) characters. Trailing spaces should be removed, and every line must be terminated with a newline character (`\n`).

Return `null/nil/None/...` if the input is an even number or negative, as it is not possible to print a diamond of even or negative size.

## Examples

A size 3 diamond:

```
 *
***
 *
```

...which would appear as a string of `" *\n***\n *\n"`

A size 5 diamond:

```
  *
 ***
*****
 ***
  *
```

...that is:

```
"  *\n ***\n*****\n ***\n  *\n"
```

My answer:
```function diamond(n){
  if(n < 0 || n % 2 === 0 || !n) return null;
  
  let arr = [], midpoint = Math.floor(n/2);
  for(let i = 0; i < n; i++){
    let spaces = Math.abs(midpoint - i);
    let stars = n - 2 * spaces;
    arr.push(" ".repeat(spaces) + "*".repeat(stars) + "\n");
  }
  
  return arr.join('');
}
```

Another answer:
```
const diamond = n =>
  n < 0 || --n % 2 ? null : [...Array(n + 1)].map((_, idx) => ` `.repeat(Math.abs(n / 2 - idx)) + `*`.repeat(n + 1 - Math.abs(n - 2 * idx)) + `\n`).join(``);
```

# Sort and Star (8kyu)
You will be given a list of strings. You must sort it alphabetically (case-sensitive, and based on the ASCII values of the chars) and then return the first value.

The returned value must be a string, and have `"***"` between each of its letters.

You should not remove or add elements from/to the array.

My answer:
```function twoSort(s) {
  return s.sort()[0].split('').join("***");
}
```
 
# Filter out the geese (8 kyu)
Write a function that takes a list of strings as an argument and returns a filtered list containing the same elements but with the 'geese' removed.

The geese are any strings in the following array, which is pre-populated in your solution:

```
  ["African", "Roman Tufted", "Toulouse", "Pilgrim", "Steinbacher"]
```

For example, if this array were passed as an argument:

```
 ["Mallard", "Hook Bill", "African", "Crested", "Pilgrim", "Toulouse", "Blue Swedish"]
```

Your function would return the following array:

```
["Mallard", "Hook Bill", "Crested", "Blue Swedish"]
```

The elements in the returned array should be in the same order as in the initial array passed to your function, albeit with the 'geese' removed. Note that all of the strings will be in the same case as those provided, and some elements may be repeated.

My answer:
```
// return an array containing all of the strings in the input array except those that match strings in geese
function gooseFilter (birds) {
  var geese = ["African", "Roman Tufted", "Toulouse", "Pilgrim", "Steinbacher"];
  return birds.filter(bird => !geese.includes(bird));
};
```

# Remove anchor from URL (7kyu)
Complete the function/method so that it returns the url with anything after the anchor (`#`) removed.

## Examples

```
"www.codewars.com#about" --> "www.codewars.com"
"www.codewars.com?page=1" -->"www.codewars.com?page=1"
```

My answer:
```function removeUrlAnchor(url){
  return url.split('#')[0]
}
```

# No zeros for heroes (8kyu)
Numbers ending with zeros are boring.

They might be fun in your world, but not here.

Get rid of them. Only the ending ones.

```
1450   -> 145
960000 -> 96
1050   -> 105
-1050  -> -105
0      -> 0
```

**Note**: Zero should be left as it is.

Answer:
```
function noBoringZeros(n) {
  while (n % 10 === 0 && n !== 0) {
    n = n / 10
  }
  return n
}
```
Check if number is divisible by 10 and not zero. Keep dividing it until it is no longer divisible by ten.

# I love you, a little, a lot, passionately ...not at all (8 kyu)
Who remembers back to their time in the schoolyard, when girls would take a flower and tear its petals, saying each of the following phrases each time a petal was torn:

1. "I love you"
2. "a little"
3. "a lot"
4. "passionately"
5. "madly"
6. "not at all"

If there are more than 6 petals, you start over with `"I love you"` for 7 petals, `"a little"` for 8 petals and so on.

When the last petal was torn there were cries of excitement, dreams, surging thoughts and emotions.

Your goal in this kata is to determine which phrase the girls would say at the last petal for a flower of a given number of petals. The number of petals is always greater than 0.

My answer:
```function howMuchILoveYou(nbPetals) {
    const love = ["I love you", "a little", "a lot", "passionately", "madly", "not at all"];
    return love[(nbPetals - 1) % 6]
}

```

More efficient answer:
```
function howMuchILoveYou(nbPetals) {
  return ['not at all', 'I love you', 'a little', 'a lot', 'passionately', 'madly'][nbPetals%6]
}
```
Another one:
```
function howMuchILoveYou(nbPetals) {
    const phrases = ["I love you", "a little", "a lot", "passionately", "madly", "not at all"];
    return phrases[(nbPetals - 1) % phrases.length];
}
```

# Find the unique number (6kyu)
There is an array with some numbers. All numbers are equal except for one. Try to find it!

```javascript
findUniq([ 1, 1, 1, 2, 1, 1 ]) === 2
findUniq([ 0, 0, 0.55, 0, 0 ]) === 0.55
```

It’s guaranteed that array contains at least 3 numbers.

The tests contain some very huge arrays, so think about performance.

My answer:
```function findUniq(arr) {
  if(arr[0] !== arr[1]){
    return arr[0] === arr[2] ? arr[1] : arr[0]
  }
  const same = arr[0]
  for(let i = 2; i < arr.length; i++){
    if(arr[i] !== same) return arr[i]
  }
}
```

Answer using objects:
```
function findUniq(arr) {
  let uniq = {},
      result;
  arr.forEach(function(item) {
    uniq[item] = uniq[item] + 1 || 1;
  });
  Object.keys(uniq).forEach(function(key) {
    if (uniq[key] == 1) {
      result = key;
    }
  });
  
  return parseFloat(result);
}
```

Performant solution:
```
function findUniq(arr) {
  let [a,b,c] = arr.slice(0,3);
  if( a != b && a!=c ) return a;
  for( let x of arr ) if( x!=a ) return x
}
```

Clever but slow solution:
```
function findUniq(arr) {
  return arr.find(n => arr.indexOf(n) === arr.lastIndexOf(n));
}
```
Checks the the first time and an element occurs. A unique element will have these indexes be exactly the same. O(n^2) complexity.

# Reverse List Order (8kyu)
In this kata you will create a function that takes in a list and returns a list with the reverse order.

### Examples (Input -> Output)

```
* [1, 2, 3, 4]  -> [4, 3, 2, 1]
* [9, 2, 0, 7]  -> [7, 0, 2, 9]
```

Answer:
```
function reverseList(list) {
  return list.reverse();
}
```

# Directions Reduction (5kyu)
Write a function `dirReduc` which will take an array of strings and returns an array of strings with the needless directions removed (W<->E or S<->N _side by side_).

- The Haskell version takes a list of directions with `data Direction = North | East | West | South`.
- The Clojure version returns nil when the path is reduced to nothing.
- The Rust version takes a slice of `enum Direction {North, East, West, South}`.
- The OCaml version takes a list of `type direction = | North | South | East | West`.

#### See more examples in "Sample Tests:"

#### Notes

- Not all paths can be made simpler. The path ["NORTH", "WEST", "SOUTH", "EAST"] is not reducible. "NORTH" and "WEST", "WEST" and "SOUTH", "SOUTH" and "EAST" are not _directly_ opposite of each other and can't become such. Hence the result path is itself : ["NORTH", "WEST", "SOUTH", "EAST"].

My answer:
```function dirReduc(arr){
  //define a dictionary to compare values
  const redundant = {
    NORTH: "SOUTH",
    SOUTH: "NORTH", 
    WEST: "EAST",
    EAST: "WEST"
  }
  //define the previous direction for comparison
  let prev = ""
  
  //start at index 1
  for(let i = 1; i < arr.length; i++){
    prev = arr[i-1]
    if(redundant[arr[i]] === prev){
      arr.splice(i-1, 2) //remove two elements from arr
      i -= 2 //move pointer back 2 indexes
    }
  }
  
  return arr;
  
```

```
["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"],
```

A more succinct answer using reduce:
```
function dirReduc(plan) {
  const opposite = {
    'NORTH': 'SOUTH', 'EAST': 'WEST', 'SOUTH': 'NORTH', 'WEST': 'EAST'};
  return plan.reduce((dirs, dir){
      dirs[dirs.length - 1] === opposite[dir] ? dirs.pop() : dirs.push(dir);
      return dirs;
    }, []);
}
```
Compare the previous value to the current value for NORTH/SOUTH, EAST/WEST. If it matches then pop() the array else push the current value. 

Another answer using reduce:
```
function dirReduc(arr){
	const opposite = { "SOUTH":"NORTH", "NORTH":"SOUTH", "WEST":"EAST", "EAST":"WEST"}
	return arr.reduce((a, b) {
  	opposite[a.slice(-1)] === b ? a.pop() : a.push(b)
  	return a
  }, [])
}
```
a is the array object, b is the current value. a.slice(-1) returns a shallow portion of the array into a new array object, specifically the last value of the new array... for comparison with the current value for NORTH/SOUTH, EAST/WEST.

# Tribonacci Sequence (6kyu)
As the name may already reveal, it works basically like a Fibonacci, but summing the last 3 (instead of 2) numbers of the sequence to generate the next. 

So, if we are to start our Tribonacci sequence with `[1, 1, 1]` as a starting input (AKA _signature_), we have this sequence:

```
[1, 1 ,1, 3, 5, 9, 17, 31, ...]
```

But what if we started with `[0, 0, 1]` as a signature? As starting with `[0, 1]` instead of `[1, 1]` basically _shifts_ the common Fibonacci sequence by once place, you may be tempted to think that we would get the same sequence shifted by 2 places, but that is not the case and we would get:

```
[0, 0, 1, 1, 2, 4, 7, 13, 24, ...]
```

Well, you may have guessed it by now, but to be clear: you need to create a fibonacci function that given a **signature** array/list, returns **the first n elements - signature included** of the so seeded sequence.

Signature will always contain 3 numbers; n will always be a non-negative number; if `n == 0`, then return an empty array (except in C return NULL) and be ready for anything else which is not clearly specified ;)

my answer:
```function tribonacci(signature,n){
  let trib = []
  for(let i = 0; i < n; i++){
    i <= 2 ? trib.push(signature[i]) : 
            trib.push(+trib.slice(-1) + +trib.slice(-2, -1)+ +trib.slice(-3, -2) )
  }
  return trib;
}
```

better ans:
```
function tribonacci(signature,n){  
  for (var i = 0; i < n-3; i++) { // iterate n times
    signature.push(signature[i] + signature[i+1] + signature[i+2]); // add last 3 array items and push to trib
  }
  return signature.slice(0, n); //return trib - length of n
}
```

another ans:
```
function tribonacci(signature,n) {
  const result = signature.slice(0, n);
  while (result.length < n) {
    result[result.length] = result.slice(-3).reduce((p,c) => p + c, 0);
  }
  return result;
}
```

another ans one line:
```
const tribonacci = (signature, n) =>
  [...Array(n)].reduce((pre, _, idx) => [...pre, pre[idx] + pre[++idx] + pre[++idx]], signature).slice(0, n);
```

# Are You Playing Banjo? (8kyu)
Create a function which answers the question "Are you playing banjo?".  
If your name starts with the letter "R" or lower case "r", you are playing banjo!

The function takes a name as its only argument, and returns one of the following strings:

```
name + " plays banjo" 
name + " does not play banjo"
```

Names given are always valid strings.

My answer:
```function areYouPlayingBanjo(name) {
  return name[0].toLowerCase() === 'r' ? `${name} plays banjo` : `${name} does not play banjo`
}

```

Better ans:
```
function areYouPlayingBanjo(name) {
  return name + (name[0].toLowerCase() == 'r' ? ' plays' : ' does not play') + " banjo";
}
```

# Sum of odd numbers (7kyu)
Given the triangle of consecutive odd numbers:

```
             1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
...
```

Calculate the sum of the numbers in the nth row of this triangle (starting at index 1) e.g.: (**Input --> Output**)

```
1 -->  1
2 --> 3 + 5 = 8
```

Answer:
```
function rowSumOddNumbers(n)
{
  /* The rows' start numbers are Hogben's centered polygonal numbers:
     1, 3, 7, 13, 21, 31, 43 = b[n] = n^2 - n + 1.
     <https://oeis.org/A002061>
     
     The sum of one row is given by:
     s[n] = n^2 + n(b[n] - 1).
     <https://www.quora.com/What-is-the-sum-of-n-consecutive-odd-integers/answer/Xavier-Dectot>
     
     Inline b[n]:
     s[n] = n^2 + n(n^2 - n + 1 - 1)
          = n^2 + n(n^2 - n)
          = n^2 + n^3 - n^2
          = n^3
     ... oh. */
  return n * n * n;
}
```

# Exclamation marks series #11: Replace all vowel to exclamation mark in the sentence (8kyu)
Replace all vowel to exclamation mark in the sentence. `aeiouAEIOU` is vowel.

### Examples

```javascript
"Hi!" --> "H!!"
"!Hi! Hi!" --> "!H!! H!!"
"aeiou" --> "!!!!!"
"ABCDE" --> "!BCD!"
```

My answer:
```
function replace(s) {
  return s.split('').map(letter => 'AEIOUaeiou'.includes(letter) ? '!' : letter ).join('')
}
```

Slightly more efficient answer:
```
const replace = w => w.split('').map(e => new Set(['a', 'e', 'i', 'o', 'u']).has(e.toLowerCase()) ? '!' : e).join('');
```

# Title Case (6 kyu)
A string is considered to be in title case if each word in the string is either (a) capitalised (that is, only the first letter of the word is in upper case) or (b) considered to be an exception and put entirely into lower case unless it is the first word, which is always capitalised.

Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string -- it should behave in the same way even if the case of the minor word string is changed.

### Arguments (Haskell)

- **First argument**: space-delimited list of minor words that must always be lowercase except for the first word in the string.
- **Second argument**: the original string to be converted.

### Arguments (Other languages)

- **First argument (required)**: the original string to be converted.
- **Second argument (optional)**: space-delimited list of minor words that must always be lowercase except for the first word in the string. The JavaScript/CoffeeScript tests will pass `undefined` when this argument is unused.

### Example

```javascript
titleCase('a clash of KINGS', 'a an the of') // should return: 'A Clash of Kings'
titleCase('THE WIND IN THE WILLOWS', 'The In') // should return: 'The Wind in the Willows'
titleCase('the quick brown fox') // should return: 'The Quick Brown Fox'
```

My answer:
```
function titleCase(title, minorWords) {
  if(title === '') return '';
  
  minorWords = (minorWords || '').toLowerCase();
  return title.toLowerCase().split(' ').map((word,idx) => 
	    idx !== 0 && minorWords.split(' ').includes(word) 
	    ? word : word[0].toUpperCase() + word.substring(1, word.length)
      ).join(' ')
}
```
If empty string, return empty string. Define minorWords as either the given or an empty string if no parameter was given and change it to lowercase. 

Turn the string of title lowercase and into an array, and then do a check. Always capitalize the first word. If it is not the first element of the array, check if the word is in the minorWords array - if it is then return all lowercase. Finally, join the array back into a string an return it.

Another answer:
```
function titleCase(title, minorWords) {
  var minorWords = typeof minorWords !== "undefined" ? minorWords.toLowerCase().split(' ') : [];
  return title.toLowerCase().split(' ').map(function(v, i) {
    if(v != "" && ( (minorWords.indexOf(v) === -1) || i == 0)) {
      v = v.split('');
      v[0] = v[0].toUpperCase();
      v = v.join('');
    }
    return v;
  }).join(
```

# Summing a number's digits (7kyu)
Write a function which takes a number as input and returns the sum of the absolute value of each of the number's decimal digits.

For example: (**Input --> Output**)

```
10 --> 1
99 --> 18
-32 --> 5
```

Let's assume that all numbers in the input will be integer values.

My answer:
```
function sumDigits(number) {
  return Math.abs(number).toString().split('').reduce((sum, num) => sum + +num,0)
}
```

Efficient answer:
```
const sumDigits = number =>
  [...`${Math.abs(number)}`].reduce((pre, val) => pre + +val, 0);
```

# Name Shuffler (8kyu)
Write a function that returns a string in which firstname is swapped with last name.

**Example(Input --> Output)**

```
"john McClane" --> "McClane john"
```
My answer:
```function nameShuffler(str){
  return str.split(' ').reverse().join(' ')
}
```

# Find the smallest integer in the array (8kyu)
Given an array of integers your solution should find the smallest integer.

For example:

- Given `[34, 15, 88, 2]` your solution will return `2`
- Given `[34, -345, -1, 100]` your solution will return `-345`

You can assume, for the purpose of this kata, that the supplied array will not be empty.

My answer:
```function findSmallestInt(arr) {
  return Math.min(...arr)
}
```

# Plural (8kyu)
We need a simple function that determines if a plural is needed or not. It should take a number, and return true if a plural should be used with that number or false if not. This would be useful when printing out a string such as `5 minutes`, `14 apples`, or `1 sun`.

> You only need to worry about english grammar rules for this kata, where anything that isn't singular (one of something), it is plural (not one of something).

All values will be positive integers or floats, or zero.

My answer:
```function plural(n) {
  return n === 1 ? false : true
}
```
Better answer:
```
function plural(n) {
  return n === 1 ? false : true
}
```

# Shortest Word (7kyu)
Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.

My answer:
```
function findShort(s){
  return Math.min(...s.split(' ').map(word => word.length))
}
```

# Highest Scoring Word (6kyu)
Given a string of words, you need to find the highest scoring word.

Each letter of a word scores points according to its position in the alphabet: `a = 1, b = 2, c = 3` etc.

For example, the score of `abad` is `8` (1 + 2 + 1 + 4).

You need to return the highest scoring word as a string.

If two words score the same, return the word that appears earliest in the original string.

All letters will be lowercase and all inputs will be valid.

My answer:
```
function high(x){
  const scores = x.split(' ').map(word => word.split('').reduce((sum, letter) => (sum + letter.charCodeAt(0) - 96), 0))
  return x.split(' ')[scores.indexOf(Math.max(...scores))]
}
```
Split string into array of strings ["man", "i", "need"]. Then call map to replace each string with a number. This is done through the use of reduce, first splitting each individual string into characters which are then converted to their ASCII value minus 96 - the value for a is 97 and the desired value of a is 1. 
Once we have our array of words converted into numbers, we split the initial string again, using bracket notation to call the specific index of the highest scoring word. The highest scoring word is found via parsing the scores array again, using Math,max() to find the highest score and then calling indexOf() to return the index. 
Big O notation = O(2n) = O(n)

Concise and functional programming-style solution:
```
const high = x =>
  (fn => x.split(` `).sort((a, b) => fn(b) - fn(a))[0])
  (word => [...word].reduce((pre, val) => pre + val.charCodeAt() - 96, 0));
```
The first line is a helper function. fn is an **IIFE** (Immediately Invoked Function Expression) defined and immediately called, sorting the array from highest to lowest. The conversion from string -> number happens before the sorting happens.

# Are we alternate? (6kyu)
Create a function that accepts a string as an argument and validates whether the vowels (a, e, i, o, u) and consonants are in alternate order.

## Examples

```
"amazon" --> true
"apple" --> false
"banana" --> true
```

## Note

- Arguments consist of only lowercase letters.
A answer:
```
function isAlternating(str) {
  // Define vowels
  const vowels = new Set(['a', 'e', 'i', 'o', 'u']);

  // Iterate through the string
  for (let i = 0; i < str.length - 1; i++) {
    const currentChar = str[i];
    const nextChar = str[i + 1];

    // Check if current and next characters are both vowels or both consonants
    const currentIsVowel = vowels.has(currentChar);
    const nextIsVowel = vowels.has(nextChar);

    if (currentIsVowel === nextIsVowel) {
      return false; // Two vowels or two consonants in a row
    }
  }

  return true; // All characters alternate
}
```

Another answer:
```
function isAlt(word) {
  let isVowels = {'a':1,'e':1,'i':1,'o':1,'u':1}, prev, cur;
  for (let i=0; i<word.length; i++) {
    cur = word[i] in isVowels ? 'vowel' : 'consonant';
    if (cur === prev) { return false; }
    prev = cur;
  }
  return true;
}
```

My answer:
```
function isAlt(word){
    const vowels = new Set(['a', 'e', 'i', 'o', 'u']), chars = word.split('') 
    for(let i = 0; i < chars.length-1; i++){
      if(vowels.has(chars[i]) === vowels.has(chars[i+1])){
        return false
      } 
    }
    return true
} 
```

# Find a Bunch of Common Elements of Two Lists in a Certain Range (6kyu)
We are given two arrays of integers A and B and we have to output a sorted array with the integers that fulfill the following constraints:

- they are present in both ones
    
- they occur more than once in A and more than once in B
    
- their values are within a given range (inclusive)
    
- they are odd or even according as it is requested
    

## Example

Given two arrays, a range, and a wanted parity:

```python
arrA = [1, -2, 7, 2, 1, 3, 7, 1, 0, 2, 3]
arrB = [2, -1, 1, 1, 1, 1, 2, 3, 3, 7, 7, 0]
rng = [-4, 4] # is the range of the integers from -4 to 4 (inclusive)
wanted = "odd"
```

Process to obtain the result:

```
0, 1, 2, 3, 7, are the numbers present in arrA and arrB
1, 2, 3, 7,  occur twice or more in arrA and arrB
1, 2, 3,  are in the range [-4, 4]
1, 3, are odd
output = [1, 3] 
```

For the case:

```python
arrA = [1, -2, 7, 2, 1, 3, 4, 7, 1, 0, 2, 3, 0, 4]
arrB = [0, 4, 2, -1, 1, 1, 1, 1, 2, 3, 3, 7, 7, 0, 4]
rng = [-4, 4]
wanted = "even"
output = [0, 2, 4] 
```

If there are no elements that fulfill the constraints given above, the result will be an empty array.

Features of the tests:

```
Number of Random Tests = 300
Length of the arrays A and B between 1000 and 10000
```

You may assume that you will always receive valid entries for all the tests.

My answer using maps:
```
function findArr(arrA, arrB, rng, wanted) {
  const countA = new Map(), countB = new Map()
  
  //get counts of each element in A
  arrA.forEach(n => {countA.set(n, (countA.get(n) || 0) +1)}) 
  //get counts of each element in B
  arrB.forEach(n => {countB.set(n, (countB.get(n) || 0) +1)}) 
  
  //check A/B for same values that also occur > 1
  let duplicates = []
  for(let n of countA.keys()){
    if (countA.get(n) > 1 && countB.get(n) > 1) {
      duplicates.push(n);
    }
  }
  
  //filter for range and odd/even
  return duplicates
    .filter(n => n >= rng[0] && n <= rng[1] && (wanted === 'even' ? n % 2 === 0 : n % 2 !== 0))
    .sort((a, b) => a - b);
  
}
```

Another much more elegant answer:
```
const findArr = (arrA, arrB, [min, max], wanted) =>
  [... new Set(arrA.filter(val =>
                 val >= min && val <= max
                   &&
                 (val & 1) === +(wanted === `odd`)
                   &&
                 arrA.indexOf(val) !== arrA.lastIndexOf(val)
                   &&
                 arrB.indexOf(val) !== arrB.lastIndexOf(val)))
  ].sort((a, b) => a - b);
```

# The Wide-Mouthed frog! (8kyu)
The wide-mouth frog is particularly interested in the eating habits of other creatures.

He just can't stop asking the creatures he encounters what they like to eat. But, then he meets the alligator who just LOVES to eat wide-mouthed frogs!

When he meets the alligator, it then makes a tiny mouth.

Your goal in this kata is to create complete the `mouth_size` method this method takes one argument `animal` which corresponds to the animal encountered by the frog. If this one is an `alligator` (case-insensitive) return `small` otherwise return `wide`.

My answer:
```
function mouthSize(animal) {
  return animal.toLowerCase() === 'alligator' ? 'small' : 'wide'
}
```
# Mexican Wave (6kyu)
## Task

In this simple Kata your task is to create a function that turns a string into a Mexican Wave. You will be passed a string and you must return that string in an array where an uppercase letter is a person standing up. 

## Rules

 1.  The input string will always be lower case but maybe empty.  
 2.  If the character in the string is whitespace then pass over it as if it was an empty seat

## Example

```javascript
wave("hello") => ["Hello", "hEllo", "heLlo", "helLo", "hellO"]
```

My answer:
```
function wave(str){
  let str2 = str.toLowerCase();
  return Array(str2.length)
    .fill(str2)
    .map((n,idx) => {
    	if (str[idx] === ' ') return null
      let letters = n.split('')
      letters[idx] = letters[idx].toUpperCase()
      return letters.join('')
    })
    .filter(str => str !== null)
}
```

Another answer using a for() loop
```
function wave(str) {
  let str = str.toLowerCase(), result = [];
  for (let i = 0; i < str.length; i++) {
    if (str[i] === ' ') continue; // Skip spaces
    const waveStr = str.slice(0, i) + str[i].toUpperCase() + str.slice(i + 1);
    result.push(waveStr);
  }
  return result;
}
```

# Remove duplicates from list (8kyu)
Define a function that removes duplicates from an array of non negative numbers and returns it as a result.

The order of the sequence has to stay the same.

Examples:

```
Input -> Output
[1, 1, 2] -> [1, 2]
[1, 2, 1, 1, 3, 2] -> [1, 2, 3]
```

My answer:
```
function distinct(a) {
  return [...new Set(a)];
}
```

# Maximum subarray sum (5kyu)
The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:

```javascript
maxSequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
// should be 6: [4, -1, 2, 1]
```

Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.

An answer:
```
function maxSequence(arr) {
    // Edge cases: empty array or all negative numbers
    if (!arr.length || arr.every(x => x < 0)) {
        return 0;
    }

    let maxSum = 0;      // Tracks the maximum sum found so far
    let currentSum = 0;  // Tracks the sum of the current subarray

    for (let num of arr) {
        // Update currentSum to be the maximum of the current number or the currentSum + current number
        currentSum = Math.max(num, currentSum + num);
        // Update maxSum if currentSum is greater
        maxSum = Math.max(maxSum, currentSum);
    }

    return maxSum;
}
```

Another answer:
```
var maxSequence = function(arr) {
  let min = 0, ans = 0, i, sum = 0;
  for (i = 0; i < arr.length; ++i) {
    sum += arr[i];          // Calculate the prefix sum up to the current index
    min = Math.min(sum, min); // Track the minimum prefix sum encountered so far
    ans = Math.max(ans, sum - min); // Update the answer with the maximum subarray sum
  }
  return ans;
};
```

# Word Challenges at School (6kyu)
The principal of a school likes to put challenges to the students related with finding words of certain features. One day she said: "Dear students, the challenge for today is to find a word that has only one vowel and seven consonants but cannot have the letters "y" and "m". I'll give a special award for the first student that finds it." One of the students used his dictionary and spent all the night without sleeping, trying in vain to find the word. The next day, the word had not been found yet. This student observed that the principal has a pattern in the features for the wanted words:

- The word should have **n** vowels, may be repeated, for example: in "engineering", n = 5.
    
- The word should have **m** consonants, may be repeated also: in "engineering", m = 6.
    
- The word should not have some forbidden letters (in an array), forbid_letters
    

You will be provided with a list of words, WORD_LIST(python/crystal), wordList(javascript), wordList (haskell), $word_list(ruby), and you have to create the function, `wanted_words()`, that receives the three arguments in the order given above, `wanted_words(n, m, forbid_list)`and output an array with the word or an array, having the words in the order given in the pre-loaded list, in the case of two or more words were found.

Let's see some cases:

```javascript
wantedWords(1, 7, ["m", "y"]) == ["strength"]
wantedWords(3, 7, ["m", "y"]) == ['afterwards', 'background', 'photograph', 'successful', 'understand']
```

For cases where no words are found the function will output an empty array.

```javascript
wantedWords(3, 7, ["a", "s" , "m", "y"]) == []
```

Help our student to win this and the next challenges of the school. He needs to sure about a suspect that he has. That many times there are no solutions for what the principal is asking for. All words have its letters in lowercase format.

My answer:
```
function wantedWords(n, m, forbid_let){
    return wordList.filter(word => {
      let chars = word.split(''), vowCount = 0, consCount = 0, forbidden = false
      chars.forEach(letter => {
        ['a', 'e', 'i', 'o', 'u'].includes(letter) ? vowCount++ : consCount++
        if(forbid_let.includes(letter)) forbidden = true
      })
      
      if(vowCount === n && consCount === m && forbidden === false){
        return word
        }
    })
}
```
Iterate over every word with filter(). Split each word into individual characters. Check each character if it's a vowel - updating a vowel/consonant count accordingly - AND checking if it includes forbidden letters. If the vowels/cons/forbidden = false match then add this word to the array to be returned.  Time complexity is O(N * W * (1 + F)) where W is word and F is the forbidden letters. 

Another answer with optimized time complexity ( O(N  W))
```
function wantedWords(n, m, forbid_let) {
  const vowels = new Set(['a', 'e', 'i', 'o', 'u']);
  const forbiddenLetters = new Set(forbid_let);

  return wordList.filter(word => {
    let vowCount = 0, consCount = 0, forbidden = false;

    for (const letter of word) {
      if (forbiddenLetters.has(letter)) {
        forbidden = true;
        break; // Early exit if forbidden letter found
      }
      vowels.has(letter) ? vowCount++ : consCount++;
    }

    return vowCount === n && consCount === m && !forbidden;
  });
}
```
Optimizations here: using set guarantees a O(1) since .includes() will search through the array until it finds a match: best case O(1), worst case O(5). We use a for of loop instead of array.forEach() allowing for an early exit upon finding a forbidden letter and to avoid split('') and forEach(). This is faster/more efficient code.

Modern JS engines (V8, spidermonkey, etc) are optimized for string iteration. Performance difference is negligible (less than 1% in benchmarks) Therefore string iteration is fine for 99% of cases, and the algo choice (set vs array) matters far more.

Hyper-optimized version:
```
function wantedWords(n, m, forbid_let) {
  const vowels = new Set(['a','e','i','o','u']);
  const useSet = forbid_let.length > 3;
  const forbidden = useSet ? new Set(forbid_let) : forbid_let;
  
  return wordList.filter(word => {
    let v = 0, c = 0, bad = false;
    for (let i = 0; i < word.length; i++) {
      const letter = word[i];
      if (useSet ? forbidden.has(letter) : forbidden.includes(letter)) {
        bad = true;
        break;
      }
      vowels.has(letter) ? v++ : c++;
    }
    return v === n && c === m && !bad;
  });
}
```
Does a check to check if the forbidden letters length is greater than 3. This is because using an array for a length <=3 is more efficient than using a Set, which has overhead. This method gets the best of both worlds, using an array or set when either one is more efficient. 

# Drone Fly-By (7kyu)
You will be given two strings: `lamps` and `drone`. `lamps` represents a row of lamps, currently off, each represented by `x`. When these lamps are on, they should be represented by `o`.

The `drone` string represents the position of the drone `T` (any better suggestion for character??) and its flight path up until this point `=`. The drone always flies left to right, and always begins at the start of the row of lamps. Anywhere the drone has flown, including its current position, will result in the lamp at that position switching on.

Return the resulting `lamps` string. See example tests for more clarity.

my answer:
```
function flyBy(lamps, drone){
  return "o".repeat(Math.min(drone.length, lamps.length) ) + "x".repeat(Math.max(0, (lamps.length - drone.length) ))
}

//o.repeat(drone.length) + x.repeat(lamps.length - drone.length)
```

a more efficient answer: 
```
const flyBy = (lamps, drone) => [...lamps].fill(`o`, 0, drone.length).join(``)
```
1. **`[...lamps]`**
    
    - Converts the `lamps` string into an array of individual characters (e.g., `"xxxx"` becomes `['x', 'x', 'x', 'x']`).
        
2. **`.fill('o', 0, drone.length)`**
    
    - Replaces elements in the array from index `0` up to (but not including) `drone.length` with `'o'`.
        
    - Example: If `drone = "==="` (length 3), the first 3 `'x'`s become `'o'`s.
        
    - If `drone` is longer than `lamps`, it just replaces all `'x'`s with `'o'`s (no error).
        
3. **`.join('')`**
    
    - Combines the array back into a string (e.g., `['o', 'o', 'o', 'x']` becomes `"ooox"`).

Another good answer:
```
const flyBy = (lamps, drone) =>
  `${`o`.repeat(drone.length)}${lamps}`.slice(0, lamps.length);
```
Generate o's of drone length and combine it with the lamps string. "ooooxxxx"
Then truncate the string based on the length of the original lamp string "oooox"

# Sort array by string length (7kyu)
Write a function that takes an array of strings as an argument and returns a sorted array containing the same strings, ordered from shortest to longest.

For example, if this array were passed as an argument:

```javascript
["Telescopes", "Glasses", "Eyes", "Monocles"]
```

Your function would return the following array:

```javascript
["Eyes", "Glasses", "Monocles", "Telescopes"]
```

All of the strings in the array passed to your function will be different lengths, so you will not have to decide how to order multiple strings of the same length.

My answer:
```
function sortByLength (array) {
    return array.sort((a,b) => a.length - b.length)
}
```

# Numbers to Letters (7kyu)
Given an array of numbers (in string format), you must return a string. The numbers correspond to the letters of the alphabet in reverse order: a=26, z=1 etc. You should also account for `'!'`, `'?'` and `' '` that are represented by '27', '28' and '29' respectively.

All inputs will be valid.

My answer:
```
function switcher(x){
  return x.map(n => {
    n = parseInt(n, 10)
    return n === 27 ? '!' :
      n === 28 ? '?' :
      n === 29 ? ' ' :
      String.fromCharCode(123 - n) 
  }).join('')
}
```
Loop over array. Cast string element into a number. Do a check for 27/28/29 special chars. Then takes 123, subtract the current number from it and convert it using ASCII table values. 

Another answer:
```
const switcher = x =>
  x.reduce((pre, val) => pre + `zyxwvutsrqponmlkjihgfedcba!? `[--val], ``);
```
Iterates over the array using .reduce(), adding a new value based on the lookup table. `[--val]` does two things: converts string to number due to preincrement operator and decrements the number by 1 to adjust for zero-based indexing. `--val` is equivalent to `val = val - 1`
- Suppose `val` is `"26"` (a string).
- `--val` is a pre-decrement operation.
    - JavaScript first converts the string `"26"` to the number `26` (because the `--` operator coerces the string to a number).
    - Then, it decrements `26` by `1`, resulting in `25`.
- Now, `[25]` is used to index into the lookup string `'zyxwvutsrqponmlkjihgfedcba!? '`:
    - The character at index `25` is `'a'`.

# String Incrementer (5kyu)
Your job is to write a function which increments a string, to create a new string.

- If the string already ends with a number, the number should be incremented by 1.
- If the string does not end with a number. the number 1 should be appended to the new string.

Examples:

`foo -> foo1`

`foobar23 -> foobar24`

`foo0042 -> foo0043`

`foo9 -> foo10`

`foo099 -> foo100`

_Attention: If the number has leading zeros the amount of digits should be considered._

My answer:
```
function incrementString (strng) {
  //edge cases
  if(!Number.isInteger(Number(strng[strng.length-1]))) return strng + "1";
  
  let numIdx = 0;
  //loop over str from the end
  for(let i = strng.length - 1; i > 0; i--){
    let curr = strng[i].toLowerCase().charCodeAt(0);
    if(curr >= 97 && curr <=122){
      numIdx = i + 1; //add 1 since slicing is start inclusive
      break; //exit loop once index is found
    }
  }
  let numLen = strng.slice(numIdx).length //length of padded zeros
  let num = (Number(strng.slice(numIdx))+ 1).toString() //increment number then cast to str
  num = num.padStart(numLen, "0"); //pad zeros
  return strng.slice(0, numIdx) + num;
}
```

A really elegant solution using regex:
```
const incrementString = strng =>
  strng.replace(/[0-8]?9*$/, val => ++val);
```

# Help the bookseller ! (6kyu)
A bookseller has lots of books classified in 26 categories labeled `A, B, C, ..., Z`. Each book has a _code_ of at least 3 characters. The **1st character** of a code is a capital letter which **defines the book category**.

In the bookseller's stocklist each code is followed by a space and by a positive integer, which indicates the _quantity_ of books of this code in stock.

## Task

You will receive the bookseller's stocklist and a list of categories. Your task is to find the total number of books in the bookseller's stocklist, with the category codes in the list of categories. Note: the codes are in the same order in both lists.

Return the result as a string described in the example below, or as a list of pairs (Haskell/Clojure/Racket/Prolog).

If any of the input lists is empty, return an empty string, or an empty array/list (Clojure/Racket/Prolog).

## Example

```python
# the bookseller's stocklist:
"ABART 20", "CDXEF 50", "BKWRK 25", "BTSQZ 89", "DRTYM 60"

# list of categories: 
"A", "B", "C", "W"

# result:
"(A : 20) - (B : 114) - (C : 50) - (W : 0)"
```

Explanation:

- category `A`: 20 books (`ABART`)
- category `B`: 114 books = 25 (`BKWRK`) + 89 (`BTSQZ`)
- category `C`: 50 books (`CDXEF`)
- category `W`: 0 books

My answer: 
```
function stockList(books, categories) {
  if(books.length === 0 || categories.length === 0) return ""
  
  //intialize object
  let obj = {}
  categories.forEach(ch => obj[ch] = 0)
  
  //iterate over books
  books.forEach(code =>{
    const category = code[0], quant = +code.slice(code.indexOf(' '))   
    if (obj.hasOwnProperty(category)) obj[category] += quant;
  })
  
  //create string from obj and categories
  return categories.map(letter => `(${letter} : ${obj[letter]})`).join(' - ')
}

//create obj using categories
//loop over books, taking the first chr for book title and last chars for number
//loop over obj using [first chr] and add num to it
//loop over obj again using string literals to create formatting
```

Crazy one liner:
```
const stockList = (listOfArt, listOfCat) =>
  listOfArt.length ? listOfCat.map(val => `(${val} : ${listOfArt.reduce((pre, v) => pre + (v[0] === val) * v.split(` `)[1], 0)})`).join(` - `) : ``;
```

# Template Strings (8kyu)
### Task

Your task is to return the correct string using the Template String Feature.

### Input

Two Strings, no validation is needed.

### Output

You must output a string containing the two strings with the word ```' are '```

Reference: [https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/template_strings](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/template_strings)

My answer:
```
var templateStrings = function(noun, adjective) {
  return `${noun} are ${adjective}`
}
```

# Nut Farm (6 kyu)
## Story

It's a pretty relaxing life here at the nut farm.

Most of the time we just sit around looking at our nuts.

But once a year comes harvesting time...

Harvesting nuts is very easy. We just shake the trees and the nuts fall out!

---

As they fall down the nuts might hit branches:

- Sometimes they bounce left.
- Sometimes they bounce right.
- Sometimes they get stuck in the tree and don't fall out at all.

## Legend

- `o` = a nut
- `\` = branch. A nut hitting this branch bounces right
- `/` = branch. A nut hitting this branch bounces left
- `_` = branch. A nut hitting this branch gets stuck in the tree
- `.` = leaves, which have no effect on falling nuts
- `|` = tree trunk, which has no effect on falling nuts
- = empty space, which has no effect on falling nuts

## Kata Task

Shake the tree and count where the nuts land.

**Output** - An array (same width as the tree) which indicates how many nuts fell at each position ^

^ See the example tests

## Notes

- The nuts are always found at the top of the tree
- Nuts do not affect the falling patterns of other nuts
- There are always enough spaces for nuts to fall between branches
- There are no branches at the extreme left/right edges of the tree matrix so it is not possible for a nut to fall "out of bounds"

## Example

```
.o.oooooo.o.o.oooooo.
..\.\.../..\.../..\..
..../..\..../....../.
.....\...././.\..\.\.
...../../././...\....
.../.../..\./.\..\...
./.......\../.\../...
....\..../....././...
.../.\._.\../._../.\.
.\...././....\../.\..
./......././.../../..
         
         
         
         
         
         
101005000020000000040
```

An answer: 
```
var shakeTree = function(tree) {
  const result = Array(tree[0].length).fill(0)
  tree[0].forEach((nut,c) => {
    if (nut === 'o') {
      for (let r = 1; r < tree.length; r++) {
        if (tree[r][c] === '/') c--
        if (tree[r][c] === '\\') c++
        if (tree[r][c] === '_') return
      }
      result[c]++
    }
  })
  return result
}
```

Another answer: 
```
const nuts = a => [ a[0].map( c => Number(c==='o') ) ].concat( a.slice(1) ) ;
```

Another answer:
```
function drop(z,v) {
  let r = Array.from( z, () => 0 );
  for ( let i=0; i in v; i++ )
    if ( v[i]!=='_' )
      r[ i + Number(v[i]==='\\') - Number(v[i]==='/') ] += z[i];
  return r;
}

const shakeTree = tree => nuts(tree).reduce(drop) ;
```

# Multiplication table (6kyu)
Your task, is to create N×N multiplication table, of size provided in parameter.

For example, when given `size` is 3:

```
1 2 3
2 4 6
3 6 9
```

For the given example, the return value should be:

```js
[[1,2,3],[2,4,6],[3,6,9]]
```

My answer:
```
function multiplicationTable(size) {
  return [...Array(size)].map((_, idx) => { 
	const current = idx+1;
    return [...Array(size)].map((_, innerIdx) => current * (innerIdx+1) )
  })
}

//given int, return array of n x n size
//1*1, 1*2, 1*3
//2*1, 2*2, 2*3
//3*1, 3*2, 3*3

//declare new array of size n, using idx to iterate
//[idx+1, idx+1, idx+1] = [1, 2, 3]
//inside each element, i call map again
//current idx+1 * idx+1
//[1 * idx+1, 1 * idx+1, 1 * idx+1] = [1, 2, 3]
```
Spread operator is required because Array(size) creates a **sparse array** (no actual slots, just a `length` property) and .map() skips empty slots. (Tricks like `[...Array(n)]` or `Array(n).fill()` required to force iteration.)

A more concise answer (same as mine):
```
const multiplicationTable = size =>
  [...Array(size)].map((_, idx) => [...Array(size)].map((_, i) => ++i * (idx + 1)));
```

A differing answer using Array.from():
```
const multiplicationTable = size =>
  Array.from({length: size}, (_1, m1) => 
    Array.from({length: size}, (_2, m2) => 
      (m1 + 1) * (m2 + 1)));
```
**`Array.from()`** pre-allocates the array and fills it in a single pass, giving a fully iterable source. 
When you use Array.from(), it expects the first argument to be an array-like object or an iterable. An "array-like object" is specifically defined as an object with:
- A length property that indicates how many elements it contains
- Indexed elements (0, 1, 2, etc.)
- 
If you passed {size}, you'd be creating an object with a property named size instead of length. The Array.from() method wouldn't recognize this as indicating the desired array length.

Another answer using Array.from():
```
const multiplicationTable = length => Array.from( { length }, (_,i) => Array.from( { length }, (_,j) => (i+1)*(j+1) ) ) ;
```
This code is using a shorthand property syntax in JavaScript called "property value shorthand." When you create an object and the variable name matches the property name you want to use, you can write it once instead of twice.

- `{ length }` is equivalent to `{ length: length }`

This works because:

1. The parameter to the function is named `length`
2. You're creating an object with a property that should also be named `length`
3. You want the value of that property to be the value of the `length` parameter


Fastest implementation using for loops:
```
function multiplicationTable(size) {
  const table = new Array(size);
  for (let row = 0; row < size; row++) {
    const currentRow = new Array(size);
    for (let col = 0; col < size; col++) {
      currentRow[col] = (row + 1) * (col + 1);
    }
    table[row] = currentRow;
  }
  return table;
}
```
### **Performance Comparison**

| Method                 | Time Complexity | Notes                            |
| ---------------------- | --------------- | -------------------------------- |
| **Nested `for` loops** | **O(n²)**       | Fastest for large sizes          |
| `Array.from` + `map`   | O(n²)           | Cleaner but slower               |
| Chained `.map()`       | O(n²)           | Slowest due to callback overhead |

# Maximum Length Difference (7kyu)
You are given two arrays `a1` and `a2` of strings. Each string is composed with letters from `a` to `z`. Let `x` be any string in the first array and `y` be any string in the second array.

`Find max(abs(length(x) − length(y)))`

If `a1` and/or `a2` are empty return `-1` in each language except in Haskell (F#) where you will return `Nothing` (None).

#### Example:

```
a1 = ["hoqq", "bbllkw", "oox", "ejjuyyy", "plmiis", "xxxzgpsssa", "xxwwkktt", "znnnnfqknaz", "qqquuhii", "dvvvwz"]
a2 = ["cccooommaaqqoxii", "gggqaffhhh", "tttoowwwmmww"]
mxdiflg(a1, a2) --> 13
```

My answer:
```
function mxdiflg(a1, a2) {
    if (a1.length === 0 || a2.length === 0) return -1
    
    let a1Min = Infinity, a2Min = Infinity
    let a1Max = 0, a2Max = 0
    
    for(str of a1){
      if(str.length < a1Min) a1Min = str.length
      if(str.length > a1Max) a1Max = str.length
    }
  
    for(str of a2){
      if(str.length < a2Min) a2Min = str.length
      if(str.length > a2Max) a2Max = str.length
    }
  
    return Math.max(Math.abs(a1Max - a2Min), Math.abs(a2Max - a1Min))
}
```

Another answer:
```
const mxdiflg = (a1, a2) =>
  a1.reduce((pre, val) => Math.max(pre, a2.reduce((p, v) => Math.max(p, Math.abs(val.length - v.length)), -1)), -1);
```
Brute force solution that compares the length of every string. Time complexity is O(n * m) where n is the length of array a1, and m is the length of array a2.

A more readable version of the answer above:
```
function mxdiflg(a1, a2) {
  if (a1.length === 0 || a2.length === 0) return -1;
  
  let maxDiff = -1;
  
  for (let str1 of a1) {
    for (let str2 of a2) {
      let diff = Math.abs(str1.length - str2.length);
      if (diff > maxDiff) maxDiff = diff;
    }
  }
  
  return maxDiff;
}
```

# The Coupon Code (7kyu)
## Task

Your mission:  
Write a function called `checkCoupon` which verifies that a coupon code is valid and not expired.

A coupon is no more valid on the day **AFTER** the expiration date. All dates will be passed as strings in this format: `"MONTH DATE, YEAR"`.

## Examples:

```javascript
checkCoupon("123", "123", "July 9, 2015", "July 9, 2015")  ===  true
checkCoupon("123", "123", "July 9, 2015", "July 2, 2015")  ===  false
```

My answer:
```
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate){
  return enteredCode === correctCode 
      && new Date(currentDate).getTime() <= new Date(expirationDate).getTime() 
  
}
```
- This version explicitly converts the `Date` objects to their numeric timestamps (milliseconds since Unix epoch) using `.getTime()` before comparing them.
- This is more explicit and avoids any potential ambiguity, though in practice it behaves the same way as the first version when using `<=`.

Another answer: 
```
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate) {
  return enteredCode === correctCode && new Date(currentDate) <= new Date(expirationDate);
}
```
When comparing `Date` objects with `<=`, JavaScript automatically coerces the `Date` objects to their numeric timestamp values (equivalent to `.getTime()`) and then performs the comparison.

# My Language Skills (7kyu)
### Task

You are given a dictionary-like object (implementation may vary by language) containing languages as keys and your corresponding test results as values. Return the list of languages where your score is at least `60`, in descending order of the scores.

Note: the scores will always be unique (so no duplicate values)

### Examples

```
Input object with key-value pairs:
"Java" -> 10, "Ruby" -> 80, "Python" -> 65
Ouput:
[ "Ruby", "Python" ]

Input object with key-value pairs:
"Hindi" -> 60, "Greek" -> 71, "Dutch" -> 93
Output:
[ "Dutch", "Greek", "Hindi" ]

Input object with key-value pairs:
"C++" -> 50, "ASM" -> 10, "Haskell" -> 20
Output:
[ ]
```

My answer: 
```
function myLanguages(results) {
  let highScores = []
  for (const key in results){
    if(results[key] >=60) {
        highScores.push([key, results[key]])
      }
    }
  return highScores.sort((a, b) => b[1] - a[1]).map(lang => lang[0]) 
}

//for(... in) loop has no intermediate array and is therefore more efficient
//add language and score to new array
//sort arr using second value of each element
//map new sorted arr based on the first value of each element
```

Another answer:
```
function myLanguages(results) {
  return Object.keys(results)
  .filter(r => results[r] > 59)
  .sort((a,b) => results[b] - results[a]);
}
```
Get keys, filter them based on value > 59, then call sort, using the keys and results array. Why didn't I think of that? It's much more elegant than stuffing my array with two element arrays per element. Both my and this solution is O(n log n). O(n) looping over the initial array, and then O(log n) for sorting.

# Dominant array elements (7kyu)
An element in an array is dominant if it is greater than all elements to its right. You will be given an array and your task will be to return a list of all dominant elements. For example:

```
solve([1,21,4,7,5]) = [21,7,5] because 21, 7 and 5 are greater than elments to their right. 
solve([5,4,3,2,1]) = [5,4,3,2,1]

Notice that the last element is always included. All numbers will be greater than 0.
```

My answer:
```javascript
function solve(arr) {
  const domArr = []
  checkDominance: for(let i = 0; i < arr.length; i++){
    const current = arr[i]
    for(let j = i + 1; j < arr.length; j++){
	  //skip to next iteration of outer loop
      if(arr[j] >= current) continue checkDominance 
    }
    domArr.push(arr[i]) //only executes if no arr[j] > current is found
  }
  return domArr
}
```
A labeled statement is any statement that is prefixed with an identifier. You can jump to this label using a break or continue statement nested within the labeled statement. checkDominance is a labeled statement intended to continue the loop once the invalid condition is found - a value to the right of the current value is greater or equal to it. This is an inefficient solution O(n^2) time efficiency.

Another answer:
```javascript
const solve = arr =>
  arr.filter((val, idx) => val > Math.max(...arr.slice(++idx)));
```
For each element, it slices into the next index till the end of the array. It's important to pre-increment as idx++ will increment **after** arr.slice() is called. Math.max() is called to find the largest value in this slice. If Math.max() finds a num larger than val, then the current value is not a dominant element and skips it. Otherwise it's added to the return array. 

Claude answer:
```javascript
function solve(arr) {
  if (!arr.length) return []; //empty arr = return empty arr

  let max = arr[arr.length - 1];
  const result = [max]; // Last element is always dominant
  
  // Traverse from right to left
  for (let i = arr.length - 2; i >= 0; i--) {
    if (arr[i] > max) {
      result.unshift(arr[i]);
      max = arr[i];
    }
  }
  
  return result;
}
```
**Time complexity: O(n) and Space Complexity: O(k) where k is the number of dominant elements**
1) Set max value, 'max' to the last element in the array and initialize the result array with aforementioned value. 
2) Loop over the array from right to left, starting at the second to last value. We check if the current element is greater than the max value. If it is then we add the current element to the beginning of the result array and set max to arr[i]

# Two fighters, one winner (7kyu)
Create a function that returns the name of the winner in a fight between two fighters.

Each fighter takes turns attacking the other and whoever kills the other first is victorious. Death is defined as having `health <= 0`.

Each fighter will be a `Fighter` object/instance. See the Fighter class below in your chosen language.

Both `health` and `damagePerAttack` (`damage_per_attack` for python) will be integers larger than `0`. You can mutate the `Fighter` objects.

Your function also receives a third argument, a string, with the name of the fighter that attacks first.

## Example:

```
  declare_winner(Fighter("Lew", 10, 2), Fighter("Harry", 5, 4), "Lew") => "Lew"
  
  Lew attacks Harry; Harry now has 3 health.
  Harry attacks Lew; Lew now has 6 health.
  Lew attacks Harry; Harry now has 1 health.
  Harry attacks Lew; Lew now has 2 health.
  Lew attacks Harry: Harry now has -1 health and is dead. Lew wins.
```

```javascript
function Fighter(name, health, damagePerAttack) {
        this.name = name;
        this.health = health;
        this.damagePerAttack = damagePerAttack;
        this.toString = function() { return this.name; }
}
```

My answer: 
```javascript
function declareWinner(fighter1, fighter2, firstAttacker) {
  let firstPlayerMove = false
  if(firstAttacker === fighter1.name) firstPlayerMove = true
  //console.log(firstAttacker === fighter1.name)
  //console.log(`${fighter1.name} has ${fighter1.health} and deals ${fighter1.damagePerAttack} dmg`)
  //console.log(`${fighter2.name} has ${fighter2.health} and deals ${fighter2.damagePerAttack} dmg`)
  
  while(fighter1.health > 0 && fighter2.health > 0){
    if(firstPlayerMove){
      fighter2.health -= fighter1.damagePerAttack
      console.log(`${fighter1} attacks ${fighter2} for ${fighter1.damagePerAttack}; ${fighter2} now has ${fighter2.health} health`)
      firstPlayerMove = false
    }else{
      fighter1.health -= fighter2.damagePerAttack
      console.log(`${fighter2} attacks ${fighter1} ${fighter2.damagePerAttack}; ${fighter2} now has ${fighter1.health} health`)
      firstPlayerMove = true
    }
  }
  
  return fighter1.health > 0 ? fighter1.name : fighter2.name
}
```

An optimized form of my answer:
```javascript
function declareWinner(fighter1, fighter2, firstAttacker) {
  let attacker = fighter1.name === firstAttacker ? fighter1 : fighter2;
  let defender = attacker === fighter1 ? fighter2 : fighter1;

  while (fighter1.health > 0 && fighter2.health > 0) {
    defender.health -= attacker.damagePerAttack;
    console.log(`${attacker} attacks ${defender}; ${defender} now has ${defender.health} health.`);
    [attacker, defender] = [defender, attacker]; // Swap roles
  }

  return fighter1.health > 0 ? fighter1.name : fighter2.name;
}
```
Instead of using a boolean, attack and defender are declared first, allowing the code to be more readable and concise. We no longer have to write two different log statements or update an attacker flag. 

A mathematically optimized answer:
```javascript
const declareWinner = (fighter1, fighter2, firstAttacker) =>
  (val => val > 0 ? fighter1.name : val < 0 ? fighter2.name : firstAttacker)
  (Math.ceil(fighter1.health / fighter2.damagePerAttack) - Math.ceil(fighter2.health / fighter1.damagePerAttack));
```
 O(1) runtime but does not output the steps. This style is functional programming a programming paradigm that treats computations as evaluation of math functions and avoids changing-state and mutable data -- ideally functions only take inputs and produce outputs, avoiding any internal state changes. 
How the program works:
- (val =>  ternary checks )( computed value passed as `val`) This is an **IIFE** (Immediately Invoked Function Expression). 
- `Math.ceil(fighter1.health / fighter2.damagePerAttack)`= 10/4 = 2.5 = 3 = 3 hits to kill P1
- `Math.ceil(fighter2.health / fighter1.damagePerAttack)`= 5/2 = 2.5 = 3 = 3 hits to kill P2
- `val = (hitsToKillFighter1) - (hitsToKillFighter2)` Val > 0 = P1 wins; Val < 0 = P2 wins; Val === 0; first attacker wins 


equivalent to: 
```javascript
const declareWinner = (fighter1, fighter2, firstAttacker) => {
  const val = Math.ceil(fighter1.health / fighter2.damagePerAttack) - 
              Math.ceil(fighter2.health / fighter1.damagePerAttack);
  
  if (val > 0) return fighter1.name;
  else if (val < 0) return fighter2.name;
  else return firstAttacker; // Tiebreaker
};
```

What is an IIFE? An **IIFE** (Immediately Invoked Function Expression) is an idiom in which a [JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript) [function](https://developer.mozilla.org/en-US/docs/Glossary/Function) runs as soon as it is defined. It is also known as a _self-executing anonymous function_.
```javascript
// standard IIFE
(function () {
  // statements…
})();

// arrow function variant
(() => {
  // statements…
})();

// async IIFE
(async () => {
  // statements…
})();

```
1. A [function _expression_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function). This usually needs to be [enclosed in parentheses](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Grouping) in order to be parsed correctly.
2. Immediately _calling_ the function expression. Arguments may be provided, though IIFEs without arguments are more common.
Example: 
```
f(x) = x + 1  
f(2) → 3
```
```javascript
(x => x + 1)(2)  // Returns 3

```

# The Poet and the Pendulum (7kyu)
## Task

**_Given_** an _array/list [] of n integers_ , **_Arrange_** _them in a way similar to the to-and-fro movement of a Pendulum_

- **_The Smallest element_** of the list of integers , must come _in center position of array/list_.
    
    - **_The Higher than smallest_** , _goes to the right_ .
- **_The Next higher_** number goes _to the left of minimum number_ and So on , in a to-and-fro manner similar to that of a Pendulum.
## Notes

- **_Array/list_** size is _at least **_3_**_ .
    
- In **_Even array size_** , _The minimum element should be moved to (n-1)/2 index_ (considering that indexes start from 0)
    
- **_Repetition_** of numbers in _the array/list could occur_ , So **_(duplications are included when Arranging)_**.
## Input >> Output Examples:

```
pendulum ([6, 6, 8 ,5 ,10]) ==> [10, 6, 5, 6, 8]
```

## **_Explanation_**:

- **_Since_** , `5` is the **_The Smallest element_** of the list of integers , came _in The center position of array/list_
    
- **_The Higher than smallest_** is `6` _goes to the right_ of `5` .
    
- **_The Next higher_** number goes _to the left of minimum number_ and So on .
    
- Remember , **_Duplications are included when Arranging_** , Don't Delete Them .
    
    ---
    

```
pendulum ([-9, -2, -10, -6]) ==> [-6, -10, -9, -2]
```

## **_Explanation_**:

- **_Since_** , `-10` is the **_The Smallest element_** of the list of integers , came _in The center position of array/list_
    
- **_The Higher than smallest_** is `-9` _goes to the right_ of it .
    
- **_The Next higher_** number goes _to the left of_ `-10` , and So on .
    
- Remeber , In **_Even array size_** , _The minimum element moved to (n-1)/2 index_ (considering that indexes start from 0) .
    
    ---
    

```
pendulum ([11, -16, -18, 13, -11, -12, 3, 18]) ==> [13, 3, -12, -18, -16, -11, 11, 18]
```

## **_Explanation_**:

- **_Since_** , `-18` is the **_The Smallest element_** of the list of integers , came _in The center position of array/list_
    
- **_The Higher than smallest_** is `-16` _goes to the right_ of it .
    
- **_The Next higher_** number goes _to the left of_ `-18` , and So on .
    
- Remember , In **_Even array size_** , _The minimum element moved to (n-1)/2 index_ (considering that indexes start from 0) .

My answer:
```
function pendulum(values) {
  const min = Math.min(...values), arr = [min]
  values.sort((a, b) => a - b)
    .filter((n, idx) => {
      if(idx > 0){
        idx % 2 === 0 ? arr.unshift(n) : arr.push(n)
        }
    })
  return arr
}


//6, 6, 8, 5, 10
//5, 6, 6, 8, 10
//0, 1, 2, 3, 4
```
Time complexity: O(log(n)) to sort, then O(n) to iterate over the array and O(n) to unshift(). Unshift() is O(n) because it must shift all existing elements one position to the right and insert the new element at index 0.

Another answer using reduce():
```
const pendulum = values =>
  values.sort((a, b) => a - b).reduce((pre, val) => pre.length % 2 ? [...pre, val] : [val, ...pre], []);
```
Sort from least to greatest, then call reduce() using an empty array as the base. The array is built with modulo using the spread syntax to append the current element to the array  based on odd or even - evens go to the right while odds go to the left. Time complexity is O(n^2). Sort is O(nlogn), reduce is O(n) and [...pre, val]/[val, ...pre] is O(n) in the same way that unshift() is O(n). 

A more efficient solution:
```
function pendulum(values) {
  const sorted = [...values].sort((a, b) => a - b);
  const result = Array(values.length);
  let left = Math.floor((values.length - 1) / 2), right = left + 1;

  values.forEach((n, i) => i%2 ? result[right++] = n : result[left--] = n)

  return result;
}
```
- [...values] copies the array to avoid mutating the original. 
- Pre-allocating space for the array prevents dynamic resizing and is faster than push/unshift - it's O(1). 
- Left and right are defined as index trackers in order to properly place elements.
- The for loop relies on the index to place elements to the left or to the right, using truthy/falsy. 0 = falsy, placed left. 1 = truthy, placed right, and so on and so forth. 
Time complexity: O(n logn). Space complexity: O(n) for results array.

# Translate DNA in 6 frames (5kyu)
In genetics a reading frame is a way to divide a sequence of nucleotides (DNA bases) into a set of consecutive non-overlapping triplets (also called codon). Each of this triplets is translated into an amino-acid during a translation process to create proteins.

In a single strand of DNA you find 3 Reading frames, for example the following sequence:

```
AGGTGACACCGCAAGCCTTATATTAGC
```

will be decompose in:

```
Frame 1: AGG·TGA·CAC·CGC·AAG·CCT·TAT·ATT·AGC
Frame 2: A·GGT·GAC·ACC·GCA·AGC·CTT·ATA·TTA·GC
Frame 3: AG·GTG·ACA·CCG·CAA·GCC·TTA·TAT·TAG·C
```

In a double strand DNA you find 3 more Reading frames base on the reverse complement-strand, given the previous DNA sequence, in the reverse complement ( A-->T, G-->C, T-->A, C-->G). Due to the splicing of DNA strands and the fixed reading direction of a nucleotide strand, the reverse complement gets read from right to left

```
                        AGGTGACACCGCAAGCCTTATATTAGC
Reverse complement:     TCCACTGTGGCGTTCGGAATATAATCG  
reversed reverse frame: GCTAATATAAGGCTTGCGGTGTCACCT
```

You have:

```
Reverse Frame 1: GCT AAT ATA AGG CTT GCG GTG TCA CCT
reverse Frame 2: G CTA ATA TAA GGC TTG CGG TGT CAC CT
reverse Frame 3: GC TAA TAT AAG GCT TGC GGT GTC ACC T
```

You can find more information about the Open Reading frame in wikipedia just [here] ([https://en.wikipedia.org/wiki/Reading_frame](https://en.wikipedia.org/wiki/Reading_frame))

Given the [standard table of genetic code](http://www.ncbi.nlm.nih.gov/Taxonomy/Utils/wprintgc.cgi#SG1):

```
    AAs  = FFLLSSSSYY**CC*WLLLLPPPPHHQQRRRRIIIMTTTTNNKKSSRRVVVVAAAADDEEGGGG
  Base1  = TTTTTTTTTTTTTTTTCCCCCCCCCCCCCCCCAAAAAAAAAAAAAAAAGGGGGGGGGGGGGGGG
  Base2  = TTTTCCCCAAAAGGGGTTTTCCCCAAAAGGGGTTTTCCCCAAAAGGGGTTTTCCCCAAAAGGGG
  Base3  = TCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAGTCAG
```

The tri-nucleotide TTT = F, TTC = F, TTA = L...

So our 6 frames will be translate as:

```
Frame 1: AGG·TGA·CAC·CGC·AAG·CCT·TAT·ATT·AGC
          R   *   H   R   K   P   Y   I   S
         
Frame 2: A·GGT·GAC·ACC·GCA·AGC·CTT·ATA·TTA·GC
             G  D   T   A   S   L   I   L  
            
Frame 3: AG·GTG·ACA·CCG·CAA·GCC·TTA·TAT·TAG·C
             V   T   P   Q   A   L   Y   *
            
Reverse Frame 1: GCT AAT ATA AGG CTT GCG GTG TCA CCT
                  A   N   I   R   L   A   V   S   P

Reverse Frame 2: G CTA ATA TAA GGC TTG CGG TGT CAC CT
                    L   I   *   G   L   R   C   H

Reverse Frame 3: GC TAA TAT AAG GCT TGC GGT GTC ACC T
                     *   Y   K   A   C   G   V   T
            
```

In this kata you should create a function that translates DNA on all 6 frames, this function takes 2 arguments. The first one is the DNA sequence the second one is an array of frame number for example if we want to translate in Frame 1 and Reverse 1 this array will be [1,-1]. Valid frames are 1, 2, 3 and -1, -2, -3.

The translation hash is available for you under a translation hash `$codons` [Ruby] or `codon` [other languages] (for example to access value of 'TTT' you should call $codons['TTT'] => 'F').

The function should return an array with all translation asked for, by default the function do the translation on all 6 frames.

My answer:
```
function translateWithFrame(dna, frames=[1,2,3,-1,-2,-3]){
  const complement = {"A" : "T", "T": "A", "C": "G", "G": "C"}
  const translation = [], dnaArr = dna.split(""),
        cDnaArr = [...dna].map(c => complement[c]).reverse() 
  
  for(let i = 0; i < frames.length; i++){
    let readingFrame = [], start = Math.abs(frames[i]) - 1 
    
    // RF = 1 -> 3
    if(frames[i] > 0){
      for(let j = start; j <= dnaArr.length - 3; j+=3){
        readingFrame.push(codons[dnaArr[j] + dnaArr[j+1] + dnaArr[j+2]])
      }
    }else{ // RF = -1 > -3
      for(let j = start; j <= dnaArr.length - 3; j+=3){
        readingFrame.push(codons[cDnaArr[j] + cDnaArr[j+1] + cDnaArr[j+2]])
      }
    }
    
    translation.push(readingFrame.join("") )
  }
  
  return translation
}
```
Problem solved by breaking it down into smaller steps. 
- First solved translating a single reading frame: Convert str to arr. For() loop: i = 0; i < arr.length i+=3. Call codons on arr[i], arr[i+1], arr[i+2]. Using + is faster than any other method. Push the value given by codons into an array which is joined into a string and pushed into an array that is returned. 
- Second step is to extend to three different reading frames: Add an outer for() that loops over frames parameter. Inside the outer loop and before inner loop, initialize temp arr to place codons in. Define start by calling math.abs() on current frames value and subtract one. (1, -1 correspond to 0; 2, -2 correspond to 1; 3, -3 correspond to 2). This value is used in our inner loop. After the inner loop is done (part 1), push the joined (arr -> str) codons return value to the translation arr to return later.
- Last step is adding reverse complement functionality. Define a dictionary of DNA complement values to use later. While defining translation = empty array, turning the given dna str into an arr, we call map() on dnaArr, using the DNA complement dictionary to get the complement DNA string, and then we reverse it. This variable is called cDnaArr. Add control flow, checking frames[i] value to separate between frames[i] > 0 and <0. In frames[i] < 0, copy the inner loop, substituting dnaArr for the reversed complement. 
Time complexity O(n) * 8 or something like that =>> O(n)

A refactored solution: 
```
function translateWithFrame(dna, frames = [1, 2, 3, -1, -2, -3]) {
  const COMPLEMENT = { "A": "T", "T": "A", "C": "G", "G": "C" };
  const OFR = [], 
        dnaArr = dna.split(""),
        len = dna.length - 3;
        cDnaArr = [...dnaArr].reverse().map(c => COMPLEMENT[c]); 

  for (const frame of frames) {
    const start = Math.abs(frames[i]) - 1,
	      readingFrame = [],
          currentDNA = frame > 0 ? dnaArr : cDnaArr;

    for (let j = start; j <= len; j += 3) {
      readingFrame.push(codons[currentDNA[j] + currentDNA[j+1] + currentDNA[j+2]]);
    }

    translation.push(readingFrame.join(""));
  }

  return OFR;
}
```
The variable currentDNA has a ternary operator to decide which dna array to use in the for() loop, eliminating redundancy. Pre-defining length to avoid unnecessary calls during the loop. The outer loop is converted into a for... of loop to remove unnecessary verbiage and adds clarity at the cost of being slightly less efficient. 

#  Enumerable Magic - Does My List Include This? (8kyu)
Create a method that accepts a list and an item, and returns `true` if the item belongs to the list, otherwise `false`.

Answer:
```
function include(arr, item){
  return arr.includes(item)
}
```

# L1: Bartender, drinks! (8kyu)
Complete the function that receives as input a string, and produces outputs according to the following table:

|Input|Output|
|---|---|
|"Jabroni"|"Patron Tequila"|
|"School Counselor"|"Anything with Alcohol"|
|"Programmer"|"Hipster Craft Beer"|
|"Bike Gang Member"|"Moonshine"|
|"Politician"|"Your tax dollars"|
|"Rapper"|"Cristal"|
|_anything else_|"Beer"|

**Note:** _anything else_ is the default case: if the input to the function is not any of the values in the table, then the return value should be `"Beer"`.

Make sure you cover the cases where certain words do not show up with correct capitalization. For example, the input `"pOLitiCIaN"` should still return `"Your tax dollars"`.

My answer:
```
function getDrinkByProfession(param){
  const lwrcsParam = param.toLowerCase(), 
  obj = {
    "jabroni": "Patron Tequila", 
    "school counselor": "Anything with Alcohol",
    "programmer":  	"Hipster Craft Beer",
    "bike gang member": "Moonshine",
    "politician": "Your tax dollars",
    "rapper": "Cristal",
  }
  return obj[lwrcsParam] ? obj[lwrcsParam] : "Beer"
}
```

A bit more elegant answer:
```
const drinks = {
  "jabroni": "Patron Tequila",
  "school counselor": "Anything with Alcohol",
  "programmer": "Hipster Craft Beer",
  "bike gang member": "Moonshine",
  "politician": "Your tax dollars",
  "rapper": "Cristal"
}

const getDrinkByProfession = profession => drinks[profession.toLowerCase()] || "Beer"
```
Logical OR (||) operator evaluates left side first. If it's undefined then it's falsy, therefore rightside. 

Probably best practice:
```
const getDrinkByProfession = param =>
  ({
    jabroni: `Patron Tequila`,
    'school counselor': `Anything with Alcohol`,
    programmer: `Hipster Craft Beer`,
    'bike gang member': `Moonshine`,
    politician: `Your tax dollars`,
    rapper: `Cristal`,
  })[param.toLowerCase()] || `Beer`;
```
No need to define other variables. Just return the entire thing and call param.lowerCase() on it. If it's falsy, add an OR to call beer. 

# 80's Kids #5: You Can't Do That on Television (7kyu)
If you say any of the following words a large bucket of "water" will be dumped on you: "water", "wet", "wash" This is true for any form of those words, like "washing", "watered", etc.

If you say any of the following phrases you will be doused in "slime": "I don't know", "slime"

If you say both in one sentence, a combination of water and slime, "sludge", will be dumped on you.

Write a function, bucketOf(str), that takes a string and determines what will be dumped on your head. If you haven't said anything you shouldn't have, the bucket should be filled with "air". The words should be tested regardless of case.

Examples:

```javascript
bucketOf("What is that, WATER?!?") -> "water"
bucketOf("I don't know if I'm doing this right.") -> "slime"
bucketOf("You won't get me!") -> "air"
```

My answer:
```
function bucketOf(str) {
  const strLowerCase = str.toLowerCase()
  const wetDict = ["water", "wet", "wash", "washing", "watered"]
  const slimeDict = ["i don't know", "slime"]
  let wetCheck = false, slimeCheck = false
  
  for(let i = 0; i < wetDict.length; i++){
    if(strLowerCase.includes(wetDict[i])){
      wetCheck = true
      break
    }    
  }
  for(let i = 0; i < slimeDict.length; i++){
    if(strLowerCase.includes(slimeDict[i])){
      slimeCheck = true
      break
    }    
  }
  
  return wetCheck && slimeCheck ? "sludge" :
    wetCheck ? "water" :
    slimeCheck  ? "slime" : "air"
  
}

// Make str lowercase
// Define dictionary for wet and slime
// Loop over entirety of str using .includes() for each value of wet and dict
// Break loop early if true and set wetTrue / slimeTrue 
// Return wetTrue/slimeTrue with ternary to return the correct value

```

A more efficient answer using array.some():
```
function bucketOf(str) {
  const lowerStr = str.toLowerCase();
  const hasWater = ["water", "wet", "wash", "washing", "watered"].some(w => lowerStr.includes(w));
  const hasSlime = ["i don't know", "slime"].some(s => lowerStr.includes(s));
  
  return hasWater && hasSlime ? "sludge" :
         hasWater ? "water" :
         hasSlime ? "slime" : "air";
}
```

Array.some() checks an array, testing for a function passed to it. Returns true/false based upon the testing function. 

# Multiplication table for number (8kyu)
Your goal is to return multiplication table for `number` that is always an integer from 1 to 10.

For example, a multiplication table (string) for `number == 5` looks like below:

```
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
4 * 5 = 20
5 * 5 = 25
6 * 5 = 30
7 * 5 = 35
8 * 5 = 40
9 * 5 = 45
10 * 5 = 50
```

My answer:
```
function multiTable(number) {
  return Array.from({length: 10}).map((_,idx) => {
    return `${idx+1} * ${number} = ${(idx+1) * number}`
  }).join('\n')
}
```
# Email Address Obfuscator (7kyu)
Many people choose to obfuscate their email address when displaying it on the Web. One common way of doing this is by substituting the `@` and `.` characters for their literal equivalents in brackets.

Example 1:

```
user_name@example.com
=> user_name [at] example [dot] com
```

Example 2:

```
af5134@borchmore.edu
=> af5134 [at] borchmore [dot] edu
```

Example 3:

```
jim.kuback@ennerman-hatano.com
=> jim [dot] kuback [at] ennerman-hatano [dot] com
```

Using the examples above as a guide, write a function that takes an email address string and returns the obfuscated version as a string that replaces the characters `@` and `.` with `[at]` and `[dot]`, respectively.

> Notes

> - Input (`email`) will always be a string object. Your function should return a string.

> - Change only the `@` and `.` characters.

> - Email addresses may contain more than one `.` character.

> - Note the additional whitespace around the bracketed literals in the examples!

My answer:
```
function obsfuscate(email) {
  let obsEmail = email.split('')
  for(let i = 0; i < obsEmail.length; i++){
    if(obsEmail[i] === '@') obsEmail[i] = " [at] "
    if(obsEmail[i] === '.') obsEmail[i] = " [dot] "
  }
  return obsEmail.join('')
}
```

Another answer using regex:
```
const obfuscate = email =>
  email.replace(`@`, ` [at] `).replace(/\./g, ` [dot] `);
```

# Scrolling Text (7kyu)
Your task is to complete the function which takes a string, and returns an array with all possible rotations of the given string, **in uppercase**.

### Example

`scrollingText("codewars")` should return:

```javascript
[ "CODEWARS",
  "ODEWARSC",
  "DEWARSCO",
  "EWARSCOD",
  "WARSCODE",
  "ARSCODEW"
  "RSCODEWA",
  "SCODEWAR" ]
```

My answer:
```
function scrollingText(text){
  const textArr = Array.from({length: text.length}).fill(text.toUpperCase().repeat(2))
  return textArr.map((word,idx) => word.substring(idx, text.length+idx))
}
          
//given str, return arr
// convert to uppercase, then turn into arr of duplicated strings
//[CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS, CODEWARSCODEWARS]
// text = substring(idx, text.length + idx)
```
Create an array from the text length and then fill it with the doubled string (hi -> hihi).
Call map onto the new array of doubled strings, taking a substring of the index to the length of the original text (2), not to be confused with the length of the doubled string (4). 

# If you can't sleep, just count sheep!! (8kyu)
## Task:

Given a non-negative integer, `3` for example, return a string with a murmur: `"1 sheep...2 sheep...3 sheep..."`. Input will always be valid, i.e. no negative integers.

My answer:
```
var countSheep = function (num){
  return [...Array(num)].map( (_, idx) => `${idx+1} sheep...`).join('')
}
```

Alternate answer using Array.from():
```
const countSheep = length =>
  Array.from({ length }, (_, i) => ++i + ' sheep...').join('')
```
Array.from() can take in a second argument which is a map function. If you try to call .map() on Array.from like I did in the spread operator answer above, it will not work, you must use this syntax.

# Binary to Text (ASCII) Conversion (6kyu)
Write a function that takes in a binary string and returns the equivalent decoded text (the text is ASCII encoded).

Each 8 bits on the binary string represent 1 character on the ASCII table.

The input string will always be a valid binary string.

Characters can be in the range from "00000000" to "11111111" (inclusive)

Note: In the case of an empty binary string your function should return an empty string.

My answer:
```
function binaryToString(binary) {
  let binArr = Array.from( {length: binary.length / 8}, (_, i) => binary.slice(i * 8, (i+1) * 8) )
  console.log(binArr)
  
  return binArr.map(b => String.fromCharCode(parseInt(b, 2)) ).join('')
}

//we take in a binary string and return a string of character values
//psuedocode: split() binary into 8 char chunks, then run parseInt on each element of the resulting array
// return the values and join()
```
binary.slice(i * 8, (i+1) * 8) -> (0, 8), (8, 16), (16, 24) etc. A way of jumping 8 each iteration.
parseInt(b, 2) takes '01100001' and turns it into '75'. 
String.fromCharCode takes '75' and turns it into 'a'. 

Refactored:
```
function binaryToString(binary) {
  return Array
          .from( {length: binary.length / 8 }, (_, i) => binary.slice( i * 8, (i + 1) * 8) )
          .map(b => String.fromCharCode(parseInt(b, 2)) )
          .join('')
}
```

# String to list of integers (7kyu)
Given a string containing a list of integers separated by commas, write the function that takes said string and returns a new array / list containing all integers present in the string, preserving the order.

Please note that there can be one or more consecutive commas whithout numbers, like so:

```javascript
"-1,-2,,,,,,3,4,5,,6"
```

For example

```javascript
"-1,-2,3,-4,-5"   --> [-1,-2,3,-4,-5]
"1,2,3,,,4,,5,,," --> [1,2,3,4,5]
",,,,,,,"         --> []
```

My ans:
```javascript
function stringToIntArray(s){
  return s.split(',')
    .filter(ch => ch !== '')
    .map(ch => Number(ch))
}
```

Best answer:
```javascript
function stringToIntArray(s) {
  return s.split(',').filter(Boolean).map(Number)
}
```
- JavaScript functions are first-class objects, meaning they can be passed around like any other value.
- `Boolean` and `Number` are functions, so they can be used directly as callbacks.
- Equivalent to:
```javascript
.filter(x => Boolean(x))
.map(x => Number(x))
```
1) `s.split(',')` splits the string into an array, including empty strings if there are consecutive commas (e.g., `"1,,2"` becomes `["1", "", "2"]`).
2) `.filter(Boolean)` removes all falsy values (including empty strings `""`), so `["1", "", "2"]` becomes `["1", "2"]`.
3) `.map(Number)` converts the remaining strings to numbers.
```javascript
stringToIntArray("1,,2,3,abc,,"); 
// -> ["1", "", "2", "3", "abc", "", ""] (after split)
// -> ["1", "2", "3", "abc"] (after filter)
// -> [1, 2, 3, NaN] (after map)
```

# Difference of Volumes of Cuboids (8kyu)
In this simple exercise, you will create a program that will take two lists of integers, `a` and `b`. Each list will consist of 3 positive integers above 0, representing the dimensions of cuboids `a` and `b`. You must find the difference of the cuboids' volumes regardless of which is bigger.

For example, if the parameters passed are `([2, 2, 3], [5, 4, 1])`, the volume of `a` is 12 and the volume of `b` is 20. Therefore, the function should return 8.

Your function will be tested with pre-made examples as well as random ones.

**If you can, try writing it in one line of code.**

My answer:
``` javascript
function findDifference(a, b) {
  return Math.abs(a.reduce((total, n) => total * n,1) - b.reduce((total, n) => total * n,1))
}
```

# The Feast of Many Beasts (8kyu)
All of the animals are having a feast! Each animal is bringing one dish. There is just one rule: the dish must start and end with the same letters as the animal's name. For example, the great blue heron is bringing garlic naan and the chickadee is bringing chocolate cake.

Write a function `feast` that takes the animal's name and dish as arguments and returns true or false to indicate whether the beast is allowed to bring the dish to the feast.

Assume that `beast` and `dish` are always lowercase strings, and that each has at least two letters. `beast` and `dish` may contain hyphens and spaces, but these will not appear at the beginning or end of the string. They will not contain numerals.

My ans:
``` javascript
function feast(beast, dish) {
  return beast.slice(0,1) === dish.slice(0,1) && beast.slice(-1) === dish.slice(-1)
}
```

# A wolf in sheep's clothing (8kyu)
Wolves have been reintroduced to Great Britain. You are a sheep farmer, and are now plagued by wolves which pretend to be sheep. Fortunately, you are good at spotting them.

Warn the sheep in front of the wolf that it is about to be eaten. Remember that you are standing **at the front of the queue** which is at the end of the array:

```
[sheep, sheep, sheep, sheep, sheep, wolf, sheep, sheep]      (YOU ARE HERE AT THE FRONT OF THE QUEUE)
   7      6      5      4      3            2      1
```

If the wolf is the closest animal to you, return `"Pls go away and stop eating my sheep"`. Otherwise, return `"Oi! Sheep number N! You are about to be eaten by a wolf!"` where `N` is the sheep's position in the queue.

**Note:** there will always be exactly one wolf in the array.

### Examples

Input: `["sheep", "sheep", "sheep", "wolf", "sheep"]`  
Output: `"Oi! Sheep number 1! You are about to be eaten by a wolf!"`

Input: `["sheep", "sheep", "wolf"]`  
Output: `"Pls go away and stop eating my sheep"`

My answer:
``` javascript
function warnTheSheep(queue) {
  return queue.slice(-1) == "wolf" ? "Pls go away and stop eating my sheep" 
          : `Oi! Sheep number ${queue.reverse().indexOf('wolf')}! You are about to be eaten by a wolf!`
}
```
Hacky solution. Double == because .slice(-1) on a single element array still returns an array and technically ['wolf'] !== 'wolf'. Then since we're at the start of the queue (or the end of the array), call reverse() on queue before looking up the index of 'wolf'. 

Another answer:
```javascript
const warnTheSheep = queue =>
  (val => val ? `Oi! Sheep number ${val}! You are about to be eaten by a wolf!` : `Pls go away and stop eating my sheep`)
  (queue.reverse().indexOf('wolf'));
```
Uses IIFE

# Regular Ball Super Ball (8kyu)
Create a class `Ball`. Ball objects should accept one argument for "ball type" when instantiated.

If no arguments are given, ball objects should instantiate with a "ball type" of "regular."

```javascript
ball1 = new Ball();
ball2 = new Ball("super");

ball1.ballType     //=> "regular"
ball2.ballType     //=> "super"
```

My answer:
```javascript
// var Ball = function(ballType) {
// //   return ballType ? ballType : "regular"
// };

// const Ball = (ballType = "regular") => ballType;

function Ball(ballType) {
  this.ballType = ballType !== undefined ? ballType : "regular";
}

class Ball{
  constructor(ballType = "regular"){
    this.ballType = ballType
  }
}
```
//Parameters: string, can be empty
//Returns: string
//Examples: ball1 = new Ball("soccer") >>> console.log(ball1.ballType) // "soccer"
// ball2 = new Ball('') >>> console.log(ball2.ballType) // "regular"
//Pseudocode: 

The first function does not work because 'undefined' is defined as a truthy string, returning undefined instead of the default of 'regular'. 
The second function does not work with the keyword 'new'. 
The third function works but the four function is best practice when defining a Class.  We pass "regular" as the default value and then define ballType as whatever is passed in. 
# Cuckoo Clock (6kyu)
The cuckoo bird pops out of the cuckoo clock and chimes once on the quarter hour, half hour, and three-quarter hour. At the beginning of each hour (1-12), it chimes out the hour. Given the current time and a number _n_, determine the time when the cuckoo bird has chimed _n_  times.

Input Parameters:  
_initial_time_ - a string in the format "HH:MM", where 1 ≤ HH ≤ 12 and 0 ≤ MM ≤ 59, with leading 0’s if necessary.  
_n_ - an integer representing the target number of chimes, with 1 <= _n_ <= 200.

Return Value: The time when the cuckoo bird has chimed _n_  times - a string in the same format as _initial_time_.

If the cuckoo bird chimes at _initial_time_, include those chimes in the count. If the _n_th chime is reached on the hour, report the time at the start of that hour (i.e. assume the cuckoo finishes chiming before the minute is up).

Example: _"03:38", 19_   should return _"06:00"_.  
Explanation: It chimes once at _"03:45"_, 4 times at _"04:00"_, once each at _"04:15", "04:30", "04:45"_, 5 times at _"05:00"_, and once each at _"05:15", "05:30", "05:45"_. At this point it has chimed 16 times, so the 19th chime occurs when it chimes 6 times at _"06:00"_.

Source: International Collegiate Programming Contest, North Central North American Regional, 2023.

My answer:
```javascript
function cuckooClock(inputTime, chimes) {
    let [hours, minutes] = inputTime.split(":").map(Number)
    let totalChimes = 0
    
    const quarterHourCheck = minutes%15===0
    if(!quarterHourCheck){
      minutes = 15 * Math.ceil(minutes/15) //Round to nearest 15
      if(minutes === 60){
        minutes = 0
        hours++
        if(hours > 12) hours = 1
      }
    }
    
    while(true){
      let currentChimes
      //Chime based on the hour or just once
      currentChimes = minutes===0 ? hours : 1
      
      //Check if chimes parameter is satisfied
      if(totalChimes + currentChimes >= chimes){
        return `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}` 
      }
      
      totalChimes += currentChimes
      
      minutes += 15
      if(minutes===60){
        minutes = 0
        hours++
        if(hours > 12) hours = 1
      }
    }
    
}

//Chimes at 0:25, 0:30, 0:45 and 1:00. At the top of the hour it chimes as many times as the hour, 
//so "04:00" would chime 4 times
//Parameters: String of input time wof HH:MM, 1<=HH<=-12 and 0<=NN<=59, Number of chimes 1<=n<=200
//Returns: A time string of HH:MM
//Examples: 
// console.log(cuckooClock("07:32", 1), "7:30")  // "07:30"
// console.log(cuckooClock("03:38", 19), "6:00") // "06:00"
//3:45 -> 1 (1)
//4:00 -> 4 (5)
//4:15 -> 1 (6)
//4:30 -> 1 (7)
//4:45 -> 1 (8)
//5:00 -> 5 (13)
//5:15 -> 1 (14)
//5:30 -> 1 (15)
//5:45 -> 1 (16)
//6:00 -> 6 (22)
//Psuedocode:
// Formula for chimes = 4*hour + hour
//Start with the hour, adding 15 minute increments each loop
//Subtract 1 from the count n. 
//Check if n is 0, if it is then return the current time. 

/*
const timeString = "15:30"; // 3:30 PM in 24-hour format

// Split into hours and minutes
const [hours, minutes] = timeString.split(':').map(Number);

// Create a Date object (using today's date)
const dateObj = new Date();
dateObj.setHours(hours, minutes, 0, 0); // Set time (seconds & ms = 0)

console.log(dateObj); // Output: e.g., "2023-11-15T15:30:00.000Z"
console.log(dateObj.toLocaleTimeString()); // "3:30:00 PM" (local format)
*/

// const now = new Date(); // Current time
// now.setMinutes(now.getMinutes() + 15);
// console.log(now.toLocaleTimeString()); // e.g., "3:45:00 PM"
```

Another answer:
```javascript
const cuckooClock = (inputTime, chimes) => {
  let [hh, mm] = inputTime.split`:`.map(Number);
  
  mm % 15 || (chimes -= !!mm || hh);
  chimes %= 114; //optimization to simplify chimes
  mm -= mm % 15; //round down to nearest 15 min mark
  
  while (chimes > 0) {
    (mm = (mm + 15) % 60) || (hh = hh % 12 + 1);
    chimes -= !!mm || hh;
  }
  
  return [hh, mm].map(val => `${val}`.padStart(2, '0')).join`:`;
}
```
The line `mm % 15 || (chimes -= !!mm || hh);` is a compact way of saying **"If we're on a quarter hour, subtract either 1 chime (for 15/30/45) or the hour count (for 00)"**
- `mm % 15` checks if minutes are on a quarter hour (0, 15, 30, 45), if so it equals 0 (falsy) else it's non-zero (truthy). **FirstConditional || SecondConditional** -> Evaluate **First Conditional** if left side is **truthy**. If the left side is **falsy** then it evaluates and **returns the Second Conditional**. 
- Thus, if `mm % 15` is falsy, then it evaluates `(chimes -= !!mm || hh)`.
- !mm converts mm to a boolean and negates it (not mm) => 0 -> !0 -> true
- !!mm converts mm to boolean and second ! negates it back to original boolean equiv => 0 -> !0 -> true (second !)=> !true -> false. `chimes -=` will convert 'true' into 1. (numeric context)
The line `chimes % 114` means 'keep only the remainder after diving by 114'. This reduces large chimes values down to their equivalent in one 12-hour cycle and works because a pattern repeats every 12 hours: 3 quarter hours(15, 30, 45) = 36 + full hour mark variable chimes (1-12) = 78 => 114 total chimes.
While loop continues until chimes is <= 0:
- mm = (mm+15) % 60 // [0, 15, 30, 45, 60] becomes [15, 30, 45, 0, 15]
- hh = hh % 12 + 1 // [10, 11, 12] becomes [11, 12, 1]
 
Time efficiency is O(1) after modulo reduction. Very compact, using clever boolean logic and modulo magic. 

# Format to the 2nd (7kyu)
Given some positive integers, I wish to print the integers such that all take up the same width by adding a minimum number of leading zeroes. No leading zeroes shall be added to the largest integer.

For example, given `1, 23, 2, 17, 102`, I wish to print out these numbers as follows:

```
001
023
002
017
102
```

Write a function that takes a variable number of integers and returns the string to be printed out.

My ans:
```javascript
function printNums(...args) {
  if(!args) return ''
  const maxLength = Math.max(...args.map(n => n.toString().length))
  return args.map(n => n.toString().padStart(maxLength, "0") ).join('\n')
}
```

Slightly more efficient answer:
```javascript
function printNums(...args) {
  let maxLength = Math.max(...args).toString().length;
  return args.map((num) => num.toString().padStart(maxLength, "0")).join("\n");
}
```
Getting the max value of args and then casting it to a string and getting the length is far better than calling another map function and calling toString() and .length on each individual element. 

# Highest and Lowest (7kyu)
In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest number.

### Examples

```javascript
highAndLow("1 2 3 4 5"); // return "5 1"
highAndLow("1 2 -3 4 5"); // return "5 -3"
highAndLow("1 9 3 4 -5"); // return "9 -5"
```

### Notes

- All numbers are valid `Int32`, no _need_ to validate them.
- There will always be at least one number in the input string.
- Output string must be two numbers separated by a single space, and highest number is first.

My ans:
```javascript
function highAndLow(numbers){
  const arr = numbers.split(' ')
  let max = Math.max(...arr), min = Math.min(...arr)
  return `${max} ${min}`
}
```

A better answer:
```javascript
function highAndLow(numbers){
  const numbers = numbers.split(' ');
  return `${Math.max(...numbers)} ${Math.min(...numbers)}`;
}
```

# Lario and Muigi Pipe Problem (8kyu)
### Issue

Looks like some hoodlum plumber and his brother has been running around and damaging your stages again.

The `pipes` connecting your level's stages together need to be fixed before you receive any more complaints.

The `pipes` are correct when each `pipe` after the first is `1` more than the previous one.

### Task

Given a list of unique `numbers` sorted in ascending order, return a new list so that the values increment by 1 for each index from the minimum value up to the maximum value (both included).

### Example

`Input: 1,3,5,6,7,8` `Output: 1,2,3,4,5,6,7,8`

My answer:
```javascript
function pipeFix(numbers){
  return Array(numbers[numbers.length-1] - numbers[0] + 1)
        .fill(numbers[0])
        .map((n, idx) => n+idx)
}
```

Another answer:
```javascript
const pipeFix = (numbers) =>
  [...Array(numbers[numbers.length - 1] - numbers[0] + 1)].map((_, idx) => numbers[0] + idx);
```

# Extract the domain name from a URL (5kyu)
Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:

```
* url = "http://github.com/carbonfive/raygun" -> domain name = "github"
* url = "http://www.zombie-bites.com"         -> domain name = "zombie-bites"
* url = "https://www.cnet.com"                -> domain name = cnet"
```

My answer: 
```
function domainName(url){
  let domain = url.startsWith("http") ? url.split("//")[1] : url
  return domain.startsWith("www.") ? domain.split(".")[1] : domain.split(".")[0]
}
```
Apparently my solution does not handle all possible cases. 

A regex solution:
```
const domainName = url =>
  url.replace(/.*\/\/|www.|\..*/g, ``);
```

Another solution:
```
function domainName(url) {
  // Step 1: Remove protocol (http, https, ftp)
  let domain = url;
  if (domain.startsWith("http://")) {
    domain = domain.substring(7);
  } else if (domain.startsWith("https://")) {
    domain = domain.substring(8);
  } else if (domain.startsWith("ftp://")) {
    domain = domain.substring(6);
  }

  // Step 2: Remove "www." if present
  if (domain.startsWith("www.")) {
    domain = domain.substring(4);
  }

  // Step 3: Split by '/' to remove paths, then by '.' to get the main domain
  domain = domain.split('/')[0];  // Remove paths/query strings
  return domain.split('.')[0];     // Get the main domain part
}
```

# Write Number in Expanded Form (6kyu)
You will be given a number and you will need to return it as a string in [Expanded Form](https://www.mathsisfun.com/definitions/expanded-notation.html). For example:

```
   12 --> "10 + 2"
   45 --> "40 + 5"
70304 --> "70000 + 300 + 4"
```

NOTE: All numbers will be whole numbers greater than 0.

My answer:
```
function expandedForm(num) {
  let arr = num.toString().split('')
  return arr
    .map((n, idx) => n.concat("0".repeat(arr.length - idx - 1)) )
    .filter(n => Number(n) !== 0 )
    .join(" + ")
}

//split str into array
//add (str.length - index - 1) zeros to each index
//loop over array, casting each element to Num, if num != 0, then add to new string
//return new string
```
This answer uses string manipulation, converting the number into a string before splitting and making use of the .repeat() string method to add zeroes before casting it back to a num to filter and then joining.

A more efficient answer:
```
const expandedForm = n => n.toString()
                            .split("")
                            .reverse()
                            .map( (a, i) => a * Math.pow(10, i))
                            .filter(a => a > 0)
                            .reverse()
                            .join(" + ");
```
This solution minimizes the str -> num -> str conversions, manipulating the given numbers using Math.pow. Doing this enables us to not have to worry about converting back into a number, instead the logic is simple: filter numbers greater than zero. Only on the final step do we cast it into a string, joining it with " + ". 

# Sum of a sequence (7kyu)
Your task is to write a function which returns the sum of a sequence of integers.

The sequence is defined by 3 non-negative values: **begin**, **end**, **step**.

If **begin** value is greater than the **end**, your function should return **0**. If **end** is not the result of an integer number of steps, then don't add it to the sum. See the 4th example below.

**Examples**

```
2,2,2 --> 2
2,6,2 --> 12 (2 + 4 + 6)
1,5,1 --> 15 (1 + 2 + 3 + 4 + 5)
1,5,3  --> 5 (1 + 4)
```

My answer:
```javascript
const sequenceSum = (begin, end, step) => {
  if(begin > end) return 0
  
  const arr = []
  for(let i = begin; i <= end; i += step){
    arr.push(i)
  }
  
  return arr.reduce((total, n) => total + n, 0)
};
```
I didn't need to reduce at all. A more efficient solution would simply declare an integer and then add to it during the for loop. 

A more efficient answer:
```javascript
const sequenceSum = (begin, end, step) => {
  let sum = 0
  for(let i = begin; i <= end; i += step){
    sum += i
  }
  
  return sum
};
```
This solution doesn't even need a check for begin > end. If(begin > end), it will just return 0. Elegant.

# No oddities here (7kyu)
Write a small function that returns the values of an array that are not odd.

All values in the array will be integers. Return the good values in the order they are given.

My answer:
```javascript
function noOdds( values ){
  return values.filter(n => n % 2 === 0)
}
```

or
```javascript
const noOdds = values => values.filter(n => n % 2 ===0)
```

# Equal Sides Of An Array (6kyu)
You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N.

If there is no index that would make this happen, return `-1`.

### For example:

Let's say you are given the array `{1,2,3,4,3,2,1}`:  
Your function will return the index `3`, because at the 3rd position of the array, the sum of left side of the index (`{1,2,3}`) and the sum of the right side of the index (`{3,2,1}`) both equal `6`.

Let's look at another one.  
You are given the array `{1,100,50,-51,1,1}`:  
Your function will return the index `1`, because at the 1st position of the array, the sum of left side of the index (`{1}`) and the sum of the right side of the index (`{50,-51,1,1}`) both equal `1`.

Last one:  
You are given the array `{20,10,-80,10,10,15,35}`  
At index 0 the left side is `{}`  
The right side is `{10,-80,10,10,15,35}`  
They both are equal to `0` when added. (Empty arrays are equal to 0 in this problem)  
Index 0 is the place where the left side and right side are equal.

Note: Please remember that in most languages the index of an array starts at 0.

### Input

An integer array of length `0 < arr < 1000`. The numbers in the array can be any integer positive or negative.

### Output

The lowest index `N` where the side to the left of `N` is equal to the side to the right of `N`. If you do not find an index that fits these rules, then you will return `-1`.

### Note

If you are given an array with multiple answers, return the lowest correct index.

My answer:
```javascript
function findEvenIndex(arr){
  const totalSum = arr.reduce((sum, n) => sum + n, 0)
  let leftSum = 0 
      
  for(let i = 0; i < arr.length; i++){
    const rightSum = totalSum - leftSum - arr[i]
    if(leftSum === rightSum) return i
    leftSum += arr[i]
  }

  return -1 
}
```

# Sum of Pairs (5kyu)
Given a list of integers and a single sum value, return the first two values (parse from the left please) in order of appearance that add up to form the sum.

If there are two or more pairs with the required sum, the pair whose second element has the smallest index is the solution.

```python
sum_pairs([11, 3, 7, 5],         10)
#              ^--^      3 + 7 = 10
== [3, 7]

sum_pairs([4, 3, 2, 3, 4],         6)
#          ^-----^         4 + 2 = 6, indices: 0, 2 *
#             ^-----^      3 + 3 = 6, indices: 1, 3
#                ^-----^   2 + 4 = 6, indices: 2, 4
#  * the correct answer is the pair whose second value has the smallest index
== [4, 2]

sum_pairs([0, 0, -2, 3], 2)
#  there are no pairs of values that can be added to produce 2.
== None/nil/undefined/Nothing (Based on the language)

sum_pairs([10, 5, 2, 3, 7, 5],         10)
#              ^-----------^   5 + 5 = 10, indices: 1, 5
#                    ^--^      3 + 7 = 10, indices: 3, 4 *
#  * the correct answer is the pair whose second value has the smallest index
== [3, 7]
```

Negative numbers and duplicate numbers can and will appear.

**NOTE:** There will also be lists tested of lengths upwards of 10,000,000 elements. Be sure your code doesn't time out.

My answer: 
```javascript
function sumPairs(ints, s) {
  let sumPairs = { }, min = undefined
  ints.forEach((num, i) => 
    ints.slice(i + 1).forEach((secondNum,idx) => {
      if(num + secondNum === s && (min === undefined || idx < min)){
        sumPairs[idx] = [num, secondNum]
        min = idx
      }
    })
  )
//   console.log(sumPairs, min)
  return sumPairs[min] || undefined 
}
```
O(n^2) solution since it loops twice over the same array. Not very efficient. 

O(n) solution uses a Set to store numbers as you iterate:
```javascript
function sumPairs(arr, s){
  let set = new Set()
  for(const num of arr){
    const complement = s - num
    if(set.has(complement)) return [complement, num]
    set.add(num)
  }
  return undefined
}
```

# Largest pair sum in array (7kyu)
Given a sequence of numbers, find the largest pair sum in the sequence.

For example

```
[10, 14, 2, 23, 19] -->  42 (= 23 + 19)
[99, 2, 2, 23, 19]  --> 122 (= 99 + 23)
```

Input sequence contains minimum two elements and every element is an integer.

My answer:
```javascript
function largestPairSum (numbers) {
  numbers.sort((a, b) => b - a)
  return numbers[0] + numbers[1]
}
```

# Find the stray number (7kyu)
You are given an _odd-length_ array of integers, in which all of them are the same, except for one single number.

Complete the method which accepts such an array, and returns that single different number.

**The input array will always be valid!** (odd-length >= 3)

## Examples

```
[1, 1, 2] ==> 2
[17, 17, 3, 17, 17, 17, 17] ==> 3
```

My answer:
```javascript
function stray(numbers) {
  const count = {}
  numbers.forEach(n => count[n] ? count[n] += 1 : count[n] = 1)
  for (const [key, value] of Object.entries(count)) {
    if(value===1) return +key
  }
}
```
Time complexity: O(n) + 2 = O(n), iterate over array and then over 2 values in Object.
Space complexity O(2) = O(1), store 2 values in Object. 

# Hello, Name or World! (8kyu)
Define a method `hello` that `returns` "Hello, Name!" to a given `name`, or says Hello, World! if name is not given (or passed as an empty String).

Assuming that `name` is a `String` and it checks for user typos to return a name with a first capital letter (Xxxx).

Examples:

```
* With `name` = "john"  => return "Hello, John!"
* With `name` = "aliCE" => return "Hello, Alice!"
* With `name` not given 
  or `name` = ""        => return "Hello, World!"
```

My answer:
```javascript
function hello(name) {
  return name? `Hello, ${name[0].toUpperCase()}${name.substring(1).toLowerCase()}!` : "Hello, World!"
}
```

# Number of People in the Bus (7kyu)
There is a bus moving in the city which takes and drops some people at each bus stop.

You are provided with a list (or array) of integer pairs. Elements of each pair represent the number of people that get on the bus (the first item) and the number of people that get off the bus (the second item) at a bus stop.

Your task is to return the number of people who are still on the bus after the last bus stop (after the last array). Even though it is the last bus stop, the bus might not be empty and some people might still be inside the bus, they are probably sleeping there :D

Take a look on the test cases.

Please keep in mind that the test cases ensure that the number of people in the bus is always >= 0. So the returned integer can't be negative.

The second value in the first pair in the array is 0, since the bus is empty in the first bus stop.

My answer:
```javascript
var number = function(busStops){
  return busStops.reduce((total, stop) => total += stop[0] - stop[1], 0)
}
```

Use destructuring to unpack [a,b] = [10, 0] for readability:
```
const number = (busStops) => busStops.reduce((rem, [on, off]) => rem + on - off, 0);
```

# Remove First and Last Character Part Two (8kyu)
You are given a string containing a sequence of character sequences separated by commas.

Write a function which returns a new string containing the same character sequences except the first and the last ones but this time separated by spaces.

If the input string is empty or the removal of the first and last items would cause the resulting string to be empty, return an empty value (represented as a generic value `NULL` in the examples below).

## Examples

```
"1,2,3"      =>  "2"
"1,2,3,4"    =>  "2 3"
"1,2,3,4,5"  =>  "2 3 4"

""     =>  NULL
"1"    =>  NULL
"1,2"  =>  NULL
```

My answer:
```javascript
function array(string) {
  let arr = string.split(',')
  return arr.length <= 2 ?  null : arr.slice(1, arr.length-1).join(' ')
}
```

One liner:
```javascript
function array(arr){
  return arr.split(",").slice(1,-1).join(" ") || null;
}
```

# Remove First and Last Character (8kyu)
It's pretty straightforward. Your goal is to create a function that removes the first and last characters of a string. You're given one parameter, the original string. You don't have to worry about strings with less than two characters.

My answer: 
```
function removeChar(str){
  return str.split('').slice(1, -1).join('')
}
```

Simpler:
```
function removeChar(str) {
  return str.slice(1, -1);
}
```

# Welcome to the City (8kyu)
Create a method that takes as input a name, city, and state to welcome a person. Note that `name` will be an array consisting of one or more values that should be joined together with one space between each, and the length of the `name` array in test cases will vary.

Example:

```
['John', 'Smith'], 'Phoenix', 'Arizona'
```

This example will return the string `Hello, John Smith! Welcome to Phoenix, Arizona!`

My ans:
```javascript
function sayHello( name, city, state ) {
   return `Hello, ${name.join(" ")}! Welcome to ${city}, ${state}!`
}

```

# Find the capitals (7kyu)
## Instructions

Write a function that takes a single non-empty string of only lowercase and uppercase ascii letters (`word`) as its argument, and returns an ordered list containing the indices of all capital (uppercase) letters in the string.

## Example (Input --> Output)

```
"CodEWaRs" --> [0,3,4,6]
```

My answer:
```javascript
var capitals = function (word) {
  return word.split('').reduce((arr, ch, i) => {
    if(ch === ch.toUpperCase() ) arr.push(i)
    return arr
  },[])
};
```

Another ans:
```javascript
const capitals = word =>
  [...word].reduce((pre, val, idx) => /[A-Z]/.test(val)? [...pre, idx] : pre, []);
```

# Meeting (6kyu)
John has invited some friends. His list is:

```
s = "Fred:Corwill;Wilfred:Corwill;Barney:Tornbull;Betty:Tornbull;Bjon:Tornbull;Raphael:Corwill;Alfred:Corwill";
```

Could you make a program that

- makes this string uppercase
- gives it sorted in alphabetical order by last name.

When the last names are the same, sort them by first name. Last name and first name of a guest come in the result between parentheses separated by a comma.

So the result of function `meeting(s)` will be:

```
"(CORWILL, ALFRED)(CORWILL, FRED)(CORWILL, RAPHAEL)(CORWILL, WILFRED)(TORNBULL, BARNEY)(TORNBULL, BETTY)(TORNBULL, BJON)"
```

It can happen that in two distinct families with the same family name two people have the same first name too.

My answer:
```javascript
function meeting(s) {
  const alpha = new Array(26).fill().map(() => [])
  let finalStr = []
  
  s.toUpperCase().split(';').forEach(name => {
      const [firstName, lastName] = name.split(':')
      const slot = lastName.charCodeAt(0) - 'A'.charCodeAt(0)
      alpha[slot].push(`${lastName}, ${firstName}`)
    })

  alpha.forEach(slot => {
    if(slot.length > 0){
      slot.sort()
      finalStr.push(...slot)
    }
  })
  
	return `(${finalStr.join(')(')})`
}
```

A far more efficient/simplified function:
```javascript
function meeting(s) {
  let string = s.toUpperCase().split(';')
                .map(x => x.split(':').reverse().join(', '))
                .sort()
                .join(')(')
  return '(' + string + ')'
}
```

# Find the odd int (6kyu)
Given an array of integers, find the one that appears an odd number of times.
There will always be only one integer that appears an odd number of times.
### Examples

`[7]` should return `7`, because it occurs 1 time (which is odd).  
`[0]` should return `0`, because it occurs 1 time (which is odd).  
`[1,1,2]` should return `2`, because it occurs 1 time (which is odd).  
`[0,1,0,1,0]` should return `0`, because it occurs 3 times (which is odd).  
`[1,2,2,3,3,3,4,3,3,3,2,2,1]` should return `4`, because it appears 1 time (which is odd).

My answer:
```javascript
function findOdd(A) {
  return +Object.entries(A
      .reduce((obj, n) => {
        obj[n] =  (obj[n] || 0) + 1
        return obj
      }, {})
     )          
    .find( ([key, value]) => value % 2 !==0)?.[0]
}
```
1) Loop over each number, either creating a value in the object or incrementing it by one. 
2) Use Object.entries() to convert to array.
3) .find() searches for the first value that is odd, using optional chaining to grab the key.
4) Cast it to a num before returning
Time Complexity: O(3n) = O(n)
Space complexity: O(n) 

A better and more succinct answer:
```javascript
const findOdd = (xs) => xs.reduce((a, b) => a ^ b);
```
XOR operator returns 1 if the bits are different, 0 if they are the same. e.g. 5 ^ 5 = 0, 7 ^ 0 = 7
XOR-ing all numbers:

- Pairs of identical numbers cancel out (`n ^ n = 0`)
- `0 ^ oddNumber = oddNumber`

So by the end, you're left with only the number that appears an odd number of times.
```
Given [1, 1, 2, 2, 3, 3, 5]: 
a = 0 initially (default reduce accumulator)
0 ^ 1 = 1
1 ^ 1 = 0
0 ^ 2 = 2
2 ^ 2 = 0
0 ^ 3 = 3
3 ^ 3 = 0
0 ^ 5 = 5 ✅
```

# What's the real floor (8kyu)
Americans are odd people: in their buildings, the first floor is actually the ground floor and there is no 13th floor (due to superstition).

Write a function that given a floor in the american system returns the floor in the european system.

With the 1st floor being replaced by the ground floor and the 13th floor being removed, the numbers move down to take their place. In case of above 13, they move down by two because there are two omitted numbers below them.

Basements (negatives) stay the same as the universal level.

[More information here](https://en.wikipedia.org/wiki/Storey#European_scheme)

## Examples

```
1  =>  0 
0  =>  0
5  =>  4
15  =>  13
-3  =>  -3
```

My ans:
```javascript
function getRealFloor(n) {
  return n <= 0 
          ? n  : n <= 13 
          ? n - 1 : n - 2
}
```

# The 'if' function (8kyu)
Create a function called `_if` which takes 3 arguments: a value `bool` and 2 functions (which do not take any parameters): `func1` and `func2`

When `bool` is truthy, `func1` should be called, otherwise call the `func2`.

### Example:

```javascript
_if(true, function(){console.log("True")}, function(){console.log("false")})
// Logs 'True' to the console.
```

My answer:
```javascript
function _if(bool, func1, func2) {
  return bool ? func1() : func2()
}
```

# Bin to Decimal (8kyu)
Complete the function which converts a binary number (given as a string) to a decimal number.

ANSWER:
```javascript
function binToDec(bin){
  return parseInt(bin,2);
}
```

# Check the exam (7kyu)
The first input array is the key to the correct answers to an exam, like `["a", "a", "b", "d"]`. The second one contains a student's submitted answers.

The two arrays are not empty and are the same length. Return the score for this array of answers, giving `+4` for each correct answer, `-1` for each incorrect answer, and `+0` for each blank answer, represented as an empty string (in C the space character is used).

If the score < 0, return `0`.

For example:

```
    Correct answer    |    Student's answer   |   Result         
 ---------------------|-----------------------|-----------
 ["a", "a", "b", "b"]   ["a", "c", "b", "d"]  →     6
 ["a", "a", "c", "b"]   ["a", "a", "b", "" ]  →     7
 ["a", "a", "b", "c"]   ["a", "a", "b", "c"]  →     16
 ["b", "c", "b", "a"]   ["" , "a", "a", "c"]  →     0
```

My answer:
```javascript
function checkExam(array1, array2) {
  return Math.max(
    array1.reduce((total, answer, i) => {
      answer === "" || array2[i] === "" ? total += 0 :
      answer === array2[i] ? total += 4 : total -= 1
      return total
      }, 0)
    , 0)
}
```

Another answer:
```javascript
const checkExam = (array1, array2) =>
  Math.max(array2.reduce((pre, val, idx) => val ? val === array1[idx] ? pre + 4 : --pre : pre, 0), 0);
```

# Deodorant Evaporator (7kyu)
This program tests the life of an evaporator containing a gas.

We know the content of the evaporator (content in ml), the percentage of foam or gas lost every day (evap_per_day) and the threshold (threshold) in percentage beyond which the evaporator is no longer useful. All numbers are strictly positive.

The program reports the nth day (as an integer) on which the evaporator will be out of use.

#### Example:

```
evaporator(10, 10, 5) -> 29
```

#### Note:

Content is in fact not necessary in the body of the function "evaporator", you can use it or not use it, as you wish. Some people might prefer to reason with content, some other with percentages only. It's up to you but you must keep it as a parameter because the tests have it as an argument.

My ans:
```javascript
function evaporator(content, evapPerDay, threshold) {
  let count = 0, total = 100
  while(total >= threshold){
    total = total - (total*evapPerDay/100)
    count++
  }
  
  return count
}
```

Slightly better:
```javascript
const evaporator = (content, evap_per_day, threshold) => {
  let day = 0;
  for (let vol = 100; vol >= threshold; vol *= 1 - evap_per_day / 100) {
    day++;
  }
  
  return day;
}
```

# How many stairs will Suzuki climb in 20 years? (8kyu)
Suzuki is a monk who climbs a large staircase to the monastery as part of a ritual. Some days he climbs more stairs than others depending on the number of students he must train in the morning. He is curious how many stairs might be climbed over the next 20 years and has spent a year marking down his daily progress.

The sum of all the stairs logged in a year will be used for estimating the number he might climb in 20.

20_year_estimate = one_year_total * 20

You will receive the following data structure representing the stairs Suzuki logged in a year. You will have all data for the entire year so regardless of how it is logged the problem should be simple to solve.

```
stairs = [sunday,monday,tuesday,wednesday,thursday,friday,saturday]
```

Make sure your solution takes into account all of the nesting within the stairs array.

Each weekday in the stairs array is an array.

```
sunday = [6737, 7244, 5776, 9826, 7057, 9247, 5842, 5484, 6543, 5153, 6832, 8274, 7148, 6152, 5940, 8040, 9174, 7555, 7682, 5252, 8793, 8837, 7320, 8478, 6063, 5751, 9716, 5085, 7315, 7859, 6628, 5425, 6331, 7097, 6249, 8381, 5936, 8496, 6934, 8347, 7036, 6421, 6510, 5821, 8602, 5312, 7836, 8032, 9871, 5990, 6309, 7825]
```

Your function should return the 20 year estimate of the stairs climbed using the formula above.

My answer:
```javascript
function stairsIn20(s){
  let total = 0
  s.forEach(day => {
    day.forEach(step => total += step)
  })
  return total * 20 
}
```

# Training JS #7: if..else and ternary operator
Complete function `saleHotdogs`/, function accepts 1 parameter:`n`, n is the number of hotdogs a customer will buy, different numbers have different prices (refer to the following table), return how much money will the customer spend to buy that number of hotdogs.

My answer:
```javascript
function saleHotdogs(n){
  return (n < 5) ? 100 * n :
    (n >= 5 && n < 10) ? 95 * n : 90 * n
}
```

# Reversed Sequences (8kyu)
Build a function that returns an array of integers from n to 1 where `n>0`.

Example : `n=5` --> `[5,4,3,2,1]`

My answer:
```javascript
const reverseSeq = n => {
  return Array.from({length: n}, (v, i) => i + 1).reverse()
};
```

took this from MDN:
```javascript
// Using an arrow function as the map function to
// manipulate the elements
Array.from([1, 2, 3], (x) => x + x);
// [2, 4, 6]

// Generate a sequence of numbers
// Since the array is initialized with `undefined` on each position,
// the value of `v` below will be `undefined`
Array.from({ length: 5 }, (v, i) => i);
// [0, 1, 2, 3, 4]
```

# Strings, strings, strings (Easy) (7kyu)
The `toString()` method has been disabled for `boolean`s, `number`s, `array`s and `object`s. Your goal is to retrive `toString()` for the following data types.
### I. Booleans

For booleans:

1. `true` should be converted to `"true"`
2. `false` should be converted to `"false"`

### II. Numbers

For numbers, conversion should be as follows:

```javascript
// e.g.
(3).toString() === "3"
(3.14).toString() === "3.14"
(-78).toString() === "-78"
Math.PI.toString() === "3.141592653589793"
```

### III. Arrays

For the purposes of this Kata, you will only be expected to convert arrays with **numbers only** into strings. However, on top of fixing it, we would also like to **improve** it as well. We would like to **keep** the square brackets (`[]`) around the "stringified" array as it would be seen in Javascript code. For example:

```javascript
// e.g.
[].toString() === "[]"
[1].toString() === "[1]"
[2,4,8,17].toString() === "[2, 4, 8, 17]"
[Math.PI, Math.E].toString() === "[3.141592653589793,2.718281828459045]"
```

As you may have noticed in the examples above, when the array has more than one element, some of the strings have spaces as well as commas separating each item but some strings do not. For the purposes of this Kata **whether there are whitespaces or not does not matter for stringified arrays** - before conducting the tests your input is stripped of all whitespace.

## Final Note - IMPORTANT

Your recovered `toString()` methods should only `return` the stringified version of the input - it should **NOT** alter the original value. Test cases have been created to confirm this.

Answer:
```javascript
String.prototype.toString = function(){
  return `${this}`
}
```
# Formatting decimal places #0 (8kyu)
Each number should be formatted that it is rounded to two decimal places. You don't need to check whether the input is a valid number because only valid numbers are used in the tests.

```
Example:    
5.5589 is rounded 5.56   
-3.3424 is rounded -3.34
```

My answer:
```javascript
function twoDecimalPlaces(n) {
  return +n.toFixed(2)
}
```
# Factorial (7kyu)
In mathematics, the factorial of a non-negative integer n, denoted by n!, is the product of all positive integers less than or equal to n. For example: 5! = 5 * 4 * 3 * 2 * 1 = 120. By convention the value of 0! is 1.

Write a function to calculate factorial for a given input. If input is below 0 or above 12 throw an exception of type `ArgumentOutOfRangeException` (C#) or `IllegalArgumentException` (Java) or `RangeException` (PHP) or throw a `RangeError` (JavaScript) or `ValueError` (Python) or return `-1` (C).

More details about factorial can be found [here](https://www.wikiwand.com/en/Factorial).

My answer:
```javascript
function factorial(n){
  if(n < 0 || n > 12) throw new Error("RangeError")
  return Array.from({length: n}, (_, i) => i + 1).reduce((total, n) => total * n, 1)
}
```

# Find the middle element (7kyu)
Create a function that when provided with a triplet, returns the index of the numerical element that lies between the other two elements.

The input to the function will be an array of three distinct numbers (Haskell: a tuple).

For example:

```
gimme([2, 3, 1]) => 0
```

_2_ is the number that fits between _1_ and _3_ and the index of _2_ in the input array is _0_.

Another example (just to make sure it is clear):

```
gimme([5, 10, 14]) => 1
```

_10_ is the number that fits between _5_ and _14_ and the index of _10_ in the input array is _1_.

My answer:
```javascript
function gimme (triplet) {
  const max = Math.max(...triplet), min = Math.min(...triplet)
  let index
  for(let i = 0; i < triplet.length; i++){
    if(triplet[i] !== max && triplet[i] !== min) index = i
  }
  return index
}
```

Another answer:
```javascript
function gimme(a) {
  return a.indexOf(a.slice().sort(function(a, b) { return a - b })[1])
}
```
slice() duplicates the array so sort will not modify the original
# Your order, please (6kyu)
Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.

Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).

If the input string is empty, return an empty string. The words in the input String will only contain valid consecutive numbers.

## Examples

```
"is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
"4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
""  -->  ""
```

My answer:
```javascript
function order(words){
  //split into arr, wordArr
  //new array, orderedArr
  //loop over wordArr, pushing to index
  //return joined orderedArr
  const wordArr = words.split(' ')
  const orderedArr = new Array(wordArr.length)
  wordArr.forEach(w => {
    let idx = Number(w.split('').filter(ch => !isNaN(ch)))
    orderedArr[idx - 1] = w
  })
  return orderedArr.join(' ')
}
```

# Hex to Decimal (8 kyu)
Complete the function which converts hex number (given as a string) to a decimal number.

My answer:
```javascript
function hexToDec(hexString){
  return parseInt(hexString, 16)
}
```

# Simple multiplication (8kyu)
This kata is about multiplying a given number by eight if it is an even number and by nine otherwise.

My answer:
```javascript
function simpleMultiplication(number) {
    return number % 2 === 0 ? number * 8 : number * 9
}
```

# Convert to Binary (8kyu)
Given a non-negative integer `b`, write a function which returns an integer `d` such that the _binary_ representation of `b` is the same as the _decimal_ representation of `d`.

Examples:

```
n = 1 should return 1
n = 5 should return 101
n = 11 should return 1011
```

My answer:
```javascript

```