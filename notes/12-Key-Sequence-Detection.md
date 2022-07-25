# Key Sequence Detection

## Goal

Type keys on the page to trigger certain actions.

## Steps

1. Create event listener on `keydown` event.
2. On this event, you should record the `key` and put it into a array.
3. Define a length of the array, if a new key typed and the size of array is full, shift() the array and push the new key.
4. Define a secret word that you want to match, every time user typed the key, combine the array, and compare it with the secret word.
5. If the secret word matches, trigger certain action.

## Code

```javascript
const secretWord = 'secret'
const recordKeys = []

const keyDownEvent = (e) => {
  if (recordKeys.length === secretWord.length) {
    recordKeys.shift()
  }
  recordKeys.push(e.key)
  const secretWordMatch = recordKeys.join('') === secretWord
  if (secretWordMatch) {
    alert('You win!')
  }
}

document.addEventListener('keydown', keyDownEvent)
```