# Geolocation based Speedometer and Compass

> WARNING: In order to active Geolocation correctly, running on a live server with HTTPS is needed.
>
> [Enabling HTTPS for Live Server Visual Studio Code Extension](https://graceydev.hashnode.dev/enabling-https-for-live-server-visual-studio-code-extension)

## Goal

Show the compass degree and number of speed on page using `geolocation` API.

## Concepts

### Geolocation

Geolocation API has ability to let user grant their location on web applications to achieve specific interactions and functions. It is accessed by a call to `navigator.geolocation`, user's browser will popup a notification to ask for permission to access their location data. The browser will use the data when user accept the request.

In this tutorial, `.arrow` and `.speed-value` is elements that we should control. We can get `coords.speed` and `coords.heading` from result by accessing `geolocation.watchPosition()`.

```javascript
navigator.geolocation.watchPosition(data => {
  speed.textContext = data.coords.speed
  arrow.style.transform = `rotate(${data.coords.heading}deg)`
}, err => {
  alert(err)
})
```