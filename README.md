# javascript-guide

Javascript programming language guidelines/notebook

# Javascript Basics

#

# Coding concepts
## 1. Currying
### Definition:
### Syntax:
### challenge 1:

## 2. Closures
### Definition:
### Syntax:

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
