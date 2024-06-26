# javascript-guide

Javascript programming language guidelines/notebook

# Javascript Core Basics

## Variables and Data Types

## Variables: 
Containers for storing data values.
```javascript
var name = 'Alice';    // ES5
let age = 25;          // ES6
const isStudent = true; // ES6
```
Refer to Hoisting to know more about variable differences. [Hoisting](https://github.com/kaleeswariP/javascript-guide/edit/master/README.md#8-hoisting)


## Data Types: 
JavaScript supports various data types, including:

* **Primitive:** `string`, `number`, `boolean`, `null`, `undefined`, `symbol` `(ES6)`, `bigint` `(ES11)`.
* **Non-primitive:** `object`, `array`, `function`.

You can refer to call by value and call by difference to know the difference between data types.[Call by value and call by reference](https://github.com/kaleeswariP/javascript-guide/edit/master/README.md#9-call-by-value-and-call-by-difference)

## Operators

* **Arithmetic Operators:** `+`, `-`, `*`, `/`, `%`, `++`, `--`.
* **Comparison Operators:** `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`.
* **Logical Operators:** `&&`, `||`, `!`.

## Control Structures

### **Conditionals:** 
`if`, `else if`, `else`, `switch`.
```javascript
if (age > 18) {
  console.log('Adult');
} else {
  console.log('Minor');
}
```
### **Loops:**
`for`, `while`, `do...while`, `for...of` `(ES6)`, `for...in`.

#### `for ...in` loop

**Purpose:** The for...in loop is used to iterate over the enumerable properties of an object (including inherited properties).

**Usage:** It is commonly used to loop through the properties of an object.

**Iterates Over:** <strong>Keys (property names) of the object.</strong>

Example
```javascript
const person = { name: 'Alice', age: 25, city: 'New York' };

for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}
```
#### `for ...of` loop

**Purpose:** The `for...of` loop is used to iterate over iterable objects (like arrays, strings, maps, sets, etc.).

**Usage:** It is commonly used to loop through the values of an iterable object.

**Iterates Over:**  <strong>Values of the iterable.</strong>

**Remember strings are also iterable objects so you can use ```for ...of``` to iterate string** Refer - [String](https://github.com/kaleeswariP/javascript-guide/edit/master/README.md#strings)


### Loop-breaking statements
loop breaking statements are used to alter the flow of loop iterations.

Two primary statements are used for this purpose: `break` and `continue`.  
#### `break` statement
The `break` statement is used to terminate the loop immediately, regardless of the iteration count or condition. 

When a `break` statement is encountered inside a loop, the loop stops executing, and the control is transferred to the statement immediately following the loop.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break; // Exit the loop when i equals 5
  }
  console.log(i);
}
```
#### `continue` Statement
The `continue` statement is used to skip the current iteration of the loop and move to the next iteration.

When a `continue` statement is encountered, the loop continues with the next iteration, bypassing the remaining code inside the loop for the current iteration.

```javascript
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    continue; // Skip even numbers
  }
  console.log(i);
}
```
#### Nested loops
In nested loops, `break` and `continue` only affect the loop they are in. To break out of an outer loop, you can use labeled statements.

**Labeled Statements:** Allow breaking out of or continuing specific loops in nested loop structures

```javascript
outerLoop: for (let i = 0; i < 3; i++) { // labeled statement
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) {
      break outerLoop; // Exit both loops
    }
    console.log(`i = ${i}, j = ${j}`);
  }
}

```

## Functions

**Function Declaration**
```javascript
function greet(name) {
  return 'Hello, ' + name;
}
```
**Function Expression**
```javascript
const greet = function(name) {
  return 'Hello, ' + name;
};
```
**Arrow functions`(ES6)`**
```javascript
const greet = (name) => 'Hello, ' + name;
```

## Objects and arrays
* **Objects:** Collections of key-value pairs.

```javascript
`const user = {
  name: 'Alice',
  age: 25,
  greet: function() {
    return 'Hello, ' + this.name;
  }
};
console.log(user.greet()); // Hello, Alice
```
* **Arrays:** Ordered collections of values.

