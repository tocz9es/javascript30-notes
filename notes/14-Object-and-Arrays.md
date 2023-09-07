# Object and Arrays (References VS Copying)

## Goal

Learning the non-primitive data type, and how to copy them.

## Concepts

If assign a primitive value to a variable such as `Undefined, Null, Boolean, Number, String and Symbol`, it can be directly accessed by value. Otherwise assign a non-primitive value (Object, Array), we can access this variable by reference.

More details in 'JavaScript Advanced Program Design' Book, located in `Chapter 4`.

### Ways to copy an array

- `arr.slice()`
- `[].concat(arr)`
- `[...arr]`
- `Array.from(arr)`

### Ways to copy a object

- Shallow Copy: `Object.assign({}, obj, { newVal: 1 })`
- Deep Copy: `JSON.parse(JSON.stringify(obj))`