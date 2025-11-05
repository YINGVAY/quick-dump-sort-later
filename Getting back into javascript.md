**new and revised syntax for me

`typeof null`  outputs `"object"`

a basic script that adds one value to the variable i, until it reaches 3, then it stops
```javascript
for (let i = 0; i < 3; i++) {
console.log(i);
}
```

A basic array that returns banana, we know this because we call the array with the designation 1, and arrays start at 0

```javascript
const fruits = ["apple", "banana", "cherry"];
console.log(fruits[1]);
```

object properties, this will output 30, as we are calling on the value of age

```javascript
const person = { name: "John", age: 30 };
console.log(person["age"]);
```

Truthy and falsy values, this returns falsy because a empty string is equal to zero

```javascript
if ("") {
  console.log("Truthy");
} else {
  console.log("Falsy");
}
```

`this` keyword in use, returning the value Alice

```javascript
const person = {
  name: "Alice",
  greet: function() {
    console.log(this.name);
  }
};

person.greet();
```

Arrow function returning 12

```javascript
const add = (a, b) => a + b;
console.log(add(5, 7));
```

[[2025-01-14 (fourth day, feeling overwhelmed)]]







