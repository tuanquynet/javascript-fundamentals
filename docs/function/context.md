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
assert(!aUser.disabled, "disabled of aUser has been changed." );
```
<!-- js-console -->

## Call a function, context change accidentally
```javascript
function User(){ 
  this.disabled = true; 
} 
User();
assert( window.disabled === true, "A global variable `disabled` was created accidentally" ); 
 
const toyota = { 
  change: function(){ 
    this.available = true; 
  } 
};

//invoke the method change of toyota
toyota.change(); 
assert(toyota.available === true, "When it's an object property, the value is set within the object.");
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

//call method activate of toyota but change context to honda using `call`
toyota.activate.call(honda);
assert(toyota.activated === true, "toyota.activated has been changed.");
assert(honda.activated === true, "honda.activated has been changed.");

//call method activate of toyota but change context to honda using `apply`
toyota.deactivate.apply(honda);
assert(honda.activated === false, "honda.activated is false now.");
```
<!-- js-console -->

```javascript
//bind object as context to a function
function changeName(name) {
    this.name = name;
}
const bob = {};

changeNameForBob = changeName.bind(bob);
changeNameForBob('john');
/*/
changeName.bind(bob)('john');
/*/
assert(bob.name === 'john', "now name of bob is john.");
```
<!-- js-console -->

## Advanced use of `apply` on methods of built-in Object.
```javascript
const numbers = [1,2,3];
const max = Math.max.apply(Math, numbers);

assert(max === 3, "Apply Math.max successfully");
assert(isNaN(Math.max(numbers)), "We can not pass array to Math.max()");
```
<!-- js-console -->

