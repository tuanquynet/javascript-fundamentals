# Function Prototype

When calling a method of an object, it will look up on direct member of object first if not exists, it continue to lookup on prototype of its constructor.

```javascript
function User(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}

User.prototype.getFullname = function (name) {
    return this.firstName + ' ' + this.lastName;
}

const bob = new User('Bob', 'Job');

console.log(!!bob.getFullname(), 'Instance method exists and is callable');
```
<!-- js-console -->

## Attach a method directly to the instance to override its prototype
```javascript
function User(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;

    this.getFullname = function (name) {
        return this.firstName + ', ' + this.lastName;
    }
}

User.prototype.getFullname = function (name) {
    return this.firstName + ' ' + this.lastName;
}

const bob = new User('Bob', 'Job');

console.log(bob.getFullname() === 'Bob, Job', 'Instance method exists and is callable');
```
<!-- js-console -->