```javascript
`const numbers = [1, 2, 3, 4, 5];
console.log(numbers[0]); // 1
```

## Asynchronous JavaScript
### Callbacks: 
Functions passed as arguments to other functions.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback('Data loaded');
  }, 1000);
}
fetchData(data => console.log(data));
```
### Promises: 
Represent future values or errors.

```javascript
`const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Data loaded'), 1000);
});
promise.then(data => console.log(data));
```
### Async/Await (ES8): 
Syntactic sugar for working with Promises.

```javascript
async function fetchData() {
  const data = await promise;
  console.log(data);
}
fetchData();
```
Refer [Callbacks-promises-asyncs-await](https://github.com/kaleeswariP/javascript-guide/edit/master/README.md#7-callback-promises-and-async-await)

## Strings
A string is a sequence of characters used to represent text. Strings are one of the fundamental data types in JavaScript<br>

**Declaration:** Strings can be declared using single quotes (') or double quotes (").<br>

**String Methods:** JavaScript provides a variety of built-in methods to manipulate strings, such as toUpperCase(), toLowerCase(), charAt(), substring(), slice(), indexOf(), replace(), trim(), split(), etc.<br>

**Template Literals:** Introduced in ES6, template literals allow for more flexible string formatting and interpolation(process of inserting something into something else) using backticks `() and ${}` placeholders.<br>

Refer - [string related tasks](https://github.com/kaleeswariP/javascript-guide/edit/master/README.md#6-string-related-tasks)

## Dates Handling
Date functions are methods that allow you to work with dates and times. These functions are part of the built-in Date object in JavaScript.<br>
Refer - [Date related tasks]()

### **Creating a Date Object:**
`new Date()`: Creates a new Date object representing the current date and time.<br>

`new Date(milliseconds)`: Creates a new Date object from the number of milliseconds since January 1, 1970, 00:00:00 UTC (the Unix Epoch).<br>

`new Date(dateString)`: Creates a new Date object from a date string.<br>

`new Date(year, month, day, hours, minutes, seconds, milliseconds)`: Creates a new Date object with the specified date and time components.<br>

### **Getting Date Components:**
`getDate(), getMonth(), getFullYear()`: Get the day of the month, month (0-11), and year, respectively.<br>

`getDay()`: Get the day of the week (0-6, where 0 is Sunday).<br>

`getHours(), getMinutes(), getSeconds(), getMilliseconds()`: Get the hours, minutes, seconds, and milliseconds, respectively.<br>

### **Setting Date Components:**
`setDate(day), setMonth(month), setFullYear(year)`: Set the day of the month, month (0-11), and year, respectively.<br>

`setHours(hours), setMinutes(minutes), setSeconds(seconds), setMilliseconds(milliseconds)`: Set the hours, minutes, seconds, and milliseconds, respectively.

### **Formatting Dates:**
`toDateString(), toISOString(), toLocaleDateString(), toLocaleString(), toLocaleTimeString(), toString(), toTimeString(), toUTCString()`: These methods convert a Date object to various string representations according to different formatting rules and locales.

## Dom Manuipulation APIs

# Coding concepts
## 1. Currying
### Definition:
Currying is a fundamental concept in JavaScript that involves transforming a function with multiple arguments into a series of functions, each taking a single argument.
This makes the code more flexible and reusable.
### Syntax:
* It creates a chain of functions, each taking a single argument and returning a new function that waits for the next argument
* This chaining continues until all the arguments are provided, and the final function produces the desired result.
### Challenge 1: Currency converter
```javascript
const convertCurrency = (conversionRate) => (fromCurrency) => (toCurrency) => (amount) => {
const convertedAmount = ( amount * conversionRate[fromCurrency][toCurrency]).toFixed(2);

return `${amount} ${fromCurrency} is equal to ${convertedAmount} ${toCurrency}`;
}

const usdToEur = convertCurrency({USD: { EUR: 0.85}});
console.log(usdToEur("USD")("EUR")(100));

