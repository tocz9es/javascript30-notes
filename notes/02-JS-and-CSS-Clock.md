# JS and CSS Clock

## Target

1. 三个指针（时针、分针、秒针）需要能分别绕自身元素的末端旋转
2. 做出指针转动的抖动效果（有副作用）

## Concepts

### CSS `transform` and `transform-origin` property

  - [transform - MDN](https://developer.mozilla.org/docs/Web/CSS/transform)

    `transform`'s value included: `translate`, `scale`, `rotate`...

  - [transform-origin - MDN](https://developer.mozilla.org/docs/Web/CSS/transform-origin)

    `transform-origin` sets where the position of element's `transform` starts, if set this value to `100%`, that means the action you take on this element will perform at `bottom right`.

### maybe confused with `transform`, `translate` and `transition`?

  `transition` can define different effects of an element, more on [transition - MDN](https://developer.mozilla.org/docs/Web/CSS/transition)

  `transform` allows developers to `rotate()`, `scale()`, `translate()` etc.

  `translate()` is a CSS function and pair with `transform`, it can repositions an element in the vertical or horizontal directions, more on [translate() - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate())

### `Date` object

Once you call `new Date()` on code, it represents a single moment at the time you called it. This case uses the following methods by this object:

- `Date().getHours()`
- `Date().getMinutes()`
- `Date().getSeconds()`

### Timing function: Linear and Cubic Bézier

