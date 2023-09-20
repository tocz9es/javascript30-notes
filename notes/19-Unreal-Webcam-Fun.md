# Unreal Webcam Fun

## Goal

Display user's camera and apply different effects on page using browser provided APIs.

## Concepts

### `MediaDevices.getUserMedia()`

This method belongs to the Media Capture and Streams API which provides support for streaming audio and video data. The method ask the user for permission to use a media input. This lesson is using this and assigns the result to a video element.

```javascript
const video = document.querySelector('.player')

function getVideo() {
  navigator.mediaDevices.getUserMedia({ video: true, audio: false })
    .then(localMediaStream => {
      video.srcObject = localMediaStream
      video.play()
    })
    .catch(err => console.error(err))
}

getVideo()
```

### Canvas

`<canvas>` is a HTML element to draw graphics and animations. Unlike the `<img>` element, this requires the closing tag. In this lesson, a `<canvas>` element is given. Before using `drawImage()` to draw the video image onto it, it's necessary to use `getContext()` to get a drawing context.

```javascript
const canvas = document.querySelector('.photo')
const ctx = canvas.getContext('2d')

function paintToCanvas() {
  const { width, height } = { video.videoWidth, video.videoHeight }
  canvas.width = width
  canvas.height = height

  return setInterval(() => {
    ctx.drawImage(video, 0, 0, width, height)
  }, 16)
}
```

After user confirm the authentication of `getUserMedia()`, the `paintToCanvas()` function should be activated with an `canplay` event listener.

```javascript
video.addEventListener('canplay', paintToCanvas)
```

In order to achieve the `takePhoto()` function, canvas' data can take out and convert to Base64 URL. We can create a `<a>` link element and replace the `src` attribute with URL, also set `download` attribute to make this link can be download.

```javascript
function takePhoto() {
  // play the sound
  snap.currentTime = 0
  snap.play()

  // take the data out of the canvas
  const data = canvas.toDataURL('image/jpeg');
  const link = document.createElement('a');
  link.href = data;
  link.setAttribute('download', 'handsome');
  link.innerHTML = `<img src="${data}" alt="Handsome Man" />`;
  strip.insertBefore(link, strip.firstChild);
}
```

The manipulations to show different effects basically use `getImageData()` to extract every pixels' `rgba`, then put these `rgba` data to a recalculate functions, finally use `putImageData()` to put modifications back.

Here's some effects in this lesson:

```javascript
// ...
// function paintToCanvas() {
//   ...
//   return setInterval(() => {
     ctx.drawImage(video, 0, 0, width, height)
     let pixels = ctx.getImageData(0, 0, width, height)
    //  You can only use one of these following functions
     pixels = redEffect(pixels)
     pixels = rgbSplit(pixels)
     pixels = greenScreen(pixels)
//   })
// }

function redEffect(pixels) {
  for (let i = 0; i < pixels.data.length; i += 4) {
    pixels.data[i + 0] = pixels.data[i + 0] + 200
    pixels.data[i + 1] = pixels.data[i + 1] - 50
    pixels.data[i + 2] = pixels.data[i + 2] * 0.5
  }
  return pixels
}

function rgbSplit(pixels) {
  for (let i = 0; i < pixels.data.length; i+=4) {
    pixels.data[i - 150] = pixels.data[i + 0]
    pixels.data[i + 500] = pixels.data[i + 1]
    pixels.data[i - 550] = pixels.data[i + 2]
  }
  return pixels
}

function greenScreen(pixels) {
  const levels = {}

  document.querySelectorAll('.rgb input').forEach((input) => {
    levels[input.name] = input.value
  })

  for (i = 0; i < pixels.data.length; i = i + 4) {
    red = pixels.data[i + 0]
    green = pixels.data[i + 1]
    blue = pixels.data[i + 2]
    alpha = pixels.data[i + 3]

    if (red >= levels.rmin
      && green >= levels.gmin
      && blue >= levels.bmin
      && red <= levels.rmax
      && green <= levels.gmax
      && blue <= levels.bmax) {

      pixels.data[i + 3] = 0
    }
  }

  return pixels
}
```

### Base64

> Base64 is a group of binary-to-text encoding schemes that represent binary data in sequences of 24 bits that can be represented by four 6-bit Base64 digits. … Base64 is particularly prevalent on the World Wide Web where one of its uses is the ability to embed image files or other binary assets inside textual assets such as HTML and CSS files.

> [Base64 / Wikipedia](https://en.wikipedia.org/wiki/Base64)