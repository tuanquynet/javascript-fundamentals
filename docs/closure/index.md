# Closures

We only care about closures when there is a function declared inside another function.

## Lexical scoping

```javascript
function init() {
  var name = 'JavaScript'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    console.log(name); // use variable declared in the parent function    
  }
  displayName();
}
init();
```
<!-- js-console -->

## Closure
```javascript
function makeFunc() {
  var name = 'JavaScript'; // name is a local variable created by init
  function displayName() { // displayName() is the inner function, a closure
    console.log(name); // use variable declared in the parent function    
  }
  return displayName;
}
const f = makeFunc();
f();
```
<!-- js-console -->

## Use closure to create isolated context.
```javascript
//IIFE
var counter = (function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  };   
})();
assert(counter.value() === 0, 'value of counter is initialize with 0');

counter.increment();
assert(counter.value() === 1, 'counter change value to 1');
```
<!-- js-console -->

## A quick wrapper function will do the trick.

```javascript
var count = 0;
// Here is one of common pitfalls
for ( var i = 0; i < 4; i++ ) {
  setTimeout(function(){
    assert(i == count++, "Check the value of i." );
  }, i * 200);
};
```
<!-- js-console -->

```javascript
var count = 0;
//Using closure to fix the problem
for ( var i = 0; i < 4; i++ ) (function(i){
  setTimeout(function(){
    assert(i == count++, "Check the value of i." );
  }, i * 200);
})(i);
```
<!-- js-console -->
