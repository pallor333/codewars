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