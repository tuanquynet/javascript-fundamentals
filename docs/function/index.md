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
assert(getUser instanceof Function, 'getUser is a function');
assert(addUser instanceof Function, 'addUser is a function');
assert(removeUser instanceof Function, 'removeUser is a function');

assert(addUser === undefined, 'addUser is undefined');
assert(removeUser === undefined, 'removeUser is undefined');

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

assert(obj.count === func.count, 'obj and func both are objects, both has property.');
```
<!-- js-console -->

## Function is called method when it is assigned to an object property
```javascript
const obj = {};
const count = function () {};
obj.count = count;

assert(obj.count instanceof Function, 'obj.count is a function');
```
<!-- js-console -->

