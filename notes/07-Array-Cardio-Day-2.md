# Array Cardio Day 2

## Goal

Finish all the tasks descriped in the `START.html`

## Concepts

### Difference between `Array.prototype.some()` and `Array.prototype.every()`

If a statement is given, `some()` will check if a element of the array fullfills the statement. `every()` will check if all elements fullfill the statement. Return value will be Boolean.

[Array.prototype.some() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

[Array.prototype.every() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

### Difference between `Array.prototype.find()` and `Array.prototype.findIndex()`

Set a condition to find elements that statisfy the condition. `find()` will return the first element that fullfills the condition. `findIndex()` will return the index of the first element that fullfills the condition.

Warning: These two functions aren't suitable to find more then one element. Because they only returned the first.

[Array.prototype.find() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

[Array.prototype.findIndex() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

### Difference between `Array.prototype.slice()` and `Array.prototype.splice()`

`slice()` will return **an new array** that you specified index from begin to end (not included). `splice()` will remove or add elements to the **array you specified**.

[Array.prototype.slice() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

[Array.prototype.splice() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

### Using `slice()` to create a new array with removed elements

```javascript
const comments = [
  { text: 'Love this!', id: 523423 },
  { text: 'Super good', id: 823423 },
  { text: 'You are the best', id: 2039842 },
  { text: 'Ramen is my fav food ever', id: 123523 },
  { text: 'Nice Nice Nice!', id: 542328 }
];

const index = 4;
const deletionComments = [
  ...comments.slice(0, index),
  ...comments.slice(index + 1)
];
```