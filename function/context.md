# Context

## Call a method
```javascript
var aUser = { 
  disabled: true, 
  remove: function(){ 
    this.disabled = !this.disabled; 
  } 
}; 
aUser.remove(); 
console.log(!aUser.disabled, "disabled of aUser has been changed." );
```
<!-- js-console -->

## Call a function, context change accidentally
```javascript
function User(){ 
  this.disabled = true; 
} 
User();
console.log( disabled === true, "A global object now exists with that name and value." ); 
 
const toyota = { 
  change: function(){ 
    this.available = true; 
  } 
}; 
toyota.change(); 
console.log(toyota.available === true, "When it's an object property, the value is set within the object.");
```
<!-- js-console -->

## How can we change the context of a function?
```javascript
const toyota = {
    activated: false,
    activate: function () {
        this.activated = true;
    },
    deactivate: function () {
        this.activated = false;
    }
};
const honda = {
    activated: false,
};

toyota.activate.call(honda);
console.log(toyota.activated === true, "toyota.activated has been changed.");
console.log(honda.activated === true, "honda.activated has been changed.");

toyota.deactivate.apply(honda);
console.log(honda.activated === false, "honda.activated is false now.");
```
<!-- js-console -->

```javascript
//bind as object as context to a function
function changeName(name) {
    this.name = name;
}
const bob = {};

changeNameForBob = changeName.bind(bob);
changeNameForBob('john');
/*/
changeName.bind(bob)('john');
/*/
console.log(bob.name === 'john', "now name of bob is john.");
```
<!-- js-console -->

## Advanced use of `apply` on method built-in Object.
```javascript
const numbers = [1,2,3];
const max = Math.max.apply(Math, numbers);

console.log(max === 3, "Apply Math.max successfully");
console.log(isNaN(Math.max(numbers)), "We can not pass array to Math.max()");
```
<!-- js-console -->

