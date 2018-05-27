# Flexible Arguments

## arguments is not an array. It is an liked-array
```javascript
function add() {
    console.log(Array.isArray(arguments) , "arguments is an array");
}
add(1,2,3);
```
<!-- js-console -->
