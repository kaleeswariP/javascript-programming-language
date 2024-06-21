# javascript-guide

Javascript programming language guidelines/notebook

# Javascript Basics

#

# Coding concepts
## 1. Currying
### Definition:
Currying is a fundamental concept in JavaScript that involves transforming a function with multiple arguments into a series of functions, each taking a single argument.
This makes the code more flexible and reusable.
### Syntax:
* It is creating a chain of functions,each taking a single argument and returning a new function that waits for the next argument
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
While both currying and partial functions involve breaking down functions, currying generates a chain of functions that each take one argument,<br> whereas partial functions fix some arguments and retuen a new function with fewer arguments.
Here is a comparison:
**Currying**
```javascript
const multiply = a => b => a * b;

const double = multiply(2);
console.log(double(5));
```
**Partial function**
```javascript
const partialMultiply = (a, b) => a* b;
const double = x => partialMultiply(2,x);

console.log(double(5));
```

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
Factory functions are functions that return other functions, often with some arguments or internal variables set to specific values(closures). 
They are a way to generate functions dynamically but not all dynamic function generation is done through factory functions.

```javascript
function multiplier(factor){
return x=> x*factor;
}
```
### Dynamic function generation
Dynamic function generation refers to the creation of functions at runtime based on certain conditions or parameters. This often involves closures because the dynamically generated functions might close over variables in their surrounding scope.
### function curation:
Function curation is the process of taking a function with multiple arguments and producing from it a function that takes fewer arguments. The missing arguments are set to specific values. This is closely related to the concept of "partial application" in functional programming.


## 3. IIFE

## 4. Destructuring 

## 5. Inheritance

### Protype inheritance
_proto_ is a property of every variable that points to the parent object that is inherited from whereas as prototype is a property of every constructor function that contains all stuff that its instance will inherit. So both are the same thing but act from different ends.

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

```

