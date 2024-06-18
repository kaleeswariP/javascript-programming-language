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
_proto_ is a property of every variable that points to the parent object that is inherited from whereas as prototype is a property of every constructor function that contains all stuff that will be inherited by its instance. So both are the same thing but act from different ends.

The difference between class inheritance and prototypal inheritance is that if made any changes to class methods occur after creating some objects then those objects do not get the updated methods as their old/already created instances do not get updated because when we develop functions using this in the constructor are considered as properties, not as methods 
But, in prototypal inheritance, it will get updated to all the existing instances.

There are three ways to create prototype inheritance in js

Code sample - https://github.com/ColorCode/js-10-things/blob/main/1-inheritance/example.js

### Class inheritance

## 6. Spread and rest operator

# Coding challenges
## 1. What is the output of the snippet below

```
let language = [ 'python', 'javascript'];
let obj = {..language};

console.log('2' in language);
console.log('javascript' in obj);
```
