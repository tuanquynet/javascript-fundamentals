# Scope

Before ecmascript 6 there are only 2 types of scope including global and local (function) scope.

```javascript
// Global scope
const config = {};
const version = '1.0.0';

function loadUser() {
  // local variable
  let userId = 1;
  const url = `http://my-api/users/${userId}`;

  fetch(url);
}

// `let` not working on IE11
// i is in block scope
for (let i = 0; i < 10; i++) {
  setTimeout(() => {
    console.log(i);
  }, 100)
}

for (var i = 0; i < 10; i++) {
  // j is in block scope
  let j = i;
  setTimeout(() => {
    console.log(j);
  }, 100)
}

const role = 'admin';
let task = 'fix-bug';
if (role) {
  // block scope
  let task = 'sleep';

  console.log('inside:', task);
}

console.log('outside:', task);


```
