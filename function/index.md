# Function

There are some type of functions:
1. function declaration:
```javascript
function loadData() {};
```
2. function expression (or anonymous function): 
```javascript
const loadData = function () {};
```
3. arrow function (ES6):
```javascript
const loadData = () => {};
```

## Declared Function will be hoisted but express function and arrow are not

```javascript
console.log(getUser instanceof Function, 'getUser is a function');
console.log(addUser instanceof Function, 'addUser is a function');
console.log(removeUser instanceof Function, 'removeUser is a function');

//function declaration
function getUser() {
    console.log('getUser');
};
//function expression or anonymous function
var addUser = function addUser() {};

var removeUser = () => {}
```
<!-- js-console -->

## Use Function as an Object
```javascript
const obj = {};
const func = function () {};
obj.count = 0;
func.count = 0;

console.log(obj.count === func.count, 'Both are objects, both has property.');
```
<!-- js-console -->

## Function is called method when it is assigned to an object property
```javascript
const obj = {};
const count = function () {};
obj.count = count;

console.log(obj.count instanceof Function, 'obj.count is a method');
```
<!-- js-console -->