```
### Challenge 2: customer permissions
```javascript
const checkPermission = permissions => resource => action => {
    if(permissions[resource] && permissions[resource].includes(action)){
        return `Permission granted: ${action} in ${resource}`;
    }
    
    return `Permission denied: ${action} in ${resource}`;
}

const userPermissions = checkPermission({files: ['read','write'], photos:['read']});

console.log(userPermissions("files")("read"));
```
### Challenge 3: Functional composition

```javascript
const pipe = (...fns) => (x) => fns.reduce((acc, fn) => fn(acc),x);

const square = x => x * x;

const double = x => x * 2;

const addOne = x => x + 1;

const transform = pipe(square, double, addOne);

console.log(transform(3));
// result: 19 (square(3) => double(9) => addOne(18))
```
## Currying vs Partial function
While both currying and partial functions involve breaking down functions, currying generates a chain of functions that each take one argument,<br> whereas partial functions fix some arguments and return a new function with fewer arguments.
Here is a comparison:
**Currying**
```javascript
const multiply = a => b => a * b;

const double = multiply(2);
console.log(double(5));
```
**Partial function**
This technique is often used for functional programming and can be implemented in various ways in JavaScript, such as using closures or bind() method.
```javascript
const partialMultiply = (a, b) => a* b;
const double = x => partialMultiply(2,x);

console.log(double(5));
```
*Factory functions are used to create and return instances of objects.*
*Partial functions are functions created by fixing some arguments of another function, producing a new function with reduced arity (number of arguments).*

## 2. Closures
### Definition:
A closure is a function that is bundled together with its lexical environment.ie., It is a function that remembers the scope in which it was created, even if it is executed outside of the scope.
### Syntax:
```javascript
function outerClosureFunction (input) {
    let message ='count';
    const = count = 10;
    
    function inner() {
        return message + count;
    }
    
    return inner;
}

let closureObj = new outerClosureFunction(3);
console.log(closureObj());
```
**Usecases**
### Data encapsulation
You can create private variables that can't be accessed from outside.
```javascript
function Counter(){
let count=0;
return {
increment: function(){count++;},
getCount: function(){ return count;}
};
}
```
### Factory functions:
A factory function is a function that returns an object. It is called a "factory" because it's designed to produce instances of objects, similar to how a factory produces goods.
Sometimes factory functions return other functions, often with some arguments or internal variables set to specific values(closures). 
They are a way to generate functions dynamically but not all dynamic function generation is done through factory functions.

```javascript
function multiplier(factor){
return x=> x*factor;
}

//example2
function createPerson(name, age) {
  return {
    name: name,
    age: age,
    greet: function() {
      console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
  };
}

let person1 = createPerson('Alice', 30);
let person2 = createPerson('Bob', 25);
```
### Dynamic function generation
Dynamic function generation refers to the creation of functions at runtime based on certain conditions or parameters. This often involves closures because the dynamically generated functions might close over variables in their surrounding scope.
### function curation:
Function curation is the process of taking a function with multiple arguments and producing from it a function that takes fewer arguments. The missing arguments are set to specific values. This is closely related to the concept of "partial application" in functional programming.


## 3. IIFE

## 4. Destructuring 

## 5. Inheritance

### Protype inheritance
_proto_ is a property of every variable that points to the parent object inherited from. In contrast, the prototype is a property of every constructor function that contains all stuff that its instance will inherit. So both are the same thing but act from different ends.

The difference between class inheritance and prototypal inheritance is that if any changes to class methods occur after creating some objects then those objects do not get the updated methods as their old/already created instances do not get updated because when we develop functions using this in the constructor are considered as properties, not as methods 
But, in prototypal inheritance, it will get updated to all the existing instances.

There are three ways to create prototype inheritance in js

Code sample - https://github.com/ColorCode/js-10-things/blob/main/1-inheritance/example.js

### Class inheritance

## 6. Spread and rest operator

## 7. Callback, Promises, and Async Await

### Promises
**syntax**
```javascript
let promise = new Promise(function(resolve, reject) {
  if(success)
      resolve("done!"), 1000);
      else reject("Not valid");
});

