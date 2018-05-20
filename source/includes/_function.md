# Function

Only function declaration is hoisted.

```javascript
//function declaration
function loadData() {}

//function expression or anonymous function
const loadData = function() {}

//attach directly into window to make global function
window.loadData = function() {}

console.log(getUser);//
console.log(addUser);// show function
console.log(window.removeUser);

function getUser() {};
const addUser = function addUser() {};
window.removeUser = function removeUser() {}

```
