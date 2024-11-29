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