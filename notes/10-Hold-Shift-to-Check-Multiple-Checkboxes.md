# Hold Shift to Check Multiple Checkboxes

## Goal

Check an item in a list, hold `Shift` and click on another item to check items in between.

## Methods

### Record last Selection and select checkboxes in between

1. Using `addEventListener()` to listen all checkboxes when `click` event is fired.

2. Using `let lastChecked` to record last checked checkbox.

3. Check another checkboxes with *Shift* key pressed. `handleCheck()` will loop over every checkbox and trigger the `inBetween` status when checkboxes between `lastChecked` and current checkbox.

4. When `inBetween` is triggered, `handleCheck()` will applied to those checkboxes in between.

5. [Bad behaviour] If `lastChecked` is below the current checkbox, this method will not work.

### Implement Method

Only `inBetween` variable is not enough to handle different kinds of manipulation.

A better way is to record the index of the last checkbox, then when the shift is triggered, `slice()` the checkboxes between current checkbox's index and the last.

This method will save the time, and just loop checkboxes in between. And it's flexible to judge the checkbox's index of the last and current using `Math.min()` and `Math.max()`.

> Warning: `NodeList` is not an array, so we can't use `Array.prototype.slice()` to slice it. Should use `Array.from()` to convert it to an array.

### Code

```javascript
const checkboxes = Array.from(document.querySelectorAll('.inbox input[type="checkbox"]'));

// If user directly pressed shift and check in item,
// this initial value will help user select the default (first) checkbox to the current one.
// Learned it from Gmail web app.
let lastCheck = 0;

function selectFunc(e) {
  let nowCheck = checkboxes.indexOf(this);
  let checked = this.checked;
  if (e.shiftKey) {
    checkboxes.slice(
      Math.min(lastCheck, nowCheck), Math.max(lastCheck, nowCheck) + 1
    ).forEach(item => item.checked = checked);
  }
  lastCheck = nowCheck;
}

checkboxes.forEach(item => item.addEventListener('click', selectFunc));
```