# Follow Along Links

## Goal

When user hover to a `<a>` tag link, a highlight will dynamically follow to that.

## Steps

1. Use querySelector to get all `<a>` tags.
2. Create a blank `<span>` tag and its class for highlight.
3. Add `mouseenter` eventListener to all `<a>` tags that selected, bind to a new function that process the highlighter.
4. In this new function, fetch `<a>` tag div's coord and size using `getBoundingClientRect()`, then override highlighter's style by using this width, height, top and left. In order to achieve the `following` effect, using `transform` and `translate(X, Y)`.

## Concepts

### `getBoundingClientRect()`

This method returns a `DOMRect` Object with infos about element's position and size. Notice that the top and left values should consider the scrolled value.
