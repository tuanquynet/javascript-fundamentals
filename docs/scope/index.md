# Scope

Before ecmascript 6 there are only 2 types of scope including global and local (function) scope.

* Global scope: When variable, function are declared outside any functions, it became global.
* Local scope: When variable, function are declared in a function, they are local.

ES6 add one more type of scope. It is block scope. `if` block, `for` block, `while` block. We can create a block as below
```javascript
{ 
    let blockScopeVar;
    const blockScopeConst = 20;
}
```

## Global & Local
```javascript

const config = {};
var version = '1.0.0';
var newVersion = '1.0.1';

function changeVersion() {
  // local variable
  var version;

  version = '1.0.1';
  newVersion = '2.0';

  console.log('version: ' + version);
  console.log('newVersion: ' + newVersion);
}
changeVersion();
console.log('-----------');
console.log('version: ' + version);
console.log('newVersion: ' + newVersion);

```
<!-- js-console -->

## Block
```javascript
// Noted: `let` not working on IE11
// i is in block scope
for (let i = 0; i < 10; i++) {
  setTimeout(() => {
    console.log(i);
  }, 100)
}

//The above statement is equivalent to this one
for (var i = 0; i < 10; i++) {
  // j is in block scope
  let j = i;
  setTimeout(() => {
    console.log(j);
  }, 100)
}

```
<!-- js-console -->

## Another example of block
```javascript
const role = 'admin';
let task = 'fix-bug';
if (role) {
  // block scope
  let task = 'sleep';

  console.log('inside: ' + task);
}

console.log('outside: ' + task);

```
<!-- js-console -->
