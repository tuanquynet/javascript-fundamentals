# Function Arguments

## arguments is actually not an true array. It is an liked-array
```javascript
function add() {
    console.log(Array.isArray(arguments) , "arguments is an array");
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

## But we can use call array's methods in other ways.
```javascript
function makeArray(array){ 
  return Array().slice.call( array ); 
}

function highest(){ 
  return makeArray(arguments).sort(function(a,b){ 
    return b - a; 
  }); 
} 

function sum() {
    let total = 0;
    makeArray(arguments).forEach(function (item) {
        total += item;
    });
    
    return total;
}
const num = highest(1,2,3)[0];
console.log(num === 3, 'highest number is 3');

const total = sum(1,2,3);
console.log(total === 6, 'return from sum is 6');
```
<!-- js-console -->

