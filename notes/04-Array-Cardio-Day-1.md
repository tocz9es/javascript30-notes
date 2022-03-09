# Array Cardio Day 1

## Target

1. Using Array functions: `map()`, `sort()`, `filter()`, `reduce()`...

## Concepts

### NodeList is not a stantard array

As the definition of NodeList, which is different from stantard Array, so here are some ways to convert NodeList to:

1. `Array.form(NodeList)`
2. `[...NodeList]`

### `Array.reduce()`

Be Cautious to the arguments of `reduce()`, remind to set initial value.

More on [Array.prototype.reduce() - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce).

### Functions using two values

  - `Array.prototype.sort()` must use `firstValue` and `SecondValue` to compare with.
  - `Array.prototype.reduce()` will use `previousValue` and `CurrentValue` to manipulate with.

### `includes()` function

  `includes()` function can be used in `Array` and `String`:

  - `Array.prototype.includes()` method determines whether an array includes a certain value among its entries, returning true or false as appropriate.
    
    More on [Array.prototype.includes()](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

  - `String.prototype.includes()` method performs a case-sensitive search to determine whether one string may be found within another string, returning true or false as appropriate.
    
    More on [String.prototype.includes()](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
