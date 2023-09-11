# Sort Band Names Without Articles

## Goals

Sorting band names by a given array.

## Concepts

### Regex

```regex
/^(a |the |an )/i
```

- `^`: asserts position at start of the string
- `()`: Capturing Group, alternative by `|`
- `a `, `the `, `an `: match characters, ensure the `space`
- `/i`: Global pattern flags, case insensitive match (ignores case of [a-zA-z])

### `String.replace()`

See further descriptions in [MDN][String.prototype.replace()].

### `Array.sort()`

It's usable to compare two strings with `Array.sort()`, put the filtered band name to judge that whether `a > b ? 1 : -1` or not.

Here is an example of array sorting: [Creating, displaying, and sorting an array][Array.prototype.sort()/Creating, displaying, and sorting an array]

[String.prototype.replace()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace
[Array.prototype.sort()/Creating, displaying, and sorting an array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#creating_displaying_and_sorting_an_array