# Function Arguments

## arguments is actually not an true array. It is an liked-array
```javascript
function add() {
    assert(Array.isArray(arguments) , "arguments is an array");
}
add(1,2,3);
```
<!-- js-console -->

## It does not has array's methods
```javascript
function highest(){ 
  return arguments.sort(function(a,b){ 
    return b - a; 
  }); 
} 
const num = highest(2,3,4)[0];
```
<!-- js-console -->

## But we can invoke methods of array in other ways.
```javascript
function makeArray(array){ 
  return Array().slice.call( array ); 
}

function highest(){ 
  var result = makeArray(arguments).sort(function(a,b){ 
    return b - a; 
  });
  return result[0];
} 

function sum() {
    let total = 0;
    makeArray(arguments).forEach(function (item) {
        total += item;
    });
    
    return total;
}
const num = highest(1,2,3);
assert(num === 3, 'highest number is 3');

const total = sum(1,2,3);
assert(total === 6, 'return from sum is 6');
```
<!-- js-console -->

