# JavaScript Drum Kit

## Targets

当键盘敲击对应按键时：

  1. 发出按键对应的声响；
  2. 按键对应的矩形处，添加后删除 `class=playing`，显示后隐藏带动画的黄色边框；

当键盘连续敲击（或按住）按键时：

  1. 需要即时响应按键对应的声响；
  2. 同上(2.)；

## Concepts

### KeyCode

[JavaScript event keycode detection](https://keycode.info/)

### Data attribute (data-)

[Using data attributes - MDN](https://developer.mozilla.org/docs/Learn/HTML/Howto/Use_data_attributes)

在 JavaScript 中，Data attribute 和元素选择搭配使用的示例：

```javascript
// Warning: value of data-attribute should be wrapped with double quotes
document.querySelector(`audio[data-key="65"]`)
```

### Event Listener

  1. [Event.type - MDN](https://developer.mozilla.org/docs/Web/API/Event/type)

    included: 'keydown', 'keypress', 'keyup', 'mousedown', 'mouseup', 'click', 'transitionend'...

  2. KeyboardEvent contains `key` and `keyCode`: `{ ..., key: 'a', keyCode: 65, ... }`

  3. `transitionend` can listen on an element's transition running status. When it ends, this event starts working. It's used to remove the class `playing`.

### DOM element selection APIs

常见的元素选择 API 包括：

- `document.querySelector()`
- `document.querySelectorAll()`
- `document.getElementById()`
- ...

### APIs for `<audio>` element

1. [\<audio\> - MDN](https://developer.mozilla.org/docs/Web/HTML/Element/audio)

  常见的操作有：`play()`、`pause()`...

2. 无冲突地播放音频

  利用 `audio.currentTime = 0`，将会让当前音频播放时间设置为 0，即每次按键都重置播放时间，这样能够做到瞬时播放音频。

### APIs for manipulating element's CSS style

当变量为 Node 时，可以使用 `classList()` 对元素的 `class` 进行添加或删除操作：

- `classList.add('playing')`
- `classList.remove('playing')`

### Arrow Function

For example, you can write the anonymous function by this way:

```javascript
function (key) {
  key.addEventListener('transformend', removeTransition);
}
```

While using arrow function, you can write the above code like this:

```javascript
key => key.addEventListener('transformend', removeTransition);
```

But here is a thing you need to know, the main difference is where `this` point to. [Arrow Fcuntions/Description - MDN](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Functions/Arrow_functions#description)

```javascript
'use strict';

var obj = { // does not create a new scope
  i: 10,
  b: () => console.log(this.i, this),
  c: function() {
    console.log(this.i, this);
  }
}

obj.b(); // prints undefined, Window {...} (or the global object)
obj.c(); // prints 10, Object {...}
```