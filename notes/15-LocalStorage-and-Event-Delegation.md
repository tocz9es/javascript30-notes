# LocalStorage and Event Delegation

## Goal

Try to make a interactive dishes' menu page using localStorage to store and fetch data with advanced event manipulation.

## Steps

1. Write logics about `items` render function. Fetching `items` data from localStorage by default, otherwise return a empty array. Globally execute a function, pass both items data and `itemsList` variable, set the innerHTML by looping `items` to assemble a HTML fragment.
2. Implement form's `submit` event, block default submit handling, wrap text data and default `done` status with an object. Then add this object to `items` array, set the localStorage's value with `stringify`ing it.
3. Handle with item's `click` event, find `index` of the clicked item before reversing the `item.done` boolean, and override the localStorage's value.

## Concepts

### localStorage

- Set item with key: `localStorage.setItem('key', val)`
- Get item with key: `localStorage.getItem('key')`

### Block default event's handling

```javascript
  const addItems = document.querySelector('.add-items');
  addItems.addEventListener('submit', addItem);

  function addItem(e) {
    e.preventDefault(); // block actual http request

    this.reset(); // clear form's content
  }
```