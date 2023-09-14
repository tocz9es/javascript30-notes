# Tally String Times with Reduce

## Goal

If a page provided the list with `data-time` attribute and have `string` time stamp data, try to add them up together.

## Steps

1. Using `Array.from(document.querySelectorAll())` and `Array.map()` to fetch all `string` time stamp.
2. Process the result array by splitting to separate minutes and seconds, return a total seconds of each item, and sum all of them.
3. The summed seconds should split to the hours, minutes and seconds.

## Concepts

These following points have mentioned before:

- Convert `NodeList` to a normal array: `Array.from()`
-  `Array.map()`, `Array.reduce()`

### `Number.parseFloat()`

This function parses a string argument and return a floating point number.

### `Math.floor()`

This method always rounds down and returns the largest integer less than or equal to a given number.

```javascript
console.log(Math.floor(5.9)) // 5
console.log(Math.floor(-5.1)) // -6
```