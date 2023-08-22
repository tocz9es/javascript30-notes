# Slide in on Scroll

## Goal

When user scroll the page, images should show or hide from left or right.

ps: The `debounce()` function is already prepared.

## Steps

1. Select the images you wanna control, using the `.slide-in.active` class to perform show, hide, and slide.
2. Create a `checkSlice` function, bind it to a listener to monitor the `scroll` event, the function should use `debounce()` to limit usage.
3. Implement the `checkSlide` function, here should figure out the height should trigger the `sideIn` and `sideOut` effects. Choose half of the image's height as the `sideIn` height and the bottom of the image as the `sideOut` height. 
  - Define `slideImageHalf` and `imageBottom`;
  - Calculate `isHalfShown` and `isNotScrolledPast`;
  - Judge the statement of `isHalfShown && isNotScrolledPast`. If true, add `.active` class to the image, otherwise, remove `.active` class from the image.

## Concepts

### debounce

**Debounce function** is frequently used in development, it will delay the function's execution until a certain time has passed. When user unusually trigger a function, this will decrease the browser's performance and cause errors.

> Developers often introduce both `debounce` and `throttle` to their applications to improve the performance and stability.

### `window.scrollY`, `window.innerHeight`, `offsetTop`

- `window.scrollY` is the current scroll position of the window;
- `window.innerHeight` is the height of the window;
- `offsetTop` is the distance from the top of the element to the top of the window.