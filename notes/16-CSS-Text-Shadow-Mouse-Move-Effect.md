# CSS Text Shadow Mouse Move Effect

## Goal

Make a dynamic text shadow effect when the mouse moves over the specific target `div`.

## Steps

1. Attach an event listener to the element you want to track the mouse's movement. Ensure you calculate the mouse's position accurately, be cautious about the `offsetWidth` and `offsetHeight` when the event target switches to the `text` div.
2. Define the shadow's distance and compute the relative pixel values for the shadow concerning the `text` div.
3. You can configure multiple shadows by interchanging the values of offset-x and offset-y.

## Concepts

### Relative Mouse Position

If you just want the position of the page, it's great to use `clientX` and `clientY`, but for a element, it'll become a little bit complicated. In this example, if mouse pointer move to a element inside the event listener's element, you should also get `offsetLeft` and `offsetTop` of that inner element.

```javascript
function shadow(e) {
  const { offsetX: x, offsetY: y } = e;

  if (this !== e.target) {
    x = x + e.target.offsetLeft;
    y = y + e.target.offsetTop;
  }
}
```

### Relative Shadow Offsets

The dynamic text's shadow should be effected in a container element, and a maximum distance should also provided. If this value is `500px`, how this shadow positioned?

Example uses `xWalk` and `yWalk` to calculate this:

```javascript
const xWalk = Math.round((x / width * walk) - (walk / 2));
const yWalk = Math.round((y / height * walk) - (walk / 2));
```

It's important to note that when the text is on the corner of `hero` div, shadow position should be limited to a range between `-250px` and `250px`. In `Math.round()` function, the first half mainly output the distance radio of the width / height, then subtract half of the maximum distance to ensure the shadow remains within the desired range.