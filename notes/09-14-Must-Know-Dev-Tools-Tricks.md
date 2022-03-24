# 14 Must Know Dev Tools Tricks

## Element breakpoints

If an HTML element bind to a JavaScript function (using `onClick` or etc.). It's easy to break the process if this element changes. To achieve this, using DevTools' `Elements` panel, right-click on the element and select `Break on… -> attribute modifications`. When the element changes, the breakpoint will be triggered.

## Console manipulations

### Interpolated strings

```javascript
console.log('1 + 1 = %s', '2'); // 1 + 1 = 2

// alternative way: using ``

console.log(`1 + 1 = ${1 + 1}`); // 1 + 1 = 2
```

### Styled `console.log()`

```javascript
console.log('%cHello, world!', 'color: red; font-size: 20px;');
```

### `warn()`, `error()` and `info()`

Using `warn()`, `error()` and `info()` to print different noticeable messages to the console.

### Using `assert()` to test the condition

If an error should displayed when certain condition triggers, use `assert()` to test the condition.

```javascript
console.assert(1 === 2, '1 is not equal to 2');
```

### `clear()`

It's easy to understand, clear the console.

### Using `dir()` to view DOM elements

Sometimes it's just a HTML segment displayed in the console. To view the DOM element, use `dir()`.

### `group()` and `groupEnd()`

When a object is displayed in the console, it's easy to break the object into several parts. Use `group()` to start a new group, and `groupEnd()` to end the group.

```javascript
dogs.forEach(dog => {
  console.group(dog.name);
    console.log('Breed: %s', dog.breed);
    console.log('Age: %s', dog.age);
  console.groupEnd();
})
```

### Using `count()` to count the number of times a variable or a function is called

```javascript
console.count('foo'); // foo: 1
console.count('bar'); // bar: 1
console.count('bar'); // bar: 2
console.count('bar'); // bar: 3
console.count('foo'); // foo: 2
```

### Using `time()` and `timeEnd()` to calculate the time

If you run a fetch() function, you can use `time()` and `timeEnd()` to calculate the time.

```javascript
console.time('fetch start');
fetch('https://api.github.com/users/octocat')
  .then(res => res.json())
  .then(data => {
    console.timeEnd('fetch end');
  });
```

### Using `table()` to turn an array into a table

If an array has same properties, it's easy to turn it into a table showing on the console.