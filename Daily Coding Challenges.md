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
# Find the next integral perfect square****
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
- replace() returns a new string with one, some, or all matches of a `pattern` replaced by a `replacement`
- `/[^aeiou]/` is a regular expression that matches any character that is **not** a lowercase or uppercase vowel (a, e, i, o, u).
- The `^` inside the square brackets means "negate" the character class, so it matches any character **except** vowels.
- The `gi` flags mean:
	- `g`: Global search (replace all occurrences).
	- `i`: Case-insensitive search.
- `.replace(..., '')` replaces all matched characters (non-vowels) with an empty string, effectively removing them.
Therefore, this replace() returns ONLY vowels. 

The same is repeated for consonants, and by returning the length we get the proper num of vowels/consonants.