# Inheritance

When we talk about inheritance we need to understand 2 terminology: own property, inherit property.
- own property is a property attacked directly on an object (instance).
- inherit property is a property attacked on prototype of its class (constructor) or prototype of parent class.


```javascript
function Person() {}
Person.prototype.talk = function(){};// method will typically not be overrided after defined.
Person.prototype.name = 'default'; // but property will be assigned new value.

const john = new Person();
console.log( john.name === 'default', "john has property 'name' because it inherit from its class." );
console.log( john.hasOwnProperty('name'), "but it is its own property." );
console.log( john.hasOwnProperty('talk'), "and john object owns talk method." );

//a property will be created and attached to object
john.name = 'john';
console.log( john.hasOwnProperty('name'), "when assigning value to a property, it will be created and attached to object");
```
<!-- js-console -->

## Distinguish Sharing Function and Inheritance
```javascript
function Person() {}
Person.prototype.talk = function(){};

function Student() {}

// Share the same function but it is not inheritance.
Student.prototype = Person.prototype;
Student.prototype = { talk: Person.prototype.talk };

const john = new Student();
console.log( john instanceof Person, "john receives functionality from the Person prototype" );

// Only this maintains the prototype chain
Student.prototype = new Person();

const bob = new Student();

console.log( bob instanceof Student, "bob receives functionality from the Student prototype" );
console.log( bob instanceof Person, "bob receives functionality from the Person prototype" );
```
<!-- js-console -->
