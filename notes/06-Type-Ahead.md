# Type Ahead

## Goal

  1. Fetch JSON data from certain URL
  2. Filter result by user input
  3. Display result and highlight the matched text

## Concepts

> This case uses some concepts we've mentioned before, such as DOM manipulation and event handling.

### `fetch()`

If you're developing a project with frameworks, maybe you're familiar with libraries like `axios`. But with plain JavaScript, maybe you don't know how to use `fetch()`.

So, `fetch()` is a method that is used to make a request to a server. It returns a promise. Using `then()` to handle the response.

A basic `fetch()` request looks like this:

```javascript
fetch('http://example.com/movies.json')
  .then(response => response.json())
  .then(data => console.log(data));
```

More content about `fetch()` can be found in [Using the Fetch API - MDN](https://developer.mozilla.org/docs/Web/API/Fetch_API/Using_Fetch).

### Manipulate Array

In this showcase, when a keyword has been given, we can `filter()` the array to get the result. Then use `map()` to parse the result to HTML string.

### Manipulate String

You can make a simple regex match using `match()` method. But user input is a variable, so it's better to use `new RegExp()` creating a regex with a variable as the pattern.

The final functions should be add the highlight class to the matched text. So we use regex and `replace()` to find and replace the matched text.

### `new RegExp()`

`new RegExp()` makes a new regular expression. The first argument is the pattern, and the second argument is the flags. More on [RegExp - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp).

### Spread Operator: `...`

Sometimes we met a situation that need to fit array's items into array. It's way too complicated that using for loop. So we can use spread operator to solve this.

```javascript

const arr = [1, 2, 3];

// Before
const newArr = [-1, 0];
for (let i = 0; i < arr.length; i++) {
  newArr.push(arr[i]);
}

// After
const newArr = [-1, 0, ...arr];
```