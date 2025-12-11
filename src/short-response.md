# Short Responses

For this short response assignment, aim to write a response with the following qualities (your instructor will give you feedback on these areas):

- [] Addresses all parts of the prompt
- [] Accurately uses relevant technical terminology
- [] Is free of grammar and spelling mistakes (double check with grammarly!)
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Is easy to comprehend

For each prompt below, write your response in the space provided. Aim to answer each prompt in 2-5 concise sentences. Make sure to preview your markdown to check how it is rendered before submitting.

## Prompt 1

Read the following code: s

```js
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = playlist1;
playlist2.songCount = 15;
console.log(playlist1.songCount);
```

Part A: What will be logged to the console? Why?

Part B: How would you modify the code so that reassigning `playlist2.songCount` does NOT affect `playlist1`.songCount? Write the corrected code below your response (we've provided the broken code again for you to fix).

### Response 1

Part A:
15 will be logged to the console because objects in JS are reference types, so when you do `const playlist2 = playlist1;` it doesn't create a copy of playlist 1 into playlist 2, rather it is using the refrence in the memory from playlist 1. That's why when we try to modify playlist 2 it will modify the same object, so when `playlist2.songCount` is changed to 15 `playlist1.songCount` is also changed to 15.

Part B:
I would modify this code by making a true copy of the object, I can do this by using the spread operator.

**Corrected Code:**

```js
// fix this!
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = { ...playlist1 };
playlist2.songCount = 15;
console.log(playlist1.songCount);
```

---

## Prompt 2

```js
const students = [
  { name: "Maya", grade: 92, passed: true },
  { name: "Jamal", grade: 78, passed: true },
  { name: "Destiny", grade: 88, passed: true },
  { name: "Marcus", grade: 95, passed: true },
];
```

For each task below, identify which array method (forEach, filter, map, find, or reduce) you would use.

1. You need to get an array containing only students who scored above 85.
2. You need to find the student named "Destiny" and update their grade to 90.
3. You need to calculate the average grade of all students.
4. You need to create an array of strings in the format: "Maya: 92"

### Response 2

1. .filter
2. .find
3. .reduce
4. .map

---

## Prompt 3

We should expect that the code below prints the array `[ 'A', 'B', 'C', 'D' ]` but an error is thrown when the third line of code is executed.

Explain why this error occurs, how to fix it, and provide a suggestion for how to avoid this error in the future.

```js
const letters = ["a", "b", "c", "d"];
const capitalize = (str) => str.toUpperCase();

const upperCaseLetters = letters.map(capitalize());
// Uncaught TypeError: Cannot read properties of undefined (reading 'toUpperCase')

console.log(upperCaseLetters);
```

### Response 3

This error occurs because of the line `letters.map(capatalize())` since capatalize has no argument passed there is a type error. The way to fix it is to remove the parenthesis after `capatalize` so it will looks like `letters.map(capatalized)` instead so now .map calls capatalize for each element in the array. How you would avoid this mistake in the future is by keeping in mind to not call a callback function, only use parenthesis after the callback function if you'd like to give the function something else to call.

## Prompt 4

Given this code:

```js
const orders = [
  { id: 1, total: 45 },
  { id: 2, total: 23 },
  { id: 3, total: 67 },
];

const grandTotal = orders.reduce((sum, order) => {
  return sum + order.total;
}, 0);
```

- Part A: What will `grandTotal` equal after this code runs?
- Part B: Explain what the `0` at the end of the reduce method does. Why is it important?
- Part C: Walk through what happens in the FIRST iteration of reduce:
  - What is the value of sum?
  - What is the value of order?
  - What gets returned?

### Response 4

Part A: `grandTotal` will equate to 135.
Part B: The 0 stands for the initial or starting value of the accumulator, without this `sum` would start at the first object in the array which will cause an error.
Part C: In the first iteration of reduce, the value of sum will be 0 since it will start at the initial value. The value of order will be the first element in the array which is `{id: 1, total: 45}` and what gets returned is 45 since 0 + 45 is 45.
