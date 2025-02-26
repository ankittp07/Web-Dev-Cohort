# Topics of this Class

## Variables

- let and const

```javascript
const name = "Ankit";
let age = 22;
```

## Datatypes

### Primitive Datatypes

- String - "", '', ``

```javascript
let myName = "Ankit";
```

- Number - 23(integer), 23.5(float)

```javascript
let myAge = 22;
```

- Boolean - true, false

```javascript
let isEmployed = false;
```

- null

```javascript
let favouriteColor = null;
```

- undefined

```javascript
let hometown;
```

- Symbol
- BigInt

### Non-Primitive/Object Datatypes

- array

```javascript
let skills = ["HTML", true, 23, "CSS", `Javascript`];

let fruits = new Array("apple", "mango", "banana");

console.log(fruits.length);
// output - 3

console.log(skills[0]);
// output - HTML

skills[0] = "Python";
console.log(skills);
// output - ["Python", true, 23, "CSS", `Javascript`]
```

- object

```javascript
let myProfile = {
  name: "Joe",
  age: 22,
  isPaid: true,
  skills: ["Java", "C++"],
  favouriteClass: null,
};
```

### Examples -

```javascript
console.log(typeof isEmployed);
// output - boolean

console.log(typeof skills);
// output - object

console.log(typeof hometown);
// output - undefined

console.log(typeof favouriteColor);
// output - object
```

## Conditionals

### if-else conditional -

```javascript
let num = 2;

if (num === 2) {
  console.log("it is a even number");
} else {
  console.log("it is not a even number");
}

if (num === 1) {
  console.log("it is a odd number");
} else if (num === 3) {
  console.log("it is a odd number");
} else {
  console.log("it is not a odd number");
}

let result = num === 0; // result = false;

if (result) {
  console.log("it is a even number");
} else {
  console.log("it is not a even number");
}
```

### Example -

```javascript
let numberofGuest = 4;

let pizzaSize;

if (numberofGuest <= 2) {
  pizzaSize = "small";
} else if (numberofGuest <= 5) {
  pizzaSize = "medium";
} else {
  pizzaSize = "large";
}

console.log(pizzaSize);
// output - medium
```

- internally if-else works on greedy algorithm

## Methods in Array

### array.push()

```javascript
let alpha = [1, 2];
alpha.push(3);
console.log(alpha);
// output - [1, 2, 3]
```

### array.unshift()

```javascript
let alpha = [1, 2];
alpha.unshift(3);
console.log(alpha);
// output - [3, 1, 2]
```

### array.pop()

```javascript
let alpha = [1, 2, 3];
alpha.pop();
console.log(alpha);
// output - [1, 2]
console.log(alpha.pop());
// output - 3
```

## Loops

### for-loop

```javascript
let nums = [1, 2, 3, 4, 5];
let sum = 0;

for (let i = 0; i < nums.length; i++) {
  sum = sum + nums[i];
}

console.log(sum);
// output - 15
```
