# Instantiation

We must always use `new` operator to instantiate an object. `new` operator tell JS runtime to create new object and pass this object as context to constructor.

## Wrong Instantiation

```javascript
function User(name) {
    this.name = name;
}
const bob = User('bob');
console.log(bob instanceof User, "bob is instantiated correctly");
```
<!-- js-console -->

## Correct Instantiation

```javascript
function User(name) {
    this.name = name;
}
const bob = new User('bob');

assert(bob instanceof User, "bob is instantiated correctly");
assert(bob.name === 'bob', "name of bob is bob");
```
<!-- js-console -->

## More examples

```javascript
function User(name) {
    this.name = name;
    this.changeName = function (newName) {
        this.name = newName;
    }
}
const bob = new User('bob');
assert(bob.name === 'bob', "name of bob is bob");

bob.changeName('no-bob');
assert(bob.name === 'no-bob', "now name of bob is no-bob");
```
<!-- js-console -->

We can write code better if you know that JavaScript is **dynamic** language. It allow us to **attack** any value to an object.
```javascript
function User(name) {
    this.changeName = function (newName) {
        this.name = newName;
    }
    this.changeName(name);
}

const bob = new User('bob');
assert(bob.name === 'bob', "name of bob is bob");

bob.changeName('no-bob');
assert(bob.name === 'no-bob', "now name of bob is no-bob");
```
<!-- js-console -->