// resolve runs the first function in .then
promise.then(
  result => alert(result), // shows "done!" after 1 second
  error => alert(error) // doesn't run
);
// If we’re interested only in errors, then we can use null as the first argument: .then(null, errorHandlingFunction). Or we can use .catch(errorHandlingFunction), which is exactly the same.
promise.catch(alert); // shows "Error: Whoops!" after 1 second

```
**convert the above promise to Async and await**
```javascript
const returnSamplePromise = () => {
return promise;
}

async function convert() {
    let res = await returnSamplePromise();
}

convert();

```

## 8. Hoisting 
## 9. Call by value and call by difference


# Coding challenges
## 1. What is the output of the snippet below

The JavaScript for-in statement loops through the properties of an Object:

```javascript
let language = [ 'python', 'javascript'];
let obj = {..language};

console.log('2' in language);
console.log('javascript' in obj);
```
## 2. Swap the two variables' values without using the temporary variable

```javascript
let x = 2, y = 3;
    console.log("Before Swapping: x = " +  x + ", y = " + y);
    // x now becomes 5
    x = x + y;
    // y becomes 2
    y = x - y;
    // x becomes 5
    x = x - y;
    console.log("After Swapping: x = " + x + ", y = " + y);
//using Array
[x,y] = [y,x]
```

## 3. Write a function to count the occurrences of each character in the string. 

```javascript
function countCharacterOccurrences(str) { 
  const charCount = {}; 
  for (let char of str) { 
    charCount[char] = (charCount[char] || 0) + 1; 
  } 
  return charCount; 
} 
```

## 4. Get the output format of the given input string 
let input = 'apple' the output should be `"A-Pp-Ppp-Llll-Eeeee"`

```javascript
const sample = (input) => {
    let spl = input.split('');
    
    let res = spl.reduce((acc, val, index) => {
        for(let i=0; i<=index;i++){
            if(i==0)
                acc = acc + val.toUpperCase();
            else acc = acc + val;
        }
        return index==spl.length-1 ? acc : acc+ '-';
    },'');
    
    return res;
}

console.log(sample(str));
```
## 5. Remove duplicates from the array or get the unique values in an array
```javascript
const removeDuplicates = arr => [...new Set(arr)];

console.log(removeDuplicates([1,2,3,22,3,2,4,5,5,5,6,7]));
```
**without using built-in function(set)**
```javascript
const removeDuplicates = arr => {
    let result = [];
    arr.map((val) => {
        if(!result.includes(val)){
            result.push(val);
        };
    });
    
    return result;
}

console.log(removeDuplicates([1,2,3,22,3,2,4,5,5,5,6,7]));
```

## 6. String Related tasks

### Check if a string is a palindrome
A palindrome is a word, phrase, number, or other sequence of characters that reads the same forward and backward 
```javascript
const isPalindrome = str => str === str.split('').reverse().join('');

console.log(isPalindrome('racecar'));
```
### Remove all the vowels from a string
```javascript
const removeVowels = str => str.replace(/[aeiou]/gi, '');
console.log(removeVowels('hello world'));
```
### Check if a string contains a substring
```javascript
const contains = (str, subString) => str.includes(subString);
console.log(contains('hello world', 'll'));
```
## 6. Array Related tasks
### Sorting an array
```javascript
const sortAsc = arr => array.sort((a,b) => a -b);
const sortDesc = arr => array.sort((a,b) => b-a);
```
### Get the first n elements of the array
```javascript
const take = (arr,n) => arr.slice(0,n);
console.log(take([1,2,3,4,5,6],3));
```
### Get the last n elements of the array
```javascript
const take = (arr,n) => arr.slice(-n);
console.log(take([1,2,3,4,5,6],3));
```
### Check if an array is empty
```javascript
const isArrayEmpty = arr => Array.isArray(arr) && arr.length > 0;
console.log(isArrayEmpty([1,2,3,4,5,6]));
```
### Find max/min values in array
```javascript
Math.max(...array);
Math.min(...array);
```
## 7. Find the domain name from an email
```javascript
const extractDomain = mail => mail.split('@')[1];

