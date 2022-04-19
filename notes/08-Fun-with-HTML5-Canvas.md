# Fun with HTML5 Canvas

## Goal

1. Press down the mouse to draw lines on the canvas.
2. Using `hsl()` to dynamicly transform colors on the lines.
3. Dynamicly changing the size of the lines.

## Concepts

### Canvas

Canvas provides a way to draw or animate graphics by using JavaSciprt and `<canvas>` element, and it focuses on 2D graphics.

Quickly start to get canvas element and draw a line by using following code:

```javascript
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext('2d');

ctx.beginPath();
ctx.moveTo(50, 50);
ctx.lineTo(200, 50);
ctx.stroke();
```

In this work, we also use some functions to adjust line width, color, etc.

```javascript
ctx.lineJoin(); // shape to join the two line segments
ctx.lineCap(); // shape to draw the end points of lines
ctx.lineWidth(); // line width
ctx.strokeStyle(); // line color
```

More introductions on [Canvas - MDN](https://developer.mozilla.org/docs/Web/API/Canvas_API).

### hsl()

`hsl()` is a function that takes three arguments: hue, saturation, and lightness. An optional argument controls color's transparency. The hue argument is a number between 0 and 360. So in this case, we increase the value of hue, to make the line more colorful.

```javascript
let hueVal = 0; // change color by increasing this value
ctx.strokeStyle = `hsl(${hueVal}, 100%, 50%)`;
```

[hsl() - MDN](https://developer.mozilla.org/docs/Web/CSS/color_value/hsl).

### Descructuring assignment

In early ECMAScript, it's impossible to assign data to multiple variables at once. Since ES6, we can pack multiple variables into an array and use destructuring assignment to assign data to these variables.

```javascript
let [lastX, lastY] = [0, 0];

[lastX, lastY] = [e.offsetX, e.offsetY];
```

[Destructuring assignment - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

### Mouse Event

The drawing is done by mouse event. So it's necessary to listen to mouse event on the canvas.

If the mouse is pressed, the drawing status is also triggered. Current cursor position will be saved in `lastX` and `lastY`.

If the mouse is moved, the line will be drawn from `lastX` and `lastY` to the current cursor position.

[Mouse Event - MDN](https://developer.mozilla.org/docs/Web/API/MouseEvent)