# Native Speech Recognition

## Goal

Recognize user's voice and output to page in realtime.

## Concepts

### `SpeechRecognition`

`SpeechRecognition` is a constructor that can create instances on page to detect what user is saying and provide text results.

Here's how to initialize it:

```javascript
window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition

const recognition = new SpeechRecognition()
// When interimResults option is true, SpeechRecognition will dynamic adjust the detected words and confirm at the end.
recognition.interimResults = true
recognition.lang = 'en-US'
```

After this initialization, we need to add an event listener to monitor results:

```javascript
recognition.addEventListener('result' e => {
  const transcript = Array.from(e.results)
    .map(result => result[0])
    .map(result => result.transcript)
    .join('')
})
```

When processing the output words, we can filter words that are unsuitable to appear such as bad languages.

```javascript
// recognition.addEventListener('result' e => {
//   ...
     const poopScript = transcript.replace(/poop|poo|shit|dump/gi, '💩')
     p.textContent = poopScript
// })
```

All the processing the final words need to output at `.words` element:

```javascript
// create a blank <p> element in '.words' element at first
let p = document.createElement('p')
const words = document.querySelector('.words')
words.appendChild(p)

// recognition.addEventListener('result' e => {
//   ...
     if (e.results[0].isFinal) {
      p = document.createElement('p')
      words.appendChild(p)
     }
// })
```

At the end, we should automatically start recognition when instance trigger the `end` event.

```javascript
recognition.addEventListener('end', recognition.start)

recognition.start()
```

[Ref: SpeechRecognition - MDN](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition)