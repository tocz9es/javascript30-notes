# Custom Video Player

## Goal

Make all custom control buttons, progress etc., work functionally.

## Concepts

### APIs from Video elements

1. Using `video.paused` to judge the video is playing or not. `video.play()` and `video.pause()` can be used to play and pause the video.
2. Using `video.currentTime` and `[data-skip]` to skip specific time.
3. Properties of `video` can be defined on `input` elements, so using `video[input.name]` is easy to change value.

### Make sure to set `change` and `mousemove` event on certain controls

If you only set `change` event on `input` elements, the value will be updated when you click the element, drag will not work. So it's better to set another `mousemove` event on elements.

In this work, `progress` should add a global status to judge whether the `mouseup` or `mousedown` on the progress bar.

```
let mousedown = false;

progress.addEventListener('mouseup', () => { mousedown = false });
progress.addEventListener('mousedown', () => { mousedown = true });
progress.addEventListener('mouseout', () => { mousedown = false });
progress.addEventListener('mousemove', (e) => mousedown && scrub(e));
```