console.log(extractDomain('kaleewaripss96@gmail.com'));
```
## 8. Flatten an nested array
```javascript
const extractDomain = mail => mail.split('@')[1];

console.log(extractDomain('kaleewaripss96@gmail.com'));
```

# Real-time coding snippets for the project
## 1. Generate random string
We can use `Math.random()` to generate a random string, It very convenient to generate a unique ID

```javascript
const randomString = () => Math.random().toString(36).slice(2);
```
## 2. Generate a random string of a given length

```javascript
const randomString = (length =10) => {
    let result = '';
    while(result.length < length) {
        result += Math.random().toString(36).slice(2);
    }
    
    return result.slice(0, length);
}
```
Random number of a given length
```javascript
 const generateRandomNumbers = () => {
    let random = [];
    for (let i = 0; i < count; i++) {
      random.push(Math.floor(Math.random() * 10));
    }
    setRandom(random);
  }; 
```
## 2. Copy content to the clipboard

```javascript
const copyToClipboard = text => navigator.clipboard.writeText(text);
copyToClipboard("Hello world");
```

## 3. Clear all cookies
```javascript
const clear = document.cookie.split(';').forEach(cookie => document.cookie = cookie.replace(/^ +/, '').replace(/=.*/, `=;expires=${new Date(0).toUTCString()};path=/`));
```
## 4. Get the selected text by the user
```javascript
const getSelectedText = () => window.getSelection().toString();
getSelectedText();
```
## 5. Scroll to the top of the page
```javascript
const goToTop = () => window.scrollTo(0,0);
goToTop();
```
## 6. Check whether the user has scrolled to the bottom of a page
```javascript
const scrolledToBottom = () => document.documentElement.clientHeight + window.scrollY >= document.documentElement.scrollHeight;
```
## 7. Find out if the current tab is active
```javascript
const isTabInView = () => !document.hidden
```
## 8. Redirect the user to a URL
```javascript
const redirect = url => location.href = url;

redirect("https://www.google.com/");
```
## 9. Open the browser print box
```javascript
const showPrintDialog = () => window.print();
```
## 10. Generate a random boolean value
```javascript
const randomBoolean = () => Math.random() >=0.5;

randomBoolean();
```
## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```
## 12. Check the given number is an integer
```javascript
const isInteger = (num) => num % 1 === 0;
```
## 13. Check if a variable is an array
```javascript
const isArray = arr => Array.isArray(arr);
```
## 14. Date related tasks
**Check if the date is the weekend**
`getDay()` will return the day of the week (from 0 to 6) of a date.
```javascript
const isWeekend = date => {
    console.log(date.getDay());
    return [0, 6].indexOf(date.getDay()) !== -1;
}
console.log(isWeekend(new Date('2024-06-22'))); // sat
console.log(isWeekend(new Date('2024-06-23'))); // sun
```
**getting day of the week**
```javascript
function getDayName(dayIndex) {
  const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
  return days[dayIndex];
}
// Create a Date object for February 26, 2024 (a Tuesday)
const today = new Date('2024-02-26');
// Using getDay() to retrieve the day of the week
const dayOfWeek = today.getDay();

console.log(`Today is a ${getDayName(dayOfWeek)}.`);
```
**Calculate the number of days between two dates**
```javascript
const dayDiff = (date, date2) => Math.ceil(Math.abs(date - date2) / 84600000);

console.log(dayDiff(new Date('2023-05-19'), new Date('2024-05-19')));
```
## 15. Capitalize a string
```javascript
const capitialise = str => str.charAt(0).toUpperCase() + str.slice(1);

console.log(capitialise('hello world'));
```
## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```## 11. Generate a random number between two values
```javascript
// Returns a random number between the min and max variable's values
const randomNumber = Math.random() * (max - min) + min;
```

