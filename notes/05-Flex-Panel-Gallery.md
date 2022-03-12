# Flex Panel Gallery

## Target

1. Using flexbox to display the desired effect of panels

## Concepts

### Flexbox

Flexbox is a one-dimensional layout method for arranging items in rows and columns. More on [Flexbox - MDN](https://developer.mozilla.org/docs/Learn/CSS/CSS_layout/Flexbox)

To make a element to flexbox, you should add `display: flex;` to element's rule. And some properties you may use:

- `flex` contains with `flex-grow`, `flex-shrink` and `flex-basis`.
- `flex-direction` controls which direction should box arrange, `flex-direction: row` set as default.
- `align-items` controls where the flex items sit on the cross axis.
- `justify-content` controls where the flex items sit on the main axis.

### `classList.toggle()`

Here use another method to switch to add or remove class. In this gallery case, we using `addEventListener` to detect the DOM `propertyName`. If shows the `flex-grow` property, we will trigger the class